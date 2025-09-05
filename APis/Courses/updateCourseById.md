---
title: updateCourseById

---

### Update Course by ID

Updates a course's details. This is a PATCH operation, so only include the fields you want to change. Requires the user to be the owner of the course.

**Req**
```
PATCH /api/v1/courses/update/:courseId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `courseId` | string | **Required.** The ID of the course to update. |

**Request Body**
| Name                    | Type   | Description                |
| :---------------------- | :----- | :------------------------- |
| `course_name`           | string | **Optional.** The new name of the course. |
| `course_subtitle`       | string | **Optional.** The new subtitle for the course. |
| `course_description`    | string | **Optional.** The new description for the course. |
| `duration_in_minutes`   | number | **Optional.** The new duration. Must be a positive number. |
| `difficulty`            | string | **Optional.** The new difficulty. Must be one of `Easy`, `Medium`, or `Hard`. |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{
  "code": 200,
  "message": "Course updated successfully",
  "data": {
    "course_id": "60d0fe4f5311236168a109ca"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

Possible `message` values:
* `"Invalid course_id format"`
* `"Course name cannot be empty..."` (and other fields)
* `"duration_in_minutes must be a positive number."`
* `"difficulty must be one of 'Easy', 'Medium', or 'Hard'."`
* `"No valid fields provided for update."`
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
{ "code": 403, "message": "You are not authorized to update this course", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

Possible `message` values:
* `"Course not found"`
* `"Course not found during update operation."`
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