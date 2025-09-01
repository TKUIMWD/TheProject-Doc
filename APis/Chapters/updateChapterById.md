---
title: updateChapterById

---

### Update Chapter by ID

Updates a chapter's details. This is a PATCH operation, so only include the fields you want to change. Requires the user to be the owner of the parent course.

**Req**
```
PATCH /api/v1/chapters/update/:chapterId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name        | Type   | Description                |
| :---------- | :----- | :------------------------- |
| `chapterId` | string | **Required.** The ID of the chapter to update. |

**Request Body**
| Name               | Type   | Description                               |
| :----------------- | :----- | :---------------------------------------- |
| `chapter_name`     | string | **Optional.** The new name of the chapter. Must be unique within the class. |
| `chapter_subtitle` | string | **Optional.** The new subtitle. |
| `chapter_content`  | string | **Optional.** The new content. This will be submitted for approval. |
| `chapter_order`    | number | **Optional.** The new display order. Must be a non-negative number and unique within the class. |

**Resp**
<details>
<summary><code>200 OK</code></summary>
```json
{ "code": 200, "message": "Chapter updated successfully", "data": null }
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
Possible `message` values:
* `"Invalid chapter_id format"`
* `"Chapter name cannot be empty."`
* `"chapter_order must be a non-negative number."`
* `"A chapter with the same order already exists in this class."`
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
{ "code": 403, "message": "You are not authorized to update this chapter", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
```json
{ "code": 404, "message": "Chapter not found", "data": null }
```
</details>

<details>
<summary><code>409 Conflict</code></summary>
```json
{ "code": 409, "message": "A chapter with this name already exists in this class.", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>
```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>