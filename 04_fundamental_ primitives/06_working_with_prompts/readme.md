# 7. **Working with Prompts**
   *Pre-crafted prompts banayein aur use karein taake common workflows aur AI interactions asaan ho jayein.*

---

### 💡 **Understanding MCP Prompts**

MCP mein **prompts** pre-crafted (pehle se likhe hue) instructions hote hain jo common workflows ke liye use hote hain.
Ye **user-controlled** hote hain — matlab user decide karta hai ke kab aur kaise use karna hai.
Tools aur resources ke baraks, prompts AI ko **guidance aur structure** dete hain taake uska response behtar ho.

---

### 🤔 **Why Use Prompts?**

Socho: user seedha likh sakta hai *“reformat the report.pdf in markdown”* — aur AI ek theek response de dega.
Lekin agar aap ek **specialized aur tested prompt** use karte ho jo har edge case handle karta hai aur best practices follow karta hai, to result **bahut zyada accurate aur professional** hota hai.

MCP server author ke taur par aap ye prompts likh kar, test kar kar ke optimize kar sakte ho taake wo har scenario mein sahi kaam karein.
Users ko is se faida ye hota hai ke unhe **prompt engineering expert** banne ki zarurat nahi hoti — wo seedha aapke optimized prompts use kar sakte hain.

---

### ⚙️ **Key Characteristics of Prompts**

* **User-controlled:** User khud decide karta hai kab prompt use karna hai.
* **Instruction-focused:** High-quality aur reusable instructions provide karte hain.
* **Context-aware:** Dynamic content aur formatting include kar sakte hain.
* **Reusable:** Alag-alag scenarios mein use kiye ja sakte hain.
* **Structured:** Har baar consistent pattern follow karte hain taake result reliable ho.

---

### 🔄 **How Prompts Work?**

Prompts ek **set of user aur assistant messages** define karte hain jo client use kar sakta hai.
Ye high-quality, tested aur MCP server ke purpose ke mutabiq hone chahiye.

**Workflow:**

1. Apne server ke function se related ek prompt likho aur evaluate karo.
2. MCP server mein `@mcp.prompt` decorator use karke prompt define karo.
3. Client kisi bhi waqt prompt request kar sakta hai.
4. Client ke diye gaye arguments aapke function mein keyword arguments ke roop mein pass hote hain.
5. Function formatted messages return karta hai jo AI model ko bheje jaate hain.

Is system se **reusable aur parameterized prompts** bante hain jo consistency maintain karte hue customization allow karte hain.
Ye khas taur par un workflows ke liye useful hain jahan aap chahte ho ke AI ko har baar **properly structured instructions** milein.

---

### 🧩 **Core MCP Prompts Concepts**

* **Prompt Discovery:** `prompts/list` ka use karke available templates dhoondo.
* **Prompt Generation:** `prompts/get` se customized prompts banao.
* **Parameter Handling:** Dynamic customization ke sath type validation ensure karo.

---

🆕 **2025-06-18 Features:**
Title fields, enhanced metadata, aur capabilities declaration add ki gayi hain.
