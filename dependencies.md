---
layout: default
has_children: false
has_toc: false
---

# Dependencies

{: .warning }

> Just because a new version of z/OS or Python is not mentioned does not mean it won't be supported in future versions

This page documents all dependencies required to use SEAR, not what is required to build SEAR. If you're looking for the required authorizations to use SEAR [see the authorizations page](./authorizations.md).

## Supported z/OS versions

- z/OS 2.5
- z/OS 3.1
- z/OS 3.2

Some extra PTFs are required for z/OS 2.5 and 3.1, otherwise you will get errors like this:

```sh
CEE3501S The module CRTEQCXH was not found
```

SEAR uses C++17 and requires fairly modern LE runtimes, this is why these PTFs are required on older z/OS versions.

### PTFs required for z/OS 2.5

- PH45536, PH45538, PH45672 (UI80156)
- PH60053 (UI95832)
- PH41221 (UI78912)
- PH53938 (UI94524)

### PTFs required for z/OS 3.1

- PH60056(UI95833)
- PH53938(UI94523)

## RACF sub-system address space

The RACF sub-system user needs a valid OMVS segment with a UID. The default group of the RACF sub-system user also needs an OMVS segment with a GID.

If your RACF sub-system does not have a user assigned to it then it must be created, [review the IBM documentation for more details](https://www.ibm.com/docs/en/zos/latest?topic=subsystem-activating-racf).

## Supported Python versions

You can acquire Python from your z/OS install as bypassable requisite or grab it from the IBM website. Python versions not mentioned in the table below are not officially supported.

| SEAR version | Py 3.12     | Py 3.13     | Py 3.14     |
|--------------|-------------|-------------|-------------|
| 0.4.0        |   ✅        |    ✅       |    ❌       |
| 0.3.1        |   ✅        |    ✅       |    ❌       |
| 0.3.0        |   ✅        |    ✅       |    ❌       |
| 0.2.1        |   ❌        |    ✅       |    ❌       |
| 0.2.0        |   ❌        |    ✅       |    ❌       |
| 0.1.2        |   ❌        |    ✅       |    ❌       |
| 0.1.1        |   ❌        |    ✅       |    ❌       |
| 0.1.0        |   ❌        |    ✅       |    ❌       |

It may be possible to build SEAR yourself for older or newer versions of Python than the ones supported, but we will not guarantee it works.
