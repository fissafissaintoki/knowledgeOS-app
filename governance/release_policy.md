# KnowledgeOS Release Policy

**Artifact ID:** KOS-GOV-0003  
**Title:** KnowledgeOS Release Policy  
**System:** KnowledgeOS / GosseOS / Operator Fischer  
**Version:** v1.0  
**Status:** canonical  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This policy defines when and how KnowledgeOS / GosseOS / Operator Fischer artifacts may move between release states such as `draft`, `checked`, `verified`, `canonical`, `deprecated`, and `archived`.

The goal is to prevent uncontrolled drift, preserve reproducibility, and ensure that only reviewed, traceable, and reusable artifacts become canonical.

Core principle:

```text
Human remains owner.
AI remains tool.
KnowledgeOS manages artifacts.
GosseOS manages execution logic.
Governance controls release status.
```

---

## 2. Release States

| State | Meaning | Reuse Permission |
|---|---|---|
| `raw` | Unprocessed input or capture | No reuse except extraction |
| `draft` | Structured but incomplete artifact | Internal work only |
| `checked` | Basic validation passed | Limited reuse with caution |
| `verified` | Schema, source, terminology, and drift checks passed | Reusable |
| `canonical` | Approved source of truth | Default reference |
| `deprecated` | Replaced or outdated artifact | Archive/migration only |
| `archived` | Historical record | Reference only |
| `conflict` | Blocked because of contradiction, missing source, or governance risk | No reuse |

---

## 3. Release Authority

| Actor | Authority |
|---|---|
| Operator Fischer | Final owner, approval authority, release decision |
| AI assistant | Analysis, structuring, validation, comparison, recommendation |
| Codex / tooling | Technical implementation under bounded task scope |
| Governance files | Rules, checks, release criteria |

Non-negotiable rule:

```text
AI may recommend a status.
Only the human owner approves canonical release.
```

---

## 4. Required Files for Release Control

A release decision must reference these governance files where applicable:

| File | Purpose |
|---|---|
| `registry/artifact_schema.yaml` | Defines required fields and allowed values |
| `registry/artifacts.yaml` | Master index of registered artifacts |
| `registry/deprecated_terms.yaml` | Prevents terminology drift |
| `governance/verification_checklist.md` | Defines artifact review process |
| `governance/drift_report_template.md` | Defines drift classification and scoring |
| `governance/release_policy.md` | Defines release status transitions |

---

## 5. Status Transition Rules

### 5.1 Raw → Draft

Allowed when:

- [ ] Raw input has been captured.
- [ ] Artifact purpose is identifiable.
- [ ] Initial title or working name exists.
- [ ] Owner is known.

Required action:

```yaml
status: draft
verification_status: unchecked
```

---

### 5.2 Draft → Checked

Allowed when:

- [ ] Required metadata fields are present.
- [ ] Artifact type is classified.
- [ ] Source location is at least partially traceable.
- [ ] Reuse rules exist.
- [ ] No high-severity deprecated term is used as active terminology.
- [ ] No obvious duplicate or contradiction is unresolved.

Required action:

```yaml
status: active
verification_status: checked
```

If the artifact is not intended for active use:

```yaml
status: draft
verification_status: checked
```

---

### 5.3 Checked → Verified

Allowed when:

- [ ] Schema validation passed.
- [ ] Source validation passed.
- [ ] Deprecated-term scan passed.
- [ ] Drift check completed.
- [ ] Linked artifacts were reviewed.
- [ ] Risk level is assigned.
- [ ] Drift risk is assigned.
- [ ] Governance notes are specific.
- [ ] Reuse and non-use conditions are clear.

Required action:

```yaml
verification_status: verified
```

Recommended action:

```yaml
status: active
```

---

### 5.4 Verified → Canonical

Allowed only when:

- [ ] Artifact is already verified.
- [ ] Human owner approves canonical status.
- [ ] Source is traceable.
- [ ] Drift risk is low or explicitly accepted.
- [ ] No unresolved blockers exist.
- [ ] No high-severity deprecated term remains active.
- [ ] Artifact has stable terminology.
- [ ] Artifact is reusable as a default source of truth.
- [ ] Replacement impact on existing artifacts has been reviewed.
- [ ] Registry entry in `registry/artifacts.yaml` is updated.

Required action:

```yaml
status: canonical
verification_status: verified
```

Canonical release decision block:

```yaml
release_decision:
  artifact_id: "KOS-XXXX"
  approved_status: "canonical"
  approved_by: "Operator Fischer"
  approval_date: "YYYY-MM-DD"
  conditions:
    - "No unresolved blockers"
    - "Registry updated"
  notes: "Canonical release approved."
```

---

### 5.5 Active / Canonical → Deprecated

Required when:

- [ ] A newer artifact replaces the current artifact.
- [ ] The artifact contains outdated terminology.
- [ ] The artifact conflicts with a newer canonical source.
- [ ] The artifact is still historically useful but no longer active.

Required action:

```yaml
status: deprecated
verification_status: verified
```

Required notes:

```yaml
governance_notes: "Deprecated. Use KOS-XXXX as replacement. Archive-only except migration context."
```

---

### 5.6 Deprecated → Archived

Allowed when:

- [ ] Artifact is no longer operationally relevant.
- [ ] Replacement artifact exists or no replacement is required.
- [ ] Historical value remains.
- [ ] It must not appear in active output routing.

Required action:

```yaml
status: archived
```

---

### 5.7 Any State → Conflict

Required immediately when:

- [ ] Source is missing or not traceable.
- [ ] Artifact ID is duplicated.
- [ ] Artifact contradicts a canonical artifact without explanation.
- [ ] High-severity deprecated term is used as active terminology.
- [ ] AI is framed as final owner or final decision-maker.
- [ ] Professional credentials or experience may be misrepresented.
- [ ] Automation or tool-control language removes human approval.
- [ ] Reuse could create compliance, safety, identity, career, legal, financial, or operational risk.

Required action:

```yaml
status: draft
verification_status: conflict
```

or, for already registered high-risk artifacts:

```yaml
status: active
verification_status: conflict
```

Reuse rule:

```text
Conflict artifacts must not be reused until resolved.
```

---

## 6. Release Gates

### Gate 1 — Metadata Gate

- [ ] Required fields complete.
- [ ] Artifact ID unique.
- [ ] Status valid.
- [ ] Version valid.
- [ ] Owner defined.

Failure result:

```yaml
verification_status: unchecked
```

---

### Gate 2 — Source Gate

- [ ] Source is traceable.
- [ ] Source type is clear.
- [ ] External claims are sourced where needed.
- [ ] Memory-based artifacts identify the memory baseline.
- [ ] GitHub-based artifacts include path or commit where possible.

Failure result:

```yaml
verification_status: conflict
```

---

### Gate 3 — Terminology Gate

- [ ] Deprecated terms checked.
- [ ] Replacements applied where needed.
- [ ] Archive-only terms labelled clearly.
- [ ] Public/private terminology separation preserved.

Failure result:

```yaml
verification_status: conflict
```

---

### Gate 4 — Drift Gate

- [ ] Terminology drift reviewed.
- [ ] Version drift reviewed.
- [ ] Pattern drift reviewed.
- [ ] Source drift reviewed.
- [ ] Governance drift reviewed.
- [ ] Output drift reviewed.

Failure result:

```yaml
verification_status: conflict
```

or:

```yaml
verification_status: checked
status: draft
```

if issues are minor and resolvable.

---

### Gate 5 — Owner Gate

- [ ] Human owner approves status change.
- [ ] High-risk changes are explicitly accepted or rejected.
- [ ] Canonical releases are manually approved.

Failure result:

```yaml
status: active
verification_status: verified
```

Canonical release remains blocked until owner approval.

---

## 7. Versioning Policy

Version format:

```text
vMAJOR.MINOR
```

Examples:

```text
v1.0
v1.1
v2.0
```

Version increment rules:

| Change Type | Version Action |
|---|---|
| Typo, formatting, small metadata correction | No version increment or patch note |
| Minor wording or clarification | Increase MINOR if meaning changes |
| New section, new rule, changed reuse logic | Increase MINOR |
| Breaking change, changed architecture, changed governance logic | Increase MAJOR |
| Replacement by new artifact | Deprecate old version and link replacement |

---

## 8. Registry Update Policy

Every released artifact must be reflected in `registry/artifacts.yaml`.

Required registry actions:

- [ ] Add new artifact entry.
- [ ] Update status.
- [ ] Update version.
- [ ] Update linked artifacts.
- [ ] Update drift risk.
- [ ] Update verification status.
- [ ] Add governance notes.
- [ ] Update index views if needed.

If an artifact is not in the registry, it cannot be canonical.

---

## 9. Public-Safe Release Policy

An artifact may be used in public-facing content only when:

- [ ] It does not expose internal-only governance or private architecture unnecessarily.
- [ ] It does not use deprecated internal terminology as public terminology.
- [ ] It does not claim unsupported professional credentials.
- [ ] It does not imply AI owns decisions.
- [ ] It is understandable without private context.
- [ ] It has been classified as public-safe or adapted for public use.

Classification:

```yaml
reuse_class: "internal | public-safe | restricted | archive-only"
```

---

## 10. Release Decision Matrix

| Finding | Decision |
|---|---|
| Missing metadata | Keep as `draft` |
| Missing source | Set `conflict` |
| Duplicate ID | Set `conflict` |
| Deprecated term active | Set `conflict` |
| Minor terminology issue | Update before verification |
| Medium drift | Keep `checked`, require review |
| High drift | Block canonical release |
| Verified but no owner approval | Keep `verified`, not canonical |
| Owner-approved and stable | Set `canonical` |
| Replaced by newer artifact | Set `deprecated` |
| Historical only | Set `archived` |

---

## 11. Standard Release Flow

```text
Raw Input
  ↓
Draft Artifact
  ↓
Schema Check
  ↓
Source Check
  ↓
Deprecated-Term Scan
  ↓
Drift Report
  ↓
Verification Checklist
  ↓
Registry Update
  ↓
Owner Release Decision
  ↓
Status: checked / verified / canonical / deprecated / archived / conflict
```

---

## 12. Release Record Template

Use this block for release decisions:

```yaml
release_record:
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

## 13. Conflict Resolution Policy

A `conflict` artifact may return to `draft`, `checked`, or `verified` only after:

- [ ] Conflict reason is documented.
- [ ] Source has been corrected or added.
- [ ] Deprecated terminology has been replaced or labelled.
- [ ] Contradiction with canonical artifact has been resolved.
- [ ] Risk classification has been updated.
- [ ] Reuse rules have been clarified.
- [ ] Owner has accepted the resolution.

Conflict resolution block:

```yaml
conflict_resolution:
  artifact_id: "KOS-XXXX"
  conflict_type: "source | terminology | version | pattern | governance | output | credential | automation"
  resolution_summary: "What was fixed?"
  resolved_by: "Operator Fischer / AI-assisted review"
  resolution_date: "YYYY-MM-DD"
  new_status: "draft | checked | verified | canonical | deprecated | archived"
  notes: ""
```

---

## 14. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Initial KnowledgeOS release policy created. | Operator Fischer |
