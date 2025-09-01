---
title: cleanupTasks

---

### Cleanup Old Tasks

Deletes task records older than 30 days from the database. This is an administrative action. Requires **SuperAdmin** privileges.

**Req**
```
POST /api/v1/pve/cleanupTasks
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "Task cleanup completed",
  "data": {
    "totalTasks": 50,
    "tasksByStatus": [
      { "_id": "COMPLETED", "count": 45 },
      { "_id": "FAILED", "count": 5 }
    ]
  }
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