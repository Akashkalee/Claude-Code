# CLAUDE CODE WORKING
<img width="580" height="580" alt="claude" src="https://github.com/user-attachments/assets/e41f05f0-7e59-4d07-a215-27be0efb1c8f" />

Claude Code is Anthropic's agentic coding tool that runs in your terminal. Here's how it works:

### What it is
A command-line interface (CLI) that lets you interact with Claude directly from your development environment, with full access to your codebase.

### How it works
  - Direct codebase access — Claude Code can read, write, and navigate your actual files. You don't need to copy-paste code; it understands your project structure natively.
  - Agentic execution — It can take multi-step actions autonomously: reading files, running shell commands, editing code, running tests, and iterating based on results — all in sequence without you prompting each step.
  - Terminal-native — It runs where developers already work, so it integrates naturally into existing workflows without needing a separate IDE or UI.

### What you can ask it to do:

  - Understand and explain an unfamiliar codebase
  - Write new features end-to-end
  - Fix bugs (including running the code to verify the fix)
  - Write and run tests
  - Refactor existing code
  - Handle git operations (commits, PRs, etc.)

#### Tool use under the hood — Claude Code uses tools like file read/write, bash execution, and search to act on your behalf. It shows you what it's doing and asks for confirmation on potentially impactful actions.
#### MCP support — It supports Model Context Protocol (MCP) servers, so you can extend it with integrations like GitHub, databases, or custom tools.
#

## What is CLAUDE.md?
CLAUDE.md is a markdown file that Claude automatically reads at the start of each session. It holds project-specific instructions you'd otherwise repeat in every prompt — structure, conventions, workflows, style — loaded before every conversation. Builder.io
Your CLAUDE.md file becomes part of Claude's system prompt. Every conversation starts with this context already loaded, eliminating the need to explain basic project information repeatedly. Claude

### Where to put it?
You can place it in multiple locations: the project root (most common — commit it to version control so your team shares the same context), .claude/CLAUDE.md (if you prefer config in a subdirectory), or ~/.claude/CLAUDE.md (user-level defaults that apply to all your projects). For personal preferences that shouldn't be version controlled, use CLAUDE.local.md and add it to .gitignore. The filename is case-sensitive — it must be exactly CLAUDE.md.

### How Claude discovers and prioritizes files
Claude discovers memory files by traversing from your current directory up to the filesystem root. Files closer to your current directory have higher priority (they are loaded later, so the model pays more attention to them). Files are loaded in this order: global admin policy files → your personal global instructions → project-level CLAUDE.md files from root down to your current directory. Mintlify
CLAUDE.md files can be hierarchical — you can have one project-level and one in nested directories. It looks at them all and prioritizes the most specific, the most nested when relevant. 

### What to include
Write instructions that would cause mistakes if missing. Everything else is noise. Include: exact build, test, and lint commands; architecture decisions that affect how code should be written; coding conventions specific to your project; environment setup requirements; common pitfalls to avoid; and monorepo structure. Omit things Claude already knows, like standard library APIs or obvious reminders like "write clean code." Mintlify
Think in three dimensions — WHAT (your tech stack and project structure), WHY (the purpose of different parts of the project), and HOW (how Claude should actually work on the project — e.g., do you use bun instead of node? How can it run tests, typechecks, and compilation steps?). 

### Advanced features
@ includes — You can reference external files inside CLAUDE.md using @ syntax, like @./docs/architecture.md or @~/shared/style-guide.md. External includes require explicit approval the first time they are loaded. 
Path-scoped rules — Files in .claude/rules/ can use YAML frontmatter to restrict which file paths they apply to, letting you load rules conditionally based on the file Claude is working with. 
Excluding files — If you want to prevent Claude from loading certain CLAUDE.md files (e.g., in vendored dependencies or generated code), you can add exclusion patterns to your settings using claudeMdExcludes. 

### Auto-generating with /init
Claude examines your codebase — reading package files, existing documentation, configuration files, and code structure — then generates a CLAUDE.md tailored to your project. The generated file typically includes build commands, test instructions, key directories, and coding conventions it detected. Think of /init as a starting point, not a finished product. 

### Best practices
Every token in your CLAUDE.md uses context window space. A file that runs over 2,000 tokens starts eating into the space Claude needs for actual work. If you have extensive technical documentation, reference external files rather than inlining everything. 
Keep task-specific instructions out of the root CLAUDE.md — for example, avoid including instructions about how to structure a new database schema if that won't matter most of the time. General consensus is that under 300 lines is best, and shorter is even better. 
Don't include sensitive information, API keys, credentials, or database connection strings — especially if you commit to version control. Since CLAUDE.md becomes part of Claude's system prompt, treat it as documentation that could be shared publicly.
