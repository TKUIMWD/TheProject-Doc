---
title: status

---

### Get VM Status

Retrieves the real-time status and resource usage of a specific VM. A SuperAdmin can query any VM, while a standard user can only query their own.

**Req**
```
GET /api/v1/vm/status
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's or SuperAdmin's session Bearer token. |

**Query Parameters**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `vm_id` | string | **Required.** The MongoDB `_id` of the VM. |

**Resp**
<details>
<summary><code>200 OK</code> - VM status retrieved successfully</summary>
The `resourceUsage` object is only included if the VM status is `running`.

```json
{
  "code": 200,
  "message": "VM status retrieved successfully",
  "data": {
    "status": "running",
    "uptime": 3600,
    "resourceUsage": {
      "cpu": 0.25,
      "memory": 2.5
    }
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
```json
{ "code": 400, "message": "VM ID is required", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "You don't have permission to access this VM", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "VM not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>