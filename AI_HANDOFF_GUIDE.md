# AI_HANDOFF_GUIDE.md

Status: PROPOSED
Version: 1.0.0
Updated: 2026-11-16

## 1. Purpose

This guide defines how AI agents interact with the MC GROUP Evidence & Execution System without creating new authority, new registries, or unsafe access patterns. It is a governance and handoff contract for task-scoped AI support.

It is not a deployment guide, a production access policy, or evidence that any AI integration is currently live. A handoff described here remains proposed until it is separately reviewed, tested, and approved.

## 2. Governing Rules

These rules override any ad hoc agent behavior:

- MC GROUP architecture is the source of truth.
- Do not create a replacement Registry or duplicate canonical product metadata.
- P1-P4 priority is not access permission.
- AI access must be least privilege and task-scoped.
- Confirm ownership, scope, and verification status before the AI acts on sensitive, operational, or private data.
- Secrets, keys, tokens, Vault content, personal data, and sensitive access data must never be provided to AI systems without explicit, approved controls.
- Human approval remains required for consequential actions, production changes, and decisions affecting governance, security, or deployment.
- The system must distinguish between planned, verified, and deployed states.

## 3. Scope of AI Use

AI may support the system in the following bounded ways:

- Summarizing project records and task status
- Drafting evidence descriptions, checklists, and review notes
- Formatting YAML/JSON documents and status updates
- Suggesting workflow logic, status transitions, and documentation structure
- Assisting with project register or dashboard formatting under approved schema
- Generating handoff notes, review summaries, and implementation drafts

AI must not be used for:

- Granting or changing access privileges
- Creating or modifying the canonical Registry
- Setting production deployment state without a human approval gate
- Exposing or storing secrets or private records in prompts or outputs
- Determining ownership or priority as a substitute for human governance
- Claiming that a service, domain, or environment is live without independent verification

## 4. Required Handoff Structure

Every AI task handoff should include:

- Project or work item ID
- Task objective
- Relevant source references
- Authorization scope
- Required data boundaries
- Required output format
- Review and approval path
- Evidence expectations

### Example handoff

```yaml
project_id: "MCG-EXAMPLE-001"
objective: "Draft evidence summary for project status update"
source_refs:
  - "MC_GROUP_FOUNDATION.md"
  - "STATUS_DICTIONARY.yaml"
  - "EXECUTION_WORKFLOW.yaml"
access_scope:
  allowed_data:
    - "Approved project summary"
    - "Non-sensitive workflow status"
  denied_data:
    - "Secrets"
    - "Vault contents"
    - "Private family data"
    - "Unapproved internal credentials"
output_format:
  - "Markdown summary"
  - "Status note"
  - "Evidence references only"
review_required: true
approval_required: true
```

## 5. Data Handling Rules

AI must operate under the minimum required data boundary.

### Allowed data categories

- Public or approved non-sensitive content
- Approved project-scoped summaries
- Documentation already in the repository and explicitly referenced
- Work item metadata that is not sensitive or privileged

### Forbidden data categories

- Secret keys, API tokens, passwords, or access credentials
- Vault content
- Private personal information outside approved private boundary
- Any record not explicitly authorized for the task
- Unverified control data or system state presented as fact

## 6. Human Review and Approval Gates

AI-generated content must be reviewed before it becomes operational, authoritative, or deployed.

Required human review for:

- Any change to workflow, status, or project records with operational consequences
- Any output that affects security boundaries, access, or deployment state
- Any change that touches existing Registry or system configuration
- Any output claiming verification, deployment, or production readiness

If the AI response is uncertain, incomplete, or lacks evidence, it must state uncertainty and ask for the minimum required clarification.

## 7. Handoff Workflow

### Step 1 — Intake

Confirm:

- project ID or task ID
- owner or responsible human
- objective and expected output
- approved scope and boundaries

### Step 2 — Context Provision

Provide only the data necessary for the task:

- approved repository documents
- approved project summaries
- linked evidence references
- status rules and workflow rules

Do not provide:

- secrets
- private data
- unrelated system information
- broad access to the whole repository unless explicitly required

### Step 3 — Draft Output

AI produces:

- a structured result
- source references
- any assumptions or uncertainty
- a note about required review if the output affects a system boundary

### Step 4 — Review

A human verifies:

- correctness
- compliance with governance rules
- data minimization
- correctness of statuses and references

### Step 5 — Acceptance

Accepted AI output is logged and linked to a project or evidence record. Unaccepted output remains a draft and is not treated as authoritative.

## 8. AI Output Format Standard

Each AI output should include:

1. Objective
2. Scope / Data Boundary
3. Source References
4. Key Findings
5. Uncertainty or Risks
6. Required Human Review

Example:

```text
1. Objective
Draft a project status summary for the current evidence record.

2. Scope / Data Boundary
Only approved non-sensitive project summary and status fields.

3. Source References
MC_GROUP_FOUNDATION.md
STATUS_DICTIONARY.yaml
EXECUTION_WORKFLOW.yaml

4. Key Findings
Current workflow status is PROPOSED and pending verification.

5. Uncertainty or Risks
No deployment or DNS validation is present in the current records.

6. Required Human Review
Confirm status wording, referential integrity, and whether the summary is suitable for release.
```

## 9. Registry and Platform Safety Rules

AI must never assume that the following are valid without independent evidence:

- Registry path exists and matches an approved catalog
- Domain is live or production-ready
- Authentication or MFA is active
- Service is deployed or accessible
- API integration is functioning
- Current security controls are active

All such claims must be verified by a human, by explicit system evidence, or by an approved operational check.

## 10. Readiness Gate for AI Integration

AI support is considered ready for operational use only when all of the following are true:

- The task boundary, access scope, and source references are explicit
- Human ownership and review path are defined
- Secrets and private data are excluded by default
- A verified evidence model exists for logging outcomes
- The relevant workflow and status vocabulary are in use
- Integration is reviewed as non-destructive and approved by an authorized owner

Until then, AI usage remains PROPOSED and must be treated as assistive, not authoritative.

## 11. Change Log

| Version | Date | Status | Change |
|---|---|---|---|
| 1.0.0 | 2026-11-16 | PROPOSED | Initial AI handoff governance and task-boundary guide. |

## 12. Related Files

- MC_GROUP_FOUNDATION.md
- STATUS_DICTIONARY.yaml
- EXECUTION_WORKFLOW.yaml
- PROGRESS_DASHBOARD.json
- PROJECT_REGISTER.json

This guide should be used as the governance baseline for the next AI and integration stages, while keeping all operational claims clearly marked as proposed until verified.
