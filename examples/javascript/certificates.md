---
layout: default
has_toc: false
parent: JavaScript
---


# Certificates

{: .warning }

> Please note JavaScript support is exclusive to SEAR 0.7.0 and later.

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ✅    |
| alter    | ❌    |
| delete   | ✅    |
| extract  | ❌    |
| search   | ❌    |

</div>

## Updating certificates

### Adding a certificate to a keyring

Below you can find a sample of some code that adds a certificate to the `SEARTESTRING` keyring owned by `YBTKS`.

```javascript
'use strict';

import { sear, type SearRequest } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "add",
    "admin_type": "certificate",
    "owner": "YBTKS",
    "keyring": "SEARTESTRING",
    "keyring_owner": "YBTKS",
    "label": "NewTrustedCert",
    "certificate_file": "/tmp/newtrustedcert.pem",
    "usage": "personal",
    "status": "TRUST",
};

// Call SEAR
const response = sear(request, true);

// Print result
console.log(JSON.stringify(response.result, null, 2));
```

### Deleting a certificate from a keyring

Below you can find a sample of some code that deletes a certificate from the `SEARTESTRING` keyring owned by `YBTKS`.

```javascript
'use strict';

import { sear, type SearRequest } from '@mainframe-renewal-project/searjs';

const request = {
    "operation": "delete",
    "admin_type": "certificate",
    "owner": "YBTKS",
    "keyring": "SEARTESTRING",
    "keyring_owner": "YBTKS",
    "label": "NewTrustedCert",
};

// Call SEAR
const response = sear(request, true);

// Print result
console.log(JSON.stringify(response.result, null, 2));
```
