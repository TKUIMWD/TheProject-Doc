---
title: submissions

---

### Get All Submitted Boxes (SuperAdmin)

Retrieves a list of all Box submissions for review. Requires **SuperAdmin** privileges.

**Req**
```
GET /api/v1/vmbox/submissions
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Submitted boxes fetched successfully</summary>
    
```json
{
  "code": 200,
  "message": "Submitted boxes fetched successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a10a01",
      "vmtemplate_id": "60d0fe4f5311236168a109e1",
      "box_setup_description": "A box for learning basic linux commands.",
      "submitted_date": "2025-09-02T10:00:00.000Z",
      "status": "not_approved",
      "submitter_info": {
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