# Levels — Per-Level Corpus For UniCORE AI

**The markdown content that defines what each Level in the UniCORE AI 12-level governance model is, plus the User scope.**

This folder holds the per-Level material that Solutions deliver to paired Claws at session-opening time. The 12-level governance model is a UniCORE AI (L2) concept, not a programme-wide (L1) or Solution-specific (L3) concept; this folder is the canonical home for the Level definitions.

The pairing protocol that consumes this content is specified in [UniVERSE 00061](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md). A bond file (written by UNICOREMASTER) names a Level and, by implication, the folder under `levels/<version>/<level-or-user>/` that the paired Claw is to be oriented against.

---

## Versioning

Each subfolder of `levels/` (`v1/`, `v2/`, ...) is a **frozen version** of the per-Level corpus. UniCORE AI evolves by adding new versioned subfolders, not by editing existing ones. A Solution is built against a specific version of `levels/`; the version is part of the Solution's deployment identity.

- **`v1/`** is the first canonical version, published 2026-05-16.
- A Solution's local deployment carries the `levels/v1/` content (or the subset matching its provisioned Levels) embedded as the Solution's pinned Level corpus.
- When the per-Level corpus refines, a new `v2/` subfolder is added alongside `v1/`. Previous versions remain readable.
- Pairing-time version drift between a Solution and the canonical head is surfaced to UNICOREMASTER per the failure ladder in [UniVERSE 00062](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00062-Pairing-Failure-Ladder-Pause-Mode-And-EMERGENCY.md).

This matches the same versioning discipline used by [TrueAI/foundation-requirements/](https://github.com/bryanunitek/TrueAI/tree/main/foundation-requirements) and [UniVERSE/programme-corpus/](https://github.com/bryanunitek/UniVERSE/tree/main/programme-corpus).

---

## What is in each Level folder

Each Level folder (`level-01/` through `level-12/`, plus `user/`) holds the markdown files that define **what an agent operating at that Level is**. The discipline is **no more and no less than what makes that Level what it is meant to be** — content that applies to every Level belongs in cross-Level material referenced from inside each Level's folder, not duplicated.

Today these folders are **structural placeholders**. They will be populated as the per-Level definitions are written. Each folder contains a `README.md` seeding the folder; substantive per-Level content lands in subsequent commits.

---

## Document history

- 2026-05-16 (f70ee01) — levels/v1: per-Level corpus structure; mirror 00061+00062 from UniVERSE

*Back-filled from git log on 2026-07-10 21:35 UTC. Kind 2 versioning (dated change notes) — see HORIZON.md § Evolution and versioning. Kind 1 (formal `Version:` bumps) remains OFF until first GitHub Discussion.*
