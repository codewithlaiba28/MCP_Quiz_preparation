1. **What are the three core primitives defined by MCP?**
   A) Tools, Memory, Interfaces
   B) Tools, Resources, Prompts
   C) Resources, Memory, Prompts
   D) Interfaces, Connectors, Tools
   **Correct Answer:** B

2. **In MCP architecture, what role does a “Tool” primitive serve?**
   A) A read-only data source the model uses
   B) A predefined prompt template
   C) An executable function the AI can call
   D) A user interface component
   **Correct Answer:** C

3. **What is a “Resource” primitive in MCP?**
   A) A template that guides model behaviour
   B) A service that executes actions for the model
   C) A data source or document the model can read
   D) A user-interface widget for the model
   **Correct Answer:** C

4. **What is a “Prompt” primitive in MCP?**
   A) A function that triggers external APIs
   B) A structured template or instruction for the model
   C) A file system resource the model reads
   D) A transport protocol between client and server
   **Correct Answer:** B

5. **Which problem does MCP aim to solve in AI system integration?**
   A) Lack of large language models
   B) The “N × M” integrations problem (many clients × many services)
   C) Too many prompt engineering frameworks
   D) Inability of models to generate code
   **Correct Answer:** B

6. **Which of the following is part of the MCP lifecycle initialization phase?**
   A) Client sends normal requests before server responds
   B) Server sends capabilities only after initialized notification
   C) Server starts tools without client request
   D) Client and server never exchange versions
   **Correct Answer:** B

7. **In MCP transport layers, what are typical transport mechanisms?**
   A) FTP and SMTP
   B) STDIO (for local) and HTTP + SSE (for remote)
   C) WebSockets only
   D) Proprietary binary protocols only
   **Correct Answer:** B

8. **Which statement correctly describes the “Tools” primitive control hierarchy?**
   A) Tools are user-controlled
   B) Tools are application-controlled
   C) Tools are model-controlled
   D) Tools are system-controlled
   **Correct Answer:** C

9. **Why is MCP considered more scalable than custom integrations for each AI app and service?**
   A) Because it uses more servers than before
   B) Because it reduces M×N integrations to M + N integrations
   C) Because it replaces all integrations with one monolithic API
   D) Because it eliminates the need for data security
   **Correct Answer:** B

10. **Which of the following is NOT a primitive in MCP?**
    A) Tools
    B) Resources
    C) Prompts
    D) Workflows
    **Correct Answer:** D

11. **What kind of data format or protocol does MCP often use for communication?**
    A) SOAP
    B) XML-RPC
    C) JSON-RPC 2.0
    D) Binary TCP without metadata
    **Correct Answer:** C

12. **In a typical MCP setup, who acts as the “Host/Client” and who as the “Server”?**
    A) Host = data source, Server = AI application
    B) Host = AI application (client), Server = MCP server providing tools/resources
    C) Host = user, Server = model
    D) Host = prompt template, Server = resource
    **Correct Answer:** B

13. **What benefit does the “Resource” primitive give to a language model agent?**
    A) Allows the model to execute system commands
    B) Provides structured read-only context (e.g., file contents) for the model
    C) Lets the model define UI elements
    D) Enables the model to manage authentication tokens
    **Correct Answer:** B

14. **Which of the following best describes a “Prompt” primitive’s purpose?**
    A) To execute code on behalf of the model
    B) To provide a reusable template guiding model behaviour
    C) To store large files for the model to read
    D) To transport messages between client and server
    **Correct Answer:** B

15. **Which one of these is a valid reason for adopting MCP in enterprise AI systems?**
    A) To decentralize all models and avoid integration
    B) To unify how AI agents access tools, resources, and prompts through a standard interface
    C) To ensure each AI application builds its own unique connectors
    D) To eliminate the need for any server architecture
    **Correct Answer:** B

---
