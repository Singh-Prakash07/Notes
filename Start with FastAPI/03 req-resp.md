### 📡 Web Communication: Request & Response Structure

In web development, the communication between a **Client** (your browser or mobile app) and a **Server** follows a strict pattern called the **Request-Response Cycle**.

---

#### 1. The HTTP Request
The client initiates the conversation by sending a request.

#### 🏗️ Structure
1.  **Request Line (Start Line):** Contains the **Method** (GET, POST,PUT, PATCH, DELETE etc.), the **Path** (/items/1), and the **HTTP Version**.
2.  **Headers:** Metadata about the request (e.g., `Content-Type: application/json`, `Authorization: Bearer ...`).
3.  **Empty Line:** A mandatory blank line separating headers from the body.
4.  **Body (Payload):** The actual data being sent (used in POST, PUT, and PATCH).



---

#### 2. The HTTP Response
The server processes the request and sends back a response.

#### 🏗️ Structure
1.  **Status Line:** Contains the **HTTP Version**, a **Status Code**, and a **Reason Phrase** (e.g., HTTP/1.1 200 OK).
2.  **Headers:** Metadata about the response (e.g., `Server: nginx`, `Content-Type: text/html`).
3.  **Empty Line:** A mandatory blank line.
4.  **Body:** The content requested (HTML, JSON data, or an image).

---

#### 3. 🚦 Common HTTP Status Codes
Status codes are divided into 5 "families" based on the first digit.

#### 🟢 2xx: Success
The request was successfully received, understood, and accepted.
*   **200 OK:** Standard success for GET/PUT.
*   **201 Created:** Success for POST (new resource created).
*   **204 No Content:** Success but nothing to return (often used for DELETE).

#### 🟡 3xx: Redirection
Further action needs to be taken to complete the request.
*   **301 Moved Permanently:** The URL has changed forever.
*   **304 Not Modified:** Use the cached version of the resource.

#### 🟠 4xx: Client Error
The request contains bad syntax or cannot be fulfilled (the client's fault).
*   **400 Bad Request:** General error (e.g., malformed JSON).
*   **401 Unauthorized:** You need to log in to see this.
*   **403 Forbidden:** You are logged in, but you don't have permission.
*   **404 Not Found:** The resource does not exist.

#### 🔴 5xx: Server Error
The server failed to fulfill an apparently valid request (the server's fault).
*   **500 Internal Server Error:** The server crashed or encountered an unhandled exception.
*   **502 Bad Gateway:** One server received an invalid response from another.
*   **503 Service Unavailable:** The server is overloaded or down for maintenance.
