# ✅ **curl kya hai?**
`curl` ek command-line tool hai jo aapko HTTP requests bhejne aur responses dekhne deta hai.
Ye Linux, macOS, aur Windows (Git Bash ya WSL ke saath) par chal jata hai.

Hum yahan ek test server use karenge:
`https://reqres.in` — ye ek fake REST API hai practice ke liye.

---

### **1️⃣ GET – Data hasil karna**

Users ki list lene ke liye:

```bash
curl https://reqres.in/api/users?page=2
```

➡️ Response:

```json
{
  "page": 2,
  "data": [
    { "id": 7, "email": "michael.lawson@reqres.in", ... }
  ]
}
```

✅ Ye bilkul webpage open karke us ka data dekhne jaisa hai.

---

### **2️⃣ POST – Data bhejna (jaise signup form)**

Naya user banane ke liye:

```bash
curl -X POST https://reqres.in/api/users \
  -H "Content-Type: application/json" \
  -d '{"name": "Wania", "job": "Developer"}'
```

➡️ Response:

```json
{
  "name": "Wania",
  "job": "Developer",
  "id": "245",
  "createdAt": "2025-06-17T22:00:00.000Z"
}
```

✅ Naya account create karne jaisa.

---

### **3️⃣ PUT – Pura data update karna**

User ka data replace karna:

```bash
curl -X PUT https://reqres.in/api/users/2 \
  -H "Content-Type: application/json" \
  -d '{"name": "Wania", "job": "Senior Dev"}'
```

➡️ Response:

```json
{
  "name": "Wania",
  "job": "Senior Dev",
  "updatedAt": "2025-06-17T22:05:00.000Z"
}
```

✅ Purana job replace ho gaya.

---

### **4️⃣ PATCH – Thoda sa data update karna**

Sirf job update karna:

```bash
curl -X PATCH https://reqres.in/api/users/2 \
  -H "Content-Type: application/json" \
  -d '{"job": "Engineer"}'
```

➡️ Response:

```json
{
  "job": "Engineer",
  "updatedAt": "2025-06-17T22:10:00.000Z"
}
```

✅ Sirf job change hua, name same raha.

---

### **5️⃣ DELETE – User delete karna**

```bash
curl -X DELETE https://reqres.in/api/users/2
```

➡️ Status: **204 No Content**

✅ User delete ho gaya.

---

### **6️⃣ HEAD – Sirf headers lena (content nahi)**

```bash
curl -I https://reqres.in/api/users/2
```

➡️ Output:

```
HTTP/1.1 200 OK
Content-Type: application/json
Content-Length: 123
```

✅ Sirf metadata check karne ke liye use hota hai.

---

### **7️⃣ OPTIONS – Endpoint kya allow karta hai**

```bash
curl -X OPTIONS https://reqres.in/api/users/2 -i
```

➡️ Response:

```
Allow: GET, POST, PUT, PATCH, DELETE, OPTIONS
```

✅ Batata hai is URL par konsa method allowed hai.

---

### 📝 **Summary Table**

| Method  | curl Command             |
| ------- | ------------------------ |
| GET     | `curl URL`               |
| POST    | `curl -X POST -d ...`    |
| PUT     | `curl -X PUT -d ...`     |
| PATCH   | `curl -X PATCH -d ...`   |
| DELETE  | `curl -X DELETE URL`     |
| HEAD    | `curl -I URL`            |
| OPTIONS | `curl -X OPTIONS -i URL` |

---

