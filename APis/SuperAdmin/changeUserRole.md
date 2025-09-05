---
title: changeUserRole

---

### Change User Role

Updates a specified user's role. This action can only be performed by a **SuperAdmin**. The target user's role cannot be `superadmin`.

**Req**
```
PUT /api/v1/superadmin/changeUserRole
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Request Body**
| Name      | Type   | Description                |
| :-------- | :----- | :------------------------- |
| `userId`  | string | **Required.** The ID of the target user. |
| `newRole` | string | **Required.** The new role to assign. Must be `user` or `admin`. |

**Resp**
<details>
<summary><code>200 OK</code> - User role updated successfully</summary>

```json
{
  "code": 200,
  "message": "User role updated successfully",
  "data": null
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Missing 'userId' field"`
* `"Invalid or missing 'newRole' field. Can only be 'user' or 'admin'."`
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
    
Possible `message` values:
* `"Forbidden: requires superadmin role"`
* `"Cannot change role of a superadmin"`
```json
{ "code": 403, "message": "...", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
    
```json
{ "code": 404, "message": "Target user not found", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
    
```json
{ "code": 500, "message": "Internal Server Error: ...", "data": null }
```
</details>