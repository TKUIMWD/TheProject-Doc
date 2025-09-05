---
title: addClassToCourse

---

### Add a New Class to a Course

Creates a new class and associates it with an existing course. Requires the user to be the owner of the course.

**Req**
```
POST /api/v1/classes/addClassToCourse/:courseId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `courseId` | string | **Required.** The ID of the course to which the class will be added. |

**Request Body**
| Name             | Type   | Description                |
| :--------------- | :----- | :------------------------- |
| `class_name`     | string | **Required.** The name of the new class. Must be unique within the course. |
| `class_subtitle` | string | **Required.** The subtitle for the new class. |
| `class_order`    | number | **Required.** The display order. Must be a non-negative number and unique within the course. |

**Resp**
<details>
<summary><code>200 OK</code> - Class added successfully</summary>

```json
{
  "code": 200,
  "message": "Class added successfully",
  "data": {
    "class_id": "60d0fe4f5311236168a109ce"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

Possible `message` values:
* `"Invalid course_id format"`
* `"Missing required fields: class_name, class_subtitle, class_order"`
* `"Class with this name already exists in the course"`
* `"class_order must be a non-negative number"`
* `"A class with the same order already exists in this course"`
* `"class_name cannot be empty or strings containing security-sensitive characters"`
* `"class_subtitle cannot be empty or strings containing security-sensitive characters"`
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
{ "code": 403, "message": "You are not authorized to add classes to this course", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

```json
{ "code": 404, "message": "Course not found", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>

```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>