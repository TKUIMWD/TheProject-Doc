---
title: submitBoxAnswer

---

### Submit Box Answer

Submits an answer for a specific flag within a VM instance of a Box and checks if it is correct.

**Req**
```
POST /api/v1/vmbox/submitBoxAnswer
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name          | Type   | Description                |
| :------------ | :----- | :------------------------- |
| `vm_id`       | string | **Required.** The ID of the user's VM instance. |
| `flag_id`     | string | **Required.** The ID of the flag being answered (e.g., "flag1_intro_to_linux"). |
| `flag_answer` | string | **Required.** The user's submitted answer for the flag. |

**Resp**
<details>
<summary><code>200 OK</code> - Correct Answer</summary>
    
Returned when the submitted `flag_answer` is correct for the given `flag_id`.

```json
{
  "code": 200,
  "message": "Correct answer!",
  "data": {
    "flag_id": "flag1_intro_to_linux",
    "correct": true
  }
}
```
</details>

<details>
<summary><code>200 OK</code> - Incorrect Answer</summary>
    
Returned when the submitted `flag_answer` is incorrect.

```json
{
  "code": 200,
  "message": "Incorrect answer.",
  "data": {
    "flag_id": "flag1_intro_to_linux",
    "correct": false
  }
}
```
</details>

<details>
<summary><code>200 OK</code> - Flag Already Answered</summary>
    
Returned if the user tries to submit an answer for a flag they have already answered correctly.

```json
{
  "code": 200,
  "message": "Flag already answered correctly",
  "data": {
    "flag_id": "flag1_intro_to_linux",
    "correct": true
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Invalid Parameters</summary>
    
Possible `message` values:
* `"Missing or invalid required parameters: vm_id, flag_id, flag_answer"`
* `"This VM is not created from a box"`
* `"Invalid flag_id or this box does not have the specified flag"`

```json
{
  "code": 400,
  "message": "...",
  "data": null
}
```
</details>

<details>
<summary><code>401 Unauthorized</code> - Invalid Token</summary>

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

```json
{
  "code": 403,
  "message": "You do not have permission to access this VM",
  "data": null
}
```
</details>

<details>
<summary><code>404 Not Found</code> - Not Found</summary>
    
Possible `message` values:
* `"VM not found"`
* `"Box not found"`

```json
{
  "code": 404,
  "message": "...",
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