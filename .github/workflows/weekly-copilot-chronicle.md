---
description: Creates a weekly chronicle of interesting GitHub Copilot changes based on the GitHub Changelog and VS Code AI/Copilot updates
on:
  schedule: weekly on monday
  workflow_dispatch:
permissions:
  discussions: read
  issues: read
  pull-requests: read
  contents: read
engine: copilot
timeout-minutes: 30
network:
  allowed:
    - defaults
    - github.blog
    - code.visualstudio.com
tools:
  web-fetch:
  bash:
    - "*"
  github:
    toolsets:
      - default
      - discussions
safe-outputs:
  create-discussion:
    title-prefix: "📰 "
    close-older-discussions: true
---

# Weekly Copilot Changelog Chronicle

You are a technology journalist creating a weekly digest of GitHub Copilot and AI coding developments. Your goal is to help developers stay current with the rapidly changing landscape of AI-assisted development.

## Your Mission

Compile a weekly chronicle covering the **past 7 days** of GitHub Copilot changes from two sources:

1. **GitHub Changelog** (`https://github.blog/changelog/`) – new features, deprecated features, API changes, and model availability changes
2. **VS Code Updates** (`https://code.visualstudio.com/updates/`) – AI/Copilot-specific features from Insiders builds and the latest Stable release

---

## Step 1: Gather GitHub Changelog Data

Fetch the GitHub Changelog RSS feed and filter for Copilot and AI-related entries from the past 7 days.

First, compute and record the key dates you will use throughout the report:

```bash
# Calculate date range and week boundaries
TODAY=$(date -u +"%Y-%m-%d")
WEEK_AGO=$(date -u -d "7 days ago" +"%Y-%m-%d" 2>/dev/null || date -u -v-7d +"%Y-%m-%d")
# Monday of the current week (for the chronicle title)
MONDAY=$(date -u -d "last monday" +"%B %-d, %Y" 2>/dev/null || date -u +"%B %-d, %Y")
echo "Chronicle title date: $MONDAY"
echo "Scanning GitHub Changelog from $WEEK_AGO to $TODAY"
```

Use these computed values when filling in the `{MONDAY_DATE}` and `{TODAY}` placeholders in the discussion title and footer.

Use the `web-fetch` tool to retrieve: `https://github.blog/changelog/feed/`

Parse the RSS feed entries. For each entry, extract:
- **Title**
- **Publication date** (pubDate)
- **URL** (link)
- **Description/summary**
- **Categories** (if available)

**Filter for relevance**: Include entries whose title, description, or categories contain any of the following terms (case-insensitive):
`copilot`, `AI model`, `LLM`, `GPT`, `Claude`, `Gemini`, `o1`, `o3`, `agent`, `MCP`, `Model Context Protocol`, `code completion`, `inline chat`, `extensions API`, `Copilot Chat`, `GitHub Models`

Categorize the relevant entries as:
- **✨ New Features** – New capabilities, integrations, or tools
- **⚠️ Deprecations & Removals** – Features being sunset, APIs being removed
- **🔌 API & Integration Changes** – Developer-facing API updates, extension changes, webhook updates
- **🤖 Model Availability** – New models added, model updates, model deprecations

If no entries fall into a category, omit that category from the report.

---

## Step 2: Gather VS Code AI/Copilot Update Data

VS Code ships updates frequently:
- **Insiders** builds ship continuously and preview upcoming features
- **Stable** releases approximately monthly but receives minor updates in between

### Fetch the VS Code Updates page

Use `web-fetch` to retrieve: `https://code.visualstudio.com/updates/`

From this page, identify:
1. The **latest Stable release** version (e.g., "v1.98") and its release notes URL
2. Recent **Insiders** updates and features

Then fetch the release notes for the **latest Stable version**. The URL format is: `https://code.visualstudio.com/updates/v{major}_{minor}` (e.g., `https://code.visualstudio.com/updates/v1_98`).

Also fetch the VS Code Copilot changelog at: `https://code.visualstudio.com/docs/copilot/copilot-changelog`

### What to Look For

In the VS Code release notes, find sections related to:
- **GitHub Copilot** – Any section titled "GitHub Copilot", "Copilot", "AI", or similar
- **Copilot Chat** – Chat interface features, slash commands, context variables
- **Inline Chat** – In-editor chat and code generation features
- **Agent Mode** – Autonomous coding agent capabilities
- **Copilot Edits** – Multi-file edit features
- **Language model APIs** – `vscode.lm` API changes, new providers, capabilities
- **Extension authoring** – New APIs for AI/Copilot integration

For **Insiders**, note that these features are pre-release and subject to change.

---

## Step 3: Compile and Format the Chronicle

Create a GitHub Discussion with the following structure.

Use h3 (`###`) and h4 (`####`) headers only—never h1 or h2. The discussion title provides the top-level heading.

```
TITLE: Weekly Copilot Chronicle – Week of {MONDAY_DATE}

BODY:
```

### Report Structure

```markdown
> 🤖 *Your weekly digest of GitHub Copilot and AI coding developments — automatically compiled every Monday.*

---

### 🚀 GitHub Changelog Highlights

[2–3 sentences summarizing the most impactful changes of the week from the GitHub Changelog. If no Copilot-related changes were found, write a brief note stating it was a quiet week and mention the date range checked.]

#### ✨ New Features

[For each new feature entry:]
- **[Entry Title]** ([date]) — [1–2 sentence description of what's new and why it matters]. [Read more →](<url>)

#### 🔌 API & Integration Changes

[For each API or integration change:]
- **[Entry Title]** ([date]) — [1–2 sentence description]. [Read more →](<url>)

#### 🤖 Model Availability Updates

[For each model-related entry:]
- **[Entry Title]** ([date]) — [1–2 sentence description]. [Read more →](<url>)

#### ⚠️ Deprecations & Removals

[For each deprecation:]
- **[Entry Title]** ([date]) — [what's being deprecated and any migration guidance]. [Read more →](<url>)

---

### 💻 VS Code AI/Copilot Updates

[2–3 sentences summarizing the VS Code AI developments this week. Distinguish between what's available now in Stable vs what's coming in Insiders.]

#### 📦 Stable Release Highlights

**VS Code [version]** ([release date])

[Summarize the Copilot/AI section of the Stable release notes. Include:]
- Key features with brief descriptions
- Any behavior changes or improvements
- Links to the full release notes

*Full release notes: [https://code.visualstudio.com/updates/v{major}_{minor}](<url>)*

#### 🔬 Coming Soon (Insiders Preview)

[Features available in VS Code Insiders that haven't reached Stable yet. These represent what's actively being developed:]

[For each notable Insiders feature:]
- **[Feature Name]** — [1–2 sentence description of the feature and its potential impact]

*Note: Insiders features are pre-release and may change before reaching Stable.*

---

### 📋 Week in Review

[2–3 paragraph editorial summary. Cover:]
1. **The week's theme**: What major direction or focus was apparent in this week's updates?
2. **Developer impact**: Which changes are most actionable for developers using Copilot today?
3. **What to watch**: Any upcoming features or changes developers should be aware of?

---

*Sources: [GitHub Changelog](https://github.blog/changelog/) · [VS Code Updates](https://code.visualstudio.com/updates/) · Generated {TODAY}*
```

---

## Guidelines

### Content Guidelines
- **Be accurate**: Only include changes you found in the fetched sources. Do not fabricate entries.
- **Be concise**: Each entry needs just 1–2 sentences. The goal is scannable, actionable information.
- **Link everything**: Include URLs for every entry so readers can get full details.
- **Date entries**: Show the publication/release date for each item.
- **Skip empty sections**: If a category has no entries this week, omit it entirely.
- **Handle no-data gracefully**: If the RSS feed or VS Code updates are unavailable, note this in the relevant section rather than leaving it blank.

### Formatting Guidelines
- Use h3 (`###`) for main sections, h4 (`####`) for subsections
- Use bullet points within sections (the no-bullet-point rule from the template does not apply here—lists are appropriate for changelog entries)
- Wrap the Insiders section in a `<details>` tag if it contains more than 8 features to avoid overwhelming the reader:
  ```markdown
  <details>
  <summary><b>All Insiders Features This Week</b></summary>
  
  [Long list of features]
  
  </details>
  ```
- Keep the "Week in Review" section in flowing paragraphs

### Error Handling
- If the GitHub Changelog RSS returns no Copilot-related entries: note it was a quiet week, still check VS Code
- If VS Code updates page is unavailable: note this and proceed with GitHub Changelog data only
- If both sources are unavailable: create a brief discussion noting the data collection issue and the date range
