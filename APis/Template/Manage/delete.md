---
title: delete

---

### Delete Template

Permanently deletes a template from both PVE and the database. This action reclaims the compute resources used by the template. Can only be performed by the template **owner** or a **SuperAdmin**.

**Req**
```
DELETE /api/v1/template/manage/delete
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's or SuperAdmin's session Bearer token. |

**Request Body**
| Name          | Type   | Description                |
| :------------ | :----- | :------------------------- |
| `template_id` | string | **Required.** The ID of the template to delete. |

**Resp**
<details>
<summary><code>200 OK</code> - Template deleted successfully</summary>

```json
{
  "code": 200,
  "message": "Template deleted successfully",
  "data": "60d0fe4f5311236168a109e2" // The deleted template's ID
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
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "Access denied: You don't have permission to delete this template", "data": null }
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
Also supports `401 Unauthorized` and `500 Internal Server Error` for PVE API failures.
</details>