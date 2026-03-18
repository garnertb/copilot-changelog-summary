---
description: "Analyze a GitHub Agentic Workflow (.md) for unused capabilities, suggest prioritized improvements, apply approved changes, and compile. Use when: improving workflows, auditing gh-aw features, optimizing agentic workflow configuration."
agent: "agent"
argument-hint: "Workflow filename or improvement focus area"
---

# Improve Agentic Workflow

Analyze the specified GitHub Agentic Workflow file (or the currently open `.md` workflow) and recommend improvements to maximize its quality and value.

## Context

- Read the [copilot-instructions](.github/copilot-instructions.md) for project rules (never edit `.lock.yml` files directly, always compile after changes).
- The gh-aw documentation is at `https://raw.githubusercontent.com/github/gh-aw/main/.github/aw/github-agentic-workflows.md` — fetch it for the latest available capabilities.

## Process

### 1. Audit Current Configuration

Read the workflow's YAML frontmatter and body. Inventory what's currently configured:
- Engine, tools, safe-outputs, network, triggers, permissions
- Prompt structure and instructions

### 2. Gap Analysis

Compare every section of the fetched gh-aw documentation against the workflow's current configuration. Flag any supported capability — tools, safe-outputs, configuration options, engine features, or anything else — that the workflow isn't using yet and that could add value.

### 3. Recommend Improvements

Present findings as a prioritized table:

| Priority | Capability | Why it helps | Effort |
|----------|-----------|-------------|--------|
| High | ... | ... | Low/Med/High |

Group into:
- **Quick wins** — high value, low effort, drop-in config changes
- **Medium lift** — requires prompt updates alongside config
- **Larger enhancements** — new workflow patterns or multi-workflow orchestration

For each recommendation, explain the concrete value it adds to this specific workflow (not generic benefits).

### 4. Apply Changes

After the user approves recommendations:
1. Edit the workflow `.md` file (frontmatter + body as needed)
2. Validate the schema matches gh-aw expectations (check safe-output field formats carefully)
3. Compile with `gh aw compile <workflow-name>`
4. If warnings appear, fix them and recompile until clean (0 errors, 0 warnings)

### 5. Summary

After successful compile, briefly list what changed and any follow-up considerations.
