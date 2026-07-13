# Compaction and Durable Continuity

**The model's context window is working memory. The governed substrate is the system of record. Compaction is the rule that keeps the two from being confused.**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: 2026-05-15
Status: Public. Given, not sold. Irrevocable.

---

## 1. Purpose

A class of question about a governed AI system has the shape:

> "What happens when the model's context window fills up?"

The implied worry is that governance fails when the model can no longer "remember" the rules, the conversation, the audit trail, or the principal's identity. That worry is well-founded for systems whose governance lives in the model. For a UniCORE AI deployment, the worry is mis-located, because the rules, the audit trail, and the identity are not in the model's window in the first place.

This document names the two memory substrates a UniCORE AI deployment carries, the rule for what may compact and what may not, and the way compaction itself is recorded so a saturating window does not become a governance hole.

It is a sister document to [`20001-Why-Rules-Do-Not-Live-In-The-Prompt.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/docs/20001-Why-Rules-Do-Not-Live-In-The-Prompt.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/20001-Why-Rules-Do-Not-Live-In-The-Prompt.md)). That document names where governance lives; this one names what happens when working memory runs out.

---

## 2. Two memory substrates

A UniCORE AI deployment carries two distinct memory substrates:

| Substrate | Role | Bound to model? |
|---|---|---|
| Model context window | Working memory for the current turn or conversation | Yes — bounded by the model's window size |
| Governed substrate | System of record across turns, sessions, and model generations | No — independent of any specific model |

The model context window is the active prompt + history + retrieved material the model can attend to during inference. It is bounded by the deploying model's window size (today: order of 10⁶ tokens for frontier models; the bound is implementation-detail and changes over time).

The governed substrate is the durable surface of the deployment:

- The active governance corpus (which MD documents are in force, by hash).
- The audit trail (every read, every privileged action, immutable, append-only).
- The Business Object graph and its associated attestations.
- The principal identity and scope keys for every recorded interaction.
- The certification chain that anchors the deployment to a recognised Solution.

These are stored outside the model layer entirely, in the deployment's database, audit store, and signed-corpus surface. They are not retrieved into the model's window to "exist"; they exist regardless of what the model is doing in any given turn.

---

## 3. The rule

When the model context window approaches saturation, the deployment compacts the window's contents according to a fixed rule. The rule names a small set of items that must remain in the active window — the **pinned set** — and treats everything else as compactible.

The rule is the same regardless of the model in use, the window size of the moment, or the length of the conversation. It is a property of the deployment, not a property of the model.

A turn that runs with a compacted window is fully governed. Compaction is not a degraded mode; it is the normal way long-running interactions stay within window bounds while keeping their governance posture intact.

---

## 4. The pinned set

The following must remain in the active window across all compactions of a governed interaction:

### 4.1 Active governance corpus references

The identity and hash of every MD document currently in force for this principal, scope, and jurisdiction. The model does not need the full corpus text; it needs the reference set so retrieval can be governed.

### 4.2 Principal identity and scope key

The identified principal (under Singular Pairing) and the scope under which the current interaction is authorised. Compaction never removes the answer to "who is asking, in what scope." A turn without these is not a governed turn.

### 4.3 Pending decision graph

Any open Reasonable Governance Threshold requests, pending Human Override Protocol invocations, or unresolved attestations relevant to actions the model has been asked to consider. These are load-bearing for the next decision; compacting them would let a pending governance event silently disappear from the model's attention.

### 4.4 Active attestation surface

The current `/governance-status` snapshot — the deployment's declared governance posture at this moment, as it would be reported to an auditor asking right now. This is small, structured, and load-bearing.

### 4.5 Recent audit anchors

The most recent N audit anchors (concrete N is a deployment parameter; the rule is "the chain is not lost"). The model needs to be able to reason about the immediately preceding governed events without having to issue a retrieval for them.

Everything else may compact.

---

## 5. What compacts

Compactible content includes:

- Earlier turn history of the current conversation, summarised to a hash-anchored lossy summary with a pointer back to the durable record.
- Retrieved material from the governed corpus, retained as references rather than full text once the model has consumed it.
- Tool-call traces beyond the recent set, retained as audit anchors rather than full payloads.
- Working notes, scratch reasoning, and intermediate generated content that have not been pinned by the deployment.

Compaction is **lossy by design**. The full content lives in the audit trail and the durable record. The model's window keeps a referent; the durable record keeps the original. A later turn that needs the original retrieves it.

---

## 6. Compaction is itself a recorded event

A compaction is not an invisible housekeeping operation. It is a recorded governed event in the audit trail:

```
COMPACTION_PERFORMED
  At:                  <timestamp>
  Principal:           <principal id>
  Scope:               <scope key>
  Window size pre:     <tokens>
  Window size post:    <tokens>
  Pinned bytes:        <tokens>
  Compacted summary:   <hash>
  Source history:      <hash>
  Triggering action:   <what asked for the compaction>
```

The two hashes — compacted summary and source history — let a later auditor reconstruct what was in the window before compaction (from the source history record) and confirm that the summary the model continued with is the one the deployment generated (not a substituted one). A bad-actor scenario where the summary is tampered with is therefore detectable; the audit captures the substitution.

This is the same pattern that closes every other governance surface in UniCORE AI: the event is recorded, the record is hash-anchored, the chain is verifiable.

---

## 7. Two endpoints, two windows

A UniCORE AI deployment commonly carries a paired-window topology — for example, a MyClaw client surface and a UniCORE-Claw server surface, each with its own model and its own window.

The two windows saturate independently and are governed independently:

| Endpoint | What saturation means | What happens |
|---|---|---|
| MyClaw (client) | The user-facing model has reached its bound | Client-side compaction. The user notices only that earlier conversation is summarised. |
| UniCORE-Claw (server) | The server-side model has reached its bound | Foundation-grade compaction with audit anchor and signed summary. |

Transport encryption between the two is orthogonal. Encryption protects bytes in flight; it does not affect token counts or window bounds. A deployment that adds end-to-end encryption to the MyClaw ↔ UniCORE-Claw channel has the same compaction obligations it had without encryption.

A saturating window on one endpoint does not propagate to the other. The user can be saturated while the governed substrate is fresh, or the server can be saturated while the user's session is small. Compaction is local to the endpoint whose window is full.

---

## 8. Across model generations

The governed substrate is not bound to any specific model. A Solution begun in 2026 on a frontier model of that period must remain governable when, twenty or fifty years later, the model in use is a different one entirely. That property holds because:

- The governance corpus is on disk, hash-anchored, and re-readable by any future model.
- The audit trail is on disk, append-only, and re-readable by any future model.
- The Business Object graph and attestations are on disk and re-readable by any future model.
- The principal identity surface is on disk under Singular Pairing.

A future model with a 100M-token window reads the same governed substrate that today's 1M-token model reads. A future model with a 10K-token window does the same. The governance property does not depend on what fits in the window of the moment; it depends on what is in the durable record.

This is the property that makes 100/1000-year Solution time horizons (see [`HORIZON.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/HORIZON.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/HORIZON.md))) achievable. The substrate carries forward across model generations because it was never inside any model in the first place.

[`10003-Generation-IT-Succession.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/docs/10003-Generation-IT-Succession.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/10003-Generation-IT-Succession.md)) names the producer-side property of the same continuity: the human cohort qualified to produce Solutions carries forward across human generations. Compaction is the corresponding system-side property: the substrate the Solutions are governed against carries forward across model generations. Both are required for the time horizon to hold.

---

## 9. What this rules out

| Question | Answer |
|---|---|
| What if the window fills up mid-conversation? | Compaction. The pinned set stays; everything else is summarised and recorded. |
| What if a long conversation loses the rules? | The rules are not in the conversation. They are in the corpus reference set, which is pinned. |
| What if compaction loses audit evidence? | It does not. The audit trail is on disk, not in the window. Compaction creates an additional audit record. |
| What if a future model has a smaller window than today's? | Compaction parameters change; the rule does not. The pinned set is small enough to fit in any plausible window. |
| What if a future model has a much larger window than today's? | The rule still applies. A 100M-token window is not a license to abandon compaction; it is more headroom before the next compaction is needed. |
| What if compaction summaries are tampered with? | Detectable. The pre-compaction hash is in the audit record; the post-compaction summary is hashed against it. |

---

## 10. Scope

This document applies to UniCORE AI deployments producing governed outputs — Solutions under [`10001-Singular-Pairing-Principle.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/docs/10001-Singular-Pairing-Principle.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/docs/10001-Singular-Pairing-Principle.md)), certified deployments under [`10002-Certification-Before-Layered-Governance.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/docs/10002-Certification-Before-Layered-Governance.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/docs/10002-Certification-Before-Layered-Governance.md)), and any system claiming to satisfy the Nine Invariants.

It does not apply to:

- Personal-assistant use of an AI model outside a UniCORE Solution. Such use has whatever compaction behaviour the deployer chooses, none of which is claimed here.
- Research, exploration, or prototyping that does not claim governance properties.
- Single-turn surfaces where compaction is not reached.

---

## 11. Summary

| Property | Where it lives |
|---|---|
| Active governance corpus references | Pinned (4.1) |
| Principal identity + scope | Pinned (4.2) |
| Pending decisions | Pinned (4.3) |
| Active attestation surface | Pinned (4.4) |
| Recent audit anchors | Pinned (4.5) |
| Earlier conversation history | Compactible — full record in audit trail |
| Retrieved corpus text | Compactible — reference retained, text on disk |
| Older tool-call traces | Compactible — full record in audit trail |
| The compaction event itself | Recorded in audit trail with pre/post hashes |
| The governed substrate | On disk, independent of any model's window |

The window is working memory. The substrate is the system of record. Compaction is what keeps them in their proper places.

— Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom, May 2026.
