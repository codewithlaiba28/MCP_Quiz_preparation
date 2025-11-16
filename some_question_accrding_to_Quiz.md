1. If a JSON-RPC error (code -32602: Invalid params) occurs during an MCP tool invocation over HTTP, how should the server propagate it—via JSON-RPC error object, HTTP status code (e.g., 400), or both—and what logging practices help debug transport vs. protocol issues?

2. What are the primary advantages of using JSON-RPC 2.0 over RESTful APIs for method invocation in MCP?

3. How do MCP implementations combine HTTP status codes (e.g., 4xx/5xx) with JSON-RPC error objects to provide layered diagnostics in AI tool failures?

4. What are the key differences between MCP's stdio transport and its HTTP transport?

5. Explain error propagation in MCP, combining HTTP status codes with JSON-RPC errors.

6. What version of JSON-RPC does MCP mandate?

7. Explain the difference between a JSON-RPC Request, Response, and Notification.

8. What is a JSON-RPC Batch request?

9. How does MCP extend the standard JSON-RPC error object?

10. What happens if a client sends a JSON-RPC message with a missing "method" field?

11. A client sends a valid MCP callTool request, but the tool "weather_api" does not exist. Which JSON-RPC error code must the server return, and what should the data field optionally include?

12. What is the key structural difference between a JSON-RPC Request and a Notification?

1. What is the main purpose of the “2xx” class of status codes? How does 200 OK differ from 201 Created?

2. When are “3xx” redirection codes used, and what is the difference between 301 Moved Permanently and 302 Found?

3. What defines a “4xx” class error, and how is it different from a “5xx” class error?

4. What do “5xx” status codes represent?

5. If an API frequently returns 429 Too Many Requests, what does it mean, and how should clients respond?6. In REST API design, what are the best practices for assigning and evaluating HTTP status codes?

1. What is meant by context in terms of MCP?
2. If you get  200 HTTP code but error in jsonrpc, what could be the possible reason?
3. what is the difference between tools and resources?
4. what will bethe output of following if server doesn't have any tool?{"jsonrpc":"2.0","id": 1, method :"tools/list"} 
5. what will be the output of following if server has 4 tools?{"jsonrpc":"2.0", method :"tools/list","params" : {}} 
6. write a request to call templated resource?
7. A server contains 3 tools and 4 resources, one of the request requires a parameter. what will be the output of followig request.{"jsonrpc":"2.0","id": 1, method :"resources/list"} 
8. write a requests to call addition tool that requires two (a and b ) parametrs.

1. What is the name of the method to call tool, read resource and get prompt?
2. What is the primary benefit of creating prompts in MCP server?
3. What is the difference between SSE and streamable HTTP transport?
4. In what cases is STDIO useful?
5. What are the cons of SSE transport?
6. While defining resources, which is a required parameter?
7. When a client calls a tool in MCP, what kind of message is used to perform that call?
8. In MCP, what message does a client use to list all available prompts from a server?
9. What field in a tool’s JSON description tells the client what the tool actually does?
10. If a tool fails during execution (for example, an invalid parameter), what field is used in the JSON‑RPC response?
11. When an MCP client calls tools/call, what two fields must always exist inside the params object for a valid tool invocation?
12. You want to create a tool that accesses local files but must not expose sensitive data. Which best practices aligns with MCP security principles?
13. In MCP resources, which parameter specifies the data format returned to the client?
14. Write client requests to fetch this resource via JSON‑RPC?python@mcp.resource("https://documents", mime_type="application/json")def documents() -> list[str]: return list(docs.keys())
15. Write client requests to fetch this resource via JSON‑RPC?python@mcp.resource("https://docs/{doc_id}", mime_type="text/plain")def get_doc(doc_id: str) -> str: return docs[doc_id]
16. What are the supported content types for the content field in a PromptMessage object?
17. Write a minimal JSON example of a MCP Prompt object for a "code_review" prompt?

18.  You defined this tool inside your MCP server:python@mcp.tool()
def calculate_discount(price: float, discount: float) -> float:
    return price - (price * discount / 100)The client sends this JSON‑RPC request:json{
  "jsonrpc": "2.0",
  "method": "calculate_discount",
  "params": { "price": "1000", "discount": "10" }
}What will most likely happen?

19. You modify the tool as follows:python@mcp.tool("calculate.discount")
def calc(price: float, discount: float) -> float:
    return price - (price * discount / 100)What will be the correct method field for the client’s JSON‑RPC request?

20.  Which of the following is true about path parameters in MCP resources?
a) They are optional and do not need to match the function signature
b) They are automatically mapped to function arguments
c) They are used only for tools, not resources
d) They must always be integers
20. You define a resource like this:python@mcp.resource("https://data", mime_type="application/json")
def data_resource() -> dict:
    return {"a": 1, "b": 2}Which HTTP method does this resource use by default when accessed via FastMCP or MCP?
a) POST
b) GET
c) PUT
d) DELETE

21. You have a resource defined as:python@mcp.resource("https://docs/{doc_id}", mime_type="text/plain")
def get_doc(doc_id: str) -> str:
    return docs.get(doc_id)What happens if a client calls /docs/nonexistent_doc?
a) Server returns the string "None"
b) Server raises a Python exception
c) Server returns HTTP 404 automatically
d) Server crashes

*TASK*
built  mcp server that contains any 1 tool and 3 resources 
1. tools that  uses any API to fetch data 
2. resource that should be able to access any hardcoded python data strcture
3. templated resource that can access any specified file from project directory
4. resource that read data from web

Discuss two major performance limitations of HTTP/1.1 (specifically concerning TCP connection usage), and explain how HTTP/2 addresses both of these issues through features like multiplexing and header compression.

Describe the performance function of the Connection: keep-alive header in HTTP/1.1.

what is the common factos in all HTTP versions (0.9 to 3) or (1.0 to 3)
