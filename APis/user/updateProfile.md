---
title: updateProfile

---

### Update User Profile

Updates the username for the authenticated user.

**Req**
```
PUT /api/v1/user/updateProfile
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `username` | string | **Required.** The new, unique username. |

**Resp**
<details>
<summary><code>200 OK</code> - Profile updated successfully</summary>

```json
{
  "code": 200,
  "message": "Profile updated successfully",
  "data": {
    "username": "NewJohnDoe",
    "email": "john.doe@example.com",
    "avatar_path": "/path/to/default/avatar.png"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"missing required field: username"`
* `"unable to update profile"` (Username is already taken)
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>