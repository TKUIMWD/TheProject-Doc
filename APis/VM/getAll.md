---
title: getAll

---

### Get All VMs (SuperAdmin)

Retrieves a list of all VMs in the system, along with their current status and owner information. Requires **SuperAdmin** privileges.

**Req**
```
GET /api/v1/vm/getAll
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - All VMs fetched successfully</summary>

```json
{
  "code": 200,
  "message": "All VMs fetched successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a109e5",
      "pve_vmid": "101",
      "pve_node": "pve-node-1",
      "owner": "JohnDoe",
      "status": {
        "current_status": "running",
        "uptime": 3600
      },
      "error": null
    }
  ]
}
```
</details>

<details>
<summary><code>401 Unauthorized / 403 Forbidden</code></summary>
    
```json
{ "code": 403, "message": "Forbidden: requires superadmin role", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
    
```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>