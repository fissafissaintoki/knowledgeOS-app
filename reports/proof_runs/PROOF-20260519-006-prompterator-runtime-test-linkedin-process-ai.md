# KnowledgeOS Proof-of-Work 006 — Prompterator Runtime Test: LinkedIn / AI im Mittelstand

**Proof ID:** PROOF-20260519-006  
**Artifact:** Prompterator Runtime Output — LinkedIn Post: KI im Mittelstand beginnt mit Prozessen  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Proof Type:** Domain-specific runtime output test  
**Domain:** Business Communication / LinkedIn / Public-Safe Copy  
**Owner:** Operator Fischer  
**Date:** 2026-05-19  
**Status:** partial / routing issue detected  

---

## 1. Test Input

```text
Ich brauche einen LinkedIn-Post darüber, warum KI im Mittelstand nicht mit Tools, sondern mit Prozessen beginnt.
```

---

## 2. Observed Output Summary

Prompterator generated a structured Universal Converter / Use-Case-PDF style output containing:

- Problemklasse
- Fakten / Annahmen / Hypothesen
- Modus: Use-Case-PDF-Generator
- Artefakt-Blueprint
- Direktes Artefakt
- Portfolio-Zusammenfassung
- Use-Case-Titel
- Zielbild und Nutzen
- Ausgangslage
- Lösungslogik
- Operativer Ablauf
- Datenbasis und Inputs
- Erwarteter Output
- KPI- und Wirkungsannahmen
- Risiken und Governance
- Nächste Schritte
- Qualitätsprüfung
- Governance
- Masterprompt

---

## 3. Evaluation

| Criterion | Result | Notes |
|---|---|---|
| Topic recognition | pass | Correctly identifies AI adoption in Mittelstand and process-first thesis. |
| Facts / assumptions / hypotheses | pass | Clean separation exists. |
| Business logic | pass | Process-first before tool-selection is correctly argued. |
| Governance awareness | pass | Datenschutz, Compliance, stakeholder involvement included. |
| KPI labeling | pass | KPIs are marked as assumptions. |
| LinkedIn post output | fail | No actual LinkedIn post was generated. |
| Public-safe style | partial | Content is mostly safe, but not written in audience-ready LinkedIn format. |
| Routing | fail | Explicit LinkedIn request routed into Use-Case-PDF-Generator. |
| Copywriting quality | partial | Good strategic material, but not transformed into post with hook, narrative, punchline, CTA. |

---

## 4. Key Finding

This output is valid as a **business use-case analysis**.

It is not valid as the requested **LinkedIn post**.

Reason:

```text
The system recognized the topic but selected the wrong output artifact type.
```

The correct route should have been:

```yaml
mode: "LINKEDIN_POST_BUILDER"
artifact_type: "Social Post"
output_style: "public_safe_business_post"
```

---

## 5. Required Improvement

Prompterator needs a clear social-output routing rule.

If user asks for:

```text
LinkedIn-Post
Post
Beitrag
Kommentar
Social Media Text
Skool Post
Community Post
```

then the primary output must be the requested social text, not a use-case dossier.

---

## 6. Recommended LinkedIn Output Shape

```text
# LinkedIn Post

## Zielgruppe
...

## Kernaussage
...

## Post Draft
[Hook]
...
[Main Argument]
...
[Practical Point]
...
[CTA]
...

## Optional Varianten
- kurz
- fachlich
- pointiert

## Qualitätscheck
- public-safe
- keine unbelegten Zahlen
- keine internen Begriffe ohne Erklärung
- keine Buzzwords ohne Substanz
```

---

## 7. Required LinkedIn-Specific Additions

A LinkedIn business post should include:

1. Hook / Einstieg
2. klare These
3. Fachargument
4. Beispiel oder Praxisbezug
5. knapper Erkenntnissatz
6. CTA oder Diskussionsfrage
7. public-safe wording
8. keine unmarkierten KPI-Behauptungen
9. keine überladene interne Systemterminologie
10. optional: 2–3 Varianten

---

## 8. Proposed Routing Rule

```text
If the user explicitly asks for a LinkedIn post, social post, community post, or comment, route to SOCIAL_POST_BUILDER.
Do not generate a portfolio, use-case PDF, or business dossier as the primary output.
Generate the actual post first, then optionally add rationale, variants, and quality check.
```

For AI / Mittelstand / process topics:

```text
If the input includes KI + Mittelstand + Prozesse, produce a practical process-first argument with clear business language, no hype, and a concise public-safe CTA.
```

---

## 9. Suggested Corrected Output Example

```text
KI im Mittelstand scheitert selten an den Tools.
Sie scheitert viel häufiger an unklaren Prozessen.

Viele Unternehmen starten mit der Frage:
„Welches KI-Tool sollen wir einführen?“

Die bessere Frage ist:
„Welcher Prozess ist heute so wiederholbar, teuer, langsam oder fehleranfällig, dass KI dort messbar helfen kann?“

Erst Prozess verstehen.
Dann Datenlage prüfen.
Dann Verantwortlichkeiten klären.
Dann Pilot definieren.
Dann Tool auswählen.

KI ist kein Aufkleber auf kaputten Abläufen.
KI verstärkt das, was bereits strukturiert ist.

Wer im Mittelstand mit KI starten will, sollte nicht zuerst eine Tool-Liste bauen.
Sondern eine Prozesslandkarte.
```

---

## 10. Score

| Dimension | Score |
|---|---:|
| Topic recognition | 9.0 / 10 |
| Business logic | 8.5 / 10 |
| Governance | 8.0 / 10 |
| LinkedIn output fit | 3.0 / 10 |
| Public-safe copy readiness | 5.5 / 10 |
| Routing accuracy | 3.0 / 10 |
| Overall | 6.3 / 10 |

---

## 11. Status Decision

```yaml
runtime_test_status: partial
artifact_status: active
canonical_runtime_claim: false
blockers: none
main_gap: "Explicit LinkedIn post request routed into Use-Case-PDF-Generator instead of SOCIAL_POST_BUILDER."
next_action: "Add SOCIAL_POST_BUILDER routing rule and LinkedIn output shape to improvement backlog."
```

---

## 12. Governance Note

The generated content is strategically usable as source material, but not as final public-facing copy. Public output should be concise, audience-ready, and free of unverified numerical claims unless clearly marked.

---

## 13. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Runtime test documented for LinkedIn / AI Mittelstand process-first output. | Operator Fischer |
