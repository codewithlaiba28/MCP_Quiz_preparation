# Introduction to JSON-RPC 2.0

[Specification](https://www.jsonrpc.org/specification)

## Learn by Trying JSON-RPC Requests Online

JSON-RPC requests ko try karke seekhain. Live time mein requests bhej kar aur responses dekh kar JSON-RPC ko explore karein.

JSON-RPC requests aur responses ko explore aur experiment karein is online tool ka use karke:

[JSON-RPC Playground](https://jsonrpc-playground.onrender.com/)

## What is JSON-RPC 2.0?

JSON-RPC 2.0 aik lightweight aur stateless remote procedure call (RPC) protocol hai jo notifications aur remote procedure calls ko simple, standardized tareeke se allow karta hai. Yeh JSON (JavaScript Object Notation) ko data format ke tor par use karta hai, jo ise bohot si programming languages aur platforms ke sath use karna aasaan banata hai. Yeh protocol transport-agnostic hai, matlab ise HTTP, WebSockets, ya kisi bhi message-passing environment ke through use kiya ja sakta hai.

JSON-RPC 2.0 basically kuch data structures aur unki processing ke rules define karta hai. Yeh simple design ki wajah se APIs aur distributed systems banane ke liye popular hai.

### Key Concepts

#### 1. Request Object

Remote procedure call client ke taraf se server ko `Request` object send karne se start hoti hai. Is object mein yeh members hotay hain:

* **`jsonrpc`**: String jo JSON-RPC protocol version batata hai. Version 2.0 ke liye yeh **exactly** `"2.0"` hona zaroori hai.
* **`method`**: String jisme server par invoke karne wali method ka naam hota hai.
* **`params`**: Structured value (Array ya Object) jisme method ke parameters hotay hain. Agar method parameters nahi mangti to yeh member omit kiya ja sakta hai.
* **`id`**: Client ki taraf se diya gaya identifier. String, number ya `null` ho sakta hai. Agar include na ho to request "notification" hoti hai.

#### 2. Notification

Notification aik special `Request` object hota hai jisme `id` member include nahi hota. Jab client notification send karta hai to iska matlab hota hai ke usay server ke response ki zaroorat nahi. Server **reply nahi karega** notification par.

Notifications aik-tarfa communication jaise events bhejne ya logging ke liye kaam aati hain. Lekin kyunke inka response nahi hota, client errors se unaware rehta hai.

#### 3. Parameter Structures

Method call karte waqt `params` do tareekon se diye ja sakte hain:

* **By-position**: `params` Array hota hai jisme values server ke expected order mein hoti hain.
* **By-name**: `params` aik Object hota hai jisme key-value pairs ke through parameters diye jate hain.

#### 4. Response Object

Agar client standard RPC call karta hai (notification nahi), to server **zaroor** `Response` object return karta hai. Is object mein yeh members hotay hain:

* **`jsonrpc`**: JSON-RPC protocol version, jo **"2.0"** hona chahiye.
* **`result`**: Agar call successful ho to yeh member **required** hota hai. Agar error ho to yeh **nahi hoga**.
* **`error`**: Agar error ho to yeh member **required** hota hai. Agar error na ho to yeh **nahi hoga**. Yeh aik `Error` object hota hai.
* **`id`**: Yeh **zaroori** hota hai aur request ke `id` ke barabar hota hai.

Response object mein `result` ya `error` **sirf ek hi** hoga — dono kabhi nahi.

#### 5. Error Object

Agar RPC call ke dauraan error aa jaye to `Response` object mein `error` member hota hai jisme:

* **`code`**: Integer jo error type batata hai.
* **`message`**: Short aur single-sentence error description.
* **`data`**: Extra detail (optional), jisko server define karta hai.

---

Here are some predefined error codes:

**Code — Message — Meaning**

-32700 — Parse error — Invalid JSON server ko receive hua.\
-32600 — Invalid Request — Jo JSON send kiya gaya woh valid Request object nahi hai.\
-32601 — Method not found — Method exist nahi karti ya available nahi hai.\
-32602 — Invalid params — Method ke parameters galat hain.\
-32603 — Internal error — Internal JSON-RPC error.\
-32000 to -32099 — Server error — Server ke taraf se defined errors ke liye reserved.

### 6. Batch Requests

Multiple Request objects aik sath bhejne ke liye, client Requests ka Array send karta hai. Server saari requests ko process karta hai aur unke corresponding Response objects ka Array return karta hai. Server batch requests ko kisi bhi order mein process kar sakta hai, aur responses bhi kisi bhi order mein aasakte hain. Client ko har request ke `id` se uske response ko match karna hota hai.

---

### Examples

Yahan kuch JSON-RPC 2.0 ke examples diye gaye hain:

#### RPC call with positional parameters:

**Client sends:**

```json
{"jsonrpc": "2.0", "method": "subtract", "params": [42, 23], "id": 1}
```

**Server responds:**

```json
{"jsonrpc": "2.0", "result": 19, "id": 1}
```

#### RPC call with named parameters:

**Client sends:**

```json
{"jsonrpc": "2.0", "method": "subtract", "params": {"subtrahend": 23, "minuend": 42}, "id": 3}
```

**Server responds:**

```json
{"jsonrpc": "2.0", "result": 19, "id": 3}
```

#### A notification:

**Client sends:**

```json
{"jsonrpc": "2.0", "method": "update", "params": [1, 2, 3, 4, 5]}
```

(No response from the server)

#### RPC call to a non-existent method:

**Client sends:**

```json
{"jsonrpc": "2.0", "method": "foobar", "id": "1"}
```

**Server responds:**

```json
{"jsonrpc": "2.0", "error": {"code": -32601, "message": "Method not found"}, "id": "1"}
```

---

### Extensions

Jo method names `rpc.` se start hotay hain woh system extensions ke liye reserved hain, aur kisi aur kaam ke liye use nahi karne chahiyen.

---

## Why JSON-RPC for Model Context Protocol (MCP), not REST?

Model Context Protocol (MCP) JSON-RPC choose karta hai REST ke bajaye kuch technical aur strategy reasons ki wajah se. Yeh samajhna aapko agent frameworks design aur integrate karne mein edge dega!

---

### 1. Agent/Model Operations ko REST ki CRUD se zyada ki zaroorat hoti hai

REST CRUD par based hai (Create, Read, Update, Delete), jo HTTP verbs per map hoti hai (GET, POST, PUT, DELETE).
Lekin LLM/Agent systems jaise MCP ko zyada complex operations chahiyen:

* Start, cancel, resume session
* Streaming
* Tools call karna
* Prompt state manage karna

JSON-RPC remote procedure calls ke liye bana hai — yani "yeh specific kaam karo aur result do" — is liye yeh natural fit hai.

---

### 2. Multiplexing & Streaming Support

* Same connection par multiple calls — JSON-RPC WebSocket/HTTP2/SSE ke saath real-time commands allow karta hai
* REST har request ke liye nayi connection kholta hai
* JSON-RPC notifications allow karta hai (server-initiated messages), REST mein yeh natural nahi

---

### 3. Explicit Method Names & Structured Requests

REST mein kaam endpoint + HTTP verb define karta hai.
JSON-RPC mein aap directly specify karte ho:

```json
{"method": "tools/call", ...}
```

Naye capabilities add karna asaan — bas new method name add.

---

### 4. Stateless vs Stateful Workflows

MCP stateful workflows support karta hai — jaise sessions, tools, context state. REST stateless best practice follow karta hai.

State protocol mein nahi hoti — server maintain karta hai session_id ya context id ke through.

---

### 5. Strong Error Handling

JSON-RPC standard structured error format deta hai: `code`, `message`, `data`.

REST error handling messy ho sakti hai — status codes + random formats.

---

### 6. Ecosystem Alignment (IDE Protocols)

LLM agents language servers jaise protocols follow karte hain:

* Language Server Protocol (LSP)
* Debug Adapter Protocol

Yeh dono JSON-RPC use karte hain.

---

## Summary Table

| Feature        | REST                  | JSON-RPC (MCP)        |
| -------------- | --------------------- | --------------------- |
| Paradigm       | Resource/CRUD         | Remote Procedure Call |
| Operations     | HTTP verbs only       | Named methods         |
| Streaming      | Difficult             | Native                |
| Multiplexing   | New request each time | Same connection       |
| Notifications  | No                    | Yes                   |
| Error Handling | Mixed                 | Standard              |
| State          | Stateless             | Sessions supported    |
| Extensibility  | URLs change           | Sirf new method       |

---

### Future Insight:

MCP jaise protocols AI orchestration ke future ke liye design hue hain — sirf CRUD ke liye nahi.

Inko chahiyen:

* Real-time interaction
* Fine-grained tool control
* Notifications
* Extensibility

JSON-RPC is work ke liye perfect choice hai, REST nahi.

---

