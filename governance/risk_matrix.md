# KnowledgeOS Risk Matrix

**Artifact ID:** KOS-GOV-0005  
**Title:** KnowledgeOS Risk Matrix  
**System:** KnowledgeOS / GosseOS / Operator Fischer  
**Version:** v1.0  
**Status:** canonical  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This matrix defines how KnowledgeOS / GosseOS / Operator Fischer artifacts are classified by operational, governance, source, public, professional, automation, and drift risk.

It supports:

- artifact release decisions
- verification priority
- escalation logic
- public-safe review
- canonical approval
- conflict detection
- audit severity

Core principle:

```text
Human remains owner.
AI remains tool.
Risk classification determines review depth.
High-impact artifacts require owner review.
```

---

## 2. Risk Levels

| Level | Meaning | Default Handling |
|---|---|---|
| `low` | Low impact if wrong or incomplete | Basic review sufficient |
| `medium` | May affect reusable workflows, product copy, positioning, or process logic | Verification and governance notes required |
| `high` | May affect governance, public claims, automation, identity, career, legal, compliance, financial, security, or operational decisions | Owner review required |
| `critical` | May create direct harm, false claims, unsafe delegation, broken canonical source, or major compliance risk | Block until resolved |

---

## 3. Risk Categories

| Category | Description | Typical Artifacts |
|---|---|---|
| Metadata Risk | Incorrect ID, status, version, or links | Registry entries |
| Source Risk | Missing, stale, or unverifiable source | Memory baselines, external facts |
| Terminology Risk | Deprecated or ambiguous terms used actively | Architecture docs, public copy |
| Drift Risk | Pattern, version, source, or governance consistency loss | Pattern maps, workflows |
| Governance Risk | Human-owner, approval, or escalation logic weakened | Release policy, protocols |
| Public-Safe Risk | Internal terms or unsupported claims leak externally | README, product pages, LinkedIn |
| Professional Claim Risk | Experience, credentials, or role claims overstated | CVs, portfolios, applications |
| Automation Risk | Tool authority becomes too broad or unaudited | Codex/Claude handoffs, scripts |
| Operational Risk | Workflow failure could affect execution quality | SOPs, process workflows |
| Security / Compliance Risk | Access, secrets, sensitive data, or policy exposure | Configs, automation, governance |

---

## 4. Scoring Model

Score each relevant category from 0 to 3.

| Score | Meaning |
|---:|---|
| 0 | No relevant risk |
| 1 | Minor issue, easy to correct |
| 2 | Significant issue, review required |
| 3 | Blocker or critical issue |

```yaml
risk_score:
  metadata_risk: 0
  source_risk: 0
  terminology_risk: 0
  drift_risk: 0
  governance_risk: 0
  public_safe_risk: 0
  professional_claim_risk: 0
  automation_risk: 0
  operational_risk: 0
  security_compliance_risk: 0
  total_score: 0
  risk_band: "green | yellow | orange | red"
```

Risk bands:

| Total Score | Band | Meaning | Action |
|---:|---|---|---|
| 0–3 | green | Stable | Basic review |
| 4–7 | yellow | Moderate | Verification required |
| 8–12 | orange | Significant | Owner review required |
| 13+ | red | Critical | Block until resolved |

Any category scored `3` may force red band if it blocks release.

---

## 5. Risk Classification by Artifact Type

| Artifact Type | Default Risk | Notes |
|---|---|---|
| Prompt | low/medium | High if it drives public, career, automation, or governance output |
| SOP | medium | High if operationally critical |
| Framework | medium | High if governance or public positioning is affected |
| Dossier | medium/high | High if recruiter, legal, financial, or public use |
| PDF | low/medium | Depends on audience and claims |
| Code | medium/high | High if it modifies systems, files, access, or data |
| Research Note | low/medium | High if used as source of truth without verification |
| Checklist | low/medium | High if used for release or compliance |
| Workflow | medium/high | High if operational execution depends on it |
| Protocol | medium/high | High if multi-model authority, handoff, or automation is involved |
| Architecture | medium/high | High if it affects system governance or public product logic |
| Governance Rule | high | Owner review required |

---

## 6. Escalation Logic

| Condition | Escalation |
|---|---|
| Missing source | Block release |
| Duplicate artifact ID | Block release |
| Deprecated term active in canonical artifact | Block release |
| AI framed as decision-owner | Block release |
| False or unverified professional claim | Block release |
| Public output from internal architecture | Public-safe review required |
| Automation authority broadened | Owner review required |
| Code changes file system or external services | Owner review required |
| Governance file changed | Owner review required |
| Canonical release requested | Owner approval required |

---

## 7. Risk Review Template

```yaml
risk_review:
  review_id: "RISK-YYYYMMDD-001"
  artifact_id: "KOS-XXXX"
  artifact_title: "Artifact title"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "YYYY-MM-DD"

  category_scores:
    metadata_risk: 0
    source_risk: 0
    terminology_risk: 0
    drift_risk: 0
    governance_risk: 0
    public_safe_risk: 0
    professional_claim_risk: 0
    automation_risk: 0
    operational_risk: 0
    security_compliance_risk: 0

  total_score: 0
  risk_band: "green | yellow | orange | red"
  blocker_exists: false
  blockers:
    - ""

  required_actions:
    - "Action 1"

  release_recommendation: "approve | verify_first | owner_review | block"
  governance_notes: "Short explanation."
```

---

## 8. Default Review Depth

| Risk Band | Required Review |
|---|---|
| green | Schema and source check |
| yellow | Verification checklist and governance notes |
| orange | Drift report, risk review, owner review |
| red | Blocker resolution, owner decision, audit entry |

---

## 9. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Initial KnowledgeOS risk matrix created. | Operator Fischer |
