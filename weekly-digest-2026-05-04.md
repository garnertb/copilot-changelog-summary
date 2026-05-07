# Weekly Digest: May 4 – May 10, 2026

**Issue**: #19
**Status**: Active — compiled May 7 (sixteenth run, 18:57 UTC); updated with new Rubber Duck entry

## GitHub Changelog Entries (Covered)

- **Upcoming deprecation of GPT-5.2 and GPT-5.2-Codex** (May 1) — Both deprecated June 1, 2026. GPT-5.2 → GPT-5.5; GPT-5.2-Codex → GPT-5.3-Codex. Enterprise admins must enable alternative models in policy. Exception: GPT-5.2-Codex stays in Code Review past June 1.
- **Code-to-cloud risk visibility with Microsoft Defender for Cloud GA** (May 5) — GA of Defender+GHA integration. Runtime context filters (has:deployment, runtime-risk:internet-exposed, runtime-risk:sensitive-data). Copilot coding agent can be assigned security campaigns directly from the campaign view.
- **Secret scanning with GitHub MCP Server is now GA** (May 5) — GA for repos with GitHub Secret Protection enabled. Honors push protection customization. /plugin install advanced-security@copilot-plugins in Copilot CLI, or /secret-scanning in VS Code.
- **Dependency scanning with GitHub MCP Server is in public preview** (May 5) — dependabot toolset in GitHub MCP Server; checks GitHub Advisory Database; can run Dependabot CLI locally. Requires Dependabot alerts enabled.
- **GitHub Copilot in Visual Studio Code, April releases** (May 6) — Official monthly VS Code Copilot changelog covering v1.116–v1.119. Key: semantic search (all workspaces), /chronicle, BYOK model support, browser integration, cross-device CLI sessions, diff-in-chat, agent terminal access.
- **Enterprise-managed plugins in GitHub Copilot CLI are now in public preview** (May 6) — Admins define plugin marketplaces via .github-private settings.json; auto-distributed to all Business/Enterprise users on first auth.
- **Rubber Duck in GitHub Copilot CLI now supports more models** (May 7) — GPT sessions now get a Claude-powered Rubber Duck critic. Claude sessions upgraded to GPT-5.5 as Rubber Duck reviewer. Enable with /experimental on.

## VS Code

- **1.119.0 Stable** (May 6, 2026): Browser tab sharing with agents, VS Code Agents Insiders updates, OTel tracing (github.copilot.chat.otel.enabled), model details badge (enabled by default), background todo agent (experimental: github.copilot.chat.agent.backgroundTodoAgent.enabled), usage-based billing prep UI (June 1), allowNetwork sandbox mode (chat.agent.sandbox.enabled: "allowNetwork"), auto-approve /tmp writes for session-allowed commands.
- **1.120 Insiders** (May 4+): Agent host terminals respect preferred shell, restore copy in chat edit suggestions, hide archived sessions by default, custom snooze duration, customDiffEditorProvider proposed API.

## Key Reminders

- GPT-5.2 and GPT-5.2-Codex deprecated June 1, 2026 → switch to GPT-5.5 / GPT-5.3-Codex
- Copilot Code Review starts consuming Actions minutes June 1
- Usage-based billing for Copilot starts June 1

## Next Run

Watch for: new GitHub changelog entries for rest of week (Fri–Sun); any VS Code 1.120 Insiders updates.
