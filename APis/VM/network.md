---
title: network

---

### Get VM Network Info

Retrieves network interface details for a specific **running** VM via the QEMU Guest Agent. A SuperAdmin can query any VM, while a standard user can only query their own.

**Req**
```
GET /api/v1/vm/network
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's or SuperAdmin's session Bearer token. |

**Query Parameters**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `vm_id` | string | **Required.** The MongoDB `_id` of the VM. |

**Resp**
<details>
<summary><code>200 OK</code> - VM network information retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "VM network information retrieved successfully",
  "data": {
    "interfaces": [
      {
        "name": "ens18",
        "macAddress": "AA:BB:CC:DD:EE:FF",
        "ipAddresses": [
          "192.168.1.100"
        ]
      }
    ]
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"VM ID is required"`
* `"VM must be running to get network information"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, and `500 Internal Server Error`.
</details>