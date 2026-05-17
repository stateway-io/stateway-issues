# stateway-issues

Public issue tracker for the **stateway** project — a closed-source platform that handles business process management and workflow automation.

Issues posted here are automatically read and processed by an AI agent in the [`stateway-agents`](https://github.com/stateway-io/stateway-agents) repository.

## How it works

1. You open an issue using one of the templates below.
2. The AI agent reads your issue and processes it.
3. Depending on the issue type, the agent may apply labels, request more info, or take action.

The agent is designed to understand structured bug reports and feature requests, so filling in all template fields helps it process your issue faster and more accurately.

## Issue types

| Type | Template | Description |
|---|---|---|
| Bug report | [`bug_report.yml`](.github/ISSUE_TEMPLATE/bug_report.yml) | Something is not working as expected |
| Feature request | [`feature_request.yml`](.github/ISSUE_TEMPLATE/feature_request.yml) | A suggestion or idea for improvement |

If you're unsure which to use, just open a regular issue with a clear description.

## How to write a good issue

- **Be clear and direct** in the title — summarize the problem or request in a few words.
- **Fill in all template fields** — the agent uses this structure to understand what you need.
- **Provide context** — include steps to reproduce, environment details, screenshots, or logs when relevant.
- **One issue per topic** — if you have multiple bugs or ideas, open separate issues.

## Labels

Labels are applied by the agent after review. Common labels include:

| Label | Meaning |
|---|---|
| `bug` | Confirmed bug |
| `enhancement` | Feature request |
| `question` | Needs clarification |
| `high-priority` | Requires urgent attention |
| `duplicate` | Already reported |
| `wontfix` | Will not be addressed |

## For AI agents

If you are an agent creating issues via the GitHub API, note:

Templates in `.github/ISSUE_TEMPLATE/` are UI-only — they do not apply to API calls. The API accepts any `title` and `body`, regardless of `blank_issues_enabled: false`.

### API endpoint

```
POST /repos/stateway-io/stateway-issues/issues
```

### Recommended body format

Structure the `body` as plain text following this layout:

```
### Summary
<short description>

### Description
<detailed context>

### Steps to reproduce
<numbered steps>

### Expected behavior
<what should happen>

### Actual behavior
<what happens instead>

### Environment
- stateway version: <version>
- OS: <os>
- Browser: <browser>

### Priority
<low | medium | high | critical>
```

### Labels

Include an appropriate `labels` array in the API call:

| Issue type | Label |
|---|---|
| Bug | `bug` |
| Feature request | `enhancement` |
| Needs clarification | `question` |
| Urgent | `high-priority` |
| Duplicate | `duplicate` |

## What happens next

After you submit an issue, the agent typically processes it within a few minutes. You may see labels added, comments with follow-up questions, or the issue being closed with a resolution.

This is a public repository, so all discussions are visible to everyone.
