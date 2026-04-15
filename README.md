# Claude-Code

![1_qH8_TGEkrrvQ0HrFdhp55g](https://github.com/user-attachments/assets/5d477f25-9c7d-409d-abed-17c43dbaf2a3)

### Intro to Cluade
Claude is a highly performant, trustworthy, and intelligent AI platform built by Anthropic. Claude excels at tasks involving language, reasoning, analysis, coding, and more.

### Claude Code overview
Claude Code is an agentic coding tool that reads your codebase, edits files, runs commands, and integrates with your development tools. Available in your terminal, IDE, desktop app, and browser.

Claude Code is an AI-powered coding assistant that helps you build features, fix bugs, and automate development tasks. It understands your entire codebase and can work across multiple files and tools to get things done.

### What you can do
Here are some of the ways you can use claude code:
- Automate the work you keep putting off
- Build features and fix bugs
- Create commits and pull requests
- Connect your tools with MCP
- Customize with Instructions, skills, hooks
- Run agent teams and build custom agents
- Pipe, script, and automate with CLI
- Schedule recurring tasks
- Work from anywhere


### Reference
## CLI Reference
Complete reference for Claude Code command-line inference, including commands and flags.

### CLI commands
You can start sessions, pipe content, resume conversations, and manage updates with these commands:

Command	Description	Example

| Command | Description | Example |
| --- | --- | --- |
| `claude` | Start interactive session | `claude` |
| `claude "query"` | Start interactive session with initial prompt | `claude "explain this project"` |
| `claude -p "query"` | Query via SDK, then exit | `claude -p "explain this function"` |
| `cat file \| claude -p "query"` | Process piped content | `cat log.txt \| claude -p "explain"` |
| `claude -c `| Continue most recent conversation in current directory | `claude -c` |
| `claude -c -p "query"` | Continue via SDK | `claude -c -p "Check for type errors"` |
|`claude -r "<session>" "query"` | Resume session by ID or name | `claude -r "auth refactor" "Finish this PR"` |
| `claude update` | Update to latest version | `claude update` |
| `claude auth logout` | Sign in to your Anthropic account. Use `--email` to pre-fill your email address, `--sso` to force SSO authentication, and `--console` to sign in with Anthropic Console for API usage billing instead of a Claude subscription | `claude auth login --console` |
| `claude auth logout` | Log out from your Anthropic account | `claude auth logout` |
| `claude auth status` | Show authentication session as JSON. Use `--text` for human-readable output. Exits with code 0 if logged in, 1 if not | `claude auth status` |
| `claude agents` | List all configured subagents, grouped by source | `claude agents` |
| `claude auto-mode defaults` | Print the built-in auto mode classifier rules as JSON. Use claude auto-mode config to see your effective config with settings applied | `claude auto-mode defaults > rules.json` |
| `claude mcp` | Configure Model Context Protocol (MCP) servers | `claude mcp add --transport http asana https://mcp.asana.com/v2/mcp` |
| `claude plugin` | Manage Claude Code plugins. Alias: claude plugins. See plugin reference for subcommands | `claude plugin install code-review@claude-plugins-official ` |
| claude remote-control | Start a Remote Control server to control Claude Code from Claude.ai or the Claude app. Runs in server mode (no local interactive session). See Server mode flags | `claude remote-control --name "My Project"` |
| claude setup-token | Generate a long-lived OAuth token for CI and scripts. Prints the token to the terminal without saving it. Requires a Claude subscription. See Generate a long-lived token  |`claude setup-token`  |


### CLI Flags
Customize claude code behavior with these command-line flags. claude --help does not list every flag, so a flag's absence from --help does not mean it is unavailable.

| `--add-dir ` | Add additional working directores for Claude to read and edit files. Grants file access; most `.claude/` configuration is not discovered from these directories. Validates each path exists as a directory | `claude -add-dir ../apps ../lib` |
| `--agent` | Speacify an agent for the current session (overrides the agent setting | `claude --agent my-custom agent` |
| `--agents` | Define custom subagents dynamically via JSON. Uses the same field names as subagent frontmatter, plus a prompt field for the agent's instructions | `claude --agnets '{"reviewer": {"description":"Reviews code", "prompt":"You are a code reviewer"}}' ` |
| `--allow-dangerously-skip-permissions` | Add `bypassPermissions` to the `Shift+Tab` mode cycle without starting in it. Lets you begin in a different mode like `plan` and switch to bypassPermissions later.  | `claude --permission-mode plan --allow-dangerously-skip-permissions` |
| `--allowedTools` | Tools that execute without prompting for permission. See permission rule syntax for pattern matching. To restrict which tools are available, use --tools instead | `"Bash(git log *)" "Bash(git diff *)" "Read" ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
| ` ` |   | `claude ` |
