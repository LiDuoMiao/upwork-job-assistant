# Incremental Search and Job History

## State files

Resolve configured state paths relative to the skill directory. The defaults are `state/run-state.json` and `state/job-history.json`. When a file is missing, start with the corresponding [empty run state](../state/run-state.example.json) or [empty job history](../state/job-history.example.json). Preserve valid existing state. If a file cannot be parsed, explain the issue and preserve the file.

Run state records `last_successful_run_at`, `last_deep_backfill_at`, and `last_config_version`. Store timestamps in ISO 8601 with an offset.

Key the `jobs` history by the stable job ID. Store the title, public link, publication time, first and last seen times, latest recommendation, user decision, configuration version used for evaluation, and relative report path as available. Omit full descriptions, verbatim client feedback, private account identifiers, Connects balances, trace IDs, proposal text, and credentials.

## Time windows and pagination

- Start the first run with `first_run_lookback_days`. Capture `run_started_at` once as the end of the search window.
- For regular runs, start at the last successful time minus `overlap_hours` and cap the lookback with `max_regular_lookback_days`. Disclose any period outside the covered window.
- If deep backfill is enabled, perform the first backfill on the run after the first successful regular run. Use `last_deep_backfill_at` and `interval_days` to schedule later backfills. Use the backfill's `lookback_days` and separate pagination cap. The user can also request a backfill.
- For recent or recency-sorted routes, stop when there is no next page, the entire page predates the window, or the pagination cap is reached. Filter to the window locally for routes without a server-side date filter. When capped, note that additional in-window jobs may remain.

## Across runs

Use the following common values for `last_decision`.

| Value | Meaning and follow-up |
|---|---|
| `seen` | Found in search without full analysis. Reconsider during backfill or after a material change to the job or screening rules |
| `recommended` | Evidence supports applying. Recheck within the reminder window |
| `conditional` | The user needs to meet or accept a condition. Recheck within the reminder window |
| `watch` | The user asked to keep an eye on it. Recheck within the reminder window |
| `not_recommended` | Reconsider when material information or relevant rules change |
| `applied` | Upwork shows an application, or the user confirmed it. Exclude from recommendations |
| `dismissed` | The user explicitly skipped it. Exclude from recommendations |
| `closed` | Closed, ineligible for applications, or filled. Retain in history |

Use configured limits for the scope and number of rechecks. Reanalyze a job when budget, description, hiring activity, or the user's decision materially changes. Record explicit user feedback in `user_disposition`. An `applied=true` detail field also excludes the job from recommendations.

## Save order

Save the Markdown report, then the updated history. Finally, record `run_started_at` in `last_successful_run_at` and store the configuration version. For a successful backfill, also update `last_deep_backfill_at`. Retain the previous success timestamp if a critical step fails so the next run can cover the affected interval. Merge history by job ID and reuse saved rows when retrying.
