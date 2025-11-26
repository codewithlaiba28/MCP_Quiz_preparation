## **MCP kya hai**
MCP aik standard hai jo batata hai ke aik AI app (host) kis tarah aik ya zyada “MCP servers” se connect karta hai jo tools, resources aur prompts expose karte hain.
Iska wire format **JSON-RPC 2.0** hota hai.
Yeh **stateful** hota hai, jisme pehle **initialization handshake** hota hai jo capabilities negotiate karta hai, aur phir **long-lived messaging** hoti hai requests, responses aur notifications ke liye.


Here is the text converted into **Roman Urdu**:

---

## **1. Data layer.**
Yeh layer lifecycle management define karti hai, aur woh primitives jin mein tools, resources, aur prompts shamil hote hain.
Iske andar client-side primitives bhi hotay hain jin ko server call back kar sakta hai (sampling, elicitation, logging), aur notifications bhi shamil hoti hain.
Yeh sab kuch **JSON-RPC 2.0** par hota hai.

---

## **2. Transport layer.**
Yeh layer batati hai ke messages kis tarah move karte hain.
Aaj ke spec ke mutabiq do standard transports hain:

* **stdio** jo local processes ke liye hota hai
* **Streamable HTTP** jo remote servers ke liye hota hai

Server-to-client streaming ke liye optional **SSE** bhi hoti hai.
Authentication normal HTTP methods se hoti hai, jaise **bearer tokens** ya custom headers.



----

Here is the full text converted into **clear, correct Roman Urdu**:

---

### **Core primitives par focus karein**

**Server expose karta hai:**

**• Tools.**
Aise executable functions jo client call kar sakta hai.
Inhein tools/list se discover kiya jata hai aur tools/call se chalaya jata hai.

**• Resources.**
Read-only context jaisay files, schemas, ya API responses.
Inhein resources/list se discover aur resources/read se fetch kiya jata hai.

**• Prompts.**
Server ke diye huay templates jinko parameterize kiya ja sakta hai.
prompts/list aur prompts/get se inka istemaal hota hai.

---

### **Client expose karta hai:**

**• Sampling.**
Server client ko keh sakta hai ke woh LLM se completion hasil kare using sampling/complete.

**• Elicitation.**
Server client se extra user input maang sakta hai.

**• Logging.**
Server logs ko client tak stream karta hai.
Yeh sab initialization ke waqt negotiate hota hai taake dono taraf ko pata ho kya available hai.

---

### **Workflow**

**initialize.**
Client protocolVersion aur apni capabilities bhejta hai, aur serverInfo + server capabilities wapas milti hain.

**notifications/initialized.**
Client batata hai ke woh ready hai.

**Discovery.**
tools/list, resources/list, prompts/list jaisa zarurat ho.

**Execution.**
tools/call, resources/read, prompts/get — progress aur notifications ke saath, agar supported hon.

**Notifications.**
Jaise notifications/tools/list_changed jab tools ka inventory change ho jaye.

---

### **Transports — kab kya use karein**

#### **Stdio**

• Local development, CLIs, aur editors ke liye best (jab woh child process start karte hain).
• Sabse kam latency, koi network nahi.
• Claude Desktop aur VS Code jaisay tools mein aam tor par use hota hai.

---

#### **Streamable HTTP**

• Remote servers ke liye best, ya jab aap normal HTTP auth aur routing chahte ho.
• Client-to-server POST request use hoti hai, aur server-to-client optional streaming SSE semantics se hoti hai.
• Hosted servers aur cloud platforms mein bohot istemaal hota hai.

---

### **SSE aur WebSockets ka kya scene hai?**

Spec ka current focus **stdio** aur **Streamable HTTP** par hai,
aur HTTP par optional SSE-style streaming supported hai.

Kuch community SDKs ka kehna hai ke SSE ko dheere dheere Streamable HTTP ke favor mein replace kiya ja raha hai.

---

## Hosted MCP tool (model calls the server directly, no Python callback round-trip)
• Use HostedMCPTool. You pass a server label or connector config. • Good for minimizing latency and infrastructure on your side. ([OpenAI GitHub][3])


---

1. **Question 1**
   What is the primary purpose of MCP in agentic-AI systems?

        A) To train large language models faster     
        B) To provide a standardized way for models to connect with external tools, data sources and workflows
        C) To replace all REST-APIs used in AI systems
        D) To restrict access of AI models to private data
   **Correct answer:** B

2. **Question 2**
   Which of the following best describes a “transport” mechanism in the context of MCP?

        A) The hardware device used by the client application
        B) The underlying protocol/medium by which MCP messages are carried (e.g., HTTP, stdio, SSE)
        C) The model’s internal embedding transport between layers
        D) The file-transfer mechanism for large datasets in MCP

   **Correct answer:** B

3. **Question 3**
   In MCP, when a client first connects to a server it commonly does what?

        A) Immediately invokes a tool without capability negotiation
        B) Sends a query to retrieve the server’s list of supported capabilities/tools/resources
        C) Trains the server on new data
        D) Switches to another transport automatically
   **Correct answer:** B

4. **Question 4**
   Which of the following is a benefit of using MCP transports and capabilities architecture?   

        A) Eliminates the need for any authentication when connecting tools
        B) Forces every model to use the same programming language
        C) Enables reusable, plug-and-play tool integrations across different AI agents and platforms
        D) Prevents any model from accessing external data
   **Correct answer:** C

5. **Question 5**
   Which challenge does MCP help to mitigate in building AI agent systems?

        A) The need for larger training datasets only
        B) The integration explosion (N×M problem) of many models and many tools/data sources
        C) The elimination of agents entirely
        D) Only model size scaling
   **Correct answer:** B

---


