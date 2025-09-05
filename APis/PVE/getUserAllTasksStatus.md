---
title: getUserAllTasksStatus

---

### Get All Tasks for a User

Retrieves a paginated list of all tasks initiated by the authenticated user.

**Req**
```
GET /api/v1/pve/getUserAllTasksStatus
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Query Parameters**
| Name     | Type   | Description                |
| :------- | :----- | :------------------------- |
| `page`   | number | **Optional.** The page number to retrieve. Defaults to `1`. |
| `limit`  | number | **Optional.** The number of items per page. Defaults to `10`. |
| `status` | string | **Optional.** Filter tasks by a specific status (e.g., `COMPLETED`, `FAILED`). |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "User tasks status fetched successfully",
  "data": {
    "tasks": [
      {
        "task_id": "task-abc-123",
        "status": "COMPLETED",
        "progress": 100
      }
    ],
    "pagination": {
      "page": 1,
      "limit": 10,
      "total": 1,
      "totalPages": 1
    }
  }
}
```
</details>

<details>
<summary>Other Error Responses</summary>

Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>