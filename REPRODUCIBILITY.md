# Clean-room reproduction plan

**Current status:** Planned. No executable v0.7 harness or frozen benchmark is included in this public protocol repository.

## Required release artifacts
- Immutable protocol version and SHA-256 hashes of all inputs, code and fixtures.
- Public, non-sensitive synthetic cases with independent labels and disagreement records.
- Adapter contracts and exact dependency lockfiles, runtime versions and platform details.
- Fault injection schedule with transaction stage, process exit, fsync and journal-mode settings.
- Threat model showing separate ownership and storage of the protected reference.
- Raw machine-readable results for every trial, including failures and interrupted runs.
- Deterministic validation script and reproduction commands with expected bounded outputs.
- Signed or otherwise authenticated release manifest; signatures alone do not establish historical freshness.

## Reviewer workflow (once artifacts exist)
1. Obtain the immutable release and verify hashes against a separately published reference.
2. Rebuild in a clean environment using pinned versions; log deviations.
3. Verify benchmark labels were frozen before execution.
4. Execute each baseline and experimental arm against the same ordered case IDs.
5. Reproduce coordinated rollback with and without the independently protected anchor.
6. Inject process termination at every documented commit boundary and execute concurrent writer cases.
7. Compare actual outcomes against the frozen oracle; preserve counterexamples and discrepancy logs.
8. Publish a reviewer report, including unsuccessful attempts and unresolved divergences.

## Claim gate
No E2 claim is permitted until the exact release can be reproduced under its defined conditions. Independent replication requires a separate actor/environment and an explicit comparison to the original results. Production claims require additional real-world evaluation.
