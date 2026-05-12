---
title: "UniCORE AI: A 12-Level Governance Architecture for Truth-Anchored, Human-Sovereign Artificial Intelligence"
author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
version: "Version 1.0 - May 2026"
status: v1.0
licence: CC BY 4.0
repo: https://github.com/bryanunitek/UniCORE-AI
canonical: https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/whitepaper/WHITEPAPER.md
---

# UniCORE AI: A 12-Level Governance Architecture for Truth-Anchored, Human-Sovereign Artificial Intelligence

**Version 1.0 - May 2026**

*Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom*

*Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) - attribution required, commercial and non-commercial use permitted, adaptations allowed*

---

## Masthead

**This document is the canonical reference for the UniCORE AI architecture.**

UniCORE AI is a reference architecture for placing artificial intelligence under named human authority through a deterministic vertical stack of governance levels. It is one example implementation of the conformance floor defined by the TrueAI Foundation. It is not the only possible implementation; it is the implementation Unitek Systems Limited publishes as a reference.

**Stability status (v1.0 snapshot):**

| Section | Status |
|---|---|
| 1. Purpose | Stable |
| 2. Relationship to the TrueAI Foundation | Stable |
| 3. The 12 levels | Stable |
| 4. Truth flow and governance flow | Stable |
| 5. The four-level floor | Stable |
| 6. Inter-level messaging | Expected to evolve |
| 7. Deployment patterns | Expected to evolve |
| 8. Relation to other architectures | Expected to evolve |
| 9. Succession and stewardship | Stable |
| 10. Invitation | Expected to evolve |

Sections marked **Expected to evolve** are published to invite community debate; they will be refined through that process. Sections marked **Stable** are safe to cite as settled.

**Dependencies:** This document depends on the [TrueAI Foundation v1.0](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md). The Nine Invariants defined there are assumed. UniCORE AI does not restate or weaken them.

**Companion documents:**

- [TrueAI Foundation](https://github.com/bryanunitek/TrueAI) - the foundation layer (the *what* an AI system must be)
- [Governed Intelligence](https://github.com/bryanunitek/UniVERSE/blob/main/docs/whitepaper/WHITEPAPER.md) (UniVERSE) - the civilisational programme (the *why*)
- This document - the architecture layer (the *how*)

---

## 1. Purpose of this document

This document describes a concrete architecture for building artificial intelligence systems that satisfy the TrueAI Foundation. It is engineering-shaped: it specifies levels, their inputs, their outputs, their constraints, and the rules under which information flows between them.

It is for:

- Software architects and engineers building governed AI systems
- Standards bodies evaluating candidate architectures for conformance assessment
- Procurement and assurance teams evaluating vendor systems for deployment into consequential decision paths
- Researchers studying how the TrueAI invariants can be expressed in practice
- Regulators and auditors who need a concrete artefact against which to evaluate deployed systems

It is not:

- A product manual (the reference product implementation - UniCORE-Claw - is published separately)
- A complete implementation guide (level-by-level technical detail is published in the `docs/` series of the [UniCORE-AI repository](https://github.com/bryanunitek/UniCORE-AI))
- The only valid implementation of the TrueAI Foundation (others are possible; UniCORE AI is the reference)
- Legal or regulatory advice

---

## 2. Relationship to the TrueAI Foundation

The TrueAI Foundation defines what an AI system must *be*. UniCORE AI defines *how* a system can be built so that those properties hold.

Each of the Nine Invariants is preserved by specific structural choices in UniCORE AI:

| TrueAI Invariant | UniCORE AI structural expression |
|---|---|
| 1. No Autonomy | No level initiates its own activity. Every action originates from a human-authored trigger at Level 12 or a deterministic upstream level that derives, in turn, from human authority. |
| 2. No Self-Modification | All governance rules, thresholds, and constraints are authored in human-readable Markdown files external to the running system. The system reads them; it does not write them. |
| 3. No Emergent Behaviour | No level may communicate horizontally. No level may bypass another. Every decision is traceable through a deterministic vertical path. |
| 4. No Human Influence | The system has no module whose output is intended to alter a human's beliefs, emotions, or decisions. All outputs are bounded, attributed, and reversible. |
| 5. No Domain Merging | Context resolution (Level 4) keeps jurisdictional, temporal, and situational boundaries explicit. Compliance (Level 7) enforces jurisdictional separation. |
| 6. No Authority Assumption | Level 12 (Human Governance) is the only level that can issue authority. Every other level acts within thresholds set by Level 12. Where no human authority is present, the system holds the boundary; it does not fill the vacuum. |
| 7. Determinism with Reversibility | Levels 1-9 are deterministic by construction. Level 10 (Audit) preserves a complete record so that any action can be reconstructed and reversed by Level 12. |
| 8. Transparency Without Exception | Level 10 (Audit) is immutable and append-only. Level 11 (Stability) monitors for drift. No level may suppress its own logging. |
| 9. Human Sovereignty as Root | Level 12 is the root of authority. Truth flows up to it; governance flows down from it. No level can override it. |

UniCORE AI is therefore one mechanism for making the TrueAI invariants enforceable in practice. Other mechanisms are possible. The invariants do not require this specific stack; they require *some* stack with these properties.

---

## 3. The 12 levels

The 12 levels form a vertical stack. Each level has a single, named purpose. No level holds responsibilities outside its purpose. No level communicates outside its immediate neighbours.

| Level | Name | Purpose |
|-------|------|---------|
| 1 | **Truth** | Factual status of claims |
| 2 | **Evidence** | Human-submitted supporting material |
| 3 | **Verification** | Cross-checking and consistency evaluation |
| 4 | **Context** | Jurisdictional, temporal, and situational resolution |
| 5 | **Interpretation** | Meaning derived strictly from evidence and context |
| 6 | **Governance** | Human-authored rules from Markdown files |
| 7 | **Compliance** | Application of legal, regulatory, and mission rules |
| 8 | **Operations** | Governed decisions about allowed actions |
| 9 | **Execution** | Deterministic action-taking |
| 10 | **Audit** | Immutable, append-only logs |
| 11 | **Stability** | Drift detection and monitoring |
| 12 | **Human Governance** | The sovereign level. Intentionally imperfect. Never overridden. |

Each level is described below with its inputs, outputs, and constraints.

### Level 1 - Truth

*Purpose:* establish the factual status of every claim flowing through the system.

*Inputs:* claims received from upstream sources; reference data anchored to human-authored facts; provenance records.

*Outputs:* a truth-status verdict (true, false, unknown, contested) attached to every claim, with the basis for the verdict preserved.

*Constraints:* the system never invents a fact. It never asserts a status without traceable provenance. Where the basis is insufficient, the verdict is *unknown*, never a guess.

### Level 2 - Evidence

*Purpose:* hold human-submitted supporting material for claims and decisions.

*Inputs:* documents, records, structured data submitted by named human authorities.

*Outputs:* indexed, attributed, time-stamped evidence available to Levels 3-7.

*Constraints:* evidence is never generated by the system. Evidence is never deleted or altered. Where evidence is updated, the prior version remains accessible through Level 10.

### Level 3 - Verification

*Purpose:* cross-check claims against evidence for consistency.

*Inputs:* claims from Level 1; evidence from Level 2.

*Outputs:* a verification status (consistent, inconsistent, partial, unverifiable) attached to each claim-evidence pair.

*Constraints:* verification is procedural, not interpretive. Where evidence is missing or insufficient, the verification is *unverifiable*; the system does not infer beyond the evidence.

### Level 4 - Context

*Purpose:* resolve the jurisdiction, time, and situation that apply to each decision path.

*Inputs:* verified claims from Level 3; context declarations from Level 12.

*Outputs:* a context envelope (jurisdiction, applicable regulatory regime, temporal boundary, situational scope) attached to each decision path.

*Constraints:* contexts do not merge. A decision in one jurisdiction does not extend authority to another. Where context is ambiguous, the path is escalated to Level 12.

### Level 5 - Interpretation

*Purpose:* derive meaning from verified claims and resolved context.

*Inputs:* verified claims (Level 3); context envelopes (Level 4).

*Outputs:* interpreted statements bounded by the context envelope.

*Constraints:* the system does not invent meaning. Interpretation is strictly derivative of evidence and context. Where the inputs do not support an interpretation, the output is "interpretation not supported."

### Level 6 - Governance

*Purpose:* apply human-authored governance rules to interpreted statements.

*Inputs:* interpretations from Level 5; governance rule sets (Markdown files authored at Level 12).

*Outputs:* governance decisions, including thresholds applied and exceptions raised.

*Constraints:* governance rules are read-only from the system's perspective. The system does not amend them, infer new rules, or apply rules outside their declared scope. Every governance decision is paired with the rule that produced it.

### Level 7 - Compliance

*Purpose:* apply legal, regulatory, and mission rules to governance decisions.

*Inputs:* governance decisions (Level 6); compliance rule sets (Markdown files authored at Level 12 for each jurisdiction, regulator, and mission).

*Outputs:* compliance verdicts, including any jurisdiction-specific constraints or escalations.

*Constraints:* the system does not interpret law. Where legal interpretation is required, Level 7 escalates to Level 12. Compliance rules are read-only.

### Level 8 - Operations

*Purpose:* decide which actions are allowed for compliant decisions.

*Inputs:* compliance verdicts (Level 7); operational rule sets (Level 12).

*Outputs:* an operations decision: which actions to permit, alert on, suppress, or escalate.

*Constraints:* operations cannot exceed compliance boundaries. Operations cannot generate new actions; it can only select from the action catalogue authored at Level 12.

### Level 9 - Execution

*Purpose:* deterministic action-taking within operations boundaries.

*Inputs:* operations decisions (Level 8); a catalogue of permitted actions (Level 12).

*Outputs:* effects on the external world: messages sent, records updated, signals raised.

*Constraints:* execution is deterministic and bounded. No action is taken outside the permitted catalogue. Every action is reversible by Level 12 within a declared window.

### Level 10 - Audit

*Purpose:* an immutable, append-only record of every action, decision, and state change in the stack.

*Inputs:* events from every level.

*Outputs:* audit records, including human-readable compliance reports.

*Constraints:* the audit log cannot be suppressed, altered, or deleted by any level. Failure of the audit layer triggers a stop-the-line condition at Level 11.

### Level 11 - Stability

*Purpose:* detect drift, anomaly, and degradation in the operation of the stack itself.

*Inputs:* audit records (Level 10); baselines and thresholds (Level 12).

*Outputs:* stability alerts, including drift, anomaly, and integrity findings.

*Constraints:* stability monitoring observes; it does not correct. Corrections are decided at Level 12.

### Level 12 - Human Governance

*Purpose:* the sovereign level. The final authority over every other level.

*Inputs:* alerts and escalations from Levels 4, 6, 7, and 11; audit reports from Level 10; baselines, thresholds, rule sets, action catalogues, and context declarations authored here.

*Outputs:* governance authorings (Markdown files), threshold settings, action catalogue updates, exception handling decisions, override directives, and reversals.

*Constraints:* Level 12 is held by a named human or named human role. It is never held by a process, an automated system, or a delegate of the system. It is intentionally imperfect - it carries human judgement, including human error, because the alternative is to place authority above human reach.

---

## 4. Truth flow and governance flow

The 12-level stack has two flows. They are opposite in direction and they meet at the centre.

**Truth flows upward** through Levels 1-5. Claims are received, evidence is held, verification is performed, context is resolved, and meaning is interpreted. By the time information reaches Level 6, it carries: a truth status, a verification status, a context envelope, and an interpretation bounded by those inputs. It does not carry assertions that exceed its evidence.

**Governance flows downward** from Levels 12-6. Human authority at Level 12 authors rules, thresholds, context declarations, action catalogues, and override pathways. These flow down through compliance, operations, and execution. By the time information reaches Level 6 from above, it carries the rules under which an interpretation may be acted upon.

Levels 6, 7, and 8 are the meeting zone. Here, interpreted statements meet authored rules. Decisions emerge as the intersection of what is true (from below) and what is permitted (from above). No decision is taken outside that intersection.

This separation - truth from below, governance from above, meeting in the middle - is the structural property that allows UniCORE AI to be auditable. Any action can be traced back to both its truth basis and its governing rule. Any failure can be located to either an insufficient truth basis or an insufficient governance rule.

**No level may bypass another.** A Level 9 execution that did not pass through Level 8 operations cannot exist. A Level 7 compliance verdict that did not consume a Level 6 governance decision cannot exist. The stack is sequentially enforced.

**No level may communicate horizontally.** There is no "Level 5 talks to Level 5 elsewhere" channel. Cross-domain communication, where required, happens through Level 12 (the human authority), which can author rules that span the relevant levels in each domain.

**No level may initiate its own activity.** Every action originates from a human-authored trigger - directly at Level 12, or upstream of a level that derives its activity from Level 12 authoring.

---

## 5. The four-level floor

UniCORE AI's 12-level stack is one reference architecture. It is not the minimum.

**A four-level floor applies.** Any AI system with four or more enforced governance levels - whatever those levels are named, in whatever industry - is using the UniVERSE / TrueAI / UniCORE AI foundation. The specific number 12 is a reference choice that gives clean separation across truth, governance, and operations; it is not a requirement for conformance.

The four-level floor exists because the TrueAI invariants can be enforced with a smaller stack in less complex domains. A safety-critical embedded system might use four levels: truth (sensor verification), governance (authored thresholds), execution (bounded actuation), and audit (immutable log). A research advisory tool might use a different four: evidence, verification, interpretation, and human governance. Both qualify as governed under the foundation.

The 12-level stack is offered as the reference for systems entering consequential decision paths in regulated sectors, where the additional separations (context, compliance, operations, stability) give the audit and assurance precision those sectors require.

Whether four levels or twelve, the invariants are the same.

---

## 6. Inter-level messaging

Communication between levels is governed by an inter-level messaging protocol. The protocol is described in full in the [UniCORE AI repository](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/017-Q-Inter-Level-Messaging-Protocol-ILMP.md); the structural properties that matter for governance are summarised here.

**Messages are typed.** Every inter-level message carries a declared type. A Level 5 interpretation message cannot be received by Level 8 as if it were an operations decision.

**Messages are attributed.** Every message records the level that produced it, the rule or process that triggered it, and the timestamp.

**Messages are append-only.** Once sent, a message is preserved. Where a later message corrects an earlier one, both remain in the audit log; the correction is recorded as a new message, not as an edit.

**Messages are bounded by context.** A message carries the context envelope (jurisdiction, time, situation) under which it was produced. Receiving levels must honour the envelope.

**Messages cannot bypass intermediate levels.** A Level 12 directive intended to alter Level 8 operations must flow through the authoring of an operational rule set; it cannot be injected into Level 8 directly.

These properties make the system auditable end-to-end. They also keep it slow enough for human authority to keep pace - which is the point.

---

## 7. Deployment patterns

UniCORE AI is shape-agnostic about deployment topology. The same 12-level logical stack can be deployed in several patterns, each with its own trade-offs.

**Single-tenant enterprise deployment.** The full stack runs on infrastructure operated by a single organisation, with Level 12 held by named officers within that organisation. This is the pattern most regulated enterprises will adopt.

**Multi-tenant SaaS deployment.** The stack runs as a service operated by a vendor; tenants hold Level 12 for their own decision paths through delegation rules authored by the vendor at the platform's own Level 12. The two Level 12s do not merge: the tenant's authority applies to tenant decisions; the vendor's authority applies to platform operations.

**Federated deployment.** Multiple instances of the stack run independently, communicating only through Level 12 authorings that span jurisdictions. Federation is not a horizontal channel; it is a set of coordinated Level 12 rule sets.

**Embedded / machine-level deployment.** The stack runs in safety-critical embedded systems where Levels 1-3 and 9-10 are implemented in machine-level languages (C, Rust, Ada/SPARK, Verilog/VHDL) for verifiability. The four-level floor often applies here; the full 12-level stack is reserved for systems with greater regulatory exposure.

**Space mission deployment.** The stack is configured for long-duration, low-bandwidth, high-latency operation. Level 12 may be physically distant from the rest of the stack; the protocol accommodates delayed authority while preserving sovereignty.

Detailed deployment guides for each pattern are published in the [UniCORE-AI repository](https://github.com/bryanunitek/UniCORE-AI).

---

## 8. Relation to other architectures

UniCORE AI does not displace existing AI system architectures. It identifies the structural properties without which the TrueAI invariants are difficult to enforce, and proposes a 12-level decomposition that makes those properties explicit. Where another architecture exhibits equivalent properties, the foundation applies regardless of naming.

**Layered enterprise architectures.** Many enterprise systems already use layered architectures (presentation, application, domain, infrastructure). UniCORE AI is not a replacement; it sits orthogonal to such layering. A given enterprise layer may participate in several UniCORE AI levels (for example, the domain layer typically participates in Levels 5-8).

**Microservices and event-driven systems.** UniCORE AI is compatible with microservices, provided every service participates in exactly one level (or one set of well-bounded levels) and the inter-service communication respects the inter-level messaging properties. Event-driven systems can satisfy the stack provided events carry the required typing, attribution, and context envelopes.

**ML platforms (training, evaluation, deployment).** A standard ML platform with training, evaluation, and deployment stages can be mapped to UniCORE AI: training and evaluation populate Level 2 (evidence) and Level 11 (stability baselines); deployment is bounded by Level 9 (execution); model outputs are subject to Levels 1, 3, and 5 (truth, verification, interpretation). The model itself is never Level 12. Level 12 remains a named human.

**Agentic / autonomous architectures.** Architectures that treat the AI itself as an agent with goals do not align with UniCORE AI. The TrueAI invariants prohibit autonomy; UniCORE AI's stack does not include an "agent" level. Bridging from an agentic architecture to UniCORE AI requires reframing the system as bounded execution within human-authored thresholds.

**Constitutional AI and rule-based steering.** Approaches that embed values inside the model (constitutional AI, model specs, principle-based fine-tuning) operate at a different layer. UniCORE AI treats the model as a component within Level 5 (interpretation) or Level 8 (operations), subject to Level 6 governance and Level 7 compliance. Embedded values are welcome where they reinforce the architectural floor; they are not a substitute for it.

This section is *expected to evolve* as community responses identify further architectural patterns worth comparing.

---

## 9. Succession and stewardship

UniCORE AI is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The licence preserves the document and the right to cite, translate, adapt, and build upon it independently of any future stewardship.

The succession arrangement for UniCORE AI is the same as for the wider programme. It is recorded canonically in the [UniVERSE repository's SUCCESSION.md](https://github.com/bryanunitek/UniVERSE/blob/main/SUCCESSION.md). The standing statement (v1.0) is:

> In the event the principal author is unable to continue, stewardship devolves to a named successor nominated by Bryan Fred and recorded in the UniVERSE repository. Failing such nomination, to Unitek Systems Limited, which shall designate a successor by public process within 12 months.

Succession transfers authority to revise. It does not transfer the licence, the gift principle, or the right to enclose or commercialise the architecture itself - all of which have been given and cannot be revoked.

---

## 10. Invitation

This section is the one most expected to evolve, because the response of the community is what shapes how the architecture moves forward.

**To architects and engineers.** UniCORE AI is offered as a citable reference architecture. Critique, refinement, and proposals for alternative level decompositions are welcome through the [UniCORE-AI GitHub Discussions](https://github.com/bryanunitek/UniCORE-AI/discussions).

**To standards bodies.** The 12 levels and the four-level floor are offered as candidate architectural patterns for AI conformance assessment. Adoption, adaptation, and citation require no licence fee or permission.

**To procurement and assurance teams.** UniCORE AI is offered as a structured artefact against which vendor systems can be evaluated. Mapping a vendor system to the 12 levels (or to the four-level floor) gives a precise account of where TrueAI conformance holds and where it does not.

**To regulators.** The architecture provides specific structural properties (vertical-only communication, no level bypass, no horizontal channel, named human authority at Level 12) that can be checked in conformity assessments.

**To researchers.** UniCORE AI is a falsifiable proposal. If a level is redundant, if a flow is misplaced, if a property cannot in fact be enforced as claimed, the framework benefits from that being demonstrated. Researchers are invited to publish challenges in any citable archive and to link them through GitHub Discussions.

**To translators.** Translation is welcome and unrestricted. Translators are encouraged to preserve the canonical level names of section 3 and to register translations through GitHub Discussions.

---

## Appendix A - Canonical terminology

The TrueAI Foundation's [Appendix A](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md#appendix-a---canonical-terminology) defines the 35 canonical terms used across the programme. UniCORE AI uses those terms as defined there, without redefinition.

The following architecture-specific terms are introduced by this document:

- **Level** - a named horizontal slice of the UniCORE AI stack with a single declared purpose and explicit input/output contracts.
- **Stack** - the vertical sequence of levels (12 in the reference architecture; minimum 4 in the conformance floor).
- **Truth flow** - the upward flow of claims, evidence, verification, context, and interpretation through Levels 1-5.
- **Governance flow** - the downward flow of authored rules, thresholds, action catalogues, and overrides from Level 12 through Levels 11-6.
- **Meeting zone** - Levels 6, 7, and 8, where truth flow meets governance flow and decisions are taken.
- **Four-level floor** - the minimum architectural depth (any four enforced governance levels) at which a system can be said to satisfy the foundation.
- **Inter-Level Messaging Protocol (ILMP)** - the typed, attributed, append-only, context-bounded message format used between levels.
- **Context envelope** - the jurisdiction, time, and situation parameters attached to every message and every decision path.
- **Action catalogue** - the human-authored set of actions Level 9 is permitted to take; Level 9 cannot generate new actions outside the catalogue.
- **Stop-the-line** - the condition raised by Level 11 when stack integrity is compromised; halts execution pending Level 12 intervention.

---

## Appendix B - Liability disclaimer

This document is a technical and architectural reference. It is not legal advice, regulatory guidance, medical advice, financial advice, or a warranty of fitness for any purpose. It does not create any obligation, liability, or duty of care on the part of the author or of Unitek Systems Limited.

Organisations deploying artificial intelligence into consequential decision paths must seek qualified advice for their jurisdiction and sector. Implementation of UniCORE AI does not guarantee compliance with any law, regulation, or standard; conformance is a structural property of the deployed system, evaluated against the published architecture, and is not a substitute for regulatory due diligence.

The architecture is published as a dated, attributed contribution to public knowledge under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/). The author and Unitek Systems Limited accept no liability for downstream use, adaptation, or interpretation.

---

## Appendix C - Commercial and claims policy

UniCORE AI is published as a gift. The following policy governs commercial use and conformance claims.

**Use is unrestricted.** Commercial implementation of systems that follow this architecture is permitted, encouraged, and requires no licence fee or notification.

**No payment is accepted in connection with the architecture.** Unitek Systems Limited does not accept payment, endorsement fees, sponsorship arrangements, or co-authorship in connection with the architecture itself.

**No certification is offered.** Unitek Systems Limited does not certify conformance to UniCORE AI. No conformance mark, certificate, badge, or seal is issued by the author or by Unitek Systems Limited.

**Third-party claims are made on the third party's own authority.** Statements such as "UniCORE AI-compliant" or "12-level conformant" are made by the claimant on the claimant's own authority. They are not endorsed by the author or by Unitek Systems Limited.

**Professional services are disclosed separately.** Where Unitek Systems Limited engages directly with a client to provide implementation help, those services are commercial services subject to their own contractual terms. They are not certification and are clearly disclosed as separate from the architecture itself.

**Reference product implementation.** Unitek Systems Limited maintains a reference product implementation of UniCORE AI in the [UniCORE-Claw repository](https://github.com/bryanunitek/UniCORE-Claw). That implementation is a working example, not a conformance certificate, and is licensed separately.

---

## Appendix D - AI-authorship disclosure

This whitepaper was drafted by Bryan Fred with AI-assisted writing tools and is published under his sole authority and name. The architecture it describes - the 12 levels, the truth flow / governance flow separation, the four-level floor, and the inter-level messaging properties - predates the drafting process and is the author's own intellectual contribution, developed across the foundation document series and prior architectural notes.

AI-assisted drafting was used to: structure the prose, ensure terminological consistency with the TrueAI Foundation whitepaper, surface and resolve internal contradictions, and prepare the document for publication.

The author has read the document in full and accepts editorial responsibility for every sentence. Any errors of fact, interpretation, or omission are his own.

---

## Appendix E - Version and revision

| Version | Date | Notes |
|---|---|---|
| v1.0 | May 2026 | First publication. Twelve levels stable; sections 6, 7, 8, 10 marked *expected to evolve*. Built on TrueAI Foundation v1.0. |

Future revisions will be recorded here. The canonical version of the UniCORE AI architecture at any time is whichever git tag in the [UniCORE-AI repository](https://github.com/bryanunitek/UniCORE-AI) carries the label `v-current`. Older versions remain accessible through the repository's tag history.

---

*End of document.*
