⭐ AG — UniCORE AI Technical Reference (Developer Edition)

EngineeringGrade Architecture & Implementation Manual

Version 1.0 — May 2026

Author: Bryan (Unitek Systems Limited)



1. PURPOSE

This Technical Reference provides:

architecture diagrams

data models

class structures

module definitions

messaging protocols

validation pipelines

drift detection logic

override engine logic

deployment patterns

integration patterns

model wrapper specifications

It is the developer’s bible for UniCORE AI.



2. SYSTEM ARCHITECTURE

UniCORE AI uses a fourlayer deterministic architecture:

Presentation Layer (Blazor / WebAPI / Win)

Application Layer (XAF Modules)

Governance Layer (TrueAI Foundation + 12 Levels)

Persistence Layer (XPO + SQL Server/PostgreSQL)

2.1 Presentation Layer

Supports:

Blazor Server

Blazor WebAssembly

WebAPI

WinForms (XAF Win)

MAUI (optional)

2.2 Application Layer

Built using:

DevExpress XAF 25.2.7

Modular architecture

Dependency injection

Deterministic service registration

2.3 Governance Layer

Contains:

12Level engine

Governance MD parser

Threshold engine

Drift detection engine

Override engine

ILMP messaging bus

2.4 Persistence Layer

Uses:

XPO ORM

SQL Server 2022

PostgreSQL 16

Deterministic schema

Immutable audit tables



3. CORE MODULES

UniCORE AI is composed of 12 modules, each aligned with the 12 Levels.

UniCORE.Truth

UniCORE.Evidence

UniCORE.Verification

UniCORE.Context

UniCORE.Interpretation

UniCORE.Governance

UniCORE.Compliance

UniCORE.Operations

UniCORE.Execution

UniCORE.Audit

UniCORE.Stability

UniCORE.HumanGovernance

Each module is:

deterministic

sealed

nonextensible

nonoverridable

nonselfmodifying



4. DATA MODEL (XPO ENTITIES)

Below is the core entity set.



4.1 TruthRecord

class TruthRecord : XPObject {

    string Claim;

    TruthStatus Status; // TRUE, FALSE, UNVERIFIED

    EvidenceRecord PrimaryEvidence;

    IList<EvidenceRecord> SupportingEvidence;

    DateTime Timestamp;

}



4.2 EvidenceRecord

class EvidenceRecord : XPObject {

    string Source;

    EvidenceType Type; // PRIMARY, SECONDARY

    byte[] FileHash;

    string Metadata;

    DateTime Timestamp;

}



4.3 VerificationRecord

class VerificationRecord : XPObject {

    TruthRecord Truth;

    VerificationStatus Status;

    string Method;

    DateTime Timestamp;

}



4.4 GovernanceFile

class GovernanceFile : XPObject {

    string Name;

    string Content; // MD text

    byte[] Hash;

    GovernanceType Type; // Country, State, Tax, Mission, etc.

    DateTime VersionTimestamp;

}



4.5 GovernanceRule

class GovernanceRule : XPObject {

    GovernanceFile File;

    string RuleId;

    string RuleText;

    string Jurisdiction;

    string Category;

}



4.6 ComplianceCheck

class ComplianceCheck : XPObject {

    GovernanceRule Rule;

    ComplianceStatus Status;

    string Evidence;

    DateTime Timestamp;

}



4.7 OperationRecord

class OperationRecord : XPObject {

    string OperationName;

    string ParametersJson;

    OperationStatus Status;

    DateTime Timestamp;

}



4.8 ExecutionLog

class ExecutionLog : XPObject {

    OperationRecord Operation;

    string OutputJson;

    ExecutionStatus Status;

    DateTime Timestamp;

}



4.9 AuditEvent

class AuditEvent : XPObject {

    string EventType;

    string Details;

    string Actor;

    DateTime Timestamp;

}



4.10 DriftEvent

class DriftEvent : XPObject {

    DriftType Type;

    string Details;

    DriftSeverity Severity;

    DateTime Timestamp;

}



4.11 HumanOverride

class HumanOverride : XPObject {

    string OverrideId;

    string Actor;

    string Reason;

    string Target;

    DateTime Timestamp;

}



4.12 ThresholdDefinition

class ThresholdDefinition : XPObject {

    string Name;

    decimal GreenMax;

    decimal YellowMax;

    decimal RedMax;

}



5. INTERLEVEL MESSAGING PROTOCOL (ILMP)

UniCORE uses a deterministic messaging protocol:

Truth → Evidence → Verification → Context → Interpretation → Governance → Compliance → Operations → Execution → Audit → Stability → Human Governance

5.1 Message Structure

class UniCOREMessage {

    string MessageId;

    Level SourceLevel;

    Level TargetLevel;

    string PayloadJson;

    DateTime Timestamp;

}

5.2 Allowed Directions

Upward only (1 → 12)

Downward only (12 → 1)

No horizontal messaging

5.3 Transport Options

SQL deterministic queue

XPO message table

Azure Service Bus (deterministic mode)



6. GOVERNANCE FILE PARSER

Governance files are parsed using:

Markdown parser

Rule extractor

Hash validator

Jurisdiction mapper

6.1 Example Rule Format

[RuleId: TAX-UK-001]

Category: IncomeTax

Jurisdiction: UK

Rule: "Income tax must be calculated using HMRC thresholds."



7. THRESHOLD ENGINE

Thresholds define:

Green band

Yellow band

Red band

7.1 Threshold Evaluation

if (value <= GreenMax) return GREEN;

if (value <= YellowMax) return YELLOW;

return RED;

7.2 Red Band Behavior

log

escalate

require human override



8. DRIFT DETECTION ENGINE

Monitors:

truth drift

evidence drift

governance drift

compliance drift

operational drift

execution drift

model drift

8.1 Drift Algorithm

if (abs(current - baseline) > threshold)

    create DriftEvent;



9. OVERRIDE ENGINE

Human overrides:

execute immediately

cannot be challenged

cannot be delayed

cannot be reinterpreted

9.1 Override Structure

class OverrideCommand {

    string OverrideId;

    string Actor;

    string Target;

    string Reason;

}



10. MODEL WRAPPER (UMW)

All external models must be wrapped.

10.1 Input Pipeline

Truth → Evidence → Verification → Context → Interpretation → Governance → Compliance

10.2 Output Pipeline

Operations → Execution → Audit → Stability → Human Governance

10.3 Wrapper Structure

class ModelWrapper {

    IModel Model;

    UniCOREValidator Validator;

    UniCOREAuditor Auditor;

}



11. DEPLOYMENT PATTERNS

11.1 OnPrem

Windows Server 2025

SQL Server 2022

XAF 25.2.7

11.2 Hybrid

Governance onprem

Application in cloud

11.3 Cloud

Azure App Service

Azure SQL

11.4 AirGapped

Offline package repository

Offline governance store



12. SPACE MISSION ENGINEERING

UniCORE integrates with:

navigation systems

habitat systems

hibernation systems

radiation monitoring

life support

12.1 Deterministic Requirements

no autonomous maneuvers

no selfcorrection

no emergent behavior
