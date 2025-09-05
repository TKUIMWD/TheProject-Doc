---
title: invite

---

### Invite Users to Join Course

Sends email invitations to a list of users to join a specific course. Requires **admin** privileges.

**Req**
```
POST /api/v1/courses/invite
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The admin's session Bearer token. |

**Request Body**
| Name        | Type     | Description                |
| :---------- | :------- | :------------------------- |
| `course_id` | string   | **Required.** The ID of the course to invite users to. |
| `emails`    | string[] | **Required.** An array of email addresses of the users to invite. |

**Resp**
<details>
<summary><code>200 OK</code> - Invitations sent</summary>
    
This response is returned even if some emails do not correspond to existing users or if some users are already in the course.

```json
{
  "code": 200,
  "message": "Invitations sent",
  "data": null
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Missing Parameters</summary>

```json
{
  "code": 400,
  "message": "Missing course_id or emails array",
  "data": null
}
```
</details>


<details>
<summary><code>404 Not Found</code> - Course Not Found</summary>

```json
{
  "code": 404,
  "message": "Course not found",
  "data": null
}
```
</details>

<details>
<summary><code>500 Internal Server Error</code></summary>

```json
{
  "code": 500,
  "message": "Internal Server Error",
  "data": null
}
```
</details>