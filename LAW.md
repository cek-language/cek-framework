# CEK law

Human-readable distill of the locked Cap-Effect Meta-Language (CEK) law.

This is a **reader path**, not a package, not a redesign, and **not a second CORE**. It does not invent axioms. Unique rules from [bitplorer/cek-framework](https://github.com/bitplorer/cek-framework) CORE 00–27 at commit [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f) are preserved here in prose and tables. CORE files are not copied verbatim.

**CORE wins.** If this page and CHARTER/CORE diverge, the charter is authority. This distill is not independently amendable law. Amendments belong in bitplorer/cek-framework ([CHARTER](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHARTER.md): freeze, amendment process, [STABILITY.md](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/STABILITY.md) binding). A mechanical drift check against CORE is out of scope here; it does not redefine K14.

Frozen names: [VOCABULARY.md](VOCABULARY.md). Alignment gate: [KILL.md](KILL.md). Overview: [README.md](README.md).

Gaps in a particular runtime are labeled **IMPLEMENTATION NOTE**. Those notes are not law.

---

## 1. What is allowed

CEK is the locked law of **authorized change across boundaries**.

It defines how programs may *ask*, *be allowed*, *carry out*, *bound*, *remember*, and *undo* change — and how runtimes participate as **Host** or **Peer** under one contract.

It is **not**:

- a syntactic superset of Python, TypeScript, Rust, or any other language
- a surface programming language people “write programs in”
- named after any single kernel noun (especially not **Ops**)

The sole official name of the law is **CEK** (Cap-Effect Meta-Language). **Ops** is the carry-out list (data), not the language name.

**One line.** Mint Cap → submit Intent → apply Ops → bound in Activity → record lineage → reverse on end → group with trace → keep Baseline.

**What the core fixes.**

| Problem | Core answer |
|---------|-------------|
| Ambient authority | Cap-only truth |
| Free side-effects | Ops-only effects |
| Ununloadable composition | Activity + lineage + reverse |
| Multi-step confused with permission | trace is correlation only |
| Flag-day interop | Baseline permanent |
| Decide / apply muddle | Host / Peer split |

Shared-world change needs a verified **Cap**. Boundary effects leave as ordered **Ops**. Host verifies; Peer applies. End and revoke have an honest undo story. Old correct Host/Peer pairs keep working on Baseline. Correlation never logs you in.

**Fits** agents with tools, collab/UI channels, devices — anywhere “who authorized this write?” must stay answerable.

**Skip** pure local apps with no cross-boundary authority story.

### Explicit non-goals of the core

- Choosing specific Cap cryptography
- Mandating one process topology
- Defining all domain Ops
- Replacing general-purpose programming languages
- Implementation languages, crate layout, CI, or isolation technology

Those are implementation-framework concerns, not law.

### Parents (informative)

One law, not two stacked frameworks. Parent-local APIs and brand words are discarded; intentions are kept.

| Parent | Irreducible contribution |
|--------|--------------------------|
| **ux-channel** | Intent under Cap; Result of Ops; Host/Peer; Baseline; correlation ≠ authority; fail closed |
| **Cordis** | Bounded composition with lifetime; Context mediation; inject; structural limit/isolate; reversible caused change |

**Activity** replaces unclear “Fiber”. **Baseline** replaces unclear “Floor”. **trace** replaces correlation formerly discussed as **flow** (explicitly non-authority). **limit** is the public restriction verb; **isolate** remains the structural Context-slice operation.

### Closed intention set

| Intention | Concepts |
|-----------|----------|
| Ask | Intent, submit |
| Allow | Cap, mint |
| Carry out | Ops, apply, Result |
| Bound | Activity, Context, inject, limit, isolate, part |
| Remember / undo | lineage, reverse |
| Correlate only | trace |

**trace** does not participate in ask / allow / carry out / bound / undo. It only relates Intents that already satisfy those intentions.

Every kernel noun and verb appears in exactly one row. Host / Peer / Baseline / profile are supporting concepts: Host/Peer support allow and carry out; Baseline/profile support permanence and negotiate-carry-out.

---

## 2. Axioms (A1–A10)

Constitutional. Features may not relax them without charter amendment.

| ID | Name | Statement |
|----|------|-----------|
| **A1** | Cap-only truth | The only proof of authority is a verified Cap. Sessions, mesh membership, and ambient Context never suffice alone. |
| **A2** | Ops-only effects | The only side-effects at the kernel boundary are explicit ordered Ops. |
| **A3** | Lineage accountability | Every carried-out change under a revocable Cap or endable Activity is recorded in lineage. |
| **A4** | Baseline permanent | The Baseline contract never silently breaks; power is additive or explicitly versioned. |
| **A5** | Fail closed | Failed Cap verification, missing required once-store, or required lineage write failure refuses the action. |
| **A6** | Trace ≠ authority | A trace only groups Intents; it never grants permission. |
| **A7** | Peer unprivileged | A Peer applies Ops; it does not mint root Caps or invent business truth. |
| **A8** | Attenuation monotonic | `limit` and `isolate` only narrow authority or visibility; they never widen it. |
| **A9** | Composition authorized | Opening an Activity or loading a part is Cap-gated (or uses an explicit minimal bootstrap root). |
| **A10** | One concept, one name | The kernel has no synonyms; documentation and code use the same primary names. |

**Notes that still bind.**

- **Bootstrap root** is allowed only as an explicit, minimal Host-side origin of Caps — not as ambient Peer power.
- **Non-revocable, non-endable** paths may narrow lineage requirements only under explicit policy that does not create a general ambient escape.
- **Projection determinism:** for fixed Intent outcome, profile, and projection rules, Host Ops projection should be deterministic. Non-determinism belongs in L7 generators *before* commit to Result, not in silent apply divergence.
- **Key purpose separation:** Cap authority material is conceptually distinct from transport and optional proof / telemetry material. Implementations must honor that separation.

---

## 3. Layers

```text
L0  Law         axioms + Baseline
L1  Kernels     Host · Peer
L2  Bound work  Activity · Context · inject · limit · isolate · lineage · reverse · part
L3  Correlate   trace
L4  Negotiate   profile
L5  Drivers     domain Ops
L6  Policy      optional
L7  Application product logic
```

| Layer | Responsibility |
|-------|----------------|
| **L0 Law** | What is true regardless of implementation: axioms, Baseline shape, Cap-only / Ops-only |
| **L1 Kernels** | Host and Peer mechanical duties. No domain semantics beyond verify / dispatch / apply |
| **L2 Bound work** | Lifetime, visibility, composition units, cause trail, undo |
| **L3 Correlate** | trace only. No authority, no execute |
| **L4 Negotiate** | profile declares apply ability; Host projects Ops the Peer can apply, including Baseline fallback |
| **L5 Drivers** | Meaning of domain Ops. Drivers do not mint root Caps |
| **L6 Policy** | Optional grades, meta-Caps, compensation synthesis, distributed agreement on lineage — *on top of* L0–L2 |
| **L7 Application** | Handlers, stores, product Activities, UX. Must submit Intents under Caps for shared-world change |

**Invariants.** Lower never depends on higher. L5–L7 are replaceable without changing L0–L2 meaning. L6 cannot bypass Cap verify or Ops-only emission.

L0–L2 changes are charter-level. L3–L4 must preserve A6 and Baseline. L5–L7 may evolve if axioms hold.

---

## 4. Host and Peer

L1 has **exactly two** kernels (roles). There is **no third L1 kernel**.

| Kernel | Role | Duty summary |
|--------|------|--------------|
| **Host** | Decide | Mint / verify Cap; dispatch; lineage; project; Result |
| **Peer** | Carry out | Apply Ops under profile; never mint root Caps; never invent truth |

Caller, bootstrap, lineage store, recovery Cap, profile, transport, and conformance harness are **not** kernels.

Truth and permission are Host-side. World mutation at the boundary is Peer-side apply of Ops (and Host-side lineage accounting).

```text
Intent + Cap  ──►  Host  ──►  Result + Ops  ──►  Peer
                     │
                     └── lineage / reverse (Host-owned)
```

### Host pipeline (ordered; fail closed)

No shared-world side-effects before the gate:

1. **Verify** Cap against the Intent (integrity, expiry, action bind, sealed args, optional subject / scopes). Refuse → no mutate Ops.
2. **Consume** single-use constraints and check optional **idempotency bind** before side-effects when required. Required store unavailable → **refuse**.
3. **Dispatch** the action only after verify (and after consume / bind checks).
4. **Record lineage** when the Cap is revocable or the Activity is endable (authorized set + reverse plan).
5. **Project** Ops to what the Peer’s **profile** can apply, falling back to **Baseline** forms when needed.
6. Return a **Result** containing ordered **Ops** or an error (authority refusal distinct from business miss when possible).

Additionally: **Mint** Caps under policy (Host-side privilege, including bootstrap and recovery Caps).

Hosts **reload authoritative state** from their store for magnitudes, balances, roles, and other truth. They do not trust caller-supplied “full world state.”

### Peer duties

1. **Apply** Ops in order under its profile.
2. Ignore unknown correlation / meta that is not required for Baseline.
3. Handle unknown Ops per profile policy (ignore, soft-fail, or reject in strict profiles) without crashing the kernel.
4. Optionally report an **apply receipt** (landed vs failed); receipts are not Caps.
5. **Must not** mint root Caps.
6. **Must not** invent business truth (for example rewrite sealed outcomes).

### Multiplicity

Many implementations of Host and of Peer may exist (languages, processes, hardware). Multiplicity does **not** add roles: each decide boundary is still a Host; each apply boundary is still a Peer.

The role law does not require a single process or a browser/server topology. A process may embed both roles as separate boundaries; mint must not live inside pure apply.

Extending to more Peers does not change the law: each apply boundary is still Peer; each decide boundary is still Host (or Host-delegated under Cap). Lineage remains Cap / Activity-accountable across hops if revocation spans them. L6 may add distributed agreement; it cannot drop accountability.

### Cross-Host Caps

A Cap minted under one Host’s policy is **not** automatically authority on another Host. Cross-Host acceptance requires **explicit** shared verify policy (keys, trust domain, dual-speak window). Default is separate trust domains.

---

## 5. Cap

A **Cap** is permission to **submit** a specific class of **Intent**. It is the sole authority object at the kernel boundary (A1).

### Conceptual binds

A Cap conceptually binds at least:

- the **action** (what ask is allowed)
- integrity of **sealed arguments** (what may not be altered by the caller)
- a **time window** or equivalent validity constraint

and may bind:

- **subject** (who)
- **scopes** (qualitative limits)
- **single-use** constraints

Exact encoding is implementation. The binds are conceptual law.

### Conceptual lifecycle

```text
Minted → Active → Consumed (once) | Expired | Revoked
```

| Transition | Rule |
|------------|------|
| Minted → Active | Host mint under policy (or meta-Cap) |
| Active → Consumed | Single-use consume **before** side-effects when once is required |
| Active → Expired | Outside validity window under Host clock policy → verify refuses |
| Active → Revoked | Host revoke → reverse lineage tied to that Cap per policy |

Success paths must not skip verify or required consume. Replay of a Consumed once-Cap refuses.

**mint** creates a Cap. Minting is a Host-side (or higher Cap-gated) privilege — not a Peer right (A7).

**verify** happens before dispatch. Failure → refuse (A5).

### Attenuation

Caps and Context restrictions may be **limited** only by narrowing: fewer actions, tighter sealed args, shorter validity, fewer scopes, fewer visible Context surfaces. Widening is forbidden (A8).

### Meta-Caps

Caps that mint, limit, or revoke other Caps are themselves Cap-gated and lineage-tracked. They do not create ambient root power outside bootstrap policy.

### Capability discipline

```text
Mint is rare and Host-side (or meta-Cap gated).
Hold is transferable only by attenuation or explicit grant policy.
Use is Intent submit under Cap.
End is revoke Cap and/or end Activity → reverse lineage.
```

### Cap vs trace vs Activity

| Concept | Grants permission? | Groups steps? | Owns lifetime undo? |
|---------|--------------------|---------------|---------------------|
| Cap | Yes | No | Via lineage when revocable |
| trace | No | Yes | No |
| Activity | No | No | Yes (reverse lineage on end) |

A session, TLS identity, receipt, or trace is **not** a Cap.

Clock skew on Cap expiry: fail closed on verify if outside the window under **Host** clock policy.

---

## 6. Intent, Result, and Ops

Conceptual fields only. Encodings are free as long as binds hold.

### Intent

An **Intent** is a sealed ask.

| Element | Role |
|---------|------|
| **action** | What is being asked |
| **args** | Arguments; sealed subset bound by Cap |
| **Cap** | Permission for this ask (when required by policy) |
| optional **trace** association | Correlation only |
| optional other meta | Ignorable on Baseline if unknown |

Without a valid Cap when policy requires one, Host refuses (A1, A5).

### Result

A **Result** answers an Intent.

| Element | Role |
|---------|------|
| **ok** / success signal | Whether the ask was accepted and handled |
| **Ops** | Ordered changes to carry out (may be empty) |
| **error** | On failure; authority refusal distinct from business miss when possible |
| optional meta | Never authority |

Empty Ops on success is allowed (pure decision, no carry-out).

Callers must not treat authority refusal as a normal business miss.

### Ops

**Ops** are an ordered list of carry-out instructions.

1. Order is significant within one Result.
2. Ops are **data**, not code (no Baseline eval).
3. Unknown Ops: ignore, soft-fail, or strict-reject per **profile** — never crash the kernel.
4. Domain meaning lives in L5 namespaces; law does not fix the catalog.

No eval / raw code Op as Baseline power. Peer apply is the mutation path for delivered Ops.

### Projection

Host may **project** rich internal outcomes to Ops the Peer’s profile can apply, always able to fall back to **Baseline** forms.

Given the same Intent outcome, same profile, and same projection rules, Host projection to Ops should be **deterministic**.

Compatibility pattern for new Ops:

1. Define Op in a domain namespace
2. Document Baseline lowering (equivalent classic Ops or safe no-op)
3. Advertise in profile
4. Host projects intersection
5. Add conformance vectors for rich + baseline paths

---

## 7. Sealed arguments

If the caller can change any argument after permission is granted, Cap becomes theater (confused deputy / bait-and-switch).

A Cap binds the **sealed** portion of arguments. The Host verifies that the Intent’s sealed args match the Cap bind before dispatch.

| Kind | Trust | Use |
|------|-------|-----|
| **Sealed args** | Bound by Cap; caller cannot alter without invalidating Cap | Identifiers, fixed quantities, targets the grantor already approved |
| **Open / form args** | Not bound by Cap; filled by caller | Progressive enhancement, optional fields Host re-validates from truth |

Mismatch of sealed args → Cap verify failure → refuse (no side-effects).

---

## 8. Activity and Context

### Activity

**Activity** is bounded work with a lifetime:

- opens (starts)
- runs (may submit Intents under Caps)
- ends (completes, cancels, fails, or is unloaded)

When an Activity ends, the Host **reverse**s its **lineage** under recovery policy.

Activity is **not** a Cap (it does not by itself allow asks), **not** a trace (it is not merely correlation), **not** the whole application, and **not** an OS thread.

**part**s load into an Activity under Caps (A9). Loading and unloading parts are themselves accountable composition events.

Abandoned Activity: end → reverse (optional time-box policy). ([CORE/24](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/24-moving-parts-and-corners.md))

### Context

**Context** is the mediated visible world of an Activity: what services, data surfaces, or coeffects the work may see.

Context is **not** ambient authority, **not** a substitute for Cap on outward asks, and **not** a global bag of unconstrained power.

**inject** declares what an Activity **requires** from its Context to run. Undeclared access fails closed under mediation.

- **limit** — restrict what may be seen or done (public restriction verb)
- **isolate** — separate a Context slice so names / services do not leak across boundaries

Both are **monotonic**: they only narrow (A8). isolate / limit do not grant a parent’s missing rights.

```text
Activity
  └── lives in Context
        ├── inject requirements
        ├── limit / isolate visibility
        └── submits Intents under Caps
              └── contributes to lineage
```

---

## 9. Lineage and reverse

### lineage

**lineage** is the cause trail of what was carried out under a **Cap** and/or **Activity**. It exists so authority end and Activity end have a defined undo story (A3).

A lineage entry conceptually ties:

- Cap identity (or equivalent)
- Activity identity (when applicable)
- optional **trace** association (correlation only)
- action
- sealed argument integrity reference
- Ops carried out (or their integrity reference)
- a **reverse plan** (inverse and/or compensation)

lineage is **not** generic application history, **not** full observability telemetry, **not** a substitute for Cap, and **not** a substitute for trace.

### When lineage is required

Required when:

- the Cap is revocable, **or**
- the Activity is endable and may have caused shared-world change

Optional narrowing only under explicit non-revocable / non-endable policy that does not become a general escape hatch.

### reverse

**reverse** undoes a lineage (or ends an Activity by undoing its lineage).

| Form | Meaning |
|------|---------|
| **Inverse** | Direct undo of caused Ops where possible |
| **Compensation** | New Intents under a recovery Cap when true inverse is impossible |
| **Mark non-reversible** | Explicit audit outcome when neither inverse nor compensation can complete; never silent success |

Reverse plans should respect causal order (typically reverse order of causes) unless a documented compensation graph says otherwise.

Cap revoked → reverse lineage tied to that Cap (policy may scope). Never report successful reverse when compensation / inverse failed without an explicit non-reversible mark.

### Host cause vs landed set

- **Lineage** always records what the **Host authorized** (cause under Cap / Activity).
- A Peer may optionally return an **apply receipt** (which Ops actually landed).
- Receipts are **not** Caps and grant no authority.
- When receipts exist, **reverse** prefers the **landed set**; when absent, reverse uses the authorized Ops set.
- Baseline interop does **not** require receipts.

Observe-only Ops may omit from mutate lineage if classed observe (when that optional class is adopted); else treat as mutate.

---

## 10. Trace vs Activity vs lineage

A **trace** correlates related **Intents** as one multi-step effort.

It answers: *which asks belong together?*  
It does **not** answer: *who is allowed?* or *what may be applied?* or *what must be undone?*

**Laws.**

- Trace is **not authority** (A6).
- Each step remains **Intent under Cap**.
- Ending a multi-step effort still **reverse**s **lineage** under the relevant Activities / Caps — the trace does not undo by itself.
- Resume of multi-step work uses **fresh Caps** under policy; a trace does not revive expired permission.
- No trace is fine (single-step). Trace without Cap still grants no permission.

Product state for multi-step work lives in application storage (L7). The Peer kernel does not become the system of record for business workflows merely because a trace exists.

The concept is **trace**. Implementations may assign identifiers to traces; identifiers are not a separate kernel concept. **flow** is not the primary name.

**Activity** owns lifetime undo. **lineage** is the cause trail. **trace** only groups.

### IMPLEMENTATION NOTE — cek-runtime trace and lineage

Not law. Snapshot of [cek-runtime](https://github.com/bitplorer/cek-runtime) at commit [`50fe2af2c615ab31b35b24314915c2fb2635029f`](https://github.com/bitplorer/cek-runtime/tree/50fe2af2c615ab31b35b24314915c2fb2635029f):

- `Intent.trace` is currently **field-only**. There is no `TraceStore`, echo, or grouping API. The Host submit path does not read `trace` to authorize, group, or undo.
- Lineage commit and reverse (`end_activity`) are keyed by Activity identity (`activity_id`). `LineageEntry` stores that identifier, not a stored trace association.

CORE still distinguishes **trace** (correlation) from **Activity** (lifetime undo) and still conceptually allows optional trace association on a lineage entry ([CORE/09](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/09-lineage-reverse.md), [CORE/10](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/10-trace.md)). This snapshot’s encoding does not merge those concepts, treat Activity identity as Cap, or relax A6.

---

## 11. Baseline, profile, and negotiation

### Baseline

**Baseline** is the permanent shared contract every correct Host / Peer pair supports:

- Intent under Cap
- Result with ordered Ops
- Host verifies; Peer applies
- Classic apply ability sufficient for interop

Baseline is a **concept of permanence**, not a runtime object you “open” like an Activity.

Improvements add power *above* Baseline or introduce an explicit major version of meaning. They do not silently redefine Baseline (A4).

Features above Baseline may deprecate; the Baseline path remains. Removing ability is fine if Baseline clients remain valid. Prefer profile limitation over breaking Baseline.

### profile

A **profile** declares what a Peer can **apply**.

- Host uses profile to project Ops the Peer understands.
- Missing or limited profile → Baseline projection.
- Profile never grants Cap authority.

```text
Peer declares profile
Host projects Ops ⊆ peer ability ∪ Baseline fallback
Peer applies
```

Unknown Op policy is profile-defined:

| Policy | Behavior |
|--------|----------|
| tolerant | ignore or soft-fail |
| strict | reject Result path per policy; no kernel crash |

Partial apply: profile defines stop vs continue. Peer does not invent Host truth or widen Ops.

High-assurance / multi-Peer profiles **should** use receipts (recommended). Production profiles enable receipts and idempotency; Baseline stays valid without them.

### Manifest (conceptual)

Hosts and Peers may exchange a small **manifest** of compatibility facts. Encoding is free; concepts are fixed:

| Element | Purpose |
|---------|---------|
| **Law generation** | Which CEK law generation / Baseline generation is spoken |
| **Profiles supported** | Apply-ability names the party can use |
| **Fail-closed behaviors** | Confirms once-store-down and Cap-fail refuse |
| **Optional families** | e.g. receipts, idempotency (if any) |

Rules:

- Manifest never grants Cap authority.
- Missing manifest → assume Baseline-only Peer.
- Manifest drift without dual-speak is a compatibility defect.

### IMPLEMENTATION NOTE — optional stamp

Not law. In [cek-runtime](https://github.com/bitplorer/cek-runtime) at commit [`50fe2af2c615ab31b35b24314915c2fb2635029f`](https://github.com/bitplorer/cek-runtime/tree/50fe2af2c615ab31b35b24314915c2fb2635029f), optional **stamp** is session apply-set / profile encoding: a closed `PairSet` of `(ns, name)` pairs used as the Peer apply-set (Baseline ∪ UI seed as a default stamp source). Stamp is **not** a Cap, **not** a kernel noun, and **not** permission. See [VOCABULARY.md](VOCABULARY.md).

---

## 12. Authorized set, landed set, and receipts

Optional for Baseline; **normative when receipts are used**.

| Term | Meaning |
|------|---------|
| **Authorized set** | Ops the Host placed in the Result after Cap verify (what was allowed to be carried out) |
| **Landed set** | Ops the Peer actually applied successfully |
| **Apply receipt** | Peer’s report of the landed set (and optional failures) |

Receipts are **not** Caps. They grant no authority (A1, A6, A7).

1. **Lineage** records the **authorized** cause under Cap / Activity (and reverse plan).
2. If **no receipt** → **reverse** uses the authorized set.
3. If **receipt** present → **reverse** prefers the **landed** set.
4. Partial apply does not invent Host truth; Peer does not widen Ops.
5. Baseline interop does **not** require receipts.
6. High-assurance / multi-Peer profiles **should** use receipts.

| Case | Handling |
|------|----------|
| All Ops landed | Receipt matches authorized set |
| Partial land | Receipt lists landed + failed; reverse uses landed |
| Receipt lost | Treat as no receipt → reverse authorized set; may over-compensate — policy may mark uncertainty |
| False receipt | Out of kernel scope (Peer compromise); Host still bound by Cap accounting |

---

## 13. Once and idempotency

### Single-use (once)

When a Cap is marked single-use, the Host **consumes** that constraint **before** side-effects. Second use refuses. If the required once-store is down, **refuse** (A5, K6). Concurrent submit of the same single-use Cap: at most one consume succeeds.

Once is about **this Cap instance** usable once. It is not Cap authority by itself, not trace, and not idempotency.

### Idempotency bind (optional, recommended)

**Not required for Baseline.** Recommended for production profiles.

An **idempotency bind** is an optional Cap / Intent claim that identifies one logical ask. If the Host sees a second submit with the same bind (within policy window) after a completed or in-flight handling, it does **not** create a second lineage cause or second mutate effect.

1. Bind is checked **after** Cap verify, **before** side-effects (same ordering spirit as single-use).
2. If the idempotency store is required and **down** → **refuse** (fail closed), consistent with A5.
3. First successful handling records lineage once; duplicates return the prior Result (or equivalent safe replay of Result) per Host policy.
4. Bind does **not** replace Cap, once / jti, or trace.
5. Baseline Peers need not understand the bind; it is Host-side.

| Mechanism | Job |
|-----------|-----|
| Cap | Permission |
| once / single-use | This Cap instance usable once |
| idempotency bind | This logical ask executed once even if Intent is resubmitted |
| trace | Group related steps |

---

## 14. Recovery Cap

Used when **reverse** must submit compensation Intents.

A **recovery Cap** is a Cap minted under Host policy whose actions are limited to **compensation / cleanup** for a given lineage (or Activity).

It is still a normal Cap: verify, sealed args, fail closed, lineage for its own effects if revocable.

1. Recovery Caps are **minted by Host** (or meta-Cap), never by Peer as root power.
2. Scope is **narrow**: only the compensation actions declared for that reverse plan.
3. Compensation Intents are ordinary Intents under the recovery Cap.
4. If compensation itself fails → **mark non-reversible** for the original cause; do not report clean reverse.
5. Bootstrap must not be used as a standing recovery bypass.

```text
Activity end / Cap revoke
  → reverse(lineage)
      → inverse Ops when possible
      → else submit compensation Intents under recovery Cap
      → else mark non-reversible + audit
```

---

## 15. Bootstrap and cross-Host

Every Cap system needs an origin of authority. If left implicit, bootstrap becomes ambient power and destroys A1 / A7.

**Bootstrap root** is allowed only as:

- **Host-side**
- **explicit**
- **minimal**
- **documented**
- and **not available to Peers** as a general API

Bootstrap may only:

1. Mint the first Caps required to run the system, and/or
2. Open a root Activity under those Caps, and/or
3. Install policy that governs further minting (including meta-Caps)

Bootstrap must **not**:

- Expose unconstrained “do anything” to application code by default
- Allow Peers to call bootstrap mint
- Skip lineage for subsequent revocable work “because bootstrap was trusted”
- Become a permanent second authority path beside Caps

```text
Cold start
  → Host loads bootstrap policy (out of band / config / HSM)
  → Host mints initial Caps under that policy
  → System runs only via Intent under Cap thereafter
  → Bootstrap credentials stay Host-private
```

Bootstrap mint events should be distinguishable in lineage or Host audit as **bootstrap-origin**.

Widening bootstrap surface (for example Peer-callable root mint) is a charter-level security change.

Cross-Host Caps: see [§4](#4-host-and-peer). Default is separate trust domains.

Never treat **transport security alone** as Cap. Never open a path that changes the shared world without a verified Cap (except documented bootstrap mint on Host).

---

## 16. Security model

### Trust boundaries

| Boundary | Trusted for | Not trusted for |
|----------|-------------|-----------------|
| **Host** | Cap mint / verify policy, truth for dispatch, lineage record | Blind trust of Peer-supplied “I am allowed” |
| **Peer** | Faithful apply of Ops it accepts under profile | Minting root Caps; inventing business truth |
| **Caller holding a Cap** | Submitting the bound Intent | Widening sealed args; replaying single-use Caps |
| **trace** | Grouping Intents | Permission or execute |

### Threats in scope (kernel must address)

| Threat | Primary controls |
|--------|------------------|
| Forged or tampered ask | Cap integrity bind to action + sealed args |
| Replay of single-use permission | Single-use consume before side-effects; fail closed if store unavailable |
| Ambient privilege | A1 Cap-only; A7 Peer unprivileged; A9 composition authorized |
| Residual effects after revoke / end | A3 lineage + reverse |
| Confused deputy / arg mutation | Sealed args bind; handler reloads truth from store for magnitudes |
| Correlation used as auth | A6 |
| Silent widening of power | A8 monotonic attenuation |
| Peer overreach | Ops-only apply; no root mint |
| Compatibility break as attack on dependents | A4 Baseline permanent |

### Threats out of kernel scope

| Threat | Where |
|--------|--------|
| Side channels (timing, power, traffic analysis) | L6 / L7, deployment, crypto engineering |
| Full information-flow non-interference | Optional L6 IFC; not required of Baseline |
| Physical host compromise | OS / platform security |
| Social engineering of Cap grantors | Organizational policy; meta-Cap governance |
| Poisoned domain drivers | L5 review; still cannot bypass Cap verify if Host is correct |
| Denial of service by volume | L6 budgets / quotas; platform limits |
| False apply receipt | Peer compromise; Host still bound by Cap accounting |

### Security design rules

1. **Never** open a path that changes the shared world without a verified Cap (except documented bootstrap mint on Host).
2. **Never** treat transport security alone as Cap.
3. **Never** skip single-use consumption ordering (consume before effects).
4. **Never** report successful reverse when compensation / inverse failed without explicit non-reversible mark.
5. **Separate key purposes**: Cap authority material ≠ transport keys ≠ optional proof / telemetry keys.

---

## 17. Fail-closed rules

Authority path **fails closed**. There is no “best effort allow.”

Refuse (zero mutate Ops) when:

- Cap missing when required
- Cap integrity, action bind, or sealed-args fail
- Cap expired under Host clock policy (including clock-skew case: outside window → refuse)
- Single-use replay
- Once-store unavailable and once required
- Idempotency store down when bind is required
- Required lineage cannot be written
- Attenuation would widen

Ignore (safe) when:

- Unknown optional meta on Baseline path
- Unknown Ops under a Baseline-tolerant profile

Lower (project) when:

- Rich outcome → Baseline Ops the Peer can apply
- Peer has no profile → Baseline projection

Mark (honest) when:

- Reverse cannot complete → non-reversible mark + audit, not fake success

Bound when:

- Activity end / Cap revoke → reverse what was recorded

Defer to profile when:

- Strict vs tolerant unknown-Ops
- Stop vs continue on partial apply

**No fourth path of “just this once ambient allow.”**

Session / cookie / mesh membership never alone authorizes.

---

## 18. Errors and concurrency

### Errors

Authority failures and apply failures must remain **distinguishable** in Results.

| Class | Meaning | Typical handling |
|-------|---------|------------------|
| **Authority refusal** | Cap verify failed, single-use replay, store down | Fail closed; no side-effects |
| **Dispatch error** | Action missing, policy deny after verify | No Ops or explicit error Ops only under policy |
| **Apply error** | Peer could not apply some Ops | Profile policy: stop vs continue; report |
| **Reverse error** | Inverse / compensation incomplete | Mark non-reversible; audit; do not claim clean reverse |

Baseline does not require a single error taxonomy encoding; it requires that **authority refusal does not partially apply world changes**.

### Concurrency

Multiple Activities and Intents may proceed concurrently. The law does not freeze a single global lock; it requires **Cap and lineage accountability per change**.

1. **No Cap sharing that violates single-use** — concurrent submit of the same single-use Cap: at most one succeeds consume.
2. **Lineage is per cause** — concurrent Activities do not merge lineage unless an explicit L6 policy defines joint reverse.
3. **Context mediation is per Activity** — isolate / limit apply to that Activity’s view.
4. **trace** may span concurrent Intents; still grants no power.
5. **Deterministic apply order** — Ops in one Result apply in listed order; cross-Result ordering is app / Host scheduling, not ambient Peer reordering of a single Result.

Stronger isolation (serial Activities, stricter budgets) is L6 / L7 policy. Weaker isolation must not become Cap bypass.

---

## 19. Change, versioning, and extensibility

### Fixed law, mobile surface

```text
FIXED (must not drift)
  axioms · vocabulary · Host/Peer split · Cap-only · Ops-only
  lineage/reverse obligation · Baseline · fail closed · trace ≠ authority

MOBILE (may move without charter amendment)
  domain Ops · profiles · L6 policy · L7 product · Cap encoding
  transports · optional receipts/idempotency · driver quality
```

When something moves, it moves **above** L2 or in encoding — never by silently redefining Intent, Cap, or Baseline. **trace** is L3; changing its meaning is kernel meaning ([CORE/12](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/12-change-law.md): major version + dual-speak + conformance), not a silent L4–L7 move.

**Doctrine.** Freeze the law; default every corner; let only the surface move — and when it moves, lower to Baseline or refuse, never ambient-allow.

Amendment process, freeze statement, [STABILITY.md](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/STABILITY.md) binding, and the list of what requires charter amendment (including a third conceptual parent that redefines L0–L2, and collapsing Host and Peer into one privileged role) are in [CHARTER](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHARTER.md). This distill does not replace that file.

### Change classification

| Change | Allowed when |
|--------|----------------|
| Additive domain Ops / L5 drivers | Axioms hold; Baseline peers still correct |
| Optional L6 policy | Does not relax A1–A10 |
| Optional ignored meta | Peers may ignore; not required for Baseline |
| Kernel meaning (Intent / Cap / Ops / Activity / lineage / trace / …) | Major version + dual-speak + conformance |
| Primary rename of frozen vocabulary | **Forbidden** (alias only) |
| Axiom relaxation | Charter amendment |
| Trace-as-power | **Forbidden** |

### Version kinds

| Kind | What changes | Compatibility |
|------|--------------|---------------|
| **Baseline behavior** | Never silently | Eternal for a given Baseline generation |
| **Profile revision** | Apply ability | Negotiated; fallback to Baseline |
| **Domain Op namespace** | L5 meanings | Unknown Ops ignored or projected |
| **Major law version** | Meaning of Intent / Cap / verify / apply | Dual-speak window required |
| **Charter amendment** | Axioms / meta-framework | Explicit; recorded |

**Stability guarantees (language-grade).**

1. **Primary vocabulary freeze** — Intent, Cap, Ops, Result, Activity, Context, lineage, Host, Peer, Baseline, profile, part, trace, and core verbs do not rename.
2. **Baseline interop freeze** — A Peer that only applies Baseline Ops continues to work with a Host that also speaks richer profiles.
3. **Additive preference** — New fields / ops / profiles must be ignorable or lowerable when unknown.
4. **No silent semantic shift** — Same name, same intention; if meaning changes, version the law.
5. **Deprecation without deletion of Baseline** — Features above Baseline may deprecate; Baseline path remains.

On major law version: Hosts that offer the new law must still accept Baseline-shaped participation for a documented window. Conformance vectors exist for both shapes during the window. End of window is a published date, not an accident.

Library semver may move faster than law version. Law version changes only when CORE meaning changes. Do not equate “npm major” with “Baseline break” unless it is one.

**Not frozen:** domain Op catalogs, L7 product shapes, L6 optional policies, encoding of Caps (as long as conceptual binds hold), transport.

### Extension points (allowed)

| Extension | Layer | Constraint |
|-----------|-------|------------|
| New domain Ops | L5 | Projectable or ignorable for Baseline Peers |
| New Peer surfaces (UI, agent, device) | L5 | Still apply Ops only |
| Richer profiles | L4 | Negotiate apply ability only |
| Grades, budgets, quotas | L6 | Enforced before dispatch; cannot replace Cap |
| Meta-Caps / policy engines | L6 | Cap-gated; lineage-tracked |
| Compensation strategies | L6 / L2 | Must still reverse or mark non-reversible |
| Application Activities and parts | L7 | Cap-gated composition |
| Optional proofs over lineage | L6 | Separate key purpose from Cap material |

### Extension anti-patterns (forbidden)

| Pattern | Why blocked |
|---------|-------------|
| “Trusted mode” skipping Cap | Breaks A1 |
| Side door emit outside Ops | Breaks A2 |
| Using trace as session auth | Breaks A6 |
| Peer self-grant root Cap | Breaks A7 |
| Limit that grants more than parent held | Breaks A8 |
| Plugin load without Cap | Breaks A9 |
| Second official name for Cap / Intent | Breaks A10 |

### Handling new corners later

1. Can it be handled by an existing default (refuse / ignore / lower / mark / bound / profile)? Document it; no charter change.
2. Does it need new optional policy only? L6 / profile; Baseline ignore path.
3. Does it change meaning of Cap, Intent, Ops, Activity, lineage, or Baseline? Major law version + dual-speak + charter.
4. Does it create ambient authority or free effects? Reject.

The framework is **complete** when every kernel concept maps to an intention (or correlation), every axiom has testable consequences, every known corner has a default, every moving part has a stable interface, and unknown future features have a placement rule. It is **not** incomplete merely because a domain Op catalog is unfinished, an implementation is missing, or a proposal is not adopted.

---

## 20. Corner catalog (closed defaults)

Every incomplete corner maps to a defined default that preserves axioms.

### Authority

| Corner | Default |
|--------|---------|
| Cap missing when required | Refuse |
| Cap integrity / action / sealed-args fail | Refuse |
| Single-use replay | Refuse |
| Once-store unavailable and once required | Refuse |
| Bootstrap | Host-only, minimal, explicit — never Peer |
| Idempotent retry (if bind present) | Host dedupe before lineage; store down + bind required → refuse |
| Apply receipt absent | Reverse uses Host-authorized Ops set |
| Apply receipt present | Reverse prefers landed set; receipt ≠ Cap |

### Effects

| Corner | Default |
|--------|---------|
| Unknown Op (tolerant profile) | Ignore or soft-fail |
| Unknown Op (strict profile) | Reject Result path per policy; no kernel crash |
| Empty Ops on success | Allowed (pure decision, no carry-out) |
| Peer cannot apply subset | Partial-apply policy; do not invent Host truth |

### Composition / undo

| Corner | Default |
|--------|---------|
| Activity ends | Reverse lineage |
| Cap revoked | Reverse lineage tied to that Cap (policy may scope) |
| No true inverse | Compensation under recovery Cap, or mark non-reversible |
| Observe-only Ops | May omit from mutate lineage if classed observe (when adopted); else treat as mutate |

### Correlation

| Corner | Default |
|--------|---------|
| No trace | Fine — single-step |
| Trace without Cap | Still no permission |
| Resume after expiry | Fresh Caps required; trace does not revive Cap |

### Interop

| Corner | Default |
|--------|---------|
| Peer has no profile | Baseline projection |
| Host speaks richer law | Dual-speak / Baseline still accepted during window |
| Optional meta unknown | Ignore |

### Concurrency / time

| Corner | Default |
|--------|---------|
| Concurrent single-use Cap | At most one consume wins |
| Concurrent Activities | Separate lineage unless L6 defines joint reverse |
| Clock skew on Cap expiry | Fail closed on verify if outside window under Host clock policy |
| Abandoned Activity | End → reverse (optional time-box policy) |

---

## 21. Canonical story and scenarios

The entire core must remain tellable as follows:

```text
Host mints a Cap.
Caller submits an Intent under that Cap.
Host verifies Cap, records lineage, returns Result with Ops.
Peer applies Ops.

Work is an Activity in a Context.
The Activity injects what it needs; the Host may limit or isolate it.
Parts load under Caps.

Related Intents share a trace.
When an Activity ends, reverse its lineage.

Everyone supports the Baseline.
Profile only negotiates what a Peer can apply.
```

**Full lifecycle.**

1. **Bootstrap** — Host holds minimal root policy to mint Caps (explicit, not ambient Peer power).
2. **Open Activity** — Cap-gated; Context mediated; inject requirements; optional limit / isolate.
3. **Load parts** — under Caps into the Activity.
4. **Step** — mint / use Cap → submit Intent → verify → lineage entry → Result Ops → Peer apply.
5. **Correlate** — multiple steps may share a trace without sharing authority.
6. **End** — reverse Activity lineage; unload parts; release Context mediation.
7. **Interop** — all of the above remains expressible on Baseline; profiles only enrich apply ability.

If a proposed feature cannot be inserted into this narrative without new kernel nouns, it fails the speech test.

Illustrative scenarios (all must obey axioms):

| ID | Story |
|----|--------|
| **S1** | Single Host, single Peer: mint → submit → verify → lineage if required → Result Ops → apply. Baseline sufficient. |
| **S2** | Activity-scoped multi-step: open Activity (Cap-gated); several Intents under possibly different Caps; optional shared **trace**; end → reverse. Trace groups; each step still needs Cap. |
| **S3** | Part load / unload under Cap into Activity; part’s work produces lineage; unload / end → reverse. |
| **S4** | Rich Peer declares profile → Host projects rich Ops; Baseline Peer omits profile → classic Ops only. Both remain correct. |
| **S5** | Invalid or replayed Cap → Host fails closed; no mutate Ops; Result signals authority refusal. |
| **S6** | Partial apply: profile defines stop vs continue; optional receipt can report back into lineage. |
| **S7** | Irreversible external effect: compensation under recovery Cap, or mark non-reversible with audit. Never silent “fully reversed.” |
| **S8** | Bootstrap then steady state: Host bootstrap mints initial Caps only; thereafter all shared-world change is Intent under Cap; Peer never calls bootstrap mint. |

Delivery of Result / Ops is not a kernel role. An in-process Host → Peer is equally legal.

---

## 22. Invariants (design review)

Any “no” on a required invariant blocks merge of a kernel change.

**Authority.** Shared-world change requires verified Cap (or documented Host bootstrap mint only). Session / cookie / mesh membership never alone authorizes. Single-use constraints consumed before side-effects. Missing required once-store refuses. Attenuation only narrows.

**Effects.** Kernel boundary emits only ordered Ops (plus lineage accounting). No eval / raw code Op as Baseline power. Peer apply is the mutation path for delivered Ops.

**Composition.** Activity open / part load is Cap-gated (or bootstrap). inject declares requirements; undeclared access fails under mediation. isolate / limit do not grant parent’s missing rights.

**Accountability.** Revocable Cap or endable Activity → lineage recorded. Activity end triggers reverse. Failed reverse is not reported as clean success without non-reversible mark.

**Correlation.** trace does not authorize. Each step still has its own Cap. Resume does not revive dead Caps via trace alone.

**Interop.** Baseline path still works. Unknown optional meta ignorable. Profile cannot mint authority.

**Language hygiene.** No new primary kernel synonym. Canonical speech still holds. Layer placement correct; no upward dependency of L0–L2 on L5–L7.

---

## 23. Conformance

Narrative docs do not define correctness alone. **Conformance vectors and behaviors** do.

Any claim of **CEK-compatible** or **CEK-aligned** must demonstrate all rows below.

| Family | Must demonstrate |
|--------|------------------|
| Cap verify | Success; reject bad integrity; reject action mismatch; reject sealed-arg mismatch; reject expired |
| Single-use | Consume-before-effects; second use fails; store down fails closed when required |
| Baseline apply | Peer with minimal profile can apply projected classic Ops |
| **Baseline lowering** | Rich internal outcome is projectable to classic Ops a Baseline Peer can apply |
| Unknown meta | Ignored without failure on Baseline path |
| Unknown Ops | Policy-defined ignore / soft-fail / strict-reject; no kernel crash |
| Lineage | Record on required path (revocable Cap or endable Activity) |
| **Reverse on end** | Activity end runs reverse; failed reverse is not silent success (mark non-reversible) |
| Trace | Two Intents share trace; neither gains authority from it |
| Attenuation | Limited Cap cannot exercise removed rights |
| Peer limits | Peer cannot mint root Cap in conformance harness |

**Baseline lowering** and **Reverse on end** are mandatory for compatibility claims (not optional theater).

Optional high-assurance families: idempotent submit (production profiles, recommended); apply receipt into lineage (multi-Peer / high-assurance); hash-chained lineage (audit-focused). See [CORE/19](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CORE/19-conformance.md). CORE 25–27 freeze the *conceptual* rules for receipts, idempotency bind, and recovery Cap (optional for Baseline). Drafts under `PROPOSALS/` are not law until adopted ([CHARTER](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHARTER.md)).

Vectors are versioned alongside law version. Major law version adds a new vector suite; Baseline suite remains green during dual-speak. Implementations claim conformance only to published suites. Kill criteria: [KILL.md](KILL.md).

**Non-goals of conformance:** performance SLOs, specific crypto suite, full IFC proofs, product UX.

---

## 24. Implementation boundary

This repository is a **reader path**. Implementations claim alignment against bitplorer/cek-framework CHARTER/CORE without amending that charter by shipping code.

| In CHARTER / CORE | In a kernel / runtime |
|-------------------|----------------------|
| Axioms, vocabulary, layers | Kernel languages |
| Host / Peer *roles*; Cap / Intent / Ops *concepts* | Crate and module layout |
| Lineage, reverse, Baseline, profile as law | Cap as a typed state machine in code |
| Kill criteria, conformance *families* | Submit API surface, isolation, CI |
| Encoding-free conceptual shapes | Schema files, vector JSON, crypto / store choices |
| | How L7 callers reach Host (IPC, HTTP, in-process) |

Rename of a frozen concept, change of an axiom, a third L1 role, a third conceptual parent that redefines L0–L2, or collapsing Host and Peer into one privileged role is a **charter amendment** in [CHARTER](https://github.com/bitplorer/cek-framework/blob/eca06befbd0f30e93c47481f7aab3fae66d5a57f/CHARTER.md) — not a runtime convenience.

### IMPLEMENTATION NOTE — cek-runtime snapshot

Not law. Snapshot of [cek-runtime](https://github.com/bitplorer/cek-runtime) at commit [`50fe2af2c615ab31b35b24314915c2fb2635029f`](https://github.com/bitplorer/cek-runtime/tree/50fe2af2c615ab31b35b24314915c2fb2635029f). That tree must not weaken fail-closed Cap verify or Peer no-mint.

| CORE concept | Encoding / surface in that snapshot |
|--------------|-------------------------------------|
| **trace** groups related Intents; optional trace association on lineage | `Intent.trace` is field-only; no `TraceStore` / echo / grouping |
| Lineage under Cap **and/or** Activity; optional trace on the entry | Lineage keyed by `activity_id`; reverse via `end_activity` |
| profile as declared apply ability | Optional **stamp** = session `PairSet` / `apply_set` encoding (not a Cap) |
| Activity, Context, inject, limit, isolate, part as L2 law | Kernel focuses on Cap verify, once, idempotency, project, lineage, receipts, reverse |
| Recovery Cap as ordinary Cap for compensation | Reverse classes include `Compensation`; Host mint exists |
| Cross-Host Caps with explicit shared verify | Separate Host instances; dual-speak is `law_generation` accept window |
| Bootstrap as documented Host-only origin | `Host::mint` is the Host bootstrap / policy path |

These rows are encoding observations at that commit. They do not amend CORE, merge trace into Activity, or promote stamp to Cap.

---

## CORE map (traceability)

| CORE | Covered here |
|------|----------------|
| 00 Overview, name, non-goals | §1 |
| 01 Parents | §1 |
| 02 Intentions | §1 |
| 03 Axioms | §2 |
| 04 Vocabulary | [VOCABULARY.md](VOCABULARY.md) |
| 05 Layers | §3 |
| 06 Host / Peer | §4 |
| 07 Activity / Context | §8 |
| 08 Cap | §5 |
| 09 Lineage / reverse | §9 |
| 10 Trace | §10 |
| 11 Baseline / profile | §11 |
| 12 Change law | §19 |
| 13 Canonical story | §21 |
| 14 Security model | §16 |
| 15 Bootstrap | §15 |
| 16 Versioning | §19 |
| 17 Extensibility | §19 |
| 18 Invariants | §22 |
| 19 Conformance | §23 |
| 20 Errors / concurrency | §18 |
| 21 Intent / Result / Ops | §6 |
| 22 Sealed args | §7 |
| 23 Scenarios | §21 |
| 24 Corners | §20 |
| 25 Receipts | §12 |
| 26 Idempotency | §13 |
| 27 Recovery Cap | §14 |
