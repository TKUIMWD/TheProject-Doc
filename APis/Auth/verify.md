---
title: verify

---

### Verify User Account

This endpoint verifies the user's email using a token sent to them.

**Req**
```
POST /api/v1/auth/verify
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The Bearer token for verification. e.g., `Bearer <token>` |

**Resp**
<details>
<summary><code>200 OK</code> - Verification successful</summary>

```json
{
  "code": 200,
  "message": "email verified successfully",
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