# CowAgent
## Claude Review Standard

For required AI review, use Claude CLI subscription only.

- Use the project wrapper `scripts\claude_subscription.ps1` when present.
- Reviewer model: Opus 4.8 max effort.
- Verify `modelUsage.claude-opus-4-8` in raw JSON.
- Prefer fresh one-shot review: `--no-session-persistence`.
- Prefer bounded read-only review: `--tools=Read`.
- Do not use API-key, API-base, or Bedrock Claude routes for required review.
- Do not attach files to Opus.
- Do not paste whole files unless the packet is intentionally tiny.
- Use bounded file-reference packets with exact repo path, file path, line ranges, diff summary, tests/probes, risks, and acceptance criteria.
- Review prompt must include both stable project goal/control context and worker evidence.
- Invalid review: `is_error=true`, timeout, API error, wrong model, wrong route, or missing raw JSON.
- If review returns REQUEST_CHANGES, blocker, or major: fix, test, and rerun until the final valid review has 0 blockers and 0 majors.
- Save raw JSON and markdown review logs under the repo's review log folder.
- New non-standard artifacts created by Codex use `_codex`; new non-standard artifacts created by Claude use `_claude`. Standard protocol files may keep their existing names but must identify the producer inside.

