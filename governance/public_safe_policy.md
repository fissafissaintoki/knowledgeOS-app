# KnowledgeOS Public-Safe Policy

**Artifact ID:** KOS-GOV-0006  
**Title:** KnowledgeOS Public-Safe Policy  
**System:** KnowledgeOS / GosseOS / Operator Fischer  
**Version:** v1.0  
**Status:** canonical  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This policy defines how internal KnowledgeOS / GosseOS / Operator Fischer material may be adapted for public-facing outputs.

Public-facing outputs include:

- websites
- product pages
- README files intended for external readers
- LinkedIn posts
- Skool/community posts
- portfolios
- recruiter documents
- public PDFs
- public prompts
- presentations
- product descriptions

Core principle:

```text
Internal architecture may be powerful.
Public language must be clear, credible, safe, and bounded.
Human remains owner.
AI remains tool.
```

---

## 2. Public-Safe Classification

| Class | Meaning | Use |
|---|---|---|
| `internal` | Private architecture, governance, or operator logic | Internal only |
| `public_safe` | Can be used externally after review | Websites, posts, docs |
| `restricted` | Requires explicit owner review before use | Career, product, strategic, sensitive docs |
| `archive_only` | Historical or deprecated only | Not for active public use |
| `blocked` | Must not be used publicly | Unsafe, false, unclear, or conflicting material |

---

## 3. Public-Safe Gates

Before public use, check:

- [ ] No deprecated internal term is used as active public terminology.
- [ ] Internal architecture names are explained or simplified.
- [ ] No unsupported professional claims appear.
- [ ] No false tool access, certification, or experience claim appears.
- [ ] No AI system is framed as final owner or decision-maker.
- [ ] No unbounded automation or full-control language appears.
- [ ] No sensitive private architecture detail is exposed unnecessarily.
- [ ] No source is presented as fact if it is only assumption or draft.
- [ ] Public reader can understand the content without private context.
- [ ] Claims are credible and proportionate.

---

## 4. Internal-to-Public Rewrite Rules

| Internal Term | Public-Safe Rewrite |
|---|---|
| GosseOS | AI operating framework / structured execution framework |
| KnowledgeOS | structured knowledge system / artifact registry |
| Operator Fischer | human operator / system architect / workflow designer |
| Governance Gate | approval checkpoint / quality gate |
| Runtime Router | routing logic / workflow routing |
| Mode Engine | working-mode selector |
| Artifact Engine | structured output generator |
| Drift Control | consistency control |
| Multi-Model Cooperation Protocol | multi-tool collaboration workflow |
| Agent-Layer | specialized assistant layer |
| Masterprompt | reusable instruction template |
| Canonical artifact | approved reference version |

Rule:

```text
Use internal terms in internal files.
Use public-safe rewrites when speaking to external readers unless the internal term is intentionally being introduced and explained.
```

---

## 5. Blocked Public Claims

Do not publish claims that imply:

- AI owns final decisions.
- AI has autonomous full control without human approval.
- Operator Fischer has SAP hands-on experience unless explicitly verified.
- Internal prototypes are production-certified systems.
- Memory baselines are verified sources of truth without review.
- Unmeasured KPI assumptions are measured results.
- Deprecated terms are active product names.
- GitHub or tool access exists where it does not.
- A repository feature is complete when only a draft exists.

---

## 6. KPI and Claim Labelling

Use labels:

| Label | Meaning |
|---|---|
| `[FAKT]` | Directly verified or user-provided fact |
| `[ANNAHME]` | Plausible but not measured or verified |
| `[HYPOTHESE]` | Testable statement about expected effect |
| `[MESSWERT]` | Actually measured data point |
| `[OFFEN]` | Requires validation |

Public-safe rule:

```text
Never convert assumptions into measured results.
Never convert hypotheses into facts.
```

---

## 7. Career and Positioning Rules

For recruiter, CV, portfolio, LinkedIn, and application outputs:

- [ ] Do not claim direct SAP hands-on experience.
- [ ] Use: process understanding, interface understanding, structured system thinking, readiness to learn SAP-related workflows.
- [ ] Keep logistics experience factual and grounded.
- [ ] Separate operational experience from AI/system architecture work.
- [ ] Do not overstate leadership title, certifications, or tool access.
- [ ] Make domain transfer credible, not inflated.

Safe phrasing:

```text
Er verbindet langjährige operative Logistikerfahrung mit strukturierter KI-gestützter Entscheidungsunterstützung.
```

Unsafe phrasing:

```text
Er ist SAP-Experte und KI-Entscheider für automatisierte Logistikfreigaben.
```

---

## 8. Product and Website Rules

For Prompterator or other public product copy:

- [ ] Explain what the tool does in simple terms.
- [ ] Avoid exposing private governance internals unless relevant.
- [ ] Do not promise autonomous execution.
- [ ] Do not claim enterprise-grade compliance unless validated.
- [ ] Do not claim model access or integrations that are not implemented.
- [ ] State prototype, beta, or concept status where applicable.
- [ ] Keep output claims specific and testable.

Safe phrasing:

```text
Prompterator converts rough input into structured prompts, workflows, and reusable work artifacts.
```

Unsafe phrasing:

```text
Prompterator autonomously controls all AI systems and guarantees perfect business decisions.
```

---

## 9. Public-Safe Review Template

```yaml
public_safe_review:
  review_id: "PUBSAFE-YYYYMMDD-001"
  artifact_id: "KOS-XXXX"
  artifact_title: "Artifact title"
  reviewed_output_type: "website | post | portfolio | PDF | README | presentation | prompt | product copy"
  reviewer: "Operator Fischer / AI-assisted review"
  review_date: "YYYY-MM-DD"

  checks:
    deprecated_terms_removed: true
    internal_terms_explained_or_rewritten: true
    claims_supported: true
    assumptions_labelled: true
    no_false_credentials: true
    no_unbounded_automation_claims: true
    human_owner_principle_preserved: true
    public_reader_can_understand: true

  risk_class: "low | medium | high | critical"
  decision: "public_safe | revise_before_public | restricted | blocked"
  required_revisions:
    - "Revision 1"
  notes: "Short explanation"
```

---

## 10. Release Decision

| Finding | Decision |
|---|---|
| Internal terms clear and appropriate | public_safe |
| Internal terms unclear but fixable | revise_before_public |
| Career/product claims need owner review | restricted |
| False claim, deprecated active term, or unsafe automation | blocked |

---

## 11. Standard Public-Safe Flow

```text
Select Internal Artifact
  ↓
Check Deprecated Terms
  ↓
Rewrite Internal Terminology if Needed
  ↓
Check Claims and Assumptions
  ↓
Check Human Owner Principle
  ↓
Check Audience Clarity
  ↓
Assign Public-Safe Decision
  ↓
Release / Revise / Restrict / Block
```

---

## 12. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Initial KnowledgeOS public-safe policy created. | Operator Fischer |
