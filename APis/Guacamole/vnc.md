---
title: vnc

---

### Establish VNC Connection

Creates a Guacamole VNC connection to a specified VM. Requires the user to have permission for the VM.

**Req**
```
POST /api/v1/guacamole/vnc
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Request Body**
| Name         | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `vm_id`      | string | **Required.** The ID of the target VM. |
| `password`   | string | **Optional.** The VNC password. |
| `ip_address` | string | **Optional.** A specific IP address of the VM to connect to. |
| `port`       | number | **Optional.** The VNC port. Defaults to `5900`. |

**Resp**
<details>
<summary><code>200 OK</code> - VNC connection established</summary>

```json
{
  "code": 200,
  "message": "VNC connection established",
  "data": {
    "connection_id": "vnc-60d...-167...",
    "protocol": "vnc",
    "status": "active",
    "created_at": "2025-09-01T12:08:38.000Z",
    "expires_at": "2025-09-01T16:08:38.000Z",
    "target_ip": "192.168.1.102",
    "available_ips": ["192.168.1.102"],
    "direct_url": "[https://guacamole.example.com/#/client/c2...-...?token=ABCD](https://guacamole.example.com/#/client/c2...-...?token=ABCD)..."
  }
}
```
</details>
<details>
<summary>Error Responses</summary>

Supports `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, and `503 Service Unavailable` similar to the SSH endpoint.
</details>