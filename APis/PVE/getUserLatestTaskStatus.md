---
title: getUserLatestTaskStatus

---

### Get Latest Task Status for User

Retrieves the most recently created task for the authenticated user and its current status.

**Req**
```
GET /api/v1/pve/getUserLatestTaskStatus
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "Latest task status fetched successfully",
  "data": {
    "task_id": "task-xyz-789",
    "status": "IN_PROGRESS",
    "progress": 50,
    "pve_status": {
      "status": "running",
      "exitstatus": null
    }
  }
}
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "No tasks found for the user", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>