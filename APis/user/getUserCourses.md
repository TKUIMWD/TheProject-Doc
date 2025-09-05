---
title: getUserCourses

---

### Get User's Courses

Retrieves a list of all courses the authenticated user is enrolled in.

**Req**
```
GET /api/v1/user/getUserCourses
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Resp**
<details>
<summary><code>200 OK</code> - User courses retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "User courses retrieved successfully",
  "data": [
    {
      "_id": "60d0fe4f5311236168a109ca",
      "course_name": "Advanced Web Development",
      "duration_in_minutes": 1200,
      "difficulty": "Hard",
      "rating": 4.8,
      "teacher_name": "CourseCreator",
      "update_date": "2025-08-20T10:00:00.000Z",
      "status": "published"
    }
  ]
}
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `401 Unauthorized`, `403 Forbidden` (for unverified users), and `500 Internal Server Error`.
</details>