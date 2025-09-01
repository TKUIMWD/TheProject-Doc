---
title: getProfile

---

### Get User Profile

Retrieves the profile information (username, email, avatar) for the authenticated user.

**Req**
```
GET /api/v1/user/getProfile
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Profile retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "Profile retrieved successfully",
  "data": {
    "username": "JohnDoe",
    "email": "john.doe@example.com",
    "avatar_path": "/path/to/default/avatar.png"
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
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "user is not verified", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
```json
{ "code": 500, "message": "Internal server error", "data": null }
```
</details>