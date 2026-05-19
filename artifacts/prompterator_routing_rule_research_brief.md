# Prompterator Routing Rule — Research Brief Builder

**Artifact ID:** KOS-0023  
**Title:** Prompterator Routing Rule — Research Brief Builder  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Workflow / Product Rule  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This rule fixes the runtime issue found in Proof-of-Work 007.

If the user explicitly asks for a research brief, scientific overview, research overview, or a structure with facts, assumptions, hypotheses, and open questions, Prompterator must generate an evidence-structured research brief.

It must not generate a portfolio-style use case or PDF blueprint as the primary output.

---

## 2. Trigger Rule

When user input contains any of the following signals:

```text
Forschungsbrief
Research Brief
Forschungsübersicht
wissenschaftliche Übersicht
wissenschaftlicher Überblick
Fakten, Annahmen, Hypothesen
offene Fragen
Stand der Forschung
Literaturüberblick
Recherchebrief
Research Note
```

Prompterator must route to:

```yaml
mode: "RESEARCH_BRIEF_BUILDER"
artifact_type: "Research Brief"
output_style: "evidence_structured"
```

---

## 3. Negative Rule

When explicit research-brief intent is detected, do **not** output as the primary structure:

- portfolio summary
- use-case PDF blueprint
- generic business dossier
- KPI-heavy consulting logic
- public post format
- implementation handoff
- unsupported factual claims without evidence markers

Allowed secondary elements:

- quality check
- governance note
- source plan
- next research steps
- optional PDF-ready formatting note

---

## 4. Required Output Shape

```text
# Forschungsbrief — [Thema]

## 1. Executive Summary
## 2. Forschungsfrage
## 3. Faktenlage
   - Fakt
   - Quelle erforderlich / Quelle vorhanden
   - Evidenzgrad
## 4. Annahmen
## 5. Hypothesen
## 6. Offene Forschungsfragen
## 7. Relevante Forschungsfelder
## 8. Methodische Hinweise
## 9. Risiken / Unsicherheiten
## 10. Quellenbedarf / Rechercheplan
## 11. Nächste Forschungsschritte
```

---

## 5. Required Sections

### 5.1 Executive Summary

Must summarize the research topic, current knowledge state, uncertainty, and practical relevance.

### 5.2 Forschungsfrage

Must define one clear primary research question.

Optional:

- sub-questions
- scope boundaries
- excluded topics

### 5.3 Faktenlage

Each factual claim must include evidence state:

```text
- [FAKT – QUELLE ERFORDERLICH] Claim ...
  Evidenzgrad: niedrig | mittel | hoch | unklar
  Quellenstatus: fehlt | vorhanden | zu prüfen
```

If no source is supplied or retrieved, label factual claims as source-required.

### 5.4 Annahmen

Must list plausible but unverified assumptions.

### 5.5 Hypothesen

Must list testable hypotheses about causality, probability, impact, or relationships.

### 5.6 Offene Forschungsfragen

Must include a dedicated open-questions section.

### 5.7 Relevante Forschungsfelder

Must identify adjacent domains, such as:

- algorithms
- hardware
- data efficiency
- inference optimization
- sustainability
- infrastructure
- measurement methodology

### 5.8 Methodische Hinweise

Must explain how the topic should be researched or validated.

### 5.9 Risiken / Unsicherheiten

Must explicitly mark:

- source uncertainty
- measurement uncertainty
- overgeneralization risk
- hype risk
- outdated-source risk

### 5.10 Quellenbedarf / Rechercheplan

Must specify what sources are required:

- primary papers
- official documentation
- benchmark studies
- energy measurement studies
- current review papers
- industry data if needed

### 5.11 Nächste Forschungsschritte

Must define actionable research steps.

---

## 6. Evidence Layer

Research outputs must use this evidence classification:

```text
[FAKT – BELEGT]
[FAKT – QUELLE ERFORDERLICH]
[ANNAHME]
[HYPOTHESE]
[OFFENE FRAGE]
[UNSICHER]
```

Rules:

- Do not present unsourced claims as verified facts.
- If freshness matters, mark source freshness requirement.
- If the topic is current or technical, cite or flag sources as required.
- Speculative KPI values must be labelled as assumptions or removed.

---

## 7. Source Freshness Rule

For dynamic research topics such as AI, energy efficiency, model architectures, data center infrastructure, or hardware acceleration:

```text
Mark source freshness as required.
```

If no browsing/source retrieval is available, state:

```text
Quellenprüfung erforderlich vor externer Verwendung.
```

---

## 8. Quality Gate

A research brief output passes only if it includes:

- [ ] Executive Summary
- [ ] Forschungsfrage
- [ ] Faktenlage with evidence markers
- [ ] Annahmen
- [ ] Hypothesen
- [ ] Offene Forschungsfragen
- [ ] Relevante Forschungsfelder
- [ ] Methodische Hinweise
- [ ] Risiken / Unsicherheiten
- [ ] Quellenbedarf / Rechercheplan
- [ ] Nächste Forschungsschritte

If fewer than 9 of 11 are present:

```yaml
routing_quality: "fail"
```

If all required sections are present but weak:

```yaml
routing_quality: "partial"
```

If all required sections are present and evidence markers are used correctly:

```yaml
routing_quality: "pass"
```

---

## 9. Corrected Masterprompt Snippet

```text
If the user explicitly asks for a Forschungsbrief, Research Brief, Forschungsübersicht, scientific overview, facts/assumptions/hypotheses/open questions, or Stand der Forschung, route to RESEARCH_BRIEF_BUILDER.
Do not generate a portfolio, use-case PDF, or generic business dossier as the primary output.
Generate an evidence-structured research brief with: Executive Summary, Forschungsfrage, Faktenlage with evidence status, Annahmen, Hypothesen, offene Forschungsfragen, relevante Forschungsfelder, methodische Hinweise, Risiken/Unsicherheiten, Quellenbedarf/Rechercheplan, and nächste Forschungsschritte.
Mark unsourced factual claims as [FAKT – QUELLE ERFORDERLICH]. Use [ANNAHME], [HYPOTHESE], [OFFENE FRAGE], and [UNSICHER] where appropriate.
```

---

## 10. Governance

This rule must preserve:

```text
Human remains owner.
AI remains tool.
Facts require source status.
Assumptions remain assumptions.
Hypotheses remain testable hypotheses.
No unsourced claim becomes a verified fact.
```

---

## 11. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Research brief routing rule created after runtime test showed research request produced generic portfolio/use-case framing and weak evidence/source logic. | Operator Fischer |
