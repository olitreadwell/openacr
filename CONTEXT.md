# GSA/openacr context
> refreshed 2026-09-05 | upstream default: main @ 86f890a07a2a193d2a9404fb57d2cc2d62a60a4f

## Identity & policies
- upstream: GSA/openacr, default branch main, primary language JavaScript/TypeScript, English-first (yes — README/CONTRIBUTING in English)
- CLA/DCO: none (no CLA bot, no DCO requirement in CONTRIBUTING)
- AI-assisted PR policy: unstated (no AI mention in CONTRIBUTING/.github)
- signed commits required: no
- PR template: none (no PULL_REQUEST_TEMPLATE in repo or org default)
- external tracker: github

## Conventions (verified from merged PRs)
- branch naming: mixed; dominant pattern is descriptive kebab-case (`wcag-2.1-support`, `allow-adherence-level-none`, `doc-updates`, `report-changes`); fall back to `type/desc` kebab-case
- commit style: plain imperative, no conventional-commit prefix in most human commits
- test command: `npm test` (mocha + nyc); lint: `npm run lint` (eslint); typecheck: `tsc --noEmit`
- CI: GitHub Actions present; substantive checks are lint/test/typecheck
- how outside PRs get merged: repo is low-activity (last merged PR 2024-03-12); maintainers dmundra, mgifford, patrickhlauke

## Maintainer picture
- active maintainers: dmundra, mgifford (GSA); low recent activity
- areas they are actively working: catalog data (WCAG 2.2 / VPAT 2.5), editor tool

## Issue-area health
- validator CLI area is quiet (no redesign talk); issues #363-367 filed 2026-08-13 by external contributor AlexU-A, no maintainer response yet
- open + accepted + unassigned issues we could pick: none maintainer-engaged; #363-367 are documented but unacknowledged

## Gap ledger (dedupe — READ FIRST, never re-pick)
- 2026-09-05 pr-opened: `validate`/`output` with `-c <nonexistent-file>` silently skip catalog checks and report `Valid!`/success. Fixed in src/openacr.ts (report `Invalid: catalog file does not exist` when -c file is absent) + regression test. PR https://github.com/olitreadwell/openacr/pull/1 (fork-internal, base=main, head=fix/validate-nonexistent-catalog). Lesson: the fork's `tests` workflow is red on main for pre-existing reasons (outdated caniuse-lite -> browserslist warning breaks librarian-output-cli.test.ts; plus pre-commit cache outage, deprecated upload-artifact v2, a11y browser launch). New test passes (51 passing); do not re-pick this gap.

## Mined gaps (discovered, not yet attempted)
- 2026-09-05 clean-code `validate`/`output` with `-c <nonexistent-file>` silently skip catalog checks and report `Valid!`/success (repro: `npx ts-node src/openacr.ts validate -f tests/examples/valid.yaml -c /nonexistent/catalog.yaml` -> `Valid!`, exit 0). Expected: error that the catalog file does not exist. Dedupe: no upstream issue/PR covers the nonexistent-`-c` case (#363 covers omitting `-c`; #365 covers exit status). — status: pr-opened (2026-09-05, PR #1)
