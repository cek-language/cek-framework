# CEK — Cap-Effect Meta-Language

**Who may change a shared world, how the change is listed, and how it is undone.**

Shared-world change stays *answerable*: who authorized it, how it is listed, and how it is undone.

Official name: **CEK**. **Ops** is the ordered effect list (data), not the language name.

**Status.** Law published. Kernels implement elsewhere.

## What this repo does

This repository publishes the canonical CEK **law**: frozen names, axioms, and kill criteria. It is not a package, crate, or kernel. Kernels implement elsewhere and claim alignment against this law; they do not amend it by shipping code.

Axioms live in [LAW.md §2](LAW.md#2-axioms). CHARTER lock: README must not drift from LAW.

## How it works

![Path](diagrams/01-path.svg)

1. Mint **Cap**, then submit **Intent**.
2. **Host** verifies and returns **Result{Ops}**.
3. **Peer** applies the Ops.
4. **Activity** bounds the work; **lineage** records causes.
5. **reverse** on end or revoke (or mark non-reversible). **trace** groups related Intents only.

## What you can achieve

CEK is the locked law of authorized change across boundaries: how programs ask, are allowed, carry out, bound, remember, and undo.

- **Cap**-only authority
- **Ops**-only effects
- **Activity** + **lineage** reverse story (defined reverse, not perfect undo)
- **trace** ≠ **Cap**
- **Baseline** permanence

Five-minute walk: [START.md](START.md).

## Leverage

Where **Host** decide vs **Peer** apply lives. Same two roles; placement is free. Not a third kernel. [TOPOLOGY.md](TOPOLOGY.md) · [PRACTICE.md](PRACTICE.md) · [Host ≠ Peer](diagrams/02-host-peer.svg)

### Revoke-safe admin UI

An admin UI that changes a shared world must not keep mutating after the admin’s **Cap** is revoked. **Host** returns **Result{Ops}**; the browser **Peer** applies that list (UI is L5 on the Peer outer, not a Host). **Activity** bounds the work; **lineage** records causes; **reverse** on revoke (or mark non-reversible). [TOPOLOGY.md](TOPOLOGY.md).

### Gated device control

A device must not mint Caps or invent truth. **Cap** gates submit; **Host** decide lives off-device; the MCU is **Peer** — apply **Ops** only. **Activity** bounds the control; **lineage** stays Cap/Activity-accountable across hops when revocation spans them; **reverse** on revoke. Hardware is topology, not a third kernel; device drivers stay L5. [TOPOLOGY.md](TOPOLOGY.md).

### Multi-tenant change + reverse

Several tenants change one shared world. Ending one tenant’s work must reverse that cause, without treating one Host’s **Cap** as authority on another. **Ops** list the change; **Activity** bounds the work; **lineage** plus **reverse** on end or revoke. Cross-Host acceptance needs explicit shared verify policy (default: separate trust domains). [TOPOLOGY.md](TOPOLOGY.md).

### Browser Peer + server Host

**Host** decide lives on the server: mint/verify **Cap**, return **Result{Ops}**. **Peer** apply lives in the browser: carry out those Ops only. UI is L5 on the Peer outer, not a Host. [TOPOLOGY.md](TOPOLOGY.md) · [PRACTICE.md](PRACTICE.md) · [Host ≠ Peer](diagrams/02-host-peer.svg)

### MCU as Peer

The MCU is **Peer**: apply **Ops** only — no mint, no invented truth. **Host** decide lives off-device (another process). Hardware is topology, not a third kernel; device drivers stay L5 on the Peer outer. [TOPOLOGY.md](TOPOLOGY.md) · [PRACTICE.md](PRACTICE.md) · [Host ≠ Peer](diagrams/02-host-peer.svg)

### Cap across two Hosts

Each **Host** still decides in its own domain; each **Peer** still applies. A **Cap** minted under one Host’s policy is not automatically authority on another Host — cross-Host acceptance needs explicit shared verify policy (default: separate trust domains). Hops do not add a third role. [TOPOLOGY.md](TOPOLOGY.md) · [PRACTICE.md](PRACTICE.md)

## Is / is not

| This repo **is** | This repo **is not** |
|------------------|----------------------|
| Published SSoT for CEK law | A package, crate, or runnable Host / Peer |
| Frozen names, axioms, kill criteria | Wire codecs, crypto, or domain catalogs |
| What “correct CEK” means | A surface programming language |

Kernels implement elsewhere. Domain apply catalogs stay L5 — they are not Hosts. Encoding notes (not law): [IMPLEMENTATION.md](IMPLEMENTATION.md).

## Map (Diátaxis)

| You want | Open |
|----------|------|
| Tutorial (~5 min) | [START.md](START.md) |
| Concepts | [CONCEPTS.md](CONCEPTS.md) |
| Explanation (why, not how) | [EXPLAIN.md](EXPLAIN.md) |
| Topology / multiplicity | [TOPOLOGY.md](TOPOLOGY.md) |
| Visuals | [diagrams/](diagrams/) — [Path](diagrams/01-path.svg) · [Host ≠ Peer](diagrams/02-host-peer.svg) · [Cap vs trace vs Activity](diagrams/03-cap-trace-activity.svg) · [authorized vs landed](diagrams/04-authorized-landed-reverse.svg) · [layers](diagrams/05-layers.svg) · [refuse path](diagrams/06-refuse-path.svg) |
| Pseudocode | [PSEUDOCODE.md](PSEUDOCODE.md) |
| How-to | [HOWTO-ALIGN.md](HOWTO-ALIGN.md) · [HOWTO-NAME.md](HOWTO-NAME.md) · [HOWTO-AMEND.md](HOWTO-AMEND.md) |
| Practice | [PRACTICE.md](PRACTICE.md) |
| Law (reference) | [LAW.md](LAW.md) |
| Names | [VOCABULARY.md](VOCABULARY.md) |
| Alignment | [KILL.md](KILL.md) |
| Amendment | [CHARTER.md](CHARTER.md) |
| Encoding notes (off-law) | [IMPLEMENTATION.md](IMPLEMENTATION.md) |

## How-to

- Claim CEK alignment → [HOWTO-ALIGN.md](HOWTO-ALIGN.md)
- Name a thing correctly → [HOWTO-NAME.md](HOWTO-NAME.md)
- Amend law → [HOWTO-AMEND.md](HOWTO-AMEND.md)

bitplorer/cek-framework at commit [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f) is a **historical freeze** (provenance), not a living CORE. This repository is the published SSoT.
