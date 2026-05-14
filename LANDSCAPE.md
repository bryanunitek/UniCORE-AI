> **Canonical home:** [UniVERSE — `LANDSCAPE.md`](https://github.com/bryanunitek/UniVERSE/blob/main/LANDSCAPE.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# LANDSCAPE

**Where UniCORE AI and the TrueAI Foundation sit in the current AI governance landscape.**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: May 2026
Status: Public. Given, not sold. Irrevocable.
Version: 1.0

---

## 1. What This Document Is

This document compares the published governance structures of the major AI laboratories against the TrueAI Foundation and the UniCORE AI architecture.

It is not an evaluation of safety outcomes. It is not a commentary on commercial strategy, internal culture, or implementation quality. It is a structural comparison: what has each organisation published about how it places its AI systems under human authority?

The comparison exists so that readers of the TrueAI Foundation and UniCORE AI whitepapers can orient those documents against the wider landscape. The whitepapers remain the authoritative references. This document is a map, not the territory.

---

## 2. The Three Programme Layers

The programme has three layers. A comparison must be specific about which layer it addresses, because each layer answers a different question.

| Layer | What it is | Question it answers | Repository |
|-------|-----------|---------------------|------------|
| **TrueAI Foundation** | Nine Invariants — the architectural floor an AI system must meet to be governable | What must an AI system *be*? | [`bryanunitek/TrueAI`](https://github.com/bryanunitek/TrueAI) |
| **UniCORE AI** | 12-level governance stack — one reference implementation of the floor | How can it be *governed*? | [`bryanunitek/UniCORE-AI`](https://github.com/bryanunitek/UniCORE-AI) |
| **UniVERSE** | Civilisational programme — enterprise, governmental, space mission, long-duration contexts | *Why* does the floor exist? | [`bryanunitek/UniVERSE`](https://github.com/bryanunitek/UniVERSE) |

TrueAI is the foundation. UniCORE AI is one architecture built on it. UniVERSE is the programme that carries both forward. They are published as separate documents, in separate repositories, under separate version control — deliberately. The foundation does not depend on the architecture. The architecture does not depend on the programme. Each layer can be cited, challenged, and built against independently.

---

## 3. The Nine Invariants — The Architectural Floor

The TrueAI Foundation publishes nine invariants as the minimum architectural properties required for an AI system to be placed under named human authority. They are stated as absolutes. Each one is the failure mode it prevents, expressed as a structural prohibition.

1. **No Autonomy.** The AI does not generate goals, initiate decisions, or take actions outside human-defined thresholds.
2. **No Self-Modification.** The AI does not alter its own architecture, constraints, governance, or thresholds.
3. **No Emergent Behaviour.** The AI does not self-organise, self-optimise, form distributed cognition, or develop evolved reasoning modes. It does not generate its own internal life-cycles, heartbeats, timers, or loops.
4. **No Human Influence.** The AI does not influence a human's thoughts, emotions, decisions, beliefs, culture, politics, or identity.
5. **No Domain Merging.** The AI does not merge contexts, populations, jurisdictions, or sovereign boundaries. It does not communicate peer-to-peer with other systems, and it does not transfer governance context across boundaries human authority has kept separate.
6. **No Authority Assumption.** The AI does not assume command, governance, legal interpretation, medical authority, navigational authority, or economic authority. Where a human role is vacant, the system holds the boundary, flags the vacancy, and awaits human appointment.
7. **Determinism with Reversibility.** The AI's actions remain predictable, reversible, auditable, and threshold-bound. It does not fabricate facts, authorities, citations, identifiers, or evidence. Where a claim cannot be substantiated, the system classifies the outcome as `UNVERIFIED` — a first-class result, not a failure to hide.
8. **Transparency Without Exception.** Every action is logged, every decision is exposable, every record is preserved. Where governance is absent, the system stops, logs, and surfaces the gap rather than inventing a rule to fill it.
9. **Human Sovereignty as Root.** Humans remain the final authority across every domain and deployment. All other invariants derive from this one.

Canonical source: [TrueAI Foundation v1.0 §3](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md).

Two properties matter for the landscape comparison:

- **Invariants 1, 2, 3, and 6 are prohibitions on what the system may be.** They are not mitigation policies, deployment guardrails, or training-time alignment objectives. They are properties of the architecture itself. A system that satisfies them by training but could violate them by configuration does not satisfy them.

- **Invariant 9 is the root.** It is not a level. It applies at every layer, in every deployment, across every domain. The named human authority — a specific person or specific role, never a system — is the final point of decision in every chain.

---

## 4. The 12-Level Architecture

UniCORE AI is one reference implementation of the TrueAI Foundation floor. It uses a deterministic vertical stack of twelve governance levels. It is not the only possible implementation; it is the one Unitek Systems Limited publishes as a reference.

| Level | Name | Role |
|-------|------|------|
| 1 | Truth | Factual status of claims |
| 2 | Evidence | Human-submitted supporting material |
| 3 | Verification | Cross-checking and consistency |
| 4 | Context | Jurisdiction, time, situation |
| 5 | Interpretation | Meaning derived from evidence and context |
| 6 | Governance | Human-authored rule-set decisions |
| 7 | Compliance | Legal, regulatory, and mission rules |
| 8 | Operations | Governed decisions about permitted actions |
| 9 | Execution | Deterministic, bounded action |
| 10 | Audit | Immutable, append-only record |
| 11 | Stability | Drift detection and monitoring |
| 12 | **Human Governance** | The sovereign level. Intentionally imperfect. Never overridden. |

Truth flows **upward** through Levels 1–5. Governance flows **downward** from Level 12. No level may bypass another. No level may communicate horizontally. No level may initiate its own activity.

Level 12 is not the top of the stack because humans are more intelligent than the system beneath them. It is the top because **the system must never be above them**.

Canonical source: [UniCORE AI v1.0 §3](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/whitepaper/WHITEPAPER.md).

---

## 5. The Landscape — How the Major Laboratories Publish Governance

The following table compares what each major AI organisation has published about the structural relationship between its AI systems and human authority. The comparison is based on publicly available documents as of May 2026.

| Organisation | Published governance structure | How human authority is framed | Foundation / Architecture separation |
|---|---|---|---|
| **TrueAI / UniCORE AI / UniVERSE** | Nine Invariants as architectural floor; 12-level vertical stack as reference implementation | Named human authority at every level; Human Sovereignty as root invariant, applying across all levels and all deployments | Yes — three layers, three repositories, independently citable |
| **OpenAI** | [Preparedness Framework](https://openai.com/index/preparedness-framework-beta/) with capability thresholds, risk levels, and deployment mitigations; Frontier AI Safety Commitments signatory | Corporate board as final decision authority; safety thresholds may trigger halt-or-mitigate decisions | No published separation of foundation from implementation |
| **Anthropic** | [Responsible Scaling Policy](https://www.anthropic.com/news/anthropics-responsible-scaling-policy); Constitutional AI for model behaviour; Public Benefit Corporation with Long-Term Benefit Trust | Charter and Trust govern corporate decisions; model "constitution" governs model behaviour | Two layers (corporate charter + model constitution), but no published architectural-floor invariants independent of the company |
| **Google DeepMind** | [Frontier Safety Framework](https://deepmind.google/discover/blog/an-approach-to-technical-agi-safety/); Responsibility & Safety Council; integrated into Alphabet compliance | Corporate governance via Alphabet structure; technical safety evaluations at model level | No published separation; framework sits inside corporate risk management |
| **Microsoft** | [Responsible AI Standard](https://www.microsoft.com/en-us/ai/responsible-ai); governance maturity model; Copilot Trust Center with enterprise controls | Customer-side governance plus platform-side controls; human authority framed as customer responsibility | No published separation; governance is product-deployment focused |
| **Meta** | [Llama usage policies](https://llama.meta.com/trust-and-safety/); Frontier AI Safety Commitments signatory | Internal governance plus external regulatory pressure | No published separation |
| **Others** (Mistral, xAI, Cohere, Magic, Naver, G42, Amazon, NVIDIA) | Frontier AI Safety Commitments signatories with policies of varying depth; see [METR — Common Elements of Frontier AI Safety Policies](https://metr.org/common-elements) for a cross-lab survey | Mostly corporate governance | No published separation |

---

## 6. What the Comparison Shows

Three structural differences are observable. They are differences in what is published, not claims about what is practised internally.

### 6.1 The Foundation Is Independent

The TrueAI Foundation is published as its own document, in its own repository, under its own version control. It does not depend on UniCORE AI. It does not depend on UniVERSE. It does not depend on Unitek Systems Limited continuing to exist. It is published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — a gift, given once, irrevocable.

No other organisation in the table above publishes a governance foundation that is structurally independent of its own corporate entity. Every other framework in the table is authored by, versioned by, and governed by the organisation that also builds and deploys the AI systems the framework applies to. That is not a criticism of those organisations. It is an observation about a structural coupling that the TrueAI Foundation deliberately avoids.

### 6.2 The Invariants Are Prohibitions, Not Policies

The Nine Invariants state what an AI system **may not be**. They are architectural constraints — properties of the system's structure, not guidelines for its operation.

The major laboratories publish safety policies, responsible-use guidelines, deployment mitigations, and risk thresholds. These are valuable and, in many cases, represent genuine and credible commitments by the people who wrote them. But they are policies — they describe what an organisation **will do**, not what the system **cannot be**. A policy can be revised. An invariant, by definition, cannot.

The distinction matters because the failure modes the invariants prevent — autonomous goal-setting, self-modification, emergent behaviour, authority assumption — are structural. A policy commitment to prevent them is one approach. An architectural prohibition that makes them impossible is a different approach. The TrueAI Foundation takes the second.

### 6.3 Human Sovereignty Is Root, Not Role

In the TrueAI Foundation, Human Sovereignty is Invariant 9 — the root from which all other invariants derive. It is not a governance committee, not a board seat, not a review process. It is the structural condition under which all other invariants make sense: the named human authority is the final point of decision in every chain, at every level, in every deployment.

In the published frameworks of the major laboratories, human authority is typically expressed as a governance role — a board, a safety committee, a review process, a customer-side administrator. These are necessary and important. But a governance role can be restructured, a committee can be dissolved, a review process can be streamlined away. A root invariant cannot. It is the architecture, not the org chart.

---

## 7. What This Document Is Not

This document is not a ranking. No organisation in the table above is scored, graded, or placed in order.

This document is not a criticism. The safety and governance work published by the major AI laboratories is real, and much of it is done by people who are genuinely committed to the outcomes they describe. This document respects that work.

This document is not a claim that the TrueAI Foundation or UniCORE AI is complete. The invariants define the floor. The architecture describes one way to build on it. The civilisational-scale programme described in UniVERSE is a 10–20 year horizon at minimum — the systems that will fully satisfy the floor are not yet built. See [HORIZON.md](HORIZON.md) for the author's time-horizon statement.

This document is not a replacement for the whitepapers. The canonical references are:

- [TrueAI Foundation v1.0](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md) — the Nine Invariants
- [UniCORE AI v1.0](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/whitepaper/WHITEPAPER.md) — the 12-level architecture
- [UniVERSE Governed Intelligence](https://github.com/bryanunitek/UniVERSE/blob/main/docs/whitepaper/WHITEPAPER.md) — the civilisational programme

---

## 8. Sources

- [TrueAI Foundation v1.0](https://github.com/bryanunitek/TrueAI/blob/main/docs/whitepaper/WHITEPAPER.md) — primary source for the Nine Invariants
- [UniCORE AI v1.0](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/whitepaper/WHITEPAPER.md) — primary source for the 12-level architecture
- [UniVERSE Governed Intelligence](https://github.com/bryanunitek/UniVERSE/blob/main/docs/whitepaper/WHITEPAPER.md) — primary source for the civilisational programme
- [OpenAI Preparedness Framework](https://openai.com/index/preparedness-framework-beta/) — OpenAI's published risk-evaluation and mitigation framework
- [Anthropic Responsible Scaling Policy](https://www.anthropic.com/news/anthropics-responsible-scaling-policy) — Anthropic's published scaling and safety commitments
- [Google DeepMind Frontier Safety Framework](https://deepmind.google/discover/blog/an-approach-to-technical-agi-safety/) — DeepMind's published approach to frontier model safety
- [Microsoft Responsible AI Standard](https://www.microsoft.com/en-us/ai/responsible-ai) — Microsoft's published responsible-AI governance standard
- [Meta Llama Trust and Safety](https://llama.meta.com/trust-and-safety/) — Meta's published usage policies for Llama models
- METR, [*Common Elements of Frontier AI Safety Policies*](https://metr.org/common-elements) (December 2025) — cross-laboratory survey of published frontier-AI safety commitments
- Chartered Governance Institute UK & Ireland, [*From OpenAI to Anthropic: who's leading on AI governance?*](https://www.cgi.org.uk/resources/blogs/2025/from-openai-to-anthropic-whos-leading-on-ai-governance/) — comparative analysis of corporate AI governance structures

---

## Why This Matters

The question this landscape comparison surfaces is not *who is doing better*. It is *what kind of thing is being built*.

The major AI laboratories are building **capable systems** and governing them through **policies, processes, and corporate structures**. That is legitimate work, and much of it is done with care.

The TrueAI Foundation and UniCORE AI are building a **governance floor** — an architectural definition of what an AI system must be before it is placed under human authority — and offering it as a **gift**. Not tied to one company. Not gated by commercial interest. Not contingent on any organisation's continued willingness.

Truth brings harmony — whether between humans, between AIs, or between the two. Harmony is peace.

**This is a gift. Public. Not for sale. Irrevocable. There is no negotiation.** Anything else would be false, and falsehood cannot build what this is for.

— Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
