---
title: deleteAvatar

---

### Delete Avatar

Deletes the user's custom avatar and resets it to the default image.

**Req**
```
DELETE /api/v1/user/deleteAvatar
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Avatar deleted successfully</summary>
    
```json
{
  "code": 200,
  "message": "Avatar deleted successfully",
  "data": {
    "username": "JohnDoe",
    "email": "john.doe@example.com",
    "avatar_path": "/path/to/default/avatar.png"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
```json
{ "code": 400, "message": "no custom avatar to delete", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized`, `403 Forbidden` (for unverified users), and `500 Internal Server Error`.
</details>