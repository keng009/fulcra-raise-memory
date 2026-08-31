# Fulcra Raise Memory

Two Claude skills that give your fundraise a memory, on your own [Fulcra](https://fulcra.ai) account. Fulcra is a personal context platform: your account holds your data — calendars, files, custom records — and any AI assistant you connect to it over MCP reads and writes that same account. Every investor conversation you log — a GP intro, an angel call, a partner meeting — is stored twice: a narrative entry you can read, and a typed record software can query. From there: recall before the next meeting ("prep me for Alex"), fund history ("have I talked to Meridian before?"), momentum review ("what moved this week", grouped by fund with stage changes per your notes), and a list of investors going cold (45+ days). Optional one-way copy into your CRM or tracker. Because the memory lives in your account rather than inside any one chat product, it persists across sessions and across assistants — the whole raise, remembered.

**Sibling packets**: [fulcra-dealflow-memory](https://github.com/keng009/fulcra-dealflow-memory) (investors managing deal flow — the engine's origin) and [fulcra-sales-memory](https://github.com/keng009/fulcra-sales-memory) (founders selling their own product) are the same engine flavored for different tables. All three can run on one account (disjoint `/dealflow/`, `/raise/`, and `/sales/` namespaces). See [ADR-0007](docs/adr/0007-sibling-product-fork.md).

## Which skill do I install?

| You want | Install | Commitment |
|---|---|---|
| A zero-commitment look — see the flow on your own month (or sample data), decide after | **`raise-demo`** | ~10 minutes; works on an empty account; nothing written until you say yes |
| The product — ongoing capture, meeting prep, weekly momentum, going-cold alerts, CRM sync | **`raise-memory`** | The daily workflow; picks up anything the demo stored, no migration |

Start with the demo if you're deciding; start with `raise-memory` if you're already sold. Both write the same formats to the same folder.

> **Pre-release note (this block is removed at the first release):** no release has been published yet — the "latest release" links below will work once v0.1.0 ships ([#1](https://github.com/keng009/fulcra-raise-memory/issues/1) is the gate). Until then, zip the skill folders yourself as the install steps describe.

## See it in 10 minutes — `raise-demo`

One guided session — about ten minutes once installed. The skill inspects your Fulcra data catalog, builds a **read-only snapshot of your last 30 days of investor conversations** from whatever you've connected (calendar, meeting tools), saves it as memory on a single yes — files versioned; the full skill adds a veto flow that can strike any saved item later — and generates a prep brief from what it just stored. Nothing is written until you say so; with no sources connected, it falls back to capturing one conversation conversationally. Think of it as the hello-world; `raise-memory` below is the product.

1. Create a Fulcra account at [fulcra.ai](https://fulcra.ai) if you don't have one. An empty account is fine — the demo works without prior data.
2. In Claude, open **Customize → Connectors** and connect **Fulcra**.
3. Download `raise-demo.zip` from the [latest release](https://github.com/keng009/fulcra-raise-memory/releases/latest) *(none published yet — see the note above)* (or zip the `skills/raise-demo` folder yourself) and upload it in Claude under **Customize → Skills → + Create skill → Upload a skill**. If Skills isn't visible, enable it under **Settings → Capabilities** first.
4. Start a new chat and say: **"run the Fulcra raise demo"**.

## Make it your workflow — `raise-memory`

The ongoing version: log investor conversations as they happen, prep before meetings, review the week by fund, catch investors going cold before the round loses momentum.

1. Same Fulcra account and connector as above.
2. Download `raise-memory.zip` from the [latest release](https://github.com/keng009/fulcra-raise-memory/releases/latest) *(none published yet — see the note above)* (or zip the `skills/raise-memory` folder — its `references/` subfolder must travel inside the zip) and upload it the same way.
3. Say **"show me my last 30 days"**, **"log my call with Alex"**, **"have I talked to this fund before?"**, **"prep me for tomorrow"**, **"what moved this week"**, or **"which investors have gone cold"**.

Only the Fulcra connector is required. If calendar data is reachable (in your Fulcra account or via a Claude calendar connector), the skill detects and uses it: conversations get corroborated against real meetings, and "prep me for tomorrow" reads the actual calendar. If a transcript tool (Otter, Zoom, Fireflies) is connected, it can log meetings straight from transcripts. Paste an investor's WhatsApp, LinkedIn, or iMessage thread and "log this" captures it too. Nothing to configure — each session it states what it found.

Both skills write the same formats to the same `/raise/` folder in your account, so anything you logged during the demo is picked up by the full skill as-is. No migration.

## What this looks like in real life

![Your raise scattered across silos flows into one Fulcra memory that every assistant and your CRM can read](docs/assets/raise-map.svg)

A raise generates exactly the interaction sprawl this pattern was built for: intro calls booked by three different schedulers, partner meetings with transcripts, angels who only answer on WhatsApp, associates who DM on LinkedIn — and a founder who has to remember what every one of them said, wanted, and promised, for months, while building the company. The memory lives in your account, not a vendor's, so it survives tool changes and works from every assistant you use.

Illustrative output — the demo generates one of these from your own logged conversation:

> **Prep brief — Alex Rivera (Meridian Capital)**
> **Who:** GP at Meridian; intro call in August. Fintech-focused, moves fast, asked sharp metrics questions.
> **Last touchpoint:** call, Aug 20 — seed round discussion.
> **Stage noted (last):** diligence — per your notes.
> **Open follow-ups:** you owe them the deck and current metrics.
> **Talking points:** the fintech-partner intro Alex offered; the metrics they flagged as the deciding factor.

## Already have a CRM or investor tracker?

Keep it. If your Claude has CRM tools connected, `raise-memory` offers — once per session, never requires — to copy each logged conversation into it as a note on the matched contact. One-way, notes and tasks only: it never creates contacts and never edits fields or stages, so your tracker stays the system of record for the round. Adapters are capability-based — see [`skills/raise-memory/references/crm-sync.md`](skills/raise-memory/references/crm-sync.md) for the tiers, the tested reference (Attio, in the sibling packet's engine), and the 10-minute protocol for adding your own CRM. Your CRM is never mirrored into Fulcra: the memory holds the investors you're actually talking to, not a copy of a thousand-fund list. (Individual CRM notes about those investors can be imported as touchpoints on your say-so — selection, never mirroring.)

## Why Fulcra?

Because a raise runs for months across dozens of threads, and memory that lives inside one chat product is a silo. These skills use Fulcra as the account-level store that makes the rest honest: versioned files you can read, typed records software can query, and — the load-bearing part — **the same memory readable from every assistant you connect over MCP**. Where Fulcra is necessary, where it's merely convenient, and where the platform has limits the skills admit to: [docs/why-fulcra.md](docs/why-fulcra.md).

## Privacy

These skills are instruction files: no backend of their own, no telemetry, nothing that reports back to the authors. They write to exactly two places in your Fulcra account: files under `/raise/`, and typed records in the **Raise Touchpoint** data type they create — plus, only if you accept the offer, notes in your own CRM. Reads are wider but write nothing: with a calendar, transcript tool, or CRM connected, the snapshot reads recent events, transcripts, and CRM notes in its window to build what it shows you — whether or not you ever accept CRM sync. They never write credentials or secrets to any file and never send email or messages on your behalf: ask for a follow-up and you get a clearly labeled draft. File deletes in Fulcra are soft; typed records have no per-record delete — a vetoed item is excluded from every read these skills perform but remains stored (other assistants reading the account should honor the `## Vetoed keys` list, which the contract documents), and the skills say so rather than pretending otherwise.

## Status — honest and current

This packet was forked 2026-08-27 from the [deal-flow sibling](https://github.com/keng009/fulcra-dealflow-memory)'s engine, whose write paths are live-tested with dated evidence (snapshot→commit→veto, stable per-source dedupe keys, CRM import + circularity, partial-failure healing — see its [testing matrix](https://github.com/keng009/fulcra-dealflow-memory/blob/main/docs/testing.md)). **This flavor's own surfaces have not yet been run live** — see [docs/testing.md](docs/testing.md) for exactly what has and hasn't. Until its first live run, treat this packet as engine-proven, flavor-untested.

---

MIT — see [LICENSE](LICENSE). Maintained by Nick Kengmana, Fulcra.
