# Draft: Weekly Copilot Summary – April 13, 2026 - April 19, 2026

_Issue creation failed: safeoutputs MCP server filtered by Copilot CLI MCP registry policy check_

---

> 🤖 *Your weekly digest of GitHub Copilot and AI coding developments — automatically compiled daily, grouped by week.*

---

### 🚀 GitHub Changelog Highlights

This digest runs on Monday, April 13 — the start of the week — so the GitHub Changelog scan window (April 13 only) has no new Copilot entries yet. VS Code 1.115 stable dropped last week and is covered below.

---

### 💻 VS Code AI/Copilot Updates

VS Code 1.115 landed April 8 with the headlining VS Code Agents companion app. VS Code 1.116 is in Insiders with reasoning effort controls for Copilot CLI, session history browsing, and improved terminal integration.

#### Stable: VS Code 1.115 (April 8, 2026)

VS Code Agents App (Preview) — new companion app for agent-native development:
- Parallel sessions across repos (each in its own isolated worktree)
- Monitor diffs inline, leave feedback, open PRs without switching tools
- Custom instructions, prompt files, MCP servers, hooks all carry over
- Launch: Chat: Open Agents Application in Command Palette (Insiders only)

BYOK for Copilot Business and Enterprise — org admins enable the policy in Copilot settings.

Terminal tools: new send_to_terminal lets agents interact with background terminals. Experimental chat.tools.terminal.backgroundNotifications auto-notifies agents when background commands finish.

Integrated browser: better agent tool labels, long-running Playwright script support, fewer duplicate tabs, pinch-to-zoom on macOS.

Deprecation: Edit Mode deprecated since 1.110, removed in 1.125.

Full notes: https://code.visualstudio.com/updates/v1_115

#### Insiders: VS Code 1.116 (as of April 12)

- Browse historical agent sessions in Agent Debug Panel
- Reasoning effort control for Copilot CLI sessions
- Auto branch naming by Copilot CLI agent from user prompt
- send_to_terminal / get_terminal_output now work with foreground terminals
- NeedsInput status in Agent Host Protocol for extensions
- #-triggered file-context completions in Agents app
- #changes context variable offloads large diffs to file reference (avoids token limits)

Full notes: https://code.visualstudio.com/updates/v1_116

---

### Week in Review

VS Code 1.115 shipped VS Code Agents — a dedicated app for multi-repo, parallel agentic coding. For teams, BYOK reaching Business/Enterprise is the most actionable change. VS Code 1.116 Insiders shows continued agent polish; expect stable in ~2 weeks.

---

Sources: GitHub Changelog - VS Code Updates - Last updated April 13, 2026
