### **Sampling in MCP (Simplified)**

**What is Sampling?**
Sampling lets the **server ask the client’s AI (LLM) to “think”** instead of doing all work itself. This shifts cost and control to the client, enabling more flexible and powerful tools.

**How It Works:**

1. Server fetches data (e.g., Wikipedia articles).
2. Server creates a prompt for the client.
3. Server sends a **sampling request** to the client.
4. Client’s LLM generates the content.
5. Client sends the result back to the server.
6. Server uses the generated output.

**Why Use Sampling?**

* Moves AI cost and control to the client.
* Enables adaptive, intelligent tools.
* Useful for public servers—clients pay for their own AI usage.

**Key Concepts:**

* **Stateful Connection:** Required for server-to-client requests.
* **Capability Declaration:** Client declares it supports sampling.
* **Bidirectional Communication:** Server can ask client to think and receive responses.
* **Message Flow:** Server → Client (sampling request) → Client → Server (response).

**Example Tool (Story Generator):**

```python
async def create_story(ctx: Context, topic: str) -> str:
    prompt = f"Write a story about: {topic}"
    result = await ctx.sampling.create(messages=[...])
    return result.content
```

**Power of Delegation:**

* **Traditional Tools:** Server contains all logic.
* **Sampling Tools:** Server defines process; client provides intelligence.

**Takeaway:**
Sampling allows servers to **delegate reasoning to clients**, making tools smarter and scalable while keeping server-side simple.

---
