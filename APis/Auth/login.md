---
title: login

---

### User Login

**Req**
```
POST /api/v1/auth/login
```

**Request Body**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `email`    | string | **Required.** The user's email address. |
| `password` | string | **Required.** The user's password. |

**Resp**
<details>
<summary><code>200 OK</code> - Login successful</summary>

```json
{
  "code": 200,
  "message": "login successful",
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Invalid credentials or state</summary>

Possible `message` values:
* `"missing required fields: email, password"`
* `"invalid email or password"`
* `"user is locked, please wait X minute(s) until the lock is lifted"`
* `"email not verified, please verify your email"`
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