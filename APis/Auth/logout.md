---
title: logout

---

### User Logout

This endpoint is protected and requires a valid session token. In practice, this invalidates the token on the server-side if using a session store, or relies on client-side token deletion for stateless JWT.

**Req**
```
POST /api/v1/auth/logout
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Resp**
<details>
<summary><code>200 OK</code> - Logout successful</summary>

This response is returned even if the token was already invalid.

```json
{
  "code": 200,
  "message": "logout successful",
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