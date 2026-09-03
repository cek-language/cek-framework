# CEK law

Canonical published law of the Cap-Effect Meta-Language (CEK). Not a package. Not a kernel. Amendments: [CHARTER.md](CHARTER.md). Names: [VOCABULARY.md](VOCABULARY.md). Alignment: [KILL.md](KILL.md).

bitplorer/cek-framework at commit [`eca06befbd0f30e93c47481f7aab3fae66d5a57f`](https://github.com/bitplorer/cek-framework/tree/eca06befbd0f30e93c47481f7aab3fae66d5a57f) is a **historical freeze** (provenance), not a living CORE. This repository is the published SSoT. Unique rules from that freeze (CORE 00–27) are preserved here; files are not copied verbatim. No new axioms.

---

## 1. Definition

CEK is the locked law of authorized change across boundaries: how programs **ask**, **are allowed**, **carry out**, **bound**, **remember**, and **undo** change, and how runtimes participate as **Host** or **Peer**.

It is not a syntactic superset of any programming language, not a surface language people write programs in, and not named after any single kernel noun (especially not **Ops**). Official name: **CEK**. Ops is the carry-out list (data).

**Path.** Mint Cap → submit Intent → apply Ops → bound in Activity → record lineage → reverse on end → group with trace → keep Baseline.

| Problem | Answer |
|---------|--------|
| Ambient authority | Cap-only truth |
| Free side-effects | Ops-only effects |
| Ununloadable composition | Activity + lineage + reverse |
| Multi-step confused with permission | trace is correlation only |
| Flag-day interop | Baseline permanent |
| Decide / apply muddle | Host / Peer split |

**Non-goals of the law:** Cap cryptography; one process topology; a complete domain Op catalog; replacing general-purpose languages; implementation language, crate layout, CI, or isolation technology.

**Parents (informative).** One law, not two stacked frameworks. Parent-local APIs discarded; intentions kept.

| Parent | Contribution |
|--------|----------------|
| ux-channel | Intent under Cap; Result of Ops; Host/Peer; Baseline; correlation ≠ authority; fail closed |
| Cordis | Bounded composition; Context mediation; inject; limit/isolate; reversible caused change |

**Activity** replaces “Fiber”. **Baseline** replaces “Floor”. **trace** replaces correlation formerly called **flow**. **limit** is the public restriction verb; **isolate** is the structural Context-slice operation.

| Intention | Concepts |
|-----------|----------|
| Ask | Intent, submit |
| Allow | Cap, mint |
| Carry out | Ops, apply, Result |
| Bound | Activity, Context, inject, limit, isolate, part |
| Remember / undo | lineage, reverse |
| Correlate only | trace |

**trace** is orthogonal: it does not ask, allow, carry out, bound, or undo. Host/Peer support allow and carry out. Baseline/profile support permanence and negotiate-carry-out. Every kernel noun and verb appears in exactly one row.

---

## 2. Axioms

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
| **A8** | Attenuation monotonic | limit and isolate only narrow authority or visibility; they never widen it. |
| **A9** | Composition authorized | Opening an Activity or loading a part is Cap-gated (or uses an explicit minimal bootstrap root). |
| **A10** | One concept, one name | The kernel has no synonyms; documentation and code use the same primary names. |

**Exceptions that still bind.**

- **Bootstrap root** is allowed only as an explicit, minimal Host-side origin of Caps — not ambient Peer power.
- **Non-revocable, non-endable** paths may narrow lineage requirements only under explicit policy that does not become a general ambient escape.
- **Projection determinism:** for fixed Intent outcome, profile, and projection rules, Host Ops projection should be deterministic. Non-determinism belongs in L7 generators *before* commit to Result.
- **Key purpose separation:** Cap authority material ≠ transport keys ≠ optional proof / telemetry material.

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

Lower never depends on higher. L5–L7 are replaceable without changing L0–L2 meaning. L6 cannot bypass Cap verify or Ops-only emission. L0–L2 changes are charter-level. L3–L4 must preserve A6 and Baseline. Changing **trace** meaning is kernel meaning (major version + dual-speak). L5–L7 may evolve if axioms hold. L5 drivers do not mint root Caps.

---

## 4. Host and Peer

L1 has **exactly two** kernels. No third L1 kernel. Caller, bootstrap, lineage store, recovery Cap, profile, transport, and conformance harness are not kernels. Host and Peer must not collapse into one privileged role.

| Kernel | Role | Duty |
|--------|------|------|
| **Host** | Decide | Mint/verify Cap; dispatch; lineage; project; Result |
| **Peer** | Carry out | Apply Ops under profile; never mint root Caps; never invent truth |

```text
Intent + Cap  →  Host  →  Result + Ops  →  Peer
                   └── lineage / reverse (Host-owned)
```

Truth and permission are Host-side. Boundary mutation is Peer apply of Ops (plus Host lineage accounting).

### Host pipeline (ordered; no shared-world effects before the gate)

1. **Verify** Cap against the Intent (integrity, expiry, action bind, sealed args, optional subject/scopes). Refuse → zero mutate Ops.
2. **Consume** single-use and check optional **idempotency bind** before side-effects when required. Required store down → **refuse**.
3. **Dispatch** only after verify (and consume/bind).
4. **Record lineage** when the Cap is revocable or the Activity is endable (authorized set + reverse plan).
5. **Project** Ops to the Peer’s profile, falling back to Baseline.
6. Return **Result** (ordered Ops or error; authority refusal distinct from business miss when possible).

**Mint** is a Host-side privilege (including bootstrap and recovery Caps). Hosts reload authoritative state from their store for magnitudes, balances, roles; they do not trust caller-supplied world state.

### Peer duties

1. Apply Ops in listed order under profile.
2. Ignore unknown correlation/meta not required for Baseline.
3. Unknown Ops: ignore, soft-fail, or strict-reject per profile — never crash the kernel.
4. Optional **apply receipt** (landed vs failed). Receipts are not Caps.
5. Must not mint root Caps.
6. Must not invent business truth (including rewriting sealed outcomes).

### Multiplicity and hops

Many Host and Peer implementations may exist. Multiplicity does not add roles. Topology is free (in-process, split processes, hardware). A process may embed both roles as separate boundaries; mint must not live inside pure apply.

Each apply boundary is still Peer; each decide boundary is still Host (or Host-delegated under Cap). Lineage remains Cap/Activity-accountable across hops if revocation spans them. L6 may add distributed agreement; it cannot drop accountability.

### Cross-Host Caps

A Cap minted under one Host’s policy is **not** automatically authority on another Host. Cross-Host acceptance requires **explicit** shared verify policy (keys, trust domain, dual-speak window). Default: separate trust domains.

---

## 5. Cap

A **Cap** is permission to **submit** a specific class of **Intent**. Sole authority object at the kernel boundary (A1). Session, TLS identity, receipt, and trace are not Caps.

**Required binds:** action; integrity of sealed arguments; time window or equivalent validity. **Optional binds:** subject; scopes; single-use. Encoding is free; binds are law.

```text
Minted → Active → Consumed (once) | Expired | Revoked
```

| Transition | Rule |
|------------|------|
| Minted → Active | Host mint under policy (or meta-Cap) |
| Active → Consumed | Single-use consume **before** side-effects when once is required |
| Active → Expired | Outside validity under Host clock policy → verify refuses |
| Active → Revoked | Host revoke → reverse lineage tied to that Cap per policy |

Success paths must not skip verify or required consume. Replay of a Consumed once-Cap refuses. Clock skew: fail closed if outside the window under **Host** clock policy.

**mint** is Host-side or higher Cap-gated (A7). **verify** before dispatch; failure refuses (A5).

**Attenuation** only narrows: fewer actions, tighter sealed args, shorter validity, fewer scopes, fewer visible Context surfaces (A8).

**Meta-Caps** (mint, limit, or revoke other Caps) are themselves Cap-gated and lineage-tracked. They do not create ambient root power outside bootstrap policy.

```text
Mint is rare and Host-side (or meta-Cap gated).
Hold is transferable only by attenuation or explicit grant policy.
Use is Intent submit under Cap.
End is revoke Cap and/or end Activity → reverse lineage.
```

| Concept | Permission? | Groups steps? | Lifetime undo? |
|---------|-------------|---------------|----------------|
| Cap | Yes | No | Via lineage when revocable |
| trace | No | Yes | No |
| Activity | No | No | Yes — reverse on end |

---

## 6. Intent, Result, Ops

Conceptual fields. Encodings free if binds hold. Domain meaning lives in L5; law does not fix the catalog.

### Intent

| Element | Role |
|---------|------|
| **action** | What is asked |
| **args** | Arguments; sealed subset bound by Cap |
| **Cap** | Permission (when policy requires one) |
| optional **trace** | Correlation only |
| optional other meta | Ignorable on Baseline if unknown |

Without a valid Cap when required → refuse (A1, A5).

### Result

| Element | Role |
|---------|------|
| **ok** / success | Ask accepted and handled |
| **Ops** | Ordered carry-out (may be empty) |
| **error** | Failure; authority refusal ≠ business miss when possible |
| optional meta | Never authority |

Empty Ops on success is allowed (decision, no carry-out).

### Ops

1. Order is significant within one Result.
2. Ops are **data**, not code (no Baseline eval / raw-code Op).
3. Unknown Ops: ignore, soft-fail, or strict-reject per **profile** — never crash the kernel.
4. Peer apply is the mutation path for delivered Ops.

**Projection.** Host may project internal outcomes to Ops the Peer’s profile can apply, always able to fall back to Baseline. Same Intent outcome + same profile + same projection rules → projection should be deterministic.

New domain Ops: define the Op in an L5 namespace; document Baseline lowering (equivalent classic Ops or safe no-op); advertise in profile; Host projects intersection; add conformance for both paths.

---

## 7. Sealed arguments

If the caller can change arguments after grant, Cap is theater.

A Cap binds the **sealed** portion of args. Host verifies the Intent’s sealed args match the Cap bind before dispatch. Mismatch → verify failure → refuse (zero side-effects).

| Kind | Trust | Use |
|------|-------|-----|
| **Sealed args** | Bound by Cap; caller cannot alter without invalidating Cap | Identifiers, fixed quantities, grantor-approved targets |
| **Open / form args** | Not bound; caller-filled; Host re-validates | Optional fields |

Hosts reload truth from store. They do not trust caller-supplied full world state.

---

## 8. Activity and Context

**Activity** is bounded work: opens, runs (may submit Intents under Caps), ends (complete, cancel, fail, or unload). On end, Host **reverse**s its **lineage** under recovery policy.

Activity is not a Cap, not a trace, not the whole application, and not an OS thread.

**part**s load into an Activity under Caps (A9). Load and unload are accountable composition events.

Abandoned Activity: end → reverse (optional time-box policy). Completing an apply does not itself end the Activity or reverse lineage.

**Context** is the mediated visible world of an Activity. It is not ambient authority, not a Cap substitute, and not a global bag of power.

**inject** declares what the Activity requires. Undeclared access fails closed under mediation.

- **limit** — restrict what may be seen or done.
- **isolate** — separate a Context slice so names/services do not leak.

Both only narrow (A8). They do not grant a parent’s missing rights. isolate/limit apply per Activity.

---

## 9. Lineage and reverse

**lineage** is the cause trail under a Cap and/or Activity so end and revoke have a defined undo (A3).

A lineage entry conceptually ties: Cap identity; Activity identity when applicable; optional **trace** association (correlation only); action; sealed-arg integrity reference; Ops carried out (or integrity reference); a **reverse plan**.

lineage is not generic history, not full telemetry, not a Cap, and not a trace.

**Required** when the Cap is revocable, or the Activity is endable and may have caused shared-world change. Optional narrowing only under explicit non-revocable / non-endable policy that is not a general escape.

**reverse** undoes a lineage (or ends an Activity by undoing it).

| Form | Rule |
|------|------|
| **Inverse** | Direct undo of caused Ops where possible |
| **Compensation** | New Intents under a recovery Cap when true inverse is impossible |
| **Mark non-reversible** | Explicit audit when neither completes; never silent success |

Order: typically reverse causal order unless a documented compensation graph says otherwise. Cap revoke → reverse lineage tied to that Cap (policy may scope). Never report clean reverse when inverse/compensation failed without the mark.

Observe-only Ops may omit from mutate lineage if classed observe (when that optional class is adopted); otherwise treat as mutate.

### Authorized set vs landed set

| Term | Meaning |
|------|---------|
| **Authorized set** | Ops Host placed in Result after verify |
| **Landed set** | Ops Peer actually applied |
| **Apply receipt** | Peer report of landed (and optional failures) |

Receipts are not Caps (A1, A6, A7). Optional for Baseline; normative when used. High-assurance / multi-Peer profiles should use receipts.

1. Lineage records the **authorized** cause + reverse plan.
2. No receipt → reverse uses authorized set.
3. Receipt present → reverse prefers **landed** set.
4. Partial apply does not invent Host truth; Peer does not widen Ops.

| Case | Handling |
|------|----------|
| All Ops landed | Receipt matches authorized set |
| Partial land | Receipt lists landed + failed; reverse uses landed |
| Receipt lost | Treat as no receipt → reverse authorized set; may over-compensate; policy may mark uncertainty |
| False receipt | Out of kernel scope (Peer compromise); Host still bound by Cap accounting |

---

## 10. Trace

A **trace** correlates related Intents as one multi-step effort. It does not grant permission, execute, or undo (A6).

- Each step remains Intent under Cap.
- Ending multi-step work still reverses **lineage** under the relevant Activities/Caps.
- Resume uses **fresh Caps**; a trace does not revive expired permission.
- No trace is fine (single-step). Trace without Cap still grants no permission.
- Product workflow state lives in L7 storage. A trace does not make the Peer the system of record.

The concept is **trace**. Identifiers that refer to a trace are not a separate kernel noun. **flow** is not the primary name.

---

## 11. Baseline, profile, negotiation

**Baseline** is the permanent contract every correct Host/Peer pair supports: Intent under Cap; Result with ordered Ops; Host verifies; Peer applies; classic apply ability sufficient for interop. Baseline is permanence, not an object you open.

Improvements add power *above* Baseline or introduce an explicit major version. They do not silently redefine Baseline (A4). Features above Baseline may deprecate; the Baseline path remains. Removing ability is fine if Baseline clients remain valid. Prefer profile limitation over breaking Baseline.

**profile** declares what a Peer can apply. Host projects `Ops ⊆ peer ability ∪ Baseline fallback`. Missing or limited profile → Baseline projection. Profile never grants Cap authority.

Unknown-Op policy is profile-defined: tolerant (ignore/soft-fail) or strict (reject path; no kernel crash). Partial apply: profile defines stop vs continue.

**Manifest** (conceptual; encoding free):

| Element | Purpose |
|---------|---------|
| Law generation | Which law / Baseline generation is spoken |
| Profiles supported | Apply-ability names |
| Fail-closed behaviors | Once-store-down and Cap-fail refuse |
| Optional families | Receipts, idempotency (if any) |

Manifest never grants Cap. Missing manifest → assume Baseline-only Peer. Manifest drift without dual-speak is a compatibility defect.

---

## 12. Once and idempotency

**Once (single-use).** Consume **before** side-effects. Second use refuses. Required once-store down → refuse (A5, K6). Concurrent submit of the same once-Cap: at most one consume wins. Once is this Cap instance, not Cap-as-concept, not trace, not idempotency.

**Idempotency bind** (optional; not required for Baseline; recommended for production profiles). Identifies one logical ask. A later submit with the same bind, after completed or in-flight handling, does not create a second lineage cause or second mutate effect.

1. Check **after** Cap verify, **before** side-effects.
2. Required idempotency store down → refuse (A5).
3. First success records lineage once; duplicates return the prior Result (or equivalent safe replay) per Host policy.
4. Bind does not replace Cap, once, or trace.
5. Baseline Peers need not understand the bind (Host-side).

---

## 13. Recovery Cap

A **recovery Cap** is a Cap minted under Host policy whose actions are limited to compensation / cleanup for a given lineage or Activity. It is still a normal Cap: verify, sealed args, fail closed, lineage for its own effects if revocable.

1. Minted by Host (or meta-Cap), never by Peer as root power.
2. Scope is narrow: only declared compensation actions for that reverse plan.
3. Compensation Intents are ordinary Intents under the recovery Cap.
4. Compensation failure → mark non-reversible for the original cause; do not report clean reverse.
5. Bootstrap must not be a standing recovery bypass.

```text
Activity end / Cap revoke → reverse(lineage)
  → inverse Ops when possible
  → else compensation Intents under recovery Cap
  → else mark non-reversible + audit
```

---

## 14. Bootstrap

Every Cap system needs an origin of authority. Implicit bootstrap is ambient power and destroys A1/A7.

Bootstrap root is allowed only as **Host-side**, **explicit**, **minimal**, **documented**, and **not a Peer API**.

**May:** mint the first Caps required to run; open a root Activity under those Caps; install policy that governs further minting (including meta-Caps).

**Must not:** expose unconstrained “do anything” to application code by default; allow Peers to call bootstrap mint; skip lineage for later revocable work because bootstrap was trusted; become a permanent second authority path beside Caps.

```text
Cold start → Host loads bootstrap policy (out of band / config / HSM)
          → Host mints initial Caps
          → thereafter Intent under Cap only
          → bootstrap credentials stay Host-private
```

Bootstrap mint events should be distinguishable in lineage or Host audit as bootstrap-origin. Widening bootstrap (Peer-callable root mint) is a charter-level security change. Transport security alone is never Cap.

---

## 15. Security

| Boundary | Trusted for | Not trusted for |
|----------|-------------|-----------------|
| **Host** | Mint/verify policy, dispatch truth, lineage | Peer-supplied “I am allowed” |
| **Peer** | Faithful apply of accepted Ops | Root mint; inventing business truth |
| **Caller holding a Cap** | Submitting the bound Intent | Widening sealed args; replaying once-Caps |
| **trace** | Grouping Intents | Permission or execute |

**In scope**

| Threat | Control |
|--------|---------|
| Forged or tampered ask | Cap integrity bind to action + sealed args |
| Once replay | Consume before effects; store down → refuse |
| Ambient privilege | A1, A7, A9 |
| Residual effects after revoke/end | A3 lineage + reverse |
| Confused deputy / arg mutation | Sealed-args bind; Host reloads truth |
| Correlation as auth | A6 |
| Silent widening | A8 |
| Peer overreach | Ops-only apply; no root mint |
| Compatibility break as attack | A4 |

**Out of kernel scope:** side channels; full information-flow non-interference (optional L6 IFC; not Baseline); physical host compromise; social engineering of grantors; poisoned L5 drivers (still cannot bypass Cap verify if Host is correct); volume denial of service (L6/platform); false receipt (Peer compromise).

**Rules.** Never change the shared world without a verified Cap (except documented Host bootstrap mint). Never treat transport security as Cap. Never skip once-consume-before-effects. Never report successful reverse when inverse/compensation failed without a non-reversible mark. Separate key purposes.

---

## 16. Fail-closed defaults and corners

Authority fails closed. No “best effort allow.” No “just this once ambient allow.” Session/cookie/mesh membership never alone authorizes.

| Default | When |
|---------|------|
| **Refuse** | Authority uncertain; once-store down; required idempotency store down; required lineage cannot be written |
| **Ignore** | Unknown optional meta; unknown Ops under a tolerant profile |
| **Lower** | Internal outcome → Baseline Ops the Peer can apply |
| **Mark** | Reverse cannot complete |
| **Bound** | Activity end / Cap revoke → reverse what was recorded |
| **Defer to profile** | Strict vs tolerant unknown-Ops; stop vs continue on partial apply |

### Authority

| Corner | Default |
|--------|---------|
| Cap missing when required | Refuse |
| Integrity / action / sealed-args fail | Refuse |
| Single-use replay | Refuse |
| Once-store unavailable and once required | Refuse |
| Bootstrap | Host-only, minimal, explicit — never Peer |
| Idempotent retry (bind present) | Host dedupe before lineage; store down + bind required → refuse |
| Receipt absent | Reverse authorized set |
| Receipt present | Reverse prefers landed set; receipt ≠ Cap |

### Effects

| Corner | Default |
|--------|---------|
| Unknown Op (tolerant) | Ignore or soft-fail |
| Unknown Op (strict) | Reject path per policy; no kernel crash |
| Empty Ops on success | Allowed |
| Peer cannot apply subset | Partial-apply policy; do not invent Host truth |

### Composition / undo

| Corner | Default |
|--------|---------|
| Activity ends | Reverse lineage |
| Cap revoked | Reverse lineage tied to that Cap (policy may scope) |
| No true inverse | Recovery Cap, or mark non-reversible |
| Observe-only Ops | Omit from mutate lineage only if classed observe (when adopted); else mutate |

### Correlation

| Corner | Default |
|--------|---------|
| No trace | Fine — single-step |
| Trace without Cap | Still no permission |
| Resume after expiry | Fresh Caps; trace does not revive Cap |

### Interop

| Corner | Default |
|--------|---------|
| Peer has no profile | Baseline projection |
| Host speaks a newer law generation | Dual-speak / Baseline still accepted during window |
| Optional meta unknown | Ignore |

### Concurrency / time

| Corner | Default |
|--------|---------|
| Concurrent once-Cap | At most one consume wins |
| Concurrent Activities | Separate lineage unless L6 defines joint reverse |
| Clock skew on expiry | Fail closed under Host clock policy |
| Abandoned Activity | End → reverse (optional time-box) |

---

## 17. Errors and concurrency

| Class | Meaning | Handling |
|-------|---------|----------|
| **Authority refusal** | Verify failed, once replay, store down | Fail closed; no side-effects |
| **Dispatch error** | After verify: missing action, policy deny | No Ops, or explicit error Ops only under policy |
| **Apply error** | Peer could not apply some Ops | Profile: stop vs continue; report |
| **Reverse error** | Inverse/compensation incomplete | Mark non-reversible; do not claim clean reverse |

Baseline does not require one error encoding. It requires that authority refusal does not partially apply world changes.

Multiple Activities and Intents may proceed concurrently. No global lock is mandated. Required: Cap and lineage accountability per change.

1. Concurrent once-Cap: at most one consume succeeds.
2. Lineage is per cause; concurrent Activities do not merge lineage unless L6 defines joint reverse.
3. Context mediation is per Activity.
4. trace may span concurrent Intents; still grants no power.
5. Ops in one Result apply in listed order. Cross-Result order is Host/app scheduling, not ambient Peer reordering of a single Result.

Stronger isolation is L6/L7. Weaker isolation must not become Cap bypass.

---

## 18. Change, versioning, extensibility

```text
FIXED
  axioms · vocabulary · Host/Peer split · Cap-only · Ops-only
  lineage/reverse obligation · Baseline · fail closed · trace ≠ authority

MOBILE (no amendment if axioms hold)
  domain Ops · profiles · L6 policy · L7 product · Cap encoding
  transports · optional receipts/idempotency · driver quality
```

Moves occur above L2 or in encoding — never by silently redefining Intent, Cap, or Baseline. **trace** (L3) meaning is kernel meaning: major version + dual-speak + conformance. Doctrine: freeze the law; default every corner; surface may move — lower to Baseline or refuse; never ambient-allow.

| Change | Allowed when |
|--------|----------------|
| Additive L5 domain Ops | Axioms hold; Baseline Peers still correct |
| Optional L6 policy | Does not relax A1–A10 |
| Optional ignored meta | Peers may ignore; not required for Baseline |
| Kernel meaning (Intent/Cap/Ops/Activity/lineage/**trace**/…) | Major version + dual-speak + conformance |
| Primary rename of frozen vocabulary | **Forbidden** (alias only) |
| Axiom relaxation | Charter amendment |
| Trace-as-power | **Forbidden** |

| Version kind | Compatibility |
|--------------|---------------|
| Baseline behavior | Never silent change; eternal for that Baseline generation |
| Profile revision | Negotiated; fallback to Baseline |
| Domain Op namespace | Unknown Ops ignored or projected |
| Major law version | Dual-speak window required |
| Charter amendment | Explicit; logged |

**Stability.** Primary vocabulary does not rename. A Baseline-only Peer keeps working with a Host that also speaks additional profiles. New fields/ops/profiles must be ignorable or lowerable. Same name, same intention; meaning shift versions the law. Deprecate above Baseline; do not delete the Baseline path.

On major law version: Hosts that offer the new law still accept Baseline-shaped participation for a documented window; vectors exist for both shapes; window end is a published date. Library semver may move faster than law version. Do not equate a package major with a Baseline break unless it is one.

**Not frozen:** domain Op catalogs, L7 product shapes, L6 optional policies, Cap encoding (binds hold), transport.

**Allowed extensions:** new L5 Ops (projectable or ignorable); new Peer surfaces that still only apply Ops; additional profiles that only negotiate apply ability; L6 grades/budgets/quotas enforced before dispatch (cannot replace Cap); meta-Caps / policy engines (Cap-gated, lineage-tracked); compensation strategies that still reverse or mark; L7 Activities/parts (Cap-gated); optional proofs over lineage (separate key purpose).

**Forbidden:** trusted mode skipping Cap (A1); side door emit outside Ops (A2); trace as session auth (A6); Peer self-grant root Cap (A7); limit that grants more than parent (A8); plugin load without Cap (A9); second official name for Cap/Intent (A10).

**New corners.** (1) Existing default? Document; no amendment. (2) Optional policy only? L6/profile; Baseline ignore path. (3) Changes Cap/Intent/Ops/Activity/lineage/Baseline meaning? Major version + dual-speak + charter. (4) Ambient authority or free effects? Reject.

The law is complete when every kernel concept maps to an intention or correlation, every axiom has testable consequences, every known corner has a default, every moving part has a stable interface, and unknown features have a placement rule. Unfinished domain catalogs, missing implementations, and unadopted drafts are not incompleteness of the law.

---

## 19. Canonical story and scenarios

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

1. Bootstrap — Host holds minimal root policy; not ambient Peer power.
2. Open Activity — Cap-gated; Context mediated; inject; optional limit/isolate.
3. Load parts — under Caps.
4. Step — mint/use Cap → submit → verify → lineage → Result Ops → Peer apply.
5. Correlate — optional shared trace; no shared authority.
6. End — reverse Activity lineage; unload parts; release Context mediation.
7. Interop — expressible on Baseline; profiles only enlarge apply ability.

A feature that cannot enter this narrative without a new kernel noun fails the speech test. Delivery of Result/Ops is not a kernel role. In-process Host→Peer is legal.

| ID | Story |
|----|--------|
| **S1** | Single Host, single Peer. Baseline sufficient. |
| **S2** | Activity-scoped multi-step; optional shared trace; each step still needs Cap; end → reverse. |
| **S3** | Part load/unload under Cap; work produces lineage; unload/end → reverse. |
| **S4** | Profile-extended Peer: Host projects additional Ops. Baseline-only Peer: classic Ops only. Both correct. |
| **S5** | Invalid or replayed Cap → authority refusal; zero mutate Ops. |
| **S6** | Partial apply: profile stop vs continue; optional receipt into lineage. |
| **S7** | No true inverse: recovery Cap, or mark non-reversible. Never silent “fully reversed.” |
| **S8** | Bootstrap then steady state. Thereafter Intent under Cap. Peer never calls bootstrap mint. |

---

## 20. Invariants

A “no” on a required invariant blocks merge of a kernel change.

**Authority.** Shared-world change requires verified Cap (or documented Host bootstrap mint only). Session/cookie/mesh never alone authorizes. Once consumed before effects. Missing required once-store refuses. Attenuation only narrows.

**Effects.** Kernel boundary emits only ordered Ops (plus lineage accounting). No Baseline eval. Peer apply is the mutation path.

**Composition.** Activity open / part load is Cap-gated (or bootstrap). inject declares requirements; undeclared access fails. isolate/limit do not grant missing parent rights.

**Accountability.** Revocable Cap or endable Activity → lineage. Activity end triggers reverse. Failed reverse is not clean success without non-reversible mark.

**Correlation.** trace does not authorize. Each step has its own Cap. Resume does not revive dead Caps via trace.

**Interop.** Baseline path still works. Unknown optional meta ignorable. Profile cannot mint authority.

**Hygiene.** No new primary kernel synonym. Canonical speech holds. L0–L2 do not depend on L5–L7.

---

## 21. Conformance

Narrative is not correctness. **Vectors and behaviors** are. A CEK-compatible claim must demonstrate all families:

| Family | Must show |
|--------|-----------|
| Cap verify | Success; reject bad integrity, action mismatch, sealed-arg mismatch, expired |
| Single-use | Consume-before-effects; second use fails; store down refuses when required |
| Baseline apply | Minimal profile applies projected classic Ops |
| **Baseline lowering** | Internal outcome projectable to classic Ops a Baseline Peer can apply |
| Unknown meta | Ignored without failure on Baseline path |
| Unknown Ops | Policy ignore/soft-fail/strict-reject; no kernel crash |
| Lineage | Recorded on required path |
| **Reverse on end** | Activity end runs reverse; failure is not silent success |
| Trace | Two Intents share a trace; neither gains authority |
| Attenuation | Limited Cap cannot exercise removed rights |
| Peer limits | Peer cannot mint root Cap in the harness |

Baseline lowering and reverse-on-end are mandatory for compatibility claims.

Optional high-assurance families: idempotent submit (production, recommended); apply receipt into lineage (multi-Peer / high-assurance); hash-chained lineage (audit). Receipts, idempotency bind, and recovery Cap are law as conceptual rules and optional for Baseline. Unadopted drafts are not law.

Vectors version with law version. Major version adds a suite; Baseline suite stays green during dual-speak. Claims apply only to published suites. Kill gate: [KILL.md](KILL.md).

**Not conformance:** performance SLOs, specific crypto, full IFC proofs, product UX.

Encoding observations for one kernel snapshot are in [IMPLEMENTATION.md](IMPLEMENTATION.md). They are not law.
