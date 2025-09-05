---
title: getFirstTemplateByCourseID

---

### Get First Template ID in a Course

Finds the first available VM template associated with a course by searching through its classes and chapters in their specified order. Requires the user to be enrolled in the course.

**Req**
```
GET /api/v1/courses/getFirstTemplateByCourseID/:courseId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Path Parameters**
| Name       | Type   | Description                |
| :--------- | :----- | :------------------------- |
| `courseId` | string | **Required.** The ID of the course to search within. |

**Resp**
<details>
<summary><code>200 OK</code> - Success</summary>

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "template_id": "60d0fe4f5311236168a109e1"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Invalid ID Format</summary>

```json
{
  "code": 400,
  "message": "Invalid course_id format",
  "data": null
}
```
</details>

<details>
<summary><code>403 Forbidden</code> - Not Enrolled</summary>

```json
{
  "code": 403,
  "message": "You are not authorized to access this course",
  "data": null
}
```
</details>

<details>
<summary><code>404 Not Found</code> - No Template Found</summary>
    
This error can be returned for several reasons if a template cannot be located.

Possible `message` values:
* `"Course not found"`
* `"No classes found in this course"`
* `"No chapters found in this course"`
* `"No template_id found in any chapter of this course"`

```json
{
  "code": 404,
  "message": "...",
  "data": null
}
```
</details>

<details>
<summary>Other Error Responses</summary>
    
Also supports `500 Internal Server Error`.
</details>