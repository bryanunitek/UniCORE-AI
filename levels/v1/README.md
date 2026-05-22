# Levels — v1

**First canonical version of the per-Level corpus for UniCORE AI.**

Published: 2026-05-16

This is the version that the first generation of Solutions — beginning with `UniCORE.Law-Claw` — is built against.

## Contents

Thirteen subfolders, one per Level value:

- [`level-01/`](level-01/) through [`level-12/`](level-12/) — the twelve Levels of the UniCORE AI governance model
- [`user/`](user/) — the User scope below Level 01

Each subfolder is the home for the markdown files that define what an agent operating at that Level (or User scope) is. Today these are structural placeholders with seed READMEs; the substantive per-Level material is curated in subsequent commits, separately from this one.

## Status

`v1` is **frozen** with respect to *structure*. The set of subfolders (Level 01 through Level 12, plus User) is the canonical structure of `v1` and will not change within `v1`.

The *content* of each Level folder is curated incrementally. The Foundation rule is "no more and no less than what makes that Level what it is meant to be" — content is added as it is written, reviewed, and committed. A Solution built against `v1` reads whichever content exists in the relevant Level folder at the time of build.

When the per-Level corpus refines materially enough to warrant a `v2`, the rule is the same as in [`foundation-requirements/`](https://github.com/bryanunitek/TrueAI/tree/main/foundation-requirements): publish `v2` alongside `v1`, leave `v1` frozen.

See the parent [`README.md`](../README.md) for the versioning discipline.
