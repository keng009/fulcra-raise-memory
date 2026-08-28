# Live-test matrix

Dated, sanitized record of what has actually been tested against live services. "Tested" claims in the README trace here. No user data appears below.

## Engine provenance (inherited design evidence, NOT this repo's behavior)

This packet was forked 2026-08-27 from [fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory) at contract v3.1. That repo's [testing matrix](https://github.com/keng009/fulcra-dealflow-memory/blob/main/docs/testing.md) carries dated live evidence for the shared engine design: Fulcra dual-write path, per-destination self-healing dedupe, snapshot→commit→veto end to end, stable calendar-event-id keys (first + second commit, zero duplicates), CRM-note import + circularity guard against Attio, and injected partial-failure healing.

Per ADR-0007, that evidence supports the **design** of this packet's engine — it is never evidence for this packet's **behavior**. The flavors differ (`/raise/` namespace, `Raise Touchpoint` type, investor-facing vocabulary), and every claim about this packet must trace to a row below.

## This flavor — nothing live-tested yet

| Surface | Status |
|---|---|
| `raise-demo` full session (zip upload → snapshot/capture → save → prep brief) | **Untested** |
| `raise-memory` snapshot → commit → veto on a real account | **Untested** |
| `/raise/` folder init, `Raise Touchpoint` create-if-absent, dual write + read-back | **Untested** |
| CRM adapters (any tier) under this flavor | **Untested** |
| Messaging capture (paste tier) under this flavor | **Untested** |

First release is gated on at least: one full `raise-demo` session through Claude's actual zip-upload UI, and one `raise-memory` snapshot→commit→veto run on a real account, both recorded here (dated, sanitized).
