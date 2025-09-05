---
title: getDatacenterStatus

---

### Get Datacenter Status

Retrieves a comprehensive overview of the entire Proxmox VE datacenter, including aggregated resource usage and the status of individual nodes. Requires **SuperAdmin** privileges.

**Req**
```
GET /api/v1/pve/getDatacenterStatus
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - Datacenter status fetched successfully</summary>

```json
{
  "code": 200,
  "message": "Datacenter status fetched successfully",
  "data": {
    "overview": {
      "total_nodes": 2,
      "online_nodes": 2,
      "offline_nodes": 0
    },
    "datacenter": {
      "cpu_total": 16,
      "cpu_percent": 25,
      "memory_total_gb": 64,
      "memory_used_gb": 32,
      "memory_percent": 50,
      "storage_used_tb": 1.5,
      "storage_total_tb": 10.0,
      "storage_percent": 15
    },
    "nodes": [
      {
        "name": "pve-node-1",
        "online": true,
        "address": "192.168.1.10",
        "cpu_percent": 30,
        "memory_percent": 60,
        "uptime": {
          "days": 10,
          "hours": 5,
          "minutes": 30,
          "seconds": 15
        }
      },
      {
        "name": "pve-node-2",
        "online": true,
        "address": "192.168.1.11",
        "cpu_percent": 20,
        "memory_percent": 40,
        "uptime": {
          "days": 10,
          "hours": 5,
          "minutes": 28,
          "seconds": 45
        }
      }
    ]
  }
}
```
</details>

<details>
<summary><code>404 Not Found</code> - Nodes Not Found</summary>
Occurs if the PVE API call fails to return any node data.

```json
{
  "code": 404,
  "message": "Nodes not found",
  "data": null
}
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>

```json
{
  "code": 500,
  "message": "Internal Server Error",
  "data": null
}
```
</details>