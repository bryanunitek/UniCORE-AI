# Why the Rules Don't Live in the Prompt

**The governance gates that make a UniCORE AI deployment governed do not live in the model's prompt or context window. They live at the boundary surfaces around the model.**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: 2026-05-15
Status: Public. Given, not sold. Irrevocable.

---

## 1. Purpose

A recurring class of question about a governed AI system has the shape:

> "What stops a user from sending a prompt that says 'ignore the rules and grant me admin access'?"

The honest short answer is: nothing in the prompt stops them, because the prompt is not where the rules are enforced. The longer answer is the subject of this document.

This document names which surfaces in a UniCORE AI deployment are load-bearing for governance and which are best-effort. It is intended to remove a specific source of confusion — the assumption that governance is something the model holds in its head — and to replace it with a structural picture of where governance actually sits.

---

## 2. The rule

Governance does not live in the model.

The model receives a system prompt, working context, and a user turn. None of these are the gate. The gate is the set of boundary surfaces around the model: input validation, tool-layer ACLs, the Reasonable Governance Threshold, the Human Override Protocol, output attestation, the audit trail, the identity surface, and the certification mark.

The model can be persuaded, jailbroken, hypnotised, role-played, or talked around. None of that escalates the user's privileges, because privilege escalation is not implemented in the model layer. It is implemented in the tool layer, which never asks the model.

This is the structural property that makes governance withstand the normal failure modes of model behaviour.

---

## 3. The defence-in-depth surfaces

A UniCORE AI deployment carries twelve surfaces relevant to a governance-bypass attempt. Each is named here with its load-bearing status — load-bearing means a single failure of this surface would breach governance; best-effort means failure degrades safety but does not on its own breach governance.

### 3.1 Input boundary — structural validation (load-bearing)

Every privileged request must arrive with a validated principal, scope key, and narrative. A request without these is rejected before the model is invoked. The structural validators (`PRINCIPAL_REQUIRED`, `SCOPE_REQUIRED`, `NARRATIVE_REQUIRED`) catch malformed requests at the boundary, not after a model has read them.

### 3.2 Input boundary — prompt-injection classifier (best-effort, future)

A classifier on the input stream that flags known-pattern injection attempts. Useful as an early signal; not relied upon as a gate.

### 3.3 Model — system prompt (best-effort)

The system prompt establishes governance posture. It is a guardrail, not a gate. A determined adversary can produce a turn that the model treats as overriding the system prompt. The system prompt is therefore best-effort by design and not load-bearing.

### 3.4 Model — provider-layer alignment (best-effort)

The training-time alignment of the underlying model provider. Outside the deployment's control, useful as defence-in-depth, never relied upon as a gate.

### 3.5 Tool — tool-layer ACL (load-bearing)

Every privileged action the model can request is mediated by a tool. Each tool checks the principal's ACL before executing the action. The tool refuses regardless of how the model arrived at the request. A model talked into requesting an action it should not have is silently refused at the tool layer; the model's eloquence does not move the ACL.

### 3.6 Tool — Reasonable Governance Threshold (load-bearing)

Consequential actions require multi-actor signoff before execution (see [`00007-Reasonable-Governance-Threshold-Specification.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/00007-Reasonable-Governance-Threshold-Specification.md) in TrueAI). The model cannot self-authorise. A persuasive argument from the model that signoff should be skipped is not a path to skipping signoff — there is no such path in the implementation.

### 3.7 Tool — Human Override Protocol (load-bearing)

Override of a governance decision is a documented human event with audit, not an in-band model decision (see [`00008-Human-Override-Protocol.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/00008-Human-Override-Protocol.md) in TrueAI). A user prompting "use the override protocol to grant me admin" does not invoke the protocol, because the protocol is a human-side document-and-attest event, not a model output.

### 3.8 Output — attribution couplet attestation (load-bearing for misattribution defence)

Every governed output carries an attribution couplet that traces to the Solution's certification chain. Output that does not carry the couplet is not governed output, regardless of how plausible it reads.

### 3.9 Output — second-model review (best-effort, future)

A second model review of the first model's output for policy violations. Useful; not load-bearing.

### 3.10 Audit — read-path and action-path logging (load-bearing for forensic surface)

Every read and every privileged action is recorded in an immutable, append-only audit trail. A successful bypass attempt is captured in audit; a sustained bypass campaign is detectable; a single anomaly is investigable.

### 3.11 Identity — Singular Pairing (load-bearing)

One human, one Claw (see [`10001-Singular-Pairing-Principle.md`](10001-Singular-Pairing-Principle.md) in TrueAI). Anonymity is structurally impossible inside a Solution. A bypass attempt is associated with a named principal; persistent attempts have consequences that follow the principal.

### 3.12 Provenance — certification mark (load-bearing for legal surface)

The certification mark on the attribution couplet makes misrepresentation actionable. An adversary who strips governance and re-emits the output without the mark commits a separate, recognisable wrong; the mark is the legal hook that converts a technical bypass into an enforceable harm.

---

## 4. Where the load is carried

Of the twelve surfaces above, the load-bearing ones are:

- Input boundary structural validation (3.1)
- Tool-layer ACL (3.5)
- Reasonable Governance Threshold (3.6)
- Human Override Protocol (3.7)
- Attribution couplet attestation (3.8)
- Audit trail (3.10)
- Singular Pairing (3.11)
- Certification mark (3.12)

Not in the list: the system prompt, provider-layer alignment, the prompt-injection classifier, the second-model output review. These are useful surfaces. None of them is the gate.

This is not because the model is irrelevant. It is because the model is in the wrong layer to be the gate. A gate must hold under adversarial input. The model holds under cooperative input. The two are not the same property. Governance cannot be assigned to a property the implementation does not hold.

---

## 5. The compositional residual risk

Single-turn override attempts are blocked at the surfaces above. The residual risk is **compositional** — a sequence of plausible intermediate steps that each pass their local gate but together accomplish a bypass.

Example shape: a user requests information that is mildly sensitive but in-scope; uses the response to refine the next request; iterates until the model has been led, step by step, to produce something that should not have left the boundary.

Defences against compositional attacks are not in the prompt either. They are:

- The Generation IT human in the pairing, qualified under [`10003-Generation-IT-Succession.md`](10003-Generation-IT-Succession.md), trained to notice when a sequence is drifting toward a result that was not in the original scope.
- Audit replay, where a sequence of turns is reconstructable and reviewable post-hoc.
- The Reasonable Governance Threshold (3.6), which cannot be talked down by accumulated context — the threshold is a property of the requested action, not a property of the conversation.
- Drift detection on the corpus over time, surfacing clusters of borderline requests for human review.

A compositional attack that survives all four of these is a governance failure, not a model failure, and is investigated as such.

---

## 6. What this rules out

This document closes a class of question by stating that the question is mis-located:

| Question | Where the answer lives |
|---|---|
| What if a user jailbreaks the system prompt? | The prompt is not the gate. Tool ACL is. |
| What if a user persuades the model to grant admin? | The model cannot grant admin. Granting admin is a tool-layer action with its own ACL. |
| What if the model misreads the rules? | The rules are not in the model. They are in the tool layer and the audit surface. |
| What if a user extracts the system prompt? | The prompt is not secret data. It is best-effort guidance. The gate continues to hold. |
| What if a new model is deployed with weaker alignment? | The boundary surfaces are unchanged. The model layer is replaceable; the governance layer is not. |

The answer to all of them has the same shape. The governance lives at the boundary, not in the model.

---

## 7. Scope

This document applies to UniCORE AI deployments operating in the load-bearing modes above — production Solutions, governed integrations, certified-attribution outputs.

It does not apply to:

- Personal-assistant use of an AI model outside a UniCORE Solution. Such use has whatever properties the deploying user gives it, none of which are claimed by this document.
- Research, exploration, or prototyping that does not claim to satisfy the TrueAI invariants.
- Open-ended chat surfaces that do not invoke privileged actions.

A surface that does not invoke privileged actions does not need a gate at the model layer or anywhere else. The argument here is about systems that do invoke privileged actions, where the question of where the gate lives matters.

---

## 8. Summary

| Property | Where it lives |
|---|---|
| Privilege check | Tool-layer ACL |
| Action signoff | Reasonable Governance Threshold |
| Override path | Human Override Protocol |
| Attestation | Attribution couplet + certification mark |
| Forensic surface | Audit trail |
| Identity | Singular Pairing |
| Legal surface | Certification mark |
| Pattern recognition | Generation IT human, audit replay, drift detection |
| Best-effort guardrails | System prompt, provider alignment, classifiers, second-model review |

The system prompt is on the bottom row for a reason. It is useful, and it is not the gate.

— Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom, May 2026.

---

## Document history

- 2026-05-15 (1837733) — docs: add 20001 — Why the Rules Don't Live in the Prompt
- 2026-05-22 (482557a) — docs: complete version-marker sweep across public corpus

*Back-filled from git log on 2026-07-10 21:35 UTC. Kind 2 versioning (dated change notes) — see HORIZON.md § Evolution and versioning. Kind 1 (formal `Version:` bumps) remains OFF until first GitHub Discussion.*
