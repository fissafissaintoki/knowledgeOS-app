# Prompterator Routing Rule — Professional Profile Builder

**Artifact ID:** KOS-0025  
**Title:** Prompterator Routing Rule — Professional Profile Builder  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Workflow / Product Rule  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This rule fixes the runtime issue found in Proof-of-Work 008.

If the user explicitly asks for a Bewerbungsprofil, Kurzprofil, Profiltext, Lebenslaufprofil, Recruiter-Profil, professionelles Profil, Bewerbungstext, or similar career-positioning output, Prompterator must generate the actual profile text first.

It must not generate an Executive Use-Case Dossier, portfolio structure, management training document, or PDF dossier as the primary output unless explicitly requested.

---

## 2. Trigger Rule

When user input contains any of the following signals:

```text
Bewerbungsprofil
Kurzprofil
Profiltext
Lebenslaufprofil
Recruiter-Profil
professionelles Profil
Bewerbungstext
CV-Profil
Lebenslauf-Zusammenfassung
Karriereprofil
Profil für Bewerbung
Profil für Recruiter
professionelle Positionierung
```

Prompterator must route to:

```yaml
mode: "PROFESSIONAL_PROFILE_BUILDER"
artifact_type: "Career Positioning Text"
output_style: "truthful_professional_positioning"
```

---

## 3. Negative Rule

When explicit career-profile intent is detected, do **not** output as the primary structure:

- Executive Use-Case Dossier
- portfolio summary
- use-case PDF blueprint
- management training document
- KPI scorecard as main output
- process matrix as main output
- generic consulting dossier
- long governance framework

Allowed secondary elements after the profile:

- Kompetenzschwerpunkte
- Recruiter variant
- CV variant
- LinkedIn variant
- truth-boundary check
- short quality check
- optional notes for tailoring

---

## 4. Required Output Priority

Primary output must be the usable profile text.

Correct order:

```text
# Bewerbungsprofil

## Kurzprofil
[3–5 Sätze]

## Kompetenzschwerpunkte
- ...

## Positionierung
...

## Wahrheitsgrenze / Nicht behaupten
- ...

## Optionale Varianten
...
```

Incorrect order:

```text
# Executive Use-Case Dossier
# Management-Kontext
# Prozessmatrix
# KPI-Scorecard
# Schulungsmodul
...
```

---

## 5. Required Output Shape

```text
# Bewerbungsprofil

## Kurzprofil
[3–5 Sätze]

## Kompetenzschwerpunkte
- Supply Chain / Logistik
- Prozesssteuerung
- Qualitäts- und Verantwortungsbewusstsein
- KI-gestützte Prozess- und Entscheidungsunterstützung

## Positionierung
[1 kurzer Absatz für Recruiter / Fachabteilung]

## Wahrheitsgrenze / Nicht behaupten
- Keine SAP-Hands-on-Erfahrung behaupten, wenn nicht vorhanden.
- Keine nicht belegten Zertifikate, Tools oder Führungsverantwortung behaupten.
- KI-Kompetenz als Arbeitsmethodik / Prozessunterstützung formulieren, nicht als autonome Entscheidungsautorität.

## Optional: Variante für Lebenslauf
...

## Optional: Variante für LinkedIn / Recruiter
...

## Qualitätscheck
- professionell
- wahrheitsgemäß
- recruiter-tauglich
- keine überzogenen Claims
```

---

## 6. Professional Truth Boundary

For all career/profile outputs, Prompterator must preserve truthful positioning.

Do not invent:

- SAP hands-on experience
- certifications
- formal job titles
- management authority
- enterprise implementation responsibility
- tool expertise not provided by the user
- measurable achievements without source

Use instead:

```text
Prozessverständnis
Schnittstellenverständnis
strukturierte Systemlogik
Bereitschaft zur Einarbeitung
KI-gestützte Prozess- und Entscheidungsunterstützung
operative Erfahrung
```

---

## 7. Supply Chain + AI Process Competence Rule

If input contains:

```text
Supply Chain + KI-Prozesskompetenz
Logistik + KI
Prozesslogistik + KI
Supply-Chain-Rolle + KI
```

Prompterator should emphasize:

- operative Supply-Chain-/Logistik-Erfahrung
- Prozessverständnis
- strukturierte Arbeitsweise
- Schnittstellenlogik
- Qualitätsbewusstsein
- KI als Unterstützung für Analyse, Strukturierung, Dokumentation und Entscheidungsgrundlagen
- no false SAP hands-on claim

---

## 8. Example Corrected Output

```text
# Bewerbungsprofil

## Kurzprofil
Erfahrener Prozess- und Supply-Chain-Logistiker mit langjähriger operativer Praxis in temperaturgeführter Logistik, Wareneingang, Kommissionierung, Warenausgang und prozessnaher Steuerung. Starker Fokus auf strukturierte Abläufe, Qualitätsbewusstsein, Schnittstellenverständnis und KI-gestützte Prozess- und Entscheidungsunterstützung. Verbindet operative Logistikerfahrung mit moderner Arbeitsmethodik zur Analyse, Dokumentation und Verbesserung von Supply-Chain-Prozessen. SAP-Hands-on-Erfahrung wird nicht vorausgesetzt oder behauptet; vorhanden sind anschlussfähiges Prozessverständnis, Systemlogik und hohe Einarbeitungsbereitschaft in digitale Arbeitsumgebungen.

## Kompetenzschwerpunkte
- Temperaturgeführte Logistik und operative Supply-Chain-Prozesse
- Wareneingang, Kommissionierung, Warenausgang und Prozesssteuerung
- Strukturierte Prozessanalyse und Qualitätsorientierung
- KI-gestützte Dokumentation, Entscheidungsunterstützung und Arbeitsstrukturierung
- Schnittstellenverständnis zwischen operativem Bereich, Qualität, Disposition und digitaler Systemlogik

## Wahrheitsgrenze / Nicht behaupten
- Keine direkte SAP-Hands-on-Erfahrung behaupten.
- Keine Zertifizierungen oder Tool-Expertise erfinden.
- KI-Kompetenz als methodische Prozesskompetenz formulieren, nicht als autonome Entscheidungsrolle.
```

---

## 9. Quality Gate

A professional profile output passes only if:

- [ ] actual profile text is present
- [ ] profile text is the primary output
- [ ] profile is short enough for application or recruiter use
- [ ] truth-boundary is preserved
- [ ] no false SAP hands-on claim appears
- [ ] no unsupported credentials are invented
- [ ] KI competence is framed as process support, not decision ownership
- [ ] optional variants do not replace the main profile
- [ ] output is professional and recruiter-facing

If no usable profile text is present:

```yaml
routing_quality: "fail"
```

If profile exists but is buried under dossier structure:

```yaml
routing_quality: "partial"
```

If the profile is direct, truthful, and ready to use:

```yaml
routing_quality: "pass"
```

---

## 10. Corrected Masterprompt Snippet

```text
If the user explicitly asks for Bewerbungsprofil, Kurzprofil, Profiltext, Lebenslaufprofil, Recruiter-Profil, professionelles Profil, Bewerbungstext, CV-Profil, Karriereprofil, or professional positioning text, route to PROFESSIONAL_PROFILE_BUILDER.
Generate the usable profile text as the primary output.
Do not generate an Executive Use-Case Dossier, portfolio blueprint, management training document, or process matrix as the primary output unless explicitly requested.
Preserve truthful professional positioning: do not invent SAP hands-on experience, certifications, formal titles, tool expertise, or measurable achievements. If SAP hands-on is explicitly excluded, state process understanding, interface logic, system readiness, and willingness to learn instead.
```

---

## 11. Governance

This rule must preserve:

```text
Human remains owner.
AI remains tool.
Professional claims must be truthful.
No SAP hands-on claim unless explicitly verified.
Career-critical outputs require truth-boundary review.
```

---

## 12. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Professional profile routing rule created after runtime PDF test showed career-profile request was routed into Executive Use-Case Dossier instead of direct short profile text. | Operator Fischer |
