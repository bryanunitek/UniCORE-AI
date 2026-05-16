> **Canonical home:** [TrueAI — `docs/10005-Tool-Access-And-Certification-Model.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10005-Tool-Access-And-Certification-Model.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# Tool Access And Certification Model

**Document:** 10005
**Series:** TrueAI Foundation — load-bearing rules
**Status:** v1.0
**Date:** 2026-05-16
**Author:** Bryan Fred
**AI attribution:** drafted in paired session with MyClaw.ai (Claude), reviewed and approved by Bryan Fred.

---

## 1. Purpose

This document defines two structurally distinct gates that govern participation in the production of Foundation-aligned Enterprise Solutions:

1. **The Tool Gate** — who may obtain the singular production tool, and on what basis.
2. **The Certification Gate** — who may earn recognition as a Certified Expert, at what level, and on what basis.

The two gates are separate. They have different entry requirements, different purposes, and different populations. Collapsing them into one gate would either exclude qualified producers from the tool or grant certification without produced work. Neither is acceptable.

This document is the single canonical source of truth for both gates. All other documents that reference tool access or certification levels defer to this one. Where earlier documents describe certification in terms that predate this document (for example, [`00059-Solution-Review.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00059-Solution-Review.md) §7.1), this document governs; the earlier documents remain valid for their own scope but do not override the two-gate model defined here.

---

## 2. The singular tool

There is exactly **one** tool for producing Foundation-aligned Enterprise Solutions. That tool is **UniTEKClaw**.

No second tool may be created for this purpose. The singularity of the tool is a Foundation-level rule, not a commercial decision. The reasons are structural:

1. **Provenance.** Every Foundation-aligned Enterprise Solution produced through UniTEKClaw has a known origin: it was built inside the tool, by a qualified human paired with their AgentClaw, with tool grants declared, granted, and recorded. A second tool would create a second provenance chain with no guarantee of equivalence. One tool means one provenance standard.

2. **Governance surface.** UniTEKClaw implements the PairedClaw Bond File And Session Protocol ([UniVERSE 00061](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md)), the Pairing Failure Ladder ([UniVERSE 00062](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md)), the Nine Invariants ([UniVERSE 00056](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00056-Absolute-Safety-Invariants.md)), and the Reasonable Governance Threshold ([TrueAI 00007](https://github.com/bryanunitek/TrueAI/blob/main/docs/00007-Reasonable-Governance-Threshold-Specification.md)). A second tool would have to re-implement all of these faithfully, and there would be no structural way to verify equivalence. One tool means one governance surface.

3. **Certification anchor.** The Certification Gate (§4) recognises produced work. If multiple tools existed, a certificate would have to specify which tool produced the work and whether that tool's governance was equivalent. One tool means every certificate traces to the same production environment.

UniTEKClaw is distributed **exclusively under End-User Licence Agreement (EUL)**. The EUL is granted **free of charge** — there is no monetary cost. The EUL grants the right to use the tool in binary form. **Source code is not distributed.** The EUL is personal to the recipient and non-transferable.

### 2.1 The badge

**"Powered By UniCORE AI, Built on TrueAI Foundation"** is a certification mark displayed by applications that meet the Foundation standards. The badge is not exclusive to UniTEKClaw — any application that passes the certification standards defined in [`10002-Certification-Before-Layered-Governance.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10002-Certification-Before-Layered-Governance.md) may display it. The badge certifies the **application**, not the tool that produced it and not the human who built it.

UniTEKClaw is the singular tool for **producing** applications that earn the badge. The badge itself is open to all qualifying applications.

---

## 3. The Tool Gate

### 3.1 Who may obtain a UniTEKClaw EUL

A human with **thirty or more years of demonstrated, full-stack, in-vertical professional experience** in a specific sector (Law, Banking, Healthcare, Accountancy, Aerospace, or any other sector in which Enterprise Solutions operate) may request a UniTEKClaw EUL.

The thirty-year threshold is not arbitrary. It represents the minimum career span across which a human has:

- survived multiple technology transitions in their vertical,
- accumulated institutional memory that no document captures,
- built and maintained production systems across at least two major platform generations,
- earned the judgement that comes from decades of consequential decisions under real constraints.

This is the same profile described in [`10003-Generation-IT-Succession.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10003-Generation-IT-Succession.md) §3 as the serving Generation IT producer: the human whose cross-layer mental model, exercised against the Nine Invariants in production, is the unit of transfer to the next generation.

### 3.2 How the request works

1. The requesting human **opens a Discussion** in the [UniVERSE repository](https://github.com/bryanunitek/UniVERSE/discussions) under the appropriate category.

2. The request includes the human's **public professional identity** — LinkedIn profile, professional website, published work, or equivalent publicly verifiable record. The request does not require private documents; the thirty-year threshold is validated against **public sources only** (LinkedIn, Facebook, professional directories, company registrations, published articles, conference appearances, open-source contributions, or any other material the requesting human chooses to cite that is publicly accessible).

3. **Unitek Systems Limited** validates the request. Validation means confirming that the public record demonstrates thirty or more years of professional experience in the claimed vertical. Validation does not assess quality, reputation, or seniority beyond the thirty-year threshold — either the record shows thirty years or it does not.

4. Upon successful validation, the EUL is **issued free of charge** and the recipient receives the UniTEKClaw binary. The EUL is personal, non-transferable, and revocable (see §3.4).

5. The issuance is **recorded in the Discussion thread** so the community can see who holds EULs and when they were granted. This is the transparency mechanism: every EUL grant is public, named, and dated.

### 3.3 What the thirty-year threshold is not

- **Not an age requirement.** A human who began professional work at 16 and is now 46 meets the threshold. A human who began at 30 and is now 55 does not (25 years). The measure is career span in the vertical, not biological age.

- **Not a seniority title.** The requesting human does not need to hold a specific job title (CTO, Senior Architect, Partner, etc.). The measure is demonstrated career span, not organisational rank.

- **Not a certification.** The EUL grant is not a UniCORE Expert Certification (§4). It is access to the tool. Certification is earned separately, by produced work.

- **Not a guarantee of competence.** The thirty-year threshold filters for career survival, which is a necessary but not sufficient condition for the kind of work the Foundation expects. The Certification Gate (§4) measures competence through produced output.

### 3.4 Revocation and runtime enforcement

A UniTEKClaw EUL may be revoked, or a UniCORE Expert Certification may expire or be withdrawn, by Unitek Systems Limited for:

- **Misrepresentation** — the public professional record used to validate the request was materially false.
- **Licence violation** — the recipient violated the EUL terms (redistribution of the binary, reverse engineering, sub-licensing, etc.).
- **Foundation violation** — the recipient used UniTEKClaw to produce work that materially violates the Nine Invariants, and the violation was deliberate rather than a good-faith error correctable through the Pairing Failure Ladder ([UniVERSE 00062](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md)).
- **Certification lapse** — the holder's UniCORE Expert Certification expired without renewal.

Revocation is recorded publicly in the same Discussion thread as the original grant, with the reason stated, and reflected in the public Certificate Holders register.

**Revocation is enforced structurally at runtime.** UniTEKClaw checks the public Certificate Holders register at every login. A holder whose certification is no longer current cannot authenticate into UniTEKClaw. UniTEKClaw also enforces auto-logout after a period of idle, the duration of which is set by Unitek Systems Limited and is not user-configurable. Together these mean revocation propagates to every installation the holder operates within one idle cycle, without requiring any per-installation action.

If the Certificate Holders register cannot be reached when login is attempted, login fails. There is no offline bypass. A Certified Expert who needs to operate UniTEKClaw must be able to reach the register at the point of login.

### 3.5 Multi-machine use

The UniTEKClaw EUL is valid on multiple machines belonging to the EUL holder, within reason for personal professional use. Additional work-related machines dedicated to the EUL holder only also count. Distribution to other persons, use beyond the holder's own work, or installation on machines shared with or used by other persons is a licence violation.

Visual Studio and DevExpress licences held by the same EUL holder operate on the same multi-machine basis under their own licence terms.

The runtime enforcement mechanism described in §3.4 applies to every installation simultaneously. A revoked Expert cannot evade revocation by switching to a different installation, by working offline, or by reinstalling on a fresh machine.

### 3.6 Scope of work an EUL holder may produce

A UniTEKClaw EUL holder may use UniTEKClaw to produce three categories of work:

1. **Foundation-aligned applications.** Applications in the critical-decision path that require TrueAI Foundation governance — Banking, Healthcare, Government, Military, Aerospace, and any other vertical where AI operates in the path of consequential decisions. These applications may earn the "Powered By UniCORE AI, Built on TrueAI Foundation" badge upon passing certification per [`10002`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10002-Certification-Before-Layered-Governance.md).

2. **Non-Foundation AI applications.** Human-oriented AI applications outside the critical-decision path — personal AI assistants, creative tools, entertainment, social applications, day-to-day utilities. These do not require Foundation governance and do not earn the badge. They are produced on a separate machine (see below).

3. **Non-AI applications that use AI and the Claws within UniTEKClaw.** Applications whose primary purpose is not AI, but which use AI and the Claws as part of the production process. The Expert may pair with their AgentClaw to design, build, and refine the application; the application itself need not embed AI. These do not earn the Foundation badge and are produced on a separate machine.

**The judgement of which category a given application belongs to is the Certified Expert's competence.** That judgement — knowing when a vertical needs Foundation governance and when it does not — is part of what the certification recognises. The Foundation does not enumerate every possible application; it defines the principles, and trusts the certified human to apply them.

**Categories 2 and 3 are produced on a separate machine from the Foundation work.** The reason is non-public-repository isolation. The EUL holder's primary Foundation machine carries non-public material in its repository folders — UniTEKClaw source-repo-roots that contain Foundation-licensed work and private material. None of that may be visible to non-Foundation work. The cleanest and most defensible boundary is a different physical machine with its own repository folders. The non-Foundation machine may use any public Foundation material; it may not include, clone, copy, or otherwise transfer any non-public Foundation material.

The same EUL covers both machines under the multi-machine provision in §3.5. The same EUL holder operates both. The two machines are physically separate to make the public/private boundary structural rather than policy-based.

---

## 4. The Certification Gate

### 4.1 Who may earn a UniCORE Expert Certification

**Any human, at any career stage.** There is no minimum age, no minimum years of experience, and no prerequisite credential.

- A university student may earn a certification.
- A junior consultant may earn a certification.
- An apprentice may earn a certification.
- An entry-level practitioner may earn a certification.
- A mid-career professional may earn a certification.
- A thirty-year veteran may earn a certification.

The certification is **earned by produced work**, not by background, CV, or years of experience. The level of the certification is set by the quality and scope of the produced work, not by the producer's seniority.

### 4.2 How certification works

1. The practitioner **participates in the Foundation through [Discussions](https://github.com/bryanunitek/UniVERSE/discussions)** — contributing ideas, reviewing published specifications, proposing improvements, asking questions, collaborating with other participants.

2. The practitioner **produces original work** that demonstrates Foundation fluency. "Original work" means the practitioner's own ideas, reasoning, and contributions — not copying, summarising, or restating existing material. The work must be visible in the public Discussion record.

3. The certifying body (Unitek Systems Limited, or the certifying authority designated by Unitek Systems Limited) **evaluates the produced work** against the certification-level criteria (§4.3) and issues a certification at the level the work qualifies for.

4. The certification is **public, named, dated, and recorded** in the [`CERTIFIED-EXPERTS.md`](https://github.com/bryanunitek/UniVERSE/blob/main/CERTIFIED-EXPERTS.md) register at the root of the UniVERSE repository. The register is the canonical source of truth for who holds which certification at which level. The runtime enforcement described in §3.4 checks this register.

### 4.3 Certification levels

The certification levels correspond to the scope and depth of produced work. The exact criteria for each level will be published as a companion document to this one (extending the framework in [`00023-Training-Certification-Framework.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00023-Training-Certification-Framework.md)). The levels are:

| Level | Name | Basis |
|---|---|---|
| 1 | Apprentice | First substantive contribution through Discussions; demonstrates basic Foundation fluency |
| 2 | Entry-level | Sustained contributions; demonstrates working understanding of the Nine Invariants and the Layered CORE Model |
| 3 | Junior | Original produced work that applies Foundation principles to a concrete problem or vertical |
| 4 | Mid-level | Produced work across multiple Foundation concerns; demonstrated ability to operate a PairedClaw session under supervision |
| 5 | Senior | Substantial body of produced work; demonstrated ability to operate independently; eligible for named attestation under [`10003`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10003-Generation-IT-Succession.md) |

These levels are **not the same** as the five operational tiers in [`00023-Training-Certification-Framework.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00023-Training-Certification-Framework.md) (User, Operator, Governance Officer, Compliance Officer, Mission Commander). The `00023` tiers govern **operating** a deployed Solution. The levels in this document govern **producing** Foundation-aligned work. A human may hold certifications in both schemes independently.

### 4.4 Progression

Certification levels are not permanent. A practitioner who continues to produce work at higher scope and depth may be re-evaluated and certified at a higher level. Progression is always based on **new produced work** — a practitioner cannot re-submit the same work for a higher level.

Certification is also not perpetual. The certifying body may define renewal requirements in the companion criteria document. Until that document is published, certifications remain valid unless explicitly revoked, with the runtime enforcement in §3.4 acting as the structural cut-off.

### 4.5 Relationship between the two gates

The Tool Gate (§3) and the Certification Gate (§4) are independent but complementary:

| | Tool Gate (EUL) | Certification Gate |
|---|---|---|
| **What it grants** | Access to UniTEKClaw | Recognition as Certified Expert at a named level |
| **Entry requirement** | 30+ years validated career | Any age, any stage |
| **Basis** | Public professional record | Produced original work |
| **Population** | Small (constrained by career span) | Open (anyone who participates) |
| **Interaction** | EUL holder uses UniTEKClaw to produce Solutions | Certified Expert may or may not hold an EUL |

A human may hold:

- **An EUL without any certification** — a thirty-year veteran who has received the tool but has not yet produced certified work.
- **Certifications without an EUL** — a junior practitioner who has earned certification through Discussions and collaboration but does not yet meet the thirty-year threshold for the tool.
- **Both** — the mature state: a thirty-year veteran who has both the tool and a body of certified produced work.

### 4.6 How younger practitioners produce work without the tool

Practitioners who do not hold a UniTEKClaw EUL produce Foundation-aligned work through two paths:

1. **Discussions.** The public Discussion forums on UniVERSE, TrueAI, and UniCORE-AI are open to all. Contributions through Discussions — ideas, reviews, proposals, questions, analysis — count as produced work for certification purposes. No tool is required.

2. **Paired work under a senior.** A junior practitioner may work alongside an EUL-holding senior, contributing to the work produced on the senior's UniTEKClaw installation under the [Generation IT Succession](https://github.com/bryanunitek/TrueAI/blob/main/docs/10003-Generation-IT-Succession.md) model. The junior's contributions are recorded and attested by the senior. The produced work counts toward the junior's certification at the appropriate level.

Neither path requires the junior to hold their own UniTEKClaw EUL. Both paths produce real, attested, certifiable work.

---

## 5. Default-held certification and EUL

**Bryan Fred, as Author and Creator of UniVERSE, TrueAI, and UniCORE-AI, holds certification at the highest level by default, and holds a UniTEKClaw EUL by default.**

The default-held certification and EUL are structural properties of the Author/Creator role, not issuances. They do not require nomination, application, examination, or external authorisation, because the certifying authority and the certificate-holder are, in this case, the same originating identity. The default-held certification and EUL cannot be revoked: revocation requires an authority external to the holder, and no such authority exists for the originating identity.

The default-held certification and EUL pass to any successor named under the [TrueAI whitepaper succession statement](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md#8-succession-and-stewardship), on the same default-held basis, for as long as the succession process remains active. Successors do not need to be re-certified; they inherit the certification and EUL as part of inheriting the role.

### 5.1 Private EUL grants for potential successors

Bryan Fred and the named successor may **privately grant UniTEKClaw EULs to potential successors** — humans they are considering for the succession role under the WHITEPAPER §8 statement. These private grants are outside the public 30+ year request process described in §3.2.

The purpose of the private grant is to let a candidate **find their path**: actually use UniTEKClaw, produce work alongside the originator or named successor, and develop the cross-layer judgement that the succession demands. A candidate cannot be evaluated for the succession role through a public request form; the role requires sustained working pairing over time. The private EUL grant makes that pairing possible.

Private successor-candidate EUL grants:

- are issued by Bryan Fred personally, or by the named successor during their stewardship;
- are not subject to the public Discussion request process (§3.2);
- are recorded internally by Unitek Systems Limited but need not be publicly disclosed during the candidacy period;
- are subject to the same revocation and runtime enforcement as any other EUL (§3.4);
- carry the same multi-machine and scope-of-work rules as any other EUL (§3.5, §3.6);
- do not confer certification by themselves — the candidate still earns certification through produced work like any other practitioner (§4).

The private grant ends in one of three ways: the candidate is formally named as successor (the private EUL becomes a default-held EUL); the candidate withdraws or the originator/successor decides against the candidacy (the private EUL is revoked); or the candidate becomes eligible for a public EUL on their own merit (the private grant transitions to a public grant).

---

## 6. Software prerequisites for UniTEKClaw

UniTEKClaw runs on Windows and depends on supporting software. The prerequisites are listed in three tiers as guidelines, not absolutes. The right combination may vary based on the kind of work being produced. Where a Certified Expert has questions or wants to argue for a non-listed combination, the public Discussion forums on the Foundation repositories are where that conversation happens.

### 6.1 Required

These components must be present for UniTEKClaw to function at all:

- A supported version of **Microsoft Windows** (specific versions defined by the UniTEKClaw release notes).
- **SQL Server Express** (at minimum). UniTEKClaw stores its data in SQL Server; Express is the minimum acceptable edition. Higher editions (Standard, Enterprise) are also acceptable.
- The **.NET runtime** required by the UniTEKClaw release (specific version defined by the release notes).
- **Internet connectivity** sufficient to reach the public Certificate Holders register at login (per §3.4).

### 6.2 Recommended

These components produce the best supported development experience and the deepest integration with UniTEKClaw's Claws:

- **Visual Studio Professional Subscription** (or higher edition). UniTEKClaw is built on the same Visual Studio + .NET tooling that the Foundation repositories use, and the Claws have the deepest integration with Visual Studio.
- **DevExpress Ultimate Subscription**. UniTEKClaw is built on DevExpress XAF (eXpressApp Framework) for its XAF-based applications, and the Ultimate Subscription provides the full XAF and XPO stack.

### 6.3 Alternative

UniTEKClaw is not constrained to Visual Studio and DevExpress. Where a Certified Expert has alternative Windows-compatible compilers and IDEs installed, UniTEKClaw's Claws operate with those alternatives.

The compatible-tooling list is maintained as a separate companion document: [`90001-UniTEKClaw-Compatible-Windows-Tooling.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/90001-UniTEKClaw-Compatible-Windows-Tooling.md). The list covers compilers and IDEs for the language and platform areas in which UniTEKClaw operates, including non-.NET areas such as machine-level programming (per [`00029-Machine-Level-Integration.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00029-Machine-Level-Integration.md) §3), where Visual Studio and DevExpress are neither the natural nor the only choice.

---

## 7. Costs and Unitek Systems Limited contribution

Operating UniTEKClaw incurs real costs:

- AI provider API costs for the three agents involved in a typical UniTEKClaw installation (the application-tier AgentClaw, the user-tier AgentClaw, and the Foundation-drift-detector AgentClaw or equivalent), recurring monthly.
- Software subscriptions (Visual Studio Professional Subscription, DevExpress Ultimate Subscription, and other tools necessary to produce serious work), recurring annually.
- Hardware costs for the separate machine required for non-Foundation work (§3.6).

**Unitek Systems Limited may bear these costs**, in whole or in part, as a **cost of succession** rather than as salary or employment compensation. The Foundation is gift (per the [TrueAI Gift Principle](https://github.com/bryanunitek/TrueAI/blob/main/docs/00028-TrueAI-Foundation-Gift-Principle.md)); funding the producers of the Foundation is consistent with the same gift logic, when Unitek Systems Limited chooses to do so.

The specific arrangement — which costs Unitek bears, for which Experts, on what schedule — is operational discretion of Unitek Systems Limited and its accounting treatment. The principle this document records is that such arrangements **may** exist and are coherent with the Foundation; the operational detail belongs in Unitek's accounting and the individual arrangements with Experts and potential successors.

This provision applies particularly to **potential successors** under §5.1. Bringing a candidate to successor level may require sustained access to expensive tooling over years; Unitek Systems Limited may fund that access as part of the succession investment.

---

## 8. What this document does not cover

- **The detailed certification-level criteria.** The exact requirements for each level (§4.3) will be published as a companion document, extending [`00023-Training-Certification-Framework.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00023-Training-Certification-Framework.md). This document defines the levels; the companion defines the criteria.

- **The EUL text itself.** The legal terms of the UniTEKClaw End-User Licence Agreement are a separate legal document authored by Unitek Systems Limited. This document defines who is eligible for the EUL and how eligibility is validated; the EUL document defines the licence terms.

- **The compatible-tooling list.** §6.3 references a companion document listing the compilers and IDEs UniTEKClaw's Claws support beyond Visual Studio and DevExpress. That list is maintained as a separate document.

- **UniTEKClaw's internal architecture.** The tool's architecture, Business Object model, deployment topology, and technical implementation are documented in UniTEKClaw's own repository. This document defines the access model for the tool, not the tool itself.

- **The operational certification scheme** (examination procedures, licence-violation revocation, relationship between certifying body and L3 CORE governance layer). These will be published as separate programme documents when the scheme transitions from nomination-based to public-process-based.

- **Auto-logout idle duration.** §3.4 references an auto-logout mechanism; the specific idle duration is operational discretion of Unitek Systems Limited and is set in UniTEKClaw configuration rather than in Foundation policy.

---

## 9. Cross-references

| Document | Relationship |
|---|---|
| [`10001-Singular-Pairing-Principle.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10001-Singular-Pairing-Principle.md) | UniTEKClaw enforces Singular Pairing; the EUL grants access to the tool that does so |
| [`10002-Certification-Before-Layered-Governance.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10002-Certification-Before-Layered-Governance.md) | The badge "Powered By UniCORE AI, Built on TrueAI Foundation" is the certification mark defined here; `10002` governs the certification of the Solution artefact |
| [`10003-Generation-IT-Succession.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10003-Generation-IT-Succession.md) | The Tool Gate's thirty-year threshold aligns with the serving Generation IT producer profile; §4.6 (paired work under a senior) is the succession mechanism in practice; §5.1 (private EUL grants for potential successors) implements the highest-level succession path |
| [`10004-Reversibility-How-TrueAI-Handles-A-False-TRUE.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10004-Reversibility-How-TrueAI-Handles-A-False-TRUE.md) | Revocation and runtime enforcement (§3.4) are the Tool Gate's analogue of reversibility |
| [`00023-Training-Certification-Framework.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00023-Training-Certification-Framework.md) | The five operational tiers (User through Mission Commander) are distinct from but complementary to the five certification levels defined here |
| [`00056-Absolute-Safety-Invariants.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00056-Absolute-Safety-Invariants.md) | Foundation violation (§3.4) means deliberate violation of the Nine Invariants |
| [`00059-Solution-Review.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00059-Solution-Review.md) | §5 of this document generalises the default-held certificate provision of `00059` §7.1 to both gates and to the EUL |
| [`00061-PairedClaw-Bond-File-And-Session-Protocol.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md) | UniTEKClaw implements the PairedClaw bond; the EUL grants access to that implementation |
| [`00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md) | UniTEKClaw implements the failure ladder; Foundation violation for revocation (§3.4) is distinguished from good-faith errors handled by the ladder |
| [TrueAI WHITEPAPER §8](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md#8-succession-and-stewardship) | The succession statement that governs transfer of the default-held certification and EUL; §5.1 (private successor-candidate EULs) is the operational path leading into the succession statement |

---

## 10. Document history

| Version | Date | Author | Change |
|---|---|---|---|
| 1.0 | 2026-05-16 | Bryan Fred | Initial two-gate model: Tool Gate (30+ years, EUL, singular tool, multi-machine within reason, separate machine for non-Foundation work, runtime kill-switch via login check + auto-logout) and Certification Gate (any age, produced work, five levels). Default-held certification and EUL for Author/Creator and successors. Private successor-candidate EUL grants. Three-tier software prerequisites as guidelines. Unitek Systems Limited may bear costs as cost of succession. |
