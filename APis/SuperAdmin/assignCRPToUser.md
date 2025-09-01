---
title: assignCRPToUser

---

### Assign Compute Resource Plan to User

Assigns a specific Compute Resource Plan (CRP) to a user. This action can only be performed by a **SuperAdmin**.

**Req**
```
PUT /api/v1/superadmin/assignCRPToUser
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Request Body**
| Name     | Type   | Description                |
| :------- | :----- | :------------------------- |
| `userId` | string | **Required.** The ID of the target user. |
| `planId` | string | **Required.** The ID of the Compute Resource Plan to assign. |

**Resp**
<details>
<summary><code>200 OK</code> - CRP assigned to user successfully</summary>

```json
{
  "code": 200,
  "message": "CRP assigned to user successfully",
  "data": {
    "user": "JohnDoe",
    "role": "user",
    "planId": "60d0fe4f5311236168a109d0"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"Missing 'userId' field"`
* `"Missing 'planId' field"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>401 Unauthorized</code></summary>
```json
{ "code": 401, "message": "Unauthorized: Invalid token", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "Forbidden: requires superadmin role", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
Possible `message` values:
* `"Target user not found"`
* `"Compute Resource Plan not found"`
```json
{ "code": 404, "message": "...", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
```json
{ "code": 500, "message": "Internal Server Error: ...", "data": null }
```
</details>