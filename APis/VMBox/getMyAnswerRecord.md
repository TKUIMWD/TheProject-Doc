---
title: getMyAnswerRecord

---

### Get My Answer Record

For a VM created from a Box, retrieves the authenticated user's answer status (correct/incorrect) for each flag within that Box.

**Req**
```
GET /api/v1/vmbox/getMyAnswerRecord
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Query Parameters**
| Name    | Type   | Description                |
| :------ | :----- | :------------------------- |
| `vm_id` | string | **Required.** The MongoDB `_id` of the user's VM instance. |

**Resp**
<details>
<summary><code>200 OK</code> - Answer record fetched successfully</summary>
The `answer_record` object contains keys for each flag ID in the Box. The value is `true` if the user has answered correctly, and `false` otherwise.

```json
{
  "code": 200,
  "message": "Answer record fetched successfully",
  "data": {
    "answer_record": {
      "flag1_intro_to_linux": true,
      "flag2_file_permissions": false,
      "flag3_ssh_basics": false
    }
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Missing or Invalid Parameter</summary>
Occurs if the `vm_id` is not provided in the query string or is not a valid format.

```json
{
  "code": 400,
  "message": "Missing or invalid required parameter: vm_id",
  "data": null
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - VM is not from a Box</summary>
Occurs if the specified VM was not created from a Box and therefore has no flags to answer.

```json
{
  "code": 400,
  "message": "This VM is not created from a box",
  "data": null
}
```
</details>

<details>
<summary><code>401 Unauthorized</code> - Invalid Token</summary>
Occurs if the JWT token is missing, invalid, or expired.

```json
{
  "code": 401,
  "message": "invalid or expired token",
  "data": null
}
```
</details>

<details>
<summary><code>403 Forbidden</code> - Permission Denied</summary>
Occurs if the authenticated user is not the owner of the specified VM.

```json
{
  "code": 403,
  "message": "You do not have permission to access this VM",
  "data": null
}
```
</details>

<details>
<summary><code>404 Not Found</code> - VM Not Found</summary>
Occurs if no VM record with the given `vm_id` exists in the database.

```json
{
  "code": 404,
  "message": "VM not found",
  "data": null
}
```
</details>

<details>
<summary><code>404 Not Found</code> - Box Not Found</summary>
Occurs if the VM record exists but the associated Box record has been deleted.

```json
{
  "code": 404,
  "message": "Box not found",
  "data": null
}
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
A generic error for any other unexpected issues on the server.

```json
{
  "code": 500,
  "message": "Internal Server Error",
  "data": null
}
```
</details>