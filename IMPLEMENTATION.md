# Implementation notes (not law)

This file is **not** CEK law. Kernel nouns remain those in [VOCABULARY.md](VOCABULARY.md) and [LAW.md](LAW.md). **Baseline** is the permanence contract, not a pair catalog.

Snapshot: [cek-runtime](https://github.com/bitplorer/cek-runtime) commit [`50fe2af2c615ab31b35b24314915c2fb2635029f`](https://github.com/bitplorer/cek-runtime/tree/50fe2af2c615ab31b35b24314915c2fb2635029f).

| Law | That snapshot |
|-----|----------------|
| **trace** groups Intents; optional trace on lineage | Intent may carry a trace field; no store, echo, or grouping API |
| Lineage under Cap and/or **Activity** | Lineage and reverse keyed by an Activity identifier field |
| **profile** = declared apply ability | Apply ability encoded as a session apply-set (not a Cap) |
| L2 Context / inject / isolate / part | Kernel surface centers verify, once, idempotency, project, lineage, receipts, reverse |
| Recovery Cap | Reverse class includes compensation; Host mint exists |
| Cross-Host Caps | Separate Host instances; dual-speak is law-generation accept window |
| Bootstrap | Host mint is the Host bootstrap / policy path |

Some encodings identify an Op with two fields (namespace and name). That is encoding, not a kernel noun, not Cap, and not Baseline.

Field names and session encodings are implementation.
