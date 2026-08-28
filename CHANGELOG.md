# Changelog

User-visible changes to the skill packet. Format follows [Keep a Changelog](https://keepachangelog.com/); versions are [release tags](https://github.com/keng009/fulcra-raise-memory/releases) with ready-to-upload zips attached. Live-behavior evidence for every claim: [docs/testing.md](docs/testing.md).

## [Unreleased] — 0.1.0

### Added
- Initial public packet, forked 2026-08-27 from [fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory)'s engine (contract v3.1) and re-flavored for founders actively raising (ADR-0007): `/raise/` namespace, `Raise Touchpoint` type, investor/fund vocabulary, raise-stage `stage_noted` vocabulary (`intro` → `passed`/`committed`), "Investors going cold" reporting.
- The two skills: `raise-demo` (guided 10-minute session, snapshot-first) and `raise-memory` (ongoing capture/recall/report with the same snapshot-first Show→Save→Tend flow as the sibling — identical time-to-value by design).
- Engine features carried from the fork point: stable per-source dedupe keys (`touch:cal:<event-id>`, transcript ids, CRM-note ids), the veto-set-first invariant and tombstone list, review queue, backfill hygiene, dual-surface calendar detection, CRM capability tiers + "Add your CRM" protocol, messaging capture registry (`message` channel; WhatsApp/Telegram/Signal/iMessage/LinkedIn/Slack paste tier).
- CI validation, release packaging, ADRs 0001–0007, five-rule CONTRIBUTING.

### Release gate
- First release requires the live runs listed in [docs/testing.md](docs/testing.md) — this flavor ships engine-proven but flavor-untested until then, and the README says so.
