# CEK vocabulary

Frozen kernel names. Tutorial gloss is allowed once; it does not create a second official language.

The official name of the law is **CEK** (Cap-Effect Meta-Language).

- **Ops** is effects (the ordered carry-out list as data). Ops is **not** the language name.
- **Cap** is authority (permission to submit a class of Intent).
- **trace** is correlation only. It never grants, executes, or undoes.
- **flow** is rejected as a primary law name.

If documentation or code needs a second word for one of these jobs, that is a naming defect (axiom **A10**, kill criterion **K10**), not a synonym.

**Reader path.** Source: [bitplorer/cek-framework](https://github.com/bitplorer/cek-framework) commit [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f) — [`CORE/04-vocabulary.md`](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/04-vocabulary.md), [`CORE/00-overview.md`](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/00-overview.md), [`META/04-naming-law.md`](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/META/04-naming-law.md), [`CHOICES.md`](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHOICES.md), [`GLOSSARY.md`](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/GLOSSARY.md). If this page and CORE diverge, **CORE wins**. This distill is not independently amendable law.

---

## Frozen nouns

| Name | Meaning |
|------|---------|
| **Intent** | Sealed ask to change something |
| **Cap** | Permission to submit that Intent |
| **Ops** | Ordered changes that may be carried out |
| **Result** | Answer to an Intent |
| **Activity** | Bounded work that starts, ends, and can be reversed |
| **Context** | What an Activity is allowed to see (not ambient authority) |
| **lineage** | Cause trail under Cap / Activity for undo |
| **Host** | Side that verifies Cap and decides truth |
| **Peer** | Side that only applies Ops |
| **Baseline** | Permanent shared contract |
| **profile** | Declared Peer apply abilities |
| **part** | Composition unit loaded under a Cap |
| **trace** | Correlation of related Intents (not power) |

---

## Frozen verbs

| Name | Meaning |
|------|---------|
| **mint** | Create a Cap |
| **submit** | Send an Intent under a Cap |
| **apply** | Carry out Ops |
| **inject** | Declare what an Activity requires |
| **limit** | Restrict what may be seen or done |
| **isolate** | Separate a Context slice |
| **reverse** | Undo lineage / end Activity cleanly |

---

## Supporting terms (not extra kernel nouns)

These names are frozen as *supporting* vocabulary. They do not add a seventh intention.

| Term | Definition |
|------|------------|
| **authorized set** | Ops the Host put in the Result after Cap verify |
| **landed set** | Ops the Peer actually applied successfully |
| **apply receipt** | Peer report of the landed set (not a Cap) |
| **idempotency bind** | Optional claim so retried asks share one logical cause |
| **recovery Cap** | Narrow Cap used to submit compensation during reverse |
| **manifest** | Compatibility handshake (law generation, profiles, fail-closed facts). Never grants Cap authority. |
| **meta-Cap** | Cap that mints, limits, or revokes other Caps — still Cap-gated |
| **bootstrap root** | Explicit, minimal, Host-side origin of Caps — not ambient Peer power |

Host / Peer / Baseline / profile support the same intention rows: Host and Peer support allow and carry out; Baseline and profile support permanence and negotiate-carry-out.

---

## Intention map

Every kernel noun and verb maps to exactly one row. **trace** does not participate in ask / allow / carry out / bound / undo.

| Intention | Concepts |
|-----------|----------|
| Ask | Intent, submit |
| Allow | Cap, mint |
| Carry out | Ops, apply, Result |
| Bound | Activity, Context, inject, limit, isolate, part |
| Remember / undo | lineage, reverse |
| Correlate only | trace |

---

## Cap vs trace vs Activity

| Concept | Grants permission? | Groups steps? | Owns lifetime undo? |
|---------|--------------------|---------------|---------------------|
| **Cap** | Yes | No | Via lineage when revocable |
| **trace** | No | Yes | No |
| **Activity** | No | No | Yes (reverse lineage on end) |

**trace** answers: *which asks belong together?* It does not answer *who is allowed?*, *what may be applied?*, or *what must be undone?*

Each step remains Intent under Cap. Resume of multi-step work uses fresh Caps under policy; a trace does not revive expired permission.

---

## Rejected primary names

Do not use these as official kernel names (even as “the other word for” a frozen concept):

| Rejected | Why |
|----------|-----|
| **flow** | Product / engine collision; rejected as the correlation (and as the primary law) name. Use **trace** to group steps; use **CEK** for the law. |
| Fiber | Unclear job; replaced by **Activity** |
| Floor | Unclear permanence; replaced by **Baseline** |
| run | Collides with apply / execute; rejected as execute *and* as correlation |
| thread | OS collision; wrong mental model |
| group / related | Too generic as the correlation concept |
| history / record | Generic log, not an authority-linked cause trail. Use **lineage**. |
| plugin | Implies ambient load. Use **part** (Cap-gated). |
| command | Substitute for **Intent** |
| token | Substitute for **Cap** |
| Ops (as language name) | Ops is one kernel noun (carry-out list), not the whole law |
| Ceksy, `c+ek`, other stylized aliases | Synonym fork (A10 / K10); fail decades stability |
| Client / Server as L1 roles | Topology-bound. Roles are **Host** and **Peer**. |
| permission (alone) as Cap | Imprecise; **Cap** is the authority object |
| effects (as emission noun) | Clash with undo / effect-tracking language; the emission noun is **Ops** |

Casual English (“related Intents share a trace”) remains allowed. It does not mint a kernel noun **related**.

**limit** is the public restriction verb. **isolate** remains the structural Context-slice operation. Do not collapse them into a single official name.

---

## Concept vs encoding

The framework names **concepts**. Implementations may use identifiers and token encodings; those are not additional kernel concepts.

| Level | Example |
|-------|---------|
| Concept | **trace**, **Cap**, **Activity**, **profile** |
| Runtime / wire identifier | an identifier string that refers to a trace, Cap token bytes, an Activity id |

Schemas may define identifiers without elevating them into the intention table. Field paths are not law.

### IMPLEMENTATION NOTE — encoding snapshot (cek-runtime)

Not law. Snapshot of [cek-runtime](https://github.com/bitplorer/cek-runtime) at commit [`50fe2af2c615ab31b35b24314915c2fb2635029f`](https://github.com/bitplorer/cek-runtime/tree/50fe2af2c615ab31b35b24314915c2fb2635029f).

**stamp** is session apply-set / profile encoding: a closed set of `(ns, name)` pairs (`PairSet`) used as the Peer’s apply-set source. That encoding is not a kernel concept, not authority, and not a Cap. Profile never grants Cap authority.

**trace** vs Activity identity in that snapshot:

- `Intent.trace` is a field only. There is no `TraceStore`, echo, or grouping API.
- Lineage is keyed by an Activity identifier (`activity_id`). Reverse runs on `end_activity`.
- `LineageEntry` records that Activity identifier, not a stored trace association.

Those encodings do not merge trace into Activity, and do not make an Activity identifier a Cap.

---

## Dual vocabulary ban

Documentation, design discussion, and code that claims CEK alignment use the **same** primary names as this file.

Tutorial gloss once is allowed. A second official name for Cap, Intent, Ops, Host, Peer, lineage, Baseline, or trace is not.
