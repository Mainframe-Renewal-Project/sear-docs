---
layout: default
has_toc: false
parent: JavaScript
---


# Groups

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

SEAR provides the `extract` and `search` operators to gather information about groups.

### Extracting a specific RACF group

Below you can find a sample of some code that extracts information about the RACF group `DEV`.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
  "operation": "extract",
  "admin_type": "group",
  "group": "DEV",
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
      "base:connected_users": [
        {
          "base:connected_user_authority": "USE",
          "base:connected_userid": "ESWIFT"
        }
      ],
      "base:create_date": "10/11/23",
      "base:owner": "ESWIFT",
      "base:superior_group": "SYS1",
      "base:terminal_universal_access": true,
      "base:universal": false
    },
    "omvs": {
      "omvs:gid": 24
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

### Searching for RACF group

#### Getting a list of all groups

The sample below returns a list of all RACF groups on the system.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
  "operation": "search",
  "admin_type": "group",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

#### Filtering group results

The sample below gets all groups that start with `SYS`. It will return a list of groups, to get metadata on them you will have to run the extract operation on every single RACF group in the list.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
  "operation": "search",
  "admin_type": "group",
  "group_filter": "SYS",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

## Updating RACF groups

SEAR provides 3 main operators for updating the RACF database, `add`, `alter`, and `delete`.

### Creating a new RACF group

The sample below creates a group called `SYSPROG` with the gid a of 6667.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
  "operation": "add",
  "admin_type": "group",
  "group": "SYSPROG",
  "traits": {
    "omvs:gid": 6667,
  },
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

You can see the full list of traits in [the traits/group section](https://mainframe-renewal-project.github.io/sear-docs/traits/group/)

### Altering a RACF group

The sample below changes the `SYSPROG` RACF group to have a gid of 1234567.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
  "operation": "alter",
  "admin_type": "group",
  "group": "SYSPROG",
  "traits": {
    "omvs:gid": 1234567,
  },
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```

You can see the full list of traits in [the traits/group section](https://mainframe-renewal-project.github.io/sear-docs/traits/group/)

### Deleting a RACF group

The below sample deletes the RACF group `DEVOPS`.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
  "operation": "delete",
  "admin_type": "group",
  "group": "DEVOPS",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```
