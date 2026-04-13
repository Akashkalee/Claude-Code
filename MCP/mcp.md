# MCP - MODEL CONTEXT PROTOCOL
[MCP official documentation](https://modelcontextprotocol.io/docs/getting-started/intro)
[GitHub](https://github.com/modelcontextprotocol)

## What is the Model Context Portocol (MCP)?
<img width="826" height="431" alt="image" src="https://github.com/user-attachments/assets/1a4db2d4-eb84-4e09-877e-56b1afc4444c" />

What is MCP?
Model Context Protocol (MCP) is an open-source standardized protocol developed by Anthropic that enables AI models (like Claude) to safely access external tools, data sources, and services. Think of it as a universal adapter that allows Claude to connect to thousands of applications without needing custom integrations for each one.
The Problem MCP Solves
Before MCP, if you wanted Claude to interact with external services (like Asana, Gmail, databases), you'd need:

Custom code for each integration
Complex security handling
Difficulty scaling to many services
No standardization

MCP solves this with a single, unified protocol.
Core Architecture
MCP uses a client-server model:

Client: Claude or your application (e.g., Claude.ai, Claude API in your app)
Server: The MCP server that wraps an external service (Gmail, Asana, custom APIs)
Protocol: JSON-RPC (standardized message format) over secure transports

The communication flows through secure channels using stdio (for local apps), HTTP, or WebSocket (for remote services).
