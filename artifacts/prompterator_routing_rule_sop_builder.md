# Prompterator Routing Rule — SOP Builder

**Artifact ID:** KOS-0024  
**Title:** Prompterator Routing Rule — SOP Builder  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Workflow / Product Rule  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This rule fixes the runtime issue found in Proof-of-Work 005.

If the user explicitly asks for an SOP, Standard Operating Procedure, Arbeitsanweisung, Prozessanweisung, Verfahrensanweisung, or operative Schrittfolge, Prompterator must generate a direct SOP document.

It must not generate a portfolio-style use case or PDF blueprint as the primary output.

---

## 2. Trigger Rule

When user input contains any of the following signals:

```text
SOP
Standard Operating Procedure
Arbeitsanweisung
Prozessanweisung
Verfahrensanweisung
Standardprozess
Prozessbeschreibung
Schritt-für-Schritt-Anweisung
operative Anweisung
Arbeitsablauf mit Verantwortlichkeiten
Eskalationslogik
```

Prompterator must route to:

```yaml
mode: "SOP_BUILDER"
artifact_type: "SOP"
output_style: "operational_procedure"
```

---

## 3. Negative Rule

When explicit SOP intent is detected, do **not** output as the primary structure:

- portfolio summary
- use-case PDF blueprint
- business case
- abstract consulting dossier
- KPI-heavy strategy document
- generic concept explanation without procedure
- masterprompt only

Allowed secondary elements after the SOP:

- short rationale
- assumptions
- governance note
- quality check
- implementation notes
- training notes
- optional one-page checklist

---

## 4. Required Output Shape

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

---

## 5. Required SOP Components

A valid SOP output must include:

1. Purpose / Zweck
2. Scope / Geltungsbereich
3. Roles and responsibilities
4. Required inputs, tools, documents, or system data
5. Step-by-step process
6. Decision points
7. Escalation logic
8. Documentation requirements
9. Exception handling
10. Quality check
11. Governance / review logic
12. Short operational checklist

---

## 6. Cold-Chain / Goods Receiving Special Rule

If the input contains:

```text
Wareneingang + temperaturgeführt
Wareneingang + Temperatur
Kühlware + Wareneingang
Tiefkühlware + Wareneingang
Cold Chain + Goods Receiving
Temperaturabweichung + Eskalation
```

Prompterator must generate a cold-chain receiving SOP with:

- temperature check
- target temperature range
- actual temperature value
- deviation duration if available
- data logger check
- product group distinction
- packaging condition
- batch / lot documentation
- acceptance decision
- quarantine / blocking logic
- supplier / carrier communication
- QS escalation

---

## 7. Required Cold-Chain SOP Output Shape

```text
# SOP — Wareneingang temperaturgeführter Ware

## 1. Zweck
## 2. Geltungsbereich
## 3. Rollen und Verantwortlichkeiten
   - Wareneingang Mitarbeiter
   - Schichtleitung / Leitstand
   - QS
   - Einkauf / Disposition
   - Lieferant / Spediteur

## 4. Benötigte Inputs / Dokumente
   - Lieferschein
   - Temperaturvorgabe
   - Ist-Temperatur
   - Datenlogger
   - Produkt- und Chargendaten
   - Verpackungszustand

## 5. Prozessablauf
## 6. Temperaturprüfung
## 7. Eskalationsmatrix
## 8. Entscheidungslogik
## 9. Dokumentationspflicht
## 10. Fehlerfälle / Sonderfälle
## 11. Qualitätsprüfung
## 12. Governance / Review
## 13. Kurz-Checkliste für den Wareneingang
```

---

## 8. Escalation Matrix Requirement

SOP outputs with escalation logic must include a matrix.

Example:

```text
| Stufe | Bedingung | Maßnahme | Owner | Dokumentation |
|---|---|---|---|---|
| Level 0 | Soll erfüllt | Ware annehmen | Wareneingang | Temperatur dokumentieren |
| Level 1 | geringe Abweichung / unklarer Befund | QS-Prüfung | QS | Foto, Messwert, Logger prüfen |
| Level 2 | kritische Abweichung | Ware sperren / Quarantäne | QS + Leitung | Sperrvermerk, Lieferant informieren |
| Level 3 | schwere oder nicht akzeptable Abweichung | Ablehnung / Rücksendung / Managemententscheid | Leitung / QS | Abweichungsbericht |
```

Thresholds must not be invented as company policy unless provided by the user.

If thresholds are missing, write:

```text
[UNTERNEHMENSSPEZIFISCH ZU DEFINIEREN]
```

---

## 9. Decision Logic Requirement

For operational SOPs, include clear decision outputs:

```text
Annehmen
Annehmen mit QS-Prüfung
Sperren / Quarantäne
Ablehnen / Rücksendung
Eskalieren an Leitung / QS / Einkauf
```

---

## 10. Quality Gate

A SOP output passes only if it includes:

- [ ] Zweck
- [ ] Geltungsbereich
- [ ] Rollen
- [ ] Inputs / Dokumente
- [ ] Prozessablauf
- [ ] Prüf- oder Entscheidungspunkte
- [ ] Eskalationsmatrix if escalation requested
- [ ] Dokumentationspflicht
- [ ] Fehlerfälle / Sonderfälle
- [ ] Qualitätsprüfung
- [ ] Governance / Review
- [ ] Kurz-Checkliste

If fewer than 9 of 12 are present:

```yaml
routing_quality: "fail"
```

If all required sections are present but not operational enough:

```yaml
routing_quality: "partial"
```

If all required sections are present and operationally usable:

```yaml
routing_quality: "pass"
```

---

## 11. Corrected Masterprompt Snippet

```text
If the user explicitly asks for an SOP, Standard Operating Procedure, Arbeitsanweisung, Prozessanweisung, Verfahrensanweisung, Standardprozess, Prozessbeschreibung, or operative Schritt-für-Schritt-Anweisung, route to SOP_BUILDER.
Do not generate a portfolio, use-case PDF, or business dossier as the primary output.
Generate a direct SOP with Zweck, Geltungsbereich, Rollen, Inputs, Prozessablauf, Prüf-/Entscheidungspunkte, Eskalationsmatrix, Dokumentationspflicht, Fehlerfälle, Qualitätsprüfung, Governance/Review, and Kurz-Checkliste.
If the SOP concerns Wareneingang temperaturgeführter Ware, include cold-chain-specific decision logic, QS escalation, blocking/quarantine, data logger handling, and documentation requirements. Do not invent company-specific thresholds; mark missing thresholds as [UNTERNEHMENSSPEZIFISCH ZU DEFINIEREN].
```

---

## 12. Governance

This rule must preserve:

```text
Human remains owner.
AI remains tool.
Operational SOPs require domain validation.
Company-specific thresholds must not be invented.
Final SOP release requires responsible department approval.
```

---

## 13. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | SOP routing rule created after runtime test showed explicit SOP request still produced too much portfolio/use-case framing and lacked a hard decision matrix. | Operator Fischer |
