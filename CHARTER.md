# Charter — freeze and amendment

This repository is the published Single Source of Truth for CEK-framework **law**.

**Locked here:** [LAW.md](LAW.md) (axioms, layers, Host/Peer, Cap, lineage, Baseline, hardening), [README.md](README.md) (entry; the A1–A10 table must remain identical to LAW §2), [VOCABULARY.md](VOCABULARY.md), [KILL.md](KILL.md), this file.

Optional drafts are not law until adopted by amendment. Editorial clarity that does not change meaning is not an amendment. README axiom-table drift is not editorial.

bitplorer/cek-framework at commit [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f) is a **historical freeze** (provenance), not a living CORE. This repository is the published SSoT. [IMPLEMENTATION.md](IMPLEMENTATION.md) is encoding notes, not locked law.

---

## May change without amendment

- L5 domain drivers and Op namespaces
- L7 application handlers and product logic
- L6 policy that does **not** relax A1–A10
- Additive optional meta Peers may ignore
- Conformance vector *additions* that clarify existing law
- Editorial wording that does not change meaning

---

## Requires amendment

- Any change to axioms
- Any rename of a frozen kernel concept (primary name)
- Any new ambient authority path
- Treating **trace** as authority or as execute
- Breaking Baseline interop for correct old Host/Peer pairs
- Introducing a **third conceptual parent that redefines L0–L2**
- **Collapsing Host and Peer into one privileged role**
- Widening bootstrap beyond Host-only minimal mint

---

## Amendment process

1. State the change in frozen vocabulary only (canonical speech).
2. Classify layer and change type ([LAW.md](LAW.md) § change).
3. Show axiom impact (none, or explicit axiom edit).
4. Show naming impact (no synonym drift).
5. Show Baseline impact (still holds, or major version + dual-speak).
6. Re-run invariants and update conformance families ([LAW.md](LAW.md) § conformance).
7. Record the amendment in the log below.

---

## Bindings

Implementations that claim CEK alignment must honor:

| Binding | Where |
|---------|--------|
| Vocabulary freeze; Baseline interop; fail closed; accountable end | This charter + [LAW.md](LAW.md) |
| Kill criteria | [KILL.md](KILL.md) |
| Security | [LAW.md](LAW.md) § security, § bootstrap |
| Dual vocabulary ban | [VOCABULARY.md](VOCABULARY.md) — tutorial gloss once; no second official names |

**Stability guarantees.** Primary kernel names do not rename. Same name keeps the same intention. New power is additive or versioned. Authority fails closed. Ending an Activity or revoking a Cap has a **defined reverse story**: inverse where possible, else compensation under a recovery Cap, else an explicit non-reversible mark. That story is not a promise of perfect undo. Kernel changes follow this process.

**Stability non-guarantees**

| Non-guarantee | Note |
|---------------|------|
| Eternal domain Op catalogs | Domains evolve at L5 |
| Single implementation forever | Multiple Host/Peer implementations allowed |
| Perfect undo of the external world | Compensation and non-reversible marks exist |
| Transport or crypto agility details | Conceptual binds matter; algorithms may evolve |
| Absence of L7 bugs | App handlers can still be wrong *under* Caps |

---

## Amendment log

| Date | Change | Rationale |
|------|--------|-----------|
| 2026-09-03 | Publish this repo as SSoT law (README, LAW, VOCABULARY, KILL, CHARTER) | Distill of freeze `eca06befbd0f30e93c47481f7aab3fae66d5a57f`; no axiom invented or dropped |
