---
title: getCourseById

---

### Get Course by ID

Retrieves the main page data for a single course. Requires the user to be enrolled in the course.

**Req**
```
GET /api/v1/courses/:courseId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The enrolled user's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `courseId` | string | **Required.** The ID of the course to retrieve. |

**Resp**
<details>
<summary><code>200 OK</code> - Course page data retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "Course page data retrieved successfully",
  "data": {
    "course_name": "Advanced Web Development",
    "course_subtitle": "Mastering the MERN Stack",
    "course_description": "A deep dive into modern web technologies.",
    "course_duration_in_minutes": 1200,
    "course_difficulty": "Hard",
    "course_rating": 4.8,
    "course_reviews": [],
    "class_ids": ["60d0fe4f5311236168a109cb"],
    "submitterInfo": {
      "username": "CourseCreator",
      "email": "creator@example.com",
      "avatar_path": "/path/to/avatar.png"
    }
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

```json
{ "code": 400, "message": "Invalid course_id format", "data": null }
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
{ "code": 403, "message": "You are not authorized to view this course", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

Possible `message` values:
* `"Course not found"`
* `"Submitter not found"`
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