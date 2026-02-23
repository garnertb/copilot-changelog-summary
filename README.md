# copilot-changelog-summary

A GitHub Agentic Workflow that automatically compiles a weekly digest of GitHub Copilot and AI coding developments.

## What It Does

Every Monday runs the `weekly-copilot-chronicle` workflow:

1. **Scans the GitHub Changelog** ([github.blog/changelog](https://github.blog/changelog/)) for Copilot and AI-related updates from the past 7 days, including:
   - New features and capabilities
   - API and integration changes
   - AI model availability updates
   - Deprecations and removals

2. **Reviews VS Code AI/Copilot Updates** ([code.visualstudio.com/updates](https://code.visualstudio.com/updates/)) covering:
   - **Insiders** builds – preview upcoming features being actively developed
   - **Stable** releases – features that shipped to general availability

3. **Publishes a GitHub Discussion** with the compiled weekly chronicle, automatically closing the previous week's entry.

## Setup

This workflow requires [GitHub Agentic Workflows (gh-aw)](https://github.com/github/gh-aw) to be installed in the repository.

After installing gh-aw, compile the workflow to generate the GitHub Actions YAML:

```bash
gh aw compile weekly-copilot-chronicle
```

### Required Repository Settings

- **GitHub Discussions** must be enabled on the repository
- The workflow uses read-only permissions; discussion creation is handled via `safe-outputs`

### Running Manually

The workflow can be triggered manually via the GitHub Actions UI using the `workflow_dispatch` event.

## Output

Results are published as GitHub Discussions with the title prefix `📰 `. Previous weeks' discussions are automatically closed and marked as outdated when a new chronicle is published.
