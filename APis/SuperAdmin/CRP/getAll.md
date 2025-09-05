---
title: getAll

---

### Get All Compute Resource Plans

Retrieves a list of all available Compute Resource Plans. Can only be performed by a **SuperAdmin**.

**Req**
```
GET /api/v1/superadmin/crp/getAll
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - CRPs retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "CRPs retrieved successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a109d0",
      "name": "Standard",
      "vcpu": 2,
      "ram_mb": 4096,
      "disk_gb": 50,
      "price_per_hour": 2.5
    },
    {
      "_id": "60d0fe4f5311236168a109d1",
      "name": "Pro",
      "vcpu": 4,
      "ram_mb": 8192,
      "disk_gb": 100,
      "price_per_hour": 5.5
    }
  ]
}
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401/403 Unauthorized` and `500 Internal Server Error`.
</details>