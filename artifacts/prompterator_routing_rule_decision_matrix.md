# Prompterator Routing Rule — Decision Matrix Builder

**Artifact ID:** KOS-0027  
**Title:** Prompterator Routing Rule — Decision Matrix Builder  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Workflow / Product Rule  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This rule fixes the runtime issue found in Proof-of-Work 009.

If the user explicitly asks for a decision matrix, decision table, Bewertungstabelle, Annahmematrix, or decision logic, Prompterator must generate the actual matrix first.

It must not generate an Executive Use-Case Dossier, portfolio structure, or management training document as the primary output unless explicitly requested.

---

## 2. Trigger Rule

When user input contains any of the following signals:

```text
Entscheidungsmatrix
Entscheidungstabelle
Entscheidungslogik
Decision Matrix
Bewertungsmatrix
Annahmematrix
Risiko-/Entscheidungsmatrix
Matrix für Entscheidung
Entscheidungshilfe
Bewertungstabelle
```

Prompterator must route to:

```yaml
mode: "DECISION_MATRIX_BUILDER"
artifact_type: "Decision Matrix"
output_style: "operational_decision_support"
```

---

## 3. Negative Rule

When explicit decision-matrix intent is detected, do **not** output as the primary structure:

- Executive Use-Case Dossier
- portfolio summary
- use-case PDF blueprint
- management training document
- KPI scorecard as main output
- abstract consulting dossier

Allowed secondary elements after the matrix:

- short rationale
- examples
- governance note
- quality check
- implementation notes
- optional KPI assumptions

---

## 4. Required Output Shape

```text
# Entscheidungsmatrix — [Thema]

## 1. Zweck
## 2. Eingabekriterien
## 3. Entscheidungsstufen
## 4. Matrix
## 5. Eskalationslogik
## 6. Dokumentationspflicht
## 7. Beispiele
## 8. Qualitätsprüfung
## 9. Governance
```

---

## 5. Goods Receiving Special Rule

If the input contains:

```text
Wareneingang + beschädigte Ware
Annahme beschädigter Ware
Schadensart + Schadensgrad
Ware beschädigt + Annahme
```

Prompterator should include:

- Schadensart
- Schadensgrad
- Produktkritikalität
- Dokumentationsstatus
- Entscheidung
- Eskalationsstufe
- Maßnahme
- QS-Freigabe
- Lieferanten-/Spediteur-Kommunikation

---

## 6. Example Matrix

```text
| Schadensart | Schadensgrad | Produktkritikalität | Dokumentation vorhanden | Entscheidung | Eskalation | Maßnahme |
|---|---|---|---|---|---|---|
| Verpackung leicht beschädigt | gering | nicht kritisch | ja | Annehmen | Level 0 | Schaden dokumentieren, Ware freigeben |
| Verpackung beschädigt | mittel | kritisch | ja | Annehmen mit Sperrvermerk | Level 1 | QS-Prüfung, Foto, Lieferant informieren |
| Produkt beschädigt | mittel | kritisch | ja/nein | Sperren / Quarantäne | Level 2 | QS-Entscheid, Reklamation vorbereiten |
| Produkt beschädigt / unklare Sicherheit | hoch | kritisch | nein | Ablehnen / Rücksprache | Level 3 | Leitung + QS + Lieferant eskalieren |
```

---

## 7. Quality Gate

A decision-matrix output passes only if:

- [ ] actual matrix is present
- [ ] matrix is the primary output
- [ ] criteria are explicit
- [ ] decision outcomes are explicit
- [ ] escalation levels are present when relevant
- [ ] documentation requirements are present
- [ ] governance / owner review is included
- [ ] no company-specific thresholds are invented

---

## 8. Governance

```text
Human remains owner.
AI remains tool.
Decision matrices require domain validation.
Company-specific thresholds, contractual rules, QA rules, and liability criteria must not be invented.
```

---

## 9. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Decision matrix routing rule created after runtime test showed decision-matrix request routed into Executive Use-Case Dossier instead of matrix-first output. | Operator Fischer |
