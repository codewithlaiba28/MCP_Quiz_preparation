**Sub-module 01: Connecting to an MCP Server (Streamable HTTP)**

**Objective:**
Ye demonstrate karna ke kaise ek OpenAI Agent ko MCP server ke saath connect karte hain jo streamable-http transport use karta hai, aur MCPServerStreamableHttp client class ko OpenAI Agents SDK se use karte hain.

**Core Concept:**
Yahan primary goal ye hai ke Agent ko initialize karte hue MCPServerStreamableHttp instance dikhaya jaye. Ye instance ek client ki tarah kaam karta hai jo running MCP server ko point karta hai. Hum confirm karna chahte hain ke agent, initialization ke waqt ya jab pehli dafa MCP tools ke saath interact karna ho, ye server se connect karne ki koshish kare. Common first interaction ye hota hai ke agent (ya SDK uski taraf se) `list_tools()` MCP server pe call karta hai.

**Key SDK Concepts:**

* **MCPServerStreamableHttpParams:** Streamable-http MCP server ke connection details configure karne ke liye
* **MCPServerStreamableHttp:** SDK me client class jo aise servers ke saath interact karti hai
* **Agent(mcp_servers=[...]):** Agent ko MCP servers ke baare me aware karna
* **mcp_server_client.list_tools():** Tool listing ko directly invoke karna (Agent ke through bhi implicit hota hai)
* **Asynchronous Context Management (async with)** MCPServerStreamableHttp ke liye
* **Runner.run()** Agent ko query ke saath execute karne ke liye

**Setup:**

**1. Run the Shared MCP Server**
Is aur agle examples me module `06_openai_agents_sdk_integration` ke liye, hum ek shared, standalone MCP server use karenge. Ye server simple hai aur consistent target provide karta hai agent examples ke liye.

**Location:**
`03_ai_protocols/01_mcp/06_openai_agents_sdk_integration/shared_mcp_server/server.py`

**To Run:**

1. Naya terminal open karo
2. Shared_mcp_server directory me navigate karo:

```bash
cd 03_ai_protocols/01_mcp/06_openai_agents_sdk_integration/shared_mcp_server/
```

3. Server script execute karo (uv run use karte hue):

```bash
uv run python server.py
```

**Server Details:**

* Ye run hota hai `http://localhost:8001` pe
* MCP protocol endpoint `/mcp` pe hai, to clients ke liye full URL `http://localhost:8001/mcp` hai
* Ye ek tool expose karta hai jiska naam `greet_from_shared_server` hai
* Incoming requests ko console pe log karega

Is server ko terminal me running rakho jab tak aap agent scripts is sub-module se execute kar rahe ho.
**Explanation of the Code**

* **MCP_SERVER_URL:** Ye shared MCP server ko point karta hai.
* **MCPServerStreamableHttpParams & MCPServerStreamableHttp:**
  Client ko configure aur create karte hain taake MCP server se connect kiya ja sake, jaise pehle versions me explain hua tha.

**Agent Initialization:**

* Agent ko initialize kiya jata hai name, instructions, `mcp_servers` (jo hamare `mcp_server_client` ko point karta hai), aur model ke saath.
* Model ek OpenAIChatCompletionsModel hai jo `model="gemini-2.0-flash"` aur `openai_client` (hamara Gemini client) ke saath configured hai.

**Explicit list_tools():**

* Script explicitly `await mcp_server_client.list_tools()` call karti hai connection verify karne aur available tools log karne ke liye.
* Ye check karta hai ke dono `greet_from_shared_server` aur `mood_from_shared_server` present hain.

**Runner.run(assistant, "What is Junaid's mood?"):**

* Ye line agent ko specific query ke saath execute karti hai.
* `Runner.run` method interaction flow handle karta hai: query aur instructions LLM ko bhejna, koi tool calls jo LLM decide kare (configured MCP server ke through) process karna, aur final result return karna.
* Query `"What is Junaid's mood?"` designed hai ke potentially `mood_from_shared_server` tool trigger ho sakta hai agar LLM appropriate samjhe.

**Expected Output/Behavior:**
Jab aap run karte ho:

```bash
uv run python main.py
```

(after starting `shared_mcp_server/server_main.py` aur ensure karte ho ke `.env` me `GEMINI_API_KEY` hai)

**Agent Script Terminal (main.py output):**

* Logs jo connection steps indicate karte hain.
* httpx logs showing HTTP requests to MCP server (`http://localhost:8001/mcp/`) aur Gemini API (`https://generativelanguage.googleapis.com/...`).
* Confirmation of `MySharedMCPServerClient` creation.
* Agent initialization logs.
* Successful listing of tools from MCP server, including `greet_from_shared_server` aur `mood_from_shared_server`.
* Log: `"Running a simple agent interaction..."`
* Further httpx logs for interactions with MCP aur Gemini during `Runner.run` call.
* Final agent response, jaise: `[AGENT RESPONSE]: OK. Junaid is happy.` (Exact response LLM aur tool execution pe depend karta hai).
* Logs indicating client context exit aur test end.

**Shared MCP Server Terminal (server_main.py output):**

* Aapko log messages dikhne chahiye jo tools/list requests receive hone indicate karte hain.
* Agar LLM ne `mood_from_shared_server` tool (ya koi aur tool) use kiya, to aap corresponding `tool/run` requests server pe log hoti hui dekhoge. Example:

```
INFO:SharedStandAloneMCPServer:MCP Request ID '...' received: tools/list
INFO:SharedStandAloneMCPServer:Responding to 'tools/list' (ID '...') with 2 tool(s)
...
INFO:SharedStandAloneMCPServer:MCP Request ID '...' received: tool/run (tool_name='mood_from_shared_server')
INFO:SharedStandAloneMCPServer:Running tool 'mood_from_shared_server' with args: {'name': 'Junaid'}
INFO:SharedStandAloneMCPServer:Tool 'mood_from_shared_server' execution successful
```

Ye comprehensive test confirm karta hai na sirf connection aur tool listing, balki agent ki ability bhi verify karta hai ke wo LLM (Gemini) use karke MCP tools invoke kar sakta hai apne execution flow ke part ke taur pe.


Good question. I couldn’t find a public readable **README** at that exact path in the repo, so instead I’ll make a **theoretical quiz** based on the general concept of integrating MCP via HTTP in the OpenAI Agents SDK, using MCP documentation. (If you find the actual README text, you can send it and I can make questions exactly from it.)

Here’s a **10‑question multiple‑choice quiz** on **Agent MCP HTTP integration**:

---

## Quiz: OpenAI Agents SDK — MCP HTTP Integration

1. **What does the OpenAI Agents SDK use MCP for?**
   A) To store training data locally
   B) To expose external tools / context to agents in a standardized way
   C) To serve model weights
   D) To manage user authentication
   **Answer:** B

2. **Which MCP transport is used when integrating via HTTP with the Agents SDK?**
   A) WebSocket
   B) Streamable HTTP (or HTTP + SSE)
   C) SMTP
   D) FTP
   **Answer:** B

3. **What Python class is typically used to connect an Agent to an HTTP‑based MCP server?**
   A) `MCPServerSse`
   B) `MCPServerStdio`
   C) `MCPHttpClient`
   D) `MCPServerStreamableHttp`
   **Answer:** D

4. **Why might you want to use the `cache_tools_list` option when connecting via HTTP?**
   A) To reduce the number of HTTP requests for `list_tools()` calls
   B) To disable tool filtering
   C) To speed up logging
   D) To force the agent to reconnect each run
   **Answer:** A

5. **What is “tool filtering” in the context of MCP + Agents SDK?**
   A) Downloading only small tools to save space
   B) Restricting which tools from the MCP server are exposed to the agent
   C) Removing duplicate tools from multiple MCP servers
   D) Encrypting tool inputs
   **Answer:** B

6. **How can you filter tools when using `MCPServerStreamableHttp`?**
   A) By passing `tool_filter` function when constructing the server class
   B) By editing the server’s source code only
   C) By using a special CLI tool only
   D) By restarting the server each time
   **Answer:** A

7. **What should you do if you expect the list of tools on the MCP server to change rarely?**
   A) Set `cache_tools_list = True`
   B) Use a different transport
   C) Disable the MCP server
   D) Always call `list_tools()` before every agent call
   **Answer:** A

8. **How does the agent find out what tools the MCP server provides?**
   A) By manually writing a tool schema
   B) By calling `list_tools()` on the MCP server
   C) By reading a JSON file in the agent
   D) By guessing tool names
   **Answer:** B

9. **If the MCP server supports Server-Sent Events (SSE), which class should you use in the SDK?**
   A) `MCPServerSse`
   B) `MCPServerStdio`
   C) `MCPServerStreamableHttp` (without SSE)
   D) `MCPServerWebSocket`
   **Answer:** A

10. **What is a major benefit of integrating MCP HTTP with the Agents SDK?**
    A) The agent can use external tools defined on the MCP server seamlessly alongside built-in tools.
    B) The agent no longer needs an OpenAI API key.
    C) The MCP server handles all model inference locally.
    D) The agent’s code size is smaller.
    **Answer:** A

---

