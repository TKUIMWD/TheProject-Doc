---
title: createFromBoxTemplate

---

### Create VM From Box Template

Creates a new VM by cloning a template specified within a "Box". A Box is a predefined configuration that simplifies VM creation. This is an asynchronous operation that returns a task ID for tracking.

**Req**
```
POST /api/v1/vm/manage/createFromBoxTemplate
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name         | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `box_id`     | string | **Required.** The ID of the source Box. |
| `name`       | string | **Required.** A name for the new VM. |
| `target`     | string | **Required.** The target PVE node to create the VM on. |
| `cpuCores`   | number | **Required.** The number of vCPU cores. |
| `memorySize` | number | **Required.** The amount of RAM in megabytes. |
| `diskSize`   | number | **Required.** The total disk size in gigabytes. |
| `storage`    | string | **Optional.** The PVE storage ID. Defaults to "NFS". |

**Resp**
<details>
<summary><code>200 OK</code> - VM creation process started</summary>
The `task_id` can be used to track the creation progress.

```json
{
  "code": 200,
  "message": "VM created and configured successfully",
  "data": {
    "task_id": "clone-60d...-167...",
    "vm_name": "my-new-vm-from-box",
    "vmid": "106"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Invalid VM name. Name must contain only alphanumeric characters, hyphens, and dots..."`
* `"Requested resources exceed the per VM limits of your compute resource plan"`
* `"Requested resources exceed the available limits of your compute resource plan"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
    
```json
{
  "code": 403,
  "message": "You do not have permission to use this template",
  "data": null
}
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
    
Possible `message` values:
* `"Box not found"`
* `"Template not found"`
* `"Compute resource plan not found"`
```json
{ "code": 404, "message": "...", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
    
Possible `message` values:
* `"Failed to clone VM from template"`
* `"VM created but configuration failed, resources have been cleaned up"`
```json
{ "code": 500, "message": "...", "data": null }
```
</details>