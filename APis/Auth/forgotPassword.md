---
title: forgotPassword

---

### Initiate Password Reset

This endpoint sends a password reset link to the user's email address.

**Req**
```
POST /api/v1/auth/forgotPassword
```

**Request Body**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `email` | string | **Required.** The user's email address. |

**Resp**
<details>
<summary><code>200 OK</code> - Email sent (or simulated)</summary>
To prevent user enumeration, this endpoint returns a success message even if the email doesn't exist in the database.

Possible `message` values:
* `"If the email exists, a password reset email has been sent"`
* `"password reset email sent"`

```json
{
  "code": 200,
  "message": "...",
  "data": null
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Missing field or rate-limited</summary>

Possible `message` values:
* `"missing email field"`
* `"please wait X minute(s) before resending the verification email"`

```json
{
  "code": 400,
  "message": "...",
  "data": null
}
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>

```json
{
  "code": 500,
  "message": "internal server error",
  "data": null
}
```
</details>



---


### Complete Password Reset

This endpoint sets a new password using a valid reset token.

**Req**
```
PUT /api/v1/auth/forgotPassword
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The password reset Bearer token. e.g., `Bearer <reset_token>` |

**Request Body**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `password` | string | **Required.** The user's new password. Must meet strength requirements. |

**Resp**
<details>
<summary><code>200 OK</code> - Password reset successful</summary>

```json
{
  "code": 200,
  "message": "password reset successful",
  "data": null
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Missing field or weak password</summary>
Possible `message` values:
* `"missing password field"`
* `"password does not meet the requirements: ..."`

```json
{
  "code": 400,
  "message": "...",
  "data": null
}
```
</details>

<details>
<summary><code>401 Unauthorized</code> - Invalid or expired token</summary>

```json
{
  "code": 401,
  "message": "invalid or expired token",
  "data": null
}
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>

```json
{
  "code": 500,
  "message": "internal server error",
  "data": null
}
```
</details>