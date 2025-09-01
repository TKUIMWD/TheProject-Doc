---
title: getQemuConfig

---

### Get QEMU VM Configuration

Retrieves the configuration of a specific QEMU virtual machine. The level of detail in the response depends on the user's role.

**Req**
```
GET /api/v1/pve/getQemuConfig
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Query Parameters**
| Name | Type   | Description                |
| :--- | :----- | :------------------------- |
| `id` | string | **Required.** The MongoDB `_id` of the VM record. |

**Resp**
<details>
<summary><code>200 OK</code> - Config fetched successfully</summary>
The structure of the `data` object varies by user role:
* **user:** Returns a `VMBasicConfig` with essential info.
* **admin:** Returns a `VMDetailedConfig` with more hardware details.
* **superadmin:** Returns the full, unfiltered config object from the PVE API.

```json
// Example for 'admin' role
{
  "code": 200,
  "message": "Detailed QEMU config fetched successfully",
  "data": {
    "vmid": 101,
    "name": "my-vm-name",
    "cores": 2,
    "memory": 4096,
    "node": "pve-node-1",
    "status": "running",
    "scsi0": "local-lvm:vm-101-disk-0,size=32G",
    "net0": "virtio=AA:BB:CC:DD:EE:FF,bridge=vmbr0",
    "bootdisk": "scsi0",
    "ostype": "l26",
    "disk_size": 32
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
```json
{ "code": 400, "message": "Missing vm_id in query parameters", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
Possible `message` values:
* `"Access denied: VM not owned by user"`
* `"Invalid role"`
```json
{ "code": 403, "message": "...", "data": null }
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