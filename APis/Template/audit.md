---
title: audit

---

### Audit Submitted Template (SuperAdmin)

Approves or rejects a submitted template. If approved, the system clones the template and makes the clone public. Requires **SuperAdmin** privileges.

**Req**
```
POST /api/v1/template/audit
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Request Body**
| Name            | Type   | Description                |
| :-------------- | :----- | :------------------------- |
| `template_id`   | string | **Required.** The `_id` of the **submission record**, not the template itself. |
| `status`        | string | **Required.** The audit decision. Must be `approved` or `rejected`. |
| `reject_reason` | string | **Optional.** A reason for rejection. Required if `status` is `rejected`. |

**Resp**
<details>
<summary><code>200 OK</code> - Template audit status updated successfully</summary>
    
```json
{
  "code": 200,
  "message": "Template audit status updated successfully",
  "data": "60d0fe4f5311236168a109f1" // The submission record's ID
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Missing required fields: template_id, status"`
* `"Invalid status. Must be 'approved' or 'rejected'."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
    
Possible `message` values:
* `"Submitted template not found"`
* `"Original template not found for the approved submission"`
```json
{ "code": 404, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401/403 Unauthorized` and `500 Internal Server Error`.
</details>