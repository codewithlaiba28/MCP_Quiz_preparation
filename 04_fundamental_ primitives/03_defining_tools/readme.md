# 03: Defining Tools with MCP
## **Introduction**
Is step mein, aap seekhenge ke kaise MCP tools create aur use kiye jaate hain FastMCP Python SDK ke sath. Ye guide aapko dikhayegi ke kaise apne Python functions ko asaan aur hassle-free tools mein convert karein.

**How Tools Work: Discovery and Execution**
Yahan process ka simple overview hai:

* **Finding Tools:** MCP client `tools/list` request bhejta hai taake available tools ki list mil sake.
* **Using Tools:** Jab aap kisi tool ko run karna chahte hain, client `tools/call` request bhejta hai tool ka naam aur required parameters ke sath.
* **Handling Errors:** Agar kuch galat hota hai (jaise document missing ho), tool Python error raise karta hai jo automatically MCP error response mein convert ho jata hai.

Neeche ek simple diagram diya gaya hai jo process ko illustrate karta hai:

---
