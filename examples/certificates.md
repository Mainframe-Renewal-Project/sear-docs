---
layout: default
has_toc: false
parent: Examples
---


# Certificates

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

Below you can find a sample of some code that adds a certficate to the `SEARTESTRING` keyring owned by `YBTKS`.

```python

from sear import sear

result = sear(
    {
        "operation": "add",
        "admin_type": "certificate",
        "owner": "YBTKS",
        "keyring": "SEARTESTRING",
        "keyring_owner": "YBTKS",
        "label": "NewTrustedCert",
        "certificate_file": "/tmp/newtrustedcert.pem",
        "usage": "personal",
        "status": "TRUST",
    },
)

print(result.result)
```

### Deleting a certificate from a keyring

Below you can find a sample of some code that deletes a certficate from the `SEARTESTRING` keyring owned by `YBTKS`.

```python

from sear import sear

result = sear(
    {
        "operation": "delete",
        "admin_type": "certificate",
        "owner": "YBTKS",
        "keyring": "SEARTESTRING",
        "keyring_owner": "YBTKS",
        "label": "NewTrustedCert",
    },
)

print(result.result)
```
