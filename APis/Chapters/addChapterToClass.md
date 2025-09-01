---
title: addChapterToClass

---

### Add a New Chapter to a Class

Creates a new chapter and associates it with an existing class. Requires the user to be the owner of the parent course.

**Req**
```
POST /api/v1/chapters/addChapterToClass/:classId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name      | Type   | Description                |
| :-------- | :----- | :------------------------- |
| `classId` | string | **Required.** The ID of the class to which the chapter will be added. |

**Request Body**
| Name               | Type   | Description                |
| :----------------- | :----- | :------------------------- |
| `chapter_name`     | string | **Required.** The name of the new chapter. Must be unique within the class. |
| `chapter_subtitle` | string | **Required.** The subtitle for the new chapter. |
| `chapter_content`  | string | **Required.** The content for the new chapter. |
| `chapter_order`    | number | **Required.** The display order. Must be a non-negative number. |

**Resp**
<details>
<summary><code>200 OK</code> - Chapter added successfully</summary>

```json
{
  "code": 200,
  "message": "Chapter added successfully",
  "data": {
    "chapter_id": "60d0fe4f5311236168a109cd"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"Invalid class_id format"`
* `"Missing required key(s) in request body: ..."`
* `"chapter_order must be a non-negative number"`
* `"chapter_name cannot be empty or strings containing security-sensitive characters"`
* `"Chapter with this name already exists in the class"`
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
Possible `message` values:
* `"Class not found"`
* `"Course not found"`
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