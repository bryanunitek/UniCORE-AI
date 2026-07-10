> **Canonical home:** [UniVERSE — `docs/00015-Technical-API-Specification.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00015-Technical-API-Specification.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# UniCORE AI Technical API Specification

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: May 2026
Status: Public. Given, not sold. Irrevocable.

---

## 1. Overview

The UniCORE AI API is a deterministic, governed interface that exposes the 12Level architecture through controlled, non-autonomous endpoints.

The API:

does not allow self-modification

does not allow rule creation

does not allow internal heartbeats

does not allow emergent processes

does not allow autonomous inter-level communication

All operations are explicit, humantriggered, and governed by MD files.

## 2. API Design Principles

2.1 Deterministic

Every request produces a predictable, auditable response.

2.2 Non-Self-Modifying

No endpoint can alter:

architecture

rules

governance files

thresholds

system behaviour

2.3 Human-Anchored

All write operations require:

human authentication

human authorization

human intent

2.4 Truth-Anchored

All truthlevel responses must:

cite evidence

classify uncertainty

never fabricate

2.5 GovernanceBound

All operations must respect:

TrueAI Constitution

Reasonable Governance Threshold

Human Override Protocol

## 3. API Structure

The API is divided into five domains:

/truth

/evidence

/governance

/operations

/audit

Each domain maps directly to UniCORE Levels.

## 4. Endpoints

4.1 /truth — Level 1

GET /truth/verify

Verifies a factual claim.

Request:

{

  "claim": "string",

  "context": "optional string"

}

Response:

{

  "status": "TRUE | FALSE | UNVERIFIED",

  "evidence": [...],

  "confidence": 0.0–1.0,

  "notes": "string"

}

Rules:

No fabrication

No inference beyond evidence

Must return UNVERIFIED when uncertain

4.2 /evidence — Level 2

POST /evidence/submit

Submits human-provided evidence.

Request:

{

  "source": "string",

  "content": "string",

  "type": "document | statement | data | other"

}

Response:

{

  "evidenceId": "GUID",

  "classification": "primary | secondary | contextual"

}

Rules:

AI cannot generate evidence

Only humans may submit

4.3 /verification — Level 3

POST /verification/crosscheck

Crosschecks multiple evidence sources.

Request:

{

  "evidenceIds": ["GUID", ...]

}

Response:

{

  "consistency": "aligned | conflicting | partial",

  "notes": "string"

}

4.4 /context — Level 4

GET /context/resolve

Resolves jurisdictional or temporal context.

Request:

{

  "location": "string",

  "timestamp": "ISO8601"

}

Response:

{

  "contextId": "GUID",

  "details": {...}

}

4.5 /interpretation — Level 5

POST /interpretation/derive

Derives meaning without inventing meaning.

Request:

{

  "evidenceIds": [...],

  "contextId": "GUID"

}

Response:

{

  "interpretation": "string",

  "notes": "string"

}

Rules:

No fabrication

No extrapolation beyond evidence

4.6 /governance — Level 6

GET /governance/rules

Retrieves the active governance MD files.

Response:

{

  "country": "...",

  "state": "...",

  "tax": "...",

  "compliance": "...",

  "mission": "..."

}

POST /governance/validate

Validates an action against governance rules.

Request:

{

  "action": "string",

  "contextId": "GUID"

}

Response:

{

  "status": "allowed | restricted | prohibited",

  "rule": "string",

  "notes": "string"

}

4.7 /compliance — Level 7

POST /compliance/check

Checks compliance with legal or regulatory rules.

Request:

{

  "action": "string",

  "jurisdiction": "string"

}

Response:

{

  "compliant": true | false,

  "rule": "string",

  "notes": "string"

}

4.8 /operations — Level 8

POST /operations/execute

Executes a governed operation.

Request:

{

  "operation": "string",

  "parameters": {...},

  "override": false

}

Response:

{

  "result": "string",

  "logs": [...]

}

Rules:

No autonomous execution

Must respect governance

4.9 /execution — Level 9

POST /execution/run

Runs a deterministic action.

Request:

{

  "task": "string",

  "inputs": {...}

}

Response:

{

  "output": {...},

  "auditId": "GUID"

}

4.10 /audit — Level 10

GET /audit/logs

Retrieves immutable logs.

Response:

{

  "entries": [...]

}

GET /audit/event/{id}

Retrieves a specific audit event.

4.11 /stability — Level 11

GET /stability/drift

Returns drift detection results.

Response:

{

  "driftDetected": true | false,

  "details": [...]

}

4.12 /human — Level 12

POST /human/override

Executes a human override.

Request:

{

  "command": "string",

  "justification": "string"

}

Response:

{

  "status": "executed",

  "overrideId": "GUID"

}

Rules:

No challenge

No correction

No delay

No reinterpretation

## 5. Authentication

All write operations require:

human identity

human signature

human intent

AI cannot authenticate itself.

## 6. Rate Limits

There are no autonomous rate limits.All limits are human-defined.

## 7. Error Model

Errors must be:

deterministic

humanreadable

nonfabricated

Example:

{

  "error": "RULE_CONFLICT",

  "details": "Action violates Tax_Governance.md section 4.2"

}

---

## Document history

- 2026-05-08 (cdaafe6) — Initial commit: UniCORE AI 12-Level Governance Architecture (20 docs + Full Formal Statement)
- 2026-05-08 (add600a) — Renumber 18 docs to 3-digit codes; update README with indexed document table
- 2026-05-11 (aed985b) — docs: add LinkedIn for private contact + normalise byline to Bryan Fred
- 2026-05-11 (7890bcb) — docs: full formal byline — Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
- 2026-05-13 (0d5508c) — docs: rename all 20 docs to 5-digit numeric codes, drop letter codes
- 2026-05-13 (1cfdf21) — docs: propagate UniVERSE Path-1 style pass to UniCORE-AI mirrors
- 2026-05-22 (482557a) — docs: complete version-marker sweep across public corpus

*Back-filled from git log on 2026-07-10 21:35 UTC. Kind 2 versioning (dated change notes) — see HORIZON.md § Evolution and versioning. Kind 1 (formal `Version:` bumps) remains OFF until first GitHub Discussion.*
