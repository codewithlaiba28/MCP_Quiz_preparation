# **🌐 What is HTTP?**
HTTP ka matlab hai HyperText Transfer Protocol.

Ye computers ke liye ek tareeqa hai ke wo internet par ek doosre se baat kar saken.
Specifically, ye wo tareeqa hai jisse aapka browser (jaise Chrome) cheezen mangta hai, jaise web pages, aur server aapko aapke mangi hui cheez deta hai.

📌 Isay aise socho:
Aap (browser) ek restaurant (server) jaate ho, menu (webpage) dekhte ho, aur waiter (HTTP) ko batate ho ke aapko kya chahiye. Waiter kitchen (server logic) mein jaata hai aur aapko dish (response jaise HTML, JSON, image, etc.) laake deta hai.

## **HTTP important kyun hai?**
Har dafa jab aap:

* Website kholte ho
* Form submit karte ho
* Website par login karte ho
* Video dekhte ho

Aap background mein HTTP ka use kar rahe ho!

## 🔄 **HTTP Request-Response Cycle (Bohat Important!)**
Ye HTTP ka heart hai. Ye do logon ke beech baat-cheet jaisa hai:

👤 **1. Client (Aap / Aapka Browser)**
Aap client ho. Aapko kuch chahiye, jaise webpage.

🧑‍🍳 **2. Server (Website ka Backend)**
Server kitchen jaisa hai. Ye aapko wo cheez deta hai jo aapne mangi.

⚙️ **Step-by-step: Kaise kaam karta hai**
Maan lo aap visit karte ho [https://example.com](https://example.com).

📨 **Step 1: Client Request Send karta hai**
Aapka browser server ko request bhejta hai. Request mein shamil hota hai:

* **Method (Kaunsa action chahiye):**

  * GET: Kuch paana (jaise webpage)
  * POST: Kuch bhejna (jaise form)
* **URL (Kya access karna hai)**
* **Headers (Extra info jaise aap kaun ho, browser type, etc.)**
* **Body (Sirf kabhi-kabhi—data bhejne ke liye, jaise login info)**

🖥️ **Step 2: Server Request Receive karta hai**
Server request receive karta hai aur decide karta hai:

* Kya manga gaya hai?
* Kya allowed hai?
* Data kahan hai?
* File return kare? Webpage? Ya error?

📬 **Step 3: Server Response Send karta hai**
Server response bhejta hai. Isme shamil hai:

* **Status Code:** Bataata hai kya hua

  * 200 OK: Sab theek hua
  * 404 Not Found: Page nahi mila
  * 500 Internal Server Error: Kuch toot gaya
* **Headers:** File type info (HTML, JSON, image), server info
* **Body:** Asal content (HTML page, JSON data, error message, etc.)

💻 **Step 4: Browser Result Show karta hai**
Aapka browser response process karta hai aur aapko website ya data dikhata hai.
