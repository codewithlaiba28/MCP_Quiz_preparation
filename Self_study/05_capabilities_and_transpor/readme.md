### **Advanced MCP Topics Quiz**

**1. What is the primary purpose of MCP transports?**
A) To store project files locally
B) To handle communication between AI clients and servers
C) To compile Python code
D) To monitor user activity
**Correct Answer:** B

**2. Which MCP transport allows session persistence across multiple HTTP requests?**
A) Stateless HTTP
B) Stateful HTTP
C) WebSocket
D) TCP only
**Correct Answer:** B

**3. What does “stateless HTTP transport” imply in MCP?**
A) Server maintains session context
B) Client context is never saved between requests
C) Files are automatically synced
D) Logging is disabled
**Correct Answer:** B

**4. In MCP, what is the role of “sampling”?**
A) Fetching project roots
B) Gradually streaming data from the server to client
C) Logging notifications
D) Encrypting communication
**Correct Answer:** B

**5. How do logging notifications benefit MCP clients?**
A) They provide real-time updates about server internal state
B) They improve file transfer speed
C) They store user credentials
D) They disable progress notifications
**Correct Answer:** A

**6. What is the function of MCP progress notifications?**
A) To send full project files
B) To track the state of long-running operations in real-time
C) To maintain client credentials
D) To change server transport type
**Correct Answer:** B

**7. MCP roots are primarily used for:**
A) Managing security and access to project directories
B) Streaming sampling data
C) Enabling logging notifications
D) Switching transport protocols
**Correct Answer:** A

**8. When using MCP roots, how does the server know which files belong to a project?**
A) By manually entering file paths
B) By requesting project roots from the client
C) By scanning all server directories
D) By using default system paths
**Correct Answer:** B

**9. Which MCP transport is best for long-lived, bidirectional communication?**
A) Stateless HTTP
B) TCP or WebSocket
C) FTP
D) SMTP
**Correct Answer:** B

**10. Why is using roots considered a security feature in MCP?**
A) They encrypt all data automatically
B) They restrict server access to only specific project directories
C) They prevent logging notifications
D) They speed up transport protocols
**Correct Answer:** B

**11. Which of the following is true about stateful HTTP in MCP?**
A) Each request is completely independent
B) The server can maintain context between requests
C) It does not support progress notifications
D) Roots are irrelevant
**Correct Answer:** B

**12. What happens during a sampling session in MCP?**
A) Full data is sent in one large batch
B) Partial data is streamed in increments to the client
C) Only metadata is transmitted
D) The client logs into the server
**Correct Answer:** B

**13. Which type of notification would inform a client about each stage of a long-running task?**
A) Logging notifications
B) Progress notifications
C) Sampling notifications
D) Roots notifications
**Correct Answer:** B

**14. How can stateless HTTP be advantageous for MCP?**
A) It reduces server memory usage by not storing client context
B) It guarantees faster sampling
C) It ensures real-time logging
D) It allows unlimited project roots
**Correct Answer:** A

**15. In MCP, which combination ensures secure, efficient project handling?**
A) Roots + Stateful HTTP + Logging notifications
B) Sampling + Stateless HTTP + Progress notifications
C) Roots + Logging + Progress notifications
D) TCP only
**Correct Answer:** C

---

