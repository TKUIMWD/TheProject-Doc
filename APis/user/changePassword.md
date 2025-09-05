---
title: changePassword

---

### Change Password

Allows an authenticated user to change their password.

**Req**
```
PUT /api/v1/user/changePassword
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name              | Type   | Description                |
| :---------------- | :----- | :------------------------- |
| `oldPassword`     | string | **Required.** The user's current password. |
| `newPassword`     | string | **Required.** The new password. Must meet strength requirements. |
| `confirmPassword` | string | **Required.** Must match `newPassword`. |

**Resp**
<details>
<summary><code>200 OK</code> - Password changed successfully</summary>
    
```json
{ "code": 200, "message": "Password changed successfully", "data": null }
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"missing required fields: ..."`
* `"newPassword and confirmPassword do not match"`
* `"oldPassword is incorrect"`
* `"password does not meet the requirements: ..."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized`, `403 Forbidden` (for unverified users), and `500 Internal Server Error`.
</details>