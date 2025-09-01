---
title: createFromTemplate

---

### Create VM From Template

Creates a new VM by cloning an existing template. This is an asynchronous operation that returns a task ID for tracking the creation and configuration process.

**Req**
```
POST /api/v1/vm/manage/createFromTemplate
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name          | Type   | Description                |
| :------------ | :----- | :------------------------- |
| `template_id` | string | **Required.** The ID of the source template. |
| `name`        | string | **Required.** A name for the new VM. |
| `target`      | string | **Required.** The target PVE node to create the VM on. |
| `cpuCores`    | number | **Required.** The number of vCPU cores. |
| `memorySize`  | number | **Required.** The amount of RAM in megabytes. |
| `diskSize`    | number | **Required.** The total disk size in gigabytes. |
| `storage`     | string | **Optional.** The PVE storage ID. Defaults to "NFS". |
| `ciuser`      | string | **Optional.** Overrides the template's default cloud-init username. |
| `cipassword`  | string | **Optional.** Overrides the template's default cloud-init password. |

**Resp**
<details>
<summary><code>200 OK</code> - VM creation process started</summary>

```json
{
  "code": 200,
  "message": "VM created and configured successfully",
  "data": {
    "task_id": "clone-60d...-167...",
    "vm_name": "my-new-vm",
    "vmid": "105"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"Missing required fields: ..."`
* `"Invalid VM name: ..."`
* `"Requested resources exceed the per VM limits of your compute resource plan"`
* `"Requested resources exceed the available limits of your compute resource plan"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "You do not have permission to use this template", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
Possible `message` values:
* `"Template not found"`
* `"Compute resource plan not found"`
```json
{ "code": 404, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized` and `500 Internal Server Error` for PVE API or task creation failures.
</details>