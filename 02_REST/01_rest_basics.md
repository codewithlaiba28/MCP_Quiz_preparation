# **REST kya hai?**
REST aik tareeqa hai web applications banane ka taake computers aapas mein internet ke zariye easily aur organized tareeqay se baat kar saken.

## 🔍 **Kya REST aik technology hai?**
Nahi, REST ye nahi hai:

* Programming language
* Software
* Tool
* Protocol jaise HTTP ya FTP

✅ REST aik style ya design pattern hai—ek set of rules jo batata hai ke web services kaise kaam karni chahiye.

## 📦 **Real-Life Misal**
Socho aap food delivery app use kar rahe ho:

* Aap food search karte ho
* Items cart mein dalte ho
* Order place karte ho
* Order status check karte ho

Ye sab actions backend server se baat karke RESTful APIs ke zariye hote hain.

Har cheez (food, cart, order) aik resource hai, aur aap unki representations ke saath interact kar rahe ho.

## 🔑 **REST ka matlab…**

| Term             | Simple Meaning                                                                        |
| ---------------- | ------------------------------------------------------------------------------------- |
| Representational | Aap real object access nahi karte—sirf uski copy (jaise JSON ya HTML) access karte ho |
| State            | Kisi cheez ka data ya condition (jaise aapke cart ka content)                         |
| Transfer         | Ye data client (aap) aur server (app backend) ke beech move hota hai                  |

## 🖼️ **REST kaam kaise karta hai – Step-by-Step**
Resources (jaise users, products, orders) ko URLs diye jate hain (jaise `api/products/1`)

Client (browser ya app) HTTP request bhejta hai jaise:

* GET → read karne ke liye
* POST → add karne ke liye
* PUT → update karne ke liye
* DELETE → delete karne ke liye

Server wapas ek representation bhejta hai (usually JSON ya XML)

## 🧱 **Example: REST in Shopping App**

| Action          | HTTP Method | URL         | Kya hota hai                       |
| --------------- | ----------- | ----------- | ---------------------------------- |
| See products    | GET         | /products   | Saare products ki list milti hai   |
| See one product | GET         | /products/5 | Product with ID 5 milta hai        |
| Add a product   | POST        | /products   | Naya product add hota hai          |
| Update product  | PUT         | /products/5 | Product with ID 5 replace hota hai |
| Delete product  | DELETE      | /products/5 | Product with ID 5 remove hota hai  |

---


# **REST ke 6 Simple Rules (Constraints)**

1. **Client-Server:** Frontend (browser/app) aur backend (server) alag rakho.
2. **Stateless:** Har request apne aap mein complete hoti hai. Server purani requests yaad nahi rakhta.
3. **Cacheable:** Responses ko store kiya ja sakta hai taake load kam ho aur speed tez ho jaye.
4. **Uniform Interface:** Saare resources same method se access hote hain (jaise GET/POST).
5. **Layered System:** Beech mein layers ho sakti hain jaise proxies ya load balancers.
6. **Code on Demand (optional):** Server client ko code bhej sakta hai (jaise JavaScript) run karne ke liye.

## ✅ **Summary (Easy Words)**

| Term           | Meaning                                               |
| -------------- | ----------------------------------------------------- |
| REST           | Web services banane ka design style                   |
| Not a protocol | HTTP use karta hai lekin HTTP nahi hai                |
| Resource       | Kisi bhi data ka piece (user, product, etc.)          |
| Representation | Data ki copy (jaise JSON) jo client ko bheji jati hai |
| Stateless      | Har request bilkul nayi tarah treat hoti hai          |

---

## **HATEOAS ka matlab kya hai?**

HATEOAS ka full form:

**Hypermedia As The Engine Of Application State**

🟢 Ye REST ka aik hissa hai jo kehta hai:

Server client ko links bheje apni responses mein, taake client ko pata ho agla step kya hai — bilkul jaise aap website browse karte ho.

📖 **Real-Life Misal: Website Browse karna**

Socho aap website use kar rahe ho:

* Aap homepage par land karte ho
* Aap links dekhte ho jaise "About", "Products", "Contact"
* Aap link click karte ho next page ke liye
* Aapko URLs yaad rakhne ki zarurat nahi — bas links follow karte ho

✅ Yehi HATEOAS ka matlab hai REST APIs ke liye.

---

## **🤖 REST APIs (Without HATEOAS vs With HATEOAS)**

❌ **Without HATEOAS:**
Client ko pehle se pata hona chahiye:

* Saare URLs (/users, /orders, /cart)
* Kya kar sakta hai

Jaise koi kahe:

> “Go to store.com/api/products, phir store.com/api/cart, aur phir store.com/api/checkout”

Agar URLs change ho gaye to client break ho jata hai.

✅ **With HATEOAS:**
Sirf aik known URL se start karte ho, jaise:

`GET /api`

Server reply karta hai:

```json
{
  "links": {
    "products": "/api/products",
    "cart": "/api/cart",
    "checkout": "/api/checkout"
  }
}
```

🔗 Ab client in links ko follow karta hai, jaise map.

Ye bilkul jaise server kehta hai: “Yeh dekho, agla kya kar sakte ho!”

---

**🔄 Example in REST API (JSON)**

Socho aapko aik user profile milta hai:

```json
{
  "id": 1,
  "name": "Wania",
  "links": {
    "self": "/api/users/1",
    "update": "/api/users/1",
    "delete": "/api/users/1",
    "orders": "/api/users/1/orders"
  }
}
```

✅ Ab client ko pata hai:

* Kaise user ko view karna hai
* Kaise update/delete karna hai
* Kaise uske orders lena hai
  Aur client ko kuch bhi yaad rakhne ki zarurat nahi!

---

## **🔑 HATEOAS kyun useful hai?**

| Benefit         | Simple Explanation                                         |
| --------------- | ---------------------------------------------------------- |
| 🔄 Flexible     | Server URLs change kar sakta hai without client break hue  |
| 🧭 Discoverable | Clients ko full guide ya list ki zarurat nahi              |
| 🔐 Secure       | Server control karta hai kaunse links/actions dikhaye jaye |
| 🔧 Evolvable    | Naye features add ho sakte hain without updating client    |

## 📝 **Summary**

| Term                     | Simple Meaning                                     |
| ------------------------ | -------------------------------------------------- |
| HATEOAS                  | Server client ko batata hai kya next kar sakta hai |
| Hypermedia               | Links (jaise websites mein) API response mein      |
| Client starts with 1 URL | Baaki discover karta hai links follow karke        |
| Less breakable           | Client hardcoded URLs par depend nahi karta        |

## 📦 **Real-Life Misal:**
Server ek tour guide hai — puri city map ek saath nahi deta, har step par batata hai aap kahan ja sakte ho next.

---

## **Idempotence ka matlab (simple words mein)**

Idempotence ka matlab hai:

**“Ek hi action bar bar karne ka effect same hai jaise ek dafa karna.”**

## 🧃 **Real-Life Example: Light Switch**

* Ek dafa switch off karo → Light off ✅
* 5 dafa switch off karo → Light still off ✅
  ➡️ Result same hai, action kitni dafa repeat ho isse farq nahi padta ✅

## 🍽️ **Dusra Example: Food Order Cancel karna**

* Ek dafa cancel karo → Order canceled
* Dobara cancel karo → Still canceled, kuch change nahi ✅
  ✅ Idempotent

Lekin agar order place karte ho:

* Ek dafa "Place Order" → 1 pizza ordered 🍕
* 3 dafa press karo → 3 pizzas ordered 😱
  ❌ Not idempotent

---

## **🌐 HTTP Methods aur Idempotence**

✅ **Idempotent Methods**

| Method  | Kya karta hai              | Kyun Idempotent                                   |
| ------- | -------------------------- | ------------------------------------------------- |
| GET     | Data get karna (read only) | Bar bar get karne se data change nahi hota        |
| HEAD    | Sirf headers get karna     | Body nahi, kuch change nahi hota                  |
| OPTIONS | Poochna kya allowed hai    | Sirf question, modify nahi karta                  |
| PUT     | Data replace karna         | Same data bar bar bhejne se result same rehta hai |
| DELETE  | Resource delete karna      | 1 ya 10 dafa delete = still deleted               |

### ✅ **Example:**

```http
PUT /users/1
{
  "name": "Wania"
}
```

Isko 100 dafa bhejna same hai jaise ek dafa bhejna.

---

## ❌ **Non-Idempotent Methods**

| Method | Kya karta hai             | Kyun Not Idempotent                                     |
| ------ | ------------------------- | ------------------------------------------------------- |
| POST   | Naya item create karna    | Har request usually naya item create karta hai          |
| PATCH  | Data ka part modify karna | Idempotent ho sakta hai, careful handle karna padta hai |

### 🚫 **Example:**

```http
POST /users
{
  "name": "Wania"
}
```

3 dafa bhejne par 3 users create ho sakte hain → Not idempotent

---

## ✅ **Summary Table**

| Method  | Idempotent?  | Why?                                     |
| ------- | ------------ | ---------------------------------------- |
| GET     | ✅ Yes        | Sirf read karta hai                      |
| HEAD    | ✅ Yes        | Sirf headers read karta hai              |
| OPTIONS | ✅ Yes        | Sirf poochta hai, kuch change nahi karta |
| PUT     | ✅ Yes        | Existing data replace karta hai          |
| DELETE  | ✅ Yes        | Multiple tries ke baad bhi deleted       |
| POST    | ❌ No         | Naye items add karta hai                 |
| PATCH   | ⚠️ Sometimes | Depend karta hai use par                 |

## 📦 **Final Tip:**
Agar request repeat karne se result same rehta hai → Idempotent
Agar data add hota hai ya naya create hota hai → Not idempotent

---



