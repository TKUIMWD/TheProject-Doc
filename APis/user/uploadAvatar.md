---
title: uploadAvatar

---

### Upload Avatar

Uploads a new avatar image for the user. This endpoint expects `multipart/form-data`.

**Req**
```
POST /api/v1/user/uploadAvatar
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |
| `Content-Type`  | `multipart/form-data` |

**Form Data**
| Name      | Type | Description                |
| :-------- | :--- | :------------------------- |
| `avatar`  | File | **Required.** The image file to upload (e.g., JPEG, PNG). Max size: 2MB. |

**Resp**
<details>
<summary><code>200 OK</code> - Avatar uploaded successfully</summary>

```json
{
  "code": 200,
  "message": "Avatar uploaded successfully",
  "data": {
    "username": "JohnDoe",
    "email": "john.doe@example.com",
    "avatar_path": "/uploads/avatars/avatar-167...-unique.webp"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"no file uploaded"`
* `"File too large"` (From multer middleware)
* `"Invalid file type"` (From multer middleware)
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized`, `403 Forbidden` (for unverified users), and `500 Internal Server Error`.
</details>