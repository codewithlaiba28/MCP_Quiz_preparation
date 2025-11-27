
---

### **MCP Logging - Server’s Voice (Simplified)**

**What is MCP Logging?**
Logging lets the server **narrate what it’s doing** to the client, helping with **debugging, monitoring, and transparency**. Think of it as the server “talking” about its actions in real time.

**Why It Matters:**

* **Debugging:** See exactly what the AI agent is thinking.
* **Monitoring:** Track performance and behavior.
* **Transparency:** Users know what’s happening.
* **Development:** Faster troubleshooting and optimization.

**8 Logging Levels (RFC 5424 Standard):**

1. **emergency:** System unusable
2. **alert:** Immediate action needed
3. **critical:** Major functionality broken
4. **error:** Something failed
5. **warning:** Potential issues
6. **notice:** Significant normal events
7. **info:** General information
8. **debug:** Detailed tracing

**How It Works:**

1. **Server declares logging capability** → tells client it can send logs.
2. **Client sets preferences** → chooses minimum log level (e.g., info).
3. **Server sends structured log messages** → includes extra data like user ID, request type, timing.
4. **Client receives and displays** → formats messages in real time.

**Example:**

```python
await ctx.info("Processing user request", extra={"user_id":"123","request_type":"weather"})
# Client displays: 📰 [INFO] Processing user request | User: 123, Type: weather
```

**Benefits:**

* Structured, standardized logging
* Real-time monitoring
* Control over which messages to see
* Better debugging and performance tracking

**Summary:**
MCP logging gives your server a **voice**, helping both developers and users understand exactly what the server is doing, while letting clients **filter and display logs** as needed.

---



---

**1. What is the main purpose of MCP logging?**

    A) To replace console.log() completely
    B) To give the server a voice and narrate its activities
    C) To store user data permanently
    D) To monitor network speed

**Correct Answer:** B

---

**2. Which of these is **not** a logging level in MCP (RFC 5424)?**

    A) emergency
    B) trace
    C) notice
    D) critical

**Correct Answer:** B

---

**3. When should you use the `warning` level?**

    A) System is unusable
    B) Something failed
    C) Potential issues or caution needed
    D) General information

**Correct Answer:** C

---

**4. How does a client set the desired logging level?**

    A) By editing server.py
    B) By calling `await session.set_logging_level("level")`
    C) By modifying JSON-RPC spec
    D) By using console.log()

**Correct Answer:** B

---

**5. Which level would you use for detailed tracing of function calls?**

    A) info
    B) debug
    C) alert
    D) notice

**Correct Answer:** B

---

**6. In MCP logging, structured messages can include:**

    A) Only plain text
    B) Metadata like user_id, request_type, processing_time
    C) Only emojis
    D) Only numeric codes

**Correct Answer:** B

---

**7. Why is MCP logging better than traditional `console.log()`?**

    A) It uses emojis
    B) It is structured, standardized, and client-aware
    C) It runs faster on the server
    D) It replaces the AI model

**Correct Answer:** B

---

**8. Which step happens first in MCP logging?**

    A) Client receives logs
    B) Server sends structured messages
    C) Server declares capabilities
    D) Client sets logging preferences

**Correct Answer:** C

---

**9. What practical use does debug-level logging have?**

    A) Shows only critical errors
    B) Helps trace detailed program execution
    C) Monitors memory usage automatically
    D) Tracks network latency

**Correct Answer:** B

---

**10. Which MCP feature allows dynamic control over what logs are shown?**

    A) JSON-RPC method
    B) log_handler function
    C) Client-level filtering
    D) Syslog integration

**Correct Answer:** C

---
