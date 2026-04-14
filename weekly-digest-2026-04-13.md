> 🤖 *Your weekly digest of GitHub Copilot and AI coding developments — automatically compiled daily, grouped by week.*

---

### 🚀 GitHub Changelog Highlights

This week delivered three significant Copilot launches in a single day: enterprise-grade data residency with FedRAMP compliance, a one-click merge conflict resolution powered by the cloud agent, and remote CLI supervision from mobile or web. Together, they signal GitHub's push toward Copilot as an always-available, anywhere-accessible platform — not just a local IDE plugin.

#### ✨ New Features

- **Copilot data residency in US + EU and FedRAMP compliance now available** (Apr 13) — GitHub Copilot now keeps all inference processing and associated data within your designated geography (US or EU). For US government customers, model hosts and infrastructure meet FedRAMP Moderate authorization standards. Every generally available Copilot feature is supported under data residency: agent mode, inline suggestions, chat, Copilot cloud agent, code review, PR summaries, and Copilot CLI.

  **Models available at launch** span both OpenAI and Anthropic, including GPT-5.4, Claude Sonnet 4.6, and Claude Opus 4.6. Gemini models are not yet supported pending GCP regional inference endpoints.

  | What's covered | What's not yet |
  |---|---|
  | US and EU regions | Japan, Australia (roadmap: later 2026) |
  | All GA Copilot features | Gemini models (GCP infra limitation) |
  | OpenAI + Anthropic models | Newly released models (may lag) |

> [!IMPORTANT]
> Data-resident and FedRAMP requests carry a **10% increase in the model multiplier** (e.g., a 1× model costs 1.1 premium requests). Admins must opt-in explicitly from Copilot settings — it's off by default.

  [Read more →](https://github.blog/changelog/2026-04-13-copilot-data-residency-in-us-eu-and-fedramp-compliance-now-available)

- **Fix merge conflicts in three clicks with Copilot cloud agent** (Apr 13) — A new **Fix with Copilot** button now appears on github.com wherever a PR has merge conflicts. Click it, submit the pre-populated comment, and the cloud agent resolves conflicts, verifies the build and tests pass, then pushes — all from its own isolated cloud environment. You can also `@copilot` mention the agent in PR comments for related tasks:

  ```
  @copilot Fix the failing tests
  @copilot Address this comment
  @copilot Add a unit test covering the case when the model argument is missing
  ```

> [!NOTE]
> Copilot Business and Enterprise users need an administrator to [enable Copilot cloud agent](https://docs.github.com/en/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/manage-copilot-cloud-agent) before this feature is available.

  [Read more →](https://github.blog/changelog/2026-04-13-fix-merge-conflicts-in-three-clicks-with-copilot-cloud-agent)

- **Remote control CLI sessions on web and mobile** (Apr 13, Public Preview) — The Copilot CLI is no longer confined to your local terminal. Launch with `copilot --remote` (or enable mid-session with `/remote`) and get a shareable link and QR code. From any browser or the GitHub Mobile app (Android/iOS), you can monitor activity in real time, send steering messages, switch modes, and approve/deny permission requests.

  ```bash
  # Update to latest CLI version first
  /update

  # Start a new remote session
  copilot --remote

  # Or enable in an existing session
  /remote

  # Keep your machine awake for long tasks
  /keep-alive
  ```

> [!NOTE]
> Requires a GitHub repository as the working directory. Business/Enterprise users need an admin to enable remote control and CLI policies first. Mobile access is via [Google Play beta](https://play.google.com/apps/testing/com.github.android) or [iOS TestFlight](https://testflight.apple.com/join/NLskzwi5).

  [Read more →](https://github.blog/changelog/2026-04-13-remote-control-cli-sessions-on-web-and-mobile-in-public-preview)

---

### 💻 VS Code AI/Copilot Updates

VS Code 1.115 shipped April 8 — just before this week — with two headline additions for AI-heavy workflows: the new **VS Code Agents companion app** (Insiders-only preview) for multi-repo parallel agent sessions, and **BYOK for Copilot Business and Enterprise**. Terminal and browser tooling also received meaningful upgrades, rounding out a release focused on making VS Code a first-class agentic IDE.

#### 📦 Stable Release Highlights

**VS Code 1.115** (April 8, 2026)

- **VS Code Agents App (Preview)** — A brand-new companion app ships alongside VS Code Insiders, purpose-built for agent-native development. Run parallel agent sessions across multiple repos (each in an isolated worktree), monitor progress, review inline diffs, leave feedback, and open PRs — all without leaving the app. Custom instructions, MCP servers, prompt files, and hooks carry over automatically. Launch via **Chat: Open Agents Application** from the Command Palette.

  ![VS Code Agents App screenshot](https://code.visualstudio.com/assets/updates/1_115/agents-release-notes-1.webp)

- **Bring Your Own Key (BYOK) for Business and Enterprise** — Organizations can now allow members to connect their own API keys for providers like OpenRouter, Ollama, Google, and OpenAI in Copilot Chat. Admins enable it via the **Bring Your Own Language Model Key in VS Code** policy in [Copilot policy settings](https://github.com/settings/copilot/features).

- **Send input to background terminals** — A new `send_to_terminal` tool lets agents interact with terminals that timed out and moved to the background (e.g., an SSH session waiting for a password prompt that previously would have been stuck).

- **Background terminal notifications** *(Experimental, `chat.tools.terminal.backgroundNotifications`)* — Agents are automatically notified when a background terminal completes or needs input — no more manual polling with `get_terminal_output`.

- **Integrated browser improvements** — Better tool call labels with direct tab links, long-running Playwright script support (deferred polling for scripts >5s), smarter duplicate-tab suppression, and pinch-to-zoom on macOS.

  ![New browser tool label screenshot](https://code.visualstudio.com/assets/updates/1_115/browser-tool-new.webp)

*Full release notes: [https://code.visualstudio.com/updates/v1_115](https://code.visualstudio.com/updates/v1_115)*

#### 🔬 Coming Soon (Insiders Preview)

Features in VS Code 1.116 Insiders not yet in Stable:

- **Reasoning effort control for Copilot CLI** — Tune how deeply the model reasons before responding, balancing speed vs. quality per task.
- **Session history browsing** — Navigate back through previous agent chat sessions in the UI.
- **Auto branch naming** — Agents suggest and create descriptive branch names when starting tasks.
- **Expanded foreground terminal tools** — Richer terminal interaction capabilities for foreground sessions.

*Note: Insiders features are pre-release and may change before reaching Stable.*

---

### 📋 Week in Review

The dominant theme this week is **Copilot as infrastructure** — not just a coding assistant but a platform with enterprise-grade reliability, compliance, and remote accessibility. The data residency + FedRAMP announcement is the most consequential for large organizations: it unlocks Copilot for regulated industries and government use cases that were previously blocked by data sovereignty concerns. The 10% pricing premium is real, but for organizations in heavily regulated spaces, the compliance story often outweighs the cost.

For individual developers, the remote CLI feature is the most immediately exciting change. Being able to kick off a long-running agent session from your laptop and supervise it from your phone while you're away changes how you can structure your day. The merge conflict fix-in-three-clicks is similarly practical — it converts one of the most tedious parts of collaborative development into a nearly zero-effort task, with the cloud agent validating the result before you even look at it.

The VS Code 1.115 release, while technically shipping just before this week, is worth highlighting: the VS Code Agents companion app is a meaningful architectural bet on parallel, multi-repo agentic workflows being the future of development. Watch for BYOK adoption to grow among teams who want to route specific use cases through their own model agreements. The steady drumbeat of terminal and browser tooling improvements also underscores how much infrastructure work is going into making agents reliably autonomous in real development environments.

---

*Sources: [GitHub Changelog](https://github.blog/changelog/) · [VS Code Updates](https://code.visualstudio.com/updates/) · Last updated April 14, 2026*
