## Notes on APIs, HTTP, and Data Formats

### 1. What is an API?

**API = Application Programming Interface**

An API is a **contract** — a defined agreement that specifies:
- What operations a system exposes to the outside world
- What inputs those operations accept
- What outputs they return
- What errors can occur

### The Restaurant Analogy

```
You (Client)  →  Waiter (API)  →  Kitchen (Server)
     ↑                                    |
     └──────────── Food (Response) ───────┘
```

You don't go into the kitchen yourself. You talk to the waiter (the API), who knows the rules of how to communicate your order to the kitchen and bring back your food. The kitchen can change its internal process — as long as the waiter still delivers the same food when ordered — and you would never know.

### Three core guarantees an API makes

| Guarantee | Meaning |
|---|---|
| **Abstraction** | You do not need to know how something works internally — only how to ask for it |
| **Encapsulation** | The internal implementation can change freely without breaking callers |
| **Standardisation** | Everyone uses the same interface — no guessing |

---

## 2. History — How APIs Evolved

```
1940s–50s   Subroutine calls (in-memory)
    ↓
1960s–70s   OS system calls (kernel APIs)
    ↓
1970s–80s   RPC — Remote Procedure Calls (network, but tightly coupled)
    ↓
1990s       CORBA, DCOM (object-oriented distributed computing)
    ↓
1998–2002   SOAP + WSDL (formal XML-based web services)
    ↓
2000        Roy Fielding's REST dissertation (PhD thesis)
    ↓
2000s       REST API dominates web development
    ↓
2005        Ajax enables rich browser-server communication
    ↓
2009        WebSockets (two-way real-time communication)
    ↓
2012        Facebook creates GraphQL internally
    ↓
2015        GraphQL open-sourced; Google releases gRPC
    ↓
2016–now    gRPC, GraphQL, REST co-exist; Webhooks widespread
    ↓
2020s       API-first design; OpenAPI standard; AsyncAPI
```

### Phase 1: In-Process APIs (1940s–1960s)

The very first "APIs" were subroutine libraries — collections of reusable code that programs could call. There was no network involved. Everything ran in the same process on the same machine.

```asm
; Early assembly — calling a subroutine
CALL SQRT_ROUTINE    ; "API call" — jump to another section of code
MOV result, AX       ; get the return value
```

No JSON. No HTTP. No network. Just function calls in memory.

### Phase 2: Operating System APIs (1960s–1980s)

When operating systems emerged (Unix in 1969), programs needed a standard way to ask the OS for services — opening a file, allocating memory, sending data to a printer.

These became **system calls** — a controlled gateway into the kernel.

```c
// C program calling the OS API (POSIX standard)
int fd = open("data.txt", O_RDONLY);   // ask OS to open a file
read(fd, buffer, 1024);                 // ask OS to read bytes
close(fd);                              // ask OS to release the file
```

The OS API is still the most fundamental API on any computer today.

### Phase 3: Network APIs and RPC (1970s–1990s)

As machines got connected via networks, the need arose to call code on **remote machines**. The idea of Remote Procedure Calls (RPC) was born: make a function call that looks local but actually travels across a network.

---

## 3. HTTP — The Foundation

HTTP (HyperText Transfer Protocol) is the protocol that powers the web — and almost every modern web API.

**Tim Berners-Lee** created HTTP in 1989 at CERN. The first version (HTTP/0.9) could only fetch HTML pages. Today HTTP is a general-purpose application-layer protocol used to transfer any kind of data.

### HTTP Versions

| Version | Year | Key Feature |
|---|---|---|
| **HTTP/0.9** | 1991 | Only GET, only HTML |
| **HTTP/1.0** | 1996 | Headers, status codes, other methods |
| **HTTP/1.1** | 1997 | Persistent connections, chunked transfers — still widely used |
| **HTTP/2** | 2015 | Binary framing, multiplexing, header compression |
| **HTTP/3** | 2022 | Runs over QUIC (UDP-based), lower latency |

### The Request–Response Model

HTTP is fundamentally **stateless** and **synchronous**:

```
CLIENT                              SERVER
  |                                    |
  |  ── HTTP Request ──────────────►  |
  |                                    |  (server processes)
  |  ◄─────────────── HTTP Response ─ |
  |                                    |
```

- **Stateless**: each request is completely independent. The server remembers nothing about previous requests (cookies and sessions are workarounds *on top of* this stateless nature)
- **Request–Response**: the client always initiates; the server always responds

---

## 4. HTTP Request — Anatomy

When you type a URL in a browser, click a button in an app, or call an API, an HTTP request is constructed and sent. Here is every part of it:

```
POST /inventory/items/ HTTP/1.1
Host: api.example.com
Content-Type: application/json
Authorization: Bearer eyJhbGciOiJIUzI1NiJ9...
Accept: application/json
Content-Length: 97
User-Agent: MyApp/1.0

{
    "name": "Wireless Keyboard",
    "category": "Electronics",
    "price": 45,
    "quantity": 100,
    "barcode": 123456789
}
```

### Breaking it Down

```
┌────────────────────────────────────────────────────────┐
│  REQUEST LINE                                          │
│  POST   /inventory/items/   HTTP/1.1                  │
│  ────   ──────────────────  ────────                  │
│  Method  Path               Version                   │
├────────────────────────────────────────────────────────┤
│  HEADERS  (key: value pairs)                          │
│  Host: api.example.com                                │
│  Content-Type: application/json   ← what I'm sending  │
│  Accept: application/json         ← what I want back  │
│  Authorization: Bearer <token>    ← who I am          │
│  Content-Length: 97               ← size of body      │
├────────────────────────────────────────────────────────┤
│  BLANK LINE  (separates headers from body)            │
├────────────────────────────────────────────────────────┤
│  BODY  (optional — present for POST, PUT, PATCH)      │
│  {"name": "Wireless Keyboard", ...}                   │
└────────────────────────────────────────────────────────┘
```

### Parts of a URL

```
https://api.example.com:443/inventory/items/query/?category=Electronics&page=2#section

│─────│  │─────────────│ │─│ │──────────────────│ │────────────────────────│ │───────│
scheme    host           port  path                query string              fragment

scheme   = https (protocol)
host     = api.example.com (domain name or IP address)
port     = 443 (default for HTTPS, often omitted)
path     = /inventory/items/query/ (resource location)
query    = ?category=Electronics&page=2 (key=value pairs, starts with ?)
fragment = #section (client-side only, never sent to server)
```

### Common Request Headers

| Header | Purpose | Example |
|---|---|---|
| `Host` | Target server hostname | `api.example.com` |
| `Content-Type` | Format of the body I'm sending | `application/json` |
| `Accept` | Format I want in the response | `application/json` |
| `Authorization` | Credentials / token | `Bearer eyJ...` |
| `Content-Length` | Number of bytes in body | `97` |
| `User-Agent` | Identifies the client software | `Mozilla/5.0` |
| `Cache-Control` | Caching directives | `no-cache` |
| `Cookie` | Send stored cookies | `sessionid=abc123` |
| `Origin` | Where the request came from (CORS) | `https://app.com` |

---

## 5. HTTP Response — Anatomy

After the server processes the request, it sends back a response:

```
HTTP/1.1 201 Created
Content-Type: application/json
Location: /inventory/items/42
Date: Mon, 01 Jan 2024 12:00:00 GMT
Content-Length: 120

{
    "id": 42,
    "name": "Wireless Keyboard",
    "category": "Electronics",
    "price": 45,
    "quantity": 100,
    "barcode": 123456789
}
```

### Breaking it Down

```
┌────────────────────────────────────────────────────────┐
│  STATUS LINE                                          │
│  HTTP/1.1   201   Created                            │
│  ────────   ───   ───────                            │
│  Version   Code   Reason phrase                      │
├────────────────────────────────────────────────────────┤
│  RESPONSE HEADERS                                     │
│  Content-Type: application/json                       │
│  Location: /inventory/items/42  ← where new item is   │
│  Date: Mon, 01 Jan 2024 ...                          │
│  Content-Length: 120                                  │
├────────────────────────────────────────────────────────┤
│  BLANK LINE                                           │
├────────────────────────────────────────────────────────┤
│  BODY                                                 │
│  {"id": 42, "name": "Wireless Keyboard", ...}        │
└────────────────────────────────────────────────────────┘
```

---

## 6. HTTP Methods (Verbs)

HTTP methods tell the server **what action** to perform on the resource.

| Method | Meaning | Has Body? | Idempotent? | Safe? |
|---|---|---|---|---|
| **GET** | Retrieve data | No | ✅ Yes | ✅ Yes |
| **POST** | Create new resource | Yes | ❌ No | ❌ No |
| **PUT** | Replace entire resource | Yes | ✅ Yes | ❌ No |
| **PATCH** | Partially update resource | Yes | ✅ Yes | ❌ No |
| **DELETE** | Remove resource | Optional | ✅ Yes | ❌ No |
| **HEAD** | Like GET but no body in response | No | ✅ Yes | ✅ Yes |
| **OPTIONS** | Ask what methods are allowed | No | ✅ Yes | ✅ Yes |

**Idempotent** = calling it once produces the same result as calling it 100 times.
**Safe** = it does not modify any data on the server.

### PUT vs PATCH — The Difference

```json
// Current item in DB:
{ "id": 1, "name": "Keyboard", "price": 45, "quantity": 100 }

// PUT — you must send ALL fields (full replacement):
PUT /items/1  →  { "name": "Keyboard Pro", "price": 60, "quantity": 100 }
// If you forget "quantity", it gets wiped out or set to null

// PATCH — you only send what changed:
PATCH /items/1  →  { "price": 60 }
// Only price changes; name and quantity stay as they were
```

---

## 7. HTTP Status Codes

Status codes are three-digit numbers grouped by their first digit:

```
1xx — Informational   (request received, continuing)
2xx — Success         (request understood and completed)
3xx — Redirection     (further action needed)
4xx — Client Error    (the request has a problem — your fault)
5xx — Server Error    (the server failed — their fault)
```

### Most Common Codes

| Code | Name | When Used |
|---|---|---|
| **200** | OK | Successful GET, PUT, PATCH |
| **201** | Created | Successful POST (new resource created) |
| **204** | No Content | Successful DELETE (nothing to return) |
| **301** | Moved Permanently | Resource has a new URL forever |
| **304** | Not Modified | Cached version is still valid |
| **400** | Bad Request | Invalid input, missing fields, bad JSON |
| **401** | Unauthorized | Not authenticated (no/invalid token) |
| **403** | Forbidden | Authenticated but not allowed |
| **404** | Not Found | Resource doesn't exist |
| **405** | Method Not Allowed | e.g., POST on a read-only endpoint |
| **409** | Conflict | e.g., duplicate barcode on creation |
| **422** | Unprocessable Entity | Semantically wrong (validation failed) |
| **429** | Too Many Requests | Rate limit exceeded |
| **500** | Internal Server Error | Server crashed |
| **502** | Bad Gateway | Proxy got a bad upstream response |
| **503** | Service Unavailable | Server is down or overloaded |

---

## 8. Types of APIs

### 8.1 Library / In-Process API (The Oldest Kind)

**What it is:** A collection of functions/methods you include directly in your program. There is no network communication — everything runs in the same process and memory space.

**How it works:**
```python
# Using Python's math library — a pure library API
import math
result = math.sqrt(16)   # calls code inside the math library
print(result)            # 4.0
```

**Characteristics:**
- Fastest possible (no network overhead — it's just a function call)
- No serialization needed (data lives in shared memory)
- Tightly coupled — you ship the library with your app
- If the library crashes, your whole program crashes

**Real examples:** Python's `os`, `json`, `math` modules; Java's standard library; C's `libc`

---

### 8.2 Operating System API

**What it is:** The interface that programs use to request services from the operating system kernel. Without this, a program couldn't open a file, allocate memory, print to the screen, or use the network.

**How it works:**
```c
// Every program that opens a file uses the OS API
int fd = open("/etc/hosts", O_RDONLY);   // system call → OS kernel
ssize_t bytes = read(fd, buffer, 4096);  // another system call
close(fd);                               // release the resource
```

**Examples:**
- **POSIX** — the standard Unix/Linux/macOS OS API (open, read, write, close, fork...)
- **Win32 API** — Windows OS API (CreateFile, ReadFile, WriteFile...)
- **Android NDK** — OS API for Android apps written in C/C++

---

### 8.3 Remote Procedure Call — RPC (1970s–90s)

**What it is:** A way to call a function on a **different machine** as if it were a local function. The network transport is hidden from the programmer.

**The big idea:** Make remote calls look like local calls:

```python
# Without RPC — you'd have to handle the network yourself:
socket.send(serialize({ "method": "add", "a": 3, "b": 4 }))
response = socket.receive()
result = deserialize(response)   # 7

# With RPC — it looks like a local function call:
result = remote_server.add(3, 4)   # 7
# The RPC framework handles all the network stuff invisibly
```

**How RPC works internally:**

```
CLIENT                              SERVER
  |                                    |
  | add(3, 4)                          |
  |   → stub serializes call          |
  |   → sends over network ─────────► |
  |                                    | skeleton deserializes
  |                                    | actual add(3, 4) runs
  |                                    | result serialized
  | ◄──────────── result sent back ─  |
  | stub deserializes                  |
  | returns 7 to caller               |
```

**Problems with early RPC:**
- Tightly coupled — client and server must share the same interface definition
- Hard to evolve (changing one function signature breaks all clients)
- Doesn't handle partial failures well (was the call received? did it execute?)
- Firewall unfriendly (used custom ports/protocols)

---

### 8.4 SOAP API (Late 1990s – 2000s)

**Full name:** Simple Object Access Protocol (though it's anything but simple)

**What it is:** A highly standardized, XML-based protocol for exchanging messages between systems over a network. Designed by Microsoft, IBM, and others, it became the dominant enterprise web service standard in the early 2000s.

**Key components of SOAP:**

```
SOAP Ecosystem
├── SOAP         — the message format (XML envelope)
├── WSDL         — Web Services Description Language (describes the API)
├── UDDI         — Universal Description, Discovery and Integration (registry)
└── WS-* specs   — extensions: WS-Security, WS-ReliableMessaging, WS-AtomicTransaction...
```

**Anatomy of a SOAP message:**

```xml
<!-- Every SOAP message is wrapped in an XML envelope -->
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope
    xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/"
    xmlns:inv="http://example.com/inventory">

    <!-- HEADER: optional metadata (auth, routing, transaction info) -->
    <soap:Header>
        <inv:AuthToken>eyJhbGci...</inv:AuthToken>
    </soap:Header>

    <!-- BODY: the actual request/response -->
    <soap:Body>
        <inv:GetItemRequest>
            <inv:ItemId>42</inv:ItemId>
        </inv:GetItemRequest>
    </soap:Body>

</soap:Envelope>
```

**SOAP Response:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
    <soap:Body>
        <GetItemResponse>
            <Item>
                <Id>42</Id>
                <Name>Wireless Keyboard</Name>
                <Price>45</Price>
            </Item>
        </GetItemResponse>
    </soap:Body>
</soap:Envelope>
```

**WSDL (Web Services Description Language):**

WSDL is an XML document that fully describes a SOAP service — what operations it exposes, what data types it uses, and where to find it. It's like a contract written in XML.

```xml
<!-- Simplified WSDL excerpt -->
<definitions name="InventoryService"
    targetNamespace="http://example.com/inventory">

    <message name="GetItemRequest">
        <part name="itemId" type="xsd:integer"/>
    </message>

    <message name="GetItemResponse">
        <part name="item" type="tns:Item"/>
    </message>

    <portType name="InventoryPortType">
        <operation name="GetItem">
            <input message="tns:GetItemRequest"/>
            <output message="tns:GetItemResponse"/>
        </operation>
    </portType>
</definitions>
```

**SOAP strengths:**
- Built-in security standard (WS-Security)
- Built-in reliable messaging (WS-ReliableMessaging)
- Built-in distributed transactions
- Language and transport agnostic (can run over HTTP, SMTP, TCP...)
- Formally typed (WSDL guarantees message structure)
- Still used heavily in banking, healthcare, government systems

**SOAP weaknesses:**
- Extremely verbose (XML overhead)
- Complex to implement and debug
- Tightly coupled to WSDL contract
- Poor browser support
- Hard to cache

---

### 8.5 REST API (2000s – Present)

**Full name:** Representational State Transfer

**Origin:** Roy Fielding defined REST in his 2000 PhD dissertation at UC Irvine. He was one of the authors of the HTTP specification and designed REST to use HTTP as it was intended, rather than layering a new protocol on top of it.

**REST is not a protocol — it is an architectural style** (a set of constraints/principles). Any API that follows these constraints is called "RESTful."

#### The 6 REST Constraints

| Constraint | Meaning |
|---|---|
| **1. Client-Server** | Separation of concerns. Client handles UI; server handles data. They evolve independently. |
| **2. Stateless** | Each request must contain all information needed. Server stores no session state between requests. |
| **3. Cacheable** | Responses must declare whether they can be cached. Reduces server load and improves performance. |
| **4. Uniform Interface** | All resources follow the same interface (methods + URLs + representations). |
| **5. Layered System** | Client doesn't know if it's talking to the real server or a load balancer/proxy/cache in between. |
| **6. Code on Demand** | (Optional) Server can send executable code to the client (e.g., JavaScript). |

#### REST Resources and URLs

In REST, everything is a **resource** identified by a URL:

```
# RESOURCE NAMING CONVENTIONS

# Collections (plural nouns):
GET    /items            → list all items
POST   /items            → create a new item

# Single resource (with identifier):
GET    /items/42         → get item with id=42
PUT    /items/42         → replace item 42 completely
PATCH  /items/42         → partially update item 42
DELETE /items/42         → delete item 42

# Nested resources:
GET    /categories/electronics/items    → items in electronics category
GET    /users/5/orders                  → orders for user 5
GET    /users/5/orders/99              → specific order 99 of user 5

# Query parameters for filtering, sorting, pagination:
GET    /items?category=Electronics     → filter
GET    /items?sort=-price              → sort by price descending
GET    /items?page=2&limit=10         → pagination
GET    /items?search=keyboard         → search
```

#### REST vs SOAP in practice

```
SOAP request to get item #42:
─────────────────────────────
POST /InventoryService HTTP/1.1
Content-Type: text/xml
<soap:Envelope>
  <soap:Body>
    <GetItemRequest><ItemId>42</ItemId></GetItemRequest>
  </soap:Body>
</soap:Envelope>

REST request to get item #42:
─────────────────────────────
GET /items/42 HTTP/1.1
Accept: application/json

That's it. Nothing else needed.
```

#### REST API Example (Our Inventory API)

```
Endpoint              Method   Response  Description
────────────────────────────────────────────────────────────
/inventory/items/     GET      200       List all items
/inventory/items/     POST     201       Create new item
/inventory/items/42/  GET      200       Get item 42
/inventory/items/42/  PUT      200       Replace item 42
/inventory/items/42/  DELETE   204       Delete item 42
/inventory/items/query/?category=X  GET  200  Filter by category
/inventory/items/sort/  GET    200       Sort by price desc
```

---

### 8.6 GraphQL (2012–Present)

**Origin:** Created by Facebook in 2012 to solve problems with REST APIs for mobile applications. Open-sourced in 2015.

**Core problem it solves:**

```
REST problem 1 — Over-fetching:
  GET /users/5  returns:
  { "id": 5, "name": "Alice", "email": "...", "address": {...},
    "phone": "...", "bio": "...", "preferences": {...}, ... }
  → You only needed the name, but got everything.

REST problem 2 — Under-fetching (N+1 problem):
  GET /users/5          → { "id": 5, ... }
  GET /users/5/orders   → [{ "id": 1, ... }, { "id": 2, ... }]
  GET /orders/1/items   → [...]
  GET /orders/2/items   → [...]
  → Four requests just to show a user's order history.

GraphQL solution — ask for exactly what you need in one request:
  POST /graphql
  {
    user(id: 5) {
      name
      orders {
        id
        items {
          name
          price
        }
      }
    }
  }
```

**GraphQL anatomy:**

```graphql
# QUERY — reading data
query {
    item(id: 42) {
        name
        price
        category {
            name
        }
    }
}

# MUTATION — writing data
mutation {
    createItem(input: {
        name: "Wireless Keyboard"
        price: 45
        category: "Electronics"
    }) {
        id
        name
    }
}

# SUBSCRIPTION — real-time updates
subscription {
    itemPriceChanged(categoryId: 3) {
        id
        name
        oldPrice
        newPrice
    }
}
```

**GraphQL characteristics:**
- Single endpoint (usually `/graphql`) — not multiple URLs
- Client specifies exactly what data it needs
- Strongly typed schema (introspectable)
- Eliminates over-fetching and under-fetching
- Great for complex, nested, or highly variable data needs
- More complex to implement server-side
- Caching is harder than REST

---

### 8.7 gRPC (2016–Present)

**Origin:** Created by Google. gRPC stands for "Google Remote Procedure Call."

**What it is:** A modern, high-performance RPC framework that uses:
- **Protocol Buffers** (protobuf) for serialization — binary, compact, fast
- **HTTP/2** for transport — multiplexing, streaming, bidirectional

**How it works:**

```protobuf
// 1. Define your service in a .proto file
syntax = "proto3";

service InventoryService {
    rpc GetItem (GetItemRequest) returns (Item);
    rpc ListItems (ListItemsRequest) returns (stream Item);  // server streaming
    rpc CreateItem (Item) returns (CreateItemResponse);
}

message Item {
    int32 id = 1;
    string name = 2;
    string category = 3;
    int32 price = 4;
    int32 quantity = 5;
    int32 barcode = 6;
}

message GetItemRequest {
    int32 id = 1;
}
```

```python
# 2. Generated client code (auto-generated from .proto)
channel = grpc.insecure_channel('api.example.com:50051')
stub = InventoryStub(channel)

# Looks like a local function call
item = stub.GetItem(GetItemRequest(id=42))
print(item.name)  # "Wireless Keyboard"
```

**gRPC vs REST:**

| Feature | REST | gRPC |
|---|---|---|
| Protocol | HTTP/1.1 or HTTP/2 | HTTP/2 only |
| Data format | JSON (text) | Protocol Buffers (binary) |
| API contract | OpenAPI spec (optional) | .proto file (required) |
| Browser support | ✅ Excellent | ⚠️ Limited (needs proxy) |
| Performance | Good | **Excellent** (10x less bandwidth) |
| Streaming | Limited | **Native** (bidirectional) |
| Code generation | Optional | **Core feature** |
| Use case | Public APIs, web apps | Internal microservices |

---

### 8.8 WebSocket API

**What it is:** A protocol (not HTTP) that establishes a **persistent, full-duplex** (two-way) connection between client and server. Unlike HTTP, either side can send messages at any time without the other asking first.

```
HTTP model:              WebSocket model:
Client → Request         Client ←→ Server
Server ← Response        (both send freely at any time)
(connection closed)      (connection stays open)
```

**How the WebSocket connection starts (the handshake):**

```
1. Client sends an HTTP request with special headers:
   GET /chat HTTP/1.1
   Upgrade: websocket
   Connection: Upgrade
   Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==

2. Server responds:
   HTTP/1.1 101 Switching Protocols
   Upgrade: websocket
   Connection: Upgrade
   Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=

3. From now on, the connection is a WebSocket. HTTP is done.
   Both sides exchange frames directly.
```

**Use cases:** Live chat, real-time dashboards, multiplayer games, live sports scores, collaborative document editing (Google Docs), trading platforms

---

### 8.9 Webhook

**What it is:** A "reverse API" — instead of your app polling a server asking "anything new?", the server **calls your app** when something happens.

```
POLLING (wasteful):                    WEBHOOK (efficient):
                                       
Client: "Any new orders?"              Server: "Order #99 just arrived!"
Server: "No."                          → POST to https://yourapp.com/webhook
Client: (waits 1 second)              
Client: "Any new orders?"             Your app handles it immediately.
Server: "No."                          No polling needed.
... (repeat 1000 times)
Server: "Yes! Order #99 arrived."
```

**Real world examples:**
- GitHub webhook: "notify this URL when someone pushes to this repo"
- Stripe webhook: "POST to this URL when a payment succeeds or fails"
- Twilio webhook: "POST to this URL when an SMS arrives"

**Your app must expose a public HTTPS endpoint that the external service can POST to.**

---

### 8.10 Server-Sent Events (SSE)

**What it is:** A one-way streaming channel from server to client over HTTP. Simpler than WebSockets for scenarios where only the server needs to push data.

```
GET /stream/prices HTTP/1.1
Accept: text/event-stream

--- Server keeps the connection open and sends: ---

data: {"price": 1.23, "item": "Widget A"}

data: {"price": 1.25, "item": "Widget A"}

data: {"price": 1.22, "item": "Widget A"}
```

**SSE vs WebSocket:**

| Feature | SSE | WebSocket |
|---|---|---|
| Direction | Server → Client only | Bidirectional |
| Protocol | HTTP (easy to use) | Custom ws:// protocol |
| Reconnect | Automatic | Manual |
| Browser support | ✅ Built-in | ✅ Built-in |
| Use case | News feeds, stock prices | Chat, games |

---

## 9. REST vs SOAP — Deep Comparison

```
Feature            REST                        SOAP
───────────────────────────────────────────────────────────────────────────
Type               Architectural style         Protocol
Data format        JSON (usually), XML, etc.   XML only (mandatory)
Transport          HTTP only                   HTTP, SMTP, TCP, JMS, etc.
Message size       Small (lean JSON)           Large (verbose XML envelope)
State              Stateless                   Can be stateful
Security           HTTPS + JWT/OAuth           WS-Security (built-in standard)
Error handling     HTTP status codes           SOAPFault element in body
Performance        Fast                        Slower (XML parsing overhead)
Learning curve     Low                         High (WSDL, WS-* specs)
Caching            Easy (GET is cacheable)     Difficult (all POST)
Browser friendly   ✅ Yes                      ❌ No (complex XML)
Transaction        No built-in                 WS-AtomicTransaction
Reliable delivery  No built-in                 WS-ReliableMessaging
Contract           Optional (OpenAPI)          Mandatory (WSDL)
Code generation    Optional                    Auto-generated from WSDL
Best for           Public web/mobile APIs      Enterprise, banking, legacy
Still used by      Everything                  Banks, healthcare, govt, SAP
───────────────────────────────────────────────────────────────────────────
```

---

## 10. Data Formats for API Communication

When a client and server communicate, they need to agree on how data is **encoded** and **structured**. These formats fall into three broad categories:

### Overview

```
Data Formats
│
├── STRUCTURED ─────────── strict schema, fixed types, predictable shape
│   ├── CSV (Comma-Separated Values)
│   ├── SQL table results
│   └── Protocol Buffers (protobuf)
│
├── SEMI-STRUCTURED ─────── self-describing, flexible schema, key-value
│   ├── JSON (JavaScript Object Notation)  ← dominant for REST APIs
│   ├── XML (Extensible Markup Language)   ← dominant for SOAP APIs
│   ├── YAML (YAML Ain't Markup Language)  ← config files
│   ├── TOML (Tom's Obvious Minimal Language)
│   └── INI / Properties files
│
├── UNSTRUCTURED ────────── no inherent schema
│   ├── Plain text (txt, log files)
│   ├── HTML (for humans, not machines)
│   ├── PDF, images, audio, video
│   └── Markdown (MD)
│
└── BINARY FORMATS ─────── compact, fast, not human-readable
    ├── Protocol Buffers (protobuf) ← gRPC
    ├── MessagePack ← binary JSON equivalent
    ├── CBOR (Concise Binary Object Representation)
    ├── Apache Avro ← big data streaming
    ├── Apache Parquet ← columnar, analytics
    └── Apache Arrow ← in-memory analytics
```

---

### 10.1 Structured Data

Data that conforms to a **rigid, pre-defined schema**. Every field has a known name, type, and position. Like rows in a database table.

**Characteristics:**
- Fixed columns and types
- No optional or dynamic fields
- Best for tabular/relational data
- Easiest to query and validate

**Example — CSV:**
```csv
id,name,category,price,quantity,barcode
1,Wireless Keyboard,Electronics,45,100,123456
2,USB Mouse,Electronics,25,200,789012
3,HDMI Cable,Electronics,12,500,345678
```

Every row has the same columns. Every value is in a predictable position. The schema is defined by the header row.

---

### 10.2 Semi-Structured Data

Data that does not conform to a rigid schema but **carries its own structure** through tags, keys, or markers. The most important category for APIs.

**Characteristics:**
- Schema is embedded in the data itself (self-describing)
- Fields can be optional, nested, or dynamic
- Different records can have different shapes
- Human-readable

---

### 10.3 Unstructured Data

Data with no inherent organizational structure that a machine can parse systematically.

**Examples:** Plain text, PDFs, images, audio files, video files

APIs do deal with unstructured data — a file upload API accepts binary image data; a text API returns a plain string. But the *metadata about* those files (filename, size, type) is usually structured or semi-structured JSON.

---

### 10.4 Binary Formats

Binary formats encode data as compact byte sequences rather than human-readable text. Dramatically faster to parse and smaller to transmit, but not readable without tooling.

---

## 11. Format Deep Dives

### JSON (JavaScript Object Notation)

**Created:** 2001 by Douglas Crockford  
**Category:** Semi-structured  
**MIME type:** `application/json`

JSON is the **dominant format for REST APIs** because it is simple, lightweight, natively supported in JavaScript (and every other language), and human-readable.

#### JSON Data Types

```json
{
    "string": "Hello, World!",
    "integer": 42,
    "float": 3.14159,
    "boolean_true": true,
    "boolean_false": false,
    "null_value": null,
    "array": [1, 2, 3, "four", true],
    "nested_object": {
        "key": "value",
        "another_key": 123
    },
    "array_of_objects": [
        {"name": "Alice", "age": 30},
        {"name": "Bob", "age": 25}
    ]
}
```

#### JSON Structure Rules

```
Value types: string | number | boolean | null | object | array

Object:  { "key": value, "key2": value2 }
         ↑ keys MUST be double-quoted strings
         ↑ values can be any JSON type

Array:   [ value1, value2, value3 ]
         ↑ ordered list of any JSON values
         ↑ can mix types (though usually shouldn't)

String:  "must be in double quotes"   ← single quotes are NOT valid JSON

Number:  42        (integer)
         3.14      (decimal)
         -7        (negative)
         1.5e10    (scientific notation)

Boolean: true | false   (lowercase, no quotes)

Null:    null           (lowercase, no quotes)
```

#### JSON Limitations

| Limitation | Problem | Solution |
|---|---|---|
| No comments | Can't annotate config files | Use YAML or JSON5 instead |
| No date type | Dates sent as strings | ISO 8601: `"2024-01-15T10:30:00Z"` |
| No integer vs float distinction | `42` and `42.0` differ in some languages | Specify in API contract |
| Text-based | Larger than binary formats | Use protobuf/msgpack for performance |
| No schema enforcement | Any JSON is valid — no built-in validation | Use JSON Schema |

#### JSON Schema — Validating JSON Structure

```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "title": "Item",
    "type": "object",
    "required": ["name", "category", "price", "quantity", "barcode"],
    "properties": {
        "id": {
            "type": "integer",
            "description": "Auto-assigned primary key"
        },
        "name": {
            "type": "string",
            "minLength": 1,
            "maxLength": 255
        },
        "price": {
            "type": "integer",
            "minimum": 0
        },
        "barcode": {
            "type": "integer"
        }
    },
    "additionalProperties": false
}
```

---

### XML (Extensible Markup Language)

**Created:** 1998 by W3C  
**Category:** Semi-structured  
**MIME type:** `application/xml` or `text/xml`

XML is the format that dominated web services in the early 2000s and is still used in SOAP APIs, RSS feeds, document formats (DOCX, XLSX are zipped XML), and configuration files.

#### XML Structure

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!-- This is a comment — XML supports comments, unlike JSON -->

<inventory>                          <!-- root element -->
    <item id="42">                   <!-- element with attribute -->
        <name>Wireless Keyboard</name>
        <category>Electronics</category>
        <price currency="USD">45</price>
        <quantity>100</quantity>
        <barcode>123456789</barcode>
        <tags>                       <!-- nested element (list) -->
            <tag>wireless</tag>
            <tag>bluetooth</tag>
            <tag>mechanical</tag>
        </tags>
    </item>
</inventory>
```

#### XML vs JSON — Same Data

```xml
<!-- XML: 280 characters -->
<item id="42">
    <name>Wireless Keyboard</name>
    <category>Electronics</category>
    <price>45</price>
    <quantity>100</quantity>
</item>
```

```json
// JSON: 96 characters (66% smaller)
{ "id": 42, "name": "Wireless Keyboard", "category": "Electronics", "price": 45, "quantity": 100 }
```

#### XML Unique Features

```xml
<!-- 1. Attributes vs Elements — XML has two ways to store data -->
<item id="42" category="Electronics">      <!-- data as attributes -->
    <name>Wireless Keyboard</name>         <!-- data as elements -->
</item>

<!-- 2. CDATA — for content that contains special XML characters -->
<description><![CDATA[Price < $50 & ships in "2 days"]]></description>

<!-- 3. Namespaces — avoid name conflicts when combining XML from different sources -->
<inv:item xmlns:inv="http://example.com/inventory"
          xmlns:ship="http://example.com/shipping">
    <inv:name>Keyboard</inv:name>
    <ship:weight>0.5kg</ship:weight>
</inv:item>
```

---

### YAML (YAML Ain't Markup Language)

**Created:** 2001  
**Category:** Semi-structured  
**MIME type:** `application/x-yaml`

YAML is designed to be the most human-readable data format. It's used almost exclusively for **configuration files**, not API responses (because whitespace-sensitive syntax is fragile over networks).

```yaml
# YAML uses indentation (spaces, NOT tabs) to indicate structure
# This is a comment

item:
  id: 42
  name: "Wireless Keyboard"       # strings can be quoted or bare
  category: Electronics
  price: 45
  in_stock: true
  barcode: null                   # null value

  # Lists use - prefix
  tags:
    - wireless
    - bluetooth
    - mechanical

  # Nested objects just increase indentation
  dimensions:
    width: 43.5
    height: 14.2
    depth: 3.1

# Multi-line strings:
description: |
  This keyboard features mechanical switches
  and wireless Bluetooth connectivity.
  Compatible with all major operating systems.

# Anchors and aliases (YAML's "DRY" feature — no equivalent in JSON):
defaults: &defaults          # & defines an anchor
  currency: USD
  in_stock: true

item_a:
  <<: *defaults              # * references the anchor — copies all fields
  name: Widget A

item_b:
  <<: *defaults
  name: Widget B
```

**Where YAML is used:**
- Docker Compose (`docker-compose.yaml`)
- Kubernetes manifests
- GitHub Actions workflows
- Django settings
- Python package configs (`pyproject.toml` uses TOML, but CI/CD uses YAML)
- Ansible playbooks

---

### CSV (Comma-Separated Values)

**Category:** Structured  
**MIME type:** `text/csv`

The simplest possible format for tabular data. Every row is a record; every comma separates a column. The first row is usually the header.

```csv
id,name,category,price,quantity,barcode
1,Wireless Keyboard,Electronics,45,100,123456789
2,USB Mouse,Electronics,25,200,987654321
3,HDMI Cable,Accessories,12,500,112233445
4,"Monitor, 27inch",Electronics,350,30,556677889
```

**CSV pitfalls:**

```
1. Values with commas MUST be quoted:
   "Monitor, 27inch"

2. Values with quotes must double-escape the quote:
   "He said ""hello"""

3. Line endings vary:
   Windows: \r\n (CRLF)
   Unix/Mac: \n (LF)
   Old Mac: \r (CR)

4. No standard for null vs empty string:
   ,, (two commas) — is that null, empty, or zero?

5. No data types — everything is a string unless you parse it:
   "45" is text, not an integer

6. No support for nested data or arrays
```

**When to use CSV:**
- Bulk data export/import (database dumps, Excel uploads)
- Analytics and BI tools
- Data science and ML datasets
- Simple tabular reports

---

### Protocol Buffers (protobuf)

**Created:** 2001 (open-sourced 2008) by Google  
**Category:** Binary structured  
**File extension:** `.proto`

Protocol Buffers are Google's language-neutral mechanism for serializing structured data. Much faster and smaller than JSON or XML.

```protobuf
// item.proto — the schema definition
syntax = "proto3";

message Item {
    int32  id       = 1;   // field number (used in binary encoding, not field order)
    string name     = 2;
    string category = 3;
    int32  price    = 4;
    int32  quantity = 5;
    int32  barcode  = 6;
}

message ItemList {
    repeated Item items = 1;   // repeated = array/list
}
```

**How protobuf encoding works:**

```
JSON: {"id":42,"name":"Keyboard","price":45}
→ 41 bytes (text)

Protobuf equivalent:
→ 08 2A 12 08 4B 65 79 62 6F 61 72 64 20 2D
→ 14 bytes (binary)
→ 3x smaller

Breakdown:
08 = field 1 (id), wire type 0 (varint)
2A = 42 in varint encoding
12 = field 2 (name), wire type 2 (length-delimited)
08 = 8 bytes follow
4B 65 79 62 6F 61 72 64 = "Keyboard"
20 = field 4 (price), wire type 0
2D = 45 in varint
```

**Advantages over JSON:**
- 3–10x smaller serialized size
- 20–100x faster serialization/deserialization
- Strongly typed (schema enforced at compile time)
- Backward compatible (add new fields without breaking old clients)

**Disadvantages:**
- Binary — not human readable (need protoc or tools to inspect)
- Requires .proto file and code generation step
- Poor browser/JavaScript support
- Harder to debug

---

### MessagePack

**Category:** Binary semi-structured  
**Nickname:** "Binary JSON"

MessagePack encodes the same structure as JSON but in binary, making it much more compact. Unlike protobuf, no schema is required.

```
JSON:        {"name":"Alice","age":30,"active":true}
             → 41 bytes

MessagePack: 83 A4 6E 61 6D 65 A5 41 6C 69 63 65 A3 61 67 65 1E A6 61 63 74 69 76 65 C3
             → 25 bytes (39% smaller)
             
The 83 at the start means "fixmap with 3 keys" (no schema needed)
```

**When to use:** Embedded systems, mobile apps, game servers — anywhere JSON's overhead is too high but protobuf's schema requirement is too rigid.

---

### Apache Avro

**Created:** 2009 as part of the Apache Hadoop project  
**Category:** Binary semi-structured  
**Use case:** Data streaming (Apache Kafka)

Avro stores the **schema inside the file itself**, making it self-describing. This makes it ideal for data pipelines where the schema may evolve.

```json
// Avro schema (JSON-based schema definition):
{
    "type": "record",
    "name": "Item",
    "namespace": "com.example.inventory",
    "fields": [
        {"name": "id",       "type": "int"},
        {"name": "name",     "type": "string"},
        {"name": "price",    "type": "int"},
        {"name": "category", "type": ["null", "string"], "default": null}
    ]
}
```

**Schema evolution rules in Avro:**
- You can add new fields (with defaults)
- You can remove fields that had defaults
- You cannot change a field's type
- You cannot rename a field without an alias

---

### Apache Parquet

**Category:** Binary columnar structured  
**Use case:** Analytics, data warehousing

Parquet is a **columnar** format — it stores all values for one column together, rather than storing each row together. This makes it extremely efficient for analytical queries that only need a few columns from millions of rows.

```
ROW-ORIENTED (CSV/JSON):           COLUMN-ORIENTED (Parquet):
Row 1: id=1, name=A, price=45      Column id:    1, 2, 3, 4, 5
Row 2: id=2, name=B, price=25      Column name:  A, B, C, D, E
Row 3: id=3, name=C, price=12      Column price: 45, 25, 12, 8, 99
...                                 ...

Query: "What is the average price?"
Row format: must read ALL columns of ALL rows
Column format: read ONLY the price column → much faster, less I/O
```

---

## 12. Which Format to Use When?

```
Situation                              Best Format
────────────────────────────────────────────────────────────────────────
REST API response to web/mobile        JSON
SOAP API (enterprise/legacy)           XML
Config file (human-edited)             YAML or TOML
Data export for Excel/spreadsheets     CSV
High-performance internal service      Protocol Buffers (gRPC)
Kafka event streaming                  Avro
Analytics / data warehouse             Parquet
Mobile app with size constraints       MessagePack
File upload                            Multipart form-data
Binary file (image, PDF, video)        Base64 in JSON or multipart
Real-time browser updates              JSON over WebSocket or SSE
────────────────────────────────────────────────────────────────────────
```

---

## 13. API Authentication Methods

Before a client can use an API, it usually needs to prove who it is.

### No Authentication
For completely public APIs (e.g., weather data anyone can read).

### API Key
Simple token included in the request:
```
GET /items HTTP/1.1
X-API-Key: my-secret-api-key-abc123

# Or in the URL (less secure — shows up in logs):
GET /items?api_key=my-secret-api-key-abc123
```

### HTTP Basic Authentication
```
# Username:password encoded as Base64
Authorization: Basic dXNlcjpwYXNzd29yZA==
#                      ↑ base64("user:password")
```
Only safe over HTTPS. Never use over plain HTTP.

### Bearer Token (JWT)
The most common method for modern REST APIs:
```
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjEsImV4cCI6MTcwNTMxMjAwMH0.abc123
```

A JWT (JSON Web Token) has three parts separated by dots:
```
HEADER.PAYLOAD.SIGNATURE

eyJhbGciOiJIUzI1NiJ9         ← Header: {"alg":"HS256"} base64 encoded
.
eyJ1c2VySWQiOjF9             ← Payload: {"userId":1} base64 encoded
.
SflKxwRJSMeKKF2QT4fwpMeJf    ← Signature: HMAC-SHA256(header+payload, secret)
```

### OAuth 2.0
The standard for "Login with Google / Facebook / GitHub" — delegated authorization.
```
1. User clicks "Login with Google"
2. Browser redirects to Google's auth page
3. User logs in to Google and approves permissions
4. Google redirects back with an authorization code
5. Your server exchanges the code for an access token
6. Your server uses the access token to call Google's API
```

### Session Cookies
Traditional web approach — server stores session state, client holds a cookie:
```
Set-Cookie: sessionid=abc123; HttpOnly; Secure; SameSite=Strict
```

---

## 14. API Versioning

APIs change over time. Versioning lets old clients keep working while new clients use new features.

### URL Path Versioning (Most Common)
```
/api/v1/items/
/api/v2/items/
```
Clear, explicit, easy to test in a browser.

### Query Parameter Versioning
```
/api/items/?version=2
```

### Header Versioning
```
GET /api/items/
Accept-Version: 2
```
Keeps URLs clean but harder to test/bookmark.

### Content Negotiation
```
GET /api/items/
Accept: application/vnd.myapi.v2+json
```
Most "purist REST" approach, least practical.

---

## 15. Quick Reference Cheat Sheet

### API Types at a Glance

| API Type | Transport | Format | Use Case |
|---|---|---|---|
| Library API | In-memory | Native types | Code reuse within same app |
| OS API (syscalls) | Kernel | Native types | OS services |
| RPC (old) | TCP | XDR/Custom | Legacy distributed systems |
| SOAP | HTTP/SMTP | XML | Enterprise, banking, healthcare |
| REST | HTTP | JSON (usually) | Web APIs, mobile, public |
| GraphQL | HTTP | JSON | Complex data, mobile optimization |
| gRPC | HTTP/2 | protobuf (binary) | Microservices, high performance |
| WebSocket | TCP (ws://) | JSON/binary | Real-time, bidirectional |
| Webhook | HTTP | JSON | Event notifications, integrations |
| SSE | HTTP | text/event-stream | Server → client push only |

### Data Formats at a Glance

| Format | Type | Human-Readable | Size | Schema Required | Best For |
|---|---|---|---|---|---|
| JSON | Semi-structured | ✅ Yes | Medium | No | REST APIs |
| XML | Semi-structured | ✅ Yes | Large | Optional (XSD) | SOAP, config |
| YAML | Semi-structured | ✅ Best | Medium | No | Config files |
| CSV | Structured | ✅ Yes | Small | Header row | Tabular data |
| protobuf | Binary structured | ❌ No | Very small | Yes (.proto) | gRPC, internal |
| MessagePack | Binary semi-struct | ❌ No | Small | No | Binary JSON |
| Avro | Binary semi-struct | ❌ No | Small | Yes (embedded) | Kafka streaming |
| Parquet | Binary columnar | ❌ No | Very small | Yes | Analytics |

### HTTP Methods Quick Reference

| Method | CRUD | Idempotent | Body | When to Use |
|---|---|---|---|---|
| GET | Read | ✅ | No | Fetching data |
| POST | Create | ❌ | Yes | Creating new resource |
| PUT | Update | ✅ | Yes | Full replacement |
| PATCH | Update | ✅ | Yes | Partial update |
| DELETE | Delete | ✅ | Optional | Removing resource |

### Status Code Quick Reference

| Range | Category | Key Codes |
|---|---|---|
| 2xx | Success | 200 OK, 201 Created, 204 No Content |
| 3xx | Redirect | 301 Permanent, 304 Not Modified |
| 4xx | Client Error | 400 Bad Request, 401 Unauth, 403 Forbidden, 404 Not Found |
| 5xx | Server Error | 500 Internal Error, 502 Bad Gateway, 503 Service Unavailable |

---

> **Key Takeaway:** There is no single "best" API type or data format. The right choice depends on your requirements — audience (public vs internal), performance needs, team familiarity, existing infrastructure, and how the data will be used on the receiving end.

---

*Notes compiled — covering APIs from 1940s subroutines to modern gRPC, GraphQL, and WebSockets.*
