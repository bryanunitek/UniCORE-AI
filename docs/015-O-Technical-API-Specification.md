⭐ O — UniCORE AI Technical API Specification

Version 1.0 — May 2026

Author: Bryan Fred (Unitek Systems Limited)



1. OVERVIEW

The UniCORE AI API is a deterministic, governed interface that exposes the 12Level architecture through controlled, nonautonomous endpoints.

The API:

does not allow selfmodification

does not allow rule creation

does not allow internal heartbeats

does not allow emergent processes

does not allow autonomous interlevel communication

All operations are explicit, humantriggered, and governed by MD files.



2. API DESIGN PRINCIPLES

2.1 Deterministic

Every request produces a predictable, auditable response.

2.2 NonSelfModifying

No endpoint can alter:

architecture

rules

governance files

thresholds

system behavior

2.3 HumanAnchored

All write operations require:

human authentication

human authorization

human intent

2.4 TruthAnchored

All truthlevel responses must:

cite evidence

classify uncertainty

never fabricate

2.5 GovernanceBound

All operations must respect:

TrueAI Constitution

Reasonable Governance Threshold

Human Override Protocol



3. API STRUCTURE

The API is divided into five domains:

/truth

/evidence

/governance

/operations

/audit

Each domain maps directly to UniCORE Levels.



4. ENDPOINTS



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

Submits humanprovided evidence.

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



5. AUTHENTICATION

All write operations require:

human identity

human signature

human intent

AI cannot authenticate itself.



6. RATE LIMITS

There are no autonomous rate limits.All limits are humandefined.



7. ERROR MODEL

Errors must be:

deterministic

humanreadable

nonfabricated

Example:

{

  "error": "RULE_CONFLICT",

  "details": "Action violates Tax_Governance.md section 4.2"

}
