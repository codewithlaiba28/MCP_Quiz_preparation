*The server does not store any client context (session state) between requests. Any session state is kept on the client side.*

----

**1. What is the main role of the client in a client-server architecture?**

    a) Store data permanently
    b) Handle user interface concerns ✅
    c) Manage server security
    d) Process all business logic
*Explanation:* The client is responsible for presenting data to the user and handling input.

**2. What is the main role of the server in a client-server architecture?**

    a) Display user interface
    b) Handle data storage, business logic, and security ✅
    c) Send requests to the client
    d) Keep session state of the client
*Explanation:* The server processes requests, stores data, and enforces rules.

**3. What does it mean when a server is stateless?**

    a) Server stores all user sessions
    b) Server does not store any client context between requests ✅
    c) Server can only handle one request at a time
    d) Server keeps track of all previous requests
*Explanation:* Each request is independent; the server doesn’t remember previous requests.

**4. Where is session state usually stored in a stateless architecture?**

    a) On the server
    b) On the client ✅
    c) On a third-party server
    d) In the database only
*Explanation:* Session info like JWT tokens or cookies is stored on the client and sent with each request.

**5. Which of the following is a benefit of statelessness?**

    a) Scalability
    b) Reliability
    c) Easier monitoring
    d) All of the above ✅
*Explanation:* Statelessness improves scalability, reliability, and visibility.

**6. True or False:** In a stateless system, any server can handle any request without needing prior knowledge of the client.

    a) True ✅
    b) False
*Explanation:* Since no session state is stored on the server, any server can process any request.

**7. Why does statelessness improve reliability?**

    a) Server remembers all previous requests
    b) Server crash does not affect client state ✅
    c) It reduces the number of clients
    d) It allows multiple interfaces
*Explanation:* Client state is kept on the client side, so server failures don’t cause data loss.

**8. Which of the following must each client request contain in a stateless system?**

    a) Only the client ID
    b) Only session token
    c) All information needed for the server to process the request ✅
    d) Only the user password
*Explanation:* Each request must be self-contained so the server can handle it independently.

---

### **1. Cacheability in REST means that:**

    a) Clients must store every response
    b) Servers decide whether a response can be reused later
    c) Only POST requests can be cached
    d) Responses are always stored by CDNs

**Correct Answer:** **b**

---

### **2. What is the main benefit of a cacheable response?**

    a) Increases server load
    b) Increases response time
    c) Reduces latency and improves network efficiency
    d) Blocks intermediaries like CDNs

**Correct Answer:** **c**

---

### **3. In a layered system, a client usually:**

    a) Knows the exact path to the end server
    b) Cannot tell whether it is talking to the server or an intermediary
    c) Must always communicate with the server directly
    d) Bypasses all network layers

**Correct Answer:** **b**

---

### **4. Which of the following is *not* a benefit of a layered system?**

    a) Scalability
    b) Load balancing
    c) Shared caches
    d) Increased coupling between layers

**Correct Answer:** **d**

---

### **5. Code on Demand is:**

    a) A mandatory REST constraint
    b) The only optional REST constraint
    c) Never used in web applications
    d) Required for caching

**Correct Answer:** **b**

---

### **6. Code on Demand typically transfers:**

    a) HTML pages only
    b) Database queries
    c) Executable code such as JavaScript
    d) Audio or video files

**Correct Answer:** **c**

---

### **7. The Uniform Interface is important because it:**

    a) Makes each part tightly coupled
    b) Simplifies architecture and supports independent evolution
    c) Requires multiple interfaces
    d) Removes the need for HTTP methods

**Correct Answer:** **b**

---

### **8. Identification of resources is mainly done using:**

    a) Environment variables
    b) Cookies
    c) URIs/URLs
    d) Database primary keys only

**Correct Answer:** **c**

---

### **9. Manipulation of resources happens through:**

    a) Screenshots
    b) Representations like JSON or XML
    c) Server logs
    d) SQL scripts sent to the client

**Correct Answer:** **b**

---

### **10. A representation must contain enough information for the client to:**

    a) Restart the server
    b) Modify or delete resources on the server
    c) Change server hardware
    d) Update DNS records

**Correct Answer:** **b**

---

### **11. Self-descriptive messages include all EXCEPT:**

    a) HTTP method
    b) Resource URI
    c) Headers like Content-Type
    d) Server operating system details

**Correct Answer:** **d**

---

### **12. The Accept header in a request tells the server:**

    a) User’s IP address
    b) What media types the client wants
    c) Which database to use
    d) Where to redirect

**Correct Answer:** **b**

---

### **13. HATEOAS allows clients to discover actions by:**

    a) Searching Google
    b) Following hyperlinks provided in server responses
    c) Restarting the API
    d) Reading API documentation only

**Correct Answer:** **b**

---

### **14. A major benefit of HATEOAS is:**

    a) Clients need to hardcode all URIs
    b) Server can evolve URI structure without breaking clients
    c) Clients no longer need HTTP
    d) It removes the need for caching

**Correct Answer:** **b**

---

### **15. Which REST principle is the least implemented in modern APIs?**

    a) Cacheability
    b) Uniform Interface
    c) HATEOAS
    d) Layered System

**Correct Answer:** **c**

---

### **1. In REST, what is a "resource"?**

    a) Only files stored on the server
    b) Any entity that can be named and accessed
    c) Only database entries
    d) Only JSON data
**Correct Answer:** **b**

---

### **2. What uniquely identifies a resource in REST?**

    a) HTTP method
    b) URL parameters
    c) URI
    d) Response headers
**Correct Answer:** **c**

---

### **3. What is a representation of a resource?**

    a) The server code
    b) The state of a resource returned to the client
    c) Only HTML pages
    d) Only database results
**Correct Answer:** **b**

---

### **4. Which format is NOT a common resource representation?**

    a) JSON
    b) XML
    c) HTML
    d) SQL
**Correct Answer:** **d**

---

### **5. Which HTTP method retrieves a resource?**

    a) POST
    b) GET
    c) PUT
    d) DELETE
**Correct Answer:** **b**

---

### **6. Which HTTP method is used to create a new resource?**

    a) GET
    b) POST
    c) DELETE
    d) HEAD
**Correct Answer:** **b**

---

### **7. Which method replaces an entire existing resource?**

    a) PATCH
    b) PUT
    c) GET
    d) OPTIONS
**Correct Answer:** **b**

---

### **8. Which method is used for partial updates?**

    a) GET
    b) DELETE
    c) PATCH
    d) PUT
**Correct Answer:** **c**

---

### **9. Which method only returns headers, not the body?**

    a) GET
    b) POST
    c) HEAD
    d) OPTIONS
**Correct Answer:** **c**

---

### **10. Which method returns allowed HTTP methods for a resource?**

    a) POST
    b) OPTIONS
    c) HEAD
    d) PATCH
**Correct Answer:** **b**

---

### **11. What does status code 200 indicate?**

    a) Bad request
    b) Created
    c) OK
    d) Unauthorized
**Correct Answer:** **c**

---

### **12. Which status code means a resource was successfully created?**

    a) 200
    b) 201
    c) 400
    d) 500
**Correct Answer:** **b**

---

### **13. Which status code means a request succeeded but returns no content?**

    a) 204
    b) 404
    c) 500
    d) 401
**Correct Answer:** **a**

---

### **14. Which status code means authentication is required?**

    a) 400
    b) 401
    c) 403
    d) 500
**Correct Answer:** **b**

---

### **15. Which status code means the server refuses to authorize the request?**

    a) 401
    b) 403
    c) 404
    d) 200
**Correct Answer:** **b**

---

### **16. Which status code indicates the resource does not exist?**

    a) 403
    b) 404
    c) 500
    d) 204
**Correct Answer:** **b**

---

### **17. Which status code indicates a server-side error?**

    a) 500
    b) 404
    c) 201
    d) 301
**Correct Answer:** **a**

---

### **18. Which HTTP method is NOT idempotent?**

    a) GET
    b) DELETE
    c) POST
    d) PUT
**Correct Answer:** **c**

---

### **19. Which header specifies the client's preferred response format?**

    a) Content-Type
    b) Accept
    c) Cache-Control
    d) Auth-Type
**Correct Answer:** **b**

---

### **20. The header used to define the body format of a request/response is:**

    a) Accept
    b) Content-Type
    c) Link
    d) ETag
**Correct Answer:** **b**

---

### **1. What should URIs represent in a RESTful API?**

    a) Actions
    b) Server functions
    c) Resources
    d) SQL operations
**Correct Answer:** **c**

---

### **2. Which URI naming style is recommended for collections?**

    a) Singular nouns
    b) Verbs
    c) Plural nouns
    d) CamelCase
**Correct Answer:** **c**

---

### **3. Which of the following is an example of a good REST URI?**

    a) /getAllUsers
    b) /createUser
    c) /users/{userId}
    d) /delete/product
**Correct Answer:** **c**

---

### **4. Which HTTP method should be used to create a new resource?**

    a) GET
    b) PUT
    c) POST
    d) HEAD
**Correct Answer:** **c**

---

### **5. Which HTTP method is used for partial updates?**

    a) PATCH
    b) GET
    c) DELETE
    d) OPTIONS
**Correct Answer:** **a**

---

### **6. Which status code category should be used to indicate client-side errors?**

    a) 1xx
    b) 2xx
    c) 4xx
    d) 5xx
**Correct Answer:** **c**

---

### **7. What is the most commonly supported data format in modern REST APIs?**

    a) HTML
    b) JSON
    c) CSV
    d) YAML
**Correct Answer:** **b**

---

### **8. Which of the following is an example of filtering and pagination?**

    a) /users/all
    b) /users?page=help
    c) /users?status=active&limit=20
    d) /getUsersByName
**Correct Answer:** **c**

---

### **9. Which versioning strategy is the most commonly used?**

    a) Query parameter versioning
    b) Header versioning
    c) Media type versioning
    d) URI path versioning
**Correct Answer:** **d**

---

### **10. Which header-based versioning example is correct?**

    a) X-API-Version: 1
    b) Accept-Encoding: v1
    c) Token-Version: v1
    d) Content-Version: 2
**Correct Answer:** **a**

---

### **11. What should an API error response typically include?**

    a) Only a message
    b) Only an HTTP code
    c) Error code, message, and documentation link
    d) Only server logs
**Correct Answer:** **c**

---

### **12. Which method is commonly used for authentication in APIs?**

    a) CSS keys
    b) API Keys
    c) GET Tokens
    d) XML Tokens
**Correct Answer:** **b**

---

### **13. What should always be used to secure API communication?**

    a) HTTP
    b) FTP
    c) SSH
    d) HTTPS (TLS)
**Correct Answer:** **d**

---

### **14. Which tool is widely used for REST API documentation?**

    a) Firebase
    b) OpenAPI (Swagger)
    c) GitHub
    d) Postman Echo
**Correct Answer:** **b**

---

### **15. What does HATEOAS add to a REST API?**

    a) Encryption
    b) Speed
    c) Hyperlinks to related resources
    d) Database indexing
**Correct Answer:** **c**

---

Perfect! I can convert all **30 REST quiz questions** into that pattern. Here’s the full conversion:

---

### **1. In a RESTful API, what does the stateless constraint mean?**

```
a) The server retains client session state between requests
b) Each request from the client must contain all information needed by the server to understand it
c) The client must store all past responses
d) The server must maintain stateful connections
```

**Correct Answer:** **b**

---

### **2. Which of these is an example of client‑server separation in REST?**

```
a) The server renders UI and handles business logic
b) The client and server share database access
c) The client handles user interface, the server handles data storage and business logic
d) The client directly modifies server internal data structures
```

**Correct Answer:** **c**

---

### **3. Which header helps in defining whether a response is cacheable?**

```
a) Content‑Type
b) Cache‑Control
c) Authorization
d) Accept
```

**Correct Answer:** **b**

---

### **4. Which of the following is *not* one of the core REST architectural constraints?**

```
a) Stateless
b) Cacheable
c) Client‑Server
d) Synchronous Communication Only
```

**Correct Answer:** **d**

---

### **5. For URI design, which is considered good practice?**

```
a) Using verbs in resource names (e.g., /getUser)
b) Using nouns for resource collections (e.g., /users)
c) Including action words as part of the path (e.g., /users/delete)
d) Mixing plural and singular inconsistently (e.g., /user, /users)
```

**Correct Answer:** **b**

---

### **6. Which HTTP status code indicates that a new resource was created successfully?**

```
a) 200 OK
b) 201 Created
c) 204 No Content
d) 400 Bad Request
```

**Correct Answer:** **b**

---

### **7. When designing a RESTful API, which HTTP method is typically used to update a resource entirely?**

```
a) GET
b) POST
c) PUT
d) DELETE
```

**Correct Answer:** **c**

---

### **8. What is the best status code when a request is valid but the client has no permission to access the resource?**

```
a) 401 Unauthorized
b) 403 Forbidden
c) 404 Not Found
d) 400 Bad Request
```

**Correct Answer:** **b**

---

### **9. Which of the following URIs follows good REST design for accessing a single order with id 1234?**

```
a) /getOrder/1234
b) /orders?id=1234
c) /orders/1234
d) /order-service/orders/1234/getDetails
```

**Correct Answer:** **c**

---

### **10. What does the “uniform interface” constraint of REST entail?**

```
a) All resources share the same URI regardless of type
b) Clients must use the same HTTP method for all operations
c) A set of standardized ways (identification, representation, etc.) to interact with resources
d) The server only supports JSON responses
```

**Correct Answer:** **c**

---

### **11. If a GET request for a resource returns “304 Not Modified”, what does that imply?**

```
a) The resource was permanently removed
b) The resource has changed
c) The resource has not been modified since the client’s copy
d) The request had invalid syntax
```

**Correct Answer:** **c**

---

### **12. In a REST API, what is the advantage of being stateless?**

```
a) The server can hold many client sessions in memory
b) Easier horizontal scaling because the server does not need to remember prior requests
c) Clients can skip authentication after first request
d) The API must always return the same data for every request
```

**Correct Answer:** **b**

---

### **13. What’s wrong with the URI /users/createUser in a REST API?**

```
a) It uses plural users
b) It uses a verb createUser in the path
c) It includes an ID
d) It uses HTTP POST
```

**Correct Answer:** **b**

---

### **14. Which status code is appropriate when a client submits invalid JSON payload?**

```
a) 400 Bad Request
b) 404 Not Found
c) 409 Conflict
d) 200 OK
```

**Correct Answer:** **a**

---

### **15. For cache‑able responses, which of the following should the server ideally provide?**

```
a) Cache-Control: no-store for all responses
b) Cache-Control headers that specify how long responses are valid
c) Omit any caching header (so default caching)
d) Indicate caching only in the request, not in the response
```

**Correct Answer:** **b**

---

### **16. In a good REST API design, how should plural resource collection names be used?**

```
a) Always singular (e.g., /user)
b) Always plural (e.g., /users)
c) Mixed (singular for read, plural for create)
d) Verbs as resources (e.g., /createUsers)
```

**Correct Answer:** **b**

---

### **17. Which status code signals that the resource was successfully processed but no content is returned?**

```
a) 200 OK
b) 201 Created
c) 204 No Content
d) 202 Accepted
```

**Correct Answer:** **c**

---

### **18. A client tries to use HTTP DELETE on a resource but the server does not support DELETE for that resource — which status code is best?**

```
a) 400 Bad Request
b) 405 Method Not Allowed
c) 404 Not Found
d) 501 Not Implemented
```

**Correct Answer:** **b**

---

### **19. Which of the following is a violation of statelessness?**

```
a) Including authentication token in every request header
b) Server storing session state between requests
c) Each request containing full context
d) Server using HTTP caching for GET responses
```

**Correct Answer:** **b**

---

### **20. What does a URI design best practice suggest about versioning?**

```
a) Don’t version APIs; change them freely
b) Version the API in the path (e.g., /v1/users) or header
c) Use version in query parameter only (e.g., /users?version=1)
d) Mix multiple versions in same endpoint
```

**Correct Answer:** **b**

---

### **21. Which status code indicates that the server encountered an unexpected condition that prevented it from fulfilling the request?**

```
a) 500 Internal Server Error
b) 503 Service Unavailable
c) 502 Bad Gateway
d) 400 Bad Request
```

**Correct Answer:** **a**

---

### **22. What is good practice for nested resources in URI design?**

```
a) Avoid nesting and always flat structure
b) Use nesting when there is a clear hierarchical relationship, e.g., /users/123/orders/456
c) Use deeply nested paths for any related resources even if remote
d) Use verbs to indicate sub-actions, e.g., /users/123/processOrders
```

**Correct Answer:** **b**

---

### **23. What’s the benefit of declaring cacheability in REST responses?**

```
a) Client must always re-fetch the data
b) Reduce latency and server load by re-using responses where safe
c) Server can ignore client requests
d) Cacheability has no real benefit
```

**Correct Answer:** **b**

---

### **24. If a request is well-formed but the resource the client is trying to access doesn’t exist, which status code is appropriate?**

```
a) 400 Bad Request
b) 403 Forbidden
c) 404 Not Found
d) 410 Gone
```

**Correct Answer:** **c**

---

### **25. According to best practices, which HTTP method should you avoid exposing for simple resource retrieval?**

```
a) POST
b) GET
c) PUT
d) DELETE
```

**Correct Answer:** **a**

---

### **26. Which status code would you return if a client request tries to create a resource which already exists and duplicates are not allowed?**

```
a) 201 Created
b) 200 OK
c) 409 Conflict
d) 422 Unprocessable Entity
```

**Correct Answer:** **c**

---

### **27. Why is the separation of client and server important in REST?**

```
a) It forces server to render the UI
b) It allows client and server to evolve independently
c) The client must know the server database schema
d) The server must handle user interface logic
```

**Correct Answer:** **b**

---

### **28. What is wrong with the URI /products/ when you also have /products?id=123 for a single resource?**

```
a) It uses plural collection name
b) It uses query parameter to identify resource instead of path segment
c) It uses slash at end
d) Nothing is wrong
```

**Correct Answer:** **b**

---

### **29. In best practice status code usage: which category is for client errors?**

```
a) 1xx
b) 2xx
c) 3xx
d) 4xx
```

**Correct Answer:** **d**

---

### **30. Which status code is used when the method is accepted for processing, but the processing is not yet complete?**

```
a) 200 OK
b) 202 Accepted
c) 204 No Content
d) 201 Created
```

**Correct Answer:** **b**

---



## **What is Idempotence?**
Idempotence means: “Doing the same action many times has the same effect as doing it once.”