---
layout: default
has_toc: false
parent: Python
---


# Keyrings

Valid operators for this type of request

<div class="valid-operation-table" markdown="block">

| Operator | Valid |
|----------|-------|
| add      | ✅    |
| alter    | ❌    |
| delete   | ✅    |
| extract  | ✅    |
| search   | ❌    |

</div>

## Extracting information

SEAR provides the `extract` operators to gather information about certificates.

### Extracting a specific keyring

Below you can find a sample of some code that extracts information about the `SEARTESTRING` owned by `YBTKS`.

```python

from sear import sear

result = sear(
    {
        "operation": "extract",
        "admin_type": "keyring",
        "keyring": "SEARTESTRING",
        "owner": "YBTKS",
    },
)

print(result.result)
```

#### Returned result

<details>

```python
{
  "keyring": {
    "certificates": [
      {
        "DN": "/CN=SEAR TEST CERT",
        "default": "yes",
        "extensions": [
          {
            "critical": "yes",
            "name": "nsComment",
            "value": "Generated by the Security Server for z/OS (RACF)"
          },
          {
            "critical": "no",
            "name": "keyUsage",
            "usages": [
              "digitalSignature",
              "nonRepudiation",
              "keyEncipherment",
              "dataEncipherment"
            ]
          },
          {
            "critical": "yes",
            "name": "subjectKeyIdentifier",
            "value": "34:71:82:03:F0:08:4B:3C:78:54:FF:77:EE:9A:81:A4:2C:E1:1A:49"
          },
          {
            "critical": "yes",
            "name": "authorityKeyIdentifier",
            "value": "6A:22:36:02:E0:DF:95:54:23:1E:A1:6E:EC:4A:44:87:E9:BB:A1:CC"
          }
        ],
        "fingerprints": [
          {
            "sha256": "AB:11:7D:A9:8C:13:E6:52:41:21:44:02:BD:43:72:BE:B3:FB:67:13:FE:25:18:D5:01:2D:F9:3E:4A:50:C9:1C"
          },
          {
            "sha1": "C3:63:03:A4:B2:EB:A2:B7:AB:B3:35:A7:BB:0C:49:D3:4D:68:EB:D1"
          },
          {
            "md5": "1F:E8:9C:6E:00:65:FF:4E:D0:DF:54:40:3E:7C:A5:BB"
          }
        ],
        "issuer": "/CN=YIN CA 2024C",
        "keySize": 4096,
        "label": "SEARTESTCERT",
        "notAfter": "2034-05-19 21:59:59",
        "notBefore": "2025-05-18 22:00:00",
        "owner": "YBTKS",
        "privateKey": "yes",
        "serialNumber": "02",
        "signature": {
          "algorithm": "sha256WithRSAEncryption",
          "value": "11:53:CE:BC:65:31:A3:D1:54:C3:27:CA:3A:FE:2C:9E:43:1C:3B:53:5F:66:3F:DD:F7:44:0C:68:B3:F3:B7:A5:39:76:75:F6:8F:D6:9A:34:8E:D4:E8:F8:CA:65:A2:53:03:13:06:39:9B:B3:59:41:79:19:E0:37:22:BC:60:03:23:C7:90:17:72:45:BE:50:D0:F2:B7:08:FA:B7:67:63:66:3F:7B:F2:22:11:20:A5:72:E3:CB:5D:8B:48:54:77:B6:FF:7E:25:B1:ED:E0:57:2F:77:2A:1B:AC:81:0B:85:49:9C:FF:0E:04:EE:D6:AD:B0:F2:4C:80:66:3B:C1:23:C0:D4:BF:3E:67:AD:5B:B9:98:83:74:7F:7E:24:B8:09:82:DC:6D:7B:D4:B4:31:90:6B:45:C3:49:36:65:43:B7:19:F3:85:D0:B7:37:11:0F:82:BD:04:83:5E:A7:57:47:1A:E4:E9:D8:DE:66:13:F2:AA:EF:2D:5E:C9:48:9E:C5:D8:10:55:80:6E:55:13:47:89:9C:82:01:82:66:DC:76:CB:67:BB:7B:41:49:88:7A:1A:0E:66:81:D5:A9:1F:2E:C8:04:06:44:B7:61:A7:52:33:FC:F2:AD:C0:6B:FC:C6:26:9D:A6:1F:83:8B:8F:B2:19:9B:4D:95:35:F2:D8:80:21:BE:EB:73:62:54:61:79:46:03:BD:AA:27:8F:D0:DA:7F:AE:4C:69:E0:0F:39:2A:03:2E:37:BE:3E:64:AA:80:18:FE:BD:09:2E:7F:CB:82:5A:FA:7B:25:39:70:47:7A:96:71:D9:7F:E9:90:15:E7:7B:D1:6A:53:DF:FF:F5:AA:4C:D0:C2:E7:1B:67:DA:E9:F2:B5:64:ED:74:5D:FC:2B:98:D5:36:B5:A4:B5:47:2E:7E:FC:88:C7:AF:2F:88:7C:04:00:DD:AF:3C:9E:6F:C3:2E:34:F0:F3:92:12:6D:0F:8F:D5:ED:5F:78:46:B8:BC:B3:8A:E0:13:9E:3E:26:FE:E4:EA:C8:C0:5D:5C:C2:36:EF:44:C0:D0:45:98:ED:AA:10:92:C4:ED:1C:C4:CA:39:DC:DD:F3:B5:FB:2D:44:F0:EC:80:7C:CA:5E:0F:95:C9:C0:3D:06:32:A9:FC:65:DB:B9:56:46:AE:20:B3:B5:D0:E4:89:7B:E7:7F:66:9F:84:60:24:EB:92:BD:29:DD:DB:F7:B4:A9:C4:C0:66:88:E2:BC:10:D3:96:22:93:74:4E:0C:13:69:02:9A:A0:94:71:4E:51:8C:17:2A:89:9E:A9:C6:51:94:4E:6F:6D:5A:A7:8A:A5:52:58:C8:BE:A5:4B:A4:CE:58:F8:DF:E2:AC:64"
        },
        "status": "TRUST",
        "usage": "personal",
        "version": 3
      }
    ]
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

## Updating keyrings

SEAR provides two operators for working with certificates, `add` and `delete`.

### Creating a new keyring

Below you can find a sample of some code that adds a new keyring called `SEARTESTRING2` with `YBTKS` as the owner.

```python

from sear import sear

result = sear(
    {
        "operation": "add",
        "admin_type": "keyring",
        "keyring": "SEARTESTRING2",
        "owner": "YBTKS",
    },
)

print(result.result)
```

### Deleting a keyring

Below you can find a sample of some code that deletes the `SEARTESTRING2` keyring owned by `YBTKS`.

```python

from sear import sear

result = sear(
    {
        "operation": "delete",
        "admin_type": "keyring",
        "keyring": "SEARTESTRING2",
        "owner": "YBTKS",
    },
)

print(result.result)
```

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
