# CEK — Cap-Effect Meta-Language

**The rulebook for who may change a shared world, how the change is listed, and how it is undone.**

CEK exists so this question stays answerable: *who authorized this write, and how is it undone?*

Shared-world change is **Cap-only**, **Ops-only**, and honestly reversible.

This repository is **law and vocabulary only** — not a package, crate, or runtime. It does not ship Host or Peer kernels. Implementations that claim CEK alignment live elsewhere and must satisfy this law; they do not amend it by shipping code.

The official name of the law is **CEK** (Cap-Effect Meta-Language). **Ops** is the ordered effect list (data), not the language name.

Source of the locked charter: [bitplorer/cek-framework](https://github.com/bitplorer/cek-framework) (`main`, CORE 00–27). This repo restates that law in human-readable form. If a sentence here and that charter diverge, **the charter wins**.

Build kernels: [cek-runtime](https://github.com/bitplorer/cek-runtime) · [cek-python](https://github.com/bitplorer/cek-python) · [cek-hw](https://github.com/bitplorer/cek-hw) (L5 apply, not a Host).

| Start here | Link |
|------------|------|
| Full law | [LAW.md](LAW.md) |
| Frozen names | [VOCABULARY.md](VOCABULARY.md) |
| Still CEK? | [KILL.md](KILL.md) |

---

## One-line path

**Mint Cap → submit Intent → apply Ops → bound in Activity → record lineage → reverse on end → group with trace → keep Baseline.**

```text
mint Cap → submit Intent → Host verify
        → Result{Ops} → Peer apply
        → Activity bounds work → lineage records causes
        → end/revoke → reverse (or mark non-reversible)
        → trace only groups steps → Baseline always still works
```

Refuse a bad Cap. Zero mutate Ops. Never treat **trace** as permission.

---

## Nouns and verbs

| Noun | Meaning |
|------|---------|
| **Cap** | Permission ticket to submit a class of Intent |
| **Intent** | The sealed ask under a Cap |
| **Host** | Decides — verify Cap, lineage, `Result{Ops}` |
| **Peer** | Only applies Ops |
| **Ops** | Ordered effects as **data** |
| **Result** | Host answer to an Intent |
| **Activity** | Bounded work with a lifetime that can end and reverse |
| **Context** | Mediated visibility — not ambient authority |
| **lineage / reverse** | Honest cancel and revoke |
| **Baseline** | Classic Ops that never silent-break |
| **profile** | What this Peer can apply — never Cap authority |
| **part** | Composition unit loaded under a Cap |
| **trace** | Groups related Intents — **never** permission |

| Verb | Job |
|------|-----|
| **mint** | Create a Cap |
| **submit** | Send an Intent under a Cap |
| **apply** | Carry out Ops |
| **inject** | Declare what an Activity requires |
| **limit** | Restrict what may be seen or done |
| **isolate** | Separate a Context slice |
| **reverse** | Undo lineage / end Activity cleanly |

One concept, one name. Rejected synonyms and encoding notes: [VOCABULARY.md](VOCABULARY.md).

---

## Axioms (A1–A10)

These are constitutional. Features may not relax them without a charter amendment.

| ID | Name | Statement |
|----|------|-----------|
| **A1** | Cap-only truth | The only proof of authority is a verified Cap. Sessions, mesh membership, and ambient Context never suffice alone. |
| **A2** | Ops-only effects | The only side-effects at the kernel boundary are explicit ordered Ops. |
| **A3** | Lineage accountability | Every carried-out change under a revocable Cap or endable Activity is recorded in lineage. |
| **A4** | Baseline permanent | The Baseline contract never silently breaks; power is additive or explicitly versioned. |
| **A5** | Fail closed | Failed Cap verification, missing required once-store, or required lineage write failure refuses the action. |
| **A6** | Trace ≠ authority | A trace only groups Intents; it never grants permission. |
| **A7** | Peer unprivileged | A Peer applies Ops; it does not mint root Caps or invent business truth. |
| **A8** | Attenuation monotonic | `limit` and `isolate` only narrow authority or visibility; they never widen it. |
| **A9** | Composition authorized | Opening an Activity or loading a part is Cap-gated (or uses an explicit minimal bootstrap root). |
| **A10** | One concept, one name | The kernel has no synonyms; documentation and code use the same primary names. |

Full statements, notes, and fail-closed rules: [LAW.md](LAW.md).

---

## This repo at a glance

| This repo **is** | This repo **is not** |
|------------------|----------------------|
| Frozen vocabulary and axioms | An npm / cargo / pip library |
| What “correct CEK” means | Runnable Host / Peer |
| Design review checklist | Wire codecs, crypto, or UI widgets |

| | Owns | Does *not* own |
|--|------|----------------|
| **This repo** | Meanings, axioms, frozen names, Host/Peer *role* law, kill criteria | Runnable kernels, wire codecs, crypto, Op catalogs, crates, CI |
| **Host** | Mint, verify, lineage, Result | Apply as mutation; Peer-said “I am allowed” |
| **Peer** | Apply Ops under profile | Root mint; business truth |
| **Cap** | Permission to submit a class of Intent | Session, TLS, trace, Activity lifetime |
| **trace** | Group related Intents | Permission |

| Pain | Failure mode | CEK rule |
|------|--------------|----------|
| Agent/UI “just writes” DOM, DB, or device | No clear permission | Shared change needs a **Cap** |
| Effects hidden in callbacks | Hard to replay or bound | Boundary effects only as **Ops** |
| Session / trusted peer / admin = power | Ambient authority | **Host** verifies; **Peer** applies |
| Cancel / unload / revoke | Fake or partial cleanup | **lineage** + **reverse** (or mark) |
| New release breaks old clients | Flag-day interop | **Baseline** stays valid |
| Multi-step flow treated as login | Correlation as permission | **trace** groups; Cap still required |

**Fits:** agents with tools, collab/UI channels, devices — anywhere “who authorized this write?” must stay answerable.

**Skip:** pure local apps with no cross-boundary authority story.

---

## File map

| Path | Role |
|------|------|
| [README.md](README.md) | Overview, axioms, boundary, non-goals |
| [LAW.md](LAW.md) | Human-readable law restated from CORE 00–27 |
| [VOCABULARY.md](VOCABULARY.md) | Frozen terms and rejected synonyms |
| [KILL.md](KILL.md) | Alignment / kill criteria |

---

## Implementation boundary

This repo states **law**. It does not ship kernels.

| Here | Elsewhere |
|------|-----------|
| Meanings, axioms, kill criteria | This repository |
| Build Host / Peer, contract, CI | [cek-runtime](https://github.com/bitplorer/cek-runtime) |
| Python Host + surface | [cek-python](https://github.com/bitplorer/cek-python) |
| L5 `hw.*` apply (not a Host) | [cek-hw](https://github.com/bitplorer/cek-hw) |

Exactly two L1 kernels: **Host** (decide) and **Peer** (apply). There is no third kernel. Caller, bootstrap, lineage store, recovery Cap, profile, transport, and conformance harness are not kernels.

A process may embed both roles as separate boundaries. Mint must not live inside pure apply. Many implementations may exist; multiplicity does not add roles.

L0–L2 are law. L4–L7 (profiles, domain Ops, optional policy, product logic) may move without amending axioms. Encoding of Caps, transports, and crate layout are implementation — not law.

Implementation gaps in today’s reference runtime are labeled **IMPLEMENTATION NOTE** in [LAW.md](LAW.md). They are not law. In particular, `cek-runtime` is narrower than law in some areas (trace is a field only; lineage is keyed by `activity_id`; optional stamp is session apply-set / profile encoding).

---

## Explicit non-goals

This documentation (and the core law it restates) does **not**:

- Choose specific Cap cryptography
- Mandate one process topology (browser/server, in-process, WASM, …)
- Define all domain Ops
- Replace general-purpose programming languages
- Freeze implementation languages, crate layout, CI, or isolation technology
- Treat wire field paths, stamps, or session encodings as kernel concepts
- Ship runnable Host / Peer code

Those belong in implementation repos. They must not silently redefine Intent, Cap, or Baseline.

---

## How to use this repo

1. Read this page, then [LAW.md](LAW.md).
2. Use only the frozen vocabulary ([VOCABULARY.md](VOCABULARY.md)).
3. Check designs against [KILL.md](KILL.md).
4. Implement in [cek-runtime](https://github.com/bitplorer/cek-runtime) or [cek-python](https://github.com/bitplorer/cek-python). Domain apply packs (for example [cek-hw](https://github.com/bitplorer/cek-hw)) stay L5 — they are not Hosts.

**Goals:** Cap-only · Ops-only · fail closed · lineage / reverse · Baseline · frozen names.

**Non-goals:** Ship code, wire-as-law, UI catalogs.
