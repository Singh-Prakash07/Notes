# Anatomy of a URL

A **URL (Uniform Resource Locator)** is a specific type of URI (Uniform Resource Identifier) that provides the network "location" of a resource and the mechanism to retrieve it.

---
A complete URL can be broken down into these distinct parts:

`https://www.example.com:443/products/shoes?color=blue&size=10#reviews`

### 1. Scheme (Protocol)
The **Scheme** tells the browser "how" to communicate with the server.
*   **Examples:** `http`, `https` (secure), `ftp`, `mailto`.
*   **Syntax:** Followed by `://`.

### 2. Subdomain
An optional prefix to the main domain used to organize different website sections.
*   **Example:** `blog.website.com` or `dev.website.com`. `www` is the most common subdomain.

### 3. Domain Name (Host)
The human-readable address of the server. It consists of:
*   **SLD (Second-Level Domain):** The unique name (e.g., `google`, `github`).
*   **TLD (Top-Level Domain):** The suffix (e.g., `.com`, `.org`, `.edu`).

### 3.5. Top-Level Domain (TLD):
The extension indicating the nature or region of the site, such as .com, .org, or country codes like .uk.

### 4. Port
A technical "gate" on the server.
*   **Standard Ports:** `80` for HTTP, `443` for HTTPS. 
*   **Syntax:** Followed by a colon (e.g., `localhost:3000`). If standard ports are used, they are usually hidden from the address bar.

### 5. Path
Points to the specific resource, file, or API endpoint on the server.
*   **Syntax:** Starts with a forward slash `/`.
*   **Analogy:** If the domain is the house address, the path is the specific room inside.

### 6. Query Parameters
Used to pass data or filters to the server.
*   **Syntax:** Starts with `?`.
*   **Format:** `key=value` pairs separated by `&`.
*   **Example:** `?search=python&sort=recent`

### 7. Fragment (Anchor)
Refers to a specific internal section of the page (an element with a specific ID).
*   **Syntax:** Starts with `#`.
*   **Note:** This part is **not** sent to the server; the browser uses it locally to scroll to a specific section.

