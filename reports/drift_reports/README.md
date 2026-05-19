# KnowledgeOS Drift Reports

**Purpose:** Store formal drift reports for KnowledgeOS / GosseOS / Operator Fischer artifacts and patterns.

Drift reports are required when an artifact may be affected by:

- terminology drift
- version drift
- pattern drift
- source drift
- governance drift
- output drift
- public/private drift
- professional claim drift
- automation drift

Template reference:

```text
/governance/drift_report_template.md
```

---

## Recommended File Naming

```text
DRIFT-YYYYMMDD-001.yaml
```

Example:

```text
DRIFT-20260519-001.yaml
```

---

## Drift Report Template

```yaml
drift_report:
  report_id: "DRIFT-YYYYMMDD-001"
  reviewed_artifact_id: "KOS-XXXX"
  reviewed_artifact_title: "Artifact title"
  reviewed_artifact_version: "vX.Y"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "YYYY-MM-DD"
  review_trigger: "scheduled_review | new_artifact | version_change | conflict_detected | terminology_scan | release_gate"

  findings:
    terminology_drift:
      status: "none | minor | major | conflict"
      notes: ""
    version_drift:
      status: "none | minor | major | conflict"
      notes: ""
    pattern_drift:
      status: "none | minor | major | conflict"
      notes: ""
    source_drift:
      status: "none | minor | major | conflict"
      notes: ""
    governance_drift:
      status: "none | minor | major | conflict"
      notes: ""
    output_drift:
      status: "none | minor | major | conflict"
      notes: ""

  drift_score:
    terminology_drift: 0
    version_drift: 0
    pattern_drift: 0
    source_drift: 0
    governance_drift: 0
    output_drift: 0
    total_score: 0
    risk_band: "green | yellow | orange | red"

  blockers:
    exists: false
    items: []

  recommendation:
    release_recommendation: "keep | update | merge | deprecate | archive | block"
    proposed_status: "draft | checked | verified | canonical | deprecated | archived | conflict"
    required_actions:
      - "Action 1"
    governance_notes: "Short explanation"
```

---

## Rule

```text
If drift affects source, governance, automation, public output, or professional claims, create a drift report before release.
```
