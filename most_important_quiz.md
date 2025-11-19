**What is the primary purpose of the Model Context Protocol (MCP)?**

    a) To optimize LLM training datasets
    b) To connect AI models to external tools, data sources, and workflows securely
    c) To compress JSON data for faster transmission
    d) To manage GPU resources in agentic AI systems

**In the context of agentic AI, MCP acts as:**

    a) A universal adapter between AI applications and external services
    b) A caching mechanism for model outputs
    c) A debugging tool for prompt engineering
    d) A visualization library for AI workflows    

**MCP is designed to enable:**

    a) Stateless communication only
    b) Stateful, two-way communication between clients and servers
    c) One-way broadcasting to multiple models
    d) Local file storage for contexts    


**In MCP, the client typically refers to:**

    a) The external tool or database
    b) The AI model or application invoking tools
    c) The transport layer middleware
    d) The error handling module    


**One key benefit of MCP over custom API integrations is:**

    a) Increased latency for better accuracy
    b) Standardized, secure, and interoperable connections
    c) Requirement for proprietary hardware
    d) Limitation to single-language implementations    


**MCP supports real-time interactions primarily through:**

    a) Batch processing queues
    b) Lightweight remote procedure calls (RPCs)
    c) Email notifications
    d) File-based polling    


**JSON-RPC 2.0 is a protocol for:**

    a) Database querying
    b) Remote procedure calls using JSON encoding
    c) Image processing in AI models
    d) Vector embeddings  


**In JSON-RPC 2.0, what is the required field in every request object?**

    a) "params"
    b) "jsonrpc" (set to "2.0")
    c) "error"
    d) "session_id"

**Which field in a JSON-RPC request identifies the message for matching with responses?**

    a) "method"
    b) "id"
    c) "result"
    d) "transport"    


**JSON-RPC supports three types of messages:**

    a) Requests, Responses, and Errors
    b) Requests, Notifications, and Batch Requests
    c) Prompts, Tools, and Resources
    d) Clients, Servers, and Transports    


**A JSON-RPC Notification differs from a Request because:**

    a) It requires a response
    b) It has no "id" field and expects no reply
    c) It uses binary encoding
    d) It is only for errors    


**What is the standard error code for "Invalid Request" in JSON-RPC 2.0?**

    a) -32600
    b) -32700
    c) 200
    d) 404    


**In JSON-RPC, the "params" field can be structured as:**

    a) Only an array
    b) Only an object
    c) Either an array or an object
    d) A string only    


**Batch requests in JSON-RPC allow:**

    a) Only one method per batch
    b) Multiple requests in a single array for parallel processing
    c) Error handling without codes
    d) Mandatory responses for all   


**JSON-RPC 2.0 is transport-agnostic, meaning it works over:**

    a) HTTP, WebSockets, stdio, etc.
    b) Only HTTP POST
    c) TCP sockets exclusively
    d) UDP broadcasts
**The "result" field in a JSON-RPC response contains:**

    a) The error details
    b) The outcome of the method execution
    c) The method name
    d) The session token     



    Section 3: MCP Architecture and Components (Questions 21-30)

In MCP, the server exposes:
a) Only prompts
b) Tools, resources, and prompts via defined methods
c) Model training data
d) Hardware specifications
What MCP method is used to list available tools?
a) tools/call
b) tools/list
c) prompts/list
d) resources/fetch
The MCP transport layer is responsible for:
a) Defining tool logic
b) Converting MCP messages to/from JSON-RPC format
c) Training the AI model
d) Validating prompts
Which transport is deprecated in MCP as of version 2024-11-05?
a) HTTP POST
b) Stdio
c) SSE as standalone
d) WebSockets
In MCP, session IDs must be:
a) Plain text strings
b) Cryptographically secure and validated
c) Optional
d) Limited to 10 characters
MCP uses OAuth for:
a) Local stdio communication
b) Authentication in remote server connections
c) Prompt caching
d) Error logging
What interface must a custom MCP transport implement?
a) start(), send(), close(), and callbacks
b) train(), predict(), evaluate()
c) parse(), validate(), execute()
d) connect(), query(), disconnect()
In MCP client-to-server communication over HTTP:
a) Uses GET requests
b) Every message is a new POST to the MCP endpoint
c) Requires WebSockets only
d) Batches all in one request
MCP servers can be launched as:
a) Subprocesses or remote services
b) Only cloud instances
c) Desktop apps exclusively
d) Embedded in models
Resources in MCP refer to:
a) Pointers to files for RAG or extra context
b) Compute resources like GPUs
c) Network bandwidth limits
d) User permissions


Section 4: Integration, Security, and Advanced Topics (Questions 31-40)

LangChain supports MCP by treating servers as:
a) Prompt templates
b) Tool sources for agents
c) Database connectors
d) Visualization backends
A key security concern in MCP HTTP transports is:
a) DNS rebinding attacks
b) Overly long prompts
c) Binary data overflow
d) Color scheme mismatches
MCP extends JSON-RPC with:
a) Custom error codes and metadata like model version
b) Binary attachments
c) HTML rendering
d) Audio streaming
In production, MCP recommends:
a) Stdio for all deployments
b) HTTP with Bearer tokens or OAuth
c) No authentication
d) Local files only
Debugging in MCP is facilitated by:
a) Monitoring JSON-RPC messages directly
b) Model hallucinations
c) Prompt iterations
d) GUI dashboards only
FASTMCP library abstracts:
a) Model training
b) Protocol complexity for server creation
c) Client UI design
d) Data encryption
MCP's open standard enables:
a) Language-agnostic communication via JSON-RPC
b) Vendor lock-in
c) Single-tool support
d) Offline-only use
For RAG in MCP, resources are used to:
a) Provide extra context from files
b) Generate new data
c) Compress models
d) Schedule tasks
The MCP proxy (e.g., proxy.py) is used to:
a) Bridge stdio to HTTP
b) Train models
c) Validate emails
d) Render images
MCP version negotiation occurs during:
a) Connection lifecycle
b) Tool calls only
c) Prompt listing
d) Error responses


Section 5: Examples and Error Handling (Questions 41-50)

A sample MCP JSON-RPC request for tool listing: {"jsonrpc": "2.0", "method": ?, "id": 1}
a) "tools/list"
b) "error/handle"
c) "prompt/fetch"
d) "resource/delete"
Error code -32602 in JSON-RPC means:
a) Parse error
b) Invalid params
c) Internal error
d) Method not found
In an MCP tool call example, the response might include:
a) {"result": "cat"} for classification
b) Binary image data
c) HTML page
d) SQL query
Notifications in MCP are used for:
a) One-way updates without responses
b) Mandatory replies
c) Batch errors
d) Session closure
Custom transports in MCP are implemented using:
a) anyio for compatibility
b) TensorFlow
c) SQLAlchemy
d) React
An example MCP endpoint for SSE:
a) /mcp/sse
b) /api/train
c) /tools/upload
d) /prompts/delete
MCP handles statefulness through:
a) Session IDs and maintained connections
b) Stateless HTTP only
c) Cookies
d) Local storage
In Panaversity's course, MCP is integrated with:
a) n8n workflows and OpenAI SDK
b) Excel sheets
c) Word processors
d) Game engines
A malformed MCP request results in:
a) Code -32600 (Invalid Request)
b) Automatic retry
c) Model retraining
d) Prompt rewrite
The genius of MCP's JSON-RPC choice is:
a) Separation of message structure from transport mechanics
b) Increased complexity
c) Limited to Python
d) No error handling