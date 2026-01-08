---
layout: default
parent: SEAR development
---

# Building the Python wheel

This page covers how to build the Python wheel yourself, rather than getting it from PyPi or GitHub. Building yourself can reduce risk of supply attacks and might be necessary depending on your organizational rules.

## Pre-requisites

The following software is needed to build:

- z/OS 2.5 or later
- OpenXL C/C++ 2.1 (needed to get clang on z/OS)
- Python 3.12, 3.13, or 3.14
  - setuptools and build packages
- OpenSSL from zOpen
- zoslib from zOpen
- git (to clone the repository)

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
