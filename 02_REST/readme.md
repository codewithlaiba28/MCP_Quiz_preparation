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



**Designing a RESTful API - Best Practices**
REST ek architectural style hai, lekin kuch **best practices** hain jo practical aur user-friendly RESTful HTTP APIs design karne ke liye follow ki jati hain:

1. **Use Nouns for Resource URIs:**

   * URIs ko resources identify karna chahiye, actions nahi.
   * Collections ke liye plural nouns use karein.
   * **Good Examples:** `/users`, `/users/{userId}`, `/orders`, `/products/{productId}/reviews`
   * **Avoid:** `/getAllUsers`, `/createNewUser`, `/products/delete/{productId}`

2. **Use HTTP Methods Correctly:**

   * CRUD operations ko sahi HTTP methods se map karein:

     * GET → read
     * POST → create
     * PUT → replace
     * PATCH → partial update
     * DELETE → remove

3. **Provide Meaningful HTTP Status Codes:**

   * Standard status codes use karein jo requests ka outcome accurately indicate karein.

4. **Support Common Data Formats:**

   * JSON (`application/json`) modern REST APIs ke liye most common hai.
   * XML (`application/xml`) bhi use hota hai.

5. **Filtering, Sorting, and Pagination:**

   * Collections ke liye clients ko filter, sort aur paginate karne ke options provide karein.
   * Example: `/users?status=active&sort=lastName&offset=0&limit=20`

6. **Versioning:**

   * API evolution ke liye plan karein. Common strategies:

     * **URI Path Versioning:** `/v1/users`, `/v2/users` (simple aur common)
     * **Query Parameter Versioning:** `/users?version=1`
     * **Custom Header Versioning:** `X-API-Version: 1`
     * **Media Type Versioning (Content Negotiation):** `Accept: application/vnd.myapi.v1+json`

7. **Clear Error Handling:**

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

8. **Security:**

   * Robust authentication aur authorization implement karein.
   * **Authentication:** API Keys, OAuth 2.0 (Bearer Tokens), JWTs
   * **Authorization:** Role-Based Access Control (RBAC), OAuth 2.0 scopes
   * Hamesha **HTTPS (TLS encryption)** use karein.

9. **Documentation:**

   * API ki comprehensive, accurate aur easy-to-understand documentation provide karein.
   * Tools jaise **OpenAPI (Swagger)** widely use hote hain.

10. **HATEOAS (Optional but Recommended):**

    * Responses mein links include karein jo clients ko related resources aur available actions tak guide karein, discoverability promote karte hain.

---

**Practical Example: Raw RESTful API Request and Response Messages**
Ye example HTTP requests aur responses ka raw text format dikhata hai, jo REST principles follow karta hai:

* **GET request** → specific user resource retrieve karna (`/users/123`)
* **Server GET response** → JSON representation of user
* **POST request** → naya user resource create karna (`/users`)
* **Server POST response** → creation confirm karna JSON representation ke saath

Ye messages hypothetical API `api.example.com` ke liye hain aur REST concepts highlight karte hain: resource URIs, representations, self-descriptive messages, aur optionally **HATEOAS links** for discoverability.

---


