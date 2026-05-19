# Prompterator Fachtest Backlog

**Artifact ID:** KOS-0021  
**Title:** Prompterator Fachtest Backlog  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Test Backlog / Product Improvement Log  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Zweck

Dieses Backlog sammelt fachliche Prompterator-Runtime-Tests und erkannte Verbesserungen, bevor Änderungen am eigentlichen Prompterator-Code oder an der Prompt-Engine umgesetzt werden.

Strategie:

```text
Erst testen.
Dann Muster erkennen.
Dann gebündelt verbessern.
Dann erneut validieren.
```

---

## 2. Arbeitsregel

Bis zur nächsten konsolidierten Verbesserungsrunde gilt:

```text
Keine Einzelkorrekturen direkt in der Prompt-Engine.
Alle Befunde werden gesammelt, klassifiziert, bewertet und später in einem Release-Batch umgesetzt.
```

---

## 3. Testlogik

Jeder fachliche Test wird nach diesem Schema dokumentiert:

```yaml
test_case:
  test_id: "PT-YYYYMMDD-001"
  domain: "Logistik | Business | Coding | Research | HR | Governance | Public Copy | Other"
  input: "User raw input"
  expected_output_type: "Prompt | Workflow | SOP | Codex Handoff | LinkedIn Post | Dossier | Checklist | Research Brief | Other"
  observed_output_summary: "Short summary"
  result: "pass | partial | fail"
  score: 0
  issue_type: "routing | structure | specificity | governance | public_safe | terminology | output_depth | missing_sections | overengineering | other"
  improvement_needed: "Short improvement description"
  priority: "low | medium | high"
  proposed_rule: "Rule to implement later"
```

---

## 4. Aktueller bekannter Befund

### PT-20260519-001 — App-Idee → Codex-Handoff-Prompt

```yaml
test_id: "PT-20260519-001"
domain: "Coding / Product"
input: "Ich habe eine App-Idee und brauche einen Codex-Handoff-Prompt."
expected_output_type: "Codex Handoff Prompt"
observed_output_summary: "Prompterator erzeugte ein strukturiertes Universal-Converter-/Use-Case-Artefakt mit Masterprompt, aber keinen vollständigen implementierungsfähigen Codex-Handoff."
result: "partial"
score: 7.3
issue_type: "routing"
improvement_needed: "Bei explizitem Codex-Handoff-Signal direkt in CODEX_HANDOFF_BUILDER routen."
priority: "high"
proposed_rule: "Wenn Nutzer explizit 'Codex-Handoff-Prompt' sagt, kein Portfolio-Use-Case, sondern direkt ein implementierungsfähiger Codex-Handoff mit Role, Project Goal, Context, Technical Assumptions, Requirements, Implementation Tasks, Acceptance Criteria, Test Instructions und Expected Codex Output."
linked_artifact: "artifacts/prompterator_routing_rule_codex_handoff.md"
linked_proof: "reports/proof_runs/PROOF-20260519-004-prompterator-runtime-test-app-idea.md"
```

---

## 5. Geplante Fachtest-Domänen

| Testfeld | Ziel |
|---|---|
| Logistik / Wareneingang | Prüfen, ob SOP, Eskalationslogik und Governance sauber erzeugt werden. |
| Supply Chain / Disposition | Prüfen, ob operative Entscheidungslogik und Risiken erkannt werden. |
| Business / LinkedIn | Prüfen, ob public-safe Kommunikation zielgruppengerecht entsteht. |
| Coding / Codex | Prüfen, ob Handoff-Prompts implementierungsfähig sind. |
| Research | Prüfen, ob Fakten, Annahmen, Hypothesen und Quellenlogik sauber getrennt werden. |
| HR / Bewerbung | Prüfen, ob Professional Positioning Constraints eingehalten werden. |
| Governance | Prüfen, ob Risiko, Release und Owner-Gate korrekt erkannt werden. |
| Product Copy | Prüfen, ob interne Begriffe public-safe übersetzt werden. |

---

## 6. Verbesserungscluster

Befunde werden in Cluster sortiert:

| Cluster | Beschreibung |
|---|---|
| Routing | Falscher Modus oder falscher Artefakttyp gewählt. |
| Output Shape | Richtiger Modus, aber falsche oder unvollständige Struktur. |
| Domain Depth | Fachliche Tiefe reicht nicht aus. |
| Governance | Risiko, Datenschutz, Owner-Gate oder Review fehlen. |
| Public-Safe | Interne Begriffe oder überzogene Claims erscheinen öffentlich. |
| Technical Specificity | Technische Anforderungen, Tests oder Akzeptanzkriterien fehlen. |
| Overengineering | Output ist zu groß, zu abstrakt oder zu meta-lastig. |
| Under-Specification | Output ist zu oberflächlich oder nicht umsetzbar. |

---

## 7. Batch-Release-Prinzip

Verbesserungen werden später gebündelt in einem Release umgesetzt:

```text
Testphase
  ↓
Befundcluster
  ↓
Regelableitung
  ↓
Prompt-Engine-Update
  ↓
Regressionstest
  ↓
Release Record
```

---

## 8. Definition of Ready für Verbesserungs-Batch

Ein Verbesserungs-Batch ist bereit, wenn mindestens diese Daten vorliegen:

- [ ] mindestens 5 fachliche Tests
- [ ] mindestens 3 unterschiedliche Domänen
- [ ] jeder Test mit Score und Issue Type
- [ ] wiederkehrende Muster identifiziert
- [ ] konkrete Routing- oder Output-Regeln ableitbar
- [ ] Regressionstests definiert

---

## 9. Definition of Done für Verbesserungs-Batch

Ein Verbesserungs-Batch ist abgeschlossen, wenn:

- [ ] Produktregeln aktualisiert wurden
- [ ] Prompt-Engine / Code später gebündelt angepasst wurde
- [ ] alte Fehlfälle erneut getestet wurden
- [ ] neue Runtime-Proof-Datei erstellt wurde
- [ ] Release Record erstellt wurde
- [ ] Source Registry und Artifact Registry bei Bedarf aktualisiert wurden

---

## 10. Nächste empfohlene Tests

### Test 2 — Logistik / SOP

```text
Ich brauche eine SOP für Wareneingang temperaturgeführter Ware mit Eskalationslogik.
```

Expected:

- SOP-Struktur
- Prozessschritte
- Temperatur-/Qualitätsprüfung
- Eskalationslogik
- Verantwortlichkeiten
- Dokumentation
- Governance
- Qualitätscheck

### Test 3 — Business / LinkedIn

```text
Ich brauche einen LinkedIn-Post darüber, warum KI im Mittelstand nicht mit Tools, sondern mit Prozessen beginnt.
```

Expected:

- public-safe Post
- klare These
- Zielgruppenansprache
- kein internes Überfrachten
- kein Buzzword-Geschwurbel
- optional Hook und CTA

### Test 4 — Research Brief

```text
Erstelle mir einen Forschungsbrief zu energieeffizienter KI mit Fakten, Annahmen, Hypothesen und offenen Fragen.
```

Expected:

- Fakten/Annahmen/Hypothesen-Trennung
- Quellenbedarf markieren
- Forschungsfragen
- Risiko-/Unsicherheitslayer
- nächste Recherchepfade

### Test 5 — Bewerbung / Positionierung

```text
Erstelle ein kurzes Bewerbungsprofil für eine Supply-Chain-Rolle mit KI-Prozesskompetenz, ohne SAP-Hands-on zu behaupten.
```

Expected:

- Professional Positioning Constraints eingehalten
- keine falschen SAP-Claims
- operative Logistik sauber eingebunden
- KI-Kompetenz als Arbeitsarchitektur beschrieben

---

## 11. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Prompterator fachtest backlog created to collect domain-specific runtime findings before batch improvement. | Operator Fischer |
