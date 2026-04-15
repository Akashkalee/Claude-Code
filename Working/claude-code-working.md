# CLAUDE CODE WORKING
<img width="580" height="580" alt="claude" src="https://github.com/user-attachments/assets/e41f05f0-7e59-4d07-a215-27be0efb1c8f" />

Claude Code is Anthropic's agentic coding tool that runs in your terminal. Here's how it works:
What it is
A command-line interface (CLI) that lets you interact with Claude directly from your development environment, with full access to your codebase.
How it works
Direct codebase access — Claude Code can read, write, and navigate your actual files. You don't need to copy-paste code; it understands your project structure natively.
Agentic execution — It can take multi-step actions autonomously: reading files, running shell commands, editing code, running tests, and iterating based on results — all in sequence without you prompting each step.
Terminal-native — It runs where developers already work, so it integrates naturally into existing workflows without needing a separate IDE or UI.
What you can ask it to do:

Understand and explain an unfamiliar codebase
Write new features end-to-end
Fix bugs (including running the code to verify the fix)
Write and run tests
Refactor existing code
Handle git operations (commits, PRs, etc.)

Tool use under the hood — Claude Code uses tools like file read/write, bash execution, and search to act on your behalf. It shows you what it's doing and asks for confirmation on potentially impactful actions.
MCP support — It supports Model Context Protocol (MCP) servers, so you can extend it with integrations like GitHub, databases, or custom tools.
