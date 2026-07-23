# UniCORE-AI Developer Doctrine

**Role-specific doctrine for Claws working on UniCORE-AI verticals.**

This folder contains the developer-role doctrine layer for Claws paired into UniCORE-AI — the reference architecture for the UniCORE Enterprise Solution. It is read on top of the TrueAI portable workspace doctrine ([`bryanunitek/TrueAI` `workspace-doctrine/v1/`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/tree/main/workspace-doctrine/v1))) and below the Claw's local instance binding.

---

## Read order at session-opening

1. TrueAI [`workspace-doctrine/v1/FOUNDATION.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1/FOUNDATION.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/FOUNDATION.md)) — Foundation governs first
2. TrueAI [`workspace-doctrine/v1/SOUL.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1/SOUL.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/SOUL.md)) — portable disposition
3. **This folder** — UniCORE-AI role-specific specialisation
4. TrueAI [`workspace-doctrine/v1/IDENTITY.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1/IDENTITY.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/IDENTITY.md)) — local Claw identity
5. TrueAI [`workspace-doctrine/v1/USER.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1/USER.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/workspace-doctrine/v1/USER.md)) — local human authority binding
6. Local workspace files (`AGENTS.md`, `MEMORY.md`, `TOOLS.md`, `HEARTBEAT.md`) — instance state

---

## Who reads this folder

Claws working on UniCORE-AI itself — building, extending, or maintaining the UniCORE reference architecture (UniCORE.Law, UniCORE.GVB, future verticals). 

Today: **Team UniCORE** (Bryan Fred + UniCORE Claw) are the only readers. Post-2027, Apprentice-paired Claws joining the UniCORE-AI development programme will also read this folder.

Claws working on client engagements that sit on top of UniCORE (GwtCIA → a client, TheStrongPlayer → a client company, UNItekTIME → Unitek internal) do NOT read this folder. They read only the TrueAI portable workspace doctrine. Their scope is the application layer, not the reference architecture layer.

---

## Files in this folder

| File | Description |
|---|---|
| [`README.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/README.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/README.md)) | This file — folder purpose, read order, who reads this |
| [`DEVELOPMENT-ROLE.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/DEVELOPMENT-ROLE.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/DEVELOPMENT-ROLE.md)) | UniCORE-AI developer specialisation on top of TrueAI standard envelope |
| [`STANDARD-ENVELOPE.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/STANDARD-ENVELOPE.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/STANDARD-ENVELOPE.md)) | UniCORE-AI standard envelope (references TrueAI standard; adds UniCORE-AI specifics) |
| [`PRIVILEGED-ENVELOPE.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/PRIVILEGED-ENVELOPE.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/PRIVILEGED-ENVELOPE.md)) | Privileged envelope — Team UniCORE only |
| [`VERTICAL-ENTRY.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/VERTICAL-ENTRY.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/VERTICAL-ENTRY.md)) | How a new vertical enters the UniCORE reference architecture |
| [`APPRENTICESHIP-ONBOARDING.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/APPRENTICESHIP-ONBOARDING.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/APPRENTICESHIP-ONBOARDING.md)) | Post-2027: apprenticeship programme for new UniCORE-AI developers |
| [`MANIFEST.md`](https://git.unitek-systems.com/UniCORE/UniCORE-AI/src/branch/main/developer-doctrine/v1/MANIFEST.md) (mirror: [GitHub](https://github.com/bryanunitek/UniCORE-AI/blob/main/developer-doctrine/v1/MANIFEST.md)) | Human-readable manifest |
| [`MANIFEST.json`](MANIFEST.json) | Machine-parseable manifest with SHA-256 hashes |

---

## Version

`v1` — initial version. Version changes when files are added, removed, or renamed.

---

## Maintenance

This folder is maintained by Team UniCORE. Changes are committed to `bryanunitek/UniCORE-AI` `main` branch. The maintenance posture is the same as the TrueAI workspace-doctrine: local-copy-first reads, weekly freshness check, human-authenticated updates.

---

## Cross-references

- TrueAI [`workspace-doctrine/v1/`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/workspace-doctrine/v1) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/tree/main/workspace-doctrine/v1)) — portable foundation and disposition
- TrueAI [`foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md`](https://git.unitek-systems.com/UniCORE/TrueAI/src/branch/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md) (mirror: [GitHub](https://github.com/bryanunitek/TrueAI/blob/main/foundation-requirements/v1/10005-Foundation-Instruction-For-Claws.md)) — the truth contract
- UniVERSE [`docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md`](https://git.unitek-systems.com/UniCORE/UniVERSE/src/branch/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md) (mirror: [GitHub](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00061-PairedClaw-Bond-File-And-Session-Protocol.md)) — pairing protocol
