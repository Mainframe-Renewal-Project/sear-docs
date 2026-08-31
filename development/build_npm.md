---
layout: default
parent: SEAR development
---

# Building the JavaScript package

This page covers how to build the JavaScript package for SEAR from source.

## Pre-requisites

The following software is needed to build:

- z/OS 2.5 or later
- [IBM OpenXL C/C++ 2.1](https://www.ibm.com/products/xl-cpp-compiler-zos) or later (1.1 won't work).
- [Node.js](https://www.ibm.com/products/sdk-nodejs-compiler-zos) 20 or later.
- [OpenSSL from zOpen](https://github.com/zopencommunity/opensslport).
  - SEAR 0.6.x and below are only compatible with OpenSSL 3.x.x, not 4.x.x. SEAR 0.7.0 and above requires OpenSSL 4.x.x.
- [zoslib from zOpen](https://github.com/zopencommunity/zoslibport)
- [git](https://www.ibm.com/products/open-enterprise-foundation-zos) (to clone the repository).

### Environment variables

There are 2 different ways of informing the build process where zoslib and OpenSSL are located. The first is if you have done a full zOpen install, then you can use the ZOPEN_ROOTFS environment variable. If you have installed OpenSSL and zoslib individually, i.e. in your home directory, then you can specify OPENSSL_ROOT and ZOSLIB_ROOT. If ZOPEN_ROOTFS is not specified then both OPENSSL_ROOT and ZOSLIB_ROOT must be set.

If using the user installation method you can put zoslib and OpenSSL in a folder in your z/OS Unix home directory. Then in your .zprofile or .profile point the to the relevant folders:

```sh
# SEAR dependencies
OPENSSL_ROOT = /home/<your RACF id>/software/openssl
ZOSLIB_ROOT = /home/<your RACF id>/software/zoslib
```

Make sure Node.js is installed and available in your path. You can check this by running `node -v` in a shell, which should return the version of Node.js installed.

## Initiating the build process

First you will need to clone down the source code with git

```sh
git clone https://github.com/Mainframe-Renewal-Project/sear.git
```

```sh
npm run build
```
