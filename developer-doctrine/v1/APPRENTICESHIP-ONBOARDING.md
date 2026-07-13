# APPRENTICESHIP-ONBOARDING.md

**Post-2027 apprenticeship programme for new UniCORE-AI developers.**

This document describes the apprenticeship model for onboarding new human producers into the UniCORE-AI development programme. It is a forward-looking document (post-December 2027) describing a programme that does not yet exist in operational form. It is included in `v1` as a design anchor.

---

## Why an apprenticeship model

The UniCORE reference architecture is designed to be copied and adapted by other Generation IT producers building Solutions in other verticals. However, the first Solution in a new vertical requires full-stack-in-vertical Generation IT — a rare profile. The apprenticeship model bridges from "interested producer with domain experience" to "producer who can build a UniCORE-conformant Solution."

The model assumes that by post-2027, the foundation triad (UniVERSE / TrueAI / UniCORE-AI) will have been in production for at least 18 months, with UniCORE.Law and UniCORE.GVB as live reference implementations. The apprenticeship programme uses those reference implementations as teaching tools.

---

## The apprenticeship structure

### Tier 1 — Observer (1-3 months)

The apprentice observes Team UniCORE's operation:
- Reads the public repos (UniVERSE, TrueAI, UniCORE-AI, UniCORE, UniCORE.GVB)
- Follows the GitHub Discussions and public commit history
- Attends no private channels; receives no internal documents
- No access to Claw workspaces or production systems

Goal: understand the pattern before touching any code.

### Tier 2 — Apprentice Paired (3-6 months)

The apprentice is paired with a Claw (not Bryan Fred directly — a dedicated Apprentice Claw) and works on:
- A sandboxed learning environment (not production, not real client data)
- Exercises drawn from real UniCORE patterns (test authoring, documentation, adapter design)
- The Apprentice Claw operates under standard envelope; the apprentice human provides direction

The apprentice does not touch production systems, real client data, or the public gift surface without explicit Team UniCORE review.

### Tier 3 — Producer Candidate (6-12 months)

The apprentice, now operating as a producer with their own Claw, builds their first vertical Solution:
- Under Team UniCORE supervision (not solo)
- Using the foundation triad as a reference
- With a defined scope (one vertical, one client engagement)
- The first production deployment is reviewed by Team UniCORE before going live

### Tier 4 — Independent Producer (12+ months)

The producer operates independently:
- Owns their vertical Solution and its commercial layer
- Participates in the UniVERSE / TrueAI / UniCORE-AI public surface as a contributor
- May propose changes to the foundation triad via the Discussions interface
- May mentor future apprentices

---

## The producer pool and why it matters

Bryan's reflection (2026-05-21) on the constrained producer pool:

> "The first Solution in a new vertical needs full-stack-in-vertical Generation IT. Pool is tiny. Subsequent Solutions in other verticals need Generation IT + domain experience + the existing first Solution as a reference pattern. Pool is meaningfully larger."

The apprenticeship model is the mechanism for expanding that pool. Each independent producer who emerges from the programme becomes a reference implementation for the next wave.

---

## Cross-references

- UniCORE-AI [`developer-doctrine/v1/VERTICAL-ENTRY.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/VERTICAL-ENTRY.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/VERTICAL-ENTRY.md)) — how a new vertical enters the reference architecture
- TrueAI [`workspace-doctrine/v1/FOUNDATION.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1/FOUNDATION.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/FOUNDATION.md)) — the Foundation layer
- UniVERSE [`docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md`](https://git.unitek-systems.com/UniCORE/UniVERSE/src/branch/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md) (mirror: [GitHub](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md)) — the pairing protocol
