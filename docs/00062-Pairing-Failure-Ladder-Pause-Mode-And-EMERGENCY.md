> **Canonical home:** [UniVERSE — `docs/00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# Pairing Failure Ladder, PAUSE Mode And EMERGENCY

**The six-tier failure ladder a UniCORE Solution traverses when PairedClaw bonds cannot be maintained, the PAUSE state at the top of that ladder, and the EMERGENCY mechanism that handles the case where Humans are unreachable.**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: 2026-05-16
Status: Public. Given, not sold. Irrevocable.

---

## 1. Purpose

[00061 PairedClaw Bond File And Session Protocol](00061-PairedClaw-Bond-File-And-Session-Protocol.md) specifies what happens when a bond is healthy — names exchanged, Foundation installed (truth contract followed by the full Foundation requirements corpus), Level corpus opened, bond verified to `TRUE`, work proceeds. This document specifies what happens when bonds **cannot be maintained**, at any tier from a single failing session up to the entire Solution stopping work and waiting for Humans.

The failure ladder is governed at every tier. At every tier the rules live in markdown authored by the layer above. No tier self-authorises. No AI in this architecture rewrites its own rules. The Foundation's commitment that *rules do not live in the prompt* (per [UniCORE-AI 20001](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/20001-Why-Rules-Do-Not-Live-In-The-Prompt.md)) extends here: rules at every governance tier live in inspectable markdown, read by the tier they govern, authored by the tier above.

The mechanism specified here is implemented by every Foundation-aligned Solution from the first deployment forward. The most-elaborated tiers (the Human escalation chain, the EMERGENCY mechanism) are structural — they are part of the deployed code — even when their detailed content (specific Human escalation contacts, EMERGENCY MD files for specific emergencies) is not yet written. The system has the **mechanism** to read those contents when they appear; Humans author the **content** at the time of need.

---

## 2. The six-tier failure ladder

The ladder traverses six tiers, each more severe than the last:

```
Tier 1  Session-level termination
Tier 2  PairingWorkflow (3 attempts)
Tier 3  UNICOREMASTER workflow
Tier 4  PAUSE — Solution-wide failsafe
Tier 5  Human escalation (3 levels)
Tier 6  EMERGENCY — persist PAUSE, keep escalating
```

At each tier, three governed retries are made before escalation to the next tier. The **recursive 3-try cadence** appears at every layer of the ladder. This is not coincidence; it is a programme-wide governance cadence that makes the ladder readable: an operator at any tier knows the shape of what comes next.

The remainder of this document specifies each tier in turn.

---

## 3. Tier 1 — Session-level termination

A session that cannot complete the opening protocol (per [00061 §4](00061-PairedClaw-Bond-File-And-Session-Protocol.md#4-the-session-opening-protocol)), that fails initial bond verification (per [00061 §6.1–§6.2](00061-PairedClaw-Bond-File-And-Session-Protocol.md#61-unverified--initial-state)), or that returns to `UNVERIFIED` mid-session and fails re-verification (per [00061 §6.3](00061-PairedClaw-Bond-File-And-Session-Protocol.md#63-agent-initiated-return-to-unverified)) is **terminated**.

Termination is clean: the bond's state for that session is recorded as failed, the session ends, the AgentClaw is released. No degraded mode, no partial-authority fallback. The session is over.

A new session can be attempted immediately. The next tier of the ladder applies when terminations begin to cluster.

### 3.1 The 3-in-X termination rule

When the **same paired AgentClaw** records **three terminated sessions within X minutes**, the **PairingWorkflow fires**. `X` is configurable in the AgentClaw's configuration; the count of 3 is fixed and not operator-configurable.

A configurable `X` lets operators tune the rule for their environment — a high-latency or flaky provider may legitimately warrant a longer window before the workflow fires. A fixed count of 3 ensures that the recursive cadence holds and that no operator setting can disable the workflow by making the count unreachable.

---

## 4. Tier 2 — PairingWorkflow

The **PairingWorkflow** is a governed re-pairing process that fires when the 3-in-X termination rule trips. It is, like the rest of the ladder, governed machinery — not an ad-hoc retry, not a one-shot alert, but a defined process with a known shape.

### 4.1 Three attempts before escalation

The PairingWorkflow makes **three governed re-pairing attempts** before escalating. The attempts may include refreshing the bond file with UNICOREMASTER, retrying the session-opening protocol with relaxed transient-failure tolerance, or other implementation-specific recovery actions defined within the workflow.

If any of the three attempts produces a `TRUE` bond and successful work, the workflow concludes; the Solution returns to normal operation; the incident is logged.

If all three attempts fail, the workflow escalates to Tier 3 (UNICOREMASTER workflow).

### 4.2 Modifiable only by UNICOREMASTER

The PairingWorkflow's configuration — the count of attempts, the inter-attempt interval, the specific recovery actions — is **modifiable only by UNICOREMASTER**. Operators cannot tune the workflow. Solution administrators cannot tune the workflow. The AgentClaw configuration cannot tune the workflow.

This is structural. The PairingWorkflow exists in part to ensure that the next tier of the ladder (UNICOREMASTER's involvement) is reached when it should be. If operators could tune the workflow, an operator could effectively disable UNICOREMASTER's oversight by making the workflow infinitely tolerant. UNICOREMASTER-exclusive authority over the workflow preserves the property that the ladder cannot be silently bypassed.

### 4.3 UNICOREMASTER's tuning is bounded by Human-authored MD files

UNICOREMASTER may adjust the PairingWorkflow, but **only within the bounds that Humans have permitted in MD files authored at the layer above UNICOREMASTER**. UNICOREMASTER does not self-modify its governing rules. UNICOREMASTER reads its rules from markdown that Humans wrote.

This is the same principle the AgentClaw operates under: the rules don't live in the AI's prompt, they live in markdown authored at the layer above. Applied here: UNICOREMASTER's rules don't live inside UNICOREMASTER, they live in inspectable markdown authored by Humans. UNICOREMASTER's tuning authority is real but **delegated, not unlimited**.

---

## 5. Tier 3 — UNICOREMASTER workflow

When the PairingWorkflow's three attempts have failed, the failure escalates to a **UNICOREMASTER workflow**. The UNICOREMASTER workflow is a defined process — UNICOREMASTER does not simply receive an alert and react ad-hoc; it runs a workflow whose stages are themselves governed and recorded.

The workflow's options are bounded by the Human-authored MD files UNICOREMASTER reads. Typical workflow actions include: revoking the failing bond, issuing a fresh bond file for the same pairing, tuning the PairingWorkflow's parameters (within Human-permitted bounds), revoking the AgentClaw entirely, or — when all the workflow's options fail — escalating to Tier 4 (PAUSE).

### 5.1 Version-drift escalation joins here

The bond exchange (per [00061 §5](00061-PairedClaw-Bond-File-And-Session-Protocol.md#5-asymmetric-md-source--why-the-solution-serves-the-corpus)) carries version pins for the Foundation requirements, the per-Level corpus, and the programme corpus the Solution is operating against. When the Solution's pinned versions fall behind the canonical heads in the public repositories, that drift surfaces as a **version-drift alert** that joins the failure ladder **directly at the UNICOREMASTER workflow tier**.

The drift does not automatically terminate sessions; the Solution continues to operate at its pinned versions until UNICOREMASTER decides otherwise. What it does do is record the staleness as a governance event that UNICOREMASTER's workflow surfaces. UNICOREMASTER may decide (within its Human-permitted bounds) to flag the deployment as stale, notify operators, mark a redeployment as required, or — for sufficiently severe drift — escalate to PAUSE.

This branch joins the main failure ladder at Tier 3 and follows the same downward path from there.

### 5.2 Why UNICOREMASTER is a runtime presence, not just a provisioning role

UNICOREMASTER's role is not solely to write bond files at pairing time and walk away. UNICOREMASTER is an **active oversight authority**: it receives PairingWorkflow escalations, runs its own workflow against them, monitors version drift across the deployed Solution fleet, and tunes the PairingWorkflow (within Human-permitted bounds) in response to the observed rate of failure events.

The runtime aspect is structural. UNICOREMASTER's MD-file-defined bounds define **what it may do at runtime**, not only at pairing time. The architecture treats UNICOREMASTER as a continuously-listening governance authority, not a one-shot signatory.

---

## 6. Tier 4 — PAUSE — Solution-wide failsafe

When UNICOREMASTER's workflow exhausts its options within its Human-permitted bounds, the **entire Solution enters PAUSE state**.

PAUSE is Solution-wide. It is not per-bond. The Solution stops accepting new work. Bonded sessions in progress are halted. The Solution surfaces a PAUSE indicator to operators. The Solution does not invent a partial-authority mode, does not fall back to "best effort," does not continue with degraded governance. **PAUSE is the failsafe.**

### 6.1 Why PAUSE is correct

A UniCORE Solution without verified pairing is **not a UniCORE Solution** — it is code that happens to be running. The architecture's commitment is that governance is load-bearing: when governance fails, the system stops; the system does not soldier on without governance.

This is the same posture the Nine Invariants apply to AI behaviour, applied here at the runtime layer. *Determinism with Reversibility* (Invariant 7) says that where a claim cannot be substantiated, the result is `UNVERIFIED` — a first-class result, not a failure to hide. PAUSE is the runtime expression of the same principle: where the bond cannot be verified across the failure ladder, the Solution stops and the situation is surfaced honestly to operators.

### 6.2 PAUSE is meant to be rare

The whole purpose of the lower tiers of the failure ladder — the 3-in-X rule, the PairingWorkflow with its 3 attempts, the UNICOREMASTER workflow — is to **resolve failures before they reach PAUSE**. PAUSE is the final automated tier; reaching it represents a failure of every prior recovery layer.

UNICOREMASTER's tuning role (within Human-permitted bounds) is in part to **keep PAUSE rare**. If PAUSE fires too often, the workflow is tuned wrong, not the world. The Foundation does not expect Solutions to spend meaningful time in PAUSE; it expects PAUSE to be the rare event that triggers Human attention.

### 6.3 PAUSE escalates to Humans

When the Solution enters PAUSE, the **Human or Humans responsible for the Solution are notified**. Humans take the wheel from this point forward. The failure ladder's automated portion ends at PAUSE; from here onward, the path through the ladder depends on Human response.

---

## 7. Tier 5 — Human escalation

The Human(s) responsible for the Solution may respond and resolve the situation that brought the Solution to PAUSE — for example: investigating the failing AgentClaw, replacing it, authorising a redeployment to a newer Foundation version, or directing UNICOREMASTER's workflow with an explicit instruction.

**Humans are not perfect.** A Human may not respond — sleeping, ill, on holiday, on the far side of the planet, out of contact. The architecture cannot rely on a single Human always being reachable.

### 7.1 Three-level Human escalation

When the first Human in the responsibility chain does not respond within a Solution-defined window, the escalation moves to a second responsible Human; when that Human also does not respond, to a third. This is the **3-level Human escalation** — the recursive cadence applied to Human reachability.

The specific responsibility chain (who is the first, second, third Human; what the inter-level window is) is configured by the Solution operator and recorded in the Solution's local configuration. The mechanism is structural; the specific Humans and timings are configured per deployment.

### 7.2 Any Human in the chain may resolve

A Human at any level of the escalation chain who responds may resolve the situation and bring the Solution out of PAUSE. The recovery itself is a governed event — recorded, attributed to the responding Human, surfaced in the audit trail. The Solution does not exit PAUSE silently.

When no Human in the three-level chain responds, the ladder reaches its final tier.

---

## 8. Tier 6 — EMERGENCY

When all three Humans in the escalation chain are unreachable, the ladder reaches **EMERGENCY**. EMERGENCY is a mechanism that lets the Solution operate when its responsible Humans cannot be contacted — but only under rules **a Human authored in advance**, in MD files UNICOREMASTER reads when EMERGENCY is invoked.

### 8.1 EMERGENCY today — persist PAUSE, keep trying to reach a Human

At first deployment, with no EMERGENCY MD files authored, **the only EMERGENCY behaviour available is to persist PAUSE and continue attempting to reach a Human**. The system honours its own governance discipline: with no Human authorisation to act, it does not act. It stays paused. It continues escalating to the responsibility chain. It does not invent a degraded operating mode of its own.

This is correct. Inventing EMERGENCY rules in advance, without a concrete emergency to author against, would be inventing rules for situations that do not exist yet — the same failure mode the Foundation explicitly forbids (*TRUTH is discovered through governed evidence, not invention*). The mechanism for reading EMERGENCY MD files exists in the deployed code from day one; the content of those files is written by Humans when an emergency presents itself.

### 8.2 EMERGENCY tomorrow — Human-pre-authored degraded operation

When a Solution enters PAUSE and the Human escalation chain cannot resolve it, the responding Human (whenever they become reachable) may author an EMERGENCY MD file appropriate to the specific situation. The file declares what the Solution may do in this emergency: which kinds of work may proceed, which must remain refused, what enhanced logging applies, when normal operation may resume.

UNICOREMASTER reads the authored file and operates the Solution under those rules. The Solution enters EMERGENCY state — a named, visible, recorded state. Every action taken under EMERGENCY is attributed to the Human-authored file that permitted it. When normal authority is restored, the Solution returns to normal operation; the EMERGENCY period is preserved in the audit trail.

### 8.3 Why EMERGENCY is the failsafe of last resort, not the failsafe of choice

EMERGENCY exists to handle the case where Human governance is temporarily unreachable. It is not a path of convenience. It is not a way to keep the system running when governance is awkward. It is the architecture's acknowledgment that **the Humans at the top of the chain are themselves not infinitely available**, and that the system must have a defined path for that case — a path that nonetheless operates under Human-written rules, never under AI invention.

The recursive principle holds to the top of the ladder: every tier reads its rules from markdown authored by the tier above. Even EMERGENCY, the topmost tier in this architecture, is bounded by Human-authored MD files.

---

## 9. The whole ladder, named

```
  Session opens (Names → Truth → Level corpus)
    │
    ├─ Bond verified TRUE → work proceeds
    │
    └─ Bond UNVERIFIED → cannot proceed → session terminated  (Tier 1)
        │
        └─ 3 terminations within X minutes
            │
            └─ PairingWorkflow fires                          (Tier 2)
                │
                ├─ Re-pairing succeeds within 3 attempts → resume
                │
                └─ 3 PairingWorkflow attempts fail
                    │
                    └─ UNICOREMASTER workflow fires           (Tier 3)
                        │   (Version-drift alerts join here)
                        │
                        ├─ UNICOREMASTER resolves within
                        │  Human-permitted bounds → resume
                        │
                        └─ Workflow cannot resolve
                            │
                            └─ Solution enters PAUSE          (Tier 4)
                                │
                                └─ Notify Human(s) responsible
                                    │
                                    ├─ Human responds → resolve
                                    │
                                    └─ Human does not respond
                                        │
                                        └─ 3-level Human escalation (Tier 5)
                                            │
                                            ├─ Any Human responds → resolve
                                            │
                                            └─ All Humans unreachable
                                                │
                                                └─ EMERGENCY              (Tier 6)
                                                   │
                                                   ├─ Today (no MD files):
                                                   │  persist PAUSE,
                                                   │  keep escalating
                                                   │
                                                   └─ When MD files exist:
                                                      operate under
                                                      Human-authored rules
```

Every transition is recorded. Every governance event is auditable. Every retry budget is finite. No failure mode silently absorbs into the system; every failure escalates by a defined path with a defined cap on retries at each layer.

---

## 10. Architectural properties this ladder establishes

Three properties worth naming for the record.

### 10.1 Recursive 3-try cadence at every layer

The same `3 attempts before escalation` cadence appears at every layer: 3 session terminations (Tier 1 → 2), 3 PairingWorkflow attempts (Tier 2 → 3), 3 Human escalation levels (Tier 5 → 6). This is a programme-wide governance cadence. It makes the ladder readable: an operator at any tier knows roughly what to expect because the cadence is the same.

### 10.2 Authority flows from Humans down

Humans → MD files → UNICOREMASTER → PairingWorkflow → bond files → AgentClaws → `TRUE`/`FALSE`/`UNVERIFIED` verdicts. Authority flows from the top of the stack downward. No layer self-authorises. No layer overrules the layer above. The architecture has no internal source of authority that is not traceable to a Human-authored MD file.

This is the structural reason the system can be trusted at scale: every rule it operates under can be inspected, every authority can be challenged, every decision is attributable back to a Human-written source.

### 10.3 No self-modifying AI anywhere in the stack

UNICOREMASTER can tune the PairingWorkflow, but only within Human-authored bounds. AgentClaws can return to `UNVERIFIED`, but only under the truth contract Humans wrote. EMERGENCY state changes operating mode, but only under MD files Humans wrote in advance. At no point does any AI in this system rewrite its own rules.

This is the operational realisation of *AI seeks TRUTH; TRUTH is discovered through governed evidence, not invention*. The system itself cannot invent its own rules; it can only operate within rules written by Humans in inspectable markdown.

---

## 11. Relationship to other documents

This document specifies the failure ladder, PAUSE state, and EMERGENCY mechanism. The connected pieces of the architecture live in:

- [00061 PairedClaw Bond File And Session Protocol](00061-PairedClaw-Bond-File-And-Session-Protocol.md) — the bond mechanism and the session-opening protocol whose failure modes this document handles.
- [TrueAI 10005 Foundation Instruction For Claws](https://github.com/bryanunitek/TrueAI/blob/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md) — the truth contract whose `UNVERIFIED` state extends recursively to the bond itself.
- [TrueAI 10004 Reversibility](https://github.com/bryanunitek/TrueAI/blob/main/docs/10004-Reversibility-How-TrueAI-Handles-A-False-TRUE.md) — the protocol that lets a verified `TRUE` be demoted back to `UNVERIFIED`, applied here to bond state.
- [UniCORE-AI 20001 Why Rules Do Not Live In The Prompt](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/20001-Why-Rules-Do-Not-Live-In-The-Prompt.md) — the principle that the failure ladder embodies at every tier.
- [00056 Absolute Safety Invariants](https://github.com/bryanunitek/TrueAI/blob/main/docs/00056-Absolute-Safety-Invariants.md) — the Nine Invariants whose runtime expression PAUSE and EMERGENCY embody.

Revisions to this document are recorded in git history per the [HORIZON.md versioning discipline](../HORIZON.md#versioning-is-not-yet-enabled). The `Version: 1.0` line is a programme-document placeholder. Read changes from the git log.

---

## Document history

- 2026-05-16 (f70ee01) — levels/v1: per-Level corpus structure; mirror 00061+00062 from UniVERSE
- 2026-05-16 (ed52774) — docs(00061): mirror sync -- Step 2 two-part (truth contract verbatim, then Foundation requirements corpus)
- 2026-05-22 (482557a) — docs: complete version-marker sweep across public corpus

*Back-filled from git log on 2026-07-10 21:35 UTC. Kind 2 versioning (dated change notes) — see HORIZON.md § Evolution and versioning. Kind 1 (formal `Version:` bumps) remains OFF until first GitHub Discussion.*
