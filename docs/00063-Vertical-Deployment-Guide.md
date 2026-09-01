> **Canonical home:** [UniVERSE — `docs/00063-Vertical-Deployment-Guide.md`](https://git.unitek-systems.com/UniCORE/UniVERSE/src/branch/main/docs/00063-Vertical-Deployment-Guide.md) (mirror: [GitHub](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00063-Vertical-Deployment-Guide.md))
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# UniCORE AI — Vertical Deployment Guide (Generic)

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: September 2026
Status: Public. Given, not sold. Irrevocable.

> **The generic parent of the vertical deployment guides.** [`00019-Enterprise-Deployment-Guide.md`](./00019-Enterprise-Deployment-Guide.md) defines the general *system* deployment of UniCORE AI. **This guide defines the vertical-agnostic *organisation* pattern** — how any professional-services organisation, business, or institution deploys UniCORE AI (governance) + a vertical layer + UniCORE.GVB (substrate), with its people, its data, and its governance.
>
> Each specific vertical is a **worked instance** of this pattern, and — per the [`developer-doctrine` VERTICAL-ENTRY](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/VERTICAL-ENTRY.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/VERTICAL-ENTRY.md)) process — lives in that vertical's own gift-layer repo family (`UniCORE.<Vertical>` / `UniSaaS.UniCORE.<Vertical>`), not in the foundation. The first vertical is **Law** (`UniCORE.Law` / `UniSaaS.UniCORE.Law`). Future instances (accountancy, a business, a school, a university, a government body) follow the same structure and change only the vertical layer.
>
> This is a **public, pattern-level** guide (CC BY 4.0). It is deliberately model-agnostic, device-agnostic, and vendor-neutral: an organisation can deploy it using UniCORE, **or build its own** compliant substrate from the same pattern. Both are intended.

---

## 1. Purpose

This guide defines how **any organisation** — a professional-services firm, a business, a school, a university, a public body — deploys UniCORE AI so that:

- the organisation's people are each **AI-augmented for both deciding and thinking**, human-sovereign throughout;
- the organisation's **data stays the organisation's data** — held locally, never surrendered to an AI company;
- every AI-assisted action is **governed, truth-anchored, and auditable** under the organisation's own governance;
- the organisation can use public AI models, **or build its own**, without changing the core.

It is the reusable pattern. A vertical guide (such as the Law guide in `UniCORE.Law`) specialises it with a sector's data, workflows, and governance particulars.

## 2. The pattern, in one picture

UniCORE AI deploys into any organisation as the same five layers, all on the organisation's internal network, everything local:

```
   ORGANISATION GOVERNANCE  (UniCORE-AI 12-Level model; N levels, org-defined × org-sized, N ≤ 12)
        │   governs everything below; the org's accountable human is bound at the top level
   PEOPLE           each person has BOTH pairings:
        │             • 1H1C  → DECIDING  (accountable, consequential)
        │             • 1H2C  → THINKING  (exploratory; thinks, never decides)
        │           the 1H1C routes: it determines when the human needs the 1H2C, and
        │           when a thinking result returns for a decision. Thinking never
        │           self-escalates into a decision.
   LIBRARIAN        oversees the ONE organisation data library (operates at top-level authority)
        │             • keeps everything IN the organisation (containment / anti-exfiltration)
        │             • serves the library OPEN to each person, by their access
        │             • routine access flows automatically; only genuine ISSUES escalate,
        │               and the escalation target is itself a 1H1C (a human + Claw) who decides
   ORGANISATION DATA LIBRARY   one governed local library of the org's records, work product,
        │                      and domain data — held locally, never sent to an AI company
   ────────────────────────────────────────────────────────────────────────────────────
   UniCORE runs it. AI Models (public or the org's own) are consulted THROUGH the pairings
   as interchangeable reasoning suppliers. They never own or hold the org's core.
```

The five layers are invariant across verticals. Only the **vertical layer** (§5) changes.

## 3. The invariants (what never changes across verticals)

### 3.1 Organisation Governance (the ladder)

A deployment of the **UniCORE-AI 12-Level Governance model** (see `levels/` and `00019` §5.1). The number of levels an organisation stands up is **not fixed at 12**: it is set by **the size of the organisation × what the organisation defines as its governance**. A sole operator needs few levels; a large institution with formal risk, compliance and information-governance functions needs more, up to twelve. The accountable human is always bound at the top level in force: *no code, no AI, overrules the top level.*

Governance operates as the **12-Level walk** (`00019` §5.1): actions soft-post immediately; the certifier reconciles behind them against the grounded record; a human authorises the hard post; on any inconsistency — AI-side or human-side — the transaction reprocesses from the start. Growing detection never migrates the authority to resolve away from the human.

### 3.2 People — two pairings each

Every person operates with two pairings (see `thinking-ai-doctrine/v1`):

- **1H1C — the deciding pairing.** Accountable, consequential, certified. Where work is committed and decisions made. Also **routes** between deciding and thinking.
- **1H2C — the thinking pairing.** Two equal Claws reason against each other on TrueAI — one proposes, one challenges, the human advances every round and owns every conclusion. It **thinks; it never decides.** When a consequence attaches, work returns to the 1H1C.

These are the organisation's people in human-sovereign pairings — **not** sub-agents and **not** additional autonomous agents.

### 3.3 The Librarian and the one data library

One governed local library — not a flat shared pool, not per-person copies. A **Librarian** oversees it with two jobs:

1. **Nothing leaves the organisation** — the containment / anti-exfiltration boundary. This is what lets a pairing *use* an external AI model without *feeding it* the library.
2. **The library is open, by access** — internally open, not ask-each-time; each person freely uses everything their access covers. **Access is a property of the person** (entitlement / need-to-know), not a per-request approval.

Routine access flows automatically; only genuine issues escalate — and the escalation target is itself a **1H1C (human + Claw)** who decides. Confidentiality's hard cases are always decided by an accountable human, never an autonomous AI. Mirrors soft-post / hard-post.

### 3.4 The reasoning supplier — the fork every organisation makes

An organisation's data is protected from AI-company **collation** to exactly the degree it never reaches an AI company. Keeping the library local is necessary but not sufficient — content sent *into an external model's prompt* has left. The fork:

- **Branch A — public AI models:** best reasoning, no infra, fastest. Collation risk is real at the query boundary; rests on the provider's promise (trust, not sovereignty). **Requires an egress-minimisation layer** (only de-identified / abstracted queries cross; raw sensitive data never does). Protects data **partially**.
- **Branch B — the organisation's own model (local / self-hosted):** data never leaves; collation is **structurally impossible**. Costs hardware; a domain model on the org's own data can be excellent. Protects data **fully**.
- **Hybrid:** sensitive work to the own model (B), general work to public models (A); the Librarian enforces which is which.

**The fork does not change the core.** Governance, pairings, Librarian, library are identical either way; only *where the reasoning comes from* changes. This is the deliberate meaning of *"use UniCORE, or build your own."*

## 4. The invariants are also device- and model-agnostic

Consistent with [`HORIZON.md`](../HORIZON.md) ("Devices evolve; the sovereign pairing does not"): the *device* an organisation's people use is evolvable, the *reasoning supplier* is swappable (§3.4), and the *sovereign governed pairing* is the constant. A deployment made today on today's devices remains valid as devices evolve, because the architecture binds the *relationship* (human-sovereign, AI thinks-and-does-but-never-decides, governed at every level), not the hardware.

## 5. The one thing that changes — the vertical layer

Every deployment composes three layers; only the middle one is vertical-specific:

- **UniCORE AI** — the governance layer (12-Level model, TrueAI, ILMP `00017`, audit + override engines). *Unchanged across verticals.*
- **The vertical layer** — the organisation's domain business objects and workflows. **This is the only layer that changes.** It lives in that vertical's gift-layer repo family (`UniCORE.<Vertical>` / `UniSaaS.UniCORE.<Vertical>`).
- **UniCORE.GVB** — the substrate (nodes, per-node stores, mail security, the org's forge/version store). *Unchanged across verticals.*

Worked and anticipated instances of the vertical layer (per VERTICAL-ENTRY):

| Vertical | Vertical layer | Home |
|---|---|---|
| **Law** | legal business objects (matters, engagements, conflicts, jurisdiction, e-invoicing) | `UniCORE.Law` / `UniSaaS.UniCORE.Law` — live reference vertical |
| **Accountancy** | accountancy objects (ledgers, working papers, filings) | future `UniCORE.<Vertical>` family |
| **Business** | the business's own operational + commercial objects | future family |
| **School / University** | education objects (student, research, administrative records) | future family |
| **Government body** | jurisdiction objects under a Government-scope CORE (see `HORIZON.md`) | future family |

To create a new vertical, follow the `developer-doctrine` VERTICAL-ENTRY process: it defines entry criteria, the four-repo family creation, and reference-architecture integration. This guide is the deployment pattern those verticals instantiate; everything except the vertical layer carries over unchanged.

## 6. Deployment steps (generic)

Building on `00019` §7, specialised by the vertical guide:

1. **Provision the substrate (UniCORE.GVB).** Node(s), per-node data store, version/forge store. All local.
2. **Install UniCORE AI (governance).** Governance engine, ILMP bus (`00017`), append-only audit engine, human override engine. Governance MD files load read-only.
3. **Define Organisation Governance.** Choose the ladder (how many levels) from org size × the org's governance definition. Author the org's governance MD files. Bind the accountable human at the top level.
4. **Install the vertical layer.** Deploy the sector's business objects and workflows; load the org's domain model. *(This step is what a vertical guide details.)*
5. **Stand up the data library and Librarian.** Ingest the org's data into the one local library. Define each person's access. Configure the Librarian (containment, open-by-access, automatic routine flow, issue-escalation to a human 1H1C).
6. **Provision people's pairings.** A 1H1C (decide) and a 1H2C (think) per person on the internal network. Verify routing and that pairings reach the Librarian, never the library directly.
7. **Choose the reasoning supplier (§3.4 fork).** Branch A + egress-minimisation, Branch B, or hybrid. Confirm no sensitive content reaches an external model except through minimisation.
8. **Validate and begin operation.** Schema, governance, messaging, drift-baseline validation. Confirm the 12-Level walk certifies actions, hard posts require a human, the audit log is append-only, nothing exfiltrates. Enter deterministic, governed, audited operation.

## 7. Why this guide matters

Every organisation that handles data it is trusted with — clients', students', citizens', its own — faces the same choice AI now forces: surrender that data to an AI company's cloud and trust their promises, or keep it, govern it, and stay sovereign. This pattern is the second path, made concrete and reusable across every sector. It does not require buying anything: an organisation may deploy UniCORE, **or build its own** from this pattern. The point is that AI-compliant, sovereign, truth-anchored operation is achievable and here documented as a pattern any vertical can instantiate — so the whole of professional and institutional life can reach it.

---

*Given, not sold. Irrevocable. CC BY 4.0 — Bryan Fred, Unitek Systems Limited.*
