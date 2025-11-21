**1. What is the main purpose of the “2xx” class of status codes? How does 200 OK differ from 201 Created?**

    A) Client error; 200 = temporary error, 201 = permanent error
    B) Success; 200 = request succeeded generally, 201 = request succeeded and created a new resource ✅
    C) Redirection; 200 = redirect permanently, 201 = redirect temporarily
    D) Server error; 200 = server failed, 201 = server overload

---

**2. When are “3xx” redirection codes used, and what is the difference between 301 and 302?**

    A) Client error; 301 = temporary, 302 = permanent
    B) Server error; 301 = server failure, 302 = unavailable
    C) Redirection; 301 = resource moved permanently ✅, 302 = temporary redirect
    D) Success; 301 = created resource, 302 = updated resource

---

**3. What defines a “4xx” error and how is it different from a “5xx” error?**

    A) 4xx = server error, 5xx = client error
    B) 4xx = network error, 5xx = timeout
    C) 4xx = client-side error ✅, 5xx = server-side error
    D) 4xx = redirect, 5xx = success

---

**4. What do “5xx” status codes represent?**

    A) Client-side error
    B) Redirection
    C) Server-side error ✅
    D) Success

---

**5. If an API frequently returns 429 Too Many Requests, what does it mean?**

    A) Server crashed
    B) Client is rate-limited ✅
    C) Resource moved
    D) Request succeeded

---

**6. In REST API design, best practice for HTTP status codes is:**

    A) Always return 200 even for errors
    B) Use accurate semantics: 200/201/204 success, 400/404 client error, 500/503 server error ✅
    C) Ignore errors and log only
    D) Random status codes

---

**7. Two major HTTP/1.1 performance limitations and HTTP/2 solution:**

    A) High CPU usage → solved by caching
    B) Head-of-line blocking & multiple TCP connections → HTTP/2 multiplexing & header compression ✅
    C) Only supports GET → HTTP/2 supports POST
    D) Slow DNS → HTTP/2 removes DNS

---

**8. What is the performance function of `Connection: keep-alive`?**

    A) Closes connection after every request
    B) Reuses TCP connection for multiple requests/responses ✅
    C) Sends multiple requests in parallel
    D) Compresses data

---

**9. Common factors in all HTTP versions (0.9 to 3)?**

    A) Only supports GET
    B) Request-response model, methods, status codes, headers, text-based ✅
    C) Always uses TLS
    D) Only supports JSON

---

**10. What is meant by context in MCP?**

    A) Network address of AI
    B) Session cookies
    C) Set of resources, prompts, and tools available to AI ✅
    D) HTTP headers

---

**11. If you get 200 HTTP code but error in JSON-RPC, possible reason?**

    A) TCP failure
    B) Invalid HTTP method
    C) HTTP succeeded, but JSON-RPC layer rejected request ✅
    D) Server overloaded

---

**12. What problem does MCP solve in AI applications?**

    A) Faster HTTP
    B) Secure, standardized access between LLMs and external tools ✅
    C) GPU acceleration
    D) JSON formatting

---

**13. How does MCP differ from traditional REST APIs?**

    A) MCP is stateless only
    B) MCP: AI model = server, data provider = client ✅
    C) MCP uses XML only
    D) MCP has no authentication

---

**14. Explain client-server architecture in MCP.**

    A) AI model = client, data provider = server
    B) AI model = server, data/tools provider = client ✅
    C) Both are clients
    D) Both are servers

---

**15. Three main primitives in MCP:**

    A) GET, POST, DELETE
    B) Tools, Resources, Prompts ✅
    C) JSON, XML, CSV
    D) TCP, UDP, HTTP

---

**16. What is a "tool" in MCP?**

    A) Local script
    B) Remotely callable function exposed by client ✅
    C) Browser plugin
    D) HTTP header

---

**17. How does MCP server expose tools to AI clients?**

    A) Via FTP
    B) Using tools/list and tools/call JSON-RPC with name, description, JSON schema ✅
    C) Using email
    D) Using cookies

---

**18. Explain tool "discovery" in MCP.**

    A) Client guesses tool names
    B) Client calls tools/list to know available tools ✅
    C) Server pushes tools randomly
    D) Tools auto-installed

---

**19. How does resource URI structure work in MCP?**

    A) File paths only
    B) Unique, stable, scoped URIs (file://, http://, memory://) ✅
    C) IP addresses only
    D) Random numbers

---

**20. Concept of resource templates in MCP:**

    A) Hard-coded resources
    B) Parameterized URIs AI can fill (file://{path}) ✅
    C) Default HTTP headers
    D) CSS templates

---

**21. When to expose data as a resource vs creating a tool?**

    A) Frequent/static data → resource, expensive computation → tool ✅
    B) Always use tools
    C) Always use resources
    D) Depends on TCP port

---

**22. What are resources in MCP and how are they identified?**

    A) Functions; identified by name
    B) Data pieces exposed to AI; identified by URIs ✅
    C) Users; identified by ID
    D) Servers; identified by IP

---

**23. Purpose of prompts in MCP:**

    A) Auto-trigger actions
    B) Reusable, user-controlled message templates ✅
    C) HTTP headers
    D) JSON-RPC errors

---

**24. Example scenario combining prompt, resources, tool in MCP:**

    A) AI asks server randomly
    B) Code assistant: user prompt → AI selects code-explain prompt + file resource + run-code tool ✅
    C) Only HTTP GET
    D) Email notification

---

**25. Fundamental difference between stateful and stateless transports:**

    A) Stateful keeps session, allows server→client calls; stateless does not ✅
    B) Stateless is faster
    C) Stateful uses UDP
    D) Stateless uses cookies

---

**26. Why is STDIO stateful while Streamable HTTP can be either?**

    A) STDIO always uses TCP
    B) STDIO single pipe → stateful; Streamable HTTP can use sessions → stateful or stateless ✅
    C) HTTP cannot be stateful
    D) STDIO is faster

---

**27. What are "roots" in MCP and who exposes them?**

    A) Client-exposed directories for AI access ✅
    B) AI server folders
    C) JSON files
    D) HTTP endpoints

---

**28. Difference between roots and resources:**

    A) Roots = directories (boundaries), resources = files/data ✅
    B) Both same
    C) Roots = HTTP methods
    D) Resources = directories

---

**29. Four standard log levels in MCP:**

    A) Low, Medium, High, Critical
    B) error, warn, info, debug ✅
    C) trace, log, notice, fatal
    D) fatal, warn, info, notice

---

**30. FastMCP: stateless_http=True vs stateless_http=True + json_response=True:**

    A) First removes session & server→client; second also removes streaming ✅
    B) Both remove TCP
    C) Only removes logs
    D) Both disable HTTP

---

**31. JSON-RPC request with unquoted method/tool name:**

    A) Accepted
    B) Parse error (-32700) because JSON requires double quotes ✅
    C) Returns 404
    D) Ignored

---

**32. Client sends JSON-RPC with Multiply tool, not existing:**

    A) Success
    B) Error -32601 Unknown tool ✅
    C) Returns 200 OK
    D) Timeout

---

**33. Optional keys in MCP response:**

    A) content, isError
    B) structuredContent, progressToken, metadata ✅
    C) code, message, id
    D) jsonrpc only

---

**34. Syntax error in:**

```json
{ "jsonrpc": "2.0", "method": "resources/read" "params": {"uri": "file://test.txt"}, "id": 5 }
```

    A) Wrong method
    B) Missing comma between method & params ✅
    C) Invalid URI
    D) Missing id

---

**35. Is request `{ "method": "prompts/list", "params": {}, "id": 10 }` valid?**

    A) Yes
    B) No, missing jsonrpc field → error -32600 Invalid Request ✅
    C) No, wrong method
    D) Yes, optional id

---

**36. Three keys in error response and optional one:**

    A) code, message, data → data optional ✅
    B) error, message, id
    C) jsonrpc, result, id
    D) code, content, id

---

**37. Request:**

```json
{ "jsonrpc": "2.0", "method": "tool/execute", "params": { "name": "calculator" }, "id": 7 }
```

Expected response:
    A) Success
    B) Error -32601 Method not found ✅
    C) 200 OK
    D) Timeout

---

**38. MCP method to initialize connection:**

    A) start
    B) initialize ✅
    C) open
    D) connect

---

**39. Batch request in JSON-RPC:**

    A) Multiple requests in an array ✅
    B) Single request
    C) HTTP GET only
    D) TCP packet

---

**40. Idempotent HTTP methods:**

    A) POST, PATCH
    B) GET, PUT, DELETE, HEAD, OPTIONS, TRACE ✅
    C) GET only
    D) POST only

---

**41. Big difference between GET and POST:**

    A) GET changes state, POST does not
    B) GET safe, POST not safe (can change server state) ✅
    C) POST safe, GET not safe
    D) Both same

---

**42. HTTP method to delete a resource:**

    A) GET
    B) DELETE ✅
    C) POST
    D) PATCH

---

**43. HTTP method to update only some fields:**

    A) POST
    B) PUT
    C) PATCH ✅
    D) DELETE

---

**44. HTTP method used in web form signup:**

    A) GET
    B) POST ✅
    C) PUT
    D) PATCH

---

**45. HEAD method vs GET:**

    A) HEAD returns only headers ✅, GET returns full response
    B) HEAD returns full body
    C) HEAD = POST
    D) Same as GET

---

**46. Explain Client-Server constraint:**

    A) Client can access DB directly
    B) UI separated from data/storage → portability & scalability ✅
    C) Server controls client code
    D) No separation

---

**47. Four sub-rules of Uniform Interface:**

    A) Resource identification, Manipulation through representations, Self-descriptive messages, HATEOAS ✅
    B) GET, POST, PUT, DELETE
    C) TCP, HTTP, JSON, XML
    D) Server, Client, Proxy, Cache

---

**48. Explain HATEOAS:**

    A) Client sends only GET
    B) Responses contain links → clients discover next actions dynamically ✅
    C) Server auto-executes
    D) HTTP headers only

---

**49. Layered System constraint:**

    A) Client knows every layer
    B) Client cannot tell if connected to end server or intermediary ✅
    C) Only direct connection allowed
    D) Server hides data

---

**50. Cacheability constraint:**

    A) Responses stored & reused → improves performance ✅
    B) Always fresh data only
    C) Disables headers
    D) Only GET

---

**51. Code on Demand constraint (optional):**

    A) Server sends executable code (e.g., JS from CDN) ✅
    B) Client runs TCP
    C) Only GET allowed
    D) POST required


