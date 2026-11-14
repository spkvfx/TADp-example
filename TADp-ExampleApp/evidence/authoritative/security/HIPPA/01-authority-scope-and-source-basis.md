# HIPAA policy authority, scope, and source basis

**Policy evidence ID:** `SEC-HIPAA-AUT-001`  
**Status:** Accepted prospective policy evidence  
**Revision:** `1.0.1`  
**Owner and accepting authority:** User, project authority  
**Related suite:** [`SEC-HIPAA-SUITE-001`](00-hipaa-security-policy-suite-index.md)  

## Purpose

This record defines the authority, evidence classes, legal-source snapshot,
scope decisions, and limitations of the demonstrator's
HIPAA-aligned policy. It prevents later work from mistaking prospective policy
for an implementation assessment or from treating general HIPAA alignment as
a compliance certification.

## Baseline authority and scope

The User is the accepting project authority for this limited, prospective
HIPAA-aligned policy. The suite selects architecture-relevant safeguards and
justifies them with the official HIPAA regulation and guidance identified in
the source baseline below.

The security policy guides architecture and realization within its scope; no
policy requirement may be changed to accommodate either. Architecture `2.0.1`,
NIST policy `1.0.1`, and this HIPAA policy `1.0.1` apply together with separate
ownership and additive evidence obligations.

This baseline does not authorize product behavior changes, implementation,
ePHI, regulated use, a current-state assessment, a HIPAA compliance claim,
changes to the protected Codex invariant suite or reusable templates, initiative
acceptance, or a product lifecycle transition.

## Architecture input and policy precedence

The accepted architecture describes the technical system being governed and
is input to scope selection. This HIPAA suite remains the primary invariant for
its security, data-use, safeguard, review, and evidence scope. Architecture
must conform to the policy; the policy is not revised to fit architecture:

| Architecture evidence | Controlling scope for this policy |
|---|---|
| [`ARC-SUITE-001@2.0.1`](../../architecture/00-architecture-suite-index.md), Purpose and architectural shape | One local Docker Compose record system; architecture is a future-product specification, not implementation evidence |
| [`AUTH-EX-001`](../../architecture/01-accepted-architecture-baseline.md), Applicability and claims `.1`, `.5`, `.6`, `.9`-`.13` | Local single-user, application-unauthenticated profile; API-exclusive SQLite; excluded remote/accounts/history; hardened container and named-volume requirements |
| [`ADR-004`](../../architecture/07-ADR-004-container-only-deployment-trust-model.md), Compose trust topology and application identity boundary | OS/Docker access is the human authorization boundary; administrators and Docker-daemon controllers are inside the trust boundary |
| [`ARC-CTR-001`](../../architecture/11-record-domain-contract.md), Public model and contract rules | Generic `name` and `value` can hold sensitive text; values and full names are sensitive by default and excluded from routine logs |
| [`ARC-BND-002`](../../architecture/12-api-service-boundary.md), Inputs/outputs and invariants | One request pipeline, exact Host/Origin controls, strict input handling, safe error/log output, and no remote authentication boundary |
| [`ARC-CTR-002`](../../architecture/13-record-http-contract.md), Protocol baseline and contract rules | Loopback/private HTTP only, no-store data responses, no application authentication, safe request correlation, and no audit-history claim |
| [`ARC-BND-003`](../../architecture/15-sqlite-store-boundary.md) and [`ARC-CTR-004`](../../architecture/16-sqlite-persistence-contract.md) | Named-volume state ownership, transaction integrity, maintenance exclusion, backup, restore, migration, and failure behavior |
| [`ARC-BND-004`](../../architecture/17-python-sdk-boundary.md) through [`ARC-CTR-006`](../../architecture/20-cli-interaction-contract.md) | Containerized client data paths, sensitive output boundaries, no local persistence, and no hidden credentials or alternate API |
| [`ARC-BND-006`](../../architecture/21-web-application-boundary.md) and [`ARC-CTR-007`](../../architecture/22-web-interaction-contract.md) | Same-origin browser, memory-only record state, no browser durable storage/telemetry/third-party content, and restrictive headers |
| [`ARC-CTR-008`](../../architecture/23-operations-security-contract.md) | Compose hardening, immutable artifacts, logging limitations, lifecycle, recovery, incident preservation, and the remote-use successor requirement |
| [`ARC-CTR-009`](../../architecture/24-conformance-contract.md), Current evidence status and delivery gates | Defines future verification vectors and expressly does not claim that D2-D6 implementation or conformance evidence exists |

No implementation observation was used to create this policy. The policy
describes what future work must preserve or prove.

## Applicable peer security authority

The existing
[`SEC-NIST-SUITE-001@1.0.1`](../NIST/00-nist-security-policy-suite-index.md)
is binding, directly applicable future-development security evidence. Its
[`SEC-NIST-POL-001`](../NIST/01-demonstrator-security-policy.md) defines the
local demonstrator's NIST-aligned product controls; its
[`SEC-NIST-MAP-001`](../NIST/02-nist-control-tailoring-profile.md) records
selected and deliberately tailored-out outcomes; and its
[`SEC-NIST-VER-001`](../NIST/03-future-development-assurance.md) defines
prospective evidence without assessing current work.

This HIPAA suite supplements that baseline. In particular:

- both suites prohibit regulated, production, remote, and multi-user use;
- both treat logs as privacy-aware diagnostics rather than per-user audit;
- both require immutable configuration, least privilege, bounded resources,
  supply-chain evidence, validated recovery, vulnerability response, and
  truthful future claims;
- HIPAA de-identification evidence does not override the NIST suite's separate
  prohibition on production records, confidential business data, or data
  requiring controls outside the profile; and
- host authentication, storage protection, screen locking, physical control,
  and media handling are inherited operator/organization dependencies to be
  documented and risk-assessed, not controls claimed as implemented by the
  demonstrator application.

The detailed cross-suite mapping is in
[`SEC-HIPAA-MAP-001`](03-control-rationale-and-traceability.md#cross-suite-compatibility).
An apparent peer-suite contradiction must be preserved and routed through the
invariant-conflict process rather than resolved by choosing the more
convenient text.

## Official HIPAA source baseline

The following sources were reviewed on 2026-11-10. Links identify the source
used; section numbers in the policy remain the precise legal locators.

| Source | Standing and use in this suite | Limitation |
|---|---|---|
| [45 CFR Part 164, Subpart C](https://www.ecfr.gov/current/title-45/subtitle-A/subchapter-C/part-164/subpart-C) | Current regulatory text for the Security Rule safeguards, organizational requirements, and documentation duties | The eCFR is authoritative but unofficial; applicability and legal interpretation remain the regulated entity's responsibility |
| [HHS Summary of the HIPAA Security Rule](https://www.hhs.gov/hipaa/for-professionals/security/laws-regulations/index.html) | Official agency overview confirming the rule currently in effect, safeguard categories, flexibility, and ongoing risk/evaluation duties | HHS states that the summary is not a comprehensive compliance guide and the regulation governs if they differ |
| [HHS Guidance on Risk Analysis](https://www.hhs.gov/hipaa/for-professionals/security/guidance/guidance-risk-analysis/index.html) | Official guidance for system-wide risk scope and the role of risk analysis in selecting safeguards | Does not prescribe one compliance method or validate this application |
| [HHS De-identification Guidance](https://www.hhs.gov/hipaa/for-professionals/special-topics/de-identification/index.html) and [45 CFR 164.514](https://www.ecfr.gov/current/title-45/subtitle-A/subchapter-C/part-164/subpart-E/section-164.514) | Source for Expert Determination and Safe Harbor and for the rule that data is not de-identified merely because identifiers seem absent | The generic record app neither performs nor certifies de-identification |
| [HHS Minimum Necessary Guidance](https://www.hhs.gov/hipaa/for-professionals/privacy/guidance/minimum-necessary-requirement/index.html) | Supports limiting unnecessary data, display, access, and disclosure during development and demonstration | The Privacy Rule has exceptions and organization-specific applications outside this suite |
| [HHS Breach Notification Rule](https://www.hhs.gov/hipaa/for-professionals/breach-notification/index.html) | Supports escalation when possible PHI is impermissibly used or disclosed and preserving the regulated entity's assessment/notification record | This suite does not decide whether an event is a reportable breach |
| [HHS encryption FAQ](https://www.hhs.gov/hipaa/for-professionals/faq/is-the-use-of-encryption-mandatory-in-the-security-rule/index.html) | Clarifies that addressable encryption requires a risk-based implementation or documented alternative decision | Does not make encryption optional without the required assessment |
| [HHS January 2026 system-hardening guidance](https://www.hhs.gov/hipaa/for-professionals/security/guidance/cybersecurity-newsletter-january-2026/index.html) | Supports patching, disabling unnecessary services, secure baselines, and vulnerability management as risk-management practices | Guidance is not a substitute for the regulation or an entity-specific risk analysis |
| [NIST SP 800-66 Rev. 2](https://csrc.nist.gov/pubs/sp/800/66/r2/final) | Nonbinding federal implementation resource connecting HIPAA safeguards to cybersecurity practices and NIST controls | NIST states that the guide assists understanding; it does not certify compliance |

### Rulemaking status

The [HHS Security Rule page](https://www.hhs.gov/hipaa/for-professionals/security/index.html)
and [HHS NPRM fact sheet](https://www.hhs.gov/hipaa/for-professionals/security/hipaa-security-rule-nprm/factsheet/index.html)
identify the January 2025 cybersecurity changes as a **proposed** rule and
state that the current Security Rule remains in effect. Proposed provisions
are therefore not represented as current legal requirements in this revision.
Every future policy acceptance and release review must verify the then-current
regulation and record whether this source baseline remains current.

## Included safeguard subjects

This suite includes only subjects directly connected to the accepted app:

- data classification and a synthetic/de-identified-only development profile;
- security responsibility and application-specific risk management;
- the OS/Docker identity boundary and local single-user access;
- loopback/private-network transmission confinement;
- minimum data, safe display, caching, diagnostics, and output;
- container, dependency, image, and configuration hardening;
- record/store integrity, conditional changes, and maintenance exclusion;
- diagnostic logging, activity review, and the absence of a HIPAA audit claim;
- backup, restore, emergency access, and incident evidence preservation;
- the local workstation, physical exposure, backup media, and disposal;
- external services and business-associate escalation;
- future verification, documentation, source currency, and exceptions; and
- the successor-architecture gate for any ePHI or remote/multi-user use.

## Excluded organization-wide subjects

This limited suite does not define an employer-wide sanction program,
enterprise workforce clearance process, facility security program, clinical
records retention schedule, patient rights process, Notice of Privacy
Practices, full business-associate agreement language, breach-notification
decision process, disaster-recovery program for other systems, or compliance
officer charter. A regulated entity remains responsible for every requirement
that applies to it. None of these exclusions may be cited as an exception to
law.

## Key interpretations

### HIPAA-aligned is not HIPAA-compliant

The suite uses selected HIPAA requirements to shape future development. HHS
explains that compliance is organization-specific and ongoing, involving risk
analysis, reasonable and appropriate measures, documentation, and periodic
evaluation. A repository policy or passing product test cannot establish the
regulated entity's overall compliance.

### De-identification is an evidence claim

Only synthetic data, or data supported by a documented Expert Determination
or Safe Harbor process under 45 CFR 164.514, may enter the accepted profile.
Free text can contain direct or contextual identifiers, so a developer's
inspection, redaction guess, UUID substitution, or "test" label is
insufficient. If the evidence is absent or ambiguous, future work must treat
the data as possible ePHI and keep it out of the app.

### Local confinement is not a substitute for regulated-use controls

Loopback publication, private networking, a unique OS account, and hardened
containers reduce the demonstrator attack surface. They do not supply
application authentication, role authorization, per-user audit attribution,
application-level encryption at rest, or TLS. This is why the profile excludes
ePHI and why any regulated-use request returns to architecture design.

### Addressable does not mean optional

Future work must follow the assessment and documentation process in 45 CFR
164.306(d)(3). A developer may not omit an addressable safeguard merely
because the regulation uses that label. This suite's ePHI prohibition cannot
be waived through an addressable-specification rationale.

### RZN-001 standing

[`RZN-001`](../../../non-authoritative/realizations/v0.0/RZN-001-example-record-application.md)
supplies requested intent and source questions as non-authoritative proposal input. It is not a legal or
security source and cannot override this policy, its permitted data profile,
or `SEC-HIPAA-GATE-001`. Architecture `2.0.1` is likewise constrained by those
requirements.

## Conflict and revision rule

If a future policy interpretation appears to conflict with the accepted
architecture, preserve both claims and use the repository invariant-conflict
process. The policy remains primary for its scope: revise the architecture
through an explicitly accepted successor when needed, and never weaken this
policy to make an architecture or product pass. If external law changes, record the
new source and effective date, identify the exact affected policies, and
obtain explicit authority for a compatible successor revision.
