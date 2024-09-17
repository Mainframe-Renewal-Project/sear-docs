---
layout: page
nav_exclude: true
---

![pyRACF Logo](/assets/images/logo.png)

&nbsp;

A standardized JSON interface for RACF that enables seemless exploitation by programming languages that have a foreign language interface for C/C++ and native JSON support.
{: .fs-6 .fw-300 }

&nbsp;

{: .development_status }
> _**RACFu** is currently in **Alpha**, meaning that some core functionality may still be missing, unstable, and or may still need more thorough testing._

&nbsp;

{: .experimental }
> _Functionality that is considered **Experimental** will be accompanied by this annotation. This means that the functionality is not tested and or is subject to major changes including even being removed entirely._

&nbsp;

{: .warning }
> * _RACFu encodes the data it passes to RACF in Code Page `IBM-1047`._
> * _If you are entering information with special or national characters, users viewing or altering this information from terminals using differnt or international codepages may see unexpected data._
> * _Please consult a list of invariant characters to use for such information if this applies to you._

## Dependencies

* z/OS **2.4** or higher.
* **R_SecMgtOper (IRRSMO00)**: Security Management Operations.
* **R_Admin (IRRSEQ00)**: RACF Administration API.

## Authorizations

The following authorizations are required in order exploit all of the functionality that RACFu provides.
* More details about the authorizations required for **IRRSMO00** can be found [here](https://www.ibm.com/docs/en/zos/3.1.0?topic=operations-racf-authorization).
* More details about the authorizations required for **IRRSEQ00** can be found [here](https://www.ibm.com/docs/en/zos/3.1.0?topic=api-racf-authorization).

&nbsp;

| **Access** | **General Resource Profile** | **Class** | **Functionality** |
| `READ` | `IRR.RADMIN.LISTUSER` | `FACILITY` | Extract **User Profiles** |
| `READ` | `IRR.RADMIN.LISTGRP` | `FACILITY` | Extract **Group Profiles** |
| `READ` | `IRR.RADMIN.RLIST` | `FACILITY` | Extract **General Resource Profiles** |
| `READ` | `IRR.RADMIN.LISTDSD` | `FACILITY` | Extract **Data Set Profiles** |
| `READ` | `IRR.RADMIN.SETROPTS.LIST` | `FACILITY` | List **Setropts** |
| `READ` | `IRR.IRRSMO00.PRECHECK` | `XFACILIT` | **Alter** Profiles |
| `UPDATE` | `<userid>.IRRSMO00` | `SURROGAT` | **Run RACF Commands as a Specific Userid** |

## Installation

&nbsp;

{: .note}
 > _RACFu will eventually be made available on [pypi.org](https://pypi.org/), but currently python wheel distributions for RACFu are only available for manual download and installation via GitHub._

 &nbsp;

{: .warning}
> _If you get the following error when trying to install pyRACF from GitHub using the provided commands, ensure that you have a `.curlrc` in your **Home Directory** that is configured to point to a **Trusted CA Certificate Bundle**._
>
> ###### CA Certificate Verification Failure
> ```console
>   % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
>                                  Dload  Upload   Total   Spent    Left  Speed
>   0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
> curl: (60) SSL certificate problem: unable to get local issuer certificate
> More details here: https://curl.haxx.se/docs/sslcerts.html
> 
> curl failed to verify the legitimacy of the server and therefore could not
> establish a secure connection to it. To learn more about this situation and
> how to fix it, please visit the web page mentioned above.
> ```
>
> ###### .curlrc
> ```properties
> capath=/path/to/my/trusted/ca/
> cacert=/path/to/my/trusted/ca/ca.pem
> ```

&nbsp;

[Download & Install From GitHub](https://github.com/ambitus/racfu/releases)

## Mission Statement

As automation becomes more and more prevalent, the need to manage the security environment programmaticaly increases. On z/OS that means managing a security product like the IBM **Resource Access Control Facility** _(RACF)_. RACF is the primary facility for managing identity, authority, and access control for z/OS. There are more than 50 callable services with assembler interfaces that are part of the RACF API. The complete set of interfaces can be found [here](http://publibz.boulder.ibm.com/epubs/pdf/ich2d112.pdf).

&nbsp;

While there are a number of languages that can be used to manage RACF, _(from low level lnaguages like Assembler to higher level languages like REXX)_, the need to be able to easily exploit RACF management functions using existing indurstry standard programming languages and even programming languages that don't exist yet is paramount. The RACFu project is focused on making RACF management functions available to all programming languages that have native JSON support and a foreign language interface for C/C++. This will make it easier to pivot to new tools and programming languages as technology, skills, and business needs continue to evolve in the forseeable future.

## Architecture

&nbsp;

{: .warning }
> _Just because a **Programming Language Exploiter** is shown on this architecture diagram does not mean that there is or will be an interface created, maintained, and distributed by the RACFu team for that programming language. The interfaces currently maintained and distributed by the RACFu team can be found [here](./interfaces/)._

&nbsp;

<pre class="mermaid">
  flowchart TD
    c(C/C++ Exploiter)-- JSON (ASCII) ---RACFu
    style c fill:#01559e,color:#fff,stroke:#01559e
    python(Python Exploiter)-- JSON (ASCII) ---RACFu
    style python fill:#ffcb3c,color:#000,stroke:#ffcb3c
    nodejs(Node.JS Exploiter)-- JSON (ASCII) ---RACFu
    style nodejs fill:#417e38,color:#fff,stroke:#417e38
    java(Java Exploiter)-- JSON (ASCII) ---RACFu
    style java fill:#ec2025,color:#fff,stroke:#ec2025
    subgraph C/C+
        RACFu(["RACFu (64-bit XPLINK ASCII)"])
        style RACFu fill:#0096ff,color:#fff,stroke:#0096ff
        RACFu --- Extract(Extract)
        RACFu --- Add(Add)
        RACFu --- Alter(Alter)
        RACFu --- Delete(Delete)
        Add-- XML (EBCDIC) ---IRRSMO00("IRRSMO00 (64-bit OSLINK EBCDIC)")
        Alter-- XML (EBCDIC) ---IRRSMO00
        Delete-- XML (EBCDIC) ---IRRSMO00
        style IRRSMO00 fill:#33a,color:#fff,stroke:#33a
    end
    subgraph HLASM
        Extract-- Binary (EBCDIC) ---IRRSEQ00("IRRSEQ00 (31-bit OSLINK EBCDIC)")
        IRRSMO00-- Binary (EBCDIC) ---IRRSEQ00
        style IRRSEQ00 fill:#33a,color:#fff,stroke:#33a
    end
    IRRSEQ00 --- SAF(SAF)
    SAF --- RACF[(RACF)]

</pre>
