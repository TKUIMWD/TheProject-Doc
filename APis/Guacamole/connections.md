---
title: connections

---

### List User Connections

Lists all connection configurations created by the current user in Guacamole.

**Req**
```
GET /api/v1/guacamole/connections
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "Found 2 connections",
  "data": [
    {
      "connection_id": "123",
      "name": "SSH-VM-debian-user@example.com",
      "protocol": "ssh",
      "parameters": {
        "hostname": "192.168.1.100",
        "port": "22",
        "username": "root"
      },
      "created_at": "2025-09-01T12:08:38.000Z",
      "status": "active"
    }
  ]
}
```
</details>

<details>
<summary>Other Error Responses</summary>

Also supports `401 Unauthorized`, `500 Internal Server Error`, and `503 Service Unavailable`.
</details>