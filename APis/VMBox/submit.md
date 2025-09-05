---
title: submit

---

### Submit a Box for Approval

Submits a new Box for SuperAdmin review. Requires **admin** privileges.

**Req**
```
POST /api/v1/vmbox/submit
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The admin's session Bearer token. |

**Request Body**
| Name                    | Type                  | Description                |
| :---------------------- | :-------------------- | :------------------------- |
| `vmtemplate_id`         | string                | **Required.** The ID of the base VM template for this Box. |
| `box_setup_description` | string                | **Required.** A description of the Box's setup and purpose. |
| `flag_answers`          | Record<string, string>| **Optional.** An object containing flag IDs as keys and their correct answers as values. |

**Resp**
<details>
<summary><code>200 OK</code> - Box submission created successfully</summary>

```json
{
  "code": 200,
  "message": "Box submission created successfully, waiting for approval",
  "data": {
    "submission_id": "60d0fe4f5311236168a10a01",
    "vmtemplate_id": "60d0fe4f5311236168a109e1",
    "submitted_date": "2025-09-02T10:00:00.000Z",
    "submitter": "admin@example.com"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Missing Fields</summary>
    
```json
{ "code": 400, "message": "Missing required fields: vmtemplate_id, box_setup_description", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401/403 Unauthorized` and `500 Internal Server Error`.
</details>