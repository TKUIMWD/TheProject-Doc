---
title: convert

---

### Convert VM to Template

Converts an existing, stopped VM owned by the user into a private template. The original VM record is deleted.

**Req**
```
POST /api/v1/template/convert
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name            | Type   | Description                |
| :-------------- | :----- | :------------------------- |
| `vm_id`         | string | **Required.** The MongoDB `_id` of the VM to convert. |
| `ciuser`        | string | **Required.** The default cloud-init username for the template. |
| `cipassword`    | string | **Required.** The default cloud-init password for the template. |
| `description`   | string | **Required.** A description for the new template. |
| `template_name` | string | **Optional.** A specific name for the template in PVE. |

**Resp**
<details>
<summary><code>200 OK</code> - VM successfully converted to template</summary>

```json
{
  "code": 200,
  "message": "VM successfully converted to template",
  "data": "60d0fe4f5311236168a109e2" // The new template's ID
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Missing required fields: vm_id, ciuser, cipassword, description"`
* `"CI validation failed: ..."`
* `"VM must be stopped before converting to template"`
* `"Invalid template name: ..."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
    
```json
{ "code": 404, "message": "VM not found or you don't have permission to convert this VM", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>