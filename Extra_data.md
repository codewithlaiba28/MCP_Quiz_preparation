| Part   | Kya hota hai           | Example                     |
| ------ | ---------------------- | --------------------------- |
| Header | Metadata, instructions | Content-Type, Authorization |
| Body   | Actual data            | Form data, JSON, files      |
----
### **1. HTTP Request-Response Cycle**

Client (browser) server se TCP/IP connection banata hai.\
Phir client request bhejta hai.\
Server request ko process karta hai aur response wapas bhejta hai.\
Client response ko show (print/render) karta hai.

---

GET request → headers jaate hain, body nahi. Response mai body aati hai.

POST request → headers + body jaate hain, response mai headers + body dono ho sakte hain.

Header → sirf metadata hota hai.

Body → actual data hota hai.

----

# **Set-Cookie Header**

Ye response header hai jo server client ke browser mai cookie set karne ke liye bhejta hai.

Cookie ek chhoti si file hoti hai jo browser store karta hai aur future requests ke sath server ko bheji jati hai.

**Example:**

Set-Cookie: sessionId=abc123; Expires=Wed, 13 Nov 2025 12:00:00 GMT; Path=/; HttpOnly


**Explanation:**

* sessionId=abc123 → cookie ka naam aur value
* Expires → cookie kab expire hogi
* Path=/ → kaunse path ke liye cookie valid hai
* HttpOnly → JavaScript se access nahi ho sakti (security ke liye)



---

**HTTP/0.9: The Simple Start (Early 1990s)**

1. **Need (Zarurat):**

* Jab web naya tha, sirf basic cheez chahiye thi: **hypertext documents (HTML pages) ko fetch karna**.
* Matlab: browser ko server se page lene ka simple tareeqa chahiye tha.

2. **Protocol (Tareeqa):**

* Bohot hi simple design tha.
* Client (jaise browser) sirf **ek line** bhejta:

  ```
  GET /path/to/document
  ```
* Isme **versions, headers, status codes** kuch nahi tha.

  * Version: HTTP ka version nahi bata sakte the.
  * Headers: Extra information (jaise content type) nahi bhej sakte.
  * Status codes: Server sirf content bhejta, fail ya success ka koi code nahi hota.
* Server ka kaam sirf HTML content bhejna aur connection close kar dena tha.

3. **Takeaway (Samajhne wali baat):**

* Ye design **apne limited purpose ke liye kaam karta tha** – sirf simple web pages lana.
* **Richer interactions** jaise data server ko bhejna, request fail check karna, ya extra information lena possible nahi tha.
* Agar aapko ye karna hota: impossible!

---

**Simple analogy:**
Socho aap post office mein ja rahe ho aur bas **ek simple letter** bhej rahe ho bina sender address ya return information ke. Agar letter lose ho jaye ya post office problem ho, aapko pata nahi chalega. Yehi tha HTTP/0.9 – sirf simple letter bhejna aur receive karna.

---


### **HTTP vs HTTPS (Short Version)**

* **HTTP:** Plain-text, data encrypt nahi hota, hack ho sakta hai.
* **HTTPS:** Secure version, **TLS/SSL** se encrypted.

**TLS Features:**

* **Encryption:** Data safe
* **Integrity:** Data tampered nahi
* **Authentication:** Server verify

**Security Tips:**

* Hamesha **HTTPS use karo**
* **HSTS:** Browser ko force karta hai HTTPS use karne ke liye
* **Cookies:** `HttpOnly`, `Secure`, `SameSite` use karo
* **Input Validation:** XSS/SQL injection prevent kare
* **CORS:** Decide kare ke resources dusre domains se kaise access ho

---


* UDP alone → secure nahi, bas fast aur lightweight.

* QUIC (UDP + security layer) → fast bhi + encryption bhi (HTTP/3 me use hota hai).

-----
---

REST (Representational State Transfer)
REST aik **tariqa** hai web apps aur APIs banane ka. Yeh koi protocol nahi, bas rules ka set hota hai jisko follow karke fast, simple aur reliable web systems banaye jate hain.

Isay Roy Fielding ne 2000 mein introduce kiya tha.

REST ka simple idea yeh hai:

* Client (jaise browser/app) server se baat karta hai
* Server ke paas data hota hai (resources)
* Client server se data mangta hai ya update karta hai

Matlab:
Client request bhejta hai → Server reply deta hai

REST APIs mein mostly HTTP methods use hotay hain jaise GET, POST, PUT, DELETE.

Yeh style use karne se apps simple, fast aur easy to manage ban jati hain.


----



## Core Architectural Constraints of REST — Simple Explanation

REST ko banane ke 6 important rules hote hain. In rules ko follow karne se system fast, easy, secure aur reliable banta hai.

### 1. **Client-Server Architecture**

* Client = jahan user hota hai (browser / app)
* Server = jahan data hota hai

Client aur server alag hote hain.
Client sirf request bhejta hai, server data bhejta hai.
Is tarah dono apna kaam alag aur easily update ho sakte hain.

---

### 2. **Statelessness**

* Har request ke sath saari info honi chahiye.
* Server pichli request ya session yaad nahi rakhta.

Result:
System fast, scalable aur easy to handle hota hai.

---

### 3. **Cacheability**

* Server batata hai ke data cache ho sakta hai ya nahi.
* Agar cache ho jaye to client dubara request nahi bhejta.

Result:
Speed tez hoti hai, load kam hota hai, internet usage kam hoti hai.

---

### 4. **Layered System**

* System layers mein hota hai (proxy, security layer, load balancer etc)
* Client ko nahi pata hota ke wo kis layer se connect hai.

Result:
System zyada secure aur scalable hota hai.

---

### 5. **Code on Demand (Optional)**

* Server client ko thoda code bhej sakta hai (jaise JavaScript)
* Yeh optional feature hai.

Result:
Client ki functionality barh sakti hai.
Par ye feature zyada use nahi hota.

---

### Short Summary ✅

| Rule           | Easy Meaning                         |
| -------------- | ------------------------------------ |
| Client-Server  | Client aur server alag               |
| Stateless      | Server request store nahi karta      |
| Cacheable      | Data save ho sakta hai speed ke liye |
| Layered        | System layers mein hota hai          |
| Code on Demand | Server client ko code de sakta hai   |

---

### 6. **Uniform Interface**
**Uniform Interface** REST ka ek basic rule hai jo ensure karta hai ke client aur server ka communication simple aur predictable ho. Iske 4 main parts hain:

1. **Identification of Resources (Resource ko pehchanna)**

   * Har cheez jo server pe available hai, jaise user, product, ya article, uska ek unique address hota hai (URL).
   * Example: `https://example.com/users/1` ek specific user ko identify karta hai.

2. **Manipulation of Resources Through Representations (Resource ke data ke zariye kaam karna)**

   * Client resource ke snapshot (jaise JSON ya XML) ke saath kaam karta hai.
   * Agar client ko resource update karna hai, to wo ye snapshot server ko bhejta hai.
   * Example: JSON mein user ka data:

     ```json
     { "name": "Laiba", "age": 20 }
     ```

     Agar client isko update karta hai, server samajh jata hai kya change karna hai.

3. **Self-Descriptive Messages (Message khud explain kare)**

   * Har request aur response itni info rakhta hai ke receiver samajh sake:

     * Kaunsa resource access karna hai (URL)
     * Kaunsa action karna hai (GET, POST, PUT, DELETE)
     * Kaisa data bhej rahe hain (headers aur payload)
   * Matlab har message independent hai aur clearly communicate karta hai.

4. **HATEOAS (Hypermedia as the Engine of Application State)**

   * Client ko server ki saari URLs pehle se nahi pata hoti.
   * Client ek initial URL se start karta hai aur server ke response mein diye links follow karta hai.
   * Example: Server response:

     ```json
     {
       "user": {"name": "Laiba"},
       "links": {
         "update": "/users/1/update",
         "delete": "/users/1/delete"
       }
     }
     ```
   * Client simply `update` ya `delete` link follow karke action le sakta hai.

**Simple Summary:**
Uniform Interface REST ko simple, flexible, aur predictable banata hai:

* Har cheez ka unique address
* Client resource data ke saath interact kare
* Messages clear aur self-explanatory ho
* Client links follow kare, server ka URI structure pehle se na jane

---


**1. Resource (Resource kya hai):**

* Resource REST ka basic unit hai.
* Ye koi bhi **cheez ya information** ho sakti hai jo server pe store ho aur jisko uniquely identify kiya ja sakta hai.
* Har resource ka ek **unique URL/URI** hota hai.
* **Examples:**

  * Ek user: `https://example.com/users/1`
  * Ek article: `https://example.com/articles/101`
  * Ek image ya document: `https://example.com/images/logo.png`

**Simple tareeqa:** Resource **“kya hai”** ko represent karta hai.

---

**2. Representation (Representation kya hai):**

* Jab client resource ko request karta hai, server us resource ka **snapshot** bhejta hai.
* Ye snapshot hi **representation** kehlata hai.
* Representation bataata hai resource ka **current state** ek particular format mein.
* **Formats:** JSON, XML, HTML, plain text, images, etc.
* **Example:** Agar user resource hai, to representation JSON mein kuch is tarah ho sakti hai:

```json
{
  "id": 1,
  "name": "Laiba",
  "age": 20
}
```

**Simple tareeqa:** Representation **resource ka data** hota hai jo client aur server ke beech exchange hota hai.

---


Filter = kya chahiye?

Sort = kis order mein chahiye?

Pagination = kitne items aur kaunse page?

----

Path = URI mein version

Query = URL ke end mein version

Header = HTTP header mein version

Media Type = Accept header mein version

---

JSON-RPC aur REST dono HTTP ke through use kiye jaate hain, lekin JSON-RPC sirf HTTP tak limited nahi — WebSockets waghera ke sath bhi use hota hai. REST mostly HTTP ke sath use hota hai.