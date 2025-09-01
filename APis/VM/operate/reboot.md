---
title: reboot

---

### Reboot VM

Gracefully reboots a running VM. This is an asynchronous operation that returns a PVE task ID (UPID).

**Req**
```
POST /api/v1/vm/operate/reboot
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The VM owner's session Bearer token. |

**Request Body**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `vm_id` | string | **Required.** The MongoDB `_id` of the VM to reboot. |

**Resp**
<details>
<summary><code>200 OK</code> - VM rebooted successfully</summary>
```json
{
  "code": 200,
  "message": "VM rebooted successfully",
  "data": {
    "upid": "UPID:pve-node-1:000ABCDE:..."
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"VM ID is required"`
* `"VM must be running to reboot"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
Also supports `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, and `500 Internal Server Error`.
</details>