**Commit 4 Reflection Notes**

**Simulating Single-Threaded Server Issues**

**Observations**

When I open two browser windows and try to access `127.0.0.1/sleep` in one and `127.0.0.1` in the other, I notice that the browser takes some time to load. This is because the server is handling the requests sequentially, one at a time.

**Understanding the Issue**

The server is running on a single thread, which means it can only handle one request at a time. When a request is made to `/sleep`, the server will block for 10 seconds, preventing it from handling any other requests during that time. This can lead to performance issues and slow response times.