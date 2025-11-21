: aik question tha keh jis mein method ka name double quotes mein nhi tha yani "foo" ki bjaye "foo  likha tha to is case mein koon sa error aye ga ?

: aik yeah tha keh jis mein id nhi thi to woh notification hota hey

: aik mein simple multiply ka  methodtha to output pocha tha like {method : "multiply" params:{4,3} and id:2 to output id:2,method:mutiply and result:12 hona chahey

: iskey ilawa methods ka pocha hua like post , put , patch or get isko achy se samajh lena









---

MCP (Model Context Protocol) Questions – Comprehensive Collection


---

1. HTTP & Status Codes in REST / MCP Context

1. What is the main purpose of the “2xx” class of status codes? How does 200 OK differ from 201 Created?


2. When are “3xx” redirection codes used, and what is the difference between 301 Moved Permanently and 302 Found?


3. What defines a “4xx” class error, and how is it different from a “5xx” class error?


4. What do “5xx” status codes represent?


5. If an API frequently returns 429 Too Many Requests, what does it mean, and how should clients respond?


6. In REST API design, what are the best practices for assigning and evaluating HTTP status codes?


7. Discuss two major performance limitations of HTTP/1.1 (specifically concerning TCP connection usage), and explain how HTTP/2 addresses both issues through features like multiplexing and header compression.


8. Describe the performance function of the Connection: keep-alive header in HTTP/1.1.


9. What are the common factors in all HTTP versions (0.9 to 3) or (1.0 to 3)?




---

2. MCP Concepts and JSON-RPC Basics

1. What is meant by context in terms of MCP?


2. If you get 200 HTTP code but an error in jsonrpc, what could be the possible reason?


3. What is the difference between tools and resources?


4. What will be the output of the following if the server doesn't have any tool?



{"jsonrpc":"2.0","id":1,"method":"tools/list"}

5. What will be the output of the following if the server has 4 tools?



{"jsonrpc":"2.0","method":"tools/list","params":{}}

6. Write a request to call a templated resource.


7. A server contains 3 tools and 4 resources; one of the requests requires a parameter. What will be the output of the following request?



{"jsonrpc":"2.0","id":1,"method":"resources/list"}

8. Write a request to call an addition tool that requires two parameters (a and b).




---

3. MCP Tools & Resources

1. What is the name of the method to call a tool, read a resource, and get a prompt?


2. What is the primary benefit of creating prompts in an MCP server?


3. What is the difference between SSE and streamable HTTP transport?


4. In what cases is STDIO useful?


5. What are the cons of SSE transport?


6. While defining resources, which is a required parameter?


7. When a client calls a tool in MCP, what kind of message is used to perform that call?


8. In MCP, what message does a client use to list all available prompts from a server?


9. What field in a tool’s JSON description tells the client what the tool actually does?


10. If a tool fails during execution (for example, an invalid parameter), what field is used in the JSON-RPC response?


11. When an MCP client calls tools/call, what two fields must always exist inside the params object for a valid tool invocation?


12. You want to create a tool that accesses local files but must not expose sensitive data. Which best practices align with MCP security principles?


13. In MCP resources, which parameter specifies the data format returned to the client?


14. Write client requests to fetch this resource via JSON-RPC:



@mcp.resource("https://documents", mime_type="application/json")
def documents() -> list[str]: 
    return list(docs.keys())

15. Write client requests to fetch this templated resource via JSON-RPC:



@mcp.resource("https://docs/{doc_id}", mime_type="text/plain")
def get_doc(doc_id: str) -> str: 
    return docs[doc_id]

16. What are the supported content types for the content field in a PromptMessage object?


17. Write a minimal JSON example of an MCP Prompt object for a "code_review" prompt.




---

4. Tool Execution & JSON-RPC Requests

1. You defined this tool inside your MCP server:



@mcp.tool()
def calculate_discount(price: float, discount: float) -> float:
    return price - (price * discount / 100)

The client sends this JSON-RPC request:

{
  "jsonrpc": "2.0",
  "method": "calculate_discount",
  "params": { "price": "1000", "discount": "10" }
}

What will most likely happen?

2. You modify the tool as follows:



@mcp.tool("calculate.discount")
def calc(price: float, discount: float) -> float:
    return price - (price * discount / 100)

What will be the correct method field for the client’s JSON-RPC request?

3. Which of the following is true about path parameters in MCP resources?
a) They are optional and do not need to match the function signature
b) They are automatically mapped to function arguments
c) They are used only for tools, not resources
d) They must always be integers


4. You define a resource like this:



@mcp.resource("https://data", mime_type="application/json")
def data_resource() -> dict:
    return {"a": 1, "b": 2}

Which HTTP method does this resource use by default when accessed via FastMCP or MCP?
a) POST
b) GET
c) PUT
d) DELETE

5. You have a resource defined as:



@mcp.resource("https://docs/{doc_id}", mime_type="text/plain")
def get_doc(doc_id: str) -> str:
    return docs.get(doc_id)

What happens if a client calls /docs/nonexistent_doc?
a) Server returns the string "None"
b) Server raises a Python exception
c) Server returns HTTP 404 automatically
d) Server crashes


---

5. MCP Transport & Server Behavior

1. What are the three main transport types available in MCP?


2. What does stateless mean in the context of MCP servers?


3. What is the difference between stateless and stateful transports?


4. When you set stateless_http=True and json_response=True, what happens?


5. When you set stateless_http=True and json_response=False, what happens?


6. What is SSE (Server-Sent Events) and how does it work?


7. Can you send progress notifications with json_response=True?


8. What's the advantage of using SSE over single JSON responses?


9. How does stdio transport work?


10. Is stdio transport stateful or stateless?


11. When would you choose stdio transport over HTTP transport?


12. What is a JSON-RPC batch request?


13. How do logs and progress work in stateless servers?


14. Can a stateless server send notifications during request processing?


15. What does await ctx.info("message") do?


16. What does await ctx.report_progress(80, 100) mean?


17. What notification methods are available in the Context object?


18. You're building an MCP server that processes large files and takes 2-3 minutes. Users need to see progress. What transport configuration should you use and why?




---

6. Sample / Root-Level MCP Questions (Added)

1. Build a minimal MCP server that contains 1 tool and 3 resources:

Tool: Uses any API to fetch data

Resource: Accesses any hardcoded Python data structure

Templated Resource: Accesses any specified file from the project directory

Resource: Reads data from the web



2. Explain best practices for exposing local files via MCP tools/resources.


3. How can progress updates improve the client experience in long-running MCP tasks?


4. What is the difference between prompt-based resource calls and direct tool calls?


5. Write a JSON-RPC example to call a tool with multiple parameters, including validation.












Got it! I’ll generate a **20-question multiple-choice quiz** covering all the topics you listed, with each question having **4 options and one correct answer**. I’ll make it exam-focused and advanced-level.

---

### **HTTP & REST Fundamentals**

**1.** Which of the following best describes HTTP?
A) A protocol for sending files only
B) A stateless request–response protocol
C) A protocol that maintains session by default
D) A database query language
**Answer:** B

**2.** In HTTP, what does a 404 status code indicate?
A) Successful request
B) Resource not found
C) Server error
D) Unauthorized access
**Answer:** B

**3.** Which HTTP method is idempotent and used to update a resource?
A) POST
B) PUT
C) PATCH
D) DELETE
**Answer:** B

**4.** REST principle “statelessness” means:
A) Server stores session info for each client
B) Each request contains all information for processing
C) Client cannot send multiple requests
D) Only GET requests are allowed
**Answer:** B

**5.** Which of these is a recommended REST URI design practice?
A) Use verbs in the URI
B) Use nouns and hierarchical structure
C) Include file extensions like `.php`
D) Include query parameters for resource identification
**Answer:** B

---

### **JSON-RPC 2.0**

**6.** In JSON-RPC, which object is optional for notifications?
A) `jsonrpc`
B) `method`
C) `id`
D) `params`
**Answer:** C

**7.** What is the difference between a JSON-RPC request and a notification?
A) Requests expect a response, notifications do not
B) Notifications require authentication
C) Requests are transport-agnostic, notifications are not
D) Notifications are only for errors
**Answer:** A

**8.** Reserved method names in JSON-RPC include:
A) `echo`
B) `subtract`
C) `rpc.*`
D) `getInfo`
**Answer:** C

**9.** JSON-RPC is transport-agnostic. What does this mean?
A) It can only work over HTTP
B) It can be used over multiple transports like WebSocket, TCP, HTTP
C) It stores session data on the server
D) It requires encryption
**Answer:** B

**10.** Which JSON-RPC field contains the parameters for a method call?
A) `jsonrpc`
B) `method`
C) `params`
D) `id`
**Answer:** C

---

### **MCP Fundamental Primitives**

**11.** What is the primary role of an MCP server?
A) To store client-side data
B) To provide tools and execute client requests
C) To maintain HTTP connections only
D) To convert JSON to XML
**Answer:** B

**12.** In MCP, which primitive lists the available tools on the server?
A) CallTool
B) ListTools
C) InvokeTool
D) GetResources
**Answer:** B

**13.** MCP architecture is transport-agnostic. This means:
A) It only works over HTTP
B) It can function over multiple transports (HTTP, WebSocket, etc.)
C) It requires persistent TCP sessions
D) It is only compatible with OpenAI SDK
**Answer:** B

**14.** The MCP primitive used to invoke a server tool is:
A) ListTools
B) CallTool
C) NotifyTool
D) RunTool
**Answer:** B

**15.** Which statement about MCP Clients is correct?
A) Clients host tools
B) Clients only send requests and process responses
C) Clients cannot use JSON-RPC
D) Clients maintain tool databases
**Answer:** B

---

### **Advanced MCP Topics**

**16.** What is MCP sampling used for?
A) Listing all client connections
B) Controlling and filtering tool outputs
C) Encrypting server logs
D) Managing HTTP headers
**Answer:** B

**17.** MCP logging helps:
A) Store session data
B) Communicate server state and debug info to clients
C) Generate random tool outputs
D) Authenticate clients
**Answer:** B

**18.** MCP progress notifications are useful for:
A) Monitoring long-running tasks in real-time
B) Storing sensitive information
C) Encrypting messages
D) Creating REST APIs
**Answer:** A

**19.** What does the MCP “roots” feature handle?
A) User authentication
B) Security and trust in tool execution
C) Tool discovery
D) HTTP routing
**Answer:** B

**20.** Which transport configuration allows MCP to remain stateless?
A) WebSocket with sessions
B) Stateless HTTP
C) TCP with persistent connection
D) HTTPS with cookies
**Answer:** B

---

### **MCP & OpenAI Agents SDK Integration**

**21.** MCP integration with OpenAI Agents allows:
A) Automatic UI rendering
B) Tool discovery and invocation from within agents
C) Storing agent context in local files
D) Only HTTP GET calls
**Answer:** B

**22.** Stateless MCP connections in OpenAI Agents mean:
A) Agents must store all conversation context themselves
B) Servers save client sessions automatically
C) Clients cannot call tools
D) Connections use WebSocket exclusively
**Answer:** A

**23.** MCP workflows in OpenAI Agents can:
A) Run multiple tools in sequence automatically
B) Only call a single tool per session
C) Ignore JSON-RPC rules
D) Execute non-MCP tasks only
**Answer:** A

**24.** Which of the following is NOT part of MCP & OpenAI Agents SDK integration?
A) Tool discovery
B) Prompts
C) Sessionless execution
D) File system monitoring
**Answer:** D

**25.** When integrating MCP with OpenAI Agents, what is a primary advantage?
A) Built-in encryption of all messages
B) Ability to extend agent capabilities using server tools
C) Agents no longer need prompts
D) Eliminates the need for JSON-RPC
**Answer:** B

---

Based on the sequence diagram you uploaded, here are **5 quiz questions**:

---

**1.** In the sequence diagram, which MCP primitive is used to retrieve the list of available tools from the MCP Server?
A) CallToolRequest
B) ListToolsRequest
C) ToolUse
D) Query + Tools
**Answer:** B

---

**2.** After the MCP Server responds with `ListToolsResult`, what is the next step in the workflow?
A) User directly requests GitHub
B) MCP Client sends `CallToolRequest`
C) Our Server sends `Query + Tools` to Claude
D) MCP Server executes `ToolUse` on GitHub
**Answer:** C

---

**3.** Which component in the diagram is responsible for actually sending the request to GitHub?
A) MCP Client
B) Our Server
C) MCP Server
D) Claude
**Answer:** C

---

**4.** What is the purpose of the `CallToolResult` in the MCP workflow?
A) To request the list of tools from the server
B) To provide the result of running a tool back to the MCP Client
C) To initiate a new session with Claude
D) To store repository info in Our Server
**Answer:** B

---

**5.** In this workflow, which statement is true about the role of Claude?
A) Claude lists tools and executes them
B) Claude queries the MCP Server directly for repositories
C) Claude receives a query with tools and orchestrates tool execution
D) Claude stores results locally and sends them to GitHub
**Answer:** C

---






