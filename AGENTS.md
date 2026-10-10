# stateway-issues — agent guide

## Purpose

This is not a code repository. It is a public issue inbox for the closed-source **stateway** project. Issues posted here are consumed by an AI agent in [`stateway-agents`](https://github.com/stateway-io/stateway-agents).

There is nothing to build, test, lint, typecheck, or install locally.

## Creating issues via API

Templates under `.github/ISSUE_TEMPLATE/` are UI-only and do not apply to GitHub API calls. The API accepts any `title` and `body` regardless of `blank_issues_enabled: false`.

```
POST /repos/stateway-io/stateway-issues/issues
```

Use this body structure:

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

For urgent bugs, also add the `severity:high` or `severity:critical` label so the agent routes the issue to triage instead of attempting an automatic fix.

Include labels in the API call when applicable:

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

> **Source of truth:** the label schema lives in [`../fly-swe/docs/label-schema.md`](../fly-swe/docs/label-schema.md). This table must stay in sync with it.

## Key files

| File | Purpose |
|---|---|
| `README.md` | Full documentation for human and agent contributors |
| `.github/ISSUE_TEMPLATE/bug_report.yml` | Bug report form (UI only) |
| `.github/ISSUE_TEMPLATE/feature_request.yml` | Feature request form (UI only) |
| `.github/ISSUE_TEMPLATE/docs_change.yml` | Documentation change form (UI only) |
| `.github/ISSUE_TEMPLATE/question.yml` | Question / clarification form (UI only) |
| `.github/ISSUE_TEMPLATE/chore.yml` | Chore / maintenance form (UI only) |
| `.github/ISSUE_TEMPLATE/config.yml` | Template config, disables blank issues, contact via `hello@stateway.io` |
