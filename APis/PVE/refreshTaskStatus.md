---
title: refreshTaskStatus

---

### Refresh Task Status

Fetches the latest status of a single task from PVE and updates the local database record.

**Req**
```
POST /api/v1/pve/refreshTaskStatus
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name      | Type   | Description                |
| :-------- | :----- | :------------------------- |
| `task_id` | string | **Required.** The ID of the task to refresh. |

**Resp**
<details>
<summary><code>200 OK</code></summary>
```json
{
  "code": 200,
  "message": "Task status refreshed successfully",
  "data": {
    "task_id": "task-abc-123",
    "status": "COMPLETED",
    "progress": 100,
    "pve_status": {
      "status": "stopped",
      "exitstatus": "OK"
    }
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

```json
{ "code": 400, "message": "task_id is required", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

```json
{ "code": 404, "message": "Task not found or access denied", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>

Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>