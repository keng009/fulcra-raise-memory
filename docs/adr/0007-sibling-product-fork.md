# This packet is a deliberate product fork of fulcra-dealflow-memory

This packet serves founders actively raising. Its siblings — [fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory) (investors managing deal flow; the engine's origin) and [fulcra-sales-memory](https://github.com/keng009/fulcra-sales-memory) (founders selling their own product; derived 2026-08-31) — serve different ICPs with different vocabularies and, over time, different features. This repo was derived 2026-08-27 from the engine (contract v3.1: snapshot-first flow, per-source dedupe keys, the veto invariant, review queue, CRM and messaging adapters) with a fresh public history (ADR-0001) and a disjoint Fulcra namespace (`/raise/`, `Raise Touchpoint` — the siblings use `/dealflow/` + `Dealflow Touchpoint` and `/sales/` + `Sales Touchpoint`) so all three products can run on one account.

**Decision**: the two repos diverge intentionally. There is no shared module, no cross-repo byte-alignment rule, and no obligation to keep contracts identical. Engine-level fixes (dedupe, veto, healing) get cherry-picked between siblings by judgment when they apply; product-level features do not.

**Status**: accepted (2026-08-27, Nick).

**Consequences**: byte-alignment (CONTRIBUTING rule 1) remains strictly INTRA-repo; when adopting an engine fix from the sibling, adapt it to this contract rather than copying bytes; this repo's claims stand on its own [testing.md](../testing.md) — the sibling's live tests are evidence for the shared engine's design, never for this packet's behavior.
