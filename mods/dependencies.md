---
description: Как установить зависимости для модов Geode
---

# Зависимости

Geode предоставляет инструменты, позволяющие модам зависеть от других модов, что упрощает переиспользование кода.

Обратите внимание, что Geode **управляет только теми зависимостями, которые являются модами**. Обычные зависимости C++, такие как библиотека для парсинга JSON, библиотека ZIP или какие-нибудь сетевые утилиты, **должны быть просто установлены, как и в любом другом проекте на C++**. Используйте CPM, Git-подмодули, копируйте код в свой проект, в общем, как вам удобнее. Если библиотека динамическая, подключите `.dll` к своему моду через ключ `files` в `resources`.

Однако, иногда возникает необходимость использовать код, который нельзя подключить как обычную библиотеку; например, **custom keybinds**. Geode не предоставляет никаких готовых иструментов для настройки пользовательских клавиш, поэтому вам придется использовать библиотеку. Однако было бы не очень разумно, если бы каждый мод поставлял свои собственные несовместимые средства для работы с привязками клавиш. Вместо этого, должен быть один мод, который просто добавляет эту функциональность, а затем другие моды могут зависеть от него и вызывать его функции для работы с пользовательскими клавишами.

## Как работают моды-зависимости

Моды-зависимости по своей сути аналогичны обычным модам, за исключением того, что они **включают свои заголовочные файлы и файлы для линковки в свой .geode пакет**. Обычно заголовочные файлы находятся в папке `include` внутри пакета, но могут располагаться и в любом другом месте. Файл для линковки представляет собой `mod.id.lib` на Windows или бинарный файл мода в корне пакета на прочих платформах.

В остальном, моды-зависимости ничем не отличаются от обычных модов; они могут устанавливать хуки, патчи, добавлять функции в игру и публиковаться в каталоге модов. Однако, **моды-зависимости должны сводить функциональность, которую они добавляют, к минимуму**, и быть сфокусированными на конкретных функциях, которые они призваны добавлять. Например, мод-зависимость для пользовательских горячих клавиш должна добавлять только необходимое для работы с горячими клавишами; она не должна добавлять кучу других функций, таких как добавление новых иконок или настройка меню.

Если зависимость является обязательной, то она **линкуется**, что означает необходимость ее наличия для запуска мода, от неё зависящего. Однако, с учетом того, что иногда требуется использовать зависимость только в случае ее загрузки, **существует возможность пометить зависимость как необязательную**. В этом случае она не линкуется, а значит, прямое использование ее функций становится невозможным; вместо этого, необходимо применять функции Geode, предназначенные для работы с необязательными зависимостями. Дополнительные сведения можно найти в разделе [Необязательные зависимости](#optional-dependencies).

## Добавление зависимостей

Зависимости можно включить в ваш мод, просто добавив их в ключ `dependencies` в [mod.json](/mods/configuring.md):

```json
{
    "geode": "v1.0.0",
    "id": "my.example-mod",
    "name": "My example mod",
    "developer": "Me",
    "version": "v1.0.0",
    "dependencies": [
        {
            "id": "someone-elses.mod",
            "version": ">=v1.2.5",
            "importance": "required"
        }
    ]
}
```

Dependencies have two required properties: the ID of the dependency and the version depended on. Additionally, the dependency may have an [importance](#importance), which specifies if the dependency is required or not.

The `version` field of a dependency may be written as `>=version`, `=version`, or `<=version`. The comparisons work as expected, with the addition that if the major versions are different, the comparison is always false. This means that if you depend on version `>=1.2.5` of a mod, version `v1.8.0` will be considered acceptable but `v2.0.0` will not. For this reason, [if you make a mod that is depended upon, you should follow strict semver](https://semver.org).

Once you have added a dependency to your `mod.json`, if you have [Geode CLI v1.4.0 or higher](/geode/installcli), it's headers are automatically added to your project. If you have the mod installed, the headers from the installed version will be used. If you don't have the mod installed, Geode will install it from the mods index. The added dependency files for your project can be found in `build/geode-deps/<dep.id>`. Geode automatically add `build/geode-deps` to your project's include path, and links whatever binaries are found in dependencies, meaning you most likely don't have to configure anything.

## Example

The mod `hjfod.gmd-api` contains utilities for working with [.GMD files](https://fileinfo.com/extension/gmd). You can add it to your mod by adding the following to your `mod.json`:

```json
{
    "dependencies": [
        {
            "id": "hjfod.gmd-api",
            "version": ">=v1.0.0"
        }
    ]
}
```

Now, if you reconfigure your CMake (or if you're using CMake Tools in VS Code, it should be reconfigured automatically), Geode should automatically find `hjfod.gmd-api` in your installed mods. If the mods index, and install it for you.

```cpp
#include <hjfod.gmd-api/include/GMD.hpp>
// do things with gmd-api's functions
```

If you now go to compile and test your mod, everything should work out-of-the-box.

## Importance

> Possible values:
> - `required` (default) - Dependency must be installed for this mod to work
> - `recommended` - Dependency is not required, but is recommended and will be downloaded by default.
> - `suggested` - Dependency is not required, and will not be downloaded by default.

In case the dependency is **not required**, it is not linked to, which in turn means that you can't use any of its exported functions. In cases like these, the dependency should provide ways through Geode to dynamically call its functions, such as through events.

### Events

The key system Geode provides for optional mod interop are events. For example, a mod that adds support for drag-and-dropping files on the GD window could define a drag-and-drop event that other mods can then listen to.

Usually however, events are defined in code in a way that requires linking by inheriting from the `Event` class. To avoid this, mods that want to support being used optionally should also provide events that are specializations of the `DispatchEvent` class:

```cpp
using DragDropEvent = geode::DispatchEvent<ghc::filesystem::path>;
using DragDropFilter = geode::DispatchFilter<ghc::filesystem::path>;

// Posting events in source
DragDropEvent("geode.drag-drop/default", "path/to/file").post();
```

All `DispatchEvent`s have an associated ID, which is specific for each `DispatchEvent` specialization. This can be used to differentiate between events; for example, the drag drop API might use this to let dependencies determine which file types they listen to.

Mods that use the dependency can now listen for drag-and-drop events:

```cpp
$execute {
    new EventListener(+[](ghc::filesystem::path const& path) {
        log::info("File dropped: {}", path);
        return ListenerResult::Propagate;
    }, DragDropFilter("geode.drag-drop/default"));
};
```

An example of using dispatch events in practice [can be found in MouseAPI](https://github.com/geode-sdk/MouseAPI/blob/main/src/test.cpp#L54-L94).

### Attributes

One way for mods to communicate with optional dependencies is through **node attributes**, which may contain any data. These are like the `setUserData` and `setUserObject` functions native to `CCNode`s, except that attributes have a string key associated with them. For example, a mod that adds scrollbars to layers might use the following check to see if a scrollbar should be added to a layer:

```cpp
if (layer->getAttribute<bool>("hjfod.cool-scrollbars/enable")) {
    // add scrollbar
}
```

Other mods can set this attribute on their layers with the `CCNode::setAttribute` function.

Mods can also add an event listener to listen for when attributes are added/changed:

```cpp
$execute {
    new EventListener<AttributeSetFilter>(
        +[](AttributeSetEvent* event) {
            addScrollbar(event->node);
        },
        AttributeSetFilter("hjfod.cool-scrollbars/enable")
    );
}
```
