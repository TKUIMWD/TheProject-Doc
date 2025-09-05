---
title: updateConfig

---

### Update VM Configuration

Updates the configuration (CPU, memory, disk, etc.) of a **stopped** VM. This is an asynchronous operation that returns a task ID for tracking. The user must own the VM.

**Req**
```
POST /api/v1/vm/manage/updateConfig
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The VM owner's session Bearer token. |

**Request Body**
| Name         | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `vm_id`      | string | **Required.** The MongoDB `_id` of the VM to update. |
| `cpuCores`   | number | **Optional.** The new number of vCPU cores. |
| `memorySize` | number | **Optional.** The new amount of RAM in megabytes. |
| `diskSize`   | number | **Optional.** The new total disk size in gigabytes. **Cannot be decreased**. |
| `vmName`     | string | **Optional.** A new name for the VM. |
| `ciuser`     | string | **Optional.** A new cloud-init username. Must be provided with `cipassword`. |
| `cipassword` | string | **Optional.** A new cloud-init password. Must be provided with `ciuser`. |

**Resp**
<details>
<summary><code>200 OK</code> - VM configuration update started</summary>

```json
{
  "code": 200,
  "message": "VM configuration updated successfully",
  "data": {
    "task_id": "update-60d...-167...",
    "vm_id": "60d0fe4f5311236168a109e5",
    "pve_vmid": "101",
    "updated_config": {
      "cpu_cores": 4,
      "memory_size": 4096,
      "disk_size": 50
    }
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"vm_id is required"`
* `"At least one configuration parameter must be provided..."`
* `"VM must be stopped before updating configuration..."`
* `"Disk size reduction is not supported"`
* `"Requested resource increases exceed the available limits..."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, and `500 Internal Server Error`.
</details>