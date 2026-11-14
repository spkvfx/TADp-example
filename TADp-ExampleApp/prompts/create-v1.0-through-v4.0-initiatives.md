# Prepare the v1.0 through v4.0 application initiatives

Resolve the active scaffold `S` from this directory's governing
[AGENTS.md](AGENTS.md). The target is the project containing this `prompts/`
directory. Resolve its enclosing Git worktree `G` independently. All project
file changes must remain within `S`; necessary Git metadata operations use
`G` without expanding that boundary. Do not redirect to an archive, parent,
sibling project, or reusable scaffold library.

This prompt describes future preparation work. Storing or reviewing it does
not execute it, adopt a protocol revision, allocate an initiative, or satisfy
any authority or lifecycle gate.

## Requested outcome and limits

When explicitly invoked for execution, prepare and align the six candidate
implementation initiatives below through workflow stages 0 through 4. Each
must retain its own narrow outcome and remain `Proposed`.

The range includes `v1.0`, `v2.0`, `v2.1`, `v2.2`, `v3.0`, and `v4.0`.
These are distinct scope identities. Their numeric order does not establish
dependency satisfaction, acceptance, implementation, or release.

Execution authorizes bounded realization intake and proposal/initiative
preparation only, subject to the governing workflow and actual prerequisites.
It does not authorize protected-source edits, lock refreshes, question or
assumption resolution, initiative acceptance, delivery, completion, merges,
pushes, branch deletion, pull requests, or changes outside this project.
If evidence requires a split, another outcome, or a different mapping, stop
the affected mapping and report the exact decision needed.

## Governing inputs

Read the following inputs in order:

1. [Project instructions](../AGENTS.md), this directory's
   [instructions](AGENTS.md), and the
   [Codex invariant suite](../evidence/authoritative/LLM/00_Codex_Invariant_Suite_Index.md),
   including the canonical keyword specification and all applicable workflow,
   Git, scope, authority, decision, and coherence requirements.
2. The recorded project profile, adopted governing revision and Git baseline,
   integration configuration, and applicable scope/membership records.
3. The [architecture suite](../evidence/authoritative/architecture/00-architecture-suite-index.md),
   [NIST policy](../evidence/authoritative/security/NIST/00-nist-security-policy-suite-index.md),
   and [HIPAA policy](../evidence/authoritative/security/HIPPA/00-hipaa-security-policy-suite-index.md),
   followed by the precise authoritative records cited by each realization.
4. The six realization suite indexes and their intended notes.
5. The installed protected workflow prompts
   [00](../template/prompts/00_initiative_preparation.md),
   [01](../template/prompts/01_proposal_creation.md),
   [02](../template/prompts/02_proposal_alignment.md),
   [03](../template/prompts/03_initiative_creation.md), and
   [04](../template/prompts/04_initiative_alignment.md), their
   [shared contract](../template/prompts/WORKFLOW-CONTRACT.md), and the
   [canonical coverage map](../template/TEMPLATE-COVERAGE.md).

The template root is `S/template/`. Read reusable prompts as instructions;
instantiate record sources only at their declared destinations outside that
protected directory.

## Candidate mapping

All paths in this table are project-relative. All candidates are independent
root initiatives of type `implementation`. Dependencies do not imply a
predecessor/successor relationship.

| Scope | Suite index | Intended note | Initiative ID and slug | Decision prefix |
|---|---|---|---|---|
| `v1.0` | `evidence/non-authoritative/realizations/v1.0/00-RZN-001-P1-DOCS-suite-index.md` | `evidence/non-authoritative/realizations/v1.0/01-RZN-001-P1-DOCS-contract-documentation.md` | `INIT-IMP-001-contract-documentation` | `DOC` |
| `v2.0` | `evidence/non-authoritative/realizations/v2.0/00-RZN-001-P2-PLATFORM-suite-index.md` | `evidence/non-authoritative/realizations/v2.0/01-RZN-001-P2-PLATFORM-v2.0-container-platform.md` | `INIT-IMP-002-container-platform` | `PLT` |
| `v2.1` | `evidence/non-authoritative/realizations/v2.1/00-RZN-001-P2-API-SQLITE-suite-index.md` | `evidence/non-authoritative/realizations/v2.1/01-RZN-001-P2-API-SQLITE-v2.1-api-runtime.md` | `INIT-IMP-003-api-sqlite-runtime` | `API` |
| `v2.2` | `evidence/non-authoritative/realizations/v2.2/00-RZN-001-P2-SDK-suite-index.md` | `evidence/non-authoritative/realizations/v2.2/01-RZN-001-P2-SDK-v2.2-python-sdk.md` | `INIT-IMP-004-python-sdk` | `SDK` |
| `v3.0` | `evidence/non-authoritative/realizations/v3.0/00-RZN-001-P3-CLI-suite-index.md` | `evidence/non-authoritative/realizations/v3.0/01-RZN-001-P3-CLI-command-image.md` | `INIT-IMP-005-standalone-cli-image` | `CLI` |
| `v4.0` | `evidence/non-authoritative/realizations/v4.0/00-RZN-001-P4-WEB-suite-index.md` | `evidence/non-authoritative/realizations/v4.0/01-RZN-001-P4-WEB-browser-bundle.md` | `INIT-IMP-006-web-application-bundle` | `WEB` |

New initiative destinations follow
`initiatives/<scope>/implementation/<initiative-id-and-slug>/`.
Record dedicated initiative branches as
`initiative/<scope>-<initiative-id-and-slug>` under the installed scope
workflow. Record the actual branch, immediate parent, integration target,
and immutable creation base; do not substitute a common source commit for
the required scope parent.

## Preflight

Perform these checks before allocation or branch creation:

1. Verify `S`, all affected resolved paths, Git containment, protected locks,
   the current branch/tip, and a clean staged, unstaged, and untracked state.
   Preserve unrelated work; do not discard or absorb it.
2. Verify actual human project ownership, approval convention, integration
   branch, adopted scope-workflow governing commit, and adoption baseline.
   The installed library alone does not establish adoption. If the necessary
   authority or identity is absent, stop and report it. Recover only genuinely
   constructible documentary prerequisites through their owning procedure;
   never invent an owner, effective commit, adoption, or migration authority.
3. Inventory current initiatives, scopes, catalogs, branch roles, prior
   assignments, partial effort, and conflicts. Verify every mapped source ID
   and path. Existing complete records are reused; a prior attempt requires
   its actual recovery route, never overwrite or fresh duplicate allocation.
4. Assess each source against current authoritative evidence and mandatory
   split triggers. Preserve D1 through D6 as distinct acceptance/completion
   claims. Stop unsupported mappings and preserve unresolved choices.

Applicable canonical records include `project-profile.md`,
`initiatives/version-scopes.md`, `initiatives/initiative-index.md`,
`initiatives/status.md`, and `initiatives/work-conflicts.md`. Use migration
ledgers only when legacy work actually exists and has sufficient migration
authority; do not create migration history for a new allocation.

## Serial execution

Process candidates in table order. For each candidate, complete each stage
and its required verification before beginning the next stage:

1. Apply Stage 0 to assess fit and record source-to-target routing before
   allocation. Prepare missing major scopes `v1`, `v2`, `v3`, or `v4` from the
   recorded project integration base, and matching minor scopes from their
   own major. Reuse existing valid parents. Prepare the candidate's dedicated
   branch directly from its assigned minor scope. Record scope navigation,
   membership, provenance, branch roles, captured bases, authority, and the
   minimal `Proposed` skeleton. No proposal or full suite is created here.
2. Apply Stage 1 to create the canonical working proposal from the mapped
   realization index and note, preserving their non-authoritative standing.
3. Apply Stage 2 to align that proposal with precise authoritative evidence.
   Retain unresolved assumptions and questions.
4. Apply Stage 3 to create the complete initial implementation initiative
   suite and tracking entries using the mapped identity and decision prefix.
   Keep the initiative `Proposed`.
5. Apply Stage 4 to align the whole initiative as one coupled proposed
   specification, including current sibling effort and mandatory split
   triggers. Do not accept the initiative or resolve human decision gates.

Serialize shared worktree and registry writes, preserving earlier rows and
their actual standing. Prepare shared scope coordination through Stage 0's
owning rules; never merge unfinished initiative branches to propagate it.
If the recorded branch layout cannot make required shared coordination
available without an unauthorized merge or transfer, stop and report that
coordination blocker. Do not silently change parentage or hide sibling work.

Keep initiative-specific commits on the assigned branch with clear identity
and stage messages. Commit only traceable changes after each owning step
passes; do not create empty commits. Keep the worktree clean before switching.
Read sibling branch evidence when relevant without editing, cherry-picking,
or claiming it has been integrated.

## Verification and report

For each candidate, verify exact scope, source IDs/paths, initiative identity,
grouped destination, reciprocal mappings, current cycle, branch/base/parent,
tracking, complete Stage 3 artifact set, and truthful `Proposed` lifecycle.
Verify unresolved decision states, narrow scope, architecture/security
alignment, and mutual coherence with all available sibling effort.

Run installed protected-source, validator, link/structure, and applicable
tests with the configured environment. Preserve failures and missing
evidence. Confirm that the diff contains no protected or unrelated changes.

Report one row per scope with the stage reached, source and initiative,
branch and immutable base, canonical records, actual commits/changed paths,
verification results, unresolved choices/conflicts, and next permitted stage.
Run a read-only cross-branch identity/coherence audit without merging branches.
Stage 5 is the next permitted prompt only after Stage 4 completes without a
blocking split or conflict. Report blocked or uncreated candidates explicitly.
