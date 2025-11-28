**Module 2: Caching MCP Tool Lists with OpenAI Agents SDK**

**Introduction**
Jab ek Agent MCP server ke saath interact karta hai, to wo aksar `list_tools()` call karta hai taake available tools discover kar sake. Agar ye calls frequently ho, specially remote servers pe, to latency increase ho sakti hai. OpenAI Agents SDK ye facility provide karta hai ke aap tool list ko cache kar sakte ho taake performance improve ho.

Ye module explain karta hai ke kaise MCP server clients ke saath OpenAI Agents SDK use karte waqt tool list caching enable aur verify karte hain, official SDK documentation ke reference ke saath.

OpenAI Agents SDK MCP Documentation ke mutabiq:

* Har dafa jab Agent run hota hai, wo MCP server pe `list_tools()` call karta hai. Ye latency ka issue create kar sakta hai, especially agar server remote ho.
* Tool list ko automatically cache karne ke liye aap `cache_tools_list=True` pass kar sakte ho.

**Enabling Caching**
Tool list caching enable karne ke liye boolean parameter `cache_tools_list=True` directly MCP server client ke constructor me pass karein (jaise MCPServerStreamableHttp, MCPServerStdio, ya MCPServerSse).

```python
async with MCPServerStreamableHttp(params=mcp_params_cached, name="CachedClient", cache_tools_list=True)
```

Agar aap cache invalidate karna chahte ho, to aap `invalidate_tools_cache()` server pe call kar sakte ho.

**Verifying Caching Behavior**

* **Server-Side Logs:** Caching verify karne ka sabse reliable tareeqa ye hai ke aap MCP server ke logs check karein.
* Jab client-side caching active ho, server ko repeated `list_tools()` calls ke liye significantly kam `ListToolsRequest` messages receive honge same client instance se.

**Demonstration (agent_connect_cache/agent_tool_caching.py)**

* `agent_tool_caching.py` script (jo is module ke `agent_connect_cache` subdirectory me hai) ye caching behavior demonstrate karta hai MCPServerStreamableHttp ke saath.
* Ye MCPServerStreamableHttp client ko `cache_tools_list=True` ke saath initialize karta hai aur multiple calls to `list_tools()` karta hai.
* Server logs observe karke aap confirm kar sakte ho ke server pe `ListToolsRequest` far kam process hoti hai compared to client calls.

**Running the Example:**

1. **Ensure Shared MCP Server is Running:**

* Client script target karega URL (e.g., `http://localhost:8001/mcp`).
* Server start karo accordingly:

```bash
uv run python shared_mcp_server/server.py
```

2. **Run the Caching Script:**

* Navigate karo directory me jahan `agent_tool_caching.py` hai:
  `05_ai_protocols/01_mcp/07_openai_agents_sdk_integration/02_caching_tool_lists/agent_connect_cache/`
* Run karo:

```bash
uv run python agent_tool_caching.py
```

3. **Observe Server Logs:**

* Note karo kitni dafa server `ListToolsRequest` log karta hai.
* `cache_tools_list=True` ke saath, repeated client calls ke liye ye minimal honi chahiye.

Ye module, official documentation aur aapke practical findings ke guidance se, clear karta hai ke kaise tool list caching enable aur verify ki jati hai.










Good idea. Here’s a quiz based on the concept of **caching tool lists** in MCP / OpenAI Agents SDK (drawing from open‑source MCP + Agents SDK docs). Since the exact GitHub README might not include all the details, I’m using the general behavior from the OpenAI Agents SDK. References include: SDK docs for `cache_tools_list`, `invalidate_tools_cache`, etc. ([OpenAI GitHub][1])

---

## Quiz: Caching Tool Lists in MCP (Agents SDK)

1. **What is the purpose of `cache_tools_list` in MCP when using the OpenAI Agents SDK?**
   A) It caches the results of `call_tool()` so each call is faster
   B) It saves the list of available tools so `list_tools()` is not called every time
   C) It enables logging of tool usage
   D) It encrypts the tool list for security

   **Answer:** B

2. **When should you set `cache_tools_list = True`?**
   A) If the list of tools on the server changes very frequently
   B) If the MCP server is local and fast
   C) If you know the server’s tool set is stable and does not change often
   D) Always, regardless of server stability

   **Answer:** C

3. **What disadvantage might occur if you enable `cache_tools_list` but the server’s tools change later?**
   A) The agent will crash when calling a tool
   B) The agent will not see newly added tools until the cache is invalidated
   C) Latency will increase for every `list_tools()` call
   D) The server will reject requests

   **Answer:** B

4. **How do you force a refresh of the cached tool list?**
   A) Restart the agent process
   B) Call `invalidate_tools_cache()` on the MCP server instance
   C) Use a special HTTP header on the next `list_tools()` call
   D) Reinitialize the whole agent

   **Answer:** B

5. **What is the primary benefit of enabling tool list caching in remote MCP servers?**
   A) It reduces memory usage on the server
   B) It reduces network latency by avoiding repeated round‑trips
   C) It makes `call_tool()` faster
   D) It allows more tools to be loaded at once

   **Answer:** B

6. **True or False: If `cache_tools_list` is disabled (`False`), the SDK will call `list_tools()` on every agent run.**
   A) True
   B) False

   **Answer:** A

7. **Which method in the MCP server class is used to clear / invalidate the current tool list cache?**
   A) `clear_tool_cache()`
   B) `refresh_tools()`
   C) `invalidate_tools_cache()`
   D) `reset_tools()`

   **Answer:** C

8. **If you have a dynamic tool filter (i.e., tools exposed depend on the agent or run context), is caching still useful?**
   A) Yes, because caching only affects the base list of tools
   B) No, because filtering requires fresh `list_tools()` each time
   C) No, because cached tools will be permanently filtered out
   D) Yes, but only if you disable filtering

   **Answer:** A

9. **Which of the following is a correct reason for *not* using `cache_tools_list`?**
   A) You want to minimize memory usage
   B) The MCP server is on the same machine
   C) The list of tools changes frequently (e.g., tools register/unregister dynamically)
   D) You don’t use any tools at all

   **Answer:** C

10. **How does tool caching in MCP improve overall performance?**
    A) By compressing the tool definitions
    B) By avoiding repeated network calls to fetch the tool list
    C) By caching tool outputs
    D) By reducing the number of allowed tools

    **Answer:** B

---


