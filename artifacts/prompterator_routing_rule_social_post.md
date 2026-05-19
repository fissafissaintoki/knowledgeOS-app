# Prompterator Routing Rule — Social Post Builder

**Artifact ID:** KOS-0022  
**Title:** Prompterator Routing Rule — Social Post Builder  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Workflow / Product Rule  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This rule fixes the runtime routing issue found in Proof-of-Work 006.

If the user explicitly asks for a LinkedIn post, social post, community post, Skool post, comment, or Beitrag, Prompterator must not generate a portfolio-style use case or PDF blueprint as the main output.

It must generate the requested public-facing social text first.

---

## 2. Trigger Rule

When user input contains any of the following signals:

```text
LinkedIn-Post
LinkedIn Post
Post
Beitrag
Kommentar
Social-Media-Text
Social Media Text
Skool-Post
Skool Post
Community-Post
Community Post
Thread
Antwort auf einen Beitrag
Kommentiere den Beitrag
```

Prompterator must route to:

```yaml
mode: "SOCIAL_POST_BUILDER"
artifact_type: "Social Post"
output_style: "public_safe_business_post"
```

---

## 3. Negative Rule

When explicit social-post intent is detected, do **not** output as the primary structure:

- portfolio summary
- use-case PDF blueprint
- business dossier
- KPI-heavy consulting document
- long governance framework
- internal KnowledgeOS / GosseOS explanation unless requested
- generic analysis without an actual post draft

Allowed secondary elements after the post:

- optional variants
- short rationale
- quality check
- public-safe notes
- hook alternatives
- CTA alternatives

---

## 4. Required Output Priority

Primary output must be the finished post.

Correct order:

```text
# LinkedIn Post / Social Post

## Post Draft
...

## Varianten optional
...

## Qualitätscheck optional
...
```

Incorrect order:

```text
# Problemklasse
# Artefakt-Blueprint
# Portfolio-Zusammenfassung
# Use-Case-Titel
...
```

---

## 5. Required Output Shape

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

## 6. Required Social-Post Components

A social post output must include:

1. Hook / Einstieg
2. Clear thesis
3. Main argument
4. Practical relevance
5. Reader-facing language
6. Optional call to action or discussion question
7. Public-safe wording
8. No unsupported numbers unless labelled
9. No unnecessary internal terminology
10. No hidden governance overloading

---

## 7. Public-Safe Rules

For public posts, Prompterator must:

- avoid unverified metrics
- avoid exaggerated claims
- avoid internal-only system language unless explained
- avoid unsupported authority claims
- keep claims proportionate
- keep wording understandable for external readers
- preserve human-owner principle where relevant

---

## 8. Domain-Specific Rule — AI / Mittelstand / Prozesse

If input contains:

```text
KI + Mittelstand + Prozesse
```

or semantically similar wording, the post should emphasize:

- process-first thinking
- tool selection as consequence, not starting point
- operational fit
- employee adoption
- data and responsibility clarity
- measurable pilot logic
- no AI hype

Preferred message:

```text
KI scheitert selten an fehlenden Tools. Sie scheitert häufiger an unklaren Prozessen.
```

---

## 9. Corrected Output Example

```text
# LinkedIn Post

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

## 10. Quality Gate

A social-post output passes only if:

- [ ] actual post draft is present
- [ ] post is the primary output
- [ ] topic is clearly translated into audience-facing language
- [ ] no use-case/portfolio structure dominates
- [ ] no unsupported KPI claim appears
- [ ] public-safe wording is used
- [ ] optional quality check does not replace the post itself

If no finished post draft is present:

```yaml
routing_quality: "fail"
```

If post draft is present but weak:

```yaml
routing_quality: "partial"
```

If the post draft is ready to use and public-safe:

```yaml
routing_quality: "pass"
```

---

## 11. Corrected Masterprompt Snippet

```text
If the user explicitly asks for a LinkedIn post, post, Beitrag, comment, social-media text, Skool post, or community post, route to SOCIAL_POST_BUILDER.
Generate the finished post as the primary output.
Do not generate a portfolio, use-case PDF, or business dossier as the primary output.
Optionally add variants, rationale, and a quality check after the post.
Keep the language public-safe, concise, audience-facing, and free of unsupported numerical claims.
```

---

## 12. Governance

This rule must preserve:

```text
Human remains owner.
AI remains tool.
Public claims remain bounded.
No unsupported numbers.
No internal architecture overload unless explicitly requested.
```

---

## 13. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Social-post routing rule created after runtime test showed LinkedIn request routed into Use-Case-PDF mode instead of direct post output. | Operator Fischer |
