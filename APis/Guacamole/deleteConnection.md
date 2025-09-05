---
title: deleteConnection

---

### Delete Connection Configuration

Deletes a connection configuration from Guacamole. The user can only delete connections they created. A SuperAdmin can delete any connection.

**Req**
```
DELETE /api/v1/guacamole/deleteConnection
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's or SuperAdmin's session Bearer token. |

**Request Body**
| Name            | Type   | Description                |
| :-------------- | :----- | :------------------------- |
| `connection_id` | string | **Required.** The Guacamole connection configuration ID (e.g., from the `list connections` endpoint). |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "Connection deleted successfully",
  "data": {
    "connection_id": "123",
    "name": "SSH-VM-debian-user@example.com",
    "deleted_at": "2025-09-01T13:00:00.000Z",
    "deleted_by": "user@example.com"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

```json
{ "code": 400, "message": "Connection ID is required", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>

```json
{ "code": 403, "message": "You don't have permission to delete this connection", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

```json
{ "code": 404, "message": "Connection not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>

Also supports `401 Unauthorized`, `500 Internal Server Error`, and `503 Service Unavailable`.
</details>