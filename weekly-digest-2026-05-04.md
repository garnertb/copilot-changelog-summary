# Weekly Digest: May 4 – May 10, 2026

**Issue**: #19
**Status**: Active — updated May 6 (tenth run, VS Code 1.119 stable released)

## GitHub Changelog Entries (Covered)

- **Upcoming deprecation of GPT-5.2 and GPT-5.2-Codex** (May 1) — Both deprecated June 1, 2026. GPT-5.2 → GPT-5.5; GPT-5.2-Codex → GPT-5.3-Codex. Enterprise admins must enable alternative models in policy. Exception: GPT-5.2-Codex stays in Code Review past June 1.
- **Code-to-cloud risk visibility with Microsoft Defender for Cloud GA** (May 5) — GA of Defender+GHA integration. Copilot coding agent can be assigned security campaigns from the campaign view.
- **Secret scanning with GitHub MCP Server is now GA** (May 5, 22:04 UTC) — GA for repos with GitHub Secret Protection enabled. Honors push protection customization. Get started with /plugin install advanced-security@copilot-plugins in Copilot CLI.
- **Dependency scanning with GitHub MCP Server is in public preview** (May 5, 20:45 UTC) — `dependabot` toolset in GitHub MCP Server; checks GitHub Advisory Database; can also run Dependabot CLI locally. Requires Dependabot alerts enabled.

## VS Code

- **1.119.0 Stable** (May 6, 2026 — RELEASED TODAY): Full release notes available. Key features:
  - Sharing browser tabs with agents (agents can request/use integrated browser)
  - OpenTelemetry tracing for agent sessions (github.copilot.chat.otel.enabled)
  - Model details badge on Copilot CLI/Claude agent responses
  - Optimized token usage via background todo agent (experimental)
  - Usage-based billing UI prep (June 1 transition)
  - allowNetwork sandbox mode for agent sandboxes
  - Auto-approve temp folder writes
  - VS Code Agents (Insiders) updates: redesigned repo picker, sub-session improvements
  - TypeScript 7 for Copilot extension (typecheck: 22s → 4s)
  - Edit Mode fully removed at 1.125

## Key Reminders Highlighted

- GPT-5.2 and GPT-5.2-Codex deprecated June 1, 2026 → switch to GPT-5.5 / GPT-5.3-Codex
- Copilot code review starts consuming Actions minutes June 1
- Usage-based billing for Copilot starts June 1

## Next Run

Watch for: new GitHub changelog entries for rest of week.
