---
title: getUserOwned

---

### Get User's Owned VMs

Retrieves a list of all VMs owned by the authenticated user.

**Req**
```
GET /api/v1/vm/getUserOwned
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - User VMs fetched successfully</summary>
The response format is the same as `getAll`, but the list is filtered to the current user and the `owner` field is omitted.

```json
{
  "code": 200,
  "message": "User VMs fetched successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a109e5",
      "pve_vmid": "101",
      "pve_node": "pve-node-1",
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