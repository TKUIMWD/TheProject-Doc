---
title: getClassById

---

### Get Class by ID

Retrieves the data for a single class. Requires the user to be the owner of the parent course.

**Req**
```
GET /api/v1/classes/:classId
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The course owner's session Bearer token. e.g., `Bearer <token>` |

**Path Parameters**
| Name      | Type   | Description                |
| :-------- | :----- | :------------------------- |
| `classId` | string | **Required.** The ID of the class to retrieve. |

**Resp**
<details>
<summary><code>200 OK</code> - Success</summary>

```json
{
  "code": 200,
  "message": "success",
  "data": {
    "classData": {
      "_id": "60d0fe4f5311236168a109cb",
      "course_id": "60d0fe4f5311236168a109ca",
      "class_name": "Variables and Data Types",
      "class_subtitle": "Learn the basics",
      "class_order": 1,
      "chapter_ids": [
        "60d0fe4f5311236168a109cc",
        "60d0fe4f5311236168a109cd"
      ]
    }
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>

```json
{ "code": 400, "message": "Invalid class_id format", "data": null }
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
{ "code": 403, "message": "You are not authorized to view this class", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>

Possible `message` values:
* `"Class not found"`
* `"Associated course not found"`
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