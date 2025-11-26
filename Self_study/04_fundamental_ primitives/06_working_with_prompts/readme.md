Build and use pre-crafted prompts for common workflows and AI interactions


## **Key Characteristics of Prompts**
* User-controlled: Users decide when to apply prompts
* Instruction-focused: Provide high-quality, reusable instructions
* Context-aware: Can include dynamic content and formatting
* Reusable: Can be applied across different scenarios
* Structured: Follow consistent patterns for effectiveness


## **How Prompts Work?**
Prompts define a set of user and assistant messages that clients can use. They should be high-quality, well-tested, and relevant to your MCP server's purpose. The workflow is:

* Write and evaluate a prompt relevant to your server's functionality
* Define the prompt in your MCP server using the @mcp.prompt decorator
* Clients can request the prompt at any time
* Arguments provided by the client become keyword arguments in your prompt function
* The function returns formatted messages ready for the AI model

This system creates reusable, parameterized prompts that maintain consistency while allowing customization through variables. It's particularly useful for complex workflows where you want to ensure the AI receives properly structured instructions every time


## **Core MCP Prompts Concepts**
* Prompt Discovery: Using prompts/list to find available templates
* Prompt Generation: Using prompts/get to create customized prompts
* Parameter Handling: Dynamic prompt customization with type validation
* 2025-06-18 Features: Title fields, enhanced metadata, and capabilities declaration