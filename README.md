# CEK — Cap-Effect Meta-Language

**Who may change a shared world, how the change is listed, and how it is undone.**

Shared-world change is Cap-only, Ops-only, and honestly reversible. Official name: **CEK**. **Ops** is the ordered effect list (data), not the language name.

This repository is the **canonical published Single Source of Truth** for CEK-framework **law**. It is not a package, crate, or kernel. Implementations claim alignment against this law; they do not amend it by shipping code.

| Law | Vocabulary | Alignment | Amendment |
|-----|------------|-----------|-----------|
| [LAW.md](LAW.md) | [VOCABULARY.md](VOCABULARY.md) | [KILL.md](KILL.md) | [CHARTER.md](CHARTER.md) |

**Path.** Mint Cap → submit Intent → Host verify → Result{Ops} → Peer apply → Activity bounds work → lineage records causes → end/revoke → reverse (or mark non-reversible) → trace groups steps only → Baseline always still works.

---

## Nouns and verbs

| Noun | Meaning | Verb | Job |
|------|---------|------|-----|
| **Cap** | Permission to submit a class of Intent | **mint** | Create a Cap |
| **Intent** | Sealed ask under a Cap | **submit** | Send an Intent under a Cap |
| **Host** | Verifies Cap; decides; returns Result | **apply** | Carry out Ops |
| **Peer** | Applies Ops only | **inject** | Declare Activity requirements |
| **Ops** | Ordered effects as data; identity is `(ns, name)` | **limit** | Restrict what may be seen or done |
| **Result** | Host answer to an Intent | **isolate** | Separate a Context slice |
| **Activity** | Bounded work; reverse on end | **reverse** | Undo lineage / end cleanly |
| **Context** | Mediated visibility, not ambient authority | | |
| **lineage** | Cause trail under Cap / Activity | | |
| **Baseline** | Permanent interop contract | | |
| **profile** | Declared Peer apply ability — never Cap | | |
| **part** | Composition unit loaded under a Cap | | |
| **trace** | Correlation of Intents — never permission | | |

---

## Axioms A1–A10

Constitutional. Features may not relax them without [CHARTER](CHARTER.md) amendment.

| ID | Name | Statement |
|----|------|-----------|
| **A1** | Cap-only truth | The only proof of authority is a verified Cap. Sessions, mesh membership, and ambient Context never suffice alone. |
| **A2** | Ops-only effects | The only side-effects at the kernel boundary are explicit ordered Ops. |
| **A3** | Lineage accountability | Every carried-out change under a revocable Cap or endable Activity is recorded in lineage. |
| **A4** | Baseline permanent | The Baseline contract never silently breaks; power is additive or explicitly versioned. |
| **A5** | Fail closed | Failed Cap verification, missing required once-store, or required lineage write failure refuses the action. |
| **A6** | Trace ≠ authority | A trace only groups Intents; it never grants permission. |
| **A7** | Peer unprivileged | A Peer applies Ops; it does not mint root Caps or invent business truth. |
| **A8** | Attenuation monotonic | `limit` and `isolate` only narrow; they never widen. |
| **A9** | Composition authorized | Opening an Activity or loading a part is Cap-gated (or explicit Host bootstrap). |
| **A10** | One concept, one name | No kernel synonyms; docs and code use the same primary names. |

---

## Layers and roles

```text
L0  Law         axioms + Baseline
L1  Kernels     Host · Peer
L2  Bound work  Activity · Context · inject · limit · isolate · lineage · reverse · part
L3  Correlate   trace
L4  Negotiate   profile
L5  Drivers     domain Ops
L6  Policy      optional
L7  Application product logic
```

Exactly two L1 kernels. **Host** decides (mint, verify, lineage, project, Result). **Peer** applies Ops. There is no third kernel. Host and Peer must not collapse into one privileged role. Changing **trace** meaning (L3) is kernel meaning: major version + dual-speak ([LAW.md](LAW.md) § change).

L5–L7 and optional L6 that does not relax axioms may move without amendment. A third conceptual parent that redefines L0–L2 is forbidden.

| This repo **is** | This repo **is not** |
|------------------|----------------------|
| Published SSoT for CEK law | A package, crate, or runnable Host / Peer |
| Frozen names, axioms, kill criteria | Wire codecs, crypto, or domain catalogs |
| What “correct CEK” means | A surface programming language |

Kernels implement elsewhere. Domain apply catalogs stay L5 — they are not Hosts.

Provenance (not living CORE): distilled from bitplorer/cek-framework [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f).
