---
title: delete

---

### Delete Compute Resource Plan

Deletes a Compute Resource Plan by its ID. Can only be performed by a **SuperAdmin**.

**Req**
```
DELETE /api/v1/superadmin/crp/delete/:crpId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The SuperAdmin's session Bearer token. |

**Path Parameters**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `crpId` | string | **Required.** The ID of the CRP to delete. |

**Resp**
<details>
<summary><code>200 OK</code> - CRP deleted successfully</summary>

```json
{
  "code": 200,
  "message": "CRP deleted successfully",
  "data": null
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