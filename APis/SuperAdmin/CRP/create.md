---
title: create

---

### Create Compute Resource Plan

Creates a new Compute Resource Plan (CRP). This action can only be performed by a **SuperAdmin**.

**Req**
```
POST /api/v1/superadmin/crp/create
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Request Body**
| Name        | Type    | Description                |
| :---------- | :------ | :------------------------- |
| `name`      | string  | **Required.** The unique name of the plan (e.g., "Standard", "Pro"). |
| `vcpu`      | number  | **Required.** The number of virtual CPU cores. |
| `ram_mb`    | number  | **Required.** The amount of RAM in megabytes. |
| `disk_gb`   | number  | **Required.** The amount of disk space in gigabytes. |
| `price_per_hour` | number | **Required.** The hourly cost of the plan. |

**Resp**
<details>
<summary><code>201 Created</code> - CRP created successfully</summary>

```json
{
  "code": 201,
  "message": "CRP created successfully",
  "data": {
    "name": "Pro",
    "vcpu": 4,
    "ram_mb": 8192,
    "disk_gb": 100,
    "price_per_hour": 5.5,
    "_id": "60d0fe4f5311236168a109d1",
    "createdAt": "2025-09-01T20:21:17.000Z",
    "updatedAt": "2025-09-01T20:21:17.000Z"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
```json
{ "code": 400, "message": "Bad Request: Missing required field 'name'", "data": null }
```
</details>

<details>
<summary><code>401 Unauthorized / 403 Forbidden</code></summary>
    
```json
{ "code": 403, "message": "Forbidden: requires superadmin role", "data": null }
```
</details>

<details>
<summary><code>409 Conflict</code></summary>
    
```json
{ "code": 409, "message": "Conflict: CRP with name \"Pro\" already exists", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
    
```json
{ "code": 500, "message": "Internal Server Error: ...", "data": null }
```
</details>