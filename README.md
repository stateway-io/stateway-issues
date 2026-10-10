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
| Documentation | [`docs_change.yml`](.github/ISSUE_TEMPLATE/docs_change.yml) | Improvements or additions to documentation |
| Question | [`question.yml`](.github/ISSUE_TEMPLATE/question.yml) | Needs clarification |
| Chore | [`chore.yml`](.github/ISSUE_TEMPLATE/chore.yml) | Light refactor, lint, dependency bump, or maintenance |

If you're unsure which to use, just open a regular issue with a clear description.

## How to write a good issue

- **Be clear and direct** in the title — summarize the problem or request in a few words.
- **Fill in all template fields** — the agent uses this structure to understand what you need.
- **Provide context** — include steps to reproduce, environment details, screenshots, or logs when relevant.
- **One issue per topic** — if you have multiple bugs or ideas, open separate issues.

## Labels

Labels are applied by the agent after review. Actionable labels include:

| Label | Meaning |
|---|---|
| `bug` | Confirmed bug — agent attempts a fix and opens a PR |
| `feature-request` | Feature request — agent records it for triage |
| `docs` | Documentation / README / API reference edits |
| `chore` | Light refactor, lint, dependency bump, or maintenance |
| `question` | Needs clarification — agent only comments and defers to a human |
| `severity:high` | Urgent bug — promoted to triage, no automatic fix |
| `severity:critical` | Critical bug — promoted to triage, no automatic fix |
| `agent-fix-please` | Maintainer override: force the agent to attempt a fix |
| `agent-skip` | Maintainer override: force the agent to ignore the issue |

### Manual maintainer labels

These labels are not part of the agent routing schema and are applied manually by maintainers:

| Label | Meaning |
|---|---|
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

For urgent bugs, also include the `severity:high` or `severity:critical` label so the agent routes the issue to triage instead of attempting an automatic fix.

### Labels

Include an appropriate `labels` array in the API call:

| Issue type | Label |
|---|---|
| Bug | `bug` |
| Feature request | `feature-request` |
| Documentation | `docs` |
| Chore | `chore` |
| Needs clarification | `question` |
| Urgent bug | `severity:high` or `severity:critical` |

Maintainer override labels (not set by issue templates):

| Override | Label |
|---|---|
| Force agent fix | `agent-fix-please` |
| Force agent skip | `agent-skip` |

## What happens next

After you submit an issue, the agent typically processes it within a few minutes. You may see labels added, comments with follow-up questions, or the issue being closed with a resolution.

This is a public repository, so all discussions are visible to everyone.
