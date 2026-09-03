# CEK vocabulary

Official name of the law: **CEK** (Cap-Effect Meta-Language).

- **Ops** is the ordered carry-out list (data). Ops is **not** the language name.
- **Cap** is authority: permission to submit a class of Intent.
- **trace** is correlation only. It never grants, executes, or undoes.
- **flow** is rejected as a primary law name.

One concept, one name (A10, K10). Tutorial gloss once is allowed; it does not create a second official language.

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

Host / Peer support allow and carry out. Baseline / profile support permanence and negotiate-carry-out.

---

## Intention map

Every kernel noun and verb maps to exactly one row. **trace** does not ask, allow, carry out, bound, or undo.

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

**trace** answers which asks belong together. It does not answer who is allowed, what may be applied, or what must be undone. Each step remains Intent under Cap. Resume uses fresh Caps; a trace does not revive expired permission.

---

## Rejected primary names

| Rejected | Use instead |
|----------|-------------|
| **flow** | **trace** (correlation); **CEK** (the law) |
| Fiber | **Activity** |
| Floor | **Baseline** |
| run (execute or correlation) | **apply** / **trace** |
| thread | **Activity** |
| group / related (as correlation name) | **trace** |
| history / record (as cause trail) | **lineage** |
| plugin (ambient load) | **part** |
| command (as the ask) | **Intent** |
| token (as authority) | **Cap** |
| Ops as language name | **CEK** |
| Ceksy, `c+ek`, stylized aliases | **CEK** |
| Client / Server as L1 roles | **Host** / **Peer** |
| permission (alone) | **Cap** |
| effects (as emission noun) | **Ops** |

Casual English (“related Intents share a trace”) is allowed. It does not mint a kernel noun **related**.

**limit** is the public restriction verb. **isolate** is the structural Context-slice operation. Do not collapse them into one official name.

Concepts vs encodings: the framework names concepts. Identifiers and token encodings are not additional kernel nouns. Field names are implementation, not vocabulary.
