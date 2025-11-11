# **REST (Representational State Transfer)**
REST, yaani **Representational State Transfer**, ek software architectural style hai jo networked applications, khaas tor par web services ko design karne ke liye use hota hai.

Isay pehli dafa Roy Fielding ne 2000 mein apni doctoral dissertation mein define kiya tha, jo World Wide Web ki architecture ke principles par mabni thi.

REST koi protocol ya specific technology nahi hota, balkay constraints ka ek set hota hai jo apply karne se system scalable, stateless aur reliable ban jata hai. Iska basic idea yeh hota hai ke clients server ke paas mojood resources ke representations ke saath interact karte hain.


----



## Core Architectural Constraints of REST

REST ko six guiding architectural constraints define kartay hain. In constraints par amal karne ka maqsad aise systems banana hota hai jin mai performance, scalability, simplicity, modifiability, visibility, portability, aur reliability jaise non-functional qualities paayi jayein.

1. **Client-Server Architecture**:

   * Client (jo user interface concerns handle karta hai) aur server (jo data storage, business logic, aur security handle karta hai) ke darmiyan separation assume ki jati hai.
   * Yeh separation client aur server components ko independently evolve karne ki ijazat deta hai, jab tak unke darmiyan interface consistent rahe.

2. **Statelessness**:

   * Har request jo client server ko bhejta hai, usme sari information honi chahiye jo server ko request samajhne aur process karne ke liye darkar ho.
   * Server kisi client context (session state) ko requests ke darmiyan store nahi karta. Koi bhi session state client side par rakhi jati hai.
   * Benefits: Scalability improve hoti hai (koi bhi server koi bhi request handle kar sakta hai), reliability barhti hai (failures se recover karna aasaan hota hai), aur visibility improve hoti hai (monitoring aasaan hoti hai kyunke har request independent hoti hai).

3. **Cacheability**:

   * Server responses ko clearly batana hota hai ke wo cacheable hain ya nahi.
   * Agar response cacheable ho, to client (ya kisi intermediary jaise CDN) response ko aage ke similar requests ke liye reuse kar sakta hai.
   * Benefits: Latency kam hoti hai, network efficiency improve hoti hai, aur server load reduce hota hai.

4. **Layered System**:

   * REST architecture layered system hota hai. Ek layer ke components sirf adjacent layers ke components ke saath interact karte hain.
   * Client aam tor par yeh identify nahi kar sakta ke wo directly end server se connected hai ya kisi intermediary (e.g., load balancer, proxy, API gateway) ke zariye.
   * Benefits: Scalability barhti hai load balancing aur shared caching se. Security policies bhi different layers par enforce ki jati hain.

5. **Code on Demand (Optional)**:

   * Servers temporary taur par client ki functionality ko executable code (e.g., JavaScript applets ya scripts) transfer karke extend ya customize kar sakte hain.
   * Yeh REST ka sirf optional constraint hai. Yeh powerful hai lekin visibility ko kam kar sakta hai, aur modern REST API design mai data exchange ko zyada emphasis diya jata hai.

6. **Uniform Interface**:

   * Yeh REST ko doosri architectural styles se distinguish karta hai. Yeh architecture ko simplify aur decouple karta hai, jisse har part independently evolve kar sakta hai. Uniform Interface chaar sub-constraints par mabni hai:

     1. **Identification of Resources**: Har resource (jaise user profile, product, articles ka collection) ko unique Uniform Resource Identifiers (URIs), aksar URLs, se identify kiya jata hai.
     2. **Manipulation of Resources Through Representations**: Clients resources ke sath unki representations exchange karke interact karte hain. Representation resource ki state ka snapshot hota hai kisi waqt par, aam tor par JSON ya XML format mein. Representation (metadata ke sath) client ko resource modify ya delete karne ke liye kaafi honi chahiye.
     3. **Self-Descriptive Messages**: Har message (request ya response) jo client aur server ke darmiyan exchange hota hai, usme itni information hoti hai ke receiver usay samajh kar process kar sake. Isme shamil hota hai:

        * Resource URI
        * HTTP method (verb) jo desired action show karta hai
        * Headers mein metadata (e.g., `Content-Type`, `Accept`)
        * Payload (POST/PUT requests aur responses ke liye)
     4. **Hypermedia as the Engine of Application State (HATEOAS)**: Yeh REST ka mature aur aksar kam implement hone wala aspect hai. Clients ko possible actions aur navigation hyper-links ke zariye milti hai jo server response mein hoti hain. Client ko pehle se saare URIs ka pata nahi hota — wo ek initial URI se start karta hai aur server ke diye links follow karta hai. Is se server apni URI space aur actions evolve kar sakta hai baghair clients toray.

---


**Key Concepts in RESTful APIs**
Jab RESTful APIs (wo APIs jo REST principles follow karti hain) ki baat hoti hai, to kuch central concepts hote hain:

**Resources:** REST ka sab se basic concept. Resource koi bhi information ya entity ho sakti hai jo naam aur address se identify ho. Examples: ek document, ek image, ek user, ek service, ya dusre resources ka collection. Resources ko URIs se identify kiya jata hai.

**Representations:** Jab client kisi resource ko request karta hai, server us resource ki state ka ek representation bhejta hai. Ye aam tor par JSON ya XML format mein hota hai, lekin HTML, plain text, images, waghera bhi ho sakta hai. Ek hi resource ke multiple representations ho sakti hain (jaise ek user resource JSON ya XML mein).

**HTTP Methods (Verbs):** Standard HTTP methods resources par operations perform karne ke liye use hoti hain (Create, Read, Update, Delete – CRUD):

* **GET:** Resource ya resource collection ka representation retrieve karna.
* **POST:** Naya resource create karna. Usually un actions ke liye jo directly CRUD operations mein fit nahi hotay.
* **PUT:** Existing resource ko poori tarah replace karna. Agar resource exist na kare, to create bhi kar sakta hai.
* **DELETE:** Resource remove karna.
* **PATCH:** Existing resource ko partially update karna.
* **OPTIONS:** Target resource ke liye communication options jaise allowed HTTP methods lena.
* **HEAD:** Sirf resource ke headers retrieve karna, body nahi (GET jaisa hai lekin response body nahi).

**HTTP Status Codes:** Standard codes jo response mein use hote hain to indicate request ka outcome. Examples:

* **200 OK:** Request successful.
* **201 Created:** Resource successfully create ho gaya (usually POST ya PUT response mein).
* **204 No Content:** Request successful hai, lekin return karne ke liye content nahi (jaise successful DELETE).
* **400 Bad Request:** Server request process nahi kar sakta client error ki wajah se (jaise malformed syntax).
* **401 Unauthorized:** Authentication required hai aur fail ya abhi provide nahi hui.
* **403 Forbidden:** Server ne request samjhi, lekin authorize karne se inkaar kiya (client ke paas permission nahi).
* **404 Not Found:** Requested resource server par nahi mili.
* **500 Internal Server Error:** Generic error message jab server pe unexpected condition encounter ho.

**Idempotence:** Ek operation idempotent hai agar multiple identical requests ka effect same ho jaise ek hi request ka effect. HTTP mein:

* **GET, HEAD, OPTIONS, PUT, DELETE** usually idempotent hote hain.
* **POST** generally idempotent nahi (multiple POSTs usually multiple resources create karte hain).
* **PATCH** carefully implement karne par idempotent ho sakta hai (jaise conditional requests use kar ke).

**Media Types:** Representation ka format specify karte hain (jaise application/json, application/xml, text/html, image/jpeg). Ye **Content-Type** (request/response bodies ke liye) aur **Accept** (client-chahie response formats ke liye) headers ke through communicate hota hai.

---



# **Designing a RESTful API - Best Practices**
REST ek architectural style hai, lekin kuch **best practices** hain jo practical aur user-friendly RESTful HTTP APIs design karne ke liye follow ki jati hain:

## 1. **Use Nouns for Resource URIs:**

   * URIs ko resources identify karna chahiye, actions nahi.
   * Collections ke liye plural nouns use karein.
   * **Good Examples:** `/users`, `/users/{userId}`, `/orders`, `/products/{productId}/reviews`
   * **Avoid:** `/getAllUsers`, `/createNewUser`, `/products/delete/{productId}`

## 2. **Use HTTP Methods Correctly:**

   * CRUD operations ko sahi HTTP methods se map karein:

     * GET → read
     * POST → create
     * PUT → replace
     * PATCH → partial update
     * DELETE → remove

## 3. **Provide Meaningful HTTP Status Codes:**

   * Standard status codes use karein jo requests ka outcome accurately indicate karein.

## 4. **Support Common Data Formats:**

   * JSON (`application/json`) modern REST APIs ke liye most common hai.
   * XML (`application/xml`) bhi use hota hai.

## 5. **Filtering, Sorting, and Pagination:**

   * Collections ke liye clients ko filter, sort aur paginate karne ke options provide karein.
   * Example: `/users?status=active&sort=lastName&offset=0&limit=20`

## 6. **Versioning:**

   * API evolution ke liye plan karein. Common strategies:

     * **URI Path Versioning:** `/v1/users`, `/v2/users` (simple aur common)
     * **Query Parameter Versioning:** `/users?version=1`
     * **Custom Header Versioning:** `X-API-Version: 1`
     * **Media Type Versioning (Content Negotiation):** `Accept: application/vnd.myapi.v1+json`

## 7. **Clear Error Handling:**

   * Error status code return hone par response body mein informative error messages dein.
   * Include karein: error code, human-readable message, aur links to documentation.
   * **Example:**

   ```json
   {
     "error": {
       "code": "INVALID_INPUT",
       "message": "The 'email' field is required and must be a valid email address.",
       "details_url": "https://api.example.com/docs/errors#INVALID_INPUT"
     }
   }
   ```

## 8. **Security:**

   * Robust authentication aur authorization implement karein.
   * **Authentication:** API Keys, OAuth 2.0 (Bearer Tokens), JWTs
   * **Authorization:** Role-Based Access Control (RBAC), OAuth 2.0 scopes
   * Hamesha **HTTPS (TLS encryption)** use karein.

## 9. **Documentation:**

   * API ki comprehensive, accurate aur easy-to-understand documentation provide karein.
   * Tools jaise **OpenAPI (Swagger)** widely use hote hain.

## 10. **HATEOAS (Optional but Recommended):**

    * Responses mein links include karein jo clients ko related resources aur available actions tak guide karein, discoverability promote karte hain.

---

# **Practical Example: Raw RESTful API Request and Response Messages**
Ye example HTTP requests aur responses ka raw text format dikhata hai, jo REST principles follow karta hai:

* **GET request** → specific user resource retrieve karna (`/users/123`)
* **Server GET response** → JSON representation of user
* **POST request** → naya user resource create karna (`/users`)
* **Server POST response** → creation confirm karna JSON representation ke saath

Ye messages hypothetical API `api.example.com` ke liye hain aur REST concepts highlight karte hain: resource URIs, representations, self-descriptive messages, aur optionally **HATEOAS links** for discoverability.

---

# **Raw RESTful API Messages aur Unke Components**
Neeche raw HTTP messages diye gaye hain, har ek ke baad uske components ka explanation diya gaya hai, jisme focus hai ke ye REST principles ko kaise embody karte hain. Messages bilkul waise hi formatted hain jaise network transaction mai appear hote hain, proper line breaks aur spacing ke saath.

---

# **1. GET Request**

```
GET /users/123 HTTP/1.1
Host: api.example.com
Accept: application/json
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
Accept-Language: en-US,en;q=0.5
Connection: keep-alive
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

**Explanation:**

## **REST Principles Demonstrated:**

* **Identification of Resources:** URI `/users/123` ek specific user resource ko uniquely identify karta hai, REST convention ke mutabiq nouns resources ko represent karte hain.
* **Statelessness:** Request mai saari necessary information (URI, headers, authentication token) included hai taake server bina client ke stored context ke process kar sake.
* **Uniform Interface:** GET method use hota hai resource ka representation retrieve karne ke liye, Accept header format specify karta hai (application/json).

## **Message Components:**

* **Start-Line:** GET /users/123 HTTP/1.1
* **Method:** GET – user resource ka representation retrieve karne ke liye.
* **URI:** /users/123 – specific user ID 123 ko identify karta hai.
* **HTTP Version:** HTTP/1.1
* **Headers:**

  * Host: api.example.com – API domain specify karta hai.
  * Accept: application/json – JSON format request karta hai.
  * User-Agent – client identify karta hai (browser ya custom client).
  * Accept-Language – preferred language response ke liye.
  * Connection: keep-alive – TCP connection maintain karne ke liye.
  * Authorization – Bearer token include karta hai for authentication.
* **Empty Line:** Headers aur body ko separate karta hai.
* **Body:** None – GET requests usually data retrieve karte hain aur body nahi hoti.

---

### **2. GET Response**

```
HTTP/1.1 200 OK
Date: Thu, 12 Jun 2025 09:19:00 GMT
Server: Nginx/1.18.0
Content-Type: application/json; charset=UTF-8
Content-Length: 165
Cache-Control: max-age=3600
Connection: keep-alive

{
  "id": 123,
  "name": "Alice Smith",
  "email": "alice@example.com",
  "_links": {
    "self": {"href": "/users/123"},
    "update": {"href": "/users/123", "method": "PATCH"},
    "delete": {"href": "/users/123", "method": "DELETE"}
  }
}
```

## **Explanation:**

## **REST Principles Demonstrated:**

* **Manipulation of Resources Through Representations:** Response JSON mai user resource ka state show karta hai (id, name, email).
* **Self-Descriptive Messages:** Content-Type header format specify karta hai aur body mai saara data included hai.
* **HATEOAS:** `_links` object related actions ke hyperlinks deta hai (self, update, delete).
* **Cacheability:** Cache-Control header (max-age=3600) response ko 1 hour ke liye cache karne allow karta hai.

## **Message Components:**

* **Start-Line:** HTTP/1.1 200 OK
* **HTTP Version:** HTTP/1.1
* **Status Code:** 200 – request successful.
* **Reason Phrase:** OK
* **Headers:**

  * Date – response ka timestamp
  * Server – server software identify karta hai
  * Content-Type – JSON format aur UTF-8 encoding specify karta hai
  * Content-Length – JSON body ka length bytes mai
  * Cache-Control – caching enable karta hai
  * Connection: keep-alive – connection reuse allow karta hai
* **Empty Line:** Headers aur body ko separate karta hai
* **Body:** JSON object with HATEOAS links

---

# **3. POST Request**

```
POST /users HTTP/1.1
Host: api.example.com
Accept: application/json
Content-Type: application/json
Content-Length: 65
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
Connection: keep-alive
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

{
  "name": "Bob Johnson",
  "email": "bob@example.com"
}
```

## **Explanation:**

## **REST Principles Demonstrated:**

* **Identification of Resources:** URI `/users` user collection ko identify karta hai jahan naya user create hoga.
* **Statelessness:** Request mai saari data (JSON payload, authentication token) included hai, server-side session ki zarurat nahi.
* **Uniform Interface:** POST method naya resource create karne ke liye, Content-Type aur Accept headers JSON specify karte hain.
* **Manipulation of Resources Through Representations:** JSON body naya user ka representation provide karti hai.

## **Message Components:**

* **Start-Line:** POST /users HTTP/1.1
* **Method:** POST – naya resource create karne ke liye
* **URI:** /users – users collection target
* **HTTP Version:** HTTP/1.1
* **Headers:** Same as GET request + Content-Type, Content-Length
* **Empty Line:** Headers aur body separate karta hai
* **Body:** JSON object with name aur email

---

# **4. POST Response**

```
HTTP/1.1 201 Created
Date: Thu, 12 Jun 2025 09:19:05 GMT
Server: Nginx/1.18.0
Content-Type: application/json; charset=UTF-8
Content-Length: 188
Location: /users/124
Connection: keep-alive

{
  "id": 124,
  "name": "Bob Johnson",
  "email": "bob@example.com",
  "_links": {
    "self": {"href": "/users/124"},
    "update": {"href": "/users/124", "method": "PATCH"},
    "delete": {"href": "/users/124", "method": "DELETE"}
  }
}
```

## **Explanation:**

## **REST Principles Demonstrated:**

* **Manipulation of Resources Through Representations:** Response naya user ka JSON representation return karta hai, server-assigned id ke saath.
* **Self-Descriptive Messages:** Content-Type aur Location headers response aur naya resource URI ke baare mai batate hain.
* **HATEOAS:** `_links` object hyperlinks provide karta hai for further actions.
* **Uniform Interface:** 201 Created status code aur Location header successful resource creation aur URI batate hain.

## **Message Components:**

* **Start-Line:** HTTP/1.1 201 Created
* **HTTP Version:** HTTP/1.1
* **Status Code:** 201 – resource successfully created
* **Reason Phrase:** Created
* **Headers:** Same as GET response + Location
* **Empty Line:** Headers aur body separate karta hai
* **Body:** JSON object with new user aur HATEOAS links

---


| **Message / Concept** | **Key Points (Roman Urdu)**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| --------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **GET Request**       | - URI `/users/123` specific user ko identify karta hai<br>- GET method data retrieve karta hai<br>- Headers mai Accept, Authorization, Connection etc. hote hain<br>- Body usually nahi hoti<br>- Stateless: request mai saari info included                                                                                                                                                                                                                                                                                                                                                   |
| **GET Response**      | - JSON format mai user ka data return hota hai<br>- Status: 200 OK<br>- HATEOAS links: self, update, delete<br>- Cache-Control: max-age=3600 (1 hour cache)<br>- Headers mai Date, Server, Content-Type etc. included                                                                                                                                                                                                                                                                                                                                                                          |
| **POST Request**      | - URI `/users` naya user create karne ke liye<br>- POST method use hota hai<br>- Body mai JSON payload: name aur email<br>- Stateless: saari required info included<br>- Headers: Content-Type, Authorization etc.                                                                                                                                                                                                                                                                                                                                                                             |
| **POST Response**     | - JSON mai naya user ka data return hota hai<br>- Status: 201 Created<br>- Location header: `/users/124` (new resource URI)<br>- HATEOAS links included<br>- Headers similar to GET response                                                                                                                                                                                                                                                                                                                                                                                                   |
| **Key REST Concepts** | - **Client-Server:** Request aur response alag<br>- **Stateless:** Each request self-contained<br>- **Cacheable:** GET response caching support<br>- **Uniform Interface:** Same method rules<br>- **Resource Identification:** URIs uniquely identify resources<br>- **Representation:** JSON payloads show resource state<br>- **Self-Descriptive:** Headers make messages interpretable<br>- **HATEOAS:** Links guide next actions<br>- **HTTP Methods:** GET for read, POST for create<br>- **HTTP Status Codes:** 200 OK, 201 Created<br>- **Media Types:** application/json consistently |



---

# ***REST vs. Other Architectural Styles/Protocols***

### **SOAP (Simple Object Access Protocol):**
SOAP aik protocol hai jismein sakht rules hote hain, aam tor par XML format use hota hai messages bhejne ke liye, aur WSDL par depend karta hai services describe karne ke liye.

REST aik architectural style hai jo zyada flexible hota hai, aam tor par JSON aur HTTP use karta hai, aur OpenAPI jaisi cheezein use kar sakta hai description ke liye.

SOAP thora complex aur lamba hota hai, lekin ismein built-in security standards (WS-Security) aur transactions support hoti hai, isi liye zyada enterprise systems mein use hota hai.

### **GraphQL short Roman Urdu version:**

GraphQL APIs ke liye aik query language hai aur server par queries run karne ka system bhi hai. Ismein client sirf wohi data mangta hai jo usay chahiye, is liye extra ya kam data nahi milta jaise REST mein hota hai. GraphQL usually aik hi endpoint use karta hai (jaise /graphql) aur zyada tar HTTP POST hota hai. REST mein multiple endpoints hote hain aur different HTTP verbs use hote hain. Dono sath bhi use ho sakte hain — GraphQL flexible data ke liye, aur REST simple operations ke liye.

### **gRPC short Roman Urdu version:**

gRPC Google ka high-performance RPC framework hai jo different environments mein chal sakta hai. Ismein Protocol Buffers use hote hain services aur messages define karne ke liye, aur transport ke liye HTTP/2 hota hai. Yeh bohot fast, low-latency aur strongly-typed communication deta hai, is liye microservices ke liye bohot acha hai. Jabke REST resources par focus karta hai aur normal HTTP system use karta hai, jo zyada common aur asaan hota hai.


## **REST vs SOAP vs GraphQL vs gRPC**

| Technology  | Kya Hai              | Use Case                         | Data Format      | Endpoint Style                    |
| ----------- | -------------------- | -------------------------------- | ---------------- | --------------------------------- |
| **REST**    | Architectural style  | Web APIs, simple apps            | JSON/HTTP        | Multiple endpoints                |
| **SOAP**    | Strict protocol      | Enterprise, secure systems       | XML              | WSDL + multiple operations        |
| **GraphQL** | Query language       | Flexible data fetch, modern apps | JSON (mostly)    | Single endpoint                   |
| **gRPC**    | High-performance RPC | Microservices, fast systems      | Protocol Buffers | Typically single endpoint, HTTP/2 |

---



## **REST ki Strengths :**

* **Simplicity aur Asaani:**
REST samajhna aur use karna asaan hai kyunke yeh HTTP methods aur URIs par based hota hai.

* **Scalability:**
REST stateless hota hai aur caching support karta hai, jis se systems easily scale ho sakte hain.

* **Interoperability aur Wide Adoption:**
Har language aur platform mein support milta hai, is liye bohot zyada use hota hai.

* **Flexible Data Formats:**
REST mein JSON zyada use hota hai, lekin XML, HTML, text ya koi bhi format use ho sakta hai.

* **Web Infrastructure ka Faida:**
REST standard web cheezein use karta hai jaise HTTP, URLs, DNS aur caching.

* **Discoverability (HATEOAS):**
Agar HATEOAS sahi implement ho to client API ke links follow karke automatically navigate kar sakta hai.


----


## **REST ki Weaknesses / Limitations (Roman Urdu)**

* **Over-fetching aur Under-fetching:**
REST fixed resource return karta hai, is liye kabhi zaroorat se zyada data mil jata hai (over-fetch) aur kabhi complete data lane ke liye multiple requests karni padti hain (under-fetch). GraphQL yeh issue solve karta hai.

* **Multiple Round Trips:**
Agar data complex ho to related information lane ke liye client ko kaafi dafa server se request karni padti hai, jis se latency barh sakti hai.

* **Stateless Hone ka Overhead:**
Har request independent hoti hai, is liye bar bar authentication token ya extra info bhejni parti hai.

* **Real-time Support ki Kami:**
REST pull-based model hai. Real-time updates ke liye WebSockets ya SSE zyada behtar hain kyunke REST push-based communication nahi deta.

* **Standardization Loose Hoti Hai:**
REST ek style hai, strict rules nahi. Har developer apni interpretation bana leta hai, jis se APIs mein differences aa jate hain.

* **Zyada Endpoints Manage Karna:**
Agar system bohot large ho to endpoints bohot zyada ho jate hain, jinhein manage karna mushkil ho sakta hai.

---

## **Use Cases in Agentic AI Systems (DACA) – Roman Urdu (Short & Clear)**

REST APIs agentic AI systems (DACA pattern) mein bohot important role play karti hain:

### **1. Core Agent Functions:**
REST endpoints se agent ki capabilities, status aur tasks manage kiye jaate hain.
Examples:
`GET /agents/{id}/status` → agent ki halat janna
`POST /agents/{id}/tasks` → agent ko naya task dena

### **2. Tool Integration:**
Agents dusre web tools ya services se connect hote hain jo REST APIs deti hain — jese weather API, search engine, knowledge base etc.

### **3. Data Storage & Retrieval:**
Agents databases, vector stores wagaira mein data store ya fetch karte hain REST ke through.

### **4. Agent-to-Agent Communication:**
Agar simple request-response communication ho, to agents REST se easily baat kar sakte hain — specially jab agents microservices hon.

### **5. System Management:**
DACA infrastructure (deploy, scale, monitor agents) REST APIs ke zariye manage hota hai.

### **6. Human-in-the-Loop Dashboards:**
Web dashboards jo humans ko agents control karne deti hain, backend se REST API ke zariye connect hoti hain.

### **7. Model Serving:**
Chote models ya custom inference logic REST API se expose kiya ja sakta:
`POST /models/{id}/predict`

### **8. Logging & Monitoring:**
Agents apne logs aur metrics REST API se central system ko bhejte hain.

---

**Summary :**
DACA agent system mein REST APIs alag components — agents, tools, data services, UI — ko aasani se communicate, manage aur scale karne mein help karti hain. ✅
