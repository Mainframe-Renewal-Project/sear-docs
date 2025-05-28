---
layout: default
---

# Building from source

This page covers dependencies and the process of building SEAR from source.

## Dependencies

### zOpen

SEAR requires several things included with [zOpen](https://zopen.community/#/):

- make (the one IBM provides will cause the process to fail)
- cmake
- OpenSSL (necessary because of the certificate support)

This list will expand in the future as more language interfaces get added.

### IBM

SEAR requires the following products from IBM:

- RACF
- z/OS 2.5 or later
- [OpenXLC 2.1](https://www.ibm.com/products/xl-cpp-compiler-zos) or later (1.1 won't work)
- [Python](https://www.ibm.com/products/open-enterprise-python-zos) (3.13 or later)

This list will expand in the future as more language interfaces get added.

## Build process

Alternatively to installing from Pip, _SEAR_ can be built from source on a z/OS system. _SEAR_ uses a CMake build system, and can be built via a two-step process.

First pull down SEAR

```shell
git clone https://github.com/Mainframe-Renewal-Project/sear.git
```

secondly, configure the build environment:

```shell
cmake -S . -B build --toolchain cmake/ibm-clang.cmake
```

This will generate the build environment in a directory named `build`. Then the project can be built:

```shell
cmake --build build
```

To build the python module use:

```shell
python -m build
```

Build artifacts are located within the build directory.
