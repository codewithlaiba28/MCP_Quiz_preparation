04: Dynamic Tool Filtering with MCPServerStreamableHttp
What Are We Learning? (The “Why”)
In this step, you’ll learn how to dynamically control which tools your agent can see and use—not just with a fixed list, but with custom logic that can change based on the agent, the server, or even the current situation.

**Roman Urdu:**
Is step mein aap seekhogi ke dynamically control kaise karna hai ke agent kaun se tools dekh sakta hai aur use kar sakta hai — sirf ek fixed list nahi, balkay aisi custom logic ke saath jo agent, server ya current situation ke hisaab se change ho sakti hai.

---

Why is this important?
Sometimes you want to show or hide tools based on who the user is, what the agent is doing, or other runtime conditions.
Dynamic filtering gives you fine-grained, context-aware control over your agent’s toolbox.
This is a “next step” after static filtering, and is essential for building smart, adaptive, and secure agentic systems.

**Roman Urdu:**
Yeh kyu important hai?
Kabhi kabhi aap user, agent ki activity, ya runtime conditions ke hisaab se tools show/hide karna chahti ho.
Dynamic filtering aapko bohot fine-grained aur context-aware control deta hai agent ke toolbox par.
Yeh static filtering ke baad agla step hai, aur smart, adaptive aur secure agentic systems banane ke liye zaroori hai.

---

What’s the Big Idea?
Dynamic tool filtering means you write a function that decides, for each tool, whether it should be available—using information about the agent, the server, and the current context.
Your filter can be synchronous or asynchronous, and can use any logic you want.

**Roman Urdu:**
Big idea kya hai?
Dynamic tool filtering ka matlab hai ke aap ek function likhti ho jo decide karta hai ke har tool available hona chahiye ya nahi — agent, server aur current context ki information use karke.
Aapka filter sync bhi ho sakta hai aur async bhi, aur aap koi bhi custom logic use kar sakti ho.

---

How Does It Work? (The “How”)
Write a filter function that takes a ToolFilterContext and a tool, and returns True (show the tool) or False (hide it).
Pass your filter function as the tool_filter when creating your MCP server client.
The SDK will call your function for each tool, every time it needs to know which tools are available.

**Roman Urdu:**
Kaise kaam karta hai?
Aap ek filter function banati ho jo ToolFilterContext aur tool leta hai, aur True (tool show karo) ya False (tool hide karo) return karta hai.
Phir is filter function ko MCP server client banate waqt tool_filter ke taur par pass karti ho.
SDK har tool ke liye ye function call karta hai jab bhi usay available tools check karne hote hain.

---

Step-by-Step Example

1. Import the context type:
   from agents.mcp import ToolFilterContext

**Roman Urdu:**

1. Context type import karo:
   from agents.mcp import ToolFilterContext

---

2. Write your filter function:

def custom_filter(context: ToolFilterContext, tool) -> bool:
# Only allow tools that start with "mood"
return tool.name.startswith("mood")

**Roman Urdu:**
2. Apna filter function likho:

def custom_filter(context: ToolFilterContext, tool) -> bool:
# Sirf woh tools allow karo jo "mood" se start hote hain
return tool.name.startswith("mood")

---

Or, for context-aware logic:

def context_aware_filter(context: ToolFilterContext, tool) -> bool:
# Only allow tools for a specific agent
return context.agent.name == "MyMCPConnectedAssistant" and tool.name == "mood_from_shared_server"

**Roman Urdu:**
Ya context-aware logic ke liye:

def context_aware_filter(context: ToolFilterContext, tool) -> bool:
# Sirf specific agent ke liye tools allow karo
return context.agent.name == "MyMCPConnectedAssistant" and tool.name == "mood_from_shared_server"

---

Or, for async logic:

async def async_filter(context: ToolFilterContext, tool) -> bool:
# Example: check a database or external API before allowing the tool
return await some_async_check(context, tool)

**Roman Urdu:**
Ya async logic ke liye:

async def async_filter(context: ToolFilterContext, tool) -> bool:
# Example: tool allow karne se pehle database ya external API check karo
return await some_async_check(context, tool)

---

3. Use your filter when creating the MCP server client:

from agents.mcp import MCPServerStreamableHttp, MCPServerStreamableHttpParams

mcp_params = MCPServerStreamableHttpParams(url="[http://localhost:8001/mcp/](http://localhost:8001/mcp/)")
async with MCPServerStreamableHttp(params=mcp_params, tool_filter=custom_filter, name="MyDynamicMCPServer") as mcp_server_client:
# ... set up your agent and run as before ...

**Roman Urdu:**
3. MCP server client banate waqt apna filter use karo:

from agents.mcp import MCPServerStreamableHttp, MCPServerStreamableHttpParams

mcp_params = MCPServerStreamableHttpParams(url="[http://localhost:8001/mcp/](http://localhost:8001/mcp/)")
async with MCPServerStreamableHttp(params=mcp_params, tool_filter=custom_filter, name="MyDynamicMCPServer") as mcp_server_client:
# ... agent set up karo aur run karo ...

---

What Should You Notice?
The available tools can change depending on the agent, the server, or any other logic you put in your filter.
This is much more flexible than static filtering, and lets you build smarter, more secure agents.

**Roman Urdu:**
Aap kya notice karogi?
Available tools agent, server, ya aapki custom logic ke hisaab se change ho sakte hain.
Yeh static filtering se zyada flexible hai, aur aapko smarter aur secure agents banane deta hai.

---

Why Is This a Good Learning Step?
It’s adaptive: Your agent’s toolbox can change as needed.
It’s powerful: You can use any logic, including async checks or external data.
It’s real-world: Most production systems need this kind of flexibility.

**Roman Urdu:**
Yeh achha learning step kyun hai?

* Adaptive hai — agent ka toolbox zaroorat ke hisaab se change ho sakta hai.
* Powerful hai — aap koi bhi logic use kar sakti ho, async checks ya external data bhi.
* Real-world jaisa hai — production systems me yahi flexibility chahiye hoti hai.

---

In summary:
You’re learning how to give your agent a “smart menu” of tools that can change based on context—an essential skill for building advanced, real-world agentic systems.

**Roman Urdu:**
Summary:
Aap seekh rahi ho ke agent ko ek “smart menu” kaise diya jaye — jisme tools context ke hisaab se change hote rahen.
Yeh advanced, real-world agentic systems banane ke liye bohot important skill hai.









**Short answer: YES — server hi decide karta hai.**

**Static vs Dynamic ka difference simple:**

### ✔️ **Static Tools**

* Server **pehle se fixed** tools batata hai.
* Client ko **sirf ek dafa** milte hain.
* Change **runtime mai nahi hota**.

### ✔️ **Dynamic Tools**

* Tools **runtime mai change ho sakte hain**.
* Client jab chahe **listTools** bhej kar **updated tools** mang sakta hai.
* Server **decide karta hai** us moment pe kaunse tools available honge.

### ⭐ Final line:

**Tools hamesha SERVER ke paas hote hain — client sirf server se poochta hai. Server hi decide karta hai static ya dynamic mode mai tool expose karna hai.**




---

1. In the Agents SDK, what does a *dynamic tool filter* allow you to do?

        A) Fix the tool list once at initialization and never change it
        B) Use a callable (sync/async) that gets run-time context (agent/ run) to decide if each tool should be exposed
        C) Cache the tool list permanently so no updates occur
        D) Automatically generate tool descriptions from docstrings
**Correct Answer:** B

2. In the dynamic tool filter callable, what parameter(s) are typically provided so you can decide tool availability?

        A) Only the tool name
        B) The run context, the agent instance, and the tool object
        C) The server URL and port
        D) The tool list size
   **Correct Answer:** B

3. Why might you prefer a dynamic tool filter over a static tool filter in an agent configuration?

        A) Because the static filter changes at every run automatically
        B) Because you need to enable or disable tools based on user role, context, or agent name at runtime
        C) Because static filters increase network latency
        D) Because dynamic filters disable logging entirely
   **Correct Answer:** B

---

