---
title: reviews

---

### Get Box Reviews

Retrieves all ratings and comments for a specific public Box, sorted with the newest first.

**Req**
```
GET /api/v1/vmbox/reviews
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Query Parameters**
| Name     | Type   | Description                |
| :------- | :----- | :------------------------- |
| `box_id` | string | **Required.** The ID of the Box to get reviews for. |

**Resp**
<details>
<summary><code>200 OK</code> - Box reviews fetched successfully</summary>

```json
{
  "code": 200,
  "message": "Box reviews fetched successfully",
  "data": {
    "box_id": "60d0fe4f5311236168a10b01",
    "reviews": [
      {
        "rating_score": 5,
        "comment": "Excellent box, very helpful!",
        "submitted_date": "2025-09-02T15:00:00.000Z",
        "reviewer_info": {
          "username": "JohnDoe"
        }
      },
      {
        "rating_score": 4,
        "comment": "Good starting point.",
        "submitted_date": "2025-09-01T18:30:00.000Z",
        "reviewer_info": {
          "username": "JaneSmith"
        }
      }
    ],
    "total_reviews": 2,
    "average_rating": 4.5
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code> - Missing Parameter</summary>

```json
{
  "code": 400,
  "message": "Missing required parameter: box_id",
  "data": null
}
```
</details>

<details>
<summary><code>403 Forbidden</code> - Box is Not Public</summary>

```json
{
  "code": 403,
  "message": "Cannot view reviews for unapproved box",
  "data": null
}
```
</details>

<details>
<summary><code>404 Not Found</code> - Box Not Found</summary>

```json
{
  "code": 404,
  "message": "Box not found",
  "data": null
}
```
</details>