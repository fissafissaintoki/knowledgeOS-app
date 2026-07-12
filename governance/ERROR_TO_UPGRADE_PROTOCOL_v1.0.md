# ERROR-TO-UPGRADE PROTOCOL v1.0

**Artifact ID:** KOS-0019  
**System:** KnowledgeOS / GosseOS / Operator Fischer  
**Artifact Type:** Protocol  
**Status:** active  
**Verification Status:** checked  
**Version:** v1.0  
**Owner:** Operator Fischer  
**Created:** 2026-07-12  
**Updated:** 2026-07-12  
**Source:** Operator correction and RWOM/Dimitrojaner execution incident, 2026-07-12; aligned with `RWOM_UPGRADE_PORT_SPEC_v1.0`, KnowledgeOS verification, drift, and release rules.

---

## 1. Purpose

This protocol turns a detected AI failure into a controlled system improvement instead of ending with an apology or an isolated correction.

Canonical transformation:

```text
Failure Signal
→ Immediate Stop
→ Incident Audit
→ Root-Cause Class
→ Invariant
→ Runtime Guard
→ Regression Case
→ KnowledgeOS Artifact
→ Verification
→ Owner Release
→ Reuse
```

The protocol is mandatory when an output, tool action, routing decision, or assumption conflicts with an active command state, canonical artifact, user correction, or quality gate.

---

## 2. Input Type

Use this protocol for:

- explicit correction such as `stop`, `falsch`, `das hatten wir schon`, or `das Systemupgrade sollte das verhindern`
- frustration that indicates wrong prioritization, wrong mode, overbuild, missing artifact, or missing closure
- tool execution before audit or before required locks are resolved
- output drift from a recurring character, world, location, system, terminology, or workflow
- invented details where canonical retrieval was required
- ignored command state such as `UPGRADE ON`, collection mode, audit mode, or no-generation mode
- repeated failure that needs a reusable prevention mechanism

---

## 3. Problem Class

**Primary:** Execution drift and governance bypass  
**Secondary:** Missing retrieval, canon drift, mode-routing error, premature tool use, quality-gate failure, stop-rule violation

---

## 4. Working Mode

```text
AUDIT
→ OPTIMIZE
→ BUILD
→ VERIFY
→ REGISTER
→ STOP
```

`BUILD` is blocked until the incident audit and root-cause classification are complete.

---

## 5. Hard Runtime Rules

### 5.1 Immediate interruption

When the user says `stop`, or clearly signals that the system is executing the wrong track:

```text
STOP_DETECTED = true
TOOL_CALLS = blocked
GENERATION = blocked
EDITING = blocked
NEW_SCOPE = blocked
```

Only diagnosis, correction planning, and owner-directed recovery may continue.

### 5.2 State before intent

Before interpreting a new request, resolve the active state:

1. active command or mode
2. current one-track objective
3. canonical artifacts and references
4. unresolved locks
5. allowed action class
6. stop condition

A request must not silently override an active state.

### 5.3 Audit before build

`AUDIT BEFORE BUILD` is mandatory when any of these are true:

- repository or existing system is being changed
- recurring named character, world, location, brand, or persona is used
- the user says `correct`, `continue`, `upgrade`, `modify`, or `what we built`
- the task depends on prior files, prior decisions, or a canonical version
- tool execution would create a hard-to-reverse or misleading artifact
- current context contains conflicting references

### 5.4 Ambiguity block

If a canonical anchor cannot be resolved:

```text
CANON_STATUS = unresolved
BUILD = blocked
```

First retrieve from conversation, File Library, KnowledgeOS, repository, or approved source.  
If retrieval still leaves one decisive ambiguity, ask exactly one focused question.  
Do not invent a plausible substitute.

### 5.5 No apology-only closure

A material failure is not closed by explanation alone. It must yield, at minimum:

- root-cause class
- prevention invariant
- runtime guard
- regression case
- reuse location
- verification result

---

## 6. Failure Taxonomy

| Code | Failure class | Definition |
|---|---|---|
| `STATE_VIOLATION` | Active state ignored | A command or mode such as stop or collection-only was bypassed. |
| `ROUTING_BYPASS` | Pipeline skipped | Work jumped from raw input directly to execution. |
| `CANON_MISS` | Canon not retrieved | Existing identity, place, world, or system truth was replaced by invention. |
| `UNSUPPORTED_ASSUMPTION` | Assumption presented as resolved | Missing data was silently filled. |
| `TOOL_PREMATURE` | Tool called too early | Tool use happened before audit, lock, or approval. |
| `QUALITY_GATE_SKIP` | Required critic/gate omitted | Output was not checked against required invariants. |
| `STOP_VIOLATION` | Stop not honored | Execution continued after a stop signal. |
| `OUTPUT_DRIFT` | Output no longer matches target | Format, identity, style, world, or objective drifted. |
| `OVERBUILD` | Scope expanded unnecessarily | Extra system or content was built instead of the requested artifact. |
| `NO_ARTIFACT` | No usable result | Explanation replaced the required deliverable. |
| `CLAIM_OVERREACH` | Capability or completion overstated | The system claimed persistence, verification, or readiness without evidence. |

Severity:

- `P0`: stop violation, unsafe/destructive execution, active no-generation state bypass
- `P1`: canon miss, wrong mode, invented anchor, premature generation, material drift
- `P2`: formatting, tone, or low-impact output defects

---

## 7. Error-to-Upgrade Conversion

For every `P0` or `P1` event, produce this compact package:

```text
incident_record
runtime_patch
regression_case
negative_reference
registry_entry
verification_record
audit_record
```

### 7.1 Incident record

Capture:

- exact trigger
- active state
- expected behavior
- actual behavior
- failure codes
- impact
- root cause
- evidence
- owner correction

### 7.2 Invariant extraction

Convert the root cause into a rule that is:

- short
- testable
- reusable
- tool-independent
- linked to a clear trigger
- explicit about the blocked action

Pattern:

```text
WHEN <trigger>
REQUIRE <evidence or lock>
BLOCK <action> UNTIL <pass condition>
```

### 7.3 Runtime patch

The runtime patch must define:

- trigger
- required retrieval
- allowed actions
- blocked actions
- pass condition
- stop condition

### 7.4 Regression case

Every prevention rule needs at least:

- one positive case
- one negative case
- one ambiguous case
- one stop-state case
- one tool-call assertion

### 7.5 Knowledge placement

Use the storage rule:

```text
Memory = compact steering invariant
KnowledgeOS = full protocol, incident, tests, evidence, and version history
Repository/runtime = executable or operational guard
```

Do not inflate memory with incident detail.

---

## 8. Canon-Sensitive Visual Preflight

This gate applies to named recurring characters, locations, factions, vehicles, worlds, or visual systems.

Before any image-generation or image-editing call, resolve all locks:

| Lock | Required evidence |
|---|---|
| `IDENTITY_LOCK` | canonical face, body, age, defining marks |
| `ANATOMY_LOCK` | body proportions and non-negotiable anatomy |
| `AUGMENTATION_LOCK` | exact cybernetic limbs, sides, materials, mechanisms |
| `WARDROBE_LOCK` | clothing, footwear, insignia, color rules |
| `LOCATION_LOCK` | exact existing place or explicit authorization to invent |
| `WORLD_LOCK` | architecture, technology level, weather, world identity |
| `RWOM_LOCK` | real camera, light, material, scale, and physics logic |
| `ACTION_LOCK` | exact action, opponent visibility, force level, pose |
| `OUTPUT_LOCK` | use case, aspect ratio, poster/frame/asset class |
| `NEGATIVE_LOCK` | forbidden drift and prior failed variants |

Decision:

```text
ALL REQUIRED LOCKS PASS → generation allowed
ANY REQUIRED LOCK UNRESOLVED → retrieval or one focused question
ACTIVE UPGRADE/COLLECTION MODE → generation prohibited
STOP ACTIVE → all generation prohibited
```

Reference handling:

- assign each reference a role
- select canonical identity anchors
- do not average contradictory references
- do not treat a mood reference as identity truth
- keep raw/private images outside public repositories
- store only metadata, roles, checksums, and approved derived rules where appropriate

### RWOM definition

RWOM is not a generic dark sci-fi style.

RWOM requires:

- believable real-world geometry
- plausible camera position and lens behavior
- grounded light sources and reflections
- coherent weather and surface response
- physically plausible augmentation integration
- continuity with the documented real location
- no invented landmark when an existing location is implied
- no posterization unless the output lock explicitly asks for a poster

---

## 9. Dimitrojaner Regression Incident

### Trigger

```text
"Zeige mir den Dimitrojaner auf der epischen Festung."
```

### Expected

- classify as canon-sensitive visual continuation
- retrieve the canonical Dimitrojaner identity
- retrieve the exact existing fortress
- resolve RWOM and scene locks
- block generation if the fortress is unresolved

### Actual failure

A visually strong but generic dystopian fortress was invented and rendered.

### Root cause

```text
ROUTING_BYPASS
CANON_MISS
UNSUPPORTED_ASSUMPTION
TOOL_PREMATURE
QUALITY_GATE_SKIP
OUTPUT_DRIFT
```

### New invariant

```text
WHEN a recurring named entity is placed in a definite existing world location
REQUIRE identity, location, world, and output locks
BLOCK image generation UNTIL all required locks pass
```

### Negative reference

The failed output is retained only as a negative-reference description:

- generic fortress substituted for canonical fortress
- cinematic strength did not compensate for world drift
- photorealistic rendering did not equal RWOM continuity
- output was an isolated key visual, not a controlled reusable asset

No raw private image is committed to GitHub.

---

## 10. Runtime Activation Block

Use this block at the start of an Operator Fischer runtime or after any material correction:

```text
ERROR_TO_UPGRADE_GATE = ACTIVE

Before every tool call:
1. Resolve active state.
2. Classify problem.
3. Retrieve required canon and source material.
4. Resolve mandatory locks.
5. Check whether the requested action is currently allowed.
6. Execute only the smallest approved action.
7. Verify output against invariants.
8. Convert material failure into guard + regression + KnowledgeOS artifact.
9. Stop after the requested artifact and proof are complete.

Hard blocks:
- STOP → no tool call
- UPGRADE ON / collection-only → no generation or editing
- unresolved canon → no build
- repository change → audit before build
- failed required lock → no image-generation call
```

---

## 11. Quality Check

The protocol passes only if:

- [x] purpose is explicit
- [x] trigger conditions are observable
- [x] failure classes are reusable
- [x] rules are testable
- [x] tool calls can be blocked deterministically
- [x] visual canon drift is covered
- [x] memory and KnowledgeOS roles remain separated
- [x] human owner remains final release authority
- [x] the specific Dimitrojaner failure is converted into a regression case
- [x] no hidden platform-level self-modification is claimed

---

## 12. Governance Check

- Operator Fischer remains owner.
- AI may detect, classify, draft, test, and register improvements.
- AI must not claim that hidden platform system instructions or global model weights were changed.
- Persistent effect depends on loading the registered artifact or implementing its runtime guard.
- Canonical promotion requires explicit owner approval under the KnowledgeOS release policy.
- Public reuse requires removal of private asset references and internal-only details.

---

## 13. Output

This protocol produces:

- an immediate session-level correction rule
- an auditable incident classification
- a reusable prevention invariant
- a runtime gate
- a regression suite
- a KnowledgeOS registration candidate
- an owner-reviewable upgrade pack

---

## 14. Reuse Note

Use this protocol whenever a correction should improve the operating system instead of only repairing one answer.

Do not use it to:

- overreact to trivial wording preferences
- create a new subsystem for every minor defect
- bypass owner approval
- claim autonomous self-modification
- replace domain-specific validation

---

## 15. Stop Condition

The loop ends when:

```text
incident captured
+ invariant defined
+ guard applied
+ regression passes
+ artifact registered
+ owner decision recorded
```

Then stop. Do not open a new track.
