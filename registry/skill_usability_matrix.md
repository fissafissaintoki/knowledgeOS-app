# KnowledgeOS Skill Usability Matrix

**Artifact ID:** KOS-0028  
**Title:** KnowledgeOS Skill Usability Matrix  
**System:** KnowledgeOS / GosseOS / Prompterator / Operator Fischer  
**Artifact Type:** Skill Evaluation / Usability Matrix  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This matrix evaluates which extracted skills are immediately usable, which require live regression testing, and which should remain governance or documentation skills.

---

## 2. Usability Levels

| Level | Meaning |
|---|---|
| `ready_now` | Can be used immediately in ChatGPT / manual workflows. |
| `implemented_pending_deploy` | Implemented in code but not yet verified live. |
| `needs_regression` | Requires regression test after deployment. |
| `governance_support` | Supports governance, quality, or release work. |
| `documentation_only` | Useful as reference but not operational by itself. |

---

## 3. Skill Usability Matrix

| Skill ID | Skill | Current Usability | Notes |
|---|---|---|---|
| SKILL-0001 | Intent-to-Artifact Routing | implemented_pending_deploy | Implemented in Prompterator MVP v4; needs live deploy and regression. |
| SKILL-0002 | Codex Handoff Builder | implemented_pending_deploy | Code route exists; regression test required. |
| SKILL-0003 | Social Post Builder | implemented_pending_deploy | Code route exists; regression test required. |
| SKILL-0004 | Research Brief Builder | implemented_pending_deploy | Code route exists; source/evidence behavior must be tested live. |
| SKILL-0005 | SOP Builder | implemented_pending_deploy | Code route exists; cold-chain SOP test required. |
| SKILL-0006 | Professional Profile Builder | implemented_pending_deploy | Code route exists; SAP truth-boundary must be verified. |
| SKILL-0007 | Decision Matrix Builder | implemented_pending_deploy | Code route exists; matrix-first output must be verified. |
| SKILL-0008 | Public-Safe Rewrite | ready_now | Usable immediately for public copy and product positioning. |
| SKILL-0009 | Proof-of-Work Documentation | ready_now | Already used across multiple proof runs. |
| SKILL-0010 | Release and Regression Control | ready_now | Already used for routing batch release documentation. |

---

## 4. Immediate Manual Use

Even before live deployment, these skills can be used manually in ChatGPT or other models:

- Public-Safe Rewrite
- Proof-of-Work Documentation
- Release and Regression Control
- Codex Handoff Builder
- SOP Builder
- Research Brief Builder
- Professional Profile Builder
- Decision Matrix Builder
- Social Post Builder

Manual mode rule:

```text
Use the skill output contract directly, even if Prompterator live deployment is still pending.
```

---

## 5. Prompterator Runtime Use

Runtime use requires:

```text
1. Deploy updated index.html to prompterator.de
2. Confirm MVP v4 is visible
3. Run regression test set
4. Document PROOF-20260519-010
5. Promote runtime status from implemented_pending_deploy to verified_runtime
```

---

## 6. Recommended Next Actions

| Priority | Action |
|---|---|
| High | Deploy updated Prompterator MVP v4 index.html to live site. |
| High | Run six regression tests. |
| High | Document PROOF-20260519-010 routing regression result. |
| Medium | Add skill registry and usability matrix to registry/artifacts.yaml. |
| Medium | Create `registry/skill_to_builder_map.yaml`. |
| Low | Create checkdomain/mobile deployment skill. |

---

## 7. Application Rule

For future Operator Fischer work:

```text
When a user request matches a known skill trigger, apply the skill contract before generating generic output.
```

Example:

```text
User says: LinkedIn-Post
Apply: SKILL-0003 Social Post Builder
Do not apply: Generic Universal Converter
```

---

## 8. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Initial skill usability matrix created after extracting Prompterator routing and governance skills. | Operator Fischer |
