---
title: deleteCourseById

---

### Delete Course by ID

Deletes a course permanently. Requires admin/creator privileges. Note: This action does not currently cascade delete associated classes and chapters.

**Req**
```
DELETE /api/v1/courses/delete/:courseId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The admin/creator's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `courseId` | string | **Required.** The ID of the course to delete. |

**Resp**
<details>
<summary><code>200 OK</code></summary>
```json
{ "code": 200, "message": "Course deleted successfully", "data": null }
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