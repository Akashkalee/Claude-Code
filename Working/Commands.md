
## Commands
Complete reference for commands available in Claude Code, including built-in commands and bundled skills.

Commands control Claude Code from inside a session. They provide a quick way to switch models, manage permissions, clear context, run a workflow, and more.
Type / to see every command available to you, or type / followed by letters to filter.

The table below lists all the commands included in Claude Code. Entries marked Skill are bundled skills. They use the same mechanism as skills you write yourself: a prompt handed to Claude, which Claude can also invoke automatically when relevant. Everything else is a built-in command whose behavior is coded into the CLI. To add your own commands, see skills.

Not every command appears for every user. Availability depends on your platform, plan, and environment. For example, /desktop only shows on macOS and Windows, and /upgrade only shows on Pro and Max plans.

In the table below, <arg> indicates a required argument and [arg] indicates an optional one.

| Command | Purpose |
| --- | --- |
| `/add-dir <path>` | Add a working directory for file access during the current session. Most `.claude/` configuration is not discovered from the added directory |
