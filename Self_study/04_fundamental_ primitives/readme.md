***MCP is not just about enhancing desktop applications with agentic functionality. It's about exposing reusable tools and resources to build agentic microservices.***

**“MCP ka matlab ye hai ke pehle jo tools ka sara load tumhare server par hota tha, ab woh MCP server sambhal leta hai. Is se tumhe har project ke liye alag-alag integration code likhne ki zarurat nahi padti.”**

This module introduces the three fundamental primitives of MCP: Tools, Resources, and Prompts.



## **Core Competencies**

* ✅ Build MCP servers using the Python SDK with decorator-based tool definitions
* ✅ Implement all three MCP primitives: Tools (model-controlled), Resources (app-controlled), Prompts (user-controlled)
* ✅ Create MCP clients that connect to and interact with servers
* ✅ Use the MCP Server Inspector for testing and debugging server functionality


## **Technical Skills**

* ✅ Define tools with decorators instead of writing JSON schemas manually
* ✅ Implement file management functionality with tools for reading, writing, and managing files
* ✅ Create resources for exposing read-only data with proper MIME type handling
* ✅ Build prompts that provide pre-crafted instructions for common workflows
* ✅ Handle errors gracefully with proper exception handling and user feedback

## **Understanding**

* ✅ Distinguish between MCP primitives: Know when to use tools vs. resources vs. prompts
* ✅ Understand control models: Model-controlled (tools), app-controlled (resources), user-controlled (prompts)
* ✅ Apply best practices for security, performance, and maintainability

---

# **MCP Core Primitives**
## **1. Tools (Model-Controlled)**
Tools are functions that AI models can call to perform actions. They are:

* Model-controlled: The AI decides when and how to use them
* Action-oriented: Perform specific tasks like reading files, making API calls
* Decorator-based: Defined using Python decorators with type hints

## **2. Resources (App-Controlled)**
Resources provide read-only access to data. They are:

* App-controlled: The application decides when to expose them
* Data-focused: Provide access to documents, databases, APIs
* URI-based: Accessed through specific URIs with optional parameters

## **3. Prompts (User-Controlled)**

Prompts are pre-crafted instructions for common workflows. They are:

* User-controlled: Users decide when to apply them
* Instruction-focused: Provide high-quality, reusable prompts
* Context-aware: Can include dynamic content and formatting