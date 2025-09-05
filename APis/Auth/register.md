---
title: register

---

### Register a New User

**Req**
```
POST /api/v1/auth/register
```

**Request Body**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `username` | string | **Required.** The user's desired username. |
| `email`    | string | **Required.** The user's email address. |
| `password` | string | **Required.** The user's password. It must meet strength requirements. |

**Resp**
<details>
<summary><code>200 OK</code> - User registered successfully</summary>

```json
{
  "code": 200,
  "message": "user registered successfully",
  "data": null
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Invalid input or user exists</summary>

Possible `message` values:
* `"missing required fields: username, email, password"`
* `"email already exists but not verified , please verify your email"`
* `"cannot register"` (username or verified email already exists)
* `"password does not meet the requirements: ..."`
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

Possible `message` values:
* `"Default compute resource plan not available"`
* `"internal server error"`

```json
{
  "code": 500,
  "message": "...",
  "data": null
}
```
</details>