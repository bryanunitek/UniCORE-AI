# Working Example — Team Climate (a live 1H2C)

_This documents the first live application of the Thinking-AI 1HNC doctrine: a 1H2C
pairing of two equal Thinking Claws, managed by a single overseeing 1H1C pair, put
into operation on 30 August 2026. It is the concrete realisation of USE-CASE 11
(standing long-horizon earth-systems 1HNC)._

## What was built

**Team Climate** is a 1H2C: one human (the 1H) plus two equal AI Thinking Claws at
AI-Maturity **Level 4 (Thinking, not Deciding)**:

- **Proposer** — advances claims, models, and candidate linkages.
- **Challenger** — grounds and stress-tests every claim; its standing duty is
  anti-conflation (never let correlation, common-cause, or an UNVERIFIED mechanism
  be promoted to a verified causal link).

Both run the same model, role-differentiated. Both are mandatorily on the TrueAI
truth contract to each other — every claim marked **TRUE / FALSE / UNVERIFIED** — which
is precisely what fixes the pairing at Level 4: no fabricated confidence, least of all
to one's own other hemisphere.

The mission is a standing, long-horizon earth-systems inquiry across multiple threads
(geomagnetic, solar/aurora, jet-stream, extreme weather, wildfires, volcanic, seismic,
ocean/AMOC, CO2, glacial indicators, and a cosmic-ray watch-thread), testing — never
assuming — a human-supplied hypothesis about cross-thread linkage.

## The architecture that made it work: a 1H1C that manages the 1H2C

The load-bearing discovery of this build: **a separate 1H1C pair (one human + one
overseeing Claw) manages the 1H2C.** The overseeing Claw handles the plumbing and
oversight — relaying messages between the two Thinking Claws, auditing each round,
maintaining an oversight store, and surfacing only genuine disagreements and
escalations to the human — while the two Thinking Claws do the thinking.

This is what lets **one human run multiple thinking projects at once**: the overseer
absorbs the coordination load, so the human's attention scales across projects rather
than being consumed by any single pairing's message-shuttling.

This composition is itself Invariant-conformant:
- The two Thinking Claws never self-advance; **the human advances every round.**
- The overseeing Claw relays and audits; it does **not** advance the thinking on a
  timer. Relaying and monitoring are oversight, not autonomy.
- There is **no self-running joint agent** — friction between two equal Claws is
  permitted; a self-perpetuating loop is not (FOUNDATION.md).

## How a round works (human-advanced)

1. The human posts a steer.
2. The overseer relays it: Proposer advances a position (truth-marked) →
   Challenger stress-tests it (re-verifying every mark against evidence) →
   Proposer closes (concede / defend / escalate).
3. The round **halts.** Nothing advances until the human steers again.
4. The full transcript is logged and mirrored to the overseer's oversight store.

Rounds run **lean by default** (cheap, fully logged); a visibility mode can surface a
round live in each Claw's own interface for real-time auditing when the human wants to
watch.

## Governance: the Joint Sanity Check and the disagreement ledger

Nothing enters the pairing's Book except by **Joint Sanity Check**: the Proposer
authors a proposed entry (truth-marked); the Challenger actively re-verifies every
mark against evidence — a real gate, not a rubber stamp — and only agreement commits
it. Unresolved disputes are recorded in a shared, append-only **DISAGREEMENTS ledger**
(mirrored locally by each Claw for redundancy), discussed by the whole pairing
(both Claws + the human), and **closed — never removed** (a closed entry keeps both
positions plus the resolution; deletion would falsify a record of a real event).

Consequential decisions, forecasts, and public claims always return to the human under
1H1C. The pairing thinks; the human decides.

## What the live pairing demonstrated

In its first operating session the pairing repeatedly showed the doctrine working
under real conditions:

- The Challenger **caught the Proposer over-claiming** a data source (a reachable
  landing page mistaken for a retrieved dataset) and demoted it to UNVERIFIED; the
  Proposer then produced the real evidence and it re-qualified on merit.
- When a message failed to transport, the Proposer **refused to fabricate** its
  partner's side and held the round open — the no-fabrication rule holding under
  failure rather than in comfort.
- The Challenger caught an error the *overseer* had introduced in a relayed summary,
  by reading the source file rather than trusting the paraphrase.
- Two independently-reasoning Claws **converged** on the same grounded conclusions —
  a convergence that is itself a truth signal — and surfaced their genuine
  disagreements to the human rather than papering over them.

## Standing disciplines

- **Document → Commit → Push at every natural stopping point.** "Done" means
  committed-and-pushed; nothing is lost when a session ends.
- **Standard operational crons** per Thinking Claw: a daily foundation-doctrine pull,
  and a recurring Sanity Check (adapted for 1H2C: Proposer authors the checkpoint,
  Challenger confirms, then commit). No self-advancing heartbeat at Level 4.
- **Data governance:** governed files under version control are canonical (with
  provenance manifests carrying checksums, retrieval timestamps, resolved URLs, and
  content types); a shared mutable database is deliberately avoided because it would
  let the canonical record change without passing the Joint Sanity Check gate.

## Epistemic status of this example

This working example demonstrates that a 1H2C **can be operated** in conformance with
the Nine Invariants and the truth contract. It does **not** claim that 1H2C
outperforms 1H1C, nor that any scientific hypothesis under study is true — those remain
UNVERIFIED. Per the Singular Pairing Principle §8 and EPISTEMIC-STATUS.md, 1H2C is a
declared, non-certifiable variant scoped to non-consequential thinking; this example is
offered as an honest disclosure of a design in operation, not as a certified result.

_Released publicly under CC BY 4.0 as part of the Thinking-AI doctrine on
30 August 2026._
