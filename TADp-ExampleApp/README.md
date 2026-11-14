# Record application example

This project defines a local record application with a shared HTTP API,
SQLite persistence, a Python SDK, a containerized CLI, and a browser interface.
Docker Compose is the supported application runtime.

Start with the [architecture suite](evidence/authoritative/architecture/00-architecture-suite-index.md).
The security policies constrain that baseline; realization inputs describe
candidate future work. No application initiative, delivered product, implementation,
conformance result, or release is recorded in this baseline.

## Project baseline

- [Architecture suite](evidence/authoritative/architecture/00-architecture-suite-index.md)
- [NIST-aligned security policy](evidence/authoritative/security/NIST/00-nist-security-policy-suite-index.md)
- [HIPAA-aligned security policy](evidence/authoritative/security/HIPPA/00-hipaa-security-policy-suite-index.md)
- [Realization inputs](evidence/non-authoritative/realizations/README.md)
- [Evidence protocol](evidence/authoritative/LLM/00_Codex_Invariant_Suite_Index.md)

Architecture and security records constrain future work. Realization notes
remain non-authoritative inputs, and none of these records accepts an
initiative or proves product delivery.

## Future work

Use the [project-local prompt workspace](prompts/README.md) and the
[initiative workflow](docs/development/initiative-workflow.md). Establish the
project profile, governing-revision adoption, and required coordination
records through the applicable workflow before initiative allocation.

The [six-delivery preparation prompt](prompts/create-v1.0-through-v4.0-initiatives.md)
describes proposed work; it has not been executed in this baseline.

## Project structure

| Directory | Purpose |
|---|---|
| [evidence/](evidence/README.md) | Current binding baselines and non-authoritative inputs |
| [initiatives/](initiatives/README.md) | Future bounded-work records |
| [products/](products/README.md) | Future delivered-output records |
| [prompts/](prompts/README.md) | Project-local instructions |
| [template/](template/README.md) | Protected reusable record and workflow library |
| [tools/](tools/README.md) | Installed verification and scaffold tools |
| [docs/](docs/README.md) | Protocol usage guidance |

Read [AGENTS.md](AGENTS.md) before changing project files. The installed
template library and authoritative Codex invariant suite remain protected.
