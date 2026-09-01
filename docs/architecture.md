# Architecture and Control Boundaries

RFP Engine coordinates probabilistic model work inside deterministic application controls. Agents may propose analysis and content; application services own authoritative state, validation, lineage, review routing, and human authority.

## Execution model

1. Source files are registered, hashed, stored, extracted, and normalized.
2. The engine constructs versioned requirement and package-input inventories.
3. The controller selects the next eligible operation from authoritative state.
4. A context builder projects only the information permitted for that operation.
5. The agent returns structured output validated against its contract.
6. Domain services determine whether the result may change authoritative state.
7. The Opportunity Record is committed atomically with optimistic concurrency control.
8. Generated files are stored immutably with provenance and source-revision lineage.
9. Human input resumes affected work and is recorded as opportunity-specific authority.

## Responsibility boundary

| Concern | AI-assisted responsibility | Deterministic responsibility |
|---|---|---|
| Intake | Interpret solicitation content | Register source identity, hashes, and revisions |
| Drafting | Produce grounded candidate content | Enforce context, schema, evidence, and authority |
| Review | Identify weaknesses and corrections | Route stages and bind results to exact versions |
| Assembly | Assist with content readiness | Render, hash, version, and record package manifest |
| Submission | None | Require explicit approval and an exact package match |

## Authoritative state

Opportunity Record revisions are immutable. A database transaction advances the authoritative revision only when the caller supplies the expected current revision. Canonical serialization produces a SHA-256 checksum used to verify state integrity.

This prevents conversational or in-memory output from silently becoming authoritative. Following a restart, the application resumes from the latest verified committed revision.

## Artifact lineage

Stored artifacts retain opportunity identity, logical key, version, media type, checksum, byte size, source revision, and provenance. Blob bytes can be reused by content hash while the artifact records remain independently versioned.

## Review and package integrity

Pink and Red operate on draft state. Candidate Package Assembly produces a versioned manifest and rendered artifacts. Gold evaluates an exact package. Final human authorization records the package ID, version, and checksum. Submission closeout rejects a mismatch.

## Model runtime

Model-backed operations use structured outputs and versioned agent contracts. Least-permissive context projection fails closed when required information is unavailable or incompatible with the expected schema. A deterministic test registry allows workflow behavior to be exercised without external model calls.
