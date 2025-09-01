---
title: getNodes

---

### Get PVE Nodes

Retrieves a list of all Proxmox VE nodes in the cluster. Requires **admin** privileges.

**Req**
```
GET /api/v1/pve/getNodes
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The admin's session Bearer token. e.g., `Bearer <token>` |

**Resp**
<details>
<summary><code>200 OK</code> - Nodes fetched successfully</summary>

```json
{
  "code": 200,
  "message": "Nodes fetched successfully",
  "data": [
    {
      "node": "pve-node-1",
      "ip": "192.168.1.10",
      "status": "online",
      "cpu": 0.15,
      "maxcpu": 8,
      "mem": 8589934592,
      "maxmem": 17179869184,
      "disk": 53687091200,
      "maxdisk": 107374182400
    }
  ]
}
```
</details>

<details>
<summary><code>401 Unauthorized</code></summary>
```json
{ "code": 401, "message": "invalid or expired token", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>