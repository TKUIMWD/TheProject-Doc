---
title: getHomepage

---

### Get Homepage

Retrieves the main application webpage (HTML file). This is the primary entry point for the user interface.

**Req**
```
GET /
```

**Resp**
<details>
<summary><code>200 OK</code></summary>
The server responds with the main HTML document of the web application.

**Content-Type**: `text/html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Application Homepage</title>
    </head>
<body>
    <div id="root"></div>
    </body>
</html>
```
</details>

<details>
<summary><code>404 Not Found / 500 Internal Server Error</code></summary>
This can occur if the `HomePagePath` environment variable is not configured correctly on the server, or if the file at that path does not exist.
</details>