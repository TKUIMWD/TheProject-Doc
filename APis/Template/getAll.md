---
title: getAll

---

### Get All Templates (SuperAdmin)

Retrieves a list of all VM templates in the system, regardless of ownership or status. Requires **SuperAdmin** privileges.

**Req**
```
GET /api/v1/template/getAll
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Templates fetched successfully</summary>

```json
{
  "code": 200,
  "message": "Templates fetched successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a109e1",
      "name": "ubuntu-22.04-base",
      "description": "A base image of Ubuntu 22.04 LTS.",
      "submitted_date": "2025-08-15T10:00:00.000Z",
      "owner": "60d0fe4f5311236168a109a1",
      "is_public": true,
      "default_cpu_cores": 2,
      "default_memory_size": 2048,
      "default_disk_size": 25,
      "submitter_user_info": {
        "username": "admin_user",
        "email": "admin@example.com"
      }
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