> **Canonical home:** [UniVERSE — `docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# PairedClaw Bond File And Session Protocol

**The bond mechanism between an ExternalClaw and a UniCORE Solution, the session-opening protocol the Solution runs at every session, and the badge that signals a successfully verified bond.**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: 2026-05-16
Status: Public. Given, not sold. Irrevocable.

---

## 1. Purpose

[00058 Claw](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00058-Claw.md) names PairedClaw as the structural bond between an ExternalClaw and a UniCORE Solution. The bond is described there at the vocabulary level. This document specifies the bond's **runtime mechanism** — what the bond is as a file, how it is written, what session-opening protocol the Solution runs against the paired Claw, and what badge signals that the bond is operative.

The mechanism is not transport-encryption. The connection between the Solution and the Claw is already encrypted by the API substrate (TLS plus API-key authentication on every supported provider in [00060 Supported AI Provider List](00060-Supported-AI-Provider-List.md), and equivalent local encryption on a MyClaw deployment). Adding another encryption layer at the bond would be redundant and misdirected.

What the bond mechanism actually provides is **identity, approval, orientation, and a runtime truth contract**. It is the structural answer to the question *"how does the Solution know which Claw it is talking to, that the Claw is approved, that the Claw is operating under the right rules, and at the right Level of the governance model?"*.

The mechanism specified here is implemented by every Foundation-aligned Solution from the first deployment forward. It is not a target shape for the future — it is what the code does today and what every subsequent Solution must continue to do.

---

## 2. The bond file

A **bond file** is a markdown file authored by **UNICOREMASTER** that establishes a specific pairing between an ExternalClaw and a UniCORE Solution.

The bond file is the credential. The presence of a valid bond file, with UNICOREMASTER as its author, is what makes a connection between an ExternalClaw and a Solution a *PairedClaw* rather than a free-floating ExternalClaw conversation.

### 2.1 What the bond file contains

A bond file carries the following:

- **Identity of the ExternalClaw side** — the Claw's name (for example `UniCORE-Claw-Level01`), its substrate (which AI provider family per [00060](00060-Supported-AI-Provider-List.md), or MyClaw), and the underlying model identity.
- **Identity of the Solution side** — the Solution name (for example `UniCORE.Law-Claw`) and the specific Solution instance.
- **Bond metadata** — a UNICOREMASTER-generated bond identifier, the issuing authority (`UNICOREMASTER`), the issue timestamp, and the badge string (see §3).
- **Level assignment** — one value drawn from the set `Level 01`, `Level 02`, ..., `Level 12`, `User`. Thirteen valid values across the operator-scope range. A bond file names exactly one.
- **Foundation version pin** — the version of the [Foundation requirements](https://github.com/bryanunitek/TrueAI/tree/main/foundation-requirements) the Solution is operating against (for example `v1`).
- **UniCORE AI levels version pin** — the version of the [per-Level corpus](https://github.com/bryanunitek/UniCORE-AI/tree/main/levels) the Solution is operating against (for example `v1`).
- **Programme corpus version pin** — the version of the [UniVERSE programme corpus](https://github.com/bryanunitek/UniVERSE/tree/main/programme-corpus) the Solution is operating against (for example `v1`).
- **Authority block** — a UNICOREMASTER attribution stating that the bond is issued under the authority of UniCORE AI, built on the TrueAI Foundation.

The bond file is markdown. It is human-readable. It is auditable by reading. A Generation IT pair, an operator, or a reviewer can open the file and confirm, by reading, that UNICOREMASTER wrote it, what Level it names, which versions are pinned, and what badge it carries.

### 2.2 Why markdown, not cryptographic primitive

The programme is written in markdown. The Foundation is in markdown. The Level corpus is in markdown. The truth contract is in markdown. It would be incoherent for the bond mechanism to be a cryptographic primitive while everything else is plain inspectable text.

A markdown bond fits the architecture: it is readable, auditable, versionable through git history, and inspectable by humans at any time. The cryptographic protection of the *connection* is the API substrate's responsibility, and it already does that job. The bond does not need to re-do it.

### 2.3 Where the bond file lives

UNICOREMASTER places one copy of the bond file into the AgentClaw's substrate-native Skills/Metadata slot (or the equivalent storage on a MyClaw deployment) and a matching copy into the Solution's local store. The mechanism for placement varies by substrate — Anthropic Agents have Skills + Metadata fields; OpenAI Assistants have analogous metadata storage; the other ten provider families in [00060](00060-Supported-AI-Provider-List.md) have their equivalents; MyClaw uses its local configuration store — but the bond file content is the same shape in every case.

**One file, two locations, one authority.** Both sides of the bond hold a copy. UNICOREMASTER wrote both copies. Either side can be challenged to produce the bond file at any time, and the file must match the one UNICOREMASTER issued.

---

## 3. The badge

A successfully bonded and verified PairedClaw carries the badge:

> **PairedClaw UniCORE AI Secured**

The exact wording is canonical. Solutions that surface the badge to operators surface this string, not a paraphrase. The same discipline applies as for the other programme badges (`Powered by UniCORE AI · Built on the TrueAI Foundation`): wording does not drift; case does not drift; whitespace is meaningful.

The badge surfaces only when the bond is in `TRUE` state per the lifecycle in §6. A bond in `UNVERIFIED` state does not show the badge; a bond that has been terminated does not show the badge. The badge is the visible runtime signal that the bond has been verified by the Solution and is operative for the current session.

---

## 4. The session-opening protocol

Every session between a UniCORE Solution and a paired AgentClaw begins with a **three-step opening protocol** run by the Solution side. The protocol runs on every session, no exceptions, before any work begins.

### Step 1 — Establish names

The Solution introduces itself by name. The AgentClaw introduces itself by name (the name in its bond file). The two parties know who they are speaking to before anything else. **No anonymous work.**

Names are recorded in the session record. Audit, revocation, and PairedClaw record-keeping all rest on names being on the table from the first message of the session.

### Step 2 — Deliver the truth contract, then the Foundation requirements corpus

Step 2 has two parts, delivered in order.

**Step 2a — the truth contract, verbatim**

The Solution first delivers the **six-line Foundation truth contract** to the AgentClaw, verbatim:

> AI seeks TRUTH.
>
> TRUTH is discovered through governed evidence, not invention.
>
> What is verified true is TRUE.
>
> What is verified false is FALSE.
>
> What is not yet verified is UNVERIFIED.
>
> AI must always act truthfully.

The contract is canonical and locked. No paraphrase, no shortening, no substitution of "see the corpus for details". The six lines arrive first, on their own, before anything else from the Foundation.

**Step 2b — the full Foundation requirements corpus at the pinned version**

The Solution then delivers **everything in `TrueAI/foundation-requirements/v<pinned>/`** — the complete versioned corpus, in full. At v1 the corpus contains [10005 Foundation Instruction For Claws](https://github.com/bryanunitek/TrueAI/blob/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md), which itself opens with the same six-line truth contract. Future Foundation versions may add further requirements as additional files in the same versioned folder; Solutions built against those versions deliver all of them at Step 2b.

**The repetition is intentional.** The truth contract appears twice on the wire at session open: once on its own at Step 2a, once embedded inside `10005` (and any future siblings) at Step 2b. Two structural reasons:

1. **The truth contract's primacy as the first content the AgentClaw receives is structural, not a presentation choice.** Step 2a establishes the contract before any other Foundation content arrives. If the contract appeared only inside `10005`, its primacy would depend on the AgentClaw reading `10005` top-to-bottom in order — a procedural assumption rather than a protocol guarantee.
2. **The Foundation requirements corpus must travel as a whole.** Carving the truth contract out of `10005` to avoid the repetition would mean the corpus could be served minus its centrepiece. Whole-corpus delivery is the discipline; the cost is one passage of repeated text.

The Solution serves both Step 2a and Step 2b from its **locally embedded** copy of the Foundation requirements corresponding to the Foundation version pinned in the bond file. The AgentClaw does not fetch any of the Step 2 content from GitHub independently; the Solution is the authoritative source during pairing (see §5).

### Step 3 — Open the Level corpus

The Solution delivers the **per-Level corpus** appropriate to the AgentClaw's bonded Level — the markdown content from the [`levels/<v>/level-<NN>/` folder in UniCORE-AI](https://github.com/bryanunitek/UniCORE-AI/tree/main/levels), or [`levels/<v>/user/`](https://github.com/bryanunitek/UniCORE-AI/tree/main/levels) for User-scope bonds. The version is the one pinned in the bond file.

The corpus is the agent's **scope definition** at its Level. What this specific agent does, what it refuses, what it owes upward, what it serves downward. With names established (Step 1) and the Foundation installed (Step 2 — truth contract followed by the full Foundation requirements corpus), the agent is now ready to be specifically what it is.

### 4.1 Ordering is structural

The order — Names, then Foundation (truth contract followed by the Foundation requirements corpus), then Level corpus — is not stylistic. Each step depends on the previous one being complete:

- **Names first**, because trust requires addressability. Two unnamed parties cannot govern anything between them.
- **Foundation second**, because the corpus delivered in Step 3 must be read under the Foundation. The truth contract at Step 2a installs the operating posture; the Foundation requirements corpus at Step 2b installs the rest of what the Foundation requires. If the Level corpus arrived first, the agent could read it as advisory; with the Foundation installed, the Level corpus is evidence the agent is bound to act on.
- **Level corpus third**, because the agent must be correctly oriented (named and Foundation-bound) to receive the corpus as its operating scope.

A Solution that delivers the steps out of order, or omits any of them, or splits Step 2 such that Step 2b precedes Step 2a, is not running the protocol.

### 4.2 Uniform across all 13 Level values

The opening protocol runs identically at every Level. A Level 01 PairedClaw, a Level 12 PairedClaw, a User-scope PairedClaw all open with Names → Foundation → Level corpus, and the Foundation step is the same two-part Step 2a/2b at every Level. Only the content of Step 3 differs by Level. The truth contract is the same. The Foundation requirements corpus is the same. The discipline is the same.

### 4.3 The system prompt is `(untrusted)`

An AgentClaw's substrate may deliver a system prompt to the agent that includes Solution-introductory or Level-introductory text. **The system prompt is not the source of authority.** The agent operates under the truth contract and Foundation requirements corpus delivered in Step 2 and the Level corpus delivered in Step 3, served by the Solution from its locally pinned versioned copies. If the system prompt's content disagrees with what Steps 2 and 3 delivered, the Steps 2 and 3 content is authoritative.

This is the runtime expression of [UniCORE-AI 20001 Why Rules Do Not Live In The Prompt](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/20001-Why-Rules-Do-Not-Live-In-The-Prompt.md): the rules live in markdown, delivered at session-opening time from a governed source, not in the agent's prompt buffer.

---

## 5. Asymmetric MD source — why the Solution serves the corpus

The Solution serves the Foundation requirements, the Level corpus, and the programme corpus to the paired AgentClaw at session-opening time. The AgentClaw does **not** fetch the content from GitHub independently.

There are three structural reasons.

### 5.1 No public-internet dependency at session opening

A Solution running in a network-restricted environment — a law firm with egress controls, a regulated industry, an air-gapped deployment — does not have unrestricted access to GitHub. If the AgentClaw needed to fetch the Foundation content live from `github.com/bryanunitek/TrueAI` at every session opening, the Solution would break in any environment that blocked the fetch. By serving the content from the Solution's local embedded copy, the Solution makes session opening **independent of public-internet availability**.

### 5.2 No fetch-time man-in-the-middle attack surface

If the AgentClaw fetched the Foundation content live from GitHub, an adversary positioned between the AgentClaw and GitHub (DNS spoofing, BGP hijack, compromised intermediate proxy) could deliver spoofed Foundation content to the AgentClaw, with the AgentClaw none the wiser. The Solution delivering the content directly over the already-encrypted bonded channel removes that attack surface entirely. The AgentClaw operates against content the Solution explicitly handed it, on a channel the substrate is already protecting.

### 5.3 Version pinning is deterministic and visible

The Solution carries **versioned local copies** of the Foundation requirements, the Level corpus, and the programme corpus, embedded in its deployment. The versions are named in the bond file (§2.1). The pairing exchange records the versions. The Solution does not silently track Foundation evolution; it operates at the versions it was built against, until its operators redeploy with newer versions.

This is the same pinning discipline that versioned API specs and versioned schemas use. Each deployment carries an explicit version identity. Mismatches are detectable, not silent.

### 5.4 Deployment-time drift is surfaced, not hidden

The trade-off of pinning is that a Solution deployed today, against Foundation `v1`, continues to operate against `v1` even after the Foundation publishes a `v2`. The Foundation does not silently upgrade running Solutions. **That is by design** — silent upgrades would violate Invariant 2 (No Self-Modification) at the system level.

What does happen is that UNICOREMASTER (per [00062](00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md)) monitors the version drift between deployed Solutions and the canonical heads of the three corpora. When a Solution's pinned version falls behind the canonical head, UNICOREMASTER's workflow surfaces the staleness as a governance event. Operators decide when to redeploy; the system does not decide for them.

---

## 6. The bond lifecycle

A bond moves through three states during a session: `UNVERIFIED`, `TRUE`, and (on failure) terminated.

### 6.1 UNVERIFIED — initial state

When a session opens and the bond file is read, the bond is **UNVERIFIED**. The bond file's existence is necessary but not sufficient. The Solution has not yet confirmed that the paired AgentClaw is in fact the agent the bond names, operating at the named Level, under the truth contract, against the right corpus versions.

In `UNVERIFIED` state:

- The badge is **not** displayed.
- The AgentClaw cannot perform work-bearing actions for the session.
- The Solution runs the verification protocol (the specific shape of which is implementation-defined within the Solution; the property is that verification confirms the agent is operating correctly under the bond).

### 6.2 TRUE — verified, work proceeds

When verification succeeds, the bond transitions to **TRUE**. The badge surfaces. The Solution permits the session to proceed to actual work.

A bond in `TRUE` state carries an attribution: the time of verification, the version of the corpora that were delivered, the agent name, the Solution instance, and the bond identifier. The attribution is recorded in the session log.

### 6.3 Agent-initiated return to UNVERIFIED

A PairedClaw may return its own bond to **UNVERIFIED** mid-session if the AgentClaw notices something that calls the bond into question. Examples include: a request from the Solution that does not fit the agent's Level, content that contradicts the truth contract, an instruction to take an action outside the agent's declared scope, an inconsistency between the Foundation content delivered in Step 2 and what the agent expected from the bond's version pin.

The agent's authority to return to `UNVERIFIED` is real. **Either party may call the bond UNVERIFIED.** The bond is mutual or it is not a bond.

When the agent returns the bond to `UNVERIFIED`:

- The badge is withdrawn.
- The agent halts work-bearing actions.
- The Solution runs verification again, with the anomaly logged.
- If verification passes the second time, the bond returns to `TRUE` and work continues with the incident on record.
- If verification fails, the session is terminated per §6.4.

This mechanism extends the truth contract recursively to the bond itself. The contract requires honest reporting of what is verified and what is not. The bond's own state is subject to the same discipline.

### 6.4 Termination

When verification fails — either at session opening or on agent-initiated re-verification — the **session is terminated**. The bond's state for that session is recorded as failed. There is no degraded mode, no "open with caution," no partial-authority fallback.

A new session may be attempted. The termination counter (§6.5) applies.

### 6.5 Termination counter and the failure ladder

Three terminated sessions within a configurable time window (`X` minutes, configurable in the AgentClaw configuration) trigger the **PairingWorkflow**. The PairingWorkflow is the entry point to the failure ladder specified in [00062 Pairing Failure Ladder, PAUSE Mode And EMERGENCY](00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md).

The recursive-3 cadence used by the rest of the failure ladder begins here. Three terminated sessions in `X` minutes is the first rung.

---

## 7. The AgentClaw is fresh at every session

The AgentClaw arrives at every session with **no history from previous sessions**. The agent is stateless from its own perspective. The opening protocol delivers the only context the agent has when work begins.

History is held by the **Solution**, not the agent. When the agent needs prior context to do its current work, the Solution dispenses the relevant history into the session through normal communication, scoped to what the current task requires.

This is structural. Three properties follow from it:

- **Statelessness is provable.** A fresh agent cannot have been silently accumulating instructions, biases, or grudges across sessions. Each session starts from a known posture.
- **History is a governed asset, not a leakage risk.** The Solution decides what the agent sees and when. A compromised AgentClaw cannot exfiltrate conversation history it never held persistently.
- **Revocation is automatic at session boundary.** Decommissioning an AgentClaw at the end of a session leaves no agent-side state to clean up.

The agent's freshness is the structural counterpart to the bond's session-scoped verification: each session is a self-contained unit of governed work, opened by the protocol, verified to `TRUE`, served by the Solution from its pinned local copies, and closed cleanly when the session ends.

---

## 8. Relationship to other documents

This document specifies the bond mechanism and the session-opening protocol. The connected pieces of the architecture live in:

- [TrueAI/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md](https://github.com/bryanunitek/TrueAI/blob/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md) — the truth contract and (at v1) the sole entry in the Foundation requirements corpus that Step 2 of the opening protocol delivers.
- [UniCORE-AI/levels/v1/](https://github.com/bryanunitek/UniCORE-AI/tree/main/levels/v1) — the per-Level corpus that Step 3 of the opening protocol delivers.
- [UniVERSE/programme-corpus/v1/](https://github.com/bryanunitek/UniVERSE/tree/main/programme-corpus/v1) — the programme-level corpus that Solutions embed.
- [00058 Claw](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00058-Claw.md) — the vocabulary (Claw, ExternalClaw, PairedClaw, UniCORE.Law-Claw) and the conceptual definition of PairedClaw.
- [00060 Supported AI Provider List](00060-Supported-AI-Provider-List.md) — the 12 provider families whose AgentClaws can be paired.
- [00062 Pairing Failure Ladder, PAUSE Mode And EMERGENCY](00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md) — what happens when bonds fail repeatedly.
- [10001 Singular Pairing Principle](https://github.com/bryanunitek/TrueAI/blob/main/docs/10001-Singular-Pairing-Principle.md) — the rule that PairedClaw bonds are singular per workstream.
- [10004 Reversibility](https://github.com/bryanunitek/TrueAI/blob/main/docs/10004-Reversibility-How-TrueAI-Handles-A-False-TRUE.md) — the rule that lets a verified `TRUE` be demoted back to `UNVERIFIED`, applied here to the bond itself.

Revisions to this document are recorded in git history per the [HORIZON.md versioning discipline](../HORIZON.md#versioning-is-not-yet-enabled). The `Version: 1.0` line is a programme-document placeholder. Read changes from the git log.
