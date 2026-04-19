
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
| `/agents` | Manage agent configurations |
| `/autofix-pr [prompt]` | Spawn a Claude Code on the web session that watches the current branch’s PR and pushes fixes when CI fails or reviewers leave comments. Detects the open PR from your checked-out branch with `gh pr view`; to watch a different PR, check out its branch first. By default the remote session is told to fix every CI failure and review comment; pass a prompt to give it different instructions, for example `/autofix-pr only fix lint and type errors`. Requires the `gh` CLI and access to Claude Code on the web |
| `/batch <instruction>` | Orchestrate large-scale changes across a codebase in parallel. Researches the codebase, decomposes the work into 5 to 30 independent units, and presents a plan. Once approved, spawns one background agent per unit in an isolated git worktree. Each agent implements its unit, runs tests, and opens a pull request. |
| `/branch [name]` | Create a branch of the current conversation at this point. Switches you into the branch and preserves the original, which you can return to with /resume. Alias: /fork |
| `/btw <question>` | Ask a quick side question without adding to the conversation |
| `/chrome` | Configure Claude in Chrome settings |
| `/claude-api` | Load Claude API reference material for your project’s language (Python, TypeScript, Java, Go, Ruby, C#, PHP, or cURL) and Managed Agents reference. Covers tool use, streaming, batches, structured outputs, and common pitfalls. Also activates automatically when your code imports anthropic or @anthropic-ai/sdk |
| `/clear` | Start a new conversation with empty context. The previous conversation stays available in /resume. To free up context while continuing the same conversation, use /compact instead. Aliases: /reset, /new |
| `/color [color\|default]` | Set the prompt bar color for the current session. Available colors: red, blue, green, yellow, purple, orange, pink, cyan. Use default to reset |
| `/compact [instructions]` | Free up context by summarizing the conversation so far. Optionally pass focus instructions for the summary. See how compaction handles rules, skills, and memory files |
| `/config` | Open the Settings interface to adjust theme, model, output style, and other preferences. Alias: /settings |
| `/context` | Visualize current context usage as a colored grid. Shows optimization suggestions for context-heavy tools, memory bloat, and capacity warnings |
| `/copy [N]` | Copy the last assistant response to clipboard. Pass a number N to copy the Nth-latest response: /copy 2 copies the second-to-last. When code blocks are present, shows an interactive picker to select individual blocks or the full response. Press w in the picker to write the selection to a file instead of the clipboard, which is useful over SSH |
| `/cost` | Show token usage statistics. See cost tracking guide for subscription-specific details |
| `/debug [description]` | Enable debug logging for the current session and troubleshoot issues by reading the session debug log. Debug logging is off by default unless you started with claude --debug, so running /debug mid-session starts capturing logs from that point forward. Optionally describe the issue to focus the analysis |
| `/desktop` | Continue the current session in the Claude Code Desktop app. macOS and Windows only. Alias: /app |
| `/diff` | Open an interactive diff viewer showing uncommitted changes and per-turn diffs. Use left/right arrows to switch between the current git diff and individual Claude turns, and up/down to browse files |
| `/doctor` | Diagnose and verify your Claude Code installation and settings. Results show with status icons. Press f to have Claude fix any reported issues |
| `/effort [level\|auto]` | Set the model effort level. Accepts low, medium, high, xhigh, or max; available levels depend on the model and max is session-only. auto resets to the model default. Without an argument, opens an interactive slider; use left and right arrows to pick a level and Enter to apply. Takes effect immediately without waiting for the current response to finish |
| `/exit` | Exit the CLI. Alias: /quit |
| `/export [filename]` | Export the current conversation as plain text. With a filename, writes directly to that file. Without, opens a dialog to copy to clipboard or save to a file |
| `/extra-usage` | Configure extra usage to keep working when rate limits are hit |
| `/fast [on\|off]` | Toggle fast mode on or off |
| `/feedback [report]` | Submit feedback about Claude Code. Alias: /bug  |
| `/fewer-permission-prompts` | Scan your transcripts for common read-only Bash and MCP tool calls, then add a prioritized allowlist to project .claude/settings.json to reduce permission prompts |
