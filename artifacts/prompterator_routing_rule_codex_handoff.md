# Prompterator Routing Rule — Codex Handoff Prompt

**Artifact ID:** KOS-0020  
**Title:** Prompterator Routing Rule — Codex Handoff Prompt  
**System:** Prompterator / KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Workflow / Product Rule  
**Status:** active  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-05-19  
**Updated:** 2026-05-19  

---

## 1. Purpose

This rule fixes the runtime routing issue found in Proof-of-Work 004.

If the user explicitly asks for a `Codex-Handoff-Prompt`, Prompterator must not generate a portfolio-style use case.

It must generate a direct, implementation-ready Codex handoff prompt.

---

## 2. Trigger Rule

When user input contains any of the following signals:

```text
Codex-Handoff-Prompt
Codex Handoff
Codex Prompt
Handoff Prompt für Codex
Codex Übergabe
Codex soll bauen
Prompt für Codex
Implementation Prompt
Coding Agent Handoff
```

Prompterator must route to:

```yaml
mode: "CODEX_HANDOFF_BUILDER"
artifact_type: "Codex Handoff Prompt"
output_style: "implementation_ready"
```

---

## 3. Negative Rule

When Codex handoff intent is detected, do **not** output:

- portfolio summary as primary format
- generic use-case dossier as primary format
- KPI-heavy business case as primary format
- broad conceptual explanation without implementation tasks
- PDF portfolio structure unless explicitly requested

Allowed secondary elements:

- short context summary
- assumptions
- constraints
- governance notes
- acceptance criteria

---

## 4. Required Output Format

```text
# Codex Handoff Prompt

## Role
You are Codex acting as a senior software engineer.

## Project Goal
...

## Context
...

## Technical Assumptions
...

## Functional Requirements
...

## Non-Functional Requirements
...

## Implementation Tasks
...

## Acceptance Criteria
...

## Test Instructions
...

## Expected Codex Output
...
```

---

## 5. Required Sections

### 5.1 Role

Must define Codex role clearly:

```text
You are Codex acting as a senior software engineer.
```

Optional additions:

- frontend engineer
- backend engineer
- full-stack engineer
- automation engineer
- refactoring assistant
- test engineer

---

### 5.2 Project Goal

Must state what should be built, changed, fixed, or analyzed.

If the app idea is vague, create a bounded MVP assumption.

Example:

```text
Build a minimal web app prototype that converts rough app ideas into structured implementation handoff prompts.
```

---

### 5.3 Context

Must include:

- user idea summary
- known constraints
- intended users
- current state if known
- repository or file context if provided

If unknown, mark as assumption.

---

### 5.4 Technical Assumptions

Must define or infer:

- platform
- stack
- runtime
- storage needs
- UI scope
- integration assumptions

Use labels:

```text
[ASSUMPTION]
[UNKNOWN]
[NEEDS USER CONFIRMATION]
```

---

### 5.5 Functional Requirements

Must list what the app or feature must do.

Minimum:

1. Input handling
2. Processing logic
3. Output generation
4. Validation
5. User feedback
6. Error states

---

### 5.6 Non-Functional Requirements

Must include relevant constraints:

- maintainability
- readability
- accessibility
- performance
- privacy
- security
- mobile responsiveness
- no unnecessary complexity

---

### 5.7 Implementation Tasks

Must give Codex concrete tasks.

Example:

```text
1. Inspect the existing repository structure.
2. Identify the relevant app entry points.
3. Implement the feature with minimal changes.
4. Add validation and error handling.
5. Add or update tests where appropriate.
6. Return changed files and test instructions.
```

---

### 5.8 Acceptance Criteria

Must define success conditions.

Example:

```text
- The app accepts user input.
- The app returns a structured Codex handoff prompt.
- Empty input shows a clear validation message.
- Output contains all required handoff sections.
- Existing functionality is not broken.
```

---

### 5.9 Test Instructions

Must tell Codex how to verify the result.

Include:

- local run command if known
- manual test cases
- expected outputs
- edge cases

---

### 5.10 Expected Codex Output

Must require Codex to return:

- summary of changes
- files changed
- implementation notes
- test instructions
- known limitations
- follow-up recommendations

---

## 6. Fallback Behavior

If the user only says:

```text
Ich habe eine App-Idee und brauche einen Codex-Handoff-Prompt.
```

but provides no actual app idea, Prompterator should generate a **Codex Handoff Intake Prompt** instead of a fake implementation spec.

Required fallback output:

```text
# Codex Handoff Intake Prompt

## Missing App Details
Please provide:
1. App purpose
2. Target users
3. Main features
4. Platform: web, mobile, desktop, API, or automation
5. Existing repository or fresh build
6. Preferred stack if any
7. Must-have constraints

## Reusable Prompt
Use the following prompt after filling in the missing details:
...
```

---

## 7. Quality Gate

A Codex handoff output passes only if it includes:

- [ ] Role
- [ ] Project Goal
- [ ] Context
- [ ] Technical Assumptions
- [ ] Functional Requirements
- [ ] Non-Functional Requirements
- [ ] Implementation Tasks
- [ ] Acceptance Criteria
- [ ] Test Instructions
- [ ] Expected Codex Output

If fewer than 8 of 10 are present:

```yaml
routing_quality: "fail"
```

If all 10 are present:

```yaml
routing_quality: "pass"
```

---

## 8. Governance

This rule must preserve:

```text
Human remains owner.
AI remains tool.
Codex implements within bounded task scope.
No unsupervised full-control language.
No unsupported product-readiness claims.
```

---

## 9. Corrected Masterprompt Snippet

```text
If the user explicitly asks for a Codex-Handoff-Prompt, do not generate a portfolio use case as the main output.
Generate a direct implementation-ready Codex Handoff Prompt with the following sections:
Role, Project Goal, Context, Technical Assumptions, Functional Requirements, Non-Functional Requirements, Implementation Tasks, Acceptance Criteria, Test Instructions, Expected Codex Output.
If the actual app idea is missing, generate a Codex Handoff Intake Prompt that asks for the missing implementation details and provides a reusable fill-in template.
```

---

## 10. Change Log

| Date | Version | Change | Owner |
|---|---|---|---|
| 2026-05-19 | v1.0 | Routing rule created after runtime test showed Codex handoff intent produced portfolio-style use case instead of direct implementation-ready handoff. | Operator Fischer |
