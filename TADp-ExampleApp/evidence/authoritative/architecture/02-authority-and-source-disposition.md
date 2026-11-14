# Accepted architecture baseline decisions

**Architecture ID:** `ARC-AUT-001`  
**Status:** Accepted  
**Owner and accepting authority:** User, project authority  
**Architecture revision:** `2.0.1`  
**Related records:** [Architecture suite index](00-architecture-suite-index.md), [AUTH-EX-001](01-accepted-architecture-baseline.md)\

## Purpose

This record defines the current accepted architecture decisions and their owning
records. The [architecture suite index](00-architecture-suite-index.md) is the
starting entry point. The decisions below are self-contained; no realization
note is required to interpret or apply them.

The IDs `RZN-001-Q01` through `RZN-001-Q17` are retained solely for reciprocal
correlation with optional proposal inputs. They do not give those inputs
authority over this architecture or the security baselines.

## Baseline authority and scope

The User is the accepting project authority for this architecture. The accepted
scope includes the baseline decisions below and directly necessary boundaries,
contracts, technology choices, limits, failure behavior, and verification
obligations for the example record application.

Docker Compose is the only application runtime. Application services,
clients, tests, migrations, maintenance, and build tools run in containers;
the host needs no application-service or toolchain installation. CLI and
browser use the same versioned `/api/v1` contract and route set while retaining
their distinct host-loopback and private-container network origins.

The NIST and HIPAA suites remain the primary security and data-use invariants.
Architecture acceptance does not authorize implementation, initiative
acceptance, completion, release, ePHI, regulated or remote use, alteration of
the Codex protocol, or changes to unrelated evidence. Future changes follow
the suite's change-control process.

## Accepted baseline decisions

| Correlation ID | Accepted baseline decision | Owning record |
|---|---|---|
| `RZN-001-Q01` | `name` is the user-chosen human-readable label for the record. It has no uniqueness meaning and is not an identity. | [`ARC-CTR-001`](11-record-domain-contract.md) |
| `RZN-001-Q02` | `name` and `value` are required Unicode strings. `name` is trimmed, single-line, NFC-normalized, non-empty, and limited to 120 code points/480 UTF-8 bytes. `value` is NFC-normalized text, permits empty and multiline content, preserves surrounding whitespace, and is limited to 4,096 code points/16 KiB. Neither is unique. | [`ARC-CTR-001`](11-record-domain-contract.md) |
| `RZN-001-Q03` | The API generates a random UUIDv4 from the operating system CSPRNG. The public and SQLite representation is the canonical lowercase hyphenated 36-character form. Callers cannot supply IDs. | [`ADR-002`](05-ADR-002-identity-order-and-concurrency.md), [`ARC-CTR-001`](11-record-domain-contract.md) |
| `RZN-001-Q04` | Edits use explicit Save and Cancel actions. All updates use optimistic concurrency with the last observed strong ETag; a stale edit fails without overwrite and requires refresh/reconciliation. | [`ARC-CTR-002`](13-record-http-contract.md), [`ARC-CTR-007`](22-web-interaction-contract.md) |
| `RZN-001-Q05` | An internal monotonic, non-reused ordinal defines total creation order. Next/previous select the adjacent ordinal in the full collection or the supplied search context. Boundaries return a successful explicit boundary result without wrapping. | [`ADR-002`](05-ADR-002-identity-order-and-concurrency.md), [`ARC-CTR-003`](14-search-navigation-contract.md) |
| `RZN-001-Q06` | A search contains at most one predicate: one field, one mode, and one query. Text is NFC-normalized and matched case-sensitively without implicit trimming. Nulls do not exist. Results use ordinal order. | [`ARC-CTR-003`](14-search-navigation-contract.md) |
| `RZN-001-Q07` | Regex uses the accepted RE2-compatible subset, unanchored search semantics, explicit user anchors, a 256-byte pattern limit, bounded record/value sizes, a 10,000-record database cap, and a request budget. Unsupported or invalid patterns are stable client errors. | [`ADR-003`](06-ADR-003-search-execution-semantics.md), [`ARC-CTR-003`](14-search-navigation-contract.md) |
| `RZN-001-Q08` | `exact` is the canonical name of the exact-match search mode. | [`ARC-CTR-003`](14-search-navigation-contract.md) |
| `RZN-001-Q09` | The SDK is a separately versioned Python 3.12+ synchronous client library, modeled with Pydantic v2 and transported by HTTPX. Its wheel is built/tested in containers and installed into CLI/test/developer images; running the example never requires a host SDK/Python install. | [`ARC-BND-004`](17-python-sdk-boundary.md), [`ARC-CTR-005`](18-python-sdk-contract.md) |
| `RZN-001-Q10` | "Standalone CLI" means an independently versioned OCI image invoked as `docker compose run --rm record-cli`; it requires neither the web product nor host Python/SDK/CLI installation. It calls the API through its image-installed SDK and never mounts/opens SQLite. | [`ARC-BND-005`](19-cli-boundary.md), [`ARC-CTR-006`](20-cli-interaction-contract.md) |
| `RZN-001-Q11` | The CLI must call the API through the Python SDK. The browser app calls the same HTTP API directly through its browser adapter. Both consume the identical `/api/v1` resource paths, methods, representations, errors, search/navigation semantics, and version lifecycle; there is no CLI-only or web-only record API path. Their origins differ only because the host browser enters through Docker-published loopback while the CLI container uses private Compose DNS. Neither may share or invoke the SQLite adapter. | [`ADR-001`](04-ADR-001-api-exclusive-persistence.md), [`ARC-CTR-002`](13-record-http-contract.md) |
| `RZN-001-Q12` | The v2 target is pinned multi-stage Linux OCI images built with Docker BuildKit and orchestrated by Compose. Images contain Python 3.12+, FastAPI, Pydantic v2, `sqlite3`, official `google-re2`, HTTPX, Uvicorn, and container-built framework-free TypeScript assets. Ordered SQL migrations and all build/test tools run in containers. | [`ADR-005`](08-ADR-005-containerized-technology-stack.md) |
| `RZN-001-Q13` | V2 is a local single-user Compose application: host-loopback publication only, private internal network, no app auth/CORS/telemetry, non-root read-only images, named volumes, structured privacy-aware logs, WCAG 2.2 AA browser behavior, bounded resources, and offline networkless maintenance/backup/restore containers. Future work also applies the NIST and HIPAA suites together; only the accepted non-production synthetic/documented-de-identified data profile is permitted, actual or possible ePHI is prohibited, and remote, multi-user, shared-workstation, third-party-processing, regulated-use, identity, audit, or encryption expansion requires the recorded successor gate. | [`ADR-004`](07-ADR-004-container-only-deployment-trust-model.md), [`ARC-CTR-008`](23-operations-security-contract.md), [`SEC-NIST-SUITE-001@1.0.1`](../security/NIST/00-nist-security-policy-suite-index.md), [`SEC-HIPAA-SUITE-001@1.0.1`](../security/HIPPA/00-hipaa-security-policy-suite-index.md) |
| `RZN-001-Q14` | Deletion, bulk operations, record-level import/export, and record history are deliberately excluded from v1. Opaque validated backup-bundle transfer is an operations/recovery mechanism and does not expose record import/export. | [`AUTH-EX-001`](01-accepted-architecture-baseline.md), [`ARC-CTR-008`](23-operations-security-contract.md) |
| `RZN-001-Q15` | Sufficiency and conformance require record-level IDs; contract/schema tests; image/Compose/SBOM/provenance checks; containerized unit, API, persistence, SDK, CLI, web, migration and recovery tests; clean-host Compose vectors; and traceable completion evidence. | [`ARC-CTR-009`](24-conformance-contract.md) |
| `RZN-001-Q16` | Released documentation and contracts use immutable semantic revisions. Clarifications that cannot change conforming behavior may increment the patch revision; additive behavior increments minor; breaking meaning requires a new major/API version. Implementation evidence proposes a successor and never edits history silently. | [`ADR-006`](09-ADR-006-contract-versioning-and-feedback.md) |
| `RZN-001-Q17` | Compose/runtime packaging, API, SDK, CLI image, and web assets are separate architectural components and independently verifiable outputs. Coordinated phases are allowed, but future work uses narrow initiatives unless a human-authorized scope assessment records an invariant-compatible exception. | [`ADR-007`](10-ADR-007-product-and-delivery-decomposition.md) |

## Additional baseline choices

In addition to the decisions above, this baseline fixes:

- the v1 HTTP resource paths, media types, status behavior, problem format,
  request IDs, and ETag rules in `ARC-CTR-002`;
- the invariant that CLI and web use those same `/api/v1` paths and semantics,
  with origin differences limited to their Docker network boundaries;
- filter, pagination-cursor, weak-snapshot, and boundary behavior in
  `ARC-CTR-003`;
- physical SQLite schema, pragmas, write serialization, migrations, integrity
  checks, and restore rules in `ARC-CTR-004`;
- SDK method and exception surfaces in `ARC-CTR-005`;
- CLI commands, output streams, and exit codes in `ARC-CTR-006`;
- browser state transitions and accessible interaction behavior in
  `ARC-CTR-007`; and
- operational limits and readiness/failure behavior in `ARC-CTR-008`.

The baseline also fixes the Compose service/network/volume graph,
container-only host prerequisite, image hardening, internal/public API origins,
containerized CLI invocation, maintenance mutual exclusion, build/test
containerization, and Docker-specific recovery/conformance behavior.

The NIST and HIPAA suites are the primary security invariants guiding both
architecture and realization. Architecture owns technical behavior only within
their future-development and evidence gates. These baseline choices have the
same accepted standing as the baseline decisions above and remain subject
to the suite's change-control process.

## Evidence limitations

- `RZN-001` is not implementation or completion evidence.
- No existing product was inspected or claimed to conform.
- No deployment benchmark, accessibility audit, package build, migration,
  backup restore, or end-to-end test has yet run.
- Future initiatives must supply that missing evidence rather than treating
  the detail of this architecture as proof of delivery.
- The decisions above are governed by this record and the cited architecture/
  security owners. Optional proposal wording alone cannot reopen an accepted
  decision.
