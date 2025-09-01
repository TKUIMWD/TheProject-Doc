---
title: submit

---

### Submit Template for Approval

Submits a user-owned template for SuperAdmin review to potentially make it public. Requires **admin** or **superadmin** privileges.

**Req**
```
POST /api/v1/template/submit
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The admin's or superadmin's session Bearer token. |

**Request Body**
| Name          | Type   | Description                |
| :------------ | :----- | :------------------------- |
| `template_id` | string | **Required.** The MongoDB `_id` of the template to submit for review. |

**Resp**
<details>
<summary><code>200 OK</code> - Template submitted successfully</summary>

```json
{
  "code": 200,
  "message": "Template submitted successfully",
  "data": "60d0fe4f5311236168a109e2" // The submitted template's ID
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
```json
{ "code": 400, "message": "Missing required field: template_id", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "Template not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>