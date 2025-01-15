---
Заголовок: 3. Создание та компиляция мода
очередь: 5
---

# Создание нового мода

После установки всех программ и вещей, вы можете создать свой первый мод!

Чтобы это сделать откройте терминал в месте где вы хотите создать мод и напишите:
```bash
geode new
```
Следуя этим указаниям у вас должна содержащая папка, где содержатся все нужные файлы для создания моду.

## Файлы

Следуя этим указаяниям, у вам в папке должны появится файлы для работы над модом. Давайте разберем что это такое, и с чем это едят:
 * `CMakeLists.txt` - Это главный CMake файл, для вашего мода.
 * `about.md` - Тут вы можете написать длиннющие описание для вашего мода. КОГДА ВЫ ЕГО ПИШИТЕ ДУМАЙТЕ КАК БУДТО ЭТО ФАЙЛ README (Прочитай меня). Этот файл технически не нужен, но на деле крайне рекомендуется чтобы он был
 * `logo.png` - Это иконка для вашего мода, которая будет показывается в игре. Этот файл технически не нужен, но на деле крайне рекомендуется чтобы он был.
 * `mod.json` - В этом json файле содержатся все метаданные про ваш мод, такие как: версия, имя мода, настройки его, и так далее. [Если хотите узнать об этом по подробнее перейдите сюда](/mods/configuring)

Если в ваших планах есть выпуск мода, то помните что вы должны отредактировать файлы about.md и logo.png!

Исходный код вашего мода должен находится папке `src`.

## Additional Files

Geode will also look for these special files within your mod folder:
 * `changelog.md` - Lists all of the changes between versions to the mod; [see detailed info](/mods/md-files)
 * `support.md` - Free-form info about how to show support to the developer of the mod; [see detailed info](/mods/md-files)

# Build

Now, to build your mod you have a few options:

If youre using an IDE such as Clion, VScode or Visual Studio, head over to the [IDE Setup](/getting-started/ide-setup) page.

If you're building for Android, check out the [Android section](#build-for-android).

Otherwise if you want to build your mods manually from the command line you can do that by simply running these commands in your mod's folder:
```bash
# Configures & builds for the current platform
geode build
```

> Check out `geode build --help` for other options!

If you have an issue running that command for whatever reason ([do let us know!](https://github.com/geode-sdk/cli/issues)), you can build your mod the same way using these commands:
```bash
# Configure CMake
cmake -B build

# Build the project
cmake --build build --config RelWithDebInfo
```

If you [created a profile in CLI](/getting-started/geode-cli), then the mod should be automatically installed to GD. If not, then the built `your.mod.geode` package should be in your build folder, from where you can manually install it in-game.

## Build for Android

To build mods for Android you must install the [Android NDK](https://developer.android.com/ndk/downloads). Extract it somewhere and set the `ANDROID_NDK_ROOT` enviroment variable to its path.

On **Windows** you must also install [Ninja](https://github.com/ninja-build/ninja/releases). If you have Scoop, you can do this via `scoop install ninja`.

Now you can build your mod for Android via:
```bash
geode build -p android64
# Or if you're using a 32 bit phone
geode build -p android32
```

You can then copy the built .geode file from the `build-android64` folder to your phone at this location:
```
/storage/emulated/0/Android/media/com.geode.launcher/game/geode/mods/
```

## Building Windows mods on Linux

If you have followed the steps earlier and installed all the required tools with `geode sdk install-linux`, building should be as simple as on Windows:

```bash
geode build
```

If you have installed the Windows SDK and the toolchain in a different way, you will have to provide paths to them manually:

```bash
geode build -- -DCMAKE_TOOLCHAIN_FILE=/path/to/clang-msvc-sdk/clang-msvc.cmake -DSPLAT_DIR=/path/to/splat
```
