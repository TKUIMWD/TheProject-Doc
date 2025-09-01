---
title: getAccessable

---

### Get Accessable Templates

Retrieves a list of VM templates that are either public or owned by the authenticated user.

**Req**
```
GET /api/v1/template/getAccessable
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Approved templates fetched successfully</summary>
The response format is the same as `getAll`, but the list is filtered based on user permissions.
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