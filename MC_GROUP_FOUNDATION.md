# FILE 00 — FOUNDATION & GOVERNANCE BASELINE

**Status:** PROPOSED — architecture baseline only; not evidence of deployed services, configured DNS, or verified access controls.  
**Version:** 0.1.0  
**Owner:** MC GROUP (owner approval required for changes to governance, access boundaries, or canonical structure)  
**Brand root:** `mcai-Thailand.com`  
**Related core file:** FILE 01 — `EVIDENCE_RECORD_TEMPLATE.yaml` (created separately; must remain the evidence-record format)

## 1. Purpose and Scope

This document establishes the foundation for the MC GROUP Evidence & Execution System. It defines how the system fits within the existing MC GROUP architecture, sets governance and information-boundary rules, and provides a non-destructive integration plan for later files and services.

This is a plan, not a deployment specification. A domain, integration, authentication method, data store, or service named here must not be treated as live until it is independently verified and recorded as evidence.

The Evidence & Execution System is an operational capability within MC GROUP. It is not a new corporate structure, product identity, or replacement for MCAI, MC Control, or existing registries. It supports traceable work execution and evidence while preserving MC GROUP's canonical architecture and naming.

## 2. Governance Baseline

### 2.1 Canonical principles

- MC GROUP architecture is the source of truth: preserve it, extend it, do not replace it.
- Use `mcai-Thailand.com` as the canonical brand root. Preserve established product naming, including EMCOD OS where relevant.
- Preserve the canonical MC GROUP structure and P1–P4 priority hierarchy. P1/P2 take precedence unless the owner explicitly directs otherwise.
- Keep sensitive information local-first or in an approved restricted environment; use least privilege and maintain an audit trail for consequential actions.
- Prefer evidence over assumption. Mark unverified architecture and integrations as `PROPOSED`.
- Treat documentation as versioned living documents. Extend the baseline rather than silently deleting or rewriting it.

### 2.2 Priority is not authorization

Priority labels (P1–P4) express organizational priority. They do not grant access. Access must be granted by identity, role, authentication, and authorization policy at each boundary.

### 2.3 Change control

Changes to canonical structure, data ownership, access boundaries, Registry integration, or deployment status require owner review. Record material decisions and implementation evidence in the existing evidence workflow once FILE 01 and the supporting workflow are available. Do not claim a control is implemented based only on this document.

## 3. Proposed Domain & Access Map (Architecture Plan Only)

| Domain | Priority / Zone | Access | Primary function |
|---|---|---|---|
| `www.mcai-Thailand.com` | P1 / Public | Public | Landing Page, MC Group Book |
| `api.mcai-Thailand.com` | P2 / Core | Authorized systems and services | API Gateway; secrets must not be exposed |
| `ai.mcai-Thailand.com` | P2 / Product | Authenticated members | MCAI Workspace |
| `admin.mcai-Thailand.com` | P1 / Admin | Owner only | MC Control, Registry, Vault |
| `me.mcai-Thailand.com` | P4 / Private | Owner & Family | Personal Space (Level 4) |

All entries above are proposed architecture only. DNS, hosting, identity integration, authorization policy, and deployment status have not been verified. A hostname must not be assumed to exist or be secure because it appears in this table.

## 4. Security Requirements & Constraints

- Separate Public, Core, Product, Admin, and Private into distinct access boundaries.
- Store secrets only server-side or in an approved secret manager. Never send secrets to a client, browser bundle, public endpoint, or public repository.
- Restrict `admin` and `me` with multi-factor authentication (MFA) and least privilege. Owner-only access is a requirement, not a claim that enforcement is already active.
- Integrate with the existing Registry at `Registry/products.json`; do not create a replacement Registry or duplicate the canonical product catalog.
- Keep project-specific execution and evidence records separate from MCAI platform/control-plane data (see Section 6).
- Validate identity, authorization, logging, backup, and recovery controls before handling sensitive or production data.
- Do not place credentials, private keys, tokens, personal records, or Vault contents in documentation, sample data, issues, or public commits.

**Security/integration status:** `PROPOSED` — DNS, authentication, authorization, Registry availability, and deployment have not been verified.

## 5. System Architecture and Integration Boundaries

The Evidence & Execution System is a governed operational layer under MC GROUP. It consumes approved identity and catalog references from existing systems and manages execution evidence for projects; it must not become a competing source of truth for organization identity or product registration.

Conceptual flow:

1. MC GROUP governance defines ownership, priority, and approval boundaries.
2. The existing Registry remains the authoritative product/catalog source. The system references its stable product identifiers and approved metadata rather than copying and independently editing the catalog.
3. MCAI / MC Control provide platform-level capabilities only through explicitly approved interfaces. Their internal data and secrets remain within their existing ownership and security boundaries.
4. Project work produces project-scoped execution records and evidence using FILE 01's evidence record format.
5. Dashboards and reports derive status from authorized source records; they do not silently become a separate authoritative Registry.
6. AI agents receive only task-scoped, least-privilege context and return proposed outputs or references. An AI agent does not acquire authorization merely by being named in a handoff.

No API endpoints, database schemas, authentication provider, or production topology are asserted by this conceptual plan. Define and verify them in implementation planning before deployment.

## 6. Data Ownership and Classification

| Data class | Owner / source of truth | System boundary and handling |
|---|---|---|
| MC GROUP canonical structure, governance, and priority rules | MC GROUP governance baseline | Maintain in approved governance documentation; changes require owner review. |
| Product/catalog identity and approved product metadata | Existing Registry (`Registry/products.json`, subject to path/availability verification) | Reference the existing record and stable identifiers. Do not create a second Registry. |
| MCAI platform, identity, control-plane, and service configuration data | MCAI / MC Control, according to their existing governance | Remains platform-owned; expose only approved fields/interfaces to authorized consumers. Never copy secrets into project records. |
| Project plans, execution state, decisions, and project evidence | The respective project owner | Project-scoped records; use FILE 01 format and controlled access. Reference product IDs rather than redefining products. |
| Personal/Family information | Owner & Family | Private boundary (`me`); restricted access and handling. Exclude from public views and unrelated project contexts. |
| Credentials, tokens, keys, Vault contents | The applicable service/security owner | Secret manager or approved server-side vault only; never in client code or public repository. |

When ownership or classification is unclear, do not ingest or expose the data until the owner and permitted use are confirmed. Keep personal and sensitive data out of dashboards by default; expose only the minimum required summary.

## 7. AI Access and Handoff Governance

- Every AI interaction must be bounded by a named project/task, an authorized human owner, and the minimum context needed to perform the task.
- Apply the same access boundary to AI agents as to other service identities. Do not share a user's credentials or grant unrestricted Registry, Admin, Vault, or Private-space access to an agent.
- Provide references or scoped data extracts where possible instead of copying whole repositories or sensitive records into prompts.
- Treat AI-generated changes, status updates, and recommendations as proposals until checked by an authorized human or a separately approved automated control.
- Preserve provenance: record the task, source references, outputs, reviewer/approver, and consequential changes using the evidence process when available.
- Do not send secrets, Vault contents, or unrelated personal data to external AI services. Any exception requires explicit owner approval and an approved privacy/security assessment.
- FILE 06 (AI Handoff Guide) will define the operational handoff format; this baseline sets governance constraints, not a tool-specific agent protocol.

## 8. Non-Destructive Integration and Compatibility

- Inspect and back up the target system before integration; verify repository paths and current Registry structure rather than assuming them.
- Read and reference existing Registry records. Do not replace, rename, or regenerate `Registry/products.json` as part of this system.
- Use additive fields, adapters, or versioned interfaces where approved. Preserve unknown fields and existing consumers' behavior.
- Keep project records in a distinct project-scoped location/schema; link to canonical product identifiers instead of duplicating Registry entries.
- Require schema/version checks, validation, and a rollback plan before any write to an existing system.
- Test changes in an isolated/non-production environment first. Do not make production writes or migrations without owner approval and verified backups.
- Record integration decisions, test results, and rollback evidence. If compatibility cannot be established, stop and request a decision instead of guessing.

## 9. Foundation Deliverables and Dependency Order

This Foundation is the prerequisite baseline for the remaining system artifacts. Planned order:

| File | Deliverable | Dependency / constraint |
|---|---|---|
| FILE 00 | Foundation & Governance Baseline | This document; establishes governance and boundaries. |
| Supporting | `SYSTEM_ARCHITECTURE.md` | Must align with this baseline; distinguish proposed from verified topology. |
| Supporting | `DATA_STRUCTURE.md` | Must separate Registry, MCAI/control-plane, project, and private data ownership. |
| Supporting | `INTEGRATION_MAP.md` | Must reference existing systems and document unknowns; no duplicate Registry. |
| FILE 01 | `EVIDENCE_RECORD_TEMPLATE.yaml` | Existing first core artifact; preserve as the evidence-record format. |
| FILE 02 | `STATUS_DICTIONARY.yaml` | Define consistent statuses; distinguish workflow state from verification/deployment state. |
| FILE 03 | `EXECUTION_WORKFLOW.yaml` | Define owners, approvals, handoffs, and audit events. |
| FILE 04 | `PROGRESS_DASHBOARD.json` | Derived view; no independent source of truth. |
| FILE 05 | `PROJECT_REGISTER.json` | Project execution register only; must not replace the product Registry. |
| FILE 06 | `AI_HANDOFF_GUIDE.md` | Apply Section 7; task-scoped access and human accountability. |
| FILE 07 | `IMPLEMENTATION_GUIDE.md` | Include verification, privacy, compatibility, and rollback steps. |
| FILE 08 | Registry Integration | Integrate with the existing Registry after path/schema/ownership are verified. |
| FILE 09 | MCAI / MC Control Integration | Use approved interfaces; maintain platform/project ownership boundaries. |
| FILE 10 | Test Suite | Cover schema, access boundaries, Registry non-regression, and workflow validation. |
| FILE 11 | User Interface / Dashboard | Enforce authorization and data minimization; derived views only. |
| FILE 12 | Deployment Package | Only after owner approval, security review, tests, and operational readiness. |

## 10. Repository Evidence and Open Questions

At the time this baseline was prepared, the inspected `seviermc44-design/Mcai-thailand` repository tree showed `README.md` and an `index.html` file with an unusual invisible character in its filename. It did not show `Registry/products.json`, FILE 01, or the other planned system files. Therefore:

- The Registry path and schema are user-specified integration requirements but are not yet verified in this repository snapshot.
- FILE 01 is referenced as previously created, but it was not present in the inspected repository tree; its location/source must be reconciled before dependent files are authored.
- The referenced `goolegimini-ui/Kukok.com` repository was accessible but contains only a minimal README in the inspected listing; it does not establish a Registry or deployed integration.
- The local URL `http://localhost:8158/MC-GROUP-ULTIMATE-v8.html` is not accessible for independent inspection from this repository context.
- DNS, MFA, auth enforcement, Vault controls, hosting, APIs, and deployments remain unverified.

These are verification gaps, not permission to create replacements. Resolve them by identifying the authoritative repository/path and reviewing the current schema with the owner before integration work.

## 11. Acceptance Criteria for Foundation

FILE 00 is ready to guide subsequent design when:

- MC GROUP remains the organizational source of truth and the existing Registry is not duplicated.
- Priority and access authorization are explicitly distinguished.
- MCAI/control-plane data, project data, private data, and secrets have distinct ownership and handling rules.
- AI access is task-scoped, least-privilege, and auditable.
- Proposed domains and controls are not misrepresented as deployed or verified.
- Open repository/integration gaps are recorded and resolved before dependent implementation.

## Change Log

| Version | Status | Change |
|---|---|---|
| 0.1.0 | PROPOSED | Initial foundation baseline based on the provided MC GROUP operating principles, domain/access plan, and security constraints. |
