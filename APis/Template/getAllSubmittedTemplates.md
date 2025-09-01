---
title: getAllSubmittedTemplates

---

### Get All Submitted Templates (SuperAdmin)

Retrieves a list of all templates submitted for review. Requires **SuperAdmin** privileges.

**Req**
```
GET /api/v1/template/getAllSubmittedTemplates
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Submitted templates retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "Submitted templates retrieved successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a109f1",
      "status": "not_approved",
      "template_id": "60d0fe4f5311236168a109e2",
      "submitter_user_id": "60d0fe4f5311236168a109a2",
      "submitted_date": "2025-09-01T21:00:00.000Z",
      "template_name": "ubuntu-22.04-docker",
      "template_description": "Ubuntu with Docker pre-installed.",
      "owner": "admin_user",
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
<summary>Other Error Responses</summary>
Also supports `401/403 Unauthorized` and `500 Internal Server Error`.
</details>