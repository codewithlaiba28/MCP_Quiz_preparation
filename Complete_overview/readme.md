Here is a comprehensive 25-question multiple-choice quiz covering all the topics from the exam content. It includes a mix of easy, medium, and hard questions. Answers with brief explanations are provided at the end.

### Quiz: AI Protocols – HTTP, REST, JSON-RPC & MCP

**1. HTTP is fundamentally:**
   - A) Stateful protocol  
   - B) Stateless protocol  
   - C) Connection-oriented only  
   - D) Binary protocol  
   
**2. In an HTTP request, the line “POST /users HTTP/1.1” is called:**
   - A) Header  
   - B) Request Line / Start Line  
   - C) Body  
   - D) Trailer  

**3. Which of the following HTTP methods is idempotent?**
   - A) POST  
   - B) PATCH  
   - C) PUT  
   - D) DELETE  

**4. Which status code indicates that the request requires user authentication?**
   - A) 401 Unauthorized  
   - B) 403 Forbidden  
   - C) 404 Not Found  
   - D) 407 Proxy Authentication Required  

**5. According to REST architectural constraints, which one is NOT a core principle?**
   - A) Statelessness  
   - B) Cacheability  
   - C) Mandatory use of JSON  
   - D) Uniform Interface  

**6. In proper RESTful URI design, which is the best representation for retrieving a specific order?**
   - A) /getOrder?orderId=123  
   - B) /orders/123  
   - C) /order/123/get  
   - D) /api/v1/Order.php?id=123  

**7. In JSON-RPC 2.0, a request that does NOT expect a response is called:**
   - A) Batch  
   - B) Notification  
   - C) Method Call  
   - D) Error  

**8. In JSON-RPC 2.0, the “jsonrpc” member in every object MUST have the value:**
   - A) “2.0”  
   - B) “1.0”  
   - C) Any string  
   - D) 2  

**9. Which of these method names are reserved in JSON-RPC 2.0 (i.e., clients/servers must not use them)?**
   - A) rpc.info  
   - B) rpc.discover  
   - C) Both A and B  
   - D) None  

**10. MCP (Model Communication Protocol) is:**
    - A) Tied exclusively to HTTP  
    - B) Transport-agnostic  
    - C) Only for streaming tokens  
    - D) Stateful by design  

**11. In MCP, the client first sends which message to discover available tools?**
    - A) CallTool  
    - B) ListTools  
    - C) Sample  
    - D) Progress  

**12. The primary roles in MCP are:**
    - A) Agent and Orchestrator  
    - B) MCP Client and MCP Server  
    - C) Tool Provider and Tool Consumer  
    - D) Frontend and Backend  

**13. In MCP, a “sampling” request is used for:**
    - A) Listing tools  
    - B) Getting progressive token generation (streaming/completion)  
    - C) Logging only  
    - D) Authentication  

**14. MCP supports progress notifications. These are sent:**
    - A) Only from client to server  
    - B) Only from server to client  
    - C) Bidirectionally  
    - D) Never  

**15. Security/trust in MCP is primarily established through:**
    - A) JWT tokens  
    - B) Root certificates / trust roots  
    - C) API keys in headers  
    - D) OAuth2  

**16. Which transport configuration allows MCP to run fully stateless over plain HTTP?**
    - A) WebSocket only  
    - B) Server-Sent Events (SSE)  
    - C) HTTP long-polling with session cookies  
    - D) Stateless HTTP with full state in each request/response  

**17. In the OpenAI Agents SDK integration, tool discovery happens via:**
    - A) OpenAI function calling schema  
    - B) MCP ListTools message  
    - C) Hard-coded tool definitions  
    - D) Separate OpenAPI endpoint  

**18. When using MCP with OpenAI Agents SDK, the connection is typically:**
    - A) Stateful WebSocket kept open for the entire conversation  
    - B) Stateless – new connection per turn is acceptable  
    - C) Required to use HTTPS only  
    - D) Only local Unix sockets  

**19. Which HTTP status code should a RESTful tool endpoint return when it successfully executes a tool but the tool itself wants to signal “no content” (e.g., a delete operation)?**
    - A) 200 OK  
    - B) 201 Created  
    - C) 204 No Content  
    - D) 202 Accepted  

**20. In JSON-RPC 2.0 error objects, the standard error code for “Method not found” is:**
    - A) -32600  
    - B) -32601  
    - C) -32602  
    - D) -32700  

**21. MCP CallTool requests may contain which parameter type(s)?**
    - A) Only positional parameters  
    - B) Only named parameters  
    - C) Positional, named, or both (depending on tool definition)  
    - D) Neither – parameters are sent in headers  

**22. Which of the following is a valid way to send a JSON-RPC notification?**
    - A) Include “id”: null  
    - B) Omit the “id” member entirely  
    - C) Set “id” to 0  
    - D) Both A and B are valid  

**23. In advanced MCP workflows, “logging” messages are used for:**
    - A) Debugging and audit trails only  
    - B) Allowing the server to log intermediate thoughts/tool usage  
    - C) Required for billing  
    - D) Replacing progress notifications  

**24. REST’s “Layered System” constraint allows:**
    - A) Proxies, gateways, and load balancers without the client knowing  
    - B) Only direct client-server communication  
    - C) Mandatory encryption at every layer  
    - D) Stateful sessions across layers  

**25. When integrating MCP with OpenAI Agents SDK, the recommended prompt pattern includes:**
    - A) Never mentioning tools  
    - B) Instructing the model to use the provided tools via MCP when needed  
    - C) Pre-calling ListTools in the system prompt  
    - D) Hard-coding tool schemas in the user message  

### Answer Key with Explanations

1. B) Stateless protocol  
2. B) Request Line / Start Line  
3. C) PUT (also DELETE, GET; PATCH is not guaranteed idempotent)  
4. A) 401 Unauthorized  
5. C) Mandatory use of JSON (REST is representation-agnostic)  
6. B) /orders/123 (resource-based, noun, hierarchical)  
7. B) Notification  
8. A) “2.0”  
9. C) Both A and B (all methods starting with rpc. are reserved)  
10. B) Transport-agnostic  
11. B) ListTools  
12. B) MCP Client & MCP Server  
13. B) Getting progressive token generation  
14. C) Bidirectionally (though server→client is most common)  
15. B) Root certificates / trust roots  
16. D) Stateless HTTP with full state in each request/response  
17. B) MCP ListTools message  
18. B) Stateless – new connection per turn is acceptable  
19. C) 204 No Content  
20. B) -32601  
21. C) Positional, named, or both  
22. D) Both A and B are valid (id must be omitted or null for notifications)  
23. B) Allowing the server to log intermediate thoughts/tool usage  
24. A) Proxies, gateways, and load balancers without the client knowing  
25. B) Instructing the model to use the provided tools via MCP when needed  

Feel free to use this quiz for study or actual examination. Good luck! 🚀



Here is a clean, short, exam-style **quiz** covering all 6 topics.
(10 MCQs + 10 Theoretical Questions)

---

# ✅ **MCP + HTTP + REST + JSON-RPC + Agents SDK — Quiz**

---

## **📝 MCQs**

### **1. In HTTP, which method is used to retrieve data without modifying it?**

A. POST
B. GET
C. PUT
D. PATCH
**Correct Answer: B**

---

### **2. What does “statelessness” mean in REST?**

A. Server stores user session
B. Client stores no data
C. Each request contains all required information
D. Server runs without a database
**Correct Answer: C**

---

### **3. Which HTTP status code indicates a resource was successfully created?**

A. 200
B. 201
C. 204
D. 304
**Correct Answer: B**

---

### **4. In JSON-RPC 2.0, a request **without** `"id"` is called:**

A. Error
B. Notification
C. Response
D. Method Object
**Correct Answer: B**

---

### **5. What is the main responsibility of an MCP Client?**

A. Execute tools
B. Expose tools
C. Call server tools
D. Validate HTTP headers
**Correct Answer: C**

---

### **6. Which MCP message is used to discover tools available on the server?**

A. CallTool
B. ListTools
C. Notify
D. RegisterTool
**Correct Answer: B**

---

### **7. Sampling in MCP is used for:**

A. Authentication
B. Multi-step reasoning using LLMs
C. Storing logs
D. Returning binary data
**Correct Answer: B**

---

### **8. In JSON-RPC, `"code": -32600` represents:**

A. Internal error
B. Invalid Request
C. Method not found
D. Parse error
**Correct Answer: B**

---

### **9. When integrating MCP with the OpenAI Agents SDK, tools are discovered using:**

A. Prompts
B. HTTP headers
C. ListTools
D. REST Mapping
**Correct Answer: C**

---

### **10. In MCP stateless HTTP transport, each request is:**

A. Persistent
B. Stateful
C. Completely independent
D. Multi-session
**Correct Answer: C**

---

# ✏️ **Theoretical Questions (Short answers)**

### **1. Explain the HTTP request–response cycle in simple words.**

### **2. Why is client-server separation important in REST?**

### **3. What makes JSON-RPC “transport agnostic”?**

### **4. Describe the difference between a JSON-RPC Request and Notification.**

### **5. What are ListTools and CallTool messages used for in MCP?**

### **6. Explain how sampling improves the reasoning process in MCP.**

### **7. What is the purpose of logging in MCP servers?**

### **8. How does stateless HTTP transport affect MCP server design?**

### **9. How does the OpenAI Agents SDK use MCP tools inside an agent workflow?**

### **10. What security role do “roots” play in MCP?**

---

If you want, I can generate **more MCQs**, **hard MCQs**, **coding-based questions**, or a **full exam with answers**.









