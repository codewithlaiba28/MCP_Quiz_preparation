Project Context Discovery with MCP Roots
Roots ek tareeqa hain jo MCP servers ko aapke local machine ke specific files aur folders tak access dene ke liye use hota hai. Inhein aise samjho jaise ek permission system jo kehta hai, "Hey, MCP server, tum in files ko access kar sakte ho" – lekin ye sirf permission dene se zyada kaam karte hain.

**The Problem**
Development tools ko aksar ye samajhna padta hai ke project ka structure kaisa hai:

* Konsi files project ki hain?
* Source files kahan located hain?
* Project ki boundaries kya hain?

Traditionally, iske liye manual configuration required hoti thi:

```python
project_dir = "/path/to/project"  # Hardcoded ya configured
analyze_code(f"{project_dir}/src/main.py")
```

Agar roots na hon, to aap ek common issue face karte. Socho ke aapke paas ek MCP server hai jisme video conversion tool hai jo ek file path leta hai aur MP4 ko MOV format me convert karta hai.

Jab user Claude se kehta hai "biking.mp4 ko mov format me convert karo", to Claude tool ko sirf filename ke saath call karega. Lekin problem ye hai ke Claude ke paas aapke poore file system me search karne ka tareeqa nahi hai ke woh file actually kahan hai.

Aapka file system complex ho sakta hai aur files alag-alag directories me scattered ho sakti hain. User ko pata hai ke biking.mp4 file unke Movies folder me hai, lekin Claude ke paas ye context nahi hai.

Aap is problem ko solve kar sakte ho ke users se hamesha full paths maang lo, lekin ye user-friendly nahi hai. Koi bhi har baar complete file path type karna nahi chahta.



**The Solution: MCP Roots**
MCP Roots automatic project context discovery provide karta hai:

* Clients (IDEs, editors) project directories expose karte hain
* Servers (tools, analyzers) access request karte hain jab zarurat ho
* Koi manual configuration required nahi

```python
# Server bas roots request karta hai aur project context le leta hai
roots = await ctx.session.list_roots()
project_files = roots.roots[0].list_files("**/*.py")
```

**Roots in Action**
Roots ke saath workflow is tarah change hota hai:

1. User kehta hai ke video file convert karo
2. Agent `list_roots` call karta hai taake dekhe kaunse directories access ho sakti hain
3. Agent accessible directories pe `read_dir` call karta hai file find karne ke liye
4. File milte hi, Agent conversion tool ko full path ke saath call karta hai

Ye automatically hota hai – users ab bhi sirf "convert biking.mp4" keh sakte hain bina full paths provide kiye.

🛠️ **Implementation**

**Client Side**
Client ko ye karna hota hai:

* Roots capability implement karna
* Roots/list requests handle karna
* Project directory information provide karna

`client.py` me basic implementation dekh sakte ho.

**Server Side**
Server ye kar sakta hai:

* Client se project roots request karna
* Roots use karke project structure analyze karna
* Project context me files ke saath kaam karna

`server.py` me basic implementation dekh sakte ho.

🔍 **Key Concepts**

1. **Project Roots**
   Definition: Directories jo project ki boundaries form karte hain
   Examples:

* Workspace folders in VS Code
* Project directories in PyCharm
* Git repository root directories

2. **URI Representation**

```json
# Example root structure
{
    "uri": "file:///home/user/projects/myapp",
    "name": "MyApp Project"
}
```

3. **Client-Server Flow**

💻 **Hands-On Implementation**

**Step 1: Setup Project**

```bash
cd mcp_code
uv sync
```

**Step 2: Run the Demo**

**Terminal 1:**

```bash
uv run uvicorn server:mcp_app --reload
```

**Terminal 2:**

```bash
uv run python client.py
```

**Step 3: Observe the Output**
Aap dekho ge:

* Client initialization with roots capability
* Server requesting project roots
* Project analysis results showing:

  * File counts by type
  * Project features detection
  * Basic structure analysis

📚 **Further Reading**

* MCP Roots Specification
* Project Context in Development Tools
* Best Practices for Root Handling

Yaad rakho: MCP roots ki power ye hai ke tools automatically project context samajh kar kaam kar sakte hain, jis se development zyada efficient aur context-aware ban jati hai.
