---
title: updateClassById

---

### Update Class by ID

Updates a class's details. This is a PATCH operation, so only include the fields you want to change. Requires the user to be the owner of the parent course.

**Req**
```
PATCH /api/v1/classes/update/:classId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name      | Type   | Description                |
| :-------- | :----- | :------------------------- |
| `classId` | string | **Required.** The ID of the class to update. |

**Request Body**
| Name             | Type   | Description                               |
| :--------------- | :----- | :---------------------------------------- |
| `class_name`     | string | **Optional.** The new name of the class. Must be unique within the course. |
| `class_subtitle` | string | **Optional.** The new subtitle for the class. |
| `class_order`    | number | **Optional.** The new display order. Must be a non-negative number. |

**Resp**
<details>
<summary><code>200 OK</code></summary>
```json
{ "code": 200, "message": "Update class successfully", "data": null }
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"Invalid class_id format"`
* `"class_name cannot be empty or strings containing security-sensitive characters"`
* `"class_subtitle cannot be empty or strings containing security-sensitive characters"`
* `"Class with this name already exists in the course"`
* `"class_order must be a non-negative number"`
* `"No valid fields to update"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>401 Unauthorized</code></summary>
```json
{ "code": 401, "message": "invalid or expired token", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
```json
{ "code": 403, "message": "You are not authorized to update this class", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
Possible `message` values:
* `"Class not found"`
* `"Associated course not found"`
```json
{ "code": 404, "message": "...", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>