---
title: getMultipleTasksStatus

---

### Get Status of Multiple Tasks

Retrieves the current status of multiple tasks by their IDs. Only tasks belonging to the authenticated user will be returned.

**Req**
```
POST /api/v1/pve/getMultipleTasksStatus
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name       | Type     | Description                |
| :--------- | :------- | :------------------------- |
| `task_ids` | string[] | **Required.** A non-empty array of task IDs to query. |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "Multiple tasks status fetched successfully",
  "data": [
    {
      "task_id": "task-abc-123",
      "status": "COMPLETED",
      "progress": 100,
      "pve_status": {
        "status": "stopped",
        "exitstatus": "OK"
      }
    }
  ]
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

```json
{ "code": 400, "message": "task_ids must be a non-empty array", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>

Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>