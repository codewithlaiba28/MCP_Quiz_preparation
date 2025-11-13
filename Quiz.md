Perfect! Chalo shuru karte hain. Pehla question ye hai:

---

**Question 1:**

What was the main limitation of **HTTP/0.9**?

A) It could handle multiple concurrent requests
B) It supported only a single line GET request with no headers or status codes
C) It introduced binary framing
D) It ran on QUIC instead of TCP


---
Correct ✅
HTTP/0.9 sirf **single line GET request** support karta tha, headers ya status codes nahi the.

---

**Question 2:**

Which new feature was introduced in **HTTP/1.0** to provide more information about requests and responses?

A) QUIC protocol
B) Persistent Connections
C) HTTP Headers
D) Multiplexing

---

**Correct answer:** C) **HTTP Headers**
HTTP/1.0 ne **headers introduce kiye** taake client aur server zyada information exchange kar saken (jaise Content-Type aur User-Agent).

---

**Question 3:**

What was the main improvement in **HTTP/1.1** that reduced the overhead of opening a new TCP connection for every request?

A) Persistent Connections (Keep-Alive)
B) Header Compression (HPACK)
C) Independent Streams
D) Server Push

---

Correct ✅
HTTP/1.1 ka **Persistent Connections (Keep-Alive)** feature allow karta tha ke ek TCP connection multiple requests aur responses ke liye reuse ho, latency bohot reduce ho gayi.

---

**Question 4:**

Which feature of **HTTP/2** helps eliminate Head-of-Line (HOL) blocking at the HTTP level?

A) Binary Framing and Multiplexing
B) Host Header
C) Pipelining
D) Status Codes

---


Correct ✅
HTTP/2 ka **Binary Framing aur Multiplexing** feature multiple requests/responses ko ek hi TCP connection pe concurrently allow karta hai, jis se **HTTP-level HOL blocking** eliminate ho jata hai.

---

**Question 5:**

What is the transport protocol used by **HTTP/3** instead of TCP?

A) HTTP/1.1
B) QUIC (UDP-based)
C) TLS 1.2
D) Binary Framing

----

Correct ✅
HTTP/3 **QUIC (UDP-based)** pe run karta hai, jo TCP ke limitations jaise HOL blocking aur latency ko solve karta hai.

---

**Question 6:**

Which feature of **HTTP/3** allows a connection to survive when the client’s IP changes (e.g., Wi-Fi to cellular)?

A) Server Push
B) Connection Migration
C) Persistent Connections
D) Header Compression

---


**Correct answer:** B) **Connection Migration**
HTTP/3 allows connections to survive **changes in the client’s IP address**, jaise Wi-Fi se cellular switch karna.

---

**Question 7:**

In **HTTP/1.1**, what is **HOL (Head-of-Line) Blocking**?

A) Slow response in one request blocking all others on the same connection
B) Compression of HTTP headers to save bandwidth
C) Server proactively sending resources
D) Running HTTP over UDP

----


Correct ✅
**HOL (Head-of-Line) Blocking** ka matlab hai ke **ek slow response baki requests ko same connection pe block kar deta hai**.

---

**Question 8:**

Which HTTP version first introduced **POST and HEAD methods**?

A) HTTP/0.9
B) HTTP/1.0
C) HTTP/1.1
D) HTTP/2

---

Correct ✅
**HTTP/1.0** ne **POST (data send karne ke liye) aur HEAD (sirf headers lene ke liye) methods** introduce kiye.

---

**Question 9:**

Which feature of **HTTP/2** reduces the size of headers and saves bandwidth?

A) Persistent Connections
B) Server Push
C) Header Compression (HPACK)
D) Independent Streams

---

Correct ✅
**HTTP/2** ka **Header Compression (HPACK)** feature headers ka size reduce karta hai aur bandwidth save karta hai, especially frequent API calls ke liye.

---

**Question 10:**

Why is HTTP/0.9 considered very limited for modern web interactions?

A) It supports multiplexing of requests
B) It uses QUIC instead of TCP
C) It only supports single line GET requests with no headers or status codes
D) It allows server push

----

Correct ✅
**HTTP/0.9** sirf **single line GET requests** support karta tha, aur **na headers na status codes**, is liye ye modern web interactions ke liye bohot limited tha.

---









