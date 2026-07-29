---
layout: default
has_toc: false
parent: JavaScript
---


# Resource profiles

{: .warning }

> Please note JavaScript support is exclusive to SEAR 0.7.0 and later.

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ✅    |
| alter    | ✅    |
| delete   | ✅    |
| extract  | ✅    |
| search   | ✅    |

</div>

## Extracting information

SEAR provides the `extract` and `search` operators to gather information about general resource profiles.

### Extracting a specific resource profile

The sample below extracts information about a specific resource profile.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "extract",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class_name": "facility",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

#### Returned result

<details>

```javascript
{
  "profile": {
    "base": {
      "base:alter_access_count": 0,
      "base:auditing": "FAILURES(READ)",
      "base:control_access_count": 0,
      "base:create_date": "12/20/23",
      "base:global_auditing": "NONE",
      "base:last_change_date": "12/20/23",
      "base:last_reference_date": "12/20/23",
      "base:level": "0",
      "base:owner": "ESWIFT",
      "base:read_access_count": 0,
      "base:universal_access": "READ",
      "base:update_access_count": 0,
      "base:warn_on_insufficient_access": false
    }
  },
  "return_codes": {
    "racf_reason_code": 0,
    "racf_return_code": 0,
    "saf_return_code": 0,
    "sear_return_code": 0
  }
}
```

</details>

### Searching for resource profiles

#### Getting a list of all resource profiles in a class

The sample below gets all general resource profiles in the facility class.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "search",
    "admin_type": "resource",
    "class_name": "facility",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

#### Filtering results

The sample below gets all general resource profiles that start with `IRR` in the `facility` class. It will return a list of resource profiles, to get metadata on them you will have to run the extract operation on every single resource profile in the list.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "search",
    "admin_type": "resource",
    "class_name": "facility",
    "resource_filter": "IRR",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

## Updating resource profiles

SEAR provides 3 main operators for updating the RACF database, `add`, `alter`, and `delete`.

### Creating a new resource profile

The sample below creates a resource profile called `IRR.RADMIN.**` in the `facility` class with a UACC of NONE and the owner set to the "eswift" RACF userid.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "add",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class_name": "facility",
    "traits": {
        "base:universal_access": "None",
        "base:owner": "SECADM",
    },
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

You can see the full list of traits in [the traits/resource section](https://mainframe-renewal-project.github.io/sear-docs/traits/resource/)

### Altering a resource profile

The sample below sets SECADM as the owner of the `IRR.RADMIN.**` resource profile in the `facility` class and sets UACC to "read"

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "alter",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class_name": "facility",
    "traits": {
        "base:universal_access": "Read",
        "base:owner": "SECADM",
    },
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

You can see the full list of traits in [the traits/resource section](https://mainframe-renewal-project.github.io/sear-docs/traits/resource/)

### Deleting a resource profile

The sample below deletes the `IRR.RADMIN.**` resource profile in the `facility` class.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "delete",
    "admin_type": "resource",
    "resource": "IRR.RADMIN.**",
    "class_name": "facility",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```
