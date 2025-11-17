https://github.com/panaversity/learn-agentic-ai/tree/main/03_ai_protocols/01_mcp/03_json_rpc

---

### **1. What remains the same from JSON-RPC version 0.9 up to version 3?**

A) Transport protocol only\
B) Core request-response model, `method`, `params`, `id`\
C) Only error codes\
D) JSON format changes completely

**Answer:** B

---

### **2. When something is created, which status code is returned?**

A) 200 OK\
B) 201 Created\
C) 400 Bad Request\
D) 500 Internal Server Error

**Answer:** B

---

### **3. MCP ke JSON-RPC messages kin tin types me ho sakte hain?**

A) Requests, Responses, Notifications\
B) Requests, Responses, Errors\
C) Requests, Notifications, Errors\
D) Requests, Methods, Responses

**Answer:** A

---

### **4. Which HTTP method is typically used for JSON-RPC calls in AI agent interactions?**

A) GET\
B) POST\
C) PUT\
D) DELETE

**Answer:** B

---

### **5. How does JSON-RPC handle errors in responses?**

A) Returns only a numeric code\
B) Returns an `error` object containing `code`, `message`, and optionally `data`\
C) Sends a different HTTP status code only\
D) Ignores the error

**Answer:** B

---

### **6. What is the primary purpose of JSON-RPC in the context of AI protocols like MCP?**

A) To transfer large files between agents\
B) To provide a lightweight, transport-agnostic method invocation protocol\
C) To replace TCP/IP\
D) To manage database connections

**Answer:** B

---

### **7. What can the type of `data` in an error object be?**

A) Only string\
B) Only number\
C) Any valid JSON value\
D) Only boolean

**Answer:** C

---

### **8. Which three members are required in a valid JSON-RPC Response object for a successfully executed request?**

A) `jsonrpc`, `result`, `id`\
B) `jsonrpc`, `method`, `params`\
C) `result`, `error`, `id`\
D) `method`, `id`, `jsonrpc`

**Answer:** A

---

### **9. Which two members are mandatory in a JSON-RPC Error object?**

A) `code` and `message`\
B) `code` and `result`\
C) `id` and `jsonrpc`\
D) `method` and `params`

**Answer:** A

---

### **10. If the server cannot find the method referenced in the request, which standard JSON-RPC error code should it return?**

A) -32600\
B) -32601\
C) -32700\
D) -32000

**Answer:** B

---

### **11. What two formats are supported for passing parameters to a method via the `params` member in JSON-RPC 2.0?**

A) Array (positional) and Object (named)\
B) String and Number\
C) Boolean and Array\
D) Object and String

**Answer:** A

---

### **12. Compared to a traditional REST API, what does the JSON-RPC protocol primarily focus on?**

A) Resource-based operations\
B) Method invocation and response handling\
C) File uploads\
D) Browser rendering

**Answer:** B

---

### **13. In JSON-RPC, what is a Batch Request?**

A) Sending multiple requests as a single array in one HTTP call\
B) Sending one request multiple times\
C) Sending notifications only\
D) Sending multiple responses

**Answer:** A


### **1. What is the main difference between a JSON-RPC request and a notification?**

A) Both expect a response\
B) Request has `id` and expects a response; notification has no `id` and expects no response\
C) Notification has `id` and expects a response\
D) Request never expects a response

**Answer:** B

---

### **2. Which field indicates that a JSON-RPC message expects a response?**

A) `method`\
B) `params`\
C) `id`\
D) `jsonrpc`

**Answer:** C

---

### **3. Which field is not allowed in a notification?**

A) `method`\
B) `id`\
C) `params`\
D) `jsonrpc`

**Answer:** B

---

### **4. What fields must a valid JSON-RPC response contain?**

A) `jsonrpc`, `result` or `error`, and `id`\
B) `method` and `params` only\
C) `jsonrpc` and `method`\
D) `result` only

**Answer:** A

---

### **5. What are the three fields of a JSON-RPC error object?**

A) `code`, `message`, `data` (optional)\
B) `method`, `params`, `id`\
C) `result`, `id`, `jsonrpc`\
D) `errorCode`, `errorMsg`, `errorData`

**Answer:** A

---

### **6. Why is JSON-RPC considered transport-agnostic?**

A) Because it only works over HTTP\
B) Because it can work over any transport like HTTP, WebSocket, or stdio\
C) Because it requires a database connection\
D) Because it is only for notifications

**Answer:** B

---

### **7. What are “reserved method names” in JSON-RPC 2.0?**

A) Names starting with `rpc.` reserved for system-level operations\
B) Any user-defined method names\
C) Only methods with numbers in their name\
D) Methods without parameters

**Answer:** A

---

### **8. How are positional parameters different from named parameters in JSON-RPC requests?**

A) Positional parameters are key–value; named parameters are arrays\
B) Positional parameters are arrays; named parameters are key–value objects\
C) Both are arrays\
D) Both are key–value objects

**Answer:** B

---

### **9. When should a server return an error instead of a normal result?**

A) When the request is valid\
B) When parameters are missing, invalid, or an internal error occurs\
C) Always\
D) Only for notifications

**Answer:** B

---

### **10. Why must every message include `"jsonrpc": "2.0"`?**

A) To identify the protocol version clearly\
B) To include user data\
C) To specify transport protocol\
D) It is optional

**Answer:** A

---


### **1. When JSON-RPC is enabled, what becomes possible between client and server?**

A) File transfer only\
B) Remote method calls\
C) Only notifications\
D) None of the above

**Answer:** B

---

### **2. When JSON-RPC is enabled, which message format must be followed?**

A) XML format\
B) JSON-RPC 2.0 format (`jsonrpc`, `method`, `params`, `id`)\
C) Plain text format\
D) Binary format

**Answer:** B

---

### **3. Enabling JSON-RPC allows communication over which transport?**

A) HTTP only\
B) WebSocket only\
C) Transport-agnostic (HTTP, WebSocket, stdio, etc.)\
D) TCP only

**Answer:** C

---

### **4. How does JSON-RPC handle errors when it is enabled?**

A) Ignores them\
B) Sends errors in a standard `error` object with `code`, `message`, and optional `data`\
C) Sends only HTTP error codes\
D) Logs errors locally only

**Answer:** B

---

### **5. When JSON-RPC is enabled, do notifications require a response from the server?**

A) Yes, always\
B) No, notifications do not require a response\
C) Only for positional parameters\
D) Only if the server is HTTP

**Answer:** B

---
### **6. Question: What will happen when the server receives this request?**

```
{
  "jsonrpc": "2.0",
  "method": "getUserData",
  "params": {"userId": 123},
  "id": null
}
```


A) The server treats it as a normal request and sends a response with id: null.\
B) The server treats it as a notification and does not send any response.\
C) The server throws an error because id cannot be null.\
D) The server automatically generates a numeric id and returns a response.

**Answer:** B

----

### **7. Which of the following statements is correct?**

A) A Response object can contain both result and error together.\
B) A Response object must contain either result or error, but not both.\
C) A Response object must contain result and error both.\
D) A Response object can omit both result and error.

**Answer:** B

---

### **8. What is the optional field inside an error object that provides additional details?**

A) result\
B) data\
C) jsonrpc\
D) method

**Answer:** B

-

### **Question (Scenario)**

A client sends a request to the server to get a message. The server responds:

```json
{
  "jsonrpc": "2.0",
  "result": {
    "text": {
      "type": "string",
      "content": "Hello, Laiba!"
    }
  },
  "id": 1
}
```

**Question:** Where does the actual answer from the server appear?

A) In the `id` field\
B) In the `jsonrpc` field\
C) In `result.text.content`\
D) In `result.text.type`

**Answer:** C

---


### **1. In a JSON-RPC response, what does the `code` field inside the `error` object represent?**

A) The type of error as an integer\
B) The textual description of the error\
C) The ID of the request\
D) The protocol version

**Answer:** A

---

### **2. Which of the following fields in a JSON-RPC `error` object is optional?**

A) `code`\
B) `message`\
C) `data`\
D) `id`

**Answer:** C

---

### **1. Identify the Error**

```json
{
  "jsonrpc": "2.0",
  "method": "getUserData",
  "params": {"userId": 1}
  "id": 1
}
```

**Question:** What is the error in this request?

A) Method not found (-32601)
B) Parse error (-32700)
C) Invalid params (-32602)
D) Internal error (-32603)

**Answer:** B


---

### **2. Identify the Error**

```json
{
  "jsonrpc": "2.0",
  "method": "getUserProfile",
  "params": {"userId": 1},
  "id": 1
}
```

**Question:** What is the error in this request if server does not have this method?

A) Invalid Request (-32600)
B) Method not found (-32601)
C) Invalid params (-32602)
D) Parse error (-32700)

**Answer:** B


---

### **3. Identify the Error**

```json
{
  "jsonrpc": "2.0",
  "method": "getUserData",
  "params": {"user": 1},
  "id": 1
}
```

**Question:** What is wrong with this request?

A) Invalid params (-32602)
B) Internal error (-32603)
C) Parse error (-32700)
D) Server error (-32001)

**Answer:** A



----
-


### **Question 1:**
What is the main purpose of sending multiple Request objects in a batch?
a) To reduce network overhead by sending multiple requests at once
b) To make the server ignore some requests
c) To ensure responses are always in the order of requests
d) To create multiple servers

**Answer:** a) To reduce network overhead by sending multiple requests at once

---

### **Question 2:**
When a server receives a batch of requests, in what order can it process them?
a) Only in the order received
b) Any order
c) Randomly, but must match the client’s order in response
d) Alphabetical order of method names

**Answer:** b) Any order

---

### **Question 3:**
How does the client match a response to its original request in a batch?
a) By the position of the response in the array
b) By the `id` of each request
c) By the method name
d) By the timestamp

**Answer:** b) By the `id` of each request

---


### **Question 5:**
Which data structure is used to send multiple requests in a batch?
a) Object
b) Array
c) String
d) Dictionary

**Answer:** b) Array

---



**Question 1:**
Look at the following JSON-RPC request:

```json
{"jsonrpc": "2.0", "method": "subtract", "params": [42, 23], "id": 1}
```

What will be the correct server response?

a) `{"jsonrpc": "2.0", "result": 23, "id": 1}`\
b) `{"jsonrpc": "2.0", "result": 19, "id": 1}`\
c) `{"jsonrpc": "2.0", "error": "Invalid params", "id": 1}`\
d) `{"jsonrpc": "2.0", "result": 65, "id": 1}`

**Answer:** b) `{"jsonrpc": "2.0", "result": 19, "id": 1}`

---


**Question 3:**
Which of the following JSON-RPC requests is a **notification** (does not expect a response)?

a)

```json
{"jsonrpc": "2.0", "method": "update", "params": [1, 2, 3, 4, 5]}
```

b)

```json
{"jsonrpc": "2.0", "method": "subtract", "params": [42, 23], "id": 1}
```

**Answer:** a)

---

**Question 4:**
If a client calls a non-existent method like this:

```json
{"jsonrpc": "2.0", "method": "foobar", "id": "1"}
```

What will the server respond with?

a) `{"jsonrpc": "2.0", "result": null, "id": "1"}`\
b) `{"jsonrpc": "2.0", "error": {"code": -32601, "message": "Method not found"}, "id": "1"}`\
c) `{"jsonrpc": "2.0", "result": 0, "id": "1"}`\
d) No response

**Answer:** b)

---


### **Quiz Question: JSON-RPC Subtract with Capital M**

Consider the following JSON-RPC request:

```json
{"jsonrpc": "2.0", "method": "subtract", "params": {"subtrahend": 23, "Minuend": 42}, "id": 3}
```

**Question:**
What will happen when the server receives this request?

a) The server will correctly subtract 23 from 42 and return 19./
b) The server will return an error because it cannot find the key `minuend`./
c) The server will ignore the `Minuend` key and return 23 as the result./
d) The server will automatically convert `Minuend` (capital M) to `minuend` (lowercase) and return 19.

**Answer:** b) 


---

### **Quiz Question: Invalid JSON in JSON-RPC Request**

```json
{"jsonrpc": "2.0", "method": "subtract", "params": {"Laiba }, "id": 3}
```

**Question:**
What will happen when the server receives this request?

a) The server will correctly process the request and return a result.
b) The server will ignore the invalid key `"Laiba"` and return `null`.
c) The server will return a **parse error** because the JSON is invalid.
d) The server will automatically fix the JSON and process the request.

**Answer:** c) The server will return a **parse error** because the JSON is invalid.


---


### **Quiz Question: Reserved Method Names in JSON-RPC**

**Question:**
In JSON-RPC, method names that start with `rpc.` are:

a) Allowed for any custom methods
b) Reserved for **system extensions** and should not be used for anything else
c) Used for batch requests only
d) Ignored by the server

**Answer:** b) Reserved for **system extensions** and should not be used for anything else


---

### **Quiz Question: Agent/Model Operations vs REST**

**Question 1:**
Why do LLM/Agent orchestration protocols like MCP need more than REST’s CRUD operations?

a) Because REST cannot handle HTTP requests
b) Because MCP sessions involve rich procedural operations like start, cancel, resume, and streaming
c) Because REST is slower than JSON-RPC
d) Because MCP does not use the internet

**Answer:** b) Because MCP sessions involve rich procedural operations like start, cancel, resume, and streaming

---

**Question 2:**
What is the main advantage of using JSON-RPC for agent/model operations?

a) It is built around CRUD operations
b) It allows remote procedure calls, treating functions on a server as if they were local
c) It automatically handles HTTP caching
d) It only works for database queries

**Answer:** b) It allows remote procedure calls, treating functions on a server as if they were local

---

**Question 3:**
Which of the following operations in MCP **cannot be mapped neatly** to REST CRUD verbs?

a) Start a session
b) Cancel a session
c) Resume a session
d) All of the above

**Answer:** d) All of the above

---


