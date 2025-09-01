---
title: rdp

---

### Establish RDP Connection

Creates a Guacamole RDP connection to a specified VM. Requires the user to have permission for the VM.

**Req**
```
POST /api/v1/guacamole/rdp
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Request Body**
| Name         | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `vm_id`      | string | **Required.** The ID of the target VM. |
| `username`   | string | **Required.** The RDP username. |
| `password`   | string | **Required.** The RDP password. |
| `ip_address` | string | **Optional.** A specific IP address of the VM to connect to. |
| `port`       | number | **Optional.** The RDP port. Defaults to `3389`. |

**Resp**
<details>
<summary><code>200 OK</code> - RDP connection established</summary>

```json
{
  "code": 200,
  "message": "RDP connection established",
  "data": {
    "connection_id": "rdp-60d...-167...",
    "protocol": "rdp",
    "status": "active",
    "created_at": "2025-09-01T12:08:38.000Z",
    "expires_at": "2025-09-01T16:08:38.000Z",
    "target_ip": "192.168.1.101",
    "available_ips": ["192.168.1.101"],
    "direct_url": "[https://guacamole.example.com/#/client/c2...-...?token=ABCD](https://guacamole.example.com/#/client/c2...-...?token=ABCD)..."
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"VM ID is required"`
* `"Username and password are required for RDP connection"`
* `"VM is not running..."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>
<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, and `503 Service Unavailable` similar to the SSH endpoint.
</details>