---
title: boot

---

### Boot VM

Starts a stopped VM. This is an asynchronous operation that returns a PVE task ID (UPID) for tracking.

**Req**
```
POST /api/v1/vm/operate/boot
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The VM owner's session Bearer token. |

**Request Body**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `vm_id` | string | **Required.** The MongoDB `_id` of the VM to start. |

**Resp**
<details>
<summary><code>200 OK</code> - VM started successfully</summary>
The `upid` can be used to track the task's progress.

```json
{
  "code": 200,
  "message": "VM started successfully",
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
* `"VM is already running"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
    
```json
{ "code": 403, "message": "You don't have permission to operate this VM", "data": null }
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