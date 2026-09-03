# Kill criteria — when it is not CEK

An implementation, fork, or “CEK-inspired” system **may not claim CEK alignment** if any of the following hold.

Changing these criteria is a charter amendment.

Source: [bitplorer/cek-framework](https://github.com/bitplorer/cek-framework) `KILL-CRITERIA.md`, bound by that repo’s `CHARTER.md` and `CORE/19-conformance.md`.

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
| **K14** | Compatibility claim without tests for Cap reject and reverse-on-end (see CORE/19 families) |

---

## Still allowed (not kill)

- Incomplete domain Op catalogs
- Missing optional features (idempotency bind, apply receipts) on Baseline-only deployments
- Multiple Host / Peer processes
- L7 bugs under a *valid* Cap (constrained, but possible)
- Stronger L6 policy than Baseline
- A runtime that is **narrower** than law (missing optional grouping, receipts, or rich Activity / Context), so long as it does not violate K1–K14 on the paths it does implement

---

## Defaults when unsure

| Situation | Do |
|-----------|-----|
| Authority unclear | Refuse |
| Unknown optional meta | Ignore |
| Peer can’t do rich Ops | Lower to Baseline |
| Undo impossible | Mark non-reversible; don’t fake success |
| Multi-step group | **trace** (still Cap each step) |
| Partial apply | reverse prefers **landed** Ops if a receipt exists |
| Compensation | recovery Cap; else mark non-reversible |

There is no path of “just this once ambient allow.”

---

## Use

- Gate marketing and conformance badges.
- Required behavior families for a CEK-compatible claim are listed in [LAW.md](LAW.md) (conformance).
- Vocabulary hygiene: [VOCABULARY.md](VOCABULARY.md).
