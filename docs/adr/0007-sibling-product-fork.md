# This packet is a deliberate product fork of fulcra-dealflow-memory

This packet serves founders actively raising. Its sibling, [fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory), serves investors managing deal flow — a different ICP with a different vocabulary (founders and startups instead of investors and funds, "founders going quiet" instead of "investors going cold") and, over time, different features. This repo was derived 2026-08-27 from the sibling's engine (contract v3.1: snapshot-first flow, per-source dedupe keys, the veto invariant, review queue, CRM and messaging adapters) with a fresh public history (ADR-0001) and a disjoint Fulcra namespace (`/raise/`, `Raise Touchpoint` — the sibling uses `/dealflow/`, `Dealflow Touchpoint`) so both products can run on one account.

**Decision**: the two repos diverge intentionally. There is no shared module, no cross-repo byte-alignment rule, and no obligation to keep contracts identical. Engine-level fixes (dedupe, veto, healing) get cherry-picked between siblings by judgment when they apply; product-level features do not.

**Status**: accepted (2026-08-27, Nick).

**Consequences**: byte-alignment (CONTRIBUTING rule 1) remains strictly INTRA-repo; when adopting an engine fix from the sibling, adapt it to this contract rather than copying bytes; this repo's claims stand on its own [testing.md](../testing.md) — the sibling's live tests are evidence for the shared engine's design, never for this packet's behavior.
