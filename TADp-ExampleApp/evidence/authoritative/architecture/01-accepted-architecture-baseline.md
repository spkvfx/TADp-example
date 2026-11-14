# Example record application accepted architecture baseline

**Evidence ID:** `AUTH-EX-001`  
**Classification:** `evidence/authoritative/architecture`  
**Status:** Active  
**Owner and accepting authority:** User, project authority  
**Architecture revision:** `2.0.1`\

## Binding statement

The example project must realize one coherent, locally operated record system
whose public records contain an immutable system-generated UUID, an editable
name, and an editable textual value. All executable user surfaces must use one
versioned API and one SQLite-backed authority for record behavior. The focused
records linked from this baseline define the accepted v2 interpretation of
that outcome. Application services/clients/tests/migrations/maintenance run in
Compose-managed containers and builds run through Docker BuildKit targets; the
host installs no application runtime or service.
The CLI and browser use the same `/api/v1` route set and wire behavior; their
private-network and host-loopback origins are transport boundaries, not
separate APIs.

Future work under this architecture must also satisfy the applicable
requirements of
[`SEC-NIST-SUITE-001@1.0.1`](../security/NIST/00-nist-security-policy-suite-index.md)
and
[`SEC-HIPAA-SUITE-001@1.0.1`](../security/HIPPA/00-hipaa-security-policy-suite-index.md).
The supported information profile is non-production demonstration/test data
that is purpose-created synthetic or supported by the external documented
de-identification basis accepted by the HIPAA suite, while also satisfying the
NIST suite's separate prohibition on production, confidential, regulated, or
higher-control data. Actual, possible, or insufficiently classified ePHI is
not permitted.

For security, permitted data/use, safeguards, review, and evidence, those
security suites are the primary invariants and guide this architecture. The
architecture supplies technical shape only within their limits; neither it nor
`RZN-001` can narrow, waive, or cause a policy requirement to be rewritten.

## Baseline standing and acceptance

The [architecture suite index](00-architecture-suite-index.md) is the starting
entry point. This suite is accepted project-level architecture under the User's
authority. [`ARC-AUT-001`](02-authority-and-source-disposition.md) defines its
current baseline decisions. These include Docker Compose-only application
runtime/build/test/maintenance, no host application-service or toolchain
installation, one `/api/v1` contract shared by CLI and browser, and the
security/data-use limits imposed by both policy suites.

[`RZN-001`](../../non-authoritative/realizations/v0.0/RZN-001-example-record-application.md)
is optional, non-authoritative proposal input. It is retained for source
correlation, is not a prerequisite for using this baseline, and cannot accept
its own behavior or override architecture or security requirements.

Architecture acceptance does not accept an initiative, authorize product
implementation, permit prohibited data or remote use, or establish completion,
conformance, or compliance.

## Applicability

| Applies to | Does not apply to | Rationale |
|---|---|---|
| Architecture and future documentation for the example record application | Unrelated TADp protocol, templates, or projects | The User named the example project and target architecture directory |
| Future record API, SQLite adapter, Python SDK, CLI, and browser application | A product implementation not governed by an accepted initiative | Architecture constrains products but does not authorize execution |
| Local single-user v2 Docker Compose deployment with the accepted non-production synthetic/documented-de-identified data profile | Native-host application runtime, actual or possible ePHI, production clinical use, public/remote/multi-tenant/regulated deployment, shared workstation identity, third-party record processing, Kubernetes, or non-Compose orchestration | The User requires no host service installs and the accepted security suites require a successor for excluded data or use; other environments require materially different deployment, identity, security, privacy, and operations decisions |
| Record create, retrieve, update, browse, search, and adjacent navigation | Delete, bulk operations, record-level import/export, audit history, and arbitrary queries | These capabilities are outside the bounded architecture; opaque backup transfer remains an operations concern |

## Binding claims

| Claim ID | Requirement or constraint | Verification or observation method |
|---|---|---|
| `AUTH-EX-001.1` | The API container is the sole normal runtime writer/reader of live SQLite. The networkless maintenance container may mount the data volume only under proved mutual exclusion while API is stopped. | Rendered Compose mount graph, competing-container tests, and dependency checks proving CLI/web/SDK have no SQLite path |
| `AUTH-EX-001.2` | The public record contract contains exactly `id`, `name`, and `value`; `id` is generated by the service and cannot change after creation. | Schema review, API contract tests, update rejection tests, and database trigger test |
| `AUTH-EX-001.3` | Every executable surface uses the same API-owned create, retrieve, update, search, and next/previous semantics. CLI and web consume the identical `/api/v1` paths, methods, representations, errors, and version lifecycle; no consumer-specific record API exists. Their transport origins differ only at the Docker network boundary. | Route inventory plus cross-surface conformance vectors in `ARC-CTR-009` |
| `AUTH-EX-001.4` | Searches target zero or one accepted predicate and use the field, mode, normalization, regex, ordering, and paging rules in `ARC-CTR-003`; clients must not reimplement membership. | API search tests and cross-client result comparison |
| `AUTH-EX-001.5` | Concurrency is explicit: updates require the current strong revision ETag and never silently overwrite a newer revision. | Competing-update API, SDK, CLI, and web tests |
| `AUTH-EX-001.6` | V2 is local, single-user, and unauthenticated at the application layer. The API may bind all interfaces only inside its private Compose network; Docker must publish it exclusively to host `127.0.0.1`. | Rendered Compose, host/peer reachability, Origin/Host, and publication-negative tests |
| `AUTH-EX-001.7` | Documentation/architecture, Compose/runtime packaging, API, SDK, CLI image, and web assets are distinct, independently verifiable delivery units with the dependencies in `ADR-007`. | Future scope assessments, image/build records, initiative records, and completion evidence |
| `AUTH-EX-001.8` | Released contract meaning is versioned and never rewritten in place to match implementation drift. | Revision history and compatibility review under `ADR-006` |
| `AUTH-EX-001.9` | Deletion, bulk mutation, record-level import/export, history, accounts, remote multi-user access, and offline writes are not v2 capabilities. Opaque validated backup-bundle transfer under the maintenance contract is operational recovery, not a record feature. | Route/command/UI inventory, maintenance-command boundary, and negative contract tests |
| `AUTH-EX-001.10` | No implementation or completion claim exists until a governing initiative delivers the product and supplies the evidence required by `ARC-CTR-009`. | Initiative status and completion-evidence audit |
| `AUTH-EX-001.11` | Docker Compose is the only supported runtime/orchestration path. Running the example must require no host installation of Python, SDK, CLI, SQLite, RE2, FastAPI, Uvicorn, Node/TypeScript, migration, maintenance, or test tooling. | Clean-host prerequisite inventory and end-to-end Compose-only run/build/test/maintenance audit |
| `AUTH-EX-001.12` | Live SQLite and backups use distinct Docker named volumes. Host bind mounts are forbidden for the live database; only API and mutually exclusive maintenance containers may mount data. | Compose config/mount inspection, permission/locking tests, backup export/restore drill |
| `AUTH-EX-001.13` | Released images run non-root with read-only root filesystems, dropped capabilities, no Docker socket, bounded resources, pinned/traceable inputs, and declared multi-platform targets. | Image metadata/SBOM/signature or provenance, rendered config, and runtime negative tests |
| `AUTH-EX-001.14` | Every future D2-D6 specification, delivery, release, and conformance claim must apply `SEC-NIST-SUITE-001@1.0.1` and `SEC-HIPAA-SUITE-001@1.0.1` together for their applicable scopes. Architecture evidence cannot substitute for policy evidence, and passing one security suite cannot substitute for the other. | Initiative source mapping, policy applicability matrices, exact architecture/security evidence, and release-claim review |
| `AUTH-EX-001.15` | The supported data/use profile permits only non-production demonstration/test records that are purpose-created synthetic or have the accepted externally documented de-identification basis and that do not violate the NIST suite's independent data restrictions. Actual, possible, or insufficiently classified ePHI and every successor-gate trigger are prohibited in v2. | Fixture/data manifest, provenance or de-identification record review, repository/image/artifact scans, operator documentation, and successor-gate review |

## Interpretation and conflicts

The focused accepted records in this directory are the precise interpretation
of these claims. A product convenience, implementation limitation, generated
OpenAPI document, test fixture, or client expectation cannot weaken them.
The governing Codex protocol remains higher authority for evidence handling,
human decisions, initiative lifecycle, and Git traceability.

The NIST and HIPAA suites are the primary invariants for their applicable
security, data-use, safeguard, review, and evidence scopes. Architecture owns
technical system behavior within those limits. Neither implementation
convenience nor realization-note candidate text may waive or revise a policy
gate.

If a record or product contradicts this baseline, preserve both sources, stop
only the affected work, and use the protocol invariant-conflict process.
