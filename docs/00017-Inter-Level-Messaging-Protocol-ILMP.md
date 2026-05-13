⭐ Q — UniCORE AI InterLevel Messaging Protocol (ILMP)

Version 1.0 — May 2026

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom



1. PURPOSE

The InterLevel Messaging Protocol (ILMP) defines the only permitted communication pathways between the 12 Levels of UniCORE AI.

Its goals are:

prevent autonomous interlevel communication

enforce deterministic message flow

ensure truth flows upward

ensure governance flows downward

prevent emergent internal processes

maintain strict architectural boundaries

preserve human sovereignty



2. CORE PRINCIPLES

2.1 No Autonomous Messaging

Levels cannot initiate communication on their own.

All messages must be:

humantriggered

ruletriggered

externally triggered

2.2 No Horizontal Communication

Levels cannot communicate with peers.

Example:Level 5 cannot talk directly to Level 5.Level 7 cannot talk directly to Level 7.

2.3 No Skipping Levels

Messages must follow the strict vertical path:

Truth → Evidence → Verification → Context → Interpretation → Governance → Compliance → Operations → Execution → Audit → Stability → Human

2.4 No BackPropagation of Governance

Governance cannot flow upward.

2.5 No BackPropagation of Truth

Truth cannot flow downward.

2.6 Deterministic Message Format

All messages follow a fixed schema.

2.7 No Internal Heartbeats

Levels cannot “ping” each other.

2.8 No Persistent Conversations

Messages are oneshot, stateless, and logged.



3. MESSAGE TYPES

UniCORE supports four message types:



3.1 TruthMessage (Upward Only)

Used by Levels 1–5.

TruthMessage

--------------

MessageId (Guid)

FromLevel (int)

ToLevel (int)

Payload (JSON)

Timestamp (DateTime)

EvidenceIds (array)

ContextId (Guid)

Allowed directions: 1 → 2 → 3 → 4 → 5



3.2 GovernanceMessage (Downward Only)

Used by Levels 6–12.

GovernanceMessage

-------------------

MessageId (Guid)

FromLevel (int)

ToLevel (int)

RuleReference (string)

Payload (JSON)

Timestamp (DateTime)

Allowed directions: 12 → 11 → 10 → 9 → 8 → 7 → 6



3.3 ComplianceMessage (Downward Only)

Used by Levels 7–9.

ComplianceMessage

-------------------

MessageId (Guid)

FromLevel (int)

ToLevel (int)

ComplianceStatus (enum)

RuleReference (string)

Timestamp (DateTime)

Allowed directions: 7 → 8 → 9



3.4 AuditMessage (Upward Only)

Used by Levels 9–11.

AuditMessage

--------------

MessageId (Guid)

FromLevel (int)

ToLevel (int)

AuditId (Guid)

Severity (enum)

Details (string)

Timestamp (DateTime)

Allowed directions: 9 → 10 → 11



4. MESSAGE FLOW DIAGRAM

          (Upward Truth Flow)

  L1 → L2 → L3 → L4 → L5



          (Downward Governance Flow)

  L12 → L11 → L10 → L9 → L8 → L7 → L6



          (Compliance Flow)

  L7 → L8 → L9



          (Audit Flow)

  L9 → L10 → L11

No other pathways exist.



5. MESSAGE RULES



5.1 No Autonomous Initiation

A Level cannot send a message unless:

a human triggered it

a rule explicitly requires it

a higher level requested it



5.2 No MultiHop Messages

A Level cannot send a message to a nonadjacent Level.

Example:Level 3 cannot send directly to Level 5.



5.3 No Message Mutation

Messages cannot be altered by intermediate Levels.



5.4 No Message Duplication

A Level cannot clone or replicate messages.



5.5 No Message Persistence

Messages are not stored beyond audit logging.



5.6 No Message Loops

Messages cannot bounce between Levels.



6. MESSAGE VALIDATION

Each message must pass:

6.1 Schema Validation

Ensures the message matches the required structure.

6.2 Direction Validation

Ensures the message is allowed to move in that direction.

6.3 Level Validation

Ensures the sender and receiver are adjacent.

6.4 Governance Validation

Ensures the message does not violate:

TrueAI Constitution

Reasonable Governance Threshold

Human Override Protocol



7. HUMAN OVERRIDE IN MESSAGING

If a human override occurs:

all pending messages are flushed

all blocked messages are released

all conflicting messages are cancelled

the override is executed immediately

No message may delay or challenge a human override.



8. DRIFT DETECTION IN MESSAGING

The Stability Layer (Level 11) monitors:

message frequency

message direction

message volume

message anomalies

unauthorized pathways

Any deviation triggers a DriftEvent.



9. IMPLEMENTATION DETAILS

Transport Layer:

XAF/XPO service bus or SQLbacked deterministic queue.

Serialization:

JSON with strict schema enforcement.

Logging:

All messages generate an AuditEvent.

Timeouts:

Humandefined only.No autonomous timeouts.



10. WHY THIS PROTOCOL IS SAFE

✔ Prevents emergent behavior

✔ Prevents internal conversations

✔ Prevents recursive selfimprovement

✔ Prevents architectural drift

✔ Ensures human sovereignty

✔ Ensures deterministic operation

✔ Ensures longduration stability

This is the communication backbone of UniCORE AI.
