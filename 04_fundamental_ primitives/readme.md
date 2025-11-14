# **Module 4: MCP Fundamental Primitives**
Model Context Protocol ke core building blocks ko hands-on coding ke zariye master karein
Anthropic ke *Introduction to Model Context Protocol* course par based

## **Pehle MCP Course ke Introduction Lessons padhein**

MCP sirf desktop applications ko agentic functionality se enhance karne ke liye nahi hai. Ye reusable tools aur resources expose karne ke liye hai taake agentic microservices build ki ja sakein. Dekhein:

- [Model Context Protocol (MCP) Explained for Beginners: AI Flight Booking Demo!](https://www.youtube.com/watch?v=E2DEHOEbzks)
- [Why MCP really is a big deal | Model Context Protocol with Tim Berglund](https://www.youtube.com/watch?v=FLpS7OfD5-s)

Model Context Protocol (MCP) ek communication layer hai Agents ke context aur tools ke liye, taake har project ke liye tedious integration code na likhna pade. Isay use karke tool definitions aur execution ka burden aapke server se MCP servers par shift kiya ja sakta hai.

Agar Github ke paas MCP server hai aur mera agent kuch GitHub Actions manage karna chahta hai, toh phir dubara kyun likhein?
Jaise companies APIs provide karti hain, waise hi ab woh MCP implementation create karenge.

Ye transport agnostic hai kuch caveats ke sath – client aur server alag protocols ke zariye communicate kar sakte hain.

### **Overview**
Is module mein MCP ke teen fundamental primitives introduce kiye jayenge: Tools, Resources, aur Prompts. Aap MCP servers aur clients Python SDK ke zariye build karna seekhenge, practical, code-driven examples ke sath jo real-world applications demonstrate karte hain.

## 📚 **Learning Objectives**
Is module ke end tak, aap ye kar paenge:

### **Core Competencies**
✅ Python SDK ke zariye MCP servers build karein with decorator-based tool definitions\
✅ Teenon MCP primitives implement karein: Tools (model-controlled), Resources (app-controlled), Prompts (user-controlled)\
✅ MCP clients create karein jo servers se connect aur interact kar sakein\
✅ MCP Server Inspector use karein server functionality ko test aur debug karne ke liye

### **Technical Skills**
✅ Tools define karein decorators ke zariye, manually JSON schemas likhne ke bajaye\
✅ File management functionality implement karein tools ke zariye for reading, writing, aur managing files\
✅ Resources create karein jo read-only data expose karein with proper MIME type handling\
✅ Prompts build karein jo pre-crafted instructions provide karein common workflows ke liye\
✅ Errors handle karein gracefully with proper exception handling aur user feedback

### **Understanding**
✅ MCP primitives ko distinguish karein: Kab tools use karne hain, kab resources, aur kab prompts\
✅ Control models samjhein: Model-controlled (tools), app-controlled (resources), user-controlled (prompts)\
✅ Best practices apply karein security, performance, aur maintainability ke liye

---


## **Prerequisites**

* Python programming ka working knowledge
* JSON aur HTTP request-response patterns ki basic samajh
* Python mein decorators aur type hints ki familiarity

### **Learning Structure**

## **1. Project Setup aur First Server**
### **Goal:**
Development environment establish karein aur apna pehla working MCP server create karein

* **01_hello_mcp_server** – Development environment setup karna uv ke sath using base_project
* **02_project_setup** – Apna Base Project set karein is learning module ke liye

## **2. Building Tools aur Resources**
### **Goal:** 
Practical examples ke zariye MCP ke teen fundamental primitives master karein

* **03_defining_tools** – Tools create karna decorators aur type hints ke sath
* **04_implementing_client** – MCP tools ke liye simple client create karein
* **05_defining_resources.md** – Read-only data resources create karein
* **06. Working with Prompts** – Common workflows ke liye pre-crafted prompts build karein

# **MCP Core Primitives**

## **1. Tools (Model-Controlled)**
Tools wo functions hain jo AI models call kar sakte hain actions perform karne ke liye. Ye hain:

* **Model-controlled:** AI decide karta hai kab aur kaise use karna hai
* **Action-oriented:** Specific tasks perform karte hain jaise files read karna, API calls karna
* **Decorator-based:** Python decorators aur type hints ke zariye define kiye jate hain

## **2. Resources (App-Controlled)**
Resources read-only access provide karte hain data ka. Ye hain:

* **App-controlled:** Application decide karta hai kab expose karna hai
* **Data-focused:** Documents, databases, APIs tak access provide karte hain
* **URI-based:** Specific URIs ke zariye access hote hain with optional parameters

## **3. Prompts (User-Controlled)**
Prompts pre-crafted instructions hain common workflows ke liye. Ye hain:

* **User-controlled:** Users decide karte hain kab apply karna hai
* **Instruction-focused:** High-quality, reusable prompts provide karte hain
* **Context-aware:** Dynamic content aur formatting include kar sakte hain

---


