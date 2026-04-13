# MCP - MODEL CONTEXT PROTOCOL
[MCP official documentation](https://modelcontextprotocol.io/docs/getting-started/intro)
[GitHub](https://github.com/modelcontextprotocol)

## What is the Model Context Portocol (MCP)?
<img width="826" height="431" alt="image" src="https://github.com/user-attachments/assets/1a4db2d4-eb84-4e09-877e-56b1afc4444c" />

## What is MCP?
Model Context Protocol (MCP) is an open-source standardized protocol developed by Anthropic that enables AI models (like Claude) to safely access external tools, data sources, and services. Think of it as a universal adapter that allows Claude to connect to thousands of applications without needing custom integrations for each one.

### The Problem MCP Solves
Before MCP, if you wanted Claude to interact with external services (like Asana, Gmail, databases), you'd need:
 - Custom code for each integration
 - Complex security handling
 - Difficulty scaling to many services
 - No standardization
MCP solves this with a single, unified protocol.

## Core Architecture

MCP uses a client-server model:

 - Client: Claude or your application (e.g., Claude.ai, Claude API in your app)
 - Server: The MCP server that wraps an external service (Gmail, Asana, custom APIs)
 - Protocol: JSON-RPC (standardized message format) over secure transports
The communication flows through secure channels using stdio (for local apps), HTTP, or WebSocket (for remote services).

## Key Components
1. Resources
Resources are pieces of data that servers expose — files, documents, database records, API responses. Instead of Claude requesting random data, resources are explicitly listed and sampled on demand. This makes the protocol efficient and safe because:

 - Only needed data is transferred
 - Clear boundaries on what's accessible
 - Servers can enforce permissions
Example: Gmail server exposes resources like gmail://messages/123, gmail://labels/INBOX

2. Tools
Tools are functions Claude can call to perform actions. They're like API endpoints but declared explicitly with:

 - Function name and description
 - Required parameters
 - Expected output format
Example: An Asana tool might be create_task(project_id, title, description) or update_task_status(task_id, status)

3. Prompts
Prompts are reusable instruction templates that servers provide to help Claude work effectively with their data. Instead of Claude guessing how to use a tool, servers can say: "Here's how to write a good task title" or "Here's the context you need to answer questions about our database."

4. Sampling
A key MCP concept: instead of Claude saying "give me everything", the client samples specific resources on demand. It's like saying "I need the email subject and sender, but not the full body" — much more efficient than transferring entire files.

## How It Actually Works
Let's say you ask Claude: "What are my top priority tasks in Asana?"

-- Recognition: Claude sees you mentioned Asana and recognizes it needs to fetch task data
Tool Discovery: Claude queries the MCP server: "What tools do you have?" → Gets back the list (read tasks, create task, update status, etc.)
Tool Invocation: Claude calls the tool with parameters: get_tasks(filter: "priority=high")
Server Processing: The Asana MCP server authenticates, queries the Asana API, and returns matching tasks
Result Sampling: The server sends back task names, due dates, priority levels (only what's needed)
Claude Processes: Claude reads the results and creates a human-friendly response
Response: You get "You have 3 high-priority tasks: Design system review (due tomorrow), Client presentation (due Friday)..."

## Key Benefits
### Security:

Tools and resources are explicitly declared — no surprise access
Servers control exactly what Claude can see/do
Authentication happens server-side

### Scalability:

One protocol works with infinite services
Easy to add new integrations without changing Claude
Servers can be updated independently

### Efficiency:

Only necessary data is transferred
Resource sampling avoids bloated payloads
Clear API contracts prevent errors

### Developer-Friendly:

Open standard, not vendor-locked
Works with any language/framework
Can run locally or remotely

#### Real-World MCP Servers
You can currently connect Claude to:

 - Productivity: Asana, Gmail, Slack, Google Calendar
 - Development: GitHub, GitLab, Linear (issue tracking)
 - Data: Custom databases, file systems, APIs
 - Knowledge: Internal documentation, spreadsheets
 - Custom: Build your own MCP server for proprietary systems


MCP vs. Other Approaches
| Aspect |	Traditional API |	Simple Webhooks |	MCP |
| Standardized?	| No (each API different) |	No	| ✅ Yes |
| Bidirectional? |	✅ Yes	| No (one-way) |	✅ Yes |
| Safe sampling? |	Not built-in |	No |	✅ Yes |
| Easy to add tools?	| Complex	| Limited |	✅ Simple |
| Works offline? |	No	| No | ✅ Yes (stdio) |

### The Future
MCP is designed to be composable and extensible. As more services integrate MCP servers, Claude becomes increasingly capable without requiring updates. The protocol handles:

 - Authentication and permissions
 - Rate limiting
 - Error handling
 - Resource versioning
 - Context management

This means Claude can seamlessly access your entire tool ecosystem with a single, unified interface.
### In short:
MCP is the plumbing that lets Claude safely and efficiently connect to any external tool or data source, with clear boundaries, explicit permissions, and standardized communication. It's what makes "Claude in Claude" and AI-powered integrations possible.



