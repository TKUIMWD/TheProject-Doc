---
title: pending

---

### Get Pending Boxes (SuperAdmin)

Retrieves a list of all Boxes that are pending approval. Requires **SuperAdmin** privileges.

**Req**
```
GET /api/v1/vmbox/pending
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Pending boxes fetched successfully</summary>

```json
{
  "code": 200,
  "message": "Pending boxes fetched successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a10a01",
      "name": "ubuntu-22.04-docker",
      "description": "Ubuntu with Docker pre-installed.",
      "submitted_date": "2025-09-02T10:00:00.000Z",
      "owner": "60d0fe4f5311236168a10a0a",
      "default_cpu_cores": 2,
      "default_memory_size": 2048,
      "default_disk_size": 30,
      "is_public": false,
      "box_setup_description": "A box for learning Docker basics.",
      "updated_date": "2025-09-02T10:00:00.000Z",
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
<summary><code>200 OK</code> - No pending boxes found</summary>

```json
{
  "code": 200,
  "message": "No pending boxes found",
  "data": []
}
```
</details>
    
<details>
<summary><code>500 Internal Server Error</code></summary>
    
```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>