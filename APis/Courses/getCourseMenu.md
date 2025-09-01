---
title: getCourseMenu

---

### Get Course Menu

Retrieves the course's navigation menu, consisting of its classes and their respective chapters. Requires the user to be enrolled in the course.

**Req**
```
GET /api/v1/courses/:courseId/menu
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The enrolled user's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `courseId` | string | **Required.** The ID of the course. |

**Resp**
<details>
<summary><code>200 OK</code> - Course menu data retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "Course menu data retrieved successfully",
  "data": {
    "class_titles": [
      {
        "class_id": "60d0fe4f5311236168a109cb",
        "class_order": 1,
        "class_name": "Variables and Data Types",
        "chapter_titles": [
          {
            "chapter_id": "60d0fe4f5311236168a109cc",
            "chapter_order": 1,
            "chapter_name": "What is a Variable?"
          }
        ]
      }
    ]
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
* `"No classes found for this course"`
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