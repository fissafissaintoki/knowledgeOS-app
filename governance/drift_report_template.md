# KnowledgeOS Drift Report Template

**Artifact ID:** KOS-GOV-0002  
**Title:** KnowledgeOS Drift Report Template  
**System:** KnowledgeOS / GosseOS / Operator Fischer  
**Version:** v1.0  
**Status:** canonical  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This template is used to identify, classify, and resolve knowledge drift across KnowledgeOS / GosseOS / Operator Fischer artifacts.

Drift means loss of consistency, traceability, correctness, or reuse quality over time.

Core principle:

```text
Human remains owner.
AI remains tool.
KnowledgeOS manages artifact consistency.
GosseOS manages execution logic.
Governance prevents uncontrolled drift.
```

---

## 2. Drift Report Metadata

```yaml
drift_report:
  report_id: "DRIFT-YYYYMMDD-001"
  reviewed_artifact_id: "KOS-XXXX"
  reviewed_artifact_title: "Artifact title"
  reviewed_artifact_version: "vX.Y"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "YYYY-MM-DD"
  review_trigger: "scheduled_review | new_artifact | version_change | conflict_detected | terminology_scan | release_gate"
  source_locations:
    - "GitHub path / file / memory / chat / PDF / note"
  linked_artifacts_checked:
    - "KOS-XXXX"
  overall_drift_risk: "low | medium | high | conflict"
  release_recommendation: "keep | update | merge | deprecate | archive | block"
```

---

## 3. Drift Categories

| Drift Type | Description | Typical Signal | Severity |
|---|---|---|---|
| Terminology Drift | Terms are used inconsistently or old terms reappear | Deprecated terms, unclear naming | medium/high |
| Version Drift | Older versions are used instead of current ones | v1.0 used while v1.2 exists | medium |
| Pattern Drift | Core logic changes without traceability | New pattern conflicts with canonical pattern | high |
| Source Drift | Source becomes unclear, stale, or unverifiable | Missing path, old chat, no commit | high |
| Governance Drift | Rules weaken or owner logic is bypassed | AI framed as decision-owner | high |
| Output Drift | Output no longer follows required artifact style | Missing TOC, no schema, weak structure | medium |
| Scope Drift | Artifact expands beyond intended purpose | Prompt becomes architecture without reclassification | medium |
| Public/Private Drift | Internal system language leaks into public output | Private architecture terms in product copy | medium/high |
| Credential Drift | Professional claims become overstated | False SAP hands-on claim | high |
| Automation Drift | Tool authority becomes too broad | Unsupervised control wording | high |

---

## 4. Drift Scan Checklist

### 4.1 Terminology Drift

Check against `registry/deprecated_terms.yaml`.

- [ ] No deprecated term is used as an active primary term.
- [ ] `AgentOS` is not used as the active main system name.
- [ ] Deprecated terms are labelled as legacy, archived, deprecated, or historical.
- [ ] Replacement terms are applied correctly.
- [ ] Public-facing language avoids unnecessary internal terminology.
- [ ] The distinction between Prompt, Protocol, Skill, Workflow, and Architecture is preserved.

Finding:

```yaml
terminology_drift:
  status: "none | minor | major | conflict"
  deprecated_terms_found:
    - "term"
  replacement_required: true
  recommended_replacement:
    - "replacement term"
  notes: "Short explanation"
```

---

### 4.2 Version Drift

- [ ] Artifact version is current.
- [ ] A newer version does not already exist.
- [ ] Version number changed if content changed materially.
- [ ] Linked artifacts point to current versions.
- [ ] Old versions are marked as deprecated or archived where needed.
- [ ] Change log exists for material changes.

Finding:

```yaml
version_drift:
  status: "none | minor | major | conflict"
  current_version: "vX.Y"
  latest_known_version: "vX.Y"
  outdated_references:
    - "KOS-XXXX"
  required_action: "none | update_version | deprecate_old_version | merge_versions | block_release"
  notes: "Short explanation"
```

---

### 4.3 Pattern Drift

- [ ] Core patterns match canonical architecture.
- [ ] New patterns are linked to existing artifacts.
- [ ] Existing patterns are not redefined without explanation.
- [ ] No conflicting operating logic appears.
- [ ] Mode, protocol, workflow, skill, and architecture layers are not mixed incorrectly.
- [ ] The artifact preserves the standard flow: raw input → problem class → mode → artifact → quality check → reuse.

Finding:

```yaml
pattern_drift:
  status: "none | minor | major | conflict"
  affected_patterns:
    - "Pattern name"
  conflicting_artifacts:
    - "KOS-XXXX"
  required_action: "none | link | rename | split | merge | escalate"
  notes: "Short explanation"
```

---

### 4.4 Source Drift

- [ ] Source location is traceable.
- [ ] GitHub path, commit, file name, chat source, memory baseline, or document title is named.
- [ ] Source is not stale for its use case.
- [ ] External factual claims have sources where required.
- [ ] Source type is compatible with intended reuse.
- [ ] No unverified source is treated as source of truth.

Finding:

```yaml
source_drift:
  status: "none | minor | major | conflict"
  source_status: "traceable | partial | unclear | missing"
  missing_sources:
    - "source reference"
  required_action: "none | add_source | refresh_source | verify_source | block_release"
  notes: "Short explanation"
```

---

### 4.5 Governance Drift

- [ ] Human owner remains accountable.
- [ ] AI is not framed as final decision-maker.
- [ ] Automation remains bounded and auditable.
- [ ] Risk level matches artifact impact.
- [ ] Governance notes are specific.
- [ ] Reuse rules include use and non-use cases.
- [ ] High-impact claims require evidence or explicit assumption labels.
- [ ] Professional claims remain truthful and bounded.

Finding:

```yaml
governance_drift:
  status: "none | minor | major | conflict"
  affected_rules:
    - "Rule name"
  risk_level: "low | medium | high"
  required_action: "none | add_note | restrict_reuse | owner_review | block_release"
  notes: "Short explanation"
```

---

### 4.6 Output Drift

- [ ] Output follows the expected artifact format.
- [ ] Required sections are present.
- [ ] Structure is reusable by another model or operator.
- [ ] Tables, checklists, or YAML blocks are clear.
- [ ] Quality check exists.
- [ ] Reuse pathway is explicit.
- [ ] For long PDFs/documents, navigation or table of contents is planned where technically possible.

Finding:

```yaml
output_drift:
  status: "none | minor | major | conflict"
  missing_sections:
    - "section name"
  required_action: "none | restructure | add_quality_check | add_navigation | block_release"
  notes: "Short explanation"
```

---

## 5. Drift Severity Model

| Severity | Meaning | Required Action |
|---|---|---|
| none | No relevant drift found | Keep current status |
| minor | Small metadata or wording issue | Update artifact or add governance note |
| major | Meaning, reuse, or source risk affected | Manual review before reuse |
| conflict | Contradicts source of truth, uses blocked terms, or lacks traceable source | Block release until resolved |

---

## 6. Drift Scoring

Use this simple scoring model when a numeric score helps prioritization.

| Category | Score |
|---|---:|
| No issue | 0 |
| Minor issue | 1 |
| Major issue | 2 |
| Conflict/blocker | 3 |

```yaml
drift_score:
  terminology_drift: 0
  version_drift: 0
  pattern_drift: 0
  source_drift: 0
  governance_drift: 0
  output_drift: 0
  total_score: 0
  risk_band: "green | yellow | orange | red"
```

Risk bands:

| Total Score | Band | Meaning | Action |
|---:|---|---|---|
| 0-2 | green | Stable | Keep or approve |
| 3-5 | yellow | Minor drift | Update before next release |
| 6-9 | orange | Significant drift | Manual review required |
| 10+ | red | Critical drift | Block release |

Any single blocker sets band to `red` regardless of total score.

---

## 7. Blocker Criteria

Set report to `conflict` if any condition is true:

- [ ] Artifact contradicts a canonical artifact without explanation.
- [ ] Artifact uses a high-severity deprecated term as active terminology.
- [ ] Artifact has no traceable source.
- [ ] Artifact duplicates another artifact without merge logic.
- [ ] Artifact claims human decision authority belongs to AI.
- [ ] Artifact enables unbounded or unaudited automation.
- [ ] Artifact contains professional claims that may be false or overstated.
- [ ] Artifact cannot be reproduced from its metadata.
- [ ] Artifact lacks reuse rules but is proposed for reusable status.

Blocker record:

```yaml
blocker:
  exists: true
  blocker_type: "terminology | source | governance | version | pattern | output | credential | automation"
  description: "What blocks release?"
  required_resolution: "What must happen before release?"
```

---

## 8. Resolution Actions

| Action | Meaning | When to Use |
|---|---|---|
| keep | No change required | Low/no drift |
| update | Minor correction needed | Metadata, wording, missing link |
| link | Add relation to existing artifact | Related artifact exists |
| split | Separate mixed concepts | Prompt vs architecture conflict |
| merge | Combine duplicate artifacts | Duplicate entries exist |
| rename | Correct terminology | Deprecated or unclear term |
| deprecate | Mark older artifact as replaced | Newer version exists |
| archive | Retain only for history | No active use expected |
| block | Stop release | Conflict or high risk |

---

## 9. Full Drift Report Template

Copy this block for each review:

```yaml
drift_report:
  report_id: "DRIFT-YYYYMMDD-001"
  reviewed_artifact_id: "KOS-XXXX"
  reviewed_artifact_title: "Artifact title"
  reviewed_artifact_version: "vX.Y"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "YYYY-MM-DD"
  review_trigger: "scheduled_review | new_artifact | version_change | conflict_detected | terminology_scan | release_gate"

  source_locations:
    - "source 1"
  linked_artifacts_checked:
    - "KOS-XXXX"

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
    items:
      - blocker_type: ""
        description: ""
        required_resolution: ""

  recommendation:
    release_recommendation: "keep | update | merge | deprecate | archive | block"
    proposed_status: "draft | checked | verified | canonical | deprecated | archived | conflict"
    required_actions:
      - "Action 1"
      - "Action 2"
    governance_notes: "Short explanation"

  owner_decision:
    decided_by: "Operator Fischer"
    decision_date: "YYYY-MM-DD"
    approved_action: "keep | update | merge | deprecate | archive | block"
    notes: ""
```

---

## 10. Example Mini Report

```yaml
drift_report:
  report_id: "DRIFT-20260519-001"
  reviewed_artifact_id: "KOS-0010"
  reviewed_artifact_title: "AgentOS Legacy Naming"
  reviewed_artifact_version: "legacy"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "2026-05-19"
  review_trigger: "terminology_scan"

  findings:
    terminology_drift:
      status: "major"
      notes: "AgentOS must remain archive-only and must not re-enter active system naming."
    version_drift:
      status: "none"
      notes: "Legacy status is intentional."
    pattern_drift:
      status: "minor"
      notes: "Must be mapped to Agent-Layer, Protocol Layer, GosseOS, or KnowledgeOS depending on context."
    source_drift:
      status: "none"
      notes: "Registered in deprecated_terms.yaml and artifacts.yaml."
    governance_drift:
      status: "none"
      notes: "Replacement policy exists."
    output_drift:
      status: "none"
      notes: "Archive-only output rule is clear."

  drift_score:
    terminology_drift: 2
    version_drift: 0
    pattern_drift: 1
    source_drift: 0
    governance_drift: 0
    output_drift: 0
    total_score: 3
    risk_band: "yellow"

  blockers:
    exists: false
    items: []

  recommendation:
    release_recommendation: "keep"
    proposed_status: "deprecated"
    required_actions:
      - "Keep AgentOS as archive-only terminology."
      - "Use GosseOS / KnowledgeOS / Agent-Layer as active replacements."
    governance_notes: "Deprecated term is controlled and traceable."
```

---

## 11. Standard Review Flow

```text
Select Artifact
  ↓
Check Source
  ↓
Scan Deprecated Terms
  ↓
Compare With Canonical Artifacts
  ↓
Check Version
  ↓
Check Core Patterns
  ↓
Check Governance Rules
  ↓
Score Drift
  ↓
Decide: Keep / Update / Merge / Deprecate / Archive / Block
```

---

## 12. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Initial KnowledgeOS drift report template created. | Operator Fischer |
