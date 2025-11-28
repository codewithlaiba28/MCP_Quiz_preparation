# 07: MCP Resources - Current State and Future (Roman Urdu)

**MCP Resources** — ye ek powerful feature hai jo MCP servers ko allow karta hai ke wo data aur content expose kare jo clients read kar sakte hain aur LLM interactions me context ke liye use ho sakta hai. Lekin abhi ye feature OpenAI Agents SDK me work-in-progress hai.

---

### **Current State: Resources Support Limited**

**Available abhi:**

* MCP Resources specification exist karti hai aur well-defined hai
* Individual MCP servers resources implement kar sakte hain
* Manual resource handling custom code se possible hai

**Missing abhi:**

* Native integration OpenAI Agents SDK me nahi
* Agent workflows me automatic resource processing nahi
* Tool outputs se built-in resource link parsing nahi

**GitHub PR: #1042**

Ye PR MCP Resources support SDK me add karne ke liye ongoing hai.

**PR me Add kya hota hai:**

* MCPServer base class me 3 abstract methods:

  * `list_resources()`
  * `list_resource_templates()`
  * `read_resource()`
* `_MCPServerWithClientSession` me implementation
* Example MCP resources server with demo
* Updated documentation with examples

**PR me Include nahi hota:**

* `subscribe_resource` aur `unsubscribe_resource` methods
* Agent workflows me automatic integration
* Tool outputs se resource link parsing

---

### **Key Discussion Points**

**Big Question:** "Kya ye actually useful hai?"

* @artificial-aidan ne kaha: Tool calls links return kar sakte hain, lekin abhi agent flow me resources automatically integrate nahi hote.

**OpenAI Response:**

* @seratch clarified: Abhi SDK ka agent mechanism resources directly use nahi karta. Proposed support sirf code base me methods add karta hai, lekin agent inko use karne ke liye custom code likhna padega.

---

### **Implications for You**

**Right Now:**

* MCP resources manually handle karo
* Custom code likho for resource links
* Automatic agent integration nahi hai

**Future (agar PR #1042 merge hota hai):**

* Helper methods milenge resources handle karne ke liye
* Agent flows me integrate karne ke liye abhi bhi custom logic chahiye
* SDK infrastructure provide karega, lekin automatic integration nahi

---

### **Learning Takeaways**

* MCP Resources data expose karne ke liye powerful concept hai
* Abhi OpenAI Agents SDK me limitations hain
* Future me development ke saath possibilities badh sakti hain
* Filhal manual implementation required hai
