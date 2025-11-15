# 5. Working with Resources
   Class-05: Model Context Protocol - Defining Resources aur MCP Client

MCP servers mein **resources** ka matlab hai woh data jo aap client ko dikhana chahte ho — bilkul usi tarah jaise ek HTTP server mein GET request hoti hai. Ye un situations ke liye perfect hain jahan aapko sirf information leni hoti hai, koi action perform nahi karna hota.

🏗️ **MCP Resources vs. Jo Aap Pehle Se Jaante Ho**

| Agar aap familiar ho...              | MCP Resources bilkul aise hain jaise...     | Key faida                                     |
| ------------------------------------ | ------------------------------------------- | --------------------------------------------- |
| File Systems                         | Files jise AI browse aur read kar sakta hai | AI ke liye structured aur discoverable        |
| REST API GET endpoints               | Read-only API endpoints                     | Metadata aur categorization built-in hoti hai |
| RAG (Retrieval Augmented Generation) | AI ke liye knowledge base                   | Har AI platform par standardized              |
| Documentation Sites                  | Docs jise AI navigate kar sakta hai         | Self-describing aur rich metadata ke sath     |
| Database Views                       | Queryable data collections                  | AI-friendly format aur discovery ke sath      |

### ⚙️ Key Characteristics of Resources

* **Read-only:** Resources sirf data provide karte hain, koi action nahi karte.
* **URI-based:** Ye specific URIs ke zariye access hote hain, jisme parameters ho sakte hain.
* **MIME-typed:** Alag alag content types (JSON, text, images, etc.) support karte hain.
* **App-controlled:** Application decide karti hai ke kab resource expose karna hai.
* **Static ya templated:** Direct resource ya parameterized dono ho sakte hain.

Har resource ka ek **unique URI** hota hai aur wo **text** ya **binary** data contain kar sakta hai.

---

### 📎 Resource URIs

Resources ko identify karne ke liye URIs ka format use hota hai, jaise:

```
file:///home/user/documents/report.pdf  
postgres://database/customers/schema  
screen://localhost/display1
```

Ye protocol aur path structure MCP server ke implementation par depend karta hai. Servers apne custom URI schemes bhi define kar sakte hain.

---

### 🧾 Resource ke Do Type ke Content:

* **Text resources:** UTF-8 encoded text data hota hai. Ye suitable hain source code, configuration files, JSON/XML data waghera ke liye.
* **Binary resources:** Raw binary data hota hai jo base64 me encode hota hai. Ye images, PDFs, audio/video files aur dusre non-text formats ke liye hota hai.

---

### 🔄 How Resources Work?

Resources ek **request-response pattern** follow karte hain. Jab client ko data chahiye hota hai, to wo ek **ReadResourceRequest** send karta hai jisme URI hota hai jisse identify hota hai ke kaunsa resource chahiye. MCP server is request ko process karta hai aur **ReadResourceResult** ke form me data return karta hai.

Resources kisi bhi type ka data return kar sakte hain — jaise strings, JSON, binary data, etc.
**mime_type** parameter use karke aap client ko bata sakte ho ke kis type ka data return ho raha hai:

* `"application/json"` structured data ke liye
* `"text/plain"` plain text ke liye
* `"application/pdf"` binary files ke liye

MCP Python SDK automatically aapke return values ko serialize karta hai.
Aapko manually objects ko JSON strings me convert karne ki zarurat nahi hoti — sirf data structure return karo aur SDK serialization handle karega.

---

### 🔹 Types of Resources

**1. Direct Resources**
Direct resources ke URIs static hote hain jo kabhi change nahi hote.
Ye un operations ke liye perfect hain jahan parameters ki zarurat nahi hoti.

**2. Templated Resources**
Templated resources ke URIs me parameters hote hain.
Python SDK in parameters ko automatically parse karta hai aur unhe aapke function me keyword arguments ke taur par pass karta hai.


---

### 🔍 Testing Resource Access

Jab aap resources implement kar lo, to aap unki functionality ko test kar sakte ho apne tools ke zariye:

1. **MCP Inspector start karo** taake verify ho sake ke server resources sahi implement hue hain.
2. **Postman collection use karo** taake resources ko detail me samjha ja sake.
3. **CLI application** use karo — jab aap **"@"** type karte ho aur uske baad resource ka naam likhte ho, to system ye karta hai:

   * Available resources ko **autocomplete list** me dikhata hai.
   * Arrow keys aur space se resource **select** karne deta hai.
   * Resource ka content directly aapke **prompt** me include karta hai.
   * Ye sab kuch AI model ko send hota hai **bina extra tool calls** ke.

Iske alawa, **Postman** me naye requests — `"List Documents Resource"` aur `"Get Document Content"` — use karke aap resource endpoints ko directly verify kar sakte ho.

Ye process AI model ke liye documents access karne ke liye **zyada smooth aur fast experience** create karta hai, bina alag-alag tool calls ke.
