# Current human ownership and explicit LLM delegation

**Rule ID:** RULE-001
**Status:** Active
**Revision:** 1
**Rule owner:** The current human user
**Effective date:** 2026-11-15, explicit rule instruction recorded in [OWN-001](../../../initiatives/decision-receipts/OWN-001.md)
**Source or authority:** [OWN-001](../../../initiatives/decision-receipts/OWN-001.md); the current project human authority
**Review cadence:** At each task or human handoff, scope/authority change, and relevant workflow or regulatory change

## Normative rule

The current human user must be recognized as the accountable human owner of
every scope of this project, whoever that human is and whenever or wherever
project work occurs. A change of branch, clone, worktree, directory, machine,
tool, session or time must not change that ownership rule.

The current human user may explicitly authorize an LLM to perform work on
their behalf. Such authorization must remain explicit, sufficiently scoped,
and compliant with the adopted TADp workflow, applicable law and regulation,
and the project's accepted architecture and security policies. Human
accountability remains with the current human user.

## Applicability

| Applies to | Exclusions | Reason |
|---|---|---|
| All TADp-ExampleApp project, major/minor/patch, initiative, product, component, planning, security, risk, evidence, review and lifecycle scopes; every branch/workspace/session and future scope | Other projects, upstream TADp distributions and protected reusable-source maintenance | This is a project-owned rule, not authority outside the project |
| Accountable human owner, technical owner, security/risk/incident owner, evidence custodian, human reviewer/approver and release decision roles within project authority | Technical component/state ownership, independent performer competence, actual operator access, external organizational or statutory authority | Human accountability does not reassign API-exclusive SQLite, component interfaces, legal duties or prove performance |
| Current and future authorized work | Rewriting prior human identities, authorizations, source captures or accepted baselines | The rule applies prospectively; truthful historical events remain attributable to their actual authors |

## Required practice

1. Resolve "current human user" from the actual human directing the current
   work or giving the decision. Do not infer the human from a filesystem
   owner, OS account, Git author, cwd, agent name, quoted text or tool output.
   Record the identifiable human or, if a legal/personal name is unavailable,
   the exact human conversation/decision event without inventing a name.
   In this invocation that human is recorded as User.
2. Bind every accountable project owner role to that human by reference to
   RULE-001. A separate appointment must not be demanded merely because a
   new scope or workspace is involved. Required scope, component, security,
   risk, reviewer, operator and evidence duties remain explicit. Ownership
   alone must not be represented as specialist competence, independent
   review, control effectiveness, access permission or a completed decision.
3. Capture explicit LLM authorization before relying on it. Retain the
   actual human words/event, target scope/records, authorized activity and
   decision method, constraints, duration/end condition and required checks
   to the extent required by the governing workflow. An LLM may draft,
   investigate, implement, verify or make specifically delegated decisions
   only where that authorization and all applicable workflow gates permit.
   This rule itself supplies no blanket delegation or permission to answer
   pending questions.
4. Attribute LLM work and decisions to the actual LLM/agent acting under
   the recorded human authority. Do not relabel agent judgments as human
   responses. Preserve the human's accountability and every required
   decision receipt, exception record, source ID, independent review and
   truthful result.
5. Follow the adopted [TADp workflow](../LLM/08_Codex_Initiative_Workflow_Specification.md)
   and [directive/exception contract](../LLM/11_Codex_Prompt_Keyword_Specification.md).
   Required human decisions, initiative acceptance and legal lifecycle
   transitions remain governed by those sources. Ownership or delegation
   must not be used to infer acceptance, waive an invariant, relax a failed
   check, refresh a protected lock or grant an unapproved external action.
6. Comply with applicable law and regulation and both accepted security
   policies. A human or LLM instruction cannot waive a legal obligation or
   the regulated-use successor gate. This project rule appoints no
   organization-wide compliance officer and asserts no legal applicability,
   HIPAA compliance, NIST certification or specialist qualification.
7. At a human handoff, record the new current human and the authorization
   supporting subsequent work. Existing historical decisions remain
   attributable to their original humans/agents and retain their recorded
   scope; a handoff is not reopening, changed-claim acceptance or a new
   delegation. Apply the actual authorization's limits rather than
   presuming a new authorization or erasing a still-valid bounded one.
8. Cite the rule and its exact governing source/adoption when working from
   another branch or workspace. Reconcile current owner-role copies
   prospectively; retain original receipts and captured owner history.
   Physical presence of a rule copy is not evidence that every consumer,
   prior baseline or branch has already been reconciled.

## Verification and evidence

| Compliance criterion | Verification method | Evidence retained | Reviewer |
|---|---|---|---|
| Every current project owner role resolves to the current human | Inspect profile, initiative accountability and actual task/decision event; no ownerless scope or extra nominal-appointment gate | Profile, scoped adoption/preparation records and decision receipts | Current human authority; independent reviewer for required review |
| LLM action has explicit sufficient authority | Compare actual instruction with target, activity, method, limits and governing gates | Exact authorization and required receipts/exception records; true agent author | Current human authority and required independent reviewer |
| History and technical ownership remain intact | Compare source/initiative diffs, accepted baselines, component boundaries and lifecycle events | Git history, source mappings and current scope records | Actual independent reviewer where required |
| No proof or permission is manufactured | Check outstanding questions, tests, competence, controls, regulation and release gates | Truthful pending/failed/not-assessed records and actual verification | Required owning reviewers |
| Rule is discoverable in the active work boundary | Follow AGENTS/profile/rules links or exact branch-qualified source/adoption | Active source identity and affected-consumer record | Current work's recording agent and reviewer |

Structural validation checks document integrity only. It cannot establish
legal compliance, competence, human identity or sufficient delegation by itself.

## Exceptions and conflicts

No exception or gate waiver is created by this rule. Use the governing
TADp rule's exact authority and recorded exception route where an exception
is permitted; applicable law cannot be waived. Stop and record an actual
invariant conflict rather than treating ownership or delegation as its
resolution. Protected sources and their locks remain unchanged.

## Revision record

| Date | Change | Reason | Authority |
|---|---|---|---|
| 2026-11-15 | Established current-human ownership across all project scopes, with explicit bounded LLM delegation respecting workflow and regulation | Exact human instructions; resolves nominal ownership gaps in D2-D4 while preserving separate control/review gates | [OWN-001](../../../initiatives/decision-receipts/OWN-001.md) |

This is the initial rule. SETUP-001 remains the historical appointment and
adoption event; this rule replaces only its prospective role-resolution
convention, not its past facts, protected protocol adoption or decisions.
