# Geode Доксы

### [Посетить сайт Геода](https://docs.geode-sdk.org)

Это исходный код для Geode доксов, содержащие все вручную написанные туториалы.

"Классы и функции" документация к ним построенна автоматически из [Geode исходный код](https://github.com/geode-sdk/geode).

## Building

The docs are built using [Flash](https://github.com/hjfod/flash). To build the docs, you need Flash, along with [CMake](https://cmake.org/install/) and [Clang](https://clang.llvm.org/).

To build the docs, you first need to clone Geode, and then clone the docs inside the Geode root, for a folder structure like this:

```
geode/
    docs/
        <docs files>
    <geode files>
```

For example, you can do this with the following commands:

```
git clone https://github.com/geode-sdk/geode
cd geode
git clone https://github.com/geode-sdk/docs
```

Alternatively, you can symlink your local copy of the docs folder to your local copy of the Geode folder.

After building Flash from source using Cargo or installing the latest release, you can build the docs with the following command:

```
flash -i <path/to/geode> -o <relative_output_dir> --overwrite
```

Afterwards, start up a local HTTP server in the folder where you ran Flash.

You should run Flash in the directory you want to build the docs in and use `-o .`, or run it in the parent directory and do `-o <output_dir_name>`.
