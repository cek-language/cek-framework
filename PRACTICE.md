# Practice — when designing a kernel

Short rules for kernel authors. Not law, not a second axiom book. The alignment gate is [KILL.md](KILL.md). How to claim alignment: [HOWTO-ALIGN.md](HOWTO-ALIGN.md). Concepts: [CONCEPTS.md](CONCEPTS.md).

## When designing a kernel

1. **Cap-only gate.** Shared-world change waits on a verified Cap (documented Host-only bootstrap mint is the exception). Instant miss: [KILL.md K1](KILL.md#instant-disqualification).
2. **Ops-only boundary.** Kernel-boundary mutation is listed as ordered Ops (plus lineage accounting). Instant miss: [KILL.md K2](KILL.md#instant-disqualification).
3. **Peer never mints.** Peer apply only — no root mint, no invented business truth. Instant miss: [KILL.md K3](KILL.md#instant-disqualification).
4. **reverse story ≠ perfect undo.** Activity end and Cap revoke reverse lineage (inverse, compensation under a recovery Cap, or mark non-reversible). Do not report clean reverse when that failed. [CHARTER.md Stability guarantees](CHARTER.md#stability-guarantees) · [KILL.md K12](KILL.md#soft-fail).
5. **Baseline permanence.** Do not silently break Baseline for correct old Host/Peer pairs. Instant miss: [KILL.md K9](KILL.md#instant-disqualification).

Walk those gates, then claim: [HOWTO-ALIGN.md](HOWTO-ALIGN.md).

## Next

- Concepts: [CONCEPTS.md](CONCEPTS.md)
- Alignment how-to: [HOWTO-ALIGN.md](HOWTO-ALIGN.md)
- Map: [README.md](README.md)
