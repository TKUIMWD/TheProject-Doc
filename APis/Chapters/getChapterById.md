---
title: getChapterById

---

### Get Chapter by ID

Retrieves the data for a single chapter. Requires the user to have access to the parent course.

**Req**
```
GET /api/v1/chapters/:chapterId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name        | Type   | Description                |
| :---------- | :----- | :------------------------- |
| `chapterId` | string | **Required.** The ID of the chapter to retrieve. |

**Resp**
<details>
<summary><code>200 OK</code> - Chapter data retrieved successfully</summary>

```json
{
  "code": 200,
  "message": "Chapter data retrieved successfully",
  "data": {
    "course_id": "60d0fe4f5311236168a109ca",
    "course_name": "Introduction to Programming",
    "class_id": "60d0fe4f5311236168a109cb",
    "class_name": "Variables and Data Types",
    "chapter_id": "60d0fe4f5311236168a109cc",
    "chapter_name": "What is a Variable?",
    "chapter_subtitle": "Understanding how to store data",
    "chapter_order": 1,
    "chapter_content": "<p>This is the approved chapter content...</p>"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

```json
{ "code": 400, "message": "Invalid chapter_id format", "data": null }
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
{ "code": 403, "message": "You are not authorized to view this chapter.", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

Possible `message` values:
* `"Chapter not found"`
* `"Could not find parent class for this chapter"`
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