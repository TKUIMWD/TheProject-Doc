---
title: rate

---

### Rate a Box

Submits a rating and an optional comment for a public Box. A user can only rate each Box once.

**Req**
```
POST /api/v1/vmbox/rate
```

**Headers**
| Name            | Description                               |
| :-------------- | :---------------------------------------- |
| `Authorization` | **Required.** The user's session Bearer token. |

**Request Body**
| Name      | Type   | Description                |
| :-------- | :----- | :------------------------- |
| `box_id`  | string | **Required.** The ID of the Box to rate. |
| `rating`  | number | **Required.** A rating from 1 to 5. |
| `comment` | string | **Optional.** A text comment for the review. |

**Resp**
<details>
<summary><code>200 OK</code> - Rating submitted successfully</summary>
    
```json
{
  "code": 200,
  "message": "Rating submitted successfully",
  "data": {
    "box_id": "60d0fe4f5311236168a10b01",
    "new_rating_score": 4.5,
    "review_count": 10,
    "review_id": "60d0fe4f5311236168a10c01"
  }
}
```
</details>

<details>
<summary><code>400 Bad Request</code></summary>
    
Possible `message` values:
* `"Missing required fields: box_id and rating"`
* `"Rating must be between 1 and 5"`
* `"You have already rated this box"`
```json
{ "code": 400, "message": "...", "data": null }
```
</details>

<details>
<summary><code>403 Forbidden</code></summary>
    
```json
{ "code": 403, "message": "Cannot rate unapproved box", "data": null }
```
</details>

<details>
<summary><code>404 Not Found</code></summary>
    
```json
{ "code": 404, "message": "Box not found", "data": null }
```
</details>

<details>
<summary><code>500 Error in rateBox</code></summary>
    
```json
{ "code": 500, "message": "Internal Server Error" }
```
</details>