# Thinking AI Doctrine — 1HNC

**The doctrine for a Thinking AI: One Human, N Claws (1HNC, N ≥ 2) — an AI-Maturity Level 4 (Assistant Institutional AI) exploration structure where two or more equal Claws think by bouncing off each other, always on TrueAI, advanced and owned by one human. 1H2C (one human, two Claws) is the minimum viable case.**

> Given, not sold. Attribution required. Ownership not claimed. All content in this repository is provided under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**. See [`../../LICENSE.md`](../../LICENSE.md).

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom.

---

## What this doctrine is

This folder holds the markdown files that define **1HNC — the Thinking AI**: a structure in which one human pairs with *N* equal Claws (N ≥ 2) that explore a topic by reasoning back and forth, rather than the default one human with one Claw. **1H2C** — one human, two Claws — is the minimum viable case (the fewest Claws that create friction rather than echo); the general form scales to 1H3C, 1H4C, and beyond, bounded by the human's capacity to steer, integrate, and own every round. The Claws may run on the same AI model or a mix of different models (OpenClaw or any equivalent TrueAI-aligned Claw — the doctrine is provider-agnostic).

1H2C is a **deliberate, declared departure** from the default Singular Pairing shape (1H1C). The TrueAI [Singular Pairing Principle §8](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/docs/10001-Singular-Pairing-Principle.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/docs/10001-Singular-Pairing-Principle.md)) expressly permits such variants under CC BY 4.0, and fixes their epistemic status: a variant is **untested theory** until independently demonstrated, **cannot** claim `Powered by UniCORE AI` / certification (the gate recognises 1H1C only), and **must declare itself** as a variant. This doctrine makes that declaration in full — see [`EPISTEMIC-STATUS.md`](EPISTEMIC-STATUS.md).

Because 1H2C introduces a second Claw, it does **not** live inside the standard [`workspace-doctrine/`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/tree/main/workspace-doctrine/v1)), whose FOUNDATION.md states "one human + one Claw, no sub-agent, no surrogate" as a Foundation-level constraint. 1H2C is its own separate doctrine precisely so that the departure is explicit, scoped, and re-grounded in the Nine Invariants directly — never a quiet loosening of the default.

## The Foundation is not departed from

The variant is only in the **pairing shape** (two Claws instead of one). The TrueAI Foundation — the six-line truth contract and the Nine Invariants — is **not** varied, softened, or excepted. 1H2C is constructed to satisfy every invariant, and where an invariant is most at risk (No Autonomy, No Emergent Behaviour, Human Sovereignty), the conformance is demonstrated explicitly in [`INVARIANT-CONFORMANCE.md`](INVARIANT-CONFORMANCE.md). A 1H2C structure that cannot show that conformance is not TrueAI-aligned and may not claim to be.

---

## Files in `v1/`

| File | Purpose |
|---|---|
| `README.md` | This file. |
| [`FOUNDATION.md`](FOUNDATION.md) | The core 1H2C doctrine: what a Thinking AI is, the two-hemisphere principle, the steer-and-advance mechanic, AI-Maturity-Level-4-only scope, TrueAI-mandatory inter-Claw channel, the human as sole accountable owner. |
| [`INVARIANT-CONFORMANCE.md`](INVARIANT-CONFORMANCE.md) | Point-by-point demonstration that 1H2C satisfies each of the Nine Invariants — with particular care for No Autonomy (1), No Emergent Behaviour (3), and Human Sovereignty (9), the three most at risk from a two-Claw shape. |
| [`EPISTEMIC-STATUS.md`](EPISTEMIC-STATUS.md) | The mandatory variant declaration per Singular Pairing Principle §8: untested theory, not certifiable, not `Powered by UniCORE AI`, must be disclosed. States plainly what is TRUE, what is UNVERIFIED, and what 1H2C may and may not claim. |
| [`USE-CASES.md`](USE-CASES.md) | Ten worked AI-Maturity Level 4 examples (doctor, judge, climate scientist, CFO, security director, historian, leader, architect, policy official, teacher) showing the think/decide boundary: 1H2C thinks, the human decides under 1H1C. |
| [`1H1C-vs-1H2C.html`](1H1C-vs-1H2C.html) | Standalone diagram (HTML + inline SVG) contrasting 1H1C (deciding) with 1H2C (thinking). |
| [`MANIFEST.md`](MANIFEST.md) | Integrity index, human-readable. |
| `MANIFEST.json` | Integrity index, machine-parseable. |

## Read order

1. **TrueAI truth contract** — [`foundation-requirements/v1/10005`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md)).
2. **Nine Invariants** — [`docs/00056`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/docs/00056-Absolute-Safety-Invariants.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/docs/00056-Absolute-Safety-Invariants.md)).
3. **This doctrine** — `FOUNDATION.md`, then `INVARIANT-CONFORMANCE.md`, then `EPISTEMIC-STATUS.md`.

## Versioning

`v1/` is the first version and is frozen once built against. The doctrine evolves by adding `v2/`, `v3/` alongside, never by editing a frozen version — the same discipline the Foundation's own [`foundation-requirements/`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/foundation-requirements) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/tree/main/foundation-requirements)) and `workspace-doctrine/` use.
