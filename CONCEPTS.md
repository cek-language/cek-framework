# Concepts

Six core concepts before opening all of [LAW.md](LAW.md). Not a tutorial ([START.md](START.md)), not a second axiom book. Frozen names: [VOCABULARY.md](VOCABULARY.md). Kernel-author rules: [PRACTICE.md](PRACTICE.md).

## Six core concepts

- **Cap.** Permission to submit a class of Intent. Mint is Host-side; session, receipt, and trace are not Caps. [LAW.md §5](LAW.md#5-cap) · [EXPLAIN.md — Why Cap-only](EXPLAIN.md#why-cap-only) · [refuse path](diagrams/06-refuse-path.svg)
- **Intent + Result{Ops}.** An Intent is a sealed ask under a Cap; the Host answers with a Result whose carry-out is ordered Ops (data, not the language name). Peer apply is the mutation path for those Ops. [LAW.md §6](LAW.md#6-intent-result-ops) · [EXPLAIN.md — Why Ops-only](EXPLAIN.md#why-ops-only) · [Path](diagrams/01-path.svg)
- **Host ≠ Peer.** Host decides: mint/verify Cap, dispatch, lineage, project, Result. Peer carries out: apply Ops under profile. [LAW.md §4](LAW.md#4-host-and-peer) · [EXPLAIN.md — Why Host ≠ Peer](EXPLAIN.md#why-host--peer) · [Host ≠ Peer](diagrams/02-host-peer.svg) · [PSEUDOCODE.md](PSEUDOCODE.md) · [TOPOLOGY.md](TOPOLOGY.md)
- **Activity + lineage + reverse.** Activity bounds work that opens, runs, and ends; lineage records causes so reverse on end or revoke is a defined story (inverse, compensation, or mark non-reversible) — not perfect undo. [LAW.md §8](LAW.md#8-activity-and-context) · [LAW.md §9](LAW.md#9-lineage-and-reverse) · [EXPLAIN.md — Why reverse ≠ perfect undo](EXPLAIN.md#why-reverse--perfect-undo) · [authorized vs landed](diagrams/04-authorized-landed-reverse.svg)
- **trace ≠ Cap.** A trace groups related Intents. It does not grant permission, execute, or undo; resume uses fresh Caps. [LAW.md §10](LAW.md#10-trace) · [EXPLAIN.md — Why trace ≠ Activity](EXPLAIN.md#why-trace--activity) · [Cap ≠ trace ≠ Activity](diagrams/03-cap-trace-activity.svg)
- **Baseline.** The permanent shared contract every correct Host/Peer pair supports. profile only negotiates apply ability; it never grants Cap authority. [LAW.md §11](LAW.md#11-baseline-profile-negotiation) · [EXPLAIN.md — Why Baseline permanence](EXPLAIN.md#why-baseline-permanence) · [layers](diagrams/05-layers.svg)

## Next

- Practice (kernel authors): [PRACTICE.md](PRACTICE.md)
- Topology / multiplicity: [TOPOLOGY.md](TOPOLOGY.md)
- Submit / apply order (not law): [PSEUDOCODE.md](PSEUDOCODE.md)
- Tutorial walk: [START.md](START.md)
- Why the splits: [EXPLAIN.md](EXPLAIN.md)
- Map: [README.md](README.md)
