---
layout: default
has_toc: false
parent: JavaScript
---

# RRSF

{: .warning }

> Please note JavaScript support is exclusive to SEAR 0.7.0 and later.

{: .warning }

> Please note RRSF support is exclusive to SEAR 0.4.0 and later, earlier versions do not support this feature.

{: .warning }

> Be mindful of what you do with the RRSF extracted data, it contains many pieces of sensitive information about system layout and network configuration that can be abused by bad actors.

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ❌    |
| alter    | ❌    |
| delete   | ❌    |
| extract  | ✅    |
| search   | ❌    |

</div>

## Extracting information

SEAR provides the `extract` operator to gather information about the RRSF configuration.

### Extracting RACF RRSF options

The sample below returns all of the RRSF options.

```javascript
'use strict';

import { sear } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "extract",
    "admin_type": "racf-rrsf",
};

const response = sear(request, true);

console.log(JSON.stringify(response.result, null, 2));
```
