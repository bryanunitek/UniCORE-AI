# UniCORE Reference Implementation — Technical Status

> **Document type:** Living status paper — updated periodically as implementation progresses.
> **Stability:** Working draft. Content reflects the current state of the reference implementation.
> **Author:** Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
> **Last updated:** 2026-05-12
> **Licence:** CC BY 4.0

---

## 1. Purpose

This document records the current state of the UniCORE reference implementation — the working codebase that structurally enforces the 12-level governance architecture described in the [UniCORE AI Whitepaper](docs/whitepaper/WHITEPAPER.md) and the [TrueAI Foundation](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md).

It exists to answer one question: **what is built, what works, and what comes next?**

The reference implementation is maintained in a private repository. This status paper is the public-facing summary of that work.

---

## 2. Architecture Overview

### 2.1 Solution Structure

28 projects across multiple host configurations:

| Layer | Purpose |
|-------|---------|
| **Core Module** | 340 business objects, 29 controllers, 85 services — the governed domain |
| **Blazor Host** | Web UI with TrueAI attribution |
| **Windows Host** | Desktop UI with TrueAI attribution |
| **Web API** | REST endpoints with governed middleware |
| **Middle Tier** | Shared data-access tier |
| **Intelligent Integration Controller** | 12 projects — AI governance, orchestration, cross-system integration |
| **OpenClaw Connectivity** | Governed AI connectivity layer (Connect + SecureConnect) |
| **Control Center** | Operational administration (Win + Blazor) |
| **SaaS Variants** | Reporting and view modules (UniREPORT + UniVIEW) |
| **End-to-End Tests** | Validation suite |

### 2.2 Technology Stack

- **Runtime:** .NET 10
- **Application Framework:** DevExpress XAF 25.1
- **ORM:** DevExpress XPO
- **UI:** Blazor Server + DevExpress WinForms
- **Target:** Windows (desktop host), cross-platform (web/API/middle-tier)

### 2.3 The 12-Level Governance Model in Code

Each of the 12 UniCORE AI levels has a structural representation in the codebase:

| Level | Scope | Canonical Identity |
|-------|-------|-------------------|
| 1 | Global | UniCORE-Global |
| 2 | Global Virtual Bridge | UniCORE-GlobalVirtualBridge |
| 3 | Continental | UniCORE-Continental |
| 4 | Regional | UniCORE-Regional |
| 5 | State | UniCORE-State |
| 6 | Data Centre | UniCORE-DataCentre |
| 7 | Platform | UniCORE-Platform |
| 8 | Product | UniCORE-Product |
| 9 | Deployment | UniCORE-Deployment |
| 10 | Tenant | UniCORE-Tenant |
| 11 | Role | UniCORE-Role |
| 12 | User | UniCORE-User |

Each level has a seeded cyber-security policy defining its boundary class, posture, and governance authority. A protocol authority resolution service determines which authority governs a given scope at runtime.

---

## 3. Current Capabilities

### 3.1 AI Governance Infrastructure

- **12-level scope chain** — enumerated, seeded, and resolvable at runtime
- **AI mode resolution** — per-scope On/Off/Disabled/HardOff with hierarchical override (higher scope always wins)
- **Protocol authority resolution** — runtime-enforced boundary and provider decisions per scope
- **Governance mode groups** — UniCOREMaster, Governance, Unitek, Client authority tiers
- **Boundary classes** — SecureConnect, SecureMessaging, Connect — enforced per scope
- **Policy violation detection** — runtime governance breach handling with alert generation
- **Governance alerts** — structured alert objects with category classification and violation event tracking
- **Governed service state** — lifecycle management for Integration Controller services

### 3.2 TrueAI Attribution

- **Web (Blazor):** Attribution badge component, visibility driven by AI mode resolution
- **Desktop (Windows):** Status-bar attribution panel in Ribbon UI
- **Service layer:** Singleton attribution service consuming the AI mode resolver
- **Fixed attribution text:** "Powered by UniCORE AI. Built on the TrueAI Foundation."

### 3.3 Protected Data Governance

- **Field-level AES-GCM encryption** — 20 encrypted field slots per protected record
- **Two-stage approval workflow** — requester ≠ approver enforcement (except Bank Master self-approval)
- **Shadow audit trail** — encrypted before/after snapshots on every lifecycle event
- **Atomic restore** — two-phase validate-then-apply rollback with decryption verification
- **Physical-delete guard** — 7 reference-path checks before any permanent deletion is permitted
- **Access request governance** — explicit grant required before viewing protected fields

### 3.4 AI Artifact Development

- **Governed draft lifecycle** — AI-generated artifacts (reports, enquiries, dashboards) pass through Draft → Validated → Published states
- **Artifact validation** — structural and governance checks before publication
- **Development disclosure** — governed disclosure of AI involvement in artifact creation
- **Business object projection** — governed projection of domain objects into AI-consumable form
- **Tax governance facade** — scope-aware tax rule application with protocol authority resolution

### 3.5 Intelligent Integration Controller

- **Abstractions layer** — contracts, DTOs, AI mode context, governance scope definitions
- **Core engine** — orchestration logic for governed AI interactions
- **Connectors** — Aderant legacy system connector (legal sector)
- **Service modules** — Transfer, Messaging, Workflow, AI Orchestration, AI Communication, Conflict
- **Persistence** — governed state storage for integration operations
- **Isolated hosts** — separate Win and Blazor.Server applications for the controller

### 3.6 Legal Domain (First Vertical)

340 business objects covering:

- **Practice management** — Matter, Client, Name/People, Personnel, Department, Office, Region
- **Time and billing** — Time entry (6 variants), billing headers, bill matters, bill transactions, WIP
- **Accounts payable** — Vendor invoices, payment instructions, check requests, suppliers
- **Accounts receivable** — AR invoices, allocations, collection workflows (activity, dispute, outcome, promise)
- **Trust accounting** — Trust accounts, trust transactions, governed reconciliation
- **Conflict checking** — Conflict search controller, conflict requirement evaluation
- **Expense management** — Expense claims, disbursements, adjustment notes
- **Reporting** — Report definitions, scheduled runs, dashboard definitions, enquiry definitions
- **Security** — Role assignments, application areas, tenant configuration, licensing resolution

### 3.7 Governance Workflows

- **Approval engine** — `ApprovalRequest` with rules, decisions, and outcome tracking
- **File opening** — Request and workflow controllers for new matter creation
- **Secure transfer** — Approval workflow for governed cross-system data movement
- **E-Billing** — Submission and appeal controllers
- **Accounting period lifecycle** — Governed period open/close with status tracking

---

## 4. In Progress

| Item | Description |
|------|-------------|
| About/Credits dialog | Blazor + Win — surfaces attribution, version, and governance status |
| Integration Controller Phase 1 | Runtime activation of the orchestration pipeline |

---

## 5. Planned

| Item | Description |
|------|-------------|
| Full 12-level cascade resolution | Every AI request evaluated against the complete scope chain at runtime |
| Cross-continental relay | GlobalVirtualBridge scope activated for multi-region governance relay |
| Governed markdown publication | AI-generated markdown passes through publication authority before output |
| Governed AI draft pipelines | Full wiring of artifact governance into AI preview/generation paths |

---

## 6. TrueAI Invariant Compliance

### Structurally Enforced Today

| TrueAI Invariant | Implementation |
|-----------------|----------------|
| **Truth** | Governance violation events capture breaches; policy violation service detects them at runtime |
| **Evidence** | Shadow audit trails with encrypted before/after snapshots on every protected data lifecycle event |
| **Verification** | Two-phase validate-then-apply pattern; artifact validation service checks drafts before publication |
| **Transparency** | Attribution badge (Blazor) + status-bar panel (Win); artifact development disclosure service |
| **Accountability** | Governance workflows with requester/approver separation; user audit on all shadow entries |
| **Sovereignty** | HardOff at any scope overrides all lower scopes; human override always available |
| **Boundaries** | Boundary classes (SecureConnect/SecureMessaging/Connect) enforced per scope via seeded policy |
| **Consent** | Access requests require explicit grant; deployment environment changes require request approval |
| **Continuity** | State locks for runtime preservation; succession planning in programme governance |

### Documented but Not Yet Runtime-Enforced

- Full 12-level cascade resolution on every AI request path
- Cross-continental relay via Global Virtual Bridge
- Governed markdown publication enforcement on AI output

---

## 7. Metrics

| Metric | Value |
|--------|-------|
| Source files | 658 |
| Business objects | 340 |
| Controllers | 29 |
| Services | 85 |
| Integration Controller projects | 12 |
| Host applications | 8 (4 primary + 4 variants) |
| Build result | 87/87 succeeded |
| Target framework | .NET 10 |

---

## 8. Companion Documents

- [UniVERSE Governed Intelligence Whitepaper](https://github.com/bryanunitek/UniVERSE/blob/main/docs/whitepaper/WHITEPAPER.md)
- [TrueAI Foundation Whitepaper v1.0](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md)
- [UniCORE AI Architecture Whitepaper v1.0](docs/whitepaper/WHITEPAPER.md)
- Reference Implementation Repository (private)

---

## Contact

- **Public discussion:** [GitHub Discussions](https://github.com/bryanunitek/UniCORE-AI/discussions)
- **Private contact:** [LinkedIn](https://www.linkedin.com/in/bryan-fred-02209753/)

---

*This document is updated after each significant batch of implementation work. It is not a whitepaper — it is a living record of what exists, what works, and what comes next.*
