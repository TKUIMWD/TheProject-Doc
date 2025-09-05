---
title: deleteChapterById

---

### Delete Chapter by ID

Deletes a chapter permanently. Requires the user to be the owner of the parent course.

**Req**
```
DELETE /api/v1/chapters/delete/:chapterId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name        | Type   | Description                |
| :---------- | :----- | :------------------------- |
| `chapterId` | string | **Required.** The ID of the chapter to delete. |

**Resp**
<details>
<summary><code>200 OK</code></summary>

```json
{ "code": 200, "message": "Chapter deleted successfully", "data": null }
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
{ "code": 403, "message": "You are not authorized to delete this chapter", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

```json
{ "code": 404, "message": "Chapter not found", "data": null }
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>

```json
{ "code": 500, "message": "Internal Server Error", "data": null }
```
</details>