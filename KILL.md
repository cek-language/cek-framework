# Kill criteria — when it is not CEK

An implementation, fork, or “CEK-inspired” system **may not claim CEK alignment** if any of the following hold.

This page is a reader-path copy of the charter kill list. Authority: [KILL-CRITERIA.md](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/KILL-CRITERIA.md) at commit [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f). Changing these criteria is a charter amendment in bitplorer/cek-framework ([CHARTER](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHARTER.md)), not an edit that this distill can make on its own. If this page and that file diverge, **CORE / KILL-CRITERIA wins**.

K14 is the CORE/19 families in the charter. This repo does not add a second test suite.

---

## Instant disqualification

| ID | Criterion |
|----|-----------|
| **K1** | Shared-world change is allowed **without** a verified Cap (except documented Host-only bootstrap mint) |
| **K2** | Kernel boundary emits free side-effects outside ordered **Ops** (and lineage accounting) |
| **K3** | **Peer** can mint **root** Caps or is treated as source of business truth |
| **K4** | **trace** (or correlation id) is accepted as permission or session authority |
| **K5** | Cap verification is best-effort: failures still apply mutate effects |
| **K6** | Single-use / once constraints are skipped when the required store is down (must **refuse**) |
| **K7** | **limit** / attenuation can **widen** rights beyond the parent Cap / Context |
| **K8** | Activity / part composition loads as ambient **plugin** power without Cap (or bootstrap) |
| **K9** | Baseline interop is silently broken for correct old Host / Peer pairs |
| **K10** | Primary kernel vocabulary is renamed or synonym-forked as a second official language |

---

## Soft fail

Not a CEK-compatible claim until fixed:

| ID | Criterion |
|----|-----------|
| **K11** | Revocable Cap or endable Activity mutates shared world with **no** lineage |
| **K12** | Activity end or Cap revoke reports success while reverse failed, without **non-reversible** mark |
| **K13** | Compatibility claim without Baseline-lowering path for unknown rich Ops |
| **K14** | Compatibility claim without tests for Cap reject and reverse-on-end (see [CORE/19](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/19-conformance.md)) |

---

## Still allowed (not kill)

- Incomplete domain Op catalogs
- Missing optional PROPOSALS (idempotency, receipts) on Baseline-only deployments
- Multiple Host / Peer processes
- L7 bugs under a *valid* Cap (constrained, but possible)
- Stronger L6 policy than Baseline

Corner defaults (refuse / ignore / lower / mark / bound / profile) live in [LAW.md](LAW.md) from CORE/24, not here.

---

## Use

- Gate marketing and conformance badges.
- Bound by [CHARTER](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHARTER.md) kill-criteria and stability bindings.
- Vocabulary hygiene: [VOCABULARY.md](VOCABULARY.md).
