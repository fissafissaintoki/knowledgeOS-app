# Prompterator Master Spec

**Artifact ID:** KOS-0005  
**Title:** Prompterator Master Spec v1.0  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Architecture  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  
**Source Location:** Memory baseline / Operator Fischer product concept / GitHub artifact file  

---

## 1. Purpose

Prompterator is a product and workflow system that converts rough user input into structured, reusable AI work artifacts.

It is designed to make prompt creation operational, not decorative.

Core function:

```text
Raw Input
  ↓
Problem Class
  ↓
Mode Selection
  ↓
Structured Prompt / Workflow / Artifact
  ↓
Quality Check
  ↓
Export / Reuse
```

---

## 2. Product Definition

Prompterator is a single-input prompt and artifact generator.

The user enters a rough idea, task, problem, or intent. Prompterator routes the input into a structured output format such as:

- prompt
- workflow
- SOP
- use case
- checklist
- dossier
- research note
- PDF-ready artifact
- Codex handoff
- Claude handoff
- model-agnostic task package

---

## 3. Core Product Logic

Prompterator should not merely rewrite user input.

It should classify and convert:

```text
Input → Intent → Problem Class → Mode → Artifact Type → Output Structure → Quality Gate
```

Required internal steps:

1. Detect task intent.
2. Classify problem class.
3. Select operating mode.
4. Choose artifact format.
5. Generate structured output.
6. Add constraints and quality checks.
7. Prepare export or reuse format.
8. Preserve public/private terminology boundary.

---

## 4. Primary User Experience

Target UX:

```text
One input line.
One strong generated result.
Optional advanced controls.
```

Core UI elements:

- central input field
- generate action
- output panel
- mode indicator
- copy/export button
- optional PDF export
- optional preset use cases
- optional mode prompt box

Design principle:

```text
Simple surface.
Structured engine underneath.
```

---

## 5. Operating Modes

Prompterator can route into modes such as:

| Mode | Purpose |
|---|---|
| Universal Converter | Convert rough input into structured artifact. |
| Prompt Builder | Produce a strong reusable prompt. |
| Workflow Builder | Produce process steps, triggers, checks, and outputs. |
| SOP Builder | Produce operational procedure. |
| Research Builder | Produce structured research brief. |
| Codex Handoff | Produce implementation prompt for Codex. |
| Claude Handoff | Produce longform implementation or documentation prompt. |
| Public-Safe Rewrite | Convert internal architecture language into external-facing language. |

---

## 6. KnowledgeOS Integration

Prompterator is a Proof-of-Work candidate for KnowledgeOS because it touches several system layers:

| KnowledgeOS Layer | Prompterator Role |
|---|---|
| Artifact Registry | Prompterator spec is registered as KOS-0005. |
| Canonical Terms | Internal terms must remain consistent. |
| Deprecated Terms | Legacy terms must not re-enter product language. |
| Pattern Map | Prompterator uses Universal Converter and Raw Input to Artifact patterns. |
| Source Registry | Product spec source must be traceable. |
| Artifact Relations | Prompterator depends on governance, public-safe, and multi-model cooperation artifacts. |
| Verification Checklist | Product spec must pass verification before canonical release. |
| Drift Report | Public/private terminology and product claims must be checked. |
| Release Policy | Prompterator remains active until owner-approved canonical release. |
| Public-Safe Policy | Public website copy must be simplified and claim-safe. |

---

## 7. Core Patterns

Prompterator uses these patterns:

- Raw Input to Reusable Artifact
- Universal Converter
- Mode Routing
- Prompt Builder
- Workflow Builder
- Public-Safe Rewrite
- Multi-Model Handoff
- PDF Export Candidate
- Artifact Quality Gate

---

## 8. Governance Requirements

Prompterator must obey these governance rules:

1. Do not claim autonomous full control.
2. Do not frame AI as final decision-maker.
3. Do not expose private Operator Fischer architecture unnecessarily in public copy.
4. Do not use deprecated terms as active product terminology.
5. Do not claim integrations that are not implemented.
6. Do not present prototype logic as production-certified enterprise software.
7. Label assumptions, prototypes, and future features clearly.
8. Keep human owner approval for release-critical outputs.

---

## 9. Public-Safe Product Description

Public-safe version:

```text
Prompterator converts rough input into structured prompts, workflows, and reusable work artifacts. It helps turn ideas into clear AI instructions, process drafts, use cases, and export-ready outputs.
```

Internal version:

```text
Prompterator is a productized interface on top of the Operator Fischer artifact-conversion logic, using KnowledgeOS registry principles and GosseOS-style routing patterns.
```

---

## 10. Current Release Assessment

| Area | Status |
|---|---|
| Product concept | strong |
| UI direction | active |
| KnowledgeOS integration | proof-run candidate |
| Public-safe language | requires review |
| Source traceability | improved by this file |
| Canonical readiness | not yet canonical |
| Risk level | medium |
| Drift risk | medium |

---

## 11. Reuse Rules

Use when:

- building or extending Prompterator
- preparing Codex or Claude handoffs
- writing public product descriptions
- designing UI logic
- connecting Prompterator to KnowledgeOS
- demonstrating KnowledgeOS proof-of-work

Do not use when:

- claiming finished production readiness without verification
- publishing internal architecture unfiltered
- granting AI unsupervised control
- presenting assumptions as measured results

---

## 12. Quality Check

Prompterator as Proof-of-Work must demonstrate:

- registry entry exists
- source traceability improves
- drift report exists
- verification record exists
- release record exists
- public-safe rules are applied
- governance constraints are respected
- next implementation actions are defined

---

## 13. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Prompterator converted from memory baseline into explicit KnowledgeOS artifact file. | Operator Fischer |
