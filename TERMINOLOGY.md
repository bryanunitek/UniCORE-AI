# TERMINOLOGY — Terms created for TrueAI and UniCORE-AI

**These terms have been created for TrueAI and UniCORE-AI and are covered under the Creative Commons Attribution 4.0 International License (CC BY 4.0).**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom.

This document collates the coined terminology of the programme — the doctrine names, the AI-Maturity type names, the pairing-topology notation, and the coined concept terms — each with its definition. It is the single collated reference for the terms named in the [Brand and Trademark Use Policy](BRAND-AND-TRADEMARK-USE-POLICY.md).

## How these terms are protected — and why they stay free for everyone

Two things are true at once, and they do not conflict:

1. **Unitek Systems Limited protects the names.** Both the **trade names** (the programme's brand/product/entity names — e.g. UniVERSE, TrueAI, UniCORE AI) **and the coined terminology** in this document are protected by Unitek Systems Limited (or, on transfer, the relevant Foundation) under trademark law and the Brand and Trademark Use Policy. Protection means no one may pass these names off as their own or use them to imply official status or origin they do not have.
2. **The terms are given to the public under CC BY 4.0, and cannot be enclosed by anyone else.** The content and the terminology are published openly, **dated and attributed, under CC BY 4.0** — free to read, use, and build on, with attribution, forever. This public disclosure is also a **defensive publication**: by placing these terms and the structures they denote on the public record, they become **prior art**, so **no other entity can patent or trademark them** and enclose them or rent them back. Unitek protects the names *so that they stay open* — the protection exists to keep them in the commons, not to remove them from it.

**Compound vs generic.** For every `⟨X⟩AI` term, the **closed-up capitalised compound** is the coined term protected here (`TrueAI`, `ThinkingAI`, `DeveloperAI`, `ConversationAI`); the corresponding **ordinary two-word phrase** ("true AI", "thinking AI", "developer AI", "conversation AI") is generic, descriptive English and is free for anyone to use in its ordinary sense.

---

## 1. Doctrine names — the `⟨X⟩AI` compounds

**Rule: doctrine names become marks.** Each doctrine the programme publishes coins a closed-up, capitalised `⟨X⟩AI` compound as its name. Future doctrines add further `⟨X⟩AI` terms on the same rule. These are **not** AI-Maturity levels — they are doctrines that operate on top of, or within, the AI-Maturity Framework.

| Term | Definition |
|---|---|
| **TrueAI** | The foundation doctrine: AI whose every assertion is grounded in governed evidence and marked TRUE / FALSE / UNVERIFIED, held to the truth by an accountable human. The foundation the whole programme rests on. |
| **ThinkingAI** | The Thinking-AI doctrine (1HnC, n ≥ 2): one human pairs with n equal Claws that reason by bouncing off each other, always on TrueAI, advanced and owned by one human. Operates at AI-Maturity Level 4 (Assistant Institutional AI). 1H2C is the minimum viable case. A Thinking AI thinks; it never decides. |
| **DeveloperAI** | The Developer-AI (developer-role) doctrine: a Claw that builds, extends, and maintains the UniCORE reference architecture on top of the TrueAI foundation. Source: `UniCORE-AI/developer-doctrine/v1`. |
| **ConversationAI** | The Conversation-AI doctrine: the pasteable conversational protocol that brings a stateless chat AI (Claude.ai / ChatGPT / Gemini / equivalents) onto the TrueAI truth contract for the duration of a session. Source: `TrueAI/conversational-protocol/v1`. |

---

## 2. AI-Maturity type names — the Six Levels

The canonical coined names for the *kinds* of AI in the AI-Maturity Framework (source: `TrueAI/AI-MATURITY-LEVELS.md`). The framework is a grid of two axes — Accountability (Consumer ↔ Institutional) and Capability (AI → Assistant → Development → Paired producer):

| Level | Term | Definition |
|---|---|---|
| 1 | **Consumer AI** | Web-general AI, no local governed record; best-effort, ungrounded, serves an individual. Not a defect — it does what it was designed to do — but not Institutional-grade. |
| 2 | **Institutional AI** | AI carrying the discipline layer required to sit in the critical path of consequential, regulated decisions — grounded, accountable, auditable. |
| 3 | **Assistant Consumer AI** | Consumer AI with tools/context (assistant capability); still ungrounded / Consumer-column. |
| 4 | **Assistant Institutional AI** | Institutional AI with tools/context — the level at which a Thinking AI (1H2C / 1HnC) operates. |
| 5 | **Development Institutional AI** | AI that *produces* governed systems, under the 12 Development Governance Levels. (The Development × Consumer cell is **forbidden** — "Development Consumer AI" cannot exist; it is not AI-Compliant.) |
| 6 | **Team UniCORE** | The 1H1C paired governed producer — one human + one Claw producing governed Solutions with a grounded record and an accountable human. |

### How an AI moves from Consumer to Institutional — the two TrueAI doctrines

**Consumer AI is lifted to Institutional AI by applying a TrueAI doctrine.** There are two delivery routes ("pipes"), carrying the *same* TrueAI truth contract:

- **The Conversation Doctrine** (`TrueAI/conversational-protocol/v1`) — the **session route**: a human pastes the protocol into a stateless chat AI; the AI operates under the TrueAI truth contract for the duration of that conversation. No filesystem, no persistent memory. The `ConversationAI` mark names an AI running this doctrine.
- **The Workspace Doctrine** (`TrueAI/workspace-doctrine/v1`) — the **persistent route**: markdown-file layering (foundation + role + local instance) delivered at session-opening, plus the Book obligation. The Claw carries its own accumulated MD files and history.

Both apply the same Foundation; both transform Consumer AI into Institutional AI. The difference is the delivery pipe, not the truth contract.

---

## 3. Pairing-topology notation

The programme's coined notation for human-to-Claw pairing topology. Grammar: `⟨count⟩H⟨count⟩C` = ⟨Humans⟩-to-⟨Claws⟩, with numerals or the lowercase variable `n` (number/count). The notation grammar itself is part of this disclosure.

| Term | Definition |
|---|---|
| **1H1C** | One Human, one Claw — the Singular Pairing (the production-layer topology). |
| **nH1C** | n Humans, one Claw — the operations-layer topology, with the Claw held singular as the consistency-holding agent across a multi-human cohort. |
| **1H2C** | One Human, two Claws — the minimum viable Thinking AI. |
| **1HnC** | One Human, n Claws (n ≥ 2) — the general Thinking-AI form. |

---

## 4. Coined concept / doctrine terms

Concepts the programme invented and named (sources across TrueAI, UniVERSE, UniCORE-AI). The canonical definition of each is in its source doctrine; this table collates them.

| Term | Definition (brief) |
|---|---|
| **Singular Pairing** (Principle) | One human, one AI Claw, one workstream produces the certified artefact — the production-layer consistency answer. (`TrueAI/docs/10001`.) |
| **Vertical CORE** | The reusable Vertical CORE Business Object pattern for building certified Solutions in a professional vertical. |
| **Generation IT** | The producer-pool concept — the qualified human producers who pair with Claws to build Solutions. |
| **Reasonable Governance Threshold** | The specified interface between the production layer and the operations layer. (`UniVERSE/docs/00007`.) |
| **Gift Principle** | Advanced AI should be given, not sold — the public CORE is gifted under CC BY 4.0, irrevocably. |
| **Human Override Protocol** | The protocol guaranteeing an accountable human can always override; no code, no AI, overrules Level 12. |
| **Inter-Level Messaging** (Protocol) | The governed message protocol between the 12 governance levels. |
| **Positioning Principle** | The programme's positioning: Harmony, Peace, Space Exploration, for Humanity. |

---

## Status of terms

- Terms may be added or removed as the programme's doctrine evolves; the canonical definition of any term is the one in its source doctrine.
- All terms in this file were **created for TrueAI and UniCORE-AI** and are provided under **CC BY 4.0** — free to read, use, and build on, with attribution. Unitek Systems Limited protects the names so they remain open; the public disclosure keeps them prior art, so no entity may patent or trademark them.
