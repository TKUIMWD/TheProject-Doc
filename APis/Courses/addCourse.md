---
title: addCourse

---

### Add a New Course

Creates a new course. Requires admin/creator privileges.

**Req**
```
POST /api/v1/courses/add
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The admin/creator's session Bearer token. e.g., `Bearer <token>` |

**Request Body**
| Name                    | Type   | Description                |
| :---------------------- | :----- | :------------------------- |
| `course_name`           | string | **Required.** The name of the new course. Must be unique. |
| `course_subtitle`       | string | **Required.** The subtitle for the new course. |
| `course_description`    | string | **Required.** A description of the course. |
| `duration_in_minutes`   | number | **Required.** The estimated duration in minutes. Must be a positive number. |
| `difficulty`            | string | **Required.** Must be one of `Easy`, `Medium`, or `Hard`. |

**Resp**
<details>
<summary><code>200 OK</code> - Course created successfully</summary>

```json
{
  "code": 200,
  "message": "Course created successfully",
  "data": {
    "course_id": "60d0fe4f5311236168a109cf"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

Possible `message` values:
* `"Missing required fields: ..."`
* `"course_name cannot be empty or strings containing security-sensitive characters"` (and other fields)
* `"duration_in_minutes must be a non-negative number"`
* `"difficulty must be one of 'Easy', 'Medium', or 'Hard'"`
* `"Course with the same name already exists"`
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
<summary><code>500 Internal Server Error</code></summary>

Possible `message` values:
* `"Failed to associate course with user"`
* `"Failed to create course"`
* `"Internal Server Error"`
```json
{ "code": 500, "message": "...", "data": null }
```
</details>