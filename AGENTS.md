# AGENTS.md — UniCORE-AI

**Read this first, every time, before touching this repo.**

---

## What this repo is

`bryanunitek/UniCORE-AI` — the 12-level governance architecture. The reference implementation of the TrueAI invariants. Truth-anchored, governance-bound, non-self-modifying, human-sovereign. Expressed as a 12-level vertical stack.

Sister repos:
- `bryanunitek/UniVERSE` — the civilisational programme, whitepapers, outreach
- `bryanunitek/TrueAI` — the immutable eight invariants (foundation for this repo)
- `bryanunitek/UniCORE-Claw` — the .NET/XAF codebase (product implementation, separate concern)

When Bryan says "UniCORE-AI" (with the hyphen), he means **this repo**, not the Claw build and not the general programme material. Implementation material about HOW to build a governed system goes here.

## Who pushes

**I push directly.** Commit and `git push origin main` on Bryan's behalf. No GitHub Desktop, no approval loop. Standing rule for UniVERSE, TrueAI, and UniCORE-AI.

## Branching

- **One branch: `main`.** No feature branches, no dev branches, no PRs. Direct commits.

## Commit style

- Author: `bryanunitek <bryan.fred@unitek-systems.com>` (use `--author=`).
- Message format: `<type>: <subject>` + blank + body. Types: `docs`, `architecture`, `governance`, `levels`, `chore`.

## The 12 levels (durable reference)

| Level | Name | Purpose |
|---|---|---|
| 1 | Truth | Factual status of claims |
| 2 | Evidence | Human-submitted supporting material |
| 3 | Verification | Cross-checking and consistency evaluation |
| 4 | Context | Jurisdictional, temporal, situational resolution |
| 5 | Interpretation | Meaning derived from evidence and context |
| 6 | Governance | Human-authored rules from MD files |
| 7 | Compliance | Legal, regulatory, mission rules |
| 8 | Operations | Governed decisions about allowed actions |
| 9 | Execution | Deterministic action-taking |
| 10 | Audit | Immutable, append-only logs |
| 11 | Stability | Drift detection and monitoring |
| 12 | Human Governance | Sovereign. Intentionally imperfect. Never overridden. |

**Truth flows upward 1→5. Control flows downward 12→6.** Do not invert without flagging it.

**Four-level floor:** any AI system with 4+ enforced governance levels qualifies as using the UniVERSE/TrueAI/UniCORE foundation, regardless of what the levels are named in that industry.

## Layout

| Path | Purpose |
|---|---|
| `README.md` | Architecture overview + level table + document index |
| `FULL_FORMAL_STATEMENT.md` | Canonical founding statement |
| `LICENSE.md` | CC BY 4.0 / gift licence |
| `OUTREACH.md` | Outreach index |
| `docs/` | Architecture, level specs, integration material, deployment guides |

This repo carries the implementation-shaped material: architecture diagrams, API specs, data models, deployment guides, compliance mappings. Invariants stay in TrueAI; civilisational-scale material stays in UniVERSE.

## Attribution rules (durable)

- Authorship / licence / legal entity: Unitek Systems Limited (UK)
- Hosting / SaaS / infra claims: Unitek Systems USA Inc
- Licence: CC BY 4.0, "given, not sold, irrevocable"
- Author byline: `Bryan Fred, Unitek Systems Limited`

## Contact rules (durable)

- **All public contact routes through GitHub Discussions on this repo:** https://github.com/bryanunitek/UniCORE-AI/discussions
- **Do not publish** Bryan's personal email (`bryan.fred@unitek-systems.com`, `bryan@unitek-systems.co.uk`), personal phone numbers, or the Unitek Systems generic inboxes (`info@`, `support@`, `services@`) in any file committed to this repo.
- Git commit author metadata is the one exception: use `bryanunitek <bryan.fred@unitek-systems.com>` for `--author=`. That address lives in git metadata, not in published prose.
- When writing a "Contact" section in any public document (README, LICENSE, architecture doc), use the Discussions URL only.

## Voice

- Engineering-precise. This is the "how" repo.
- Specify interfaces, inputs, outputs, constraints, invariants at each level.
- Avoid marketing language. Avoid speculation about levels above 12 or below 1.

## Do not

- Do not create branches, PRs, or dev workflow.
- Do not renumber or rename the 12 levels.
- Do not add a Level 0 or Level 13 without explicit go-ahead — the stack is defined.
- Do not put code here. Implementation code goes in UniCORE-Claw.
- Do not contradict the TrueAI invariants in UniCORE-AI material. If architecture appears to require violating one, stop and ask.

## After push

Tell Bryan the commit hash and the one-sentence change summary.
