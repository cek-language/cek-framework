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
| Visuals | [diagrams/](diagrams/) — [Path](diagrams/01-path.svg) · [Host ≠ Peer](diagrams/02-host-peer.svg) · [Cap vs trace vs Activity](diagrams/03-cap-trace-activity.svg) · [authorized vs landed](diagrams/04-authorized-landed-reverse.svg) · [layers](diagrams/05-layers.svg) · [refuse path](diagrams/06-refuse-path.svg) |
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
