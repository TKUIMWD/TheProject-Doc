---
title: delete

---

### Delete VM

Permanently deletes a VM from PVE and the database. A standard user can only delete their own VMs, while a SuperAdmin can delete any VM.

**Req**
```
DELETE /api/v1/vm/manage/delete
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's or SuperAdmin's session Bearer token. |

**Request Body**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `vm_id` | string | **Required.** The MongoDB `_id` of the VM to delete. |

**Resp**
<details>
<summary><code>200 OK</code> - VM deletion completed successfully</summary>
The response may include a `task_id` if the deletion is an asynchronous PVE task.

```json
{
  "code": 200,
  "message": "VM deletion completed successfully",
  "data": {
    "vm_id": "60d0fe4f5311236168a109e5",
    "pve_vmid": "101",
    "pve_node": "pve-node-1",
    "message": "VM deletion task completed successfully",
    "task_id": "UPID:pve-node-1:..."
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
```json
{ "code": 400, "message": "vm_id is required and must be a string", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "Access denied: VM not owned by user", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "VM not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized` and `500 Internal Server Error`.
</details>