---
layout: default
parent: SEAR development
---

# Building from source

This page covers dependencies and the process of building SEAR from source.

## Dependencies

### zOpen

SEAR requires several things included with [zOpen](https://zopen.community/#/):

- make (the one IBM provides will cause the process to fail)
- cmake
- OpenSSL from zOpen (necessary because of the certificate support)
- zoslib from zOpen

This list will expand in the future as more language interfaces get added.

### IBM

SEAR requires the following products from IBM:

- RACF
- z/OS 2.5 or later
- [IBM OpenXL C/C++ 2.1](https://www.ibm.com/products/xl-cpp-compiler-zos) or later (1.1 won't work)
- [Python](https://www.ibm.com/products/open-enterprise-python-zos) (3.12 or later)

This list will expand in the future as more language interfaces get added.

## Build process

Alternatively to installing from Pip, _SEAR_ can be built from source on a z/OS system. _SEAR_ uses a CMake build system, and can be built via a two-step process.

First pull down SEAR

```shell
git clone https://github.com/Mainframe-Renewal-Project/sear.git
```

```shell
cmake --preset <preset>
cmake --build --preset <preset> --target <sear,pysear>
```

The first command will configure the build environment and generate build scripts in a directory named `build/<preset>`, then the second command builds the given target.

A complete list of available CMake presets can be found in [CMakePresets.json](CMakePresets.json), but the most useful are:

* `default` - Does not apply any special platform handling, and should work on most platforms.

* `zos` - Applies the `cmake/ibm-clang.cmake` toolchain to the build process. This compiles the project using the IBM-Clang compiler, and works only on z/OS systems.

* `zos-pysear` - Inherits from the `zos` preset. Used internally as part of the Python package build process, and not generally used by hand.

Build artifacts are located within the build directory.

The CMake build process builds static libraries by default. If you instead wish to build shared libraries, append `-DBUILD_SHARED_LIBS=on` to the CMake configure step command (the first of the two) shown above.

Build artifacts are located within the build directory.
