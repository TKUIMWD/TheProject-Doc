---
title: audit

---

### Audit Box Submission (SuperAdmin)

Approves or rejects a submitted Box. If approved, a new public VMBox record is created. Requires **SuperAdmin** privileges.

**Req**
```
POST /api/v1/vmbox/audit
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Request Body**
| Name            | Type   | Description                |
| :-------------- | :----- | :------------------------- |
| `submission_id` | string | **Required.** The ID of the submission record to audit. |
| `status`        | string | **Required.** The audit decision. Must be `approved` or `rejected`. |
| `reject_reason` | string | **Optional.** A reason for rejection. Required if `status` is `rejected`. |

**Resp**
<details>
<summary><code>200 OK</code> - Box audit status updated successfully</summary>
    
```json
{
  "code": 200,
  "message": "Box audit status updated successfully",
  "data": "60d0fe4f5311236168a10a01" // The submission record's ID
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Missing required fields: box_id, status"`
* `"Invalid status. Must be 'approved' or 'rejected'."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code> - Submission Not Found</summary>
    
```json
{ "code": 404, "message": "Submitted box not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401/403 Unauthorized` and `500 Internal Server Error`.
</details>