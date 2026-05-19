# KnowledgeOS Release Records

**Purpose:** Store release decisions for KnowledgeOS / GosseOS / Operator Fischer artifacts.

This folder contains release records created when artifacts move between states such as:

- `draft`
- `checked`
- `verified`
- `canonical`
- `deprecated`
- `archived`
- `conflict`

Template reference:

```text
/governance/release_policy.md
```

---

## Recommended File Naming

```text
RELEASE-YYYYMMDD-001.yaml
```

Example:

```text
RELEASE-20260519-001.yaml
```

---

## Release Record Template

```yaml
release_record:
  release_id: "RELEASE-YYYYMMDD-001"
  artifact_id: "KOS-XXXX"
  artifact_title: "Artifact title"
  previous_status: "draft | active | canonical | deprecated | archived | conflict"
  previous_verification_status: "unchecked | checked | verified | conflict"
  proposed_status: "draft | active | canonical | deprecated | archived"
  proposed_verification_status: "unchecked | checked | verified | conflict"
  release_type: "new | update | canonical_release | deprecation | archive | conflict_resolution"
  version_before: "vX.Y"
  version_after: "vX.Y"
  source_check: "pass | fail | partial"
  terminology_check: "pass | fail | partial"
  drift_check: "green | yellow | orange | red"
  blocker_exists: false
  approved_by: "Operator Fischer"
  approval_date: "YYYY-MM-DD"
  required_actions:
    - "Action 1"
  governance_notes: "Short release explanation."
```

---

## Canonical Rule

```text
AI may recommend a status.
Only the human owner approves canonical release.
```
