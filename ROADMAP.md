# Roadmap

Where this packet is headed, by theme. The [issue tracker](https://github.com/keng009/fulcra-raise-memory/issues) is the source of record — this page is the map. Nothing here is a promise with a date; items gated on platform capabilities ship only when those are live (CONTRIBUTING rule 3).

## Now — first live run, then v0.1.0

This packet ships engine-proven, flavor-untested ([testing.md](docs/testing.md)). The release gate is [#1](https://github.com/keng009/fulcra-raise-memory/issues/1): a full `raise-demo` session through Claude's real zip-upload flow, and a `raise-memory` snapshot → commit → veto run on a real account. Plus a fresh-eyes review pass of the founder vocabulary and claims ([#2](https://github.com/keng009/fulcra-raise-memory/issues/2)). (CI is live: `validate` runs on every push and is a required check on main.)

## Adapters under this flavor

The capability-based adapter layers came over from the fork point; none is exercised under `/raise/` yet ([#3](https://github.com/keng009/fulcra-raise-memory/issues/3)). Founder-relevant order: Notion and HubSpot trackers first, then Attio and Affinity; messaging paste tier for the channels investors actually reply on (WhatsApp, LinkedIn, iMessage).

## Toward automatic — without losing consent

- **Scheduled message-sweep digest** ([#5](https://github.com/keng009/fulcra-raise-memory/issues/5)): the behavior is now specified in the full skill (Tend rule 5) — investors go cold in DMs, not email; what remains is the live scheduled run that promotes it from designed to tested.
- **Notes on the fund's deal/opportunity object** ([#6](https://github.com/keng009/fulcra-raise-memory/issues/6)): each tracker's own object model, never touching fields or stages.
- Zero-touch auto-commit stays out of scope until its own ADR (consent-posture change, per-user opt-in).

## Raise-specific features — earned, not guessed

This fork exists so founder features can diverge from the investor sibling (ADR-0007). Candidates will come from real raise usage — momentum views per round stage, investor-update drafting from stored touchpoints, data-room follow-up tracking — and get scoped as issues when a real user (starting with the maintainer's clients) needs them. Nothing lands as roadmap theater.

## The sibling

[fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory) serves investors managing deal flow — the origin of this engine, with the live-test evidence and its own ROADMAP.md (in [the sibling repo](https://github.com/keng009/fulcra-dealflow-memory) — on the v0.3.0 branch until PR #28 merges). Features diverge by ICP; engine fixes cherry-pick.
