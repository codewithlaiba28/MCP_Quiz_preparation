#### 1. What does HTTP stand for?
   A) HyperText Transfer Protocol  
   B) High-Tech Transmission Protocol  
   C) Hyperlink Text Transport Protocol  
   D) Host Transfer Text Protocol  
   **Correct: A**

#### 2. Which HTTP method is idempotent and used to retrieve data without modifying resources?
   A) POST  
   B) GET  
   C) PUT  
   D) DELETE  
   **Correct: B**

#### 3. In HTTP, what is the purpose of the "Content-Type" header?
   A) To specify the authentication credentials  
   B) To indicate the media type of the resource or body  
   C) To control caching behavior  
   D) To set the request timeout  
   **Correct: B**

#### 4. Which HTTP status code indicates "Not Found"?
   A) 200  
   B) 404  
   C) 500  
   D) 301  
   **Correct: B**

#### 5. What is the default port number for HTTP?
   A) 80  
   B) 443  
   C) 8080  
   D) 21  
   **Correct: A**

#### 6. Which HTTP method is typically used to update an existing resource?
   A) GET  
   B) POST  
   C) PUT  
   D) HEAD  
   **Correct: C**

#### 7. In an HTTP request, what follows the request line?
   A) Response body  
   B) Headers  
   C) Status code  
   D) Cookies only  
   **Correct: B**

#### 8. HTTP/1.1 introduced which key feature for improving performance over HTTP/1.0?
   A) Persistent connections (keep-alive)  
   B) Binary framing  
   C) Server push  
   D) QUIC transport  
   **Correct: A**

#### 9. Which status code family (2xx) indicates a successful response?
   A) Client errors  
   B) Server errors  
   C) Redirection  
   D) Success  
   **Correct: D**

#### 10. What does the "Authorization" header typically contain?
    A) User credentials for access control  
    B) MIME type of the payload  
    C) Cache expiration time  
    D) Redirect URL  
    **Correct: A**

#### 11. Which HTTP method should not have a request body?
    A) POST  
    B) PUT  
    C) GET  
    D) PATCH  
    **Correct: C**

#### 12. What is the role of the "Host" header in HTTP/1.1?
    A) To specify the target server's domain name  
    B) To set the content length  
    C) To enable compression  
    D) To track user sessions  
    **Correct: A**

#### 13. Which status code means "Internal Server Error"?
    A) 400  
    B) 401  
    C) 500  
    D) 403  
    **Correct: C**

#### 14. In RESTful APIs, which method is commonly used for creating new resources?
    A) GET  
    B) POST  
    C) DELETE  
    D) OPTIONS  
    **Correct: B**

#### 15. What is the purpose of the "Set-Cookie" response header?
    A) To request a cookie from the client  
    B) To instruct the client to store a cookie  
    C) To delete existing cookies  
    D) To encode cookie data  
    **Correct: B**

#### 16. Which HTTP version introduced multiplexing and header compression?
    A) HTTP/1.0  
    B) HTTP/1.1  
    C) HTTP/2  
    D) HTTP/3  
    **Correct: C**

#### 17. What does a 301 status code signify?
    A) Moved Permanently  
    B) Bad Request  
    C) Unauthorized  
    D) Forbidden  
    **Correct: A**

#### 18. In HTTP requests, what is the "User-Agent" header used for?
    A) Identifying the client's software or browser  
    B) Specifying the desired response format  
    C) Handling cross-origin requests  
    D) Compressing the response  
    **Correct: A**

#### 19. Which method retrieves metadata about a resource without the body?
    A) GET  
    B) POST  
    C) HEAD  
    D) TRACE  
    **Correct: C**

#### 20. What is the structure of an HTTP response? (Order: Status Line, ___, Body)
    A) Headers  
    B) Request Method  
    C) URL Path  
    D) Query Parameters  
    **Correct: A**



1. **Which transport formats does MCP support?**  
   A. SOAP + XML  
   B. JSON-RPC 2.0 over stdio or HTTP  
   C. GraphQL  
   D. Protobuf  
   **✔ Correct Answer: B**

2. **What is the primary role of MCP?**  
   A. Connecting agents to each other  
   B. Connecting models/agents to external tools and data sources  
   C. Replacing HTTP  
   D. Managing user interfaces  
   **✔ Correct Answer: B**

3. **Who exposes tools/resources in MCP?**  
   A. Client  
   B. Server  
   C. Browser  
   D. Database  
   **✔ Correct Answer: B**

4. **What is the MCP client?**  
   A. A data store  
   B. The AI model/application that sends requests  
   C. A file system  
   D. A command-line tool only  
   **✔ Correct Answer: B**

5. **Which protocol is used for agent-to-agent communication?**  
   A. MCP  
   B. A2A  
   C. FTP  
   D. SMTP  
   **✔ Correct Answer: B**

6. **MCP avoids M×N integrations.**  
   A. True  
   B. False  
   **✔ Correct Answer: A**

7. **Which is NOT a use-case of MCP?**  
   A. Database access  
   B. File reading/writing  
   C. Agent-to-agent messaging  
   D. Tool execution  
   **✔ Correct Answer: C**

8. **Which message format does MCP use?**  
   A. SOAP  
   B. JSON-RPC 2.0  
   C. RSS  
   D. GraphQL  
   **✔ Correct Answer: B**

9. **Which are valid transport methods for MCP?**  
   A. stdio  
   B. HTTP  
   C. SSE  
   D. All of the above  
   **✔ Correct Answer: D**

10. **Why is MCP security important?**  
    A. Tools can perform sensitive operations and access data  
    B. There is no risk  
    C. MCP enforces encryption automatically  
    D. MCP only works offline  
    **✔ Correct Answer: A**

11. **What is the main advantage of MCP?**  
    A. Removes the need for custom tool integrations  
    B. Increases vendor lock-in  
    C. Creates more complexity  
    D. Only works in Python  
    **✔ Correct Answer: A**

12. **What is the relationship between MCP and A2A?**  
    A. MCP = tool access, A2A = agent communication  
    B. Both are the same  
    C. A2A replaces MCP  
    D. They are unrelated  
    **✔ Correct Answer: A**

13. **What does “endpoint discovery” mean?**  
    A. Searching on Google  
    B. Agents publishing their capabilities so others can find them  
    C. DNS lookups  
    D. Web crawling  
    **✔ Correct Answer: B**

14. **Which HTTP method retrieves data?**  
    A. POST  
    B. PUT  
    C. GET  
    D. DELETE  
    **✔ Correct Answer: C**

15. **Which status code means success?**  
    A. 404  
    B. 200  
    C. 500  
    D. 301  
    **✔ Correct Answer: B**

16. **Which method is used to send data (e.g., form submission)?**  
    A. GET  
    B. POST  
    C. TRACE  
    D. CONNECT  
    **✔ Correct Answer: B**

17. **Which header indicates the media type?**  
    A. Accept-Encoding  
    B. Server  
    C. User-Agent  
    D. Content-Type  
    **✔ Correct Answer: D**

18. **What is an advantage of MCP compared to traditional APIs?**  
    A. Standard interface  
    B. Runtime tool switching  
    C. Better interoperability  
    D. All of the above  
    **✔ Correct Answer: D**

19. **Which is NOT part of the layered architecture?**  
    A. Transport layer  
    B. Message format layer  
    C. Discovery layer  
    D. UI framework  
    **✔ Correct Answer: D**

20. **What is the best analogy for MCP?**  
    A. FTP  
    B. USB-C for AI tools  
    C. Email system  
    D. Browser engine  
    **✔ Correct Answer: B**



1. HTTP is fundamentally a __________ protocol.  
   A) Stateful  
   B) Connection-oriented  
   C) Stateless  
   D) Session-based  
   **Answer: C**

2. In the HTTP request-response cycle, who initiates the communication?  
   A) Server  
   B) Proxy  
   C) Client  
   D) Gateway  
   **Answer: C**

3. Which part of an HTTP message comes first?  
   A) Headers  
   B) Body  
   C) Start-line (Request/Status line)  
   D) CRLF  
   **Answer: C**

4. The first line of an HTTP request is called:  
   A) Status Line  
   B) Header Line  
   C) Request Line  
   D) Method Line  
   **Answer: C**

5. Which of the following is NOT a valid HTTP request method?  
   A) TRACE  
   B) CONNECT  
   C) UPDATE  
   D) OPTIONS  
   **Answer: C**

6. Which HTTP method is safe but NOT idempotent?  
   A) GET  
   B) POST  
   C) PUT  
   D) DELETE  
   **Answer: B**

7. A client sends the same DELETE request twice. The second request returns 404. This still proves the method is:  
   A) Not safe  
   B) Not idempotent  
   C) Idempotent  
   D) Cacheable  
   **Answer: C**

8. Which status code indicates that the request was successful and a new resource was created?  
   A) 200 OK  
   B) 201 Created  
   C) 202 Accepted  
   D) 204 No Content  
   **Answer: B**

9. Which of the following status codes belongs to the 3xx (Redirection) class?  
   A) 301  
   B) 401  
   C) 501  
   D) 201  
   **Answer: A**

10. What does the status code 204 No Content mean?  
    A) Request failed  
    B) Success, but no response body is sent  
    C) Resource moved permanently  
    D) Server error  
    **Answer: B**

11. In HTTP, the server forgets everything about the client after sending the response because HTTP is:  
    A) Connectionless  
    B) Persistent  
    C) Stateless  
    D) Encrypted  
    **Answer: C**

12. Which header must be present in HTTP/1.1 requests?  
    A) User-Agent  
    B) Content-Length  
    C) Host  
    D) Accept-Encoding  
    **Answer: C**

13. Which header tells the server what media types the client can handle?  
    A) Content-Type  
    B) Accept  
    C) Authorization  
    D) Cache-Control  
    **Answer: B**

14. The "Content-Type" header in a response with value "application/json" describes:  
    A) The type of data in the request body  
    B) The type of data in the response body  
    C) The client’s preferred language  
    D) Authentication method  
    **Answer: B**

15. Which method is used to check what HTTP methods a server supports on a resource?  
    A) HEAD  
    B) OPTIONS  
    C) TRACE  
    D) GET  
    **Answer: B**

16. What is the correct order of an HTTP response message?  
    A) Headers → Status Line → Body  
    B) Body → Status Line → Headers  
    C) Status Line → Headers → Body  
    D) Status Line → Body → Headers  
    **Answer: C**

17. Which status code means the client needs to authenticate itself?  
    A) 401 Unauthorized  
    B) 403 Forbidden  
    C) 407 Proxy Authentication Required  
    D) 411 Length Required  
    **Answer: A**

18. An HTTP request contains sensitive data in the URL query string. Which method should NOT be used?  
    A) POST  
    B) GET  
    C) PUT  
    D) PATCH  
    **Answer: B** (because query strings are logged)

19. Which of these is a valid example of a Request Line?  
    A) HTTP/1.1 200 OK  
    B) GET /api/users HTTP/1.1  
    C) Content-Type: application/json  
    D) Host: example.com  
    **Answer: B**

20. Even though HTTP is stateless, applications can maintain user state using:  
    A) Persistent connections  
    B) Cookies and sessions  
    C) Server-side caching  
    D) HTTP/2 multiplexing  
    **Answer: B**




# **🔑 Default HTTP Method: GET**

```
┌────────────┐       HTTP Request        ┌───────────────┐
│  Browser   │ ───────────────────────▶ │    Server     │
│ (Client)   │                          │ (example.com) │
└────────────┘                          └───────────────┘
     ▲                                        │
     │       HTTP Response (HTML Page)        ▼
┌────────────┐ ◀────────────────────── ┌───────────────┐
│  You see   │                          │    Sends:     │
│ "Hello 🌍" │                          │   200 OK      │
└────────────┘                          │ HTML Page     │
                                       └───────────────┘
```

## **Key Takeaway**
* HTTP is a conversation between a browser (client) and a website (server).
* You send a request (asking for a page or data), and the server sends a response (content or error).
* This happens every time you load any website.































