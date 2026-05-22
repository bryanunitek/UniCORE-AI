> **Canonical home:** [UniVERSE — `docs/00060-Supported-AI-Provider-List.md`](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00060-Supported-AI-Provider-List.md)
> This file is a mirror kept here for in-repo reading. Source of truth is the link above.

# Supported AI Provider List

**Programme reference: which AI provider families may power a Claw**

Author: Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
First published: May 2026
Status: Public. Given, not sold. Irrevocable.

---

## 1. Purpose

This document is the programme-wide list of AI provider families
whose models may power a **Claw** as defined in
[00058 §2.1](00058-Claw.md#21-claw). The list applies uniformly to:

- a **MyClaw** ([00058 §2.3](00058-Claw.md#23-externalclaw)) — a
  person's own ExternalClaw, run on their own infrastructure or via
  a managed hosting platform such as
  [myclaw.ai](https://myclaw.ai),
- an **AgentClaw** ([00058 §2.3](00058-Claw.md#23-externalclaw)) —
  an autonomous AI-driven ExternalClaw with no human owner,
- a Claw on the Solution side of a **PairedClaw** bond
  ([00058 §2.4](00058-Claw.md#24-pairedclaw)) inside any
  `UniCORE-<vertical>-Claw` Solution
  (for example,
  [UniCORE.Law-Claw](https://github.com/bryanunitek/UniCORE.Law-Claw)
  for the Law sector).

The provider is the substrate; the Claw is the governed interface
that sits between a human and that substrate. Substrate-agnostic
governance ([00058 §4.1](00058-Claw.md#41-substrate-agnostic-governance))
means the same governance rules hold across every provider on this
list. A Claw running on one provider today and a different provider
tomorrow remains the same Claw under Foundation governance; the
audit trail, the corpus, the principal identity, the certification
mark, and the attribution couplet all sit outside the substrate.

This document does not endorse any provider over any other. It
records which providers meet the inclusion criteria below. Tenants
choose which providers their Claws use; the programme does not
choose for them.

---

## 2. Inclusion criteria

For an AI provider family to appear on this list, it must satisfy
all four of the following:

1. **A long-lived account.** A tenant (an individual, a firm, a
   research group, a sovereign body) must be able to hold an
   account or contract with the provider that persists across
   sessions and across Claw lifecycles.
2. **A chat or completions endpoint suitable for an agent loop.**
   The provider must expose an API shape that can sustain
   multi-turn interaction, not only single-shot inference.
3. **Function or tool calling.** The provider's API must allow a
   Claw to invoke tools the host exposes (read records, run
   actions, call back into the Solution). Without this, the Claw
   cannot operate as a governed channel; it can only emit text.
4. **At least one model strong enough to act as a
   Foundation-aligned agent.** The provider must offer at least
   one production model with reasoning, tool-use, and instruction-
   following sufficient to honour Foundation governance under the
   nine invariants.

Providers that ship only image generation, only embeddings, or
only voice are out of scope for this list. They may serve a Claw
as utility models, but they cannot power the Claw itself.

A provider's inclusion on this list is independent of where it is
hosted, who owns it, and what jurisdiction it operates from. The
programme does not gate the list on geopolitics; tenants gate their
own use of any provider based on their own contractual,
regulatory, and data-residency posture.

---

## 3. The supported families

The list below is current as of the document's first publication.
The set of AI provider families that meet the inclusion criteria
will evolve. New entrants will be added, current entrants may be
removed if they no longer meet the criteria, and renames within
families are tracked in the git history of this document.

### 3.1 Anthropic

Models: Claude Opus, Claude Sonnet, Claude Haiku families.
Native function calling. Strong instruction-following. The
programme's reference development instance for new Claw work runs
on Anthropic. Anthropic is one provider among many; this is a
development convenience, not an endorsement.

### 3.2 OpenAI

Models: GPT family, o-series reasoning family.
Native function calling. The largest installed base of API
consumers; most tenants will already hold an OpenAI account.

### 3.3 Google (Gemini API, Vertex AI)

Models: Gemini family across multiple sizes.
Native function calling. Two routes: Gemini API direct, and Vertex
AI for enterprise deployments with their own contractual posture.

### 3.4 Microsoft (Azure OpenAI)

Models: OpenAI's family, hosted in Azure with Microsoft's
enterprise SLA and data-residency commitments.
Native function calling. Particularly relevant to regulated
verticals where data-residency contracts mandate Azure-hosted
inference (legal, financial, healthcare, public sector).

### 3.5 Amazon (Bedrock)

Models: a multi-model gateway covering several provider families,
including Anthropic, Meta (Llama), Mistral, and Amazon's own
Titan family.
Native function calling. The default route for AWS-native
tenants and for tenants who want a single AWS-side audit and
policy point across multiple model families.

### 3.6 Mistral

Models: Mistral Large, Codestral, Magistral families.
Native function calling. Strong European-sovereignty posture;
relevant to UK and EU tenants who require EU-hosted inference or
EU-jurisdictional contractual relationships.

### 3.7 Cohere

Models: Command R+, Command A families.
Native function calling. Enterprise-RAG-leaning; legal and
research verticals find the retrieval-and-citation shape useful.

### 3.8 xAI

Models: Grok family.
Native function calling. Smaller installed base than the above
families; included for completeness and for tenants who hold an
xAI relationship.

### 3.9 DeepSeek

Models: DeepSeek-V family, DeepSeek-R reasoning family.
Native function calling. Cost-leader on inference price-per-token
in 2026; tenants with cost-sensitive workloads need the option.

### 3.10 Meta (Llama family)

Models: Llama family, used either via Meta's own access path or
via third-party hosters (Bedrock, Groq, Together, Replicate, etc.).
Function-calling support via wrapper layers; native support
varies by Llama generation. Particularly relevant to tenants who
will not run third-party-hosted AI for policy reasons but who
accept the Llama family under their own infrastructure.

### 3.11 Self-hosted local models

Models: Llama, Qwen, Mistral, DeepSeek, Phi, and similar
open-weights families, served locally via Ollama, vLLM,
llama.cpp, LM Studio, or equivalent stacks.
Function-calling support depends on the serving stack and the
specific model. This is the **on-premises lane** for tenants who
require AI inference inside their own walls (sovereign-grade
deployments, regulated verticals with strict data-egress rules,
research environments with confidentiality contracts that forbid
external inference). Foundation-aligned posture treats this lane
as first-class; nothing in the governance rules requires external
inference.

### 3.12 Aggregator gateways

Providers: OpenRouter, LiteLLM, Helicone, Portkey, and equivalent
gateway services that present a single API in front of multiple
provider families.
Function-calling support varies by underlying provider.
Tenants who run all their AI traffic through a single gateway
(for unified audit, unified policy, unified billing) need this
lane as a supported route, even though the gateway itself is not
a model. The gateway is a wrapper around the families listed
above; the governance posture is set by the underlying provider
plus the gateway's own audit layer.

---

## 4. Out of scope

The following are not on this list, and not because they are bad
tools but because they do not meet the inclusion criteria of
[§2](#2-inclusion-criteria):

- **Image-generation-only providers** (Stability AI, Midjourney,
  Ideogram, and similar). They generate output; they do not
  sustain an agent loop with tool calls.
- **Voice-only providers** (ElevenLabs, Deepgram, Whisper-only
  services). Same reason.
- **Embedding-only providers** (Voyage AI, Jina AI, and similar).
  Same reason.
- **Single-purpose verticals** (specialised legal-research models
  with no general agent loop, specialised medical models with no
  tool-calling). These can be used by a Claw as a utility model;
  they cannot power one.

A provider that today is single-purpose may move into scope if it
later exposes a general agent loop. The list is dynamic.

---

## 5. How a Claw uses a provider from this list

This document is the **list**. How a specific Claw is wired to a
specific provider is implementation detail, owned by the Solution
that hosts the Claw (or by the OpenClaw runtime for an
ExternalClaw).

The shape of the wiring is constant across providers:

- The Claw's governance layer (Foundation invariants, Solution
  policy, attribution, audit) sits **outside** the provider.
- The provider is reached through an **adapter** that translates
  between the provider's API shape and the Claw's internal
  contract.
- Provider credentials are held under a tenant-scoped resolver,
  so the same Claw definition can be moved between providers
  without rewriting governance.

A Claw that swaps from one provider on this list to another is
the same Claw under Foundation governance. The audit trail, the
corpus, the principal identity, the certification mark, and the
attribution couplet are unchanged by the swap. This is the
substrate-agnostic governance property of
[00058 §4.1](00058-Claw.md#41-substrate-agnostic-governance) in
operational form.

---

## 6. Relationship to other programme commitments

- **Claw vocabulary** ([00058](00058-Claw.md)) defines the
  governed channel that a provider on this list powers, names the
  brands of ExternalClaw (MyClaw, AgentClaw) that consume
  providers directly, and names the PairedClaw bond by which a
  Claw inside a Solution consumes providers under the Solution's
  governance.
- **Modality-agnostic governance** ([00058 §4](00058-Claw.md#4-modality-agnostic-governance))
  and **substrate-agnostic governance**
  ([00058 §4.1](00058-Claw.md#41-substrate-agnostic-governance))
  are the architectural commitments that let this list evolve
  without renegotiating governance. New providers added to the
  list join the same governance envelope as the existing ones.
- **Multi-Model Integration Framework**
  ([UniVERSE 00025](https://github.com/bryanunitek/UniVERSE/blob/main/docs/00025-Multi-Model-Integration-Framework.md))
  is the architectural framework for how UniCORE AI governs across
  multiple model families. This document is the **list of
  families** that framework applies to.
- **Why the rules do not live in the prompt**
  ([UniCORE-AI 20001](https://github.com/bryanunitek/UniCORE-AI/blob/main/docs/20001-Why-Rules-Do-Not-Live-In-The-Prompt.md))
  is the reasoning for why a provider swap does not weaken
  governance.

---

## 7. What this document is not

- It is not an endorsement of any provider over any other.
- It is not a recommendation for which provider a specific tenant
  should choose. That choice is the tenant's to make against their
  own contractual, regulatory, and data-residency posture.
- It is not a compatibility matrix of which provider supports
  which Claw feature. Implementation detail of that kind belongs
  in the relevant Solution's documentation.
- It is not a service-level statement about the providers. The
  programme does not warrant any provider's availability or
  output quality.
- It is not a closed list. New providers that meet the inclusion
  criteria of [§2](#2-inclusion-criteria) will be added.

---

## 8. Status

This document, like all programme documents, is evolving. The
inclusion criteria of [§2](#2-inclusion-criteria) are settled.
The list of supported families in [§3](#3-the-supported-families)
is current as of the document's first publication and will be
revised as the AI provider landscape evolves; revisions are
recorded in the git history of this repository per
[HORIZON.md](../HORIZON.md#versioning-is-not-yet-enabled).

Public-facing changes to the supported-provider list will be
flagged in [HORIZON.md](../HORIZON.md) when the change is material
(a new family added, an existing family removed). Renames within
a family are recorded only in git history.

---

— Bryan Fred, Unitek Systems Limited, Bedford, United Kingdom
