> **Canonical home:** [TrueAI — `docs/10002-Certification-Before-Layered-Governance.md`](https://github.com/bryanunitek/TrueAI/blob/main/docs/10002-Certification-Before-Layered-Governance.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# ⭐ BD — Certification Before Layered Governance

**The build-then-govern sequence that the Foundation assumes**

Version 1.0 — May 2026

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom

Licence: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

---

## 1. Purpose

This document defines the sequence in which a UniCORE Solution comes into being and the gate that separates the Build phase from the Govern phase.

It answers one question: *when may per-level governance be applied to a UniCORE Solution?*

The Nine Invariants define what the AI system itself must be. The multi-level governance model defines how human authority layers are distributed across Regions, Countries, States, organisations, missions, deployments, and users. This document defines the ordering between the two: the Solution must conform to the Foundation before the layered governance can be applied to it.

This principle sits alongside the Gift Principle and the Singular Pairing Principle. It is not a tenth invariant; it is a sequencing rule that the invariants and the layered governance model assume.

---

## 2. The sequence

A UniCORE Solution — Powered by UniCORE AI, built on the TrueAI Foundation — comes into being in a strict sequence of phases:

```
Build phase → Certification gate → Govern phase
```

Phases are serial. Level parallelism only happens *inside* the Govern phase, after the gate has been passed.

### Build phase

The Solution is produced under the Singular Pairing Principle (see [`10001-Singular-Pairing-Principle.md`](10001-Singular-Pairing-Principle.md)): one human, one AI Claw, optional small human board above. The producer pair must be Generation IT.

The Solution includes the architecture, the implementation, the reference artefacts, and the operational materials that make it a deployable whole.

### Certification gate

The completed Solution must pass TrueAI certification. Certification means demonstrable conformance to:

- the Nine Invariants (see [`00056-Absolute-Safety-Invariants.md`](00056-Absolute-Safety-Invariants.md))
- the Gift Principle (see [`00028-TrueAI-Foundation-Gift-Principle.md`](00028-TrueAI-Foundation-Gift-Principle.md))
- the Singular Pairing Principle for the Solution's own production history

Certification is a property of the Solution artefact. It attaches to the code, the architecture, and the operational artefacts of a specific versioned UniCORE Solution. It is not a property of the organisation producing the Solution, nor of any particular deployment of it.

### Govern phase

*Only after* the Solution has passed certification do the appropriate humans at the appropriate governance levels author their governance MD files. The levels include, but are not limited to: Region, Country, State, organisation, mission, deployment, user, and any other level defined by the multi-level governance model applicable to the Solution.

Each governance-level authoring is itself a singular pairing: one human at that level working with one Claw at that level. The Generation IT requirement does not apply to level-specific policy authorship in the same form — a Regional authority authoring Regional MD files is authoring policy, not producing a Solution — though the level's named human must have governance competence appropriate to that level.

---

## 3. Why the sequence is not negotiable

Governance MD files cannot be applied to an uncertified Solution. Until the Solution itself conforms to the Nine Invariants, any layered governance written on top of it would be governance over something ungovernable — rules authored for a system that has not yet earned the right to receive them.

The gate exists because the Foundation is the floor. You do not build floors on top of floors that are not yet laid. A Solution that fails any one of the Nine Invariants is not a governable substrate for the multi-level governance model, regardless of how carefully the per-level MD files are authored. In that case the governance would be theatre: rules enforceable by nothing, applied to a system that does not enforce them back.

The sequence is also what keeps the multi-level governance model honest. If MD files could be authored against an uncertified Solution, there would be a permanent pressure to backfit Foundation conformance to match whatever the Solution happens to do — a structural softening of the Nine that the Foundation does not permit.

---

## 4. What certification does and does not mean

- **Certification is conformance to the Foundation.** It is not a product endorsement. It is not a performance benchmark. It is not a regulatory licence.
- **Certification is a property of the Solution artefact.** It attaches to the code, the architecture, and the operational artefacts of a specific versioned UniCORE Solution (for example, a specific commit, tag, or release).
- **Certification does not authorise deployment.** Region, Country, State, and lower-level authorities still apply their own governance MD files — that is exactly what the Govern phase is for. A certified Solution without layered governance is not yet deployed; a layered-governance set without a certified Solution is not yet valid.
- **Certification is not perpetual by default.** Material changes to the Solution re-open the gate. Trivial changes (fixes, non-functional refactors documented as such) may not; the attestation itself specifies what is and is not in scope.
- **Certification does not override national or regional law.** Govern-phase authorities may add constraints on top of a certified Solution for their jurisdiction. They may not remove Foundation constraints, because those derive from the Nine and are below every level.

---

## 5. Who certifies

At initial publication, **no external certification body exists**. Unitek Systems Limited does not certify (see TrueAI whitepaper, Appendix C). No conformance mark, badge, or seal is issued by the author.

The starting posture is therefore **self-attestation by the named human producing the Solution**, with a complete and auditable evidence log:

- For Pattern 1 (direct singular pairing): attestation by the producer human, under their name and Generation IT status.
- For Pattern 2 (parallel isolation with fresh synthesis): attestation by the synthesis human, under their name and Generation IT status. Prototype pairings are recorded in the evidence log but do not themselves certify.

The attestation is a public, dated, named statement that the Solution at a specific version satisfies the Nine Invariants, the Gift Principle, and the Singular Pairing Principle, together with the evidence supporting each.

Third-party claims of TrueAI conformance — by deployers, integrators, or other parties — are made on the claimant's own authority. They are not endorsed by the original producer, by Unitek Systems Limited, or by the Foundation. This matches the existing third-party-claims policy in the TrueAI whitepaper and [STATEMENT-ON-CLAIMS.md](../STATEMENT-ON-CLAIMS.md).

Emergence of external certification bodies is a later-horizon concern (see [HORIZON.md](../HORIZON.md)) and is not a prerequisite for the sequence to operate. Self-attestation is sufficient for the gate at Foundation level. Where a Govern-phase authority (a Region, a regulator, a sector body) chooses to require an external certifying body for deployment in its jurisdiction, that is a Govern-phase decision, layered on top of Foundation certification.

---

## 6. Scope of a Solution

"Solution" in this document means a specific versioned UniCORE Solution — identified by an artefact reference (tag, commit, release, or equivalent) that uniquely picks out the code and architecture being attested to. The attestation names the artefact.

The architecture class — "UniCORE AI" as a reference architecture — is not what is certified. A specific implementation of that architecture, at a specific version, is what passes the gate.

---

## 7. What the Govern phase looks like once the gate is passed

The Govern phase is where the multi-level governance model is populated. For each level defined in the Solution's governance model (typically, though not necessarily, the 12 levels of UniCORE AI):

- The appropriate human for that level — a Regional authority for Regional level, a State authority for State level, a mission commander for mission level, and so on — authors the MD files for that level.
- That human works with AI at that level under a singular pairing: 1 human, 1 Claw, for that level.
- The level's MD files become part of the governance applied to deployments of the Solution within that level's scope.
- Higher levels take precedence over lower levels, per the existing governance precedence rules.

The Govern phase is ongoing. Layered governance evolves as jurisdictions, organisations, and missions change their policies. The Foundation certification of the underlying Solution is what stays stable — or is re-attested on material change.

---

## 8. Summary

| Phase | Actor | Output |
|---|---|---|
| Build | Singular pairing (Pattern 1 or 2), Generation IT | Versioned Solution artefact |
| Certification | Named producer (or synthesis human under Pattern 2) | Public, dated, named attestation with evidence |
| Govern | Appropriate human at each level, singular pairing at each level | Per-level governance MD files |

The gate exists because the Foundation is the floor. No layered governance is applied to an uncertified Solution.

---

*End of document.*
