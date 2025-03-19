**Commit 3 Reflection Notes**

**Validating the Request and Selectively Responding**

In this iteration, I followed the instructions in Chapter 20 of the Rust book to validate the request and selectively respond to different URLs. I updated the `handle_connection` function to check the request line and respond accordingly.

**Splitting Between Responses**

To achieve this, I split the response into two parts: one for the successful request (`"GET / HTTP/1.1"`) and another for the unsuccessful request (`"GET /bad HTTP/1.1"`). This is necessary because the response body and status line differ between the two cases.

**Refactoring**

I refactored the code to separate the response generation into two distinct blocks. This is needed to improve code readability and maintainability. By separating the concerns of each response, I can easily add or modify responses without affecting the rest of the code.

**Screenshot**

Here's a screenshot of my browser rendering the HTML content for the http://127.0.0.1:7878/bad request:

![Commit 3 screen capture](public/static/image/Screenshot%202025-03-19%20111842.png)