# Prompterator Root-Cause Finding — Intent-to-Artifact Routing

**Finding ID:** PRC-20260519-001  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Category:** Product Runtime Finding / Routing Defect  
**Owner:** Operator Fischer  
**Date:** 2026-05-19  
**Status:** active  
**Severity:** high  

---

## 1. Root-Cause Statement

Prompterator erkennt Themen gut, aber priorisiert zu oft den Executive-/Portfolio-/Use-Case-Dossier-Modus statt den explizit angeforderten Artefakttyp.

---

## 2. Pattern

Across multiple fachliche Runtime tests, Prompterator correctly recognized topic and domain, but selected an overly generic output container.

Observed pattern:

```text
Input intent recognized
  ↓
Domain understood
  ↓
Governance often included
  ↓
Wrong primary artifact type selected
  ↓
Executive / Portfolio / Use-Case Dossier dominates output
```

---

## 3. Affected Tests

| Proof ID | Requested Artifact | Observed Output | Result |
|---|---|---|---|
| PROOF-20260519-004 | Codex Handoff Prompt | Use-Case / Portfolio-style artifact | partial |
| PROOF-20260519-005 | SOP | SOP-like draft with portfolio framing | partial |
| PROOF-20260519-006 | LinkedIn Post | Use-Case-PDF structure, no finished post | partial/fail |
| PROOF-20260519-007 | Research Brief | Research planning / use-case framing | partial |
| PROOF-20260519-008 | Career Profile | 26-page Executive Use-Case Dossier | partial/fail |
| PROOF-20260519-009 | Decision Matrix | 26-page Executive Use-Case Dossier | partial/fail |

---

## 4. Diagnosis

The issue is not primarily topic understanding.

The issue is routing priority.

Prompterator currently appears to favor:

```text
Universal Converter
Executive Use-Case Dossier
Portfolio PDF
```

even when the user explicitly asks for:

```text
Codex Handoff Prompt
SOP
LinkedIn Post
Research Brief
Career Profile
Decision Matrix
```

---

## 5. Correct Priority Rule

```text
Explicit Artifact Request > Generic Universal Converter > Executive / Portfolio / PDF Dossier
```

If the user names a concrete artifact type, the requested artifact type must control the route.

---

## 6. Required System Behavior

Prompterator must:

1. detect explicit artifact keywords
2. choose specialized builder when artifact type is clear
3. generate the requested artifact as primary output
4. move analysis, governance, variants, and quality checks after the primary artifact
5. only use Executive/Portfolio/Dossier format when explicitly requested or selected

---

## 7. Current Fix Candidates

| Artifact ID | Fix Rule | Target Builder |
|---|---|---|
| KOS-0020 | Codex handoff intent | CODEX_HANDOFF_BUILDER |
| KOS-0022 | Social post intent | SOCIAL_POST_BUILDER |
| KOS-0023 | Research brief intent | RESEARCH_BRIEF_BUILDER |
| KOS-0024 | SOP intent | SOP_BUILDER |
| KOS-0025 | Professional profile intent | PROFESSIONAL_PROFILE_BUILDER |
| pending | Decision matrix intent | DECISION_MATRIX_BUILDER |

---

## 8. Product Impact

Severity: high

Reason:

The product can look powerful because it generates large dossiers, but the user may not receive the exact artifact requested.

This creates:

- unnecessary output bloat
- slower user workflow
- reduced product trust
- weak artifact specificity
- poor match between intent and deliverable
- overproduction of executive-style documents

---

## 9. Design Correction

The output hierarchy should be:

```text
1. Requested artifact first
2. Optional explanation second
3. Optional variants third
4. Optional governance / quality check fourth
5. PDF / Dossier only if requested
```

---

## 10. Implementation Note

This root-cause finding should be used as the central rationale for the Prompterator Routing Fix Batch v1.

Related artifact:

```text
artifacts/prompterator_routing_fix_batch_v1.md
```

---

## 11. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Root-cause finding documented after repeated runtime tests showed good topic recognition but weak intent-to-artifact routing. | Operator Fischer |
