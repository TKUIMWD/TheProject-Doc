---
title: update

---

### Update Template Configuration

Updates the configuration of an existing template.
- The template **owner** or a **SuperAdmin** can modify the `description`, `template_name`, and Cloud-Init credentials.
- Only a **SuperAdmin** can modify the `is_public` status.

**Req**
```
POST /api/v1/template/manage/update
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's or SuperAdmin's session Bearer token. |

**Request Body**
| Name            | Type    | Description                |
| :-------------- | :------ | :------------------------- |
| `template_id`   | string  | **Required.** The ID of the template to update. |
| `description`   | string  | **Optional.** A new description for the template. |
| `is_public`     | boolean | **Optional.** Set to `true` or `false`. **SuperAdmin only**. |
| `template_name` | string  | **Optional.** A new name for the template in PVE. |
| `ciuser`        | string  | **Optional.** A new default cloud-init username. Must be provided with `cipassword`. |
| `cipassword`    | string  | **Optional.** A new default cloud-init password. Must be provided with `ciuser`. |

**Resp**
<details>
<summary><code>200 OK</code> - Template configuration updated successfully</summary>

```json
{
  "code": 200,
  "message": "Template configuration updated successfully",
  "data": "60d0fe4f5311236168a109e2" // The updated template's ID
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Missing required field: template_id"`
* `"Both ciuser and cipassword must be provided and non-empty"`
* `"Invalid template name: name contains invalid characters or is too long"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
    
Possible `message` values:
* `"Access denied: You don't have permission to update this template"`
* `"Access denied: Only superadmin can modify template public status"`
```json
{ "code": 403, "message": "...", "data": null }
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