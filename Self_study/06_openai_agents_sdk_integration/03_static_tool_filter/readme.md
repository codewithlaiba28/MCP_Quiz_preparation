**03: Static Tool Filtering with MCPServerStreamableHttp**

**Hum Kya Seekh Rahe Hain? (The “Why”)**
Is step me aap seekh rahi ho ke kaise aap control kar sakti ho ke agent MCP server ke kin tools ko dekh sakta hai aur use kar sakta hai.
Ye skill bohot important hai safe, focused, aur user-friendly agentic systems banane ke liye.

**Ye kyu zaroori hai?**

* Kabhi MCP server bohot saare tools expose karta hai, lekin aap chahte ho ke agent sirf 1–2 specific tools use kare.
* Tool filtering se mistakes kam hoti hain aur agent ka behavior clear aur safe rehta hai.
* Ye advanced agent control ka pehla step hai — pehle static allow/block list, phir dynamic filtering.

---

### **Big Idea Kya Hai?**

* *Static tool filtering* ka matlab hai aap pehle se decide kar leti ho code me ke kaunse tools allow hain aur kaunse block.
* Aap MCP server client ko filter pass karte ho.
* Ye filter agent ke liye ek “menu” ki tarah hota hai — sirf approved items dikhenge.

---

### **Kaise Kaam Karta Hai? (The “How”)**

1. Helper function import karte ho filter banane ke liye.
2. Decide karte ho ke kaunse tools allow ya block karne hain.
3. Jab agent connect hota hai, usay sirf wohi tools dikhte hain jo aap ne choose kiye hote hain.

---

### **Step-by-Step Example**

```python
from agents.mcp import MCPServerStreamableHttp, MCPServerStreamableHttpParams, create_static_tool_filter

# Sirf "mood_from_shared_server" tool allow karein
tool_filter = create_static_tool_filter(allowed_tool_names=["mood_from_shared_server"])
mcp_params = MCPServerStreamableHttpParams(url="http://localhost:8001/mcp/")

async with MCPServerStreamableHttp(params=mcp_params, tool_filter=tool_filter, name="MyFilteredMCPServer") as mcp_server_client:
    # ... agent setup aur running yahan hogi ...
```

Ab agar aap tools list karo ya agent run karo, to agent ko **sirf** `mood_from_shared_server` tool milega.

---

### **Aapko Kya Notice Hona Chahiye?**

* Agar aap koi blocked tool use karne ki koshish karo, agent usay dekhega bhi nahi.
* Ye agent ki “toolbox” ko baby-proof karne jaisa hai — sirf safe tools available hain.

---

### **Ye Step Achha Kyun Hai?**

* **Safe:** Agent sirf wohi tools use karega jo aap allow karte ho.
* **Clear:** Aap perfectly dekh sakti ho ke agent ke paas kaunse tools available hain — debugging aasaan ho jati hai.
* **Foundational:** Ye aapko next steps ke liye ready karta hai, jahan dynamic aur context-aware filters aayenge.

---

### **In Summary:**

Aap seekh rahi ho ke agent ko ek carefully chosen set of tools kaise dena hai, bilkul usi tarah jaise ek bache ko sirf safe toys diye jate hain.
Ye safe, scalable aur maintainable agentic systems banane ka important building block hai.
















Yeh short aur easy Roman Urdu version hai:

---

### **03: Static Tool Filtering — Short & Easy**

**Kya Seekh Rahi Ho?**
Aap yeh seekh rahi ho ke agent MCP server ke kaunse tools dekh sakta hai aur kaunse nahi.
Yeh security, clarity aur control ke liye bohot important hota hai.

---

### **Ye Kyu Zaroori Hai?**

* Server me bohot tools ho sakte hain, lekin aap chahte ho agent sirf specific tools use kare.
* Isse mistakes kam hoti hain aur agent safe rehta hai.
* Ye advanced filtering ka basic step hai.

---

### **Big Idea**

* *Static filtering* ka matlab: code me pehle se decide kar lo ke kaunse tools allow hain.
* Agent ko sirf wohi tools dikhai denge jo aap allow karti ho.
* Ye ek menu ki tarah hota hai — sirf approved items show honge.

---

### **Kaise Kaam Karta Hai?**

1. Filter banati ho.
2. Batati ho ke kaunse tools allow/block hain.
3. Agent connect hota hai to sirf allowed tools dekh pata hai.

---

### **Example**

```python
tool_filter = create_static_tool_filter(
    allowed_tool_names=["mood_from_shared_server"]
)
```

Ab agent ko sirf **mood_from_shared_server** tool dikhai dega.

---

### **Kya Notice Hoga?**

* Blocked tools bilkul nazar nahi aayenge.
* Agent sirf safe tools hi use kar payega.

---

### **Ye Step Achha Kyun?**

* Safe
* Clear
* Aage dynamic filtering seekhne ke liye perfect base

---

### **Short Summary**

Aap agent ko sirf safe aur selected tools dikhana seekh rahi ho.
Ye bilkul usi tarah hai jaise ek bache ko sirf safe toys diye jate hain.





Here are **5 multiple-choice questions** focused on *static tool filtering* in the OpenAI Agents SDK (via Model Context Protocol (MCP)) — based on the docs about `ToolFilterStatic`, `create_static_tool_filter`, allow-lists and block-lists. ([OpenAI GitHub][1])

---

1. What does a **static tool filter** do in the MCP + Agents SDK context?
   A) Dynamically decide tool availability at runtime based on the agent’s context
   B) Configure at instantiation time a fixed allow-list and/or block-list of tools
   C) Cache the tool list from the server for faster retrieval
   D) Automatically update tool definitions when new ones are added on the server
   **Correct Answer:** B

2. Which of the following fields are part of `ToolFilterStatic`?
   A) `allowed_tool_names` and `blocked_tool_names`
   B) `dynamic_tool_predicate` and `agent_context`
   C) `cache_tools_list` and `invalidate_cache`
   D) `tool_call_log` and `tool_metrics`
   **Correct Answer:** A ([OpenAI GitHub][2])

3. If you set both `allowed_tool_names` and `blocked_tool_names`, how does the filtering work?
   A) First the block-list is applied, then the allow-list is ignored
   B) Both lists are ignored and no filtering is applied
   C) First the allow-list selects tools, then the block-list removes from that set
   D) Only one of the lists can be set—both together throw an error
   **Correct Answer:** C ([OpenAI GitHub][1])

4. Why might you choose to use a static tool filter rather than no filtering when configuring an MCP server for your agent?
   A) To prevent the agent from seeing tools it doesn’t need, reducing token usage and context size
   B) Because it automatically increases tool-calling speed by 100%
   C) Because the SDK requires either an allow-list or a block-list always to be set
   D) Because filtering enables caching of tool results
   **Correct Answer:** A ([GitHub][3])

5. True or False: A static tool filter can use agent-specific context (such as the agent’s name) to decide whether a tool is allowed.
   A) True
   B) False
   **Correct Answer:** B — A static tool filter uses fixed allow/block lists and does *not* use runtime agent context; for agent-specific logic you would use **dynamic tool filtering**. ([OpenAI GitHub][1])

