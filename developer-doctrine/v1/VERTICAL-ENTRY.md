# VERTICAL-ENTRY.md

**How a new vertical enters the UniCORE reference architecture.**

This document describes the process by which a new vertical Solution (Banking, Healthcare, Accounting, or any other professional services vertical) is added to the UniCORE reference architecture. It is for human decision-makers and for Claws working on the UniCORE-AI reference architecture who need to understand the process.

---

## What a vertical is

A **vertical** in the UniCORE context is a distinct professional services domain with its own data model, regulatory environment, billing patterns, and client engagement patterns.

Today, two verticals are live:
- **UniCORE.Law / UniSaaS.UniCORE.Law** — law firms, time-and-billing, matter-centric data model
- **UniCORE.GVB / UniSaaS.UniCORE.GVB** — global law firm infrastructure, multi-node tenancy, DNS/mail/security substrate

Future verticals (Banking, Healthcare, Accounting, Tax, Audit) will follow the same pattern.

---

## The entry criteria

A vertical qualifies for entry into the UniCORE reference architecture when:

1. **A producer with domain experience exists.** The vertical requires a human producer who has deep experience in that domain (not just software experience — domain experience). The producer drives the vertical's data model, regulatory posture, and client engagement patterns.
2. **The foundation triad applies.** The vertical operates under the TrueAI Foundation (truth contract, Nine Invariants, Singular Pairing, Gift Principle, Reversibility) and the UniCORE-AI reference architecture patterns (Vertical CORE, substrate services, governance models).
3. **A gift-layer repo family is created.** Each vertical produces a public gift-layer repo family (e.g. `UniCORE.<Vertical>`, `UniSaaS.UniCORE.<Vertical>`) under CC BY 4.0, following the UniVERSE / TrueAI / UniCORE-AI pattern.
4. **A commercial-layer Claw repo is created.** The commercial implementation (the actual Solution, not the reference) lives in a private Claw repo (e.g. `UniCORE.<Vertical>-Claw`, `UniSaaS.UniCORE.<Vertical>-Claw`) accessible only to the producer and their paired Claw.

---

## The entry process

### Phase 1 — Foundation alignment (human decision)

The producer confirms alignment with the foundation triad:
- TrueAI truth contract and Nine Invariants
- UniVERSE PairedClaw Bond Protocol
- CC BY 4.0 gift-layer commitment
- Singular Pairing (1 human + 1 Claw per workstream)

This is a human-level decision. The Claw surfaces the requirements; the human confirms alignment.

### Phase 2 — Repo family creation

Team UniCORE (or the Claw acting under Team UniCORE's authorisation) creates the four-repo family for the new vertical:

```
bryanunitek/UniCORE.<Vertical>              — public on-prem gift surface
bryanunitek/UniSaaS.UniCORE.<Vertical>      — public SaaS gift surface
bryanunitek/UniCORE.<Vertical>-Claw        — private on-prem working repo
bryanunitek/UniSaaS.UniCORE.<Vertical>-Claw — private SaaS working repo
```

Each repo is anchored at a stable starting tag (not full history), following the fork discipline documented in each repo's `STARTING-POINT.md`.

### Phase 3 — Reference architecture integration

The new vertical's reference architecture is built by adapting the Vertical CORE pattern:

1. **Substrate services** — the new vertical inherits the existing substrate services (Governance, Messaging, Persistence, Tenancy, NodeOperations) with minimal changes. Substrate services are shared across verticals.
2. **Vertical-specific services** — the new vertical adds its own domain services (e.g. for Law: BillMatterCalculation, TaxRateResolution, NVarcharDataMode). These are new code.
3. **Governance models** — the new vertical adopts the existing invariant patterns (BillInvariantGuard, AI mode transitions, governance thresholds) and adds vertical-specific invariants where required.
4. **Data model** — the new vertical's business objects (Matter, BillHeader, Client, etc.) are mapped to the UniCORE reference architecture patterns.

### Phase 4 — First production deployment

The vertical's first production deployment follows the same pattern as UniCORE.Law and UniCORE.GVB:
- First client engagement (proof-of-concept or paid engagement)
- Attestation record (foundation conformance attestation)
- Sanity Check entry (monthly sanity check fleet)

---

## UniCORE.Law and UniCORE.GVB as reference implementations

UniCORE.Law and UniCORE.GVB are the reference implementations. They demonstrate that the foundation triad pattern produces a working Enterprise Solution. Future verticals use them as reference architecture examples, not as templates to copy directly.

The key distinction: UniCORE.Law and UniCORE.GVB are the first Solutions in their respective verticals (Law, Infrastructure). They are not one-size-fits-all templates. They are proof that the pattern works.

---

## Cross-references

- TrueAI [`workspace-doctrine/v1/FOUNDATION.md`](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/FOUNDATION.md) — the Foundation layer
- UniVERSE [`docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md) — the pairing protocol
- UniCORE-AI [`developer-doctrine/v1/APPRENTICESHIP-ONBOARDING.md`](APPRENTICESHIP-ONBOARDING.md) — post-2027 apprenticeship programme

---

## Document history

- 2026-06-12 (884a62d) — doc(developer-doctrine/v1): anchor v1 — role-specific doctrine for UniCORE-AI developer Claws

*Back-filled from git log on 2026-07-10 21:35 UTC. Kind 2 versioning (dated change notes) — see HORIZON.md § Evolution and versioning. Kind 1 (formal `Version:` bumps) remains OFF until first GitHub Discussion.*
