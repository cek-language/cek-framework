# Pedagogical pseudocode (not law)

Teaching order for **submit**, **apply**, and refuse. Not a package. Not a kernel. Not a second axiom book.

- Law: [LAW.md §4 Host and Peer](LAW.md#4-host-and-peer)
- Why: [EXPLAIN.md — Why Host ≠ Peer](EXPLAIN.md#why-host--peer)
- Figure: [Host ≠ Peer](diagrams/02-host-peer.svg)
- Refuse: [refuse path](diagrams/06-refuse-path.svg)
- Names: [VOCABULARY.md](VOCABULARY.md)

Frozen nouns and verbs only. This page does not execute.

---

## Host.submit(Intent)

Caller **submit**s an **Intent** under a **Cap**. **Host** runs the ordered pipeline. No shared-world effects before the gate. [LAW.md §4](LAW.md#4-host-and-peer) · [diagrams/02-host-peer.svg](diagrams/02-host-peer.svg)

**Order (LAW §4, exact):** 1 Verify Cap → 2 Consume once / idempotency bind → 3 Dispatch → 4 Record lineage → 5 Project Ops → 6 Return Result. Never Project before Record lineage. **Peer** remains apply-only.

```text
Host.submit(Intent):                          # Intent under Cap

  # 1. Verify Cap against the Intent
  #    LAW §4 Host pipeline · EXPLAIN Why Host ≠ Peer
  #    diagrams/02-host-peer.svg
  if Cap verify fails:                        # integrity, expiry, action bind,
                                              # sealed args, optional subject/scopes
    refuse                                    # A5 fail closed
    return Result with empty Ops              # zero mutate Ops
                                              # diagrams/06-refuse-path.svg

  # 2. Consume once / idempotency bind
  #    LAW §4 Host pipeline — before side-effects when required
  consume once (single-use) when required
  check optional idempotency bind
  if required store is down:
    refuse                                    # A5 · K6

  # 3. Dispatch
  #    LAW §4 Host pipeline
  dispatch only after verify (and consume/bind)

  # 4. Record lineage
  #    LAW §4 Host pipeline · LAW §9
  if Cap is revocable or Activity is endable:
    record lineage                            # authorized set + reverse plan

  # 5. Project Ops
  #    LAW §4 Host pipeline · LAW §11
  project Ops to the Peer's profile
  fall back to Baseline

  # 6. Return Result
  #    LAW §4 Host pipeline · LAW §6
  return Result                               # ordered Ops or error
                                              # authority refusal distinct from
                                              # business miss when possible
```

**mint** is a Host-side privilege (including bootstrap and recovery Caps). It is not a Peer duty. [LAW.md §4](LAW.md#4-host-and-peer)

---

## Peer.apply(Result)

**Peer** applies **Ops** only. [LAW.md §4 Peer duties](LAW.md#4-host-and-peer) · [diagrams/02-host-peer.svg](diagrams/02-host-peer.svg)

```text
Peer.apply(Result):

  apply Ops in listed order under profile     # LAW §4 Peer duties · A2
  ignore unknown correlation/meta             # not required for Baseline
                                              # LAW §4 Peer duties
  unknown Ops: ignore, soft-fail, or
    strict-reject per profile                 # never crash the kernel
                                              # LAW §4 Peer duties · LAW §6
  optional apply receipt                      # landed vs failed
                                              # receipts are not Caps
                                              # LAW §4 Peer duties

  must not mint root Caps                     # LAW §4 Peer duties · A7 · K3
  must not invent business truth              # LAW §4 Peer duties
                                              # including rewriting sealed outcomes
```

---

## Refuse path

Bad **Cap** → Host refuses → **Result** with empty **Ops** → **Peer** does not apply. Fail closed. [LAW.md §4](LAW.md#4-host-and-peer) · [diagrams/06-refuse-path.svg](diagrams/06-refuse-path.svg) · [EXPLAIN.md](EXPLAIN.md#why-host--peer)

```text
# diagrams/06-refuse-path.svg

Intent under bad Cap
  → Host.submit
      Verify Cap fails
      refuse → Result with empty Ops          # zero mutate Ops
  → Peer does not apply                       # nothing to carry out
```

---

## Next

- Figure: [Host ≠ Peer](diagrams/02-host-peer.svg)
- Walk: [START.md](START.md)
- Why: [EXPLAIN.md](EXPLAIN.md)
- Map: [README.md](README.md)
