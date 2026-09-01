> **Canonical home:** [UniVERSE — `docs/00063-Law-Firm-Deployment-Guide.md`](https://git.unitek-systems.com/UniCORE/UniVERSE/src/branch/main/docs/00063-Law-Firm-Deployment-Guide.md) (mirror: [GitHub](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00063-Law-Firm-Deployment-Guide.md))
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# UniCORE AI — Law Firm Deployment Guide

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: September 2026
Status: Public. Given, not sold. Irrevocable.

> **Companion to** [`00019-Enterprise-Deployment-Guide.md`](./00019-Enterprise-Deployment-Guide.md). That guide defines the general enterprise deployment of UniCORE AI. **This guide specialises it for a professional-services firm** — a law firm as the worked example — showing how UniCORE AI (governance), UniCORE.Law (the legal vertical), and UniCORE.GVB (the substrate) deploy together, and how the same pattern generalises to any vertical (accountancy, a business, a school, a university).
>
> This is a **public, pattern-level** guide (CC BY 4.0). It describes *how the pattern works and how to stand it up*. It is deliberately model-agnostic and vendor-neutral: a firm can deploy it using UniCORE, **or build their own** compliant substrate from the same pattern. Both are intended.

---

## 1. Purpose

This guide defines how a **law firm** (or any professional-services organisation) deploys UniCORE AI so that:

- the firm's people are each **AI-augmented for both deciding and thinking**, human-sovereign throughout;
- the firm's **data stays the firm's data** — held locally, never surrendered to an AI company;
- every AI-assisted action is **governed, truth-anchored, and auditable** under the firm's own governance;
- the firm can use public AI models, **or build its own**, without changing the core.

It ensures the deployment remains deterministic, governed, truth-anchored, non-self-modifying, and compliant with the TrueAI Constitution — exactly as `00019` requires — while adding the roles a firm needs: **per-person pairings, a Librarian over one local firm data library, and a firm-defined governance ladder.**

## 2. Why a firm needs its own guide

An enterprise deployment (`00019`) governs *a system*. A firm deployment governs *people doing accountable professional work* — lawyers advising clients, bound by privilege, confidentiality, and matter-walls. Three firm-specific realities drive this guide:

- **The data is the asset and the liability.** A law firm holds enormous confidential client data. That data belongs to the firm and its clients. It must be usable by AI **without leaving the firm** or being collated by an AI company.
- **The work is both decisions and exploration.** Lawyers *decide* (consequential, accountable) and *think* (research, hypothesise, draft). These are different modes and need different AI support.
- **Confidentiality is structural, not optional.** Person A must not see Person B's client matters. This must be enforced by design, not policy alone.

## 3. The firm topology

UniCORE AI deploys into a firm as five layers, all on the firm's internal network, everything local:

```
   FIRM GOVERNANCE  (UniCORE-AI 12-Level model; N levels, firm-defined × firm-sized, N ≤ 12)
        │   governs everything below; the firm's accountable human is bound at the top level
   PEOPLE           each person has BOTH pairings:
        │             • 1H1C  → DECIDING  (accountable, consequential)
        │             • 1H2C  → THINKING  (exploratory; thinks, never decides)
        │           the 1H1C routes: it determines when the human needs the 1H2C, and
        │           when a thinking result returns for a decision. Thinking never
        │           self-escalates into a decision.
   LIBRARIAN        oversees the ONE firm data library (operates at top-level authority)
        │             • keeps everything IN the firm (containment / anti-exfiltration)
        │             • serves the library OPEN to each person, by their access
        │             • routine access flows automatically; only genuine ISSUES escalate,
        │               and the escalation target is itself a 1H1C (a human + Claw) who decides
   FIRM DATA LIBRARY   one governed local library of the firm's matters, precedents,
        │               documents and records — held locally, never sent to an AI company
   ────────────────────────────────────────────────────────────────────────────────────
   UniCORE runs it. AI Models (public or the firm's own) are consulted THROUGH the pairings
   as interchangeable reasoning suppliers. They never own or hold the firm's core.
```

### 3.1 Firm Governance (the ladder)

Firm Governance is a deployment of the **UniCORE-AI 12-Level Governance model** (see `levels/` and `00019` §5.1). The number of levels a firm stands up is **not fixed at 12**: it is set by **the size of the firm × what the firm defines as its governance**. A sole practitioner needs few levels; a large firm with partnership, risk, compliance and information-governance functions needs more, up to the full twelve. The accountable human is always bound at the top level in force: *no code, no AI, overrules the top level.*

Governance operates as the **12-Level walk** (`00019` §5.1; AI-Maturity-Levels): a background, asynchronous cross-check that certifies each action against the firm's grounded record. Actions **soft-post** immediately; the certifier reconciles behind them; a human authorises the **hard post**. On any inconsistency — from the AI side *or* the human side — the transaction is reprocessed from the start against the current record. The system getting better at *finding* inconsistency never migrates the authority to *resolve* it away from the human.

### 3.2 People — two pairings each

Every person in the firm operates with two pairings (see `thinking-ai-doctrine/v1`):

- **1H1C — the deciding pairing.** One human, one Claw. Accountable, consequential, certified. This is where advice is committed, matters progressed, decisions made. The 1H1C also **routes**: it recognises when a question needs exploration and hands it to the 1H2C, and when a thinking result is ready to come back for a decision.
- **1H2C — the thinking pairing.** One human, two equal Claws that reason against each other on TrueAI — one proposes, one challenges, the human advances every round and owns every conclusion. It **thinks; it never decides.** The moment a consequence attaches, the work returns to the 1H1C.

> The pairings are **not** sub-agents and **not** additional agents of a single Claw. They are the firm's people, each in a human-sovereign pairing. The distinction matters: adding autonomous agents is exactly what this architecture refuses.

### 3.3 The Librarian and the one firm data library

The firm holds **one** governed local data library — not a flat shared pool, not per-person copies. A **Librarian** oversees it, with two jobs:

1. **Nothing leaves the firm.** The Librarian is the containment boundary. Books and data do not walk out — not to another firm, not off the firm network, and not to an AI company. This is what lets a pairing *use* an external AI model without *feeding it* the library: the query may go out; the firm's data does not.
2. **The library is open to the firm, by access.** Internally the library is **open**, not ask-permission-each-time. A person freely uses everything their access covers. **Access is a property of the person** — their entitlement, matter-walls, need-to-know — not a per-request approval.

Routine access flows automatically; the confidentiality rules run themselves. **Only on a genuine issue** — an ambiguous request, a matter-wall question, an exception — is it raised to the Librarian and its team, **which is itself a 1H1C** (a human plus their Claw). The human decides. So confidentiality's hard cases are always decided by an accountable human, never by an autonomous AI. This mirrors the soft-post / hard-post mechanism: automatic by default, escalate-to-human on issue.

## 4. The decision every firm makes — public models or its own

A firm's confidential data is protected from AI-company **collation** to exactly the degree that its data never reaches an AI company. Keeping the *library* local (§3.3) is necessary but not sufficient: if a pairing sends confidential content *into an external model's prompt*, that content has left the firm. This is the fork every firm must decide:

**Branch A — Use public AI models** (OpenAI, Anthropic, Google, others)
- Best-in-class reasoning, no model infrastructure, fastest to start.
- Collation risk is real at the query boundary and rests on the provider's no-train / zero-retention **promise** — trust, not sovereignty.
- **Requires an egress-minimisation layer**: only de-identified or abstracted queries cross the boundary; raw confidential matter never does. Mitigates, does not eliminate.
- Protects the firm's data **partially**.

**Branch B — Build the firm's own model** (local / self-hosted)
- The data never leaves; no AI company is consulted, so collation is **structurally impossible**.
- Costs hardware and operation; a smaller model trained on the firm's own domain can nonetheless be excellent for that domain.
- The only branch that **fully** delivers "everything local, protected from collation."

**Hybrid** — route confidential matters to the firm's own model (B) and general research to public models (A); the Librarian enforces which is which.

> **This choice does not change the firm's core.** The Firm Governance, the pairings, the Librarian and the local library are identical either way. The only thing the fork changes is **where the reasoning comes from.** UniCORE AI is model-agnostic by design; the firm chooses its reasoning supplier by how much sovereignty its data demands. This is the deliberate meaning of *"use UniCORE, or build your own."*

## 5. Component stack

A firm deployment composes three layers, each with a public canonical home:

- **UniCORE AI** — the governance layer: the 12-Level model, TrueAI truth contract, the Inter-Level Messaging Protocol (`00017-ILMP`), the audit and override engines (`00019` §5). This is what makes the deployment *governed*.
- **UniCORE.Law** — the legal vertical: the firm-domain business objects and workflows (matters, engagements, conflicts, legal-identifier and jurisdiction handling, e-invoicing and posting where applicable). This is what makes the deployment *a law firm's*, not a generic system. *(The vertical's commercial packaging and Business Objects sit at the commercial layer; this guide covers the deployment pattern, not that packaging.)*
- **UniCORE.GVB** — the substrate: the governed infrastructure the whole thing runs on (nodes, per-node data stores, mail security, the firm's forge/version store). This is what keeps it *local and sovereign*.

For any other vertical, **swap the vertical layer** (accountancy objects, school/university objects, a business's own objects) and keep UniCORE AI + the substrate unchanged. The pattern is vertical-agnostic; only the middle layer changes.

## 6. Deployment models (firm sizing)

Building on `00019` §4, a firm chooses a footprint by size and sensitivity:

- **On-premise / firm-hosted (recommended for confidential legal work).** Full data sovereignty, no external dependency, highest confidentiality. Natural home for Branch B (own model). See `00019` §4.1 / §4.4.
- **Hybrid.** Governance layer and firm data library on-premise; application and presentation layers may sit in a private cloud. Compatible with Branch A **only** with the egress-minimisation layer in place. See `00019` §4.2.
- **Sole practitioner / small firm.** A single node running the full stack with a reduced governance ladder (few levels) and one person's two pairings. Everything local; simplest footprint.

Network segmentation follows `00019` §6.4: Governance Layer isolated; Firm Data Library on a private subnet; presentation internal or DMZ. **The firm's internal network is the boundary the Librarian enforces.**

## 7. Deployment steps

The general steps of `00019` §7 apply. The firm-specific additions are:

**Step 1 — Provision the substrate (UniCORE.GVB).** Stand up the firm's node(s), per-node data store, and version/forge store. Everything local; the firm owns the hardware or a sovereign-hosted equivalent.

**Step 2 — Install UniCORE AI (governance).** Deploy the governance engine, the Inter-Level Messaging bus (`00017-ILMP`), the append-only audit engine, and the human override engine (`00019` §5). Governance MD files load read-only.

**Step 3 — Define Firm Governance.** Choose the governance ladder (how many levels) from firm size × the firm's own governance definition (§3.1). Author the firm's governance MD files (confidentiality, matter-walls, conflicts, retention, jurisdiction) — human-authored, signed, versioned. Bind the firm's accountable human at the top level.

**Step 4 — Install the vertical (UniCORE.Law).** Deploy the legal business objects and workflows. Load the firm's matter/engagement/conflict model.

**Step 5 — Stand up the Firm Data Library and Librarian.** Ingest the firm's data into the one local library. Define each person's **access** (entitlement, matter-walls, need-to-know). Configure the Librarian: containment (nothing leaves), open-by-access internally, automatic routine flow, and issue-escalation to a human 1H1C.

**Step 6 — Provision people's pairings.** For each person, provision a 1H1C (deciding) and a 1H2C (thinking) on the firm's internal network. Verify the 1H1C routing (decide ↔ think) and that both pairings reach the Librarian, never the library directly.

**Step 7 — Choose the reasoning supplier (the §4 fork).** Configure Branch A (public models + egress-minimisation), Branch B (firm's own model), or the hybrid. Confirm no confidential content can reach an external model except through the minimisation layer.

**Step 8 — Validate and begin operation.** Run schema, governance, messaging and drift-baseline validation (`00019` §7 Step 6). Confirm: the 12-Level walk certifies actions; hard posts require a human; the audit log is append-only; nothing exfiltrates. The firm enters deterministic, governed, audited operation.

## 8. Confidentiality, privilege, and audit

- **Matter-walls** are enforced by the Librarian's per-person access, backed by Firm Governance. A pairing can only reach what its person is entitled to.
- **Privilege** is preserved because confidential content is either never sent to an external model (Branch B) or is minimised before egress (Branch A).
- **Every AI-assisted action is auditable**: logged, timestamped, immutable, exportable (`00019` §5.3). The firm can demonstrate, for any advice or document, what was grounded, what was human-decided, and that no data left improperly.
- **Human override is immediate and unchallenged** (`00019` §5.4): a person can always stop, correct, or overrule the AI. No AI holds a role; AI cannot access secrets autonomously (`00019` §6).

## 9. Generalising to other verticals

The same guide deploys any professional-services organisation by swapping the vertical layer:

- **Accountancy firm** — accountancy business objects; same governance, Librarian, pairings, local ledgers/working-papers library.
- **A business** — the business's own objects; the library holds its commercial and operational data.
- **A school or university** — education objects; the library holds student, research and administrative records, with the same confidentiality discipline (data-protection duties map cleanly onto matter-walls).

In every case: UniCORE AI (governance) and the substrate are unchanged; only the vertical and the firm's governance definition change. And in every case, the §4 fork stands: **use public models, or build your own** — the core is identical either way.

## 10. Why this guide matters

A profession's confidential data is its clients' trust made tangible. The prevailing offer — send it to an AI company's cloud and trust their promises — asks a firm to surrender that trust to a third party it cannot audit. This guide describes the alternative: **AI that keeps the firm's data in the firm, the human sovereign at every level, and every action governed and provable** — using UniCORE, **or a firm's own build of the same pattern.** The point is not that a firm must buy anything. The point is that AI-compliant, sovereign, truth-anchored operation is achievable and here documented, so the whole profession can reach it.

---

*Given, not sold. Irrevocable. CC BY 4.0 — Bryan Fred, Unitek Systems Limited.*
