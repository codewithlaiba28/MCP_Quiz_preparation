MCP Prompt
MCP servers prompts bhi provide kar sakte hain jo dynamically agent instructions generate karne ke liye use ho sakte hain. Yeh aapko reusable instruction templates create karne deta hai jo parameters ke saath customize kiye ja sakte hain.

Jo MCP servers prompts support karte hain wo do key methods provide karte hain:
list_prompts(): Server ke sare available prompts list karta hai
get_prompt(name, arguments): Specific prompt aur optional parameters get karta hai

Yeh example ek local MCP prompt server use karta hai jo server.py me hai.

Example run karo:
MCP Server start karo
uv run python server.py
Agent start karo
uv run python main.py

Details
Yeh step MCP prompt use karta hai jo user-controlled prompts provide karta hai jo agent instructions generate karte hain. MCP server prompts expose karta hai jaise generate_code_review_instructions jo parameters lete hain jaise focus area aur programming language. Agent ye prompts call karta hai taake dynamically apni system instructions generate kar sake based on user-provided parameters.

Workflow
Example do key functions demonstrate karta hai:

show_available_prompts - MCP server ke sare available prompts list karta hai, users ko dikhata hai ke wo kaunse prompts select kar sakte hain. Yeh MCP prompts ka discovery aspect demonstrate karta hai.

demo_code_review - Complete user-controlled prompt workflow dikhata hai:
generate_code_review_instructions ko specific parameters ke saath call karta hai (focus: "security vulnerabilities", language: "python")
Generated instructions use karta hai Agent create karne ke liye with specialized code review capabilities
Agent run karta hai vulnerable sample code par (command injection via os.system)
Agent code analyze karta hai aur security-focused feedback provide karta hai available tools use karke

Yeh pattern users ko allow karta hai ke wo dynamically agent behavior configure karein MCP prompts ke through, instead of hardcoded instructions.



Here are **3 multiple‑choice quiz questions** based on the concept of a **Prompt Server** in MCP + OpenAI Agents SDK (drawing from MCP / Agents SDK docs). Since the exact GitHub README wasn’t accessible, these questions are derived from the standard MCP behavior.

---

1. What feature does an MCP *Prompt Server* provide to the agent?
   A) It lets the agent call external tools via HTTP.
   B) It provides templated prompts that can be fetched and customised at runtime.
   C) It stores the agent’s memory between runs.
   D) It logs all tool calls for debugging.

   **Correct Answer:** B — A prompt server lets you `list_prompts()` and `get_prompt(...)` to dynamically generate instructions. ([OpenAI GitHub][1])

2. Which two methods are typically supported by an MCP server that exposes prompts?
   A) `list_tools()` and `call_tool()`
   B) `list_prompts()` and `get_prompt(name, arguments)`
   C) `start_trace()` and `end_trace()`
   D) `open_connection()` and `close_connection()`

   **Correct Answer:** B — Prompt servers implement `list_prompts()` and `get_prompt(...)` to enumerate and fetch prompt templates. ([OpenAI GitHub][2])

3. When you call `get_prompt(name, arguments)` on a prompt server, what do you receive?
   A) A list of tool schemas
   B) A concrete prompt message, potentially with arguments substituted
   C) A streaming response of tool execution results
   D) The server’s error logs

   **Correct Answer:** B — The server returns a prompt (e.g. a message template) with the given arguments filled in. ([OpenAI GitHub][1])

---

\
