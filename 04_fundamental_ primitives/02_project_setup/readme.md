# Project Setup

Chaliye baseline project setup karte hain jo hum MCP module ke fundamentals complete karne ke liye use karenge. Ye 3 different flavours mein implement hua hai aur hum `agents_sdk_cli_project` ko apna baseline project use karenge.

## MCP Chat - Agents SDK CLI project

MCP Chat ek command-line interface (CLI) application hai. Ye application document retrieval, command-based prompts, aur MCP (Model Control Protocol) architecture ke zariye extensible tool integrations support karta hai.

## Prerequisites

* Python 3.9+
* Kisi bhi Chat Completions LLM API Key aur Provider (jaise: Gemini)

## Setup

### Step 1: Environment variables configure karein

1. Project root mein `.env` file create ya edit karein aur verify karein ke ye variables sahi set hain:

```
LLM_API_KEY=""  # Apni GEMINI API secret key enter karein
LLM_CHAT_COMPLETION_URL="https://generativelanguage.googleapis.com/v1beta/openai/"
LLM_MODEL="gemini-2.0-flash"
```

### Step 2: Dependencies install karein

[uv](https://github.com/astral-sh/uv) ek fast Python package installer aur resolver hai.

1. Agar install nahi hai toh uv install karein:

```bash
pip install uv
```

2. Virtual environment create aur activate karein:

```bash
uv venv
source .venv/bin/activate  # Windows par: .venv\Scripts\activate
```

3. Dependencies install karein:

```bash
uv sync
```

4. MCP Server start karein:

```bash
uv run uvicorn mcp_server:mcp_app --reload
```

5. Project ChatAgent ke sath CLI mein run karein:

```bash
uv run main.py
```

6. Optional: Inspector start karein:

```bash
npx @modelcontextprotocol/inspector
```

## Usage

### Basic Interaction

Bas apna message type karein aur Enter press karein model se chat karne ke liye.

### Document Retrieval

@ symbol use karein followed by document ID taake document content query mein include ho jaye:

```
> Tell me about @deposition.md
```

### Commands

/MCP server mein defined commands execute karne ke liye / prefix use karein:

```
> /summarize deposition.md
```

Commands Tab press karne par auto-complete ho jayenge.

## Development

### New Documents Add Karna

`mcp_server.py` file edit karein aur `docs` dictionary mein naye documents add karein.

### MCP Features Implement Karna

MCP features ko fully implement karne ke liye:

1. `mcp_server.py` mein TODOs complete karein
2. `mcp_client.py` mein missing functionality implement karein

### Linting aur Typing Check

Koi lint ya type checks implement nahi hain.

