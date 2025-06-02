# Reflection Answers

## Exercise 1 – Review and Analyze

**Q1.** What error message appears in the terminal when accessing `http://localhost:3000`? Which line causes it?
**A1.** The error is a runtime error due to the incorrect method call `res.endd();`, which is undefined.

**Q2.** What is the purpose of `res.write()` and how does it differ from `res.end()`?
**A2.**

- `res.write()`: Sends a chunk of data to the client without ending the response. It can be called multiple times.
- `res.end()`: Ends the response and optionally sends the final data. It must be called once to complete the response.

**Q3.** What occurs if `res.end()` is not called?
**A3.** The browser will wait indefinitely for the response to finish. The connection remains open, possibly causing resource leaks and timeouts, and the client will see no response.

**Q4.** Why use `http.createServer()` instead of calling a function directly?
**A4.** `http.createServer()` creates an actual HTTP server that listens for and handles HTTP requests, manages TCP connections, and invokes a callback for each request. A plain function does not perform these tasks.

**Q5.** How can the server be made more resilient during development?
**A5.**

- Implement error handling.
- Ensure `res.end()` is always used to finalize responses.
- Use console logs for diagnostics.
- Utilize tools like Nodemon for automatic restarts after crashes.

---

## Exercise 2 – Manipulate

**Q1.** What happens when visiting a URL not defined in the routing logic?
**A1.** A plain text message displaying a 404 error is shown.

**Q2.** Why check both `req.url` and `req.method`?
**A2.** Different HTTP methods may apply to the same URL path. For example, `GET /products` retrieves data, while `POST /products` adds new data.

**Q3.** What `Content-Type` should be set when returning HTML instead of plain text?
**A3.**

- For HTML: `Content-Type: text/html`
- For plain text: `Content-Type: text/plain`

**Q4.** How does increasing route complexity affect routing logic?
**A4.**

- Leads to lengthy and complex `if-else` chains.
- Reduces readability and maintainability.
- Hinders scalability and reuse.
- Makes middleware integration difficult.

**Q5.** What are the advantages of using a framework for routing?
**A5.**

- Simplified syntax for route definitions.
- Support for middleware functions.
- Modular routing through separate files.
- Built-in error handling and utility methods (e.g., `res.status()`, `res.json()`).

---

## Exercise 3 – Create

**Q1.** Why listen for `data` and `end` events when handling a POST request?
**A1.** POST request bodies are received as streams.

- `req.on('data')`: Gathers incoming data chunks.
- `req.on('end')`: Indicates the completion of data reception.

**Q2.** What happens if the body is not buffered correctly?
**A2.**

- Data may be incomplete or lost.
- File writes may contain partial data.
- Input parsing may fail or behave unpredictably.

**Q3.** What is the format of form submissions via browser POST requests?
**A3.** `application/x-www-form-urlencoded`, e.g., `name=Heng`.

**Q4.** Why use `fs.appendFile` instead of `fs.writeFile`?
**A4.**

- `fs.writeFile` overwrites existing file content.
- `fs.appendFile` adds new data to the end, preserving existing entries.

**Q5.** How can the implementation be improved or made more secure?
**A5.**

- Properly parse and validate form data.
- Avoid synchronous file operations.
- Provide user feedback upon successful submission.
- Optionally, validate input fields and use JSON for structured data storage.
