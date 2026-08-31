# Changelog

User-visible changes to the skill packet. Format follows [Keep a Changelog](https://keepachangelog.com/); versions are [release tags](https://github.com/keng009/fulcra-raise-memory/releases) with ready-to-upload zips attached. Live-behavior evidence for every claim: [docs/testing.md](docs/testing.md).

## [Unreleased] — 0.1.0

### Added
- Initial public packet, forked 2026-08-27 from [fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory)'s engine (contract v3.1) and re-flavored for founders actively raising (ADR-0007): `/raise/` namespace, `Raise Touchpoint` type, investor/fund vocabulary, raise-stage `stage_noted` vocabulary (`intro` → `passed`/`committed`), "Investors going cold" reporting.
- The two skills: `raise-demo` (guided 10-minute session, snapshot-first) and `raise-memory` (ongoing capture/recall/report with the same snapshot-first Show→Save→Tend flow as the sibling — identical time-to-value by design).
- Engine features carried from the fork point: stable per-source dedupe keys (`touch:cal:<event-id>`, transcript ids, CRM-note ids), the veto-set-first invariant and tombstone list, review queue, backfill hygiene, dual-surface calendar detection, CRM capability tiers + "Add your CRM" protocol, messaging capture registry (`message` channel; WhatsApp/Telegram/Signal/iMessage/LinkedIn/Slack paste tier).
- CI validation, release packaging, ADRs 0001–0007, five-rule CONTRIBUTING, and docs/why-fulcra.md (what Fulcra is used for, the value, and the honest necessary-vs-convenient line).
- README chooser ("which skill do I install?"); docs/mcp-operations.md (MCP conformance list); docs/harness-matrix.md (per-harness evidence, all untried for this flavor); messaging browser-observation tier; scheduled-sweep Tend behavior; CRM slot 6 note placement — the designed features carry designed/untested labels until testing.md rows exist.

- Review round 5–7 hardening: commit ledger before every one-yes (snapshot or direct backfill), sweep watermarks with failure-safe advancement, per-destination veto disclosure, CRM delete-capability slot 7, "every read these skills perform" scoping throughout, ADR-0007 attribution completed (ADR-0002, crm-sync spoken line, protocol pointer), sample stage vocabulary corrected (intro call → `intro`). Round 7 (the first review of this repo itself): stable per-source keys are never replaced by the date-form key; the demo's sample cleanup is interruption-safe (tombstone first, then soft-delete, then summary); the snapshot loads the veto set before presenting; `delete_file` in both preflights; sync-vs-import honesty (CRM-note import is a separate consented read path, not a reverse sync); CONTRIBUTING audience corrected to founders. Findings archived in [#12](https://github.com/keng009/fulcra-raise-memory/issues/12). Round 8: crm-sync dedupe principle enumerates all five canonical key forms; README privacy copy discloses snapshot-time reads (independent of CRM-sync acceptance).

### Release gate
- First release requires the live runs listed in [docs/testing.md](docs/testing.md) — this flavor ships engine-proven but flavor-untested until then, and the README says so.
