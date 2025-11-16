# MCP Kya Hai

MCP aik standard hai jo define karta hai ke aik AI app (host) kaise aik ya zyada “MCP servers” se connect hoti hai — jo tools, resources, aur prompts expose karte hain. Iska wire format **JSON-RPC 2.0** hota hai. Ye **stateful** hota hai, matlab start mai aik initialization handshake hoti hai jisme dono sides apni capabilities share karte hain, phir long-lived messaging hoti hai requests, responses, aur notifications ke liye.

---

### Do Layers

**1. Data Layer**
Is layer ka kaam hai lifecycle management define karna — jisme tools, resources, aur prompts jese primitives hote hain.
Isme client-side primitives bhi hoti hain jinhe server call kar sakta hai, jaise sampling, elicitation, aur logging. Ye sab **JSON-RPC 2.0** ke zariye hota hai.

**2. Transport Layer**
Ye define karta hai ke messages kaise move karte hain.
Aaj ke spec ke mutabiq do standard transports hain:

* **stdio** (local processes ke liye)
* **Streamable HTTP** (remote ke liye), optional **SSE** ke sath server-to-client streaming ke liye.
  Authentication normal HTTP methods se hoti hai jaise bearer tokens ya custom headers.

---

### Core Primitives

**Server expose karta hai:**

* **Tools:** Ye executable functions hain jo client call kar sakta hai. Discover karne ke liye `tools/list` aur call karne ke liye `tools/call`.
* **Resources:** Ye read-only context hota hai jaise files, schemas, ya API responses. Discover karne ke liye `resources/list` aur read karne ke liye `resources/read`.
* **Prompts:** Ye server-provided templates hote hain jinko parameterize kiya ja sakta hai. Use karne ke liye `prompts/list` aur `prompts/get`.

**Client expose karta hai:**

* **Sampling:** Server client se keh sakta hai ke LLM completion lo (`sampling/complete`).
* **Elicitation:** Server extra user input mang sakta hai.
* **Logging:** Server apne logs client ko stream kar sakta hai.

---

### Lifecycle Summary

1. **Initialize:** Client protocolVersion aur capabilities bhejta hai, server se info wapas aata hai.
2. **notifications/initialized:** Client signal karta hai ke wo ready hai.
3. **Discovery:** `tools/list`, `resources/list`, `prompts/list`.
4. **Execution:** `tools/call`, `resources/read`, `prompts/get` ke zariye actions hote hain.
5. **Notifications:** e.g. `notifications/tools/list_changed` jab koi tool update ho.

---

### Transports — Kab Kya Use Karna Hai

**Stdio:**

* Local development, CLI, ya editors ke liye best.
* Lowest latency, network ki zarurat nahi.
* Claude Desktop ya VS Code jese tools mai common hai.

**Streamable HTTP:**

* Remote servers ke liye best, jab normal HTTP auth aur routing chahiye.
* Client POST request bhejta hai, aur optional SSE ke zariye streaming back mil sakti hai.
* Cloud aur hosted environments mai zyada use hoti hai.

---

### SSE aur WebSockets

Spec ka focus **stdio** aur **Streamable HTTP** par hai, SSE optional streaming ke liye use hota hai.
Kuch SDKs SSE ko deprecated keh kar Streamable HTTP prefer karte hain.

---

### Hosted MCP Tool (Model direct server se call kare, bina Python callback ke)

* **HostedMCPTool** use karo — sirf server label ya connector config dena hota hai.
* Ye latency kam karta hai aur infrastructure ka load bhi kam hota hai.
  (Source: OpenAI GitHub)




Here you go Laiba — **proper exam-style questions** followed by **short, clear answers** (as you prefer).

---

## **1. When should you use Sampling vs. Direct Tool Implementation?**

**Answer:**
Use **sampling** when you want the model to **think, reason, or choose** how to perform a task.
Use **direct tool implementation** when the task is **deterministic and must run exactly as coded** (e.g., fetch data, call API, run a function).

---

## **2. What is the difference between Stateful and Stateless MCP connections?**

**Answer:**
**Stateful:** Connection stays open; both sides remember session data, progress, resources, capabilities.
**Stateless:** Each request is independent; no memory between calls.

---

## **3. How do you implement proper progress notifications for long-running operations?**

**Answer:**
Send **MCP notifications** like:

* `progress` (percentage/messages)
* `status` updates
  These are sent **asynchronous notifications** from the server while the tool is still running.

---

## **4. How can servers discover and access user context through roots?**

**Answer:**
Use **roots** to access directories/files the user granted.
Server calls:

* `listRoots()`
* `readResource()`
  Roots tell the server **what the client allows it to see**.

---

## **5. How do you choose the correct MCP transport protocol?**

**Answer:**

* **HTTP Stateless** → For simple web requests or serverless environments
* **SSE (Server-Sent Events)** → For streaming model output
* **WebSockets** → For bi-directional, fast, real-time interactions
* **STDIO** → For local CLI tools, low-latency, offline use

---

## **6. What is the JSON-RPC message structure + MCP extensions?**

**Answer:**
JSON-RPC has:

* `jsonrpc`
* `id`
* `method`
* `params`
* `result` or `error`

MCP adds extensions like:

* `sampling` messages
* `tool` messages
* `resource` messages
* `notification` types like `progress`

---

## **7. How do you implement secure authentication for HTTP transport?**

**Answer:**
Use:

* **API Keys** in headers
* **OAuth tokens**
* **HMAC signatures**
  Always validate token + enforce HTTPS.

---

## **8. How do you handle errors and failures in MCP capabilities?**

**Answer:**
Use correct JSON-RPC error objects:

* `code`
* `message`
* `data`

Provide meaningful messages and log failures.
Return MCP-specific errors for:

* Tool failure
* Bad params
* Resource not found
* Prompt execution errors

---

If you want, I can convert this into **MCQs**, **quiz format**, or **one-line answers** too.
