# KnowledgeOS Verification Records

**Purpose:** Store formal verification records for KnowledgeOS / GosseOS / Operator Fischer artifacts.

Verification records document whether an artifact has passed schema, source, terminology, drift, risk, reuse, and governance checks.

Template reference:

```text
/governance/verification_checklist.md
```

---

## When To Create A Verification Record

Create a verification record when:

- a new artifact is added to `registry/artifacts.yaml`
- an artifact moves from `draft` to `checked`
- an artifact moves from `checked` to `verified`
- an artifact is proposed for `canonical`
- a conflict is detected or resolved
- source traceability changes
- deprecated terminology is replaced
- public-safe review affects release status
- a governance file changes materially

---

## Recommended File Naming

```text
VERIFY-YYYYMMDD-001.yaml
```

Example:

```text
VERIFY-20260519-001.yaml
```

---

## Verification Record Template

```yaml
verification_record:
  verification_id: "VERIFY-YYYYMMDD-001"
  artifact_id: "KOS-XXXX"
  artifact_title: "Artifact title"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "YYYY-MM-DD"

  artifact_metadata:
    artifact_type: "Prompt | SOP | Framework | Dossier | PDF | Code | Research Note | Checklist | Workflow | Protocol | Architecture | Governance Rule"
    current_status: "draft | active | canonical | deprecated | archived | conflict"
    current_verification_status: "unchecked | checked | verified | conflict"
    version: "vX.Y"
    source_location: "GitHub path / memory / chat / file / external source"

  checks:
    schema_check: "pass | partial | fail"
    source_check: "pass | partial | fail"
    terminology_check: "pass | partial | fail"
    drift_check: "green | yellow | orange | red"
    risk_check: "low | medium | high | critical"
    reuse_rule_check: "pass | partial | fail"
    governance_check: "pass | partial | fail"
    public_safe_check: "pass | partial | fail | not_applicable"

  blockers:
    exists: false
    items:
      - blocker_type: "source | terminology | drift | governance | public_safe | professional_claim | automation | other"
        description: ""
        required_resolution: ""

  decision:
    proposed_status: "draft | active | canonical | deprecated | archived | conflict"
    proposed_verification_status: "unchecked | checked | verified | conflict"
    release_recommendation: "approve | verify_first | owner_review | block"
    owner_approval_required: true

  required_actions:
    - "Action 1"

  governance_notes: "Short explanation of the verification decision."
```

---

## Verification Status Meaning

| Verification Status | Meaning |
|---|---|
| `unchecked` | Captured but not reviewed. |
| `checked` | Basic metadata, source, and terminology check passed. |
| `verified` | Schema, source, terminology, drift, risk, and reuse checks passed. |
| `conflict` | Artifact is blocked by unresolved source, terminology, governance, or drift issue. |

---

## Rule

```text
No verified or canonical artifact without a traceable verification basis.
```
