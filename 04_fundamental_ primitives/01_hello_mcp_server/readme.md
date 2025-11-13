# **01: Hello, MCP Server!**
Objective: Apna pehla, bohot basic Model Context Protocol (MCP) server FastMCP library use karke stateless mode mein run karna.

## 🌐 **MCP vs. Jo Aap Shayad Jante Hain**

| Agar aap jaante hain... | MCP hai jaise...                                             | Key difference                                  |
| ----------------------- | ------------------------------------------------------------ | ----------------------------------------------- |
| REST APIs               | Ek standard protocol, lekin AI-tool communication ke liye    | Specifically AI interactions ke liye design hua |
| OpenAI Function Calling | Function calling jo kisi bhi AI model ke sath kaam karta hai | Universal, kisi ek provider tak limited nahi    |
| Webhooks                | AI aur external systems ke darmiyan two-way communication    | Specifically AI use cases ke liye structured    |
| Plugin Systems          | AI models ke liye plugin system                              | Cross-platform aur standardized                 |

## **Ye initial step focus karta hai basic essentials par:**

* Ek server create karna jo har request independently handle kare.
* Server ko Stateless Streamable HTTP ke zariye accessible banana.
* Ek spec-compliant client use karna jo initialize handshake correctly perform kare.

Ye MCP development ke liye “Hello, World!” ki tarah hai. Ye simplest server configuration provide karta hai aur correct client-side interaction flow sikhata hai.

**Key MCP Concepts**

* **FastMCP Server:** Ek Python library jo MCP 2025-06-18 specification ke low-level details handle karti hai.
* **Stateless HTTP Transport (stateless_http=True):** FastMCP mein ek convenient mode hai jahan server har request ko nayi, independent interaction samajhta hai. Ye session handle karta hai aur turant bhool jata hai, jo basic request-response pattern sikhne ke liye perfect hai bina persistent state manage kiye.

**Implementation Plan**
Hello-mcp/ subdirectory ke andar:

**server.py:**

* Ek FastMCP server instantiate karna stateless mode mein (stateless_http=True).
* Server ko runnable ASGI application ke taur par uvicorn ke liye expose karna.

**client.py:**

* Ek simple Python script jo httpx use karke JSON-RPC requests banata hai.
* Pehle initialize call karega spec follow karne ke liye.

**Postman Collection:**

* postman/ directory mein ek collection hai jo spec-compliant, three-step interaction flow visually demonstrate karta hai.

**Key Concepts**

* **FastMCP:** Ek Python library jo MCP-compliant servers create karna simplify karti hai. Ye MCP protocol ke complex parts handle karta hai, taake aap server ke capabilities define karne par focus kar sakein.
* **Server Instantiation:** FastMCP application ka instance create karna.
* **Server Metadata:** Server ke basic info provide karna (jaise name aur version) jo clients ke sath initialization ke dauran share hota hai.
