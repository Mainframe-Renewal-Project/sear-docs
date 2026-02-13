---
layout: default
parent: SEAR development
---

# Building the Python wheel

This page covers how to build the Python wheel yourself, rather than getting it from PyPi or GitHub. Building yourself can reduce risk of supply attacks and might be necessary depending on your organizational rules.

## Pre-requisites

The following software is needed to build:

- z/OS 2.5 or later
- [IBM OpenXL C/C++ 2.1](https://www.ibm.com/products/xl-cpp-compiler-zos) or later (1.1 won't work)
- [Python](https://www.ibm.com/products/open-enterprise-python-zos) 3.12, 3.13, or 3.14
  - setuptools and build packages
- [OpenSSL from zOpen](https://github.com/zopencommunity/opensslport)
- [zoslib from zOpen](https://github.com/zopencommunity/zoslibport)
- git (to clone the repository)

### Environment variables

There are 2 different ways of informing the build process where zoslib and openssl are located. The first is if you have done a full zOpen install, then you can use the ZOPEN_ROOTFS environment variable. If you have installed openssl and zoslib individually, i.e. in your home directory, then you can specify OPENSSL_ROOT and ZOSLIB_ROOT. If ZOPEN_ROOTFS is not specified then both OPENSSL_ROOT and ZOSLIB_ROOT must be set.

## Initiating the build process

First you will need to clone down the source code with git

```sh
git clone https://github.com/Mainframe-Renewal-Project/sear.git
```

Then you will want to create a Python virtual environment and install the `build` and `setuptools` packages in it.

```sh
pip install build && pip install setuptools
```

Once you have all the necessary tools do a git clone

```sh
python -m build
```

After the build process is done a wheel will appear in `./dist/`
