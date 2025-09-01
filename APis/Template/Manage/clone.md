---
title: clone

---

### Clone Template

Creates a new, private template by cloning an existing one. This is an asynchronous operation that returns a task ID for tracking. Requires **SuperAdmin** privileges.

**Req**
```
POST /api/v1/template/manage/clone
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Request Body**
| Name                | Type   | Description                |
| :------------------ | :----- | :------------------------- |
| `template_id`       | string | **Required.** The ID of the source template to clone. |
| `new_template_name` | string | **Required.** A name for the new cloned template. |
| `description`       | string | **Required.** A description for the new template. |
| `target_node`       | string | **Optional.** The PVE node to clone to. Defaults to the source node. |
| `storage`           | string | **Optional.** The PVE storage to use. Defaults to "NFS". |

**Resp**
<details>
<summary><code>200 OK</code> - Template cloned successfully</summary>
This response indicates the cloning process has started. The status should be tracked using the returned `task_id`.

```json
{
  "code": 200,
  "message": "Template cloned successfully",
  "data": {
    "template_id": "60d0fe4f5311236168a109e3",
    "task_id": "clone-template-60d...-167..."
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"Missing required fields: template_id, new_template_name, description"`
* `"Invalid template name: ..."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "Source template not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401/403 Unauthorized` and `500 Internal Server Error` for PVE API or task creation failures.
</details>