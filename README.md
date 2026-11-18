# Upwork Job Assistant

[<kbd>中文</kbd>](README.zh-CN.md) · [<kbd>English</kbd>](README.md)

An agent skill for finding and evaluating software development jobs through the official Upwork MCP. It uses your skills, experience, rates, and delivery preferences to produce a local Markdown report with recommendations, estimated effort and earnings, Connects costs, and proposal drafts.

Upwork access is read-only. You decide which jobs to apply for and submit proposals yourself.

[View a real screening report with identifying details removed](examples/sample-report.md) to see the recommendations, earnings estimates, and proposal drafts.

## Quick start

Use an agent that supports local skills and MCP, along with your own Upwork Freelancer account. Keep the entire skill directory together so the agent can load `SKILL.md` and its supporting files. Invoke `$upwork-job-assistant` in a client that discovers local skills, or ask your agent to follow `SKILL.md` directly.

### 1. Connect the Upwork MCP

Add the official endpoint at `https://mcp.upwork.com/mcp` and authorize your own account. For Codex CLI, run the commands below.

```bash
codex mcp add upwork --url https://mcp.upwork.com/mcp
codex mcp login upwork
```

Your client and the MCP handle authentication. The local profile and preferences hold screening information.

### 2. Create your local profile and preferences

Copy the English templates from the skill directory. These commands preserve existing files.

```bash
[ -e config/profile.md ] || cp config/profile.example.md config/profile.md
[ -e config/preferences.yaml ] || cp config/preferences.example.yaml config/preferences.yaml
```

- Fill in `config/profile.md` with verified skills, relevant experience you can share, availability, and communication preferences. Remove the fictional example before using your profile.
- Customize the search terms, job types, and screening preferences in `config/preferences.yaml`. Rates, budget floors, and platform fees are optional. The report flags missing inputs that affect estimates.
- Reports and proposal drafts default to English. Set `output.language` for the report and `output.proposal_languages` for the drafts. For Simplified Chinese templates and instructions, see the [Chinese quick start](README.zh-CN.md).

### 3. Screen jobs

Ask your agent to run a screen using your local settings.

> Use Upwork Job Assistant to find recent jobs that match my profile and preferences. Save a Markdown report with recommendations, conditional recommendations, and proposal drafts.

The first run starts with empty state and uses the configured lookback period. After saving a report, the skill records the run time and job IDs in `state/` to avoid duplicates and recheck earlier candidates. To initialize these files yourself, use the commands below.

```bash
[ -e state/run-state.json ] || cp state/run-state.example.json state/run-state.json
[ -e state/job-history.json ] || cp state/job-history.example.json state/job-history.json
```

## Reading the report

Review each recommendation's rationale, delivery scope, estimated earnings, and Connects cost. Conditional recommendations explain what you need to confirm or accept before applying. Check the current posting details and review any proposal draft before submission. Search coverage depends on the data, ordering, and pagination provided by the MCP.

Tell your agent which jobs you applied for, skipped, or want to watch so it can update local history. Adjust search terms and scoring preferences as you review results.

## Files

| File | Purpose |
|---|---|
| [SKILL.md](SKILL.md) | Agent workflow and read-only Upwork access |
| [Profile template](config/profile.example.md) | Skills, experience, project evidence, and delivery constraints |
| [Preferences template](config/preferences.example.yaml) | Search, scoring, and output settings |
| [Proposal guide](config/proposal-guide.md) | Drafting and reviewing proposals |
| [Report format](references/report-format.md) | Report sections and field definitions |
| [State management](references/state-management.md) | Incremental search and history updates |
| [Sample report](examples/sample-report.md) | An actual screening run with identifying details removed |
| [State templates](state/) | Empty starting state |

## Local data and privacy

Git ignores completed local profiles and preferences, generated reports under `reports/`, and runtime files under `state/`. If you move state or report output elsewhere in the repository, update `.gitignore` to cover the new paths. Before sharing a report, remove personal details, original job links, credentials, application history, and diagnostic identifiers.

This project is distributed under the [MIT License](LICENSE).
