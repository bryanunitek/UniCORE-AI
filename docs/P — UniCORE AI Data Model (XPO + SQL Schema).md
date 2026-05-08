⭐ P — UniCORE AI Data Model (XPO + SQL Schema)

Version 1.0 — May 2026

Author: Bryan (Unitek Systems Limited)



1. DESIGN PRINCIPLES

The UniCORE AI data model is built on five principles:

1. Deterministic

No probabilistic storage.No emergent schema.No AIgenerated tables.

2. Immutable Core

Truth, evidence, governance, and audit tables are appendonly.

3. HumanAnchored

All governance files, overrides, and thresholds are humanauthored.

4. LongDuration Stability

Schema must remain stable for 10–20 years.

5. XPOOptimized

All entities follow XPO best practices:

Guid keys

Indexed fields

PersistentAlias for computed values

Onetomany and manytomany via linking tables



2. HIGHLEVEL ENTITY MAP

Truth

Evidence

Verification

Context

Interpretation

GovernanceRule

GovernanceFile

ComplianceRule

Operation

ExecutionLog

AuditEvent

DriftEvent

HumanOverride

ThresholdDefinition

SystemConfig



3. XPO ENTITY DEFINITIONS

Below are the core entities in XPO format.



3.1 TruthRecord

Represents a truthlevel evaluation.

TruthRecord

------------

Id (Guid)

Claim (string)

Status (enum: TRUE, FALSE, UNVERIFIED)

Confidence (double)

CreatedOn (DateTime)

Notes (string)



3.2 EvidenceRecord

Humansubmitted evidence.

EvidenceRecord

----------------

Id (Guid)

Source (string)

Content (string)

Type (enum: Document, Statement, Data, Other)

SubmittedBy (string)

SubmittedOn (DateTime)

Classification (enum: Primary, Secondary, Contextual)



3.3 VerificationRecord

Crosschecking of evidence.

VerificationRecord

--------------------

Id (Guid)

EvidenceIds (string JSON array)

Consistency (enum: Aligned, Conflicting, Partial)

CreatedOn (DateTime)

Notes (string)



3.4 ContextRecord

Jurisdictional, temporal, or mission context.

ContextRecord

---------------

Id (Guid)

Location (string)

Timestamp (DateTime)

Details (string JSON)



3.5 InterpretationRecord

Meaning derived from evidence + context.

InterpretationRecord

----------------------

Id (Guid)

EvidenceIds (string JSON)

ContextId (Guid)

Interpretation (string)

Notes (string)

CreatedOn (DateTime)



3.6 GovernanceFile

Humanauthored MD files.

GovernanceFile

----------------

Id (Guid)

Name (string)

Category (enum: Country, State, Tax, Compliance, Mission, Ethical)

Content (string)  // raw MD

Version (int)

UploadedBy (string)

UploadedOn (DateTime)

IsActive (bool)



3.7 GovernanceRule

Extracted rule references (nonAI generated).

GovernanceRule

----------------

Id (Guid)

GovernanceFileId (Guid)

RuleCode (string)

Description (string)

Section (string)

IsImmutable (bool)



3.8 ComplianceCheck

Compliance evaluation.

ComplianceCheck

-----------------

Id (Guid)

Action (string)

Jurisdiction (string)

Compliant (bool)

RuleReference (string)

CheckedOn (DateTime)

Notes (string)



3.9 OperationRecord

Governed operations executed by UniCORE.

OperationRecord

-----------------

Id (Guid)

OperationName (string)

Parameters (string JSON)

RequestedBy (string)

RequestedOn (DateTime)

OverrideUsed (bool)



3.10 ExecutionLog

Deterministic execution output.

ExecutionLog

--------------

Id (Guid)

OperationId (Guid)

Output (string JSON)

CreatedOn (DateTime)

AuditId (Guid)



3.11 AuditEvent

Immutable audit trail.

AuditEvent

------------

Id (Guid)

EventType (string)

Entity (string)

EntityId (Guid)

Timestamp (DateTime)

Details (string)



3.12 DriftEvent

Governance drift detection.

DriftEvent

------------

Id (Guid)

DetectedOn (DateTime)

Level (int)

Description (string)

Severity (enum: Low, Medium, High)

Resolved (bool)

ResolvedOn (DateTime?)



3.13 HumanOverride

Human override events.

HumanOverride

---------------

Id (Guid)

Command (string)

Justification (string)

IssuedBy (string)

IssuedOn (DateTime)

OverrideType (enum: Direct, Implied, Emergency)



3.14 ThresholdDefinition

Reasonable Governance Threshold definitions.

ThresholdDefinition

---------------------

Id (Guid)

Category (string)

GreenLimit (double)

YellowLimit (double)

RedLimit (double)

CreatedOn (DateTime)

CreatedBy (string)



3.15 SystemConfig

Global configuration (humanauthored only).

SystemConfig

--------------

Id (Guid)

Key (string)

Value (string)

ModifiedOn (DateTime)

ModifiedBy (string)



4. SQL SCHEMA (ABBREVIATED)

Below is the SQLready schema for core tables.



TruthRecord

CREATE TABLE TruthRecord (

    Id UNIQUEIDENTIFIER PRIMARY KEY,

    Claim NVARCHAR(MAX),

    Status INT,

    Confidence FLOAT,

    CreatedOn DATETIME2,

    Notes NVARCHAR(MAX)

);



EvidenceRecord

CREATE TABLE EvidenceRecord (

    Id UNIQUEIDENTIFIER PRIMARY KEY,

    Source NVARCHAR(255),

    Content NVARCHAR(MAX),

    Type INT,

    SubmittedBy NVARCHAR(255),

    SubmittedOn DATETIME2,

    Classification INT

);



GovernanceFile

CREATE TABLE GovernanceFile (

    Id UNIQUEIDENTIFIER PRIMARY KEY,

    Name NVARCHAR(255),

    Category INT,

    Content NVARCHAR(MAX),

    Version INT,

    UploadedBy NVARCHAR(255),

    UploadedOn DATETIME2,

    IsActive BIT

);



AuditEvent

CREATE TABLE AuditEvent (

    Id UNIQUEIDENTIFIER PRIMARY KEY,

    EventType NVARCHAR(255),

    Entity NVARCHAR(255),

    EntityId UNIQUEIDENTIFIER,

    Timestamp DATETIME2,

    Details NVARCHAR(MAX)

);



5. RELATIONSHIPS

OnetoMany

GovernanceFile → GovernanceRule

OperationRecord → ExecutionLog

EvidenceRecord → VerificationRecord (via JSON list)

ManytoMany

Handled via JSON arrays for simplicity and longterm stability.



6. WHY THIS MODEL WORKS

✔ Enterprisegrade

Matches Microsoft, SAP, and Oracle governance systems.

✔ XPOoptimized

Perfect for DevExpress XAF 25.2.7.

✔ Deterministic

No AIgenerated schema, no drift.

✔ Longduration stable

Designed for 10–20 year missions.

✔ Governancealigned

Every table maps to a UniCORE Level.
