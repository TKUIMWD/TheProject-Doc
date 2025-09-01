---
title: ssh

---

### Establish SSH Connection

Creates a Guacamole SSH connection to a specified VM. Requires the user to have permission for the VM.

**Req**
```
POST /api/v1/guacamole/ssh
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Request Body**
| Name         | Type   | Description                |
| :----------- | :----- | :------------------------- |
| `vm_id`      | string | **Required.** The ID of the target VM. |
| `ip_address` | string | **Optional.** A specific IP address of the VM to connect to. If not provided, an IP will be auto-selected. |
| `username`   | string | **Optional.** The SSH username. |
| `password`   | string | **Optional.** The SSH password. |
| `port`       | number | **Optional.** The SSH port. Defaults to `22`. |

**Resp**
<details>
<summary><code>200 OK</code> - SSH connection established</summary>

```json
{
  "code": 200,
  "message": "SSH connection established",
  "data": {
    "connection_id": "ssh-60d...-167...",
    "protocol": "ssh",
    "status": "active",
    "created_at": "2025-09-01T12:08:38.000Z",
    "expires_at": "2025-09-01T16:08:38.000Z",
    "target_ip": "192.168.1.100",
    "available_ips": ["192.168.1.100", "10.0.0.5"],
    "direct_url": "[https://guacamole.example.com/#/client/c2...-...?token=ABCD](https://guacamole.example.com/#/client/c2...-...?token=ABCD)..."
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"VM ID is required"`
* `"VM is not running (current status: stopped)"`
* `"Unable to get or validate VM IP address"`
* `"Requested IP [ip] is not available for this VM. Available IPs: ..."`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>401 Unauthorized</code></summary>
```json
{ "code": 401, "message": "Authentication failed", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "You don't have permission to access this VM", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "VM not found", "data": null }
```
</details>

<details>
<summary><code>503 Service Unavailable</code></summary>
Possible `message` values:
* `"Guacamole service is not configured. Please contact administrator to configure the service."`
* `"Cannot establish SSH connection: ... . Please ensure SSH service is running on the target VM."`
```json
{ "code": 503, "message": "...", "data": null }
```
</details>