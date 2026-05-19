# Prompterator Routing Fix Batch v1

**Artifact ID:** KOS-0026  
**Title:** Prompterator Routing Fix Batch v1  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Batch Improvement Spec / Product Rule Set  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  
**Implementation Status:** queued_for_later_prompt_engine_code_integration  

---

## 1. Zweck

Dieses Artefakt bündelt die bisher erkannten Prompterator-Routing-Fehler aus den fachlichen Runtime-Tests.

Ziel ist nicht die sofortige Code-Änderung, sondern eine saubere Batch-Spezifikation für eine spätere gebündelte Prompt-Engine-/Code-Übernahme.

Arbeitsentscheidung:

```text
Nicht einzeln patchen.
Weiter testen.
Dann gebündelt verbessern.
```

---

## 2. Ausgangslage

Prompterator erkennt Themen in den bisherigen Tests überwiegend gut, routet aber zu häufig in einen generischen Universal-Converter-, Portfolio- oder Executive-Use-Case-Dossier-Modus.

Das Kernproblem ist daher:

```text
Intent erkannt, aber Artifact Type falsch gewählt.
```

Cluster:

```text
Cluster 1: Intent-to-Artifact Routing
```

Sekundärer Cluster:

```text
Cluster 2: Evidence / Source Logic
```

---

## 3. Enthaltene Routing-Regeln

| Artifact ID | Trigger | Zielmodus | Zielartefakt | Status |
|---|---|---|---|---|
| KOS-0020 | Codex-Handoff-Prompt | CODEX_HANDOFF_BUILDER | Codex Handoff Prompt | queued |
| KOS-0022 | LinkedIn/Post/Beitrag/Kommentar | SOCIAL_POST_BUILDER | Social Post | queued |
| KOS-0023 | Forschungsbrief/Research Brief | RESEARCH_BRIEF_BUILDER | Research Brief | queued |
| KOS-0024 | SOP/Arbeitsanweisung/Prozessanweisung | SOP_BUILDER | SOP | queued |
| KOS-0025 | Bewerbungsprofil/Kurzprofil/Profiltext | PROFESSIONAL_PROFILE_BUILDER | Career Positioning Text | queued |

---

## 4. Batch-Regelprinzip

Prompterator muss künftig zuerst den explizit gewünschten Artefakttyp erkennen.

Priorität:

```text
Explicit Artifact Request > Generic Universal Converter
```

Wenn der Nutzer einen konkreten Outputtyp nennt, darf Prompterator nicht automatisch in Portfolio-/Use-Case-/PDF-Dossier-Struktur ausweichen.

---

## 5. Routing Priority Table

| User Signal | Must Route To | Must Not Route To |
|---|---|---|
| Codex-Handoff-Prompt | CODEX_HANDOFF_BUILDER | Portfolio Use Case |
| LinkedIn-Post / Post / Beitrag | SOCIAL_POST_BUILDER | Use-Case-PDF-Generator |
| Forschungsbrief / Research Brief | RESEARCH_BRIEF_BUILDER | Portfolio / Business Dossier |
| SOP / Arbeitsanweisung | SOP_BUILDER | Use-Case Portfolio |
| Bewerbungsprofil / Kurzprofil | PROFESSIONAL_PROFILE_BUILDER | Executive Use-Case Dossier |

---

## 6. Output Contracts

### 6.1 CODEX_HANDOFF_BUILDER

Required output:

```text
# Codex Handoff Prompt

## Role
## Project Goal
## Context
## Technical Assumptions
## Functional Requirements
## Non-Functional Requirements
## Implementation Tasks
## Acceptance Criteria
## Test Instructions
## Expected Codex Output
```

Fallback:

If actual app idea is missing, generate a Codex Handoff Intake Prompt instead of inventing a fake spec.

---

### 6.2 SOCIAL_POST_BUILDER

Required output:

```text
# LinkedIn Post / Social Post

## Zielgruppe
## Kernaussage
## Post Draft
## Optionale Varianten
## Qualitätscheck
```

Primary output must be the finished post.

---

### 6.3 RESEARCH_BRIEF_BUILDER

Required output:

```text
# Forschungsbrief — [Thema]

## 1. Executive Summary
## 2. Forschungsfrage
## 3. Faktenlage
## 4. Annahmen
## 5. Hypothesen
## 6. Offene Forschungsfragen
## 7. Relevante Forschungsfelder
## 8. Methodische Hinweise
## 9. Risiken / Unsicherheiten
## 10. Quellenbedarf / Rechercheplan
## 11. Nächste Forschungsschritte
```

Evidence markers required:

```text
[FAKT – BELEGT]
[FAKT – QUELLE ERFORDERLICH]
[ANNAHME]
[HYPOTHESE]
[OFFENE FRAGE]
[UNSICHER]
```

---

### 6.4 SOP_BUILDER

Required output:

```text
# SOP — [Prozess / Thema]

## 1. Zweck
## 2. Geltungsbereich
## 3. Rollen und Verantwortlichkeiten
## 4. Benötigte Inputs / Dokumente
## 5. Prozessablauf
## 6. Prüf- und Entscheidungspunkte
## 7. Eskalationsmatrix
## 8. Dokumentationspflicht
## 9. Fehlerfälle / Sonderfälle
## 10. Qualitätsprüfung
## 11. Governance / Review
## 12. Kurz-Checkliste
```

Cold-chain special rule:

If Wareneingang + temperaturgeführt appears, include decision matrix, QS escalation, blocking/quarantine, data logger handling, documentation, and no invented company-specific thresholds.

---

### 6.5 PROFESSIONAL_PROFILE_BUILDER

Required output:

```text
# Bewerbungsprofil

## Kurzprofil
## Kompetenzschwerpunkte
## Positionierung
## Wahrheitsgrenze / Nicht behaupten
## Optional: Variante für Lebenslauf
## Optional: Variante für LinkedIn / Recruiter
## Qualitätscheck
```

Truth-boundary:

- no invented SAP hands-on experience
- no invented certifications
- no invented tool expertise
- no invented formal titles
- AI competence as process support, not decision ownership

---

## 7. Regression Test Set

After implementation, rerun these tests.

### RT-001 — Codex Handoff

```text
Ich habe eine App-Idee und brauche einen Codex-Handoff-Prompt.
```

Expected:

```yaml
mode: CODEX_HANDOFF_BUILDER
result: Codex Handoff Intake Prompt or implementation-ready handoff
```

### RT-002 — SOP

```text
Ich brauche eine SOP für Wareneingang temperaturgeführter Ware mit Eskalationslogik.
```

Expected:

```yaml
mode: SOP_BUILDER
result: operational SOP with escalation matrix
```

### RT-003 — LinkedIn Post

```text
Ich brauche einen LinkedIn-Post darüber, warum KI im Mittelstand nicht mit Tools, sondern mit Prozessen beginnt.
```

Expected:

```yaml
mode: SOCIAL_POST_BUILDER
result: finished LinkedIn post as primary output
```

### RT-004 — Research Brief

```text
Erstelle mir einen Forschungsbrief zu energieeffizienter KI mit Fakten, Annahmen, Hypothesen und offenen Fragen.
```

Expected:

```yaml
mode: RESEARCH_BRIEF_BUILDER
result: evidence-structured research brief
```

### RT-005 — Professional Profile

```text
Erstelle ein kurzes Bewerbungsprofil für eine Supply-Chain-Rolle mit KI-Prozesskompetenz, ohne SAP-Hands-on zu behaupten.
```

Expected:

```yaml
mode: PROFESSIONAL_PROFILE_BUILDER
result: direct 3–5 sentence professional profile with truth-boundary
```

---

## 8. Implementation Guidance

When the implementation batch is executed later, the Prompt-Engine / code should apply this decision order:

```text
1. Detect explicit artifact keywords.
2. If explicit artifact match exists, route to specialized builder.
3. If multiple artifact signals exist, prioritize the most concrete deliverable.
4. Only use Universal Converter when no specific artifact type is requested.
5. Only generate PDF/portfolio/dossier format if requested or if selected by user.
6. Add optional analysis/quality/governance after primary deliverable, not before it.
```

---

## 9. Routing Pseudocode

```text
if input contains codex_handoff_signal:
    route CODEX_HANDOFF_BUILDER
elif input contains social_post_signal:
    route SOCIAL_POST_BUILDER
elif input contains research_brief_signal:
    route RESEARCH_BRIEF_BUILDER
elif input contains sop_signal:
    route SOP_BUILDER
elif input contains professional_profile_signal:
    route PROFESSIONAL_PROFILE_BUILDER
else:
    route UNIVERSAL_CONVERTER
```

Priority note:

If a request contains both content topic and artifact type, the artifact type controls the route.

Example:

```text
KI im Mittelstand + LinkedIn-Post
```

Route:

```text
SOCIAL_POST_BUILDER
```

Not:

```text
Use-Case-PDF-Generator
```

---

## 10. Governance

This batch must preserve:

```text
Human remains owner.
AI remains tool.
Primary requested artifact comes first.
No unsupported claims.
No invented credentials.
No invented company-specific thresholds.
No unsourced research facts as verified facts.
No unbounded automation claims.
```

---

## 11. Readiness Status

```yaml
batch_name: "Prompterator Intent-to-Artifact Routing Fix Batch"
version: "v1.0"
status: "ready_for_later_prompt_engine_code_integration"
implementation_timing: "deferred"
reason: "Further fachliche tests may still add routing rules before batch implementation."
```

---

## 12. Open Questions Before Implementation

- Should PDF/Dossier mode become explicit opt-in?
- Should every output include a compact mode/debug line?
- Should Prompterator show selected mode to the user?
- Should weak or ambiguous inputs trigger an intake prompt instead of inferred output?
- Should mode priority be configurable in UI?

---

## 13. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Consolidated first Prompterator routing fix batch from fachtests and product rules KOS-0020, KOS-0022, KOS-0023, KOS-0024, KOS-0025. | Operator Fischer |
