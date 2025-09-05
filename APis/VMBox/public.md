---
title: public

---

### Get All Public Boxes

Retrieves a list of all publicly available (approved) Boxes.

**Req**
```
GET /api/v1/vmbox/public
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Public boxes fetched successfully</summary>
    
```json
{
  "code": 200,
  "message": "Public boxes fetched successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a10b01",
      "name": "ubuntu-22.04-web-server",
      "description": "A ready-to-use web server environment.",
      "submitted_date": "2025-08-20T12:00:00.000Z",
      "owner": "60d0fe4f5311236168a10a0a",
      "default_cpu_cores": 2,
      "default_memory_size": 2048,
      "default_disk_size": 20,
      "is_public": true,
      "box_setup_description": "Contains Nginx, Node.js, and PM2.",
      "rating_score": 4.5,
      "review_count": 9,
      "updated_date": "2025-08-21T14:30:00.000Z"
    }
  ]
}
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>