# 04: Agent with Multiple MCP Servers

**Objective:** Seekhna ke kaise ek single OpenAI Agent ko configure karein ke wo ek saath multiple MCP servers se connect ho aur unke tools use kare.

---

### 🧪 **Practical Coverage**

* Multi-MCP integration ke working Python scripts
* Simulated/mock MCP server configurations
* Agent jo in servers ke tools ke saath interact karta hai
* Error handling, server isolation, aur scalability insights

[Example Trace](https://smith.langchain.com/public/1a4bfa57-791d-4b8c-97da-bf0fbdf3b874/r): Dono tools alag servers par hain jo ek Agent ke through OpenAI Agents SDK use karke call hote hain.

---

### 🧠 **Use Cases aur Advantages**

* **🔌 Distributed Toolsets:** Different MCP servers ke tools access karna — jaise ek weather ke liye, ek finance ke liye.
* **🧱 Modular Architecture:** Teams independently apne tools host kar sakti hain aur standard MCP interface expose kar sakti hain.
* **📈 Scalability aur Resilience:** Load distribute ho sakta hai; ek server down ho to bhi agent work karega.
* **🌐 3rd-Party Integrations:** Kisi bhi external service jo MCP-compatible endpoint provide kare add ki ja sakti hai.

---

### ⚙️ **Configuration & Requirements**

* Agent ka `mcp_servers` parameter **active MCP client instances ki list** accept karta hai.
* Har client `MCPServerStreamableHttpParams` ke through configure aur `AsyncExitStack` me manage hona chahiye.

#### ✅ **Recommended Async Pattern**

```python
import asyncio
from contextlib import AsyncExitStack
from agents.mcp import MCPServerStreamableHttp, MCPServerStreamableHttpParams
from agents import Agent, AsyncOpenAI, OpenAIChatCompletionsModel, Runner

MCP_SERVER_URLS = [
    "http://localhost:8001/mcp",
    "http://localhost:8002/mcp",
]

client = AsyncOpenAI(
    api_key="your-api-key",
    base_url="https://your-base-url",
)

async def main():
    mcp_servers = []

    async with AsyncExitStack() as stack:
        for url in MCP_SERVER_URLS:
            mcp_params = MCPServerStreamableHttpParams(url=url)
            mcp_server_client = await stack.enter_async_context(
                MCPServerStreamableHttp(params=mcp_params, name=f"MCPClient_{url}")
            )
            mcp_servers.append(mcp_server_client)

        assistant = Agent(
            name="MultiMCPAgent",
            instructions="You are a multi-server agent.",
            mcp_servers=mcp_servers,
            model=OpenAIChatCompletionsModel(model="gemini-2.0-flash", openai_client=client),
        )

        result = await Runner.run(assistant, "Get today's weather and Tesla stock price.")
        print(f"[AGENT RESPONSE]: {result.final_output}")

asyncio.run(main())
```

---

### 🚀 **Running Example Step-by-Step**

1. **MCP Servers Start karo:**
   Do MCP servers run karo: ek mood ke liye aur ek weather ke liye. Dono `mcp_servers` directory me hain. Alag terminals kholke run karo.

   * **Mood Server (port 8001):**

     ```bash
     cd mcp_servers
     uv run python mood_server.py
     ```

     Tool: `mood_from_shared_server`

   * **Weather Server (port 8002):**

     ```bash
     cd mcp_servers
     uv run python weather_server.py
     ```

     Tool: `get_forecast`

2. **Environment Variables Configure karo:**

   * `agent_connect/.env` file me `GEMINI_API_KEY` set karo
   * Optional: LangSmith tracing ke liye `LANGCHAIN_API_KEY`, `LANGCHAIN_TRACING_V2`, aur `LANGCHAIN_PROJECT` set karo

3. **Agent Run karo:**

   ```bash
   cd agent_connect
   uv run python main.py
   ```

   Agent dono MCP servers se connect hoga aur tools aggregate karke query process karega.

4. **Tracing Observe karo (Optional):**
   LangSmith trace agent ke decision-making aur tools calls dikhaega.

---

### 🧰 **Aggregated Tool Management**

* Agent multiple MCP servers se connect hote hi **tools ka logical registry** bana leta hai.
* `agent.tools` ya LLM decisions automatically **sab tools consider** karte hain.

---

### 🚨 **Tool Name Uniqueness & Conflict Handling**

* Tool names **har MCP me unique** hone chahiye.
* Conflicts (e.g., do `get_weather` tools) unpredictable behavior la sakte hain.
* **Best Practice:** Namespacing ya prefixing use karo:

  * `finance_get_stock_price`
  * `weather_get_forecast`

SDK conflicts automatically resolve nahi karta — ye **developer responsibility** hai.

---

Ye sub-module Python code examples ke saath concepts illustrate karta hai, including mock MCP servers aur unke saath interact karne wala agent.
