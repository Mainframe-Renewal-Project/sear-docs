---
layout: default
has_toc: false
parent: JavaScript
---


# Permits

{: .warning }

> Please note JavaScript support is exclusive to SEAR 0.7.0 and later.

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ❌    |
| alter    | ✅    |
| delete   | ✅    |
| extract  | ❌    |
| search   | ❌    |

</div>

## Creating permits

Unlike with most of the other `admin_types` you can only use `alter` and `delete` to modify permits in the RACF database, `alter` is not just used to alter permits but also create them.

### Dataset permits

The sample below gives a permit of READ to the `MATRIX.SECRETS.**` dataset profile for the user `LEONARD`.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "alter",
    "admin_type": "permission",
    "dataset": "MATRIX.SECRETS.**",
    "volume": "MYVOL",
    "generic": true,
    "userid": "LEONARD",
    "traits": {
        "base:access": "READ",
    },
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

You can see the full list of traits in [the traits/permission section](https://mainframe-renewal-project.github.io/sear-docs/traits/permission/)

### Resource permits

The sample below gives a permit of READ to the `IRR.IRRSMO00.PRECHECK` in the `XFACILIT` class to the user `FDEGILIO`.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "alter",
    "admin_type": "permission",
    "resource": "IRR.IRRSMO00.PRECHECK",
    "class": "XFACILIT",
    "userid": "FDEGILIO",
    "traits": {
        "base:access": "READ",
    },
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

You can see the full list of traits in [the traits/permission section](https://mainframe-renewal-project.github.io/sear-docs/traits/permission/)

## Deleting permits

The sample below removes `FDEGILIO`'s permit from the access list of `IRR.IRRSMO00.PRECHECK` in the `XFACILIT` class.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "delete",
    "admin_type": "permission",
    "resource": "IRR.IRRSMO00.PRECHECK",
    "class": "XFACILIT",
    "userid": "FDEGILIO",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```
