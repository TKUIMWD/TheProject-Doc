---
title: update

---

### Update Compute Resource Plan

Updates an existing Compute Resource Plan by its ID. This is a PUT operation, but the service logic allows for partial updates. Can only be performed by a **SuperAdmin**.

**Req**
```
PUT /api/v1/superadmin/crp/update/:crpId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Path Parameters**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `crpId` | string | **Required.** The ID of the CRP to update. |

**Request Body**
Any field from the Compute Resource Plan can be included for update. All fields are **optional**.

| Name        | Type    | Description                |
| :---------- | :------ | :------------------------- |
| `name`      | string  | **Optional.** A new unique name for the plan. |
| `vcpu`      | number  | **Optional.** A new value for vCPU cores. |
| `ram_mb`    | number  | **Optional.** A new value for RAM in MB. |
| `disk_gb`   | number  | **Optional.** A new value for disk space in GB. |
| `price_per_hour` | number | **Optional.** A new hourly cost. |

**Resp**
<details>
<summary><code>200 OK</code> - CRP updated successfully</summary>

```json
{
  "code": 200,
  "message": "CRP updated successfully",
  "data": {
    "_id": "60d0fe4f5311236168a109d1",
    "name": "Pro Plus",
    "vcpu": 8,
    "ram_mb": 16384,
    "disk_gb": 100,
    "price_per_hour": 7.0
  }
}
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
    
```json
{ "code": 404, "message": "Not Found: CRP not found", "data": null }
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401/403 Unauthorized` and `500 Internal Server Error`.
</details>