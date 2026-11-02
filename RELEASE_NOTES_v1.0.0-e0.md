# Release candidate — v1.0.0-e0

**Title:** NOVA-REL-01: Adversarial Verification of Relational Continuity — E0 Protocol

**Authors / attribution:** Stephen Paul Primeaux Jr. (research founder)

**Release type:** Public protocol and methods specification; no executable v0.7 benchmark or independently validated results.

## Abstract
NOVA-REL-01 specifies a falsifiable adversarial research program to test whether a system can preserve current human authorization and correction precedence across restart, migration, concurrent writes, and malicious local history alteration. The central test restores both an event journal and its local checkpoint to an older, internally consistent state; a recovery verifier must detect the discrepancy against a separately protected, newer reference. The protocol defines authority and recovery invariants, matched baselines, a planned independent-labeling procedure, and explicit limitations. It makes no claim of production security, real-human authentication, independent replication, or measured advantage.

## Included public documents
- `README.md`: overview and evidence map
- `PROTOCOL.md`: hypotheses and falsifiers
- `METHODS.md`: threat model and evaluation design
- `REPRODUCIBILITY.md`: clean-room requirements
- `LIMITATIONS.md`: unverified and excluded claims
- `GOVERNANCE.md`: corrections, provenance, disclosure
- `CITATION.cff`: citation metadata
- `EDITORIAL_REVIEW_PROMPT.md`: independent critical review brief

## Integrity and correction policy
The release tag must identify a specific Git commit. Do not alter a published tag to replace results. Publish corrections as new versioned releases with a correction record. Keep failures visible. Verify archive checksums after Zenodo publication.

## Release steps requiring account interaction
1. In GitHub, select **Releases → Draft a new release**.
2. Set tag **v1.0.0-e0**, targeting the reviewed commit, title as above, and paste this document's abstract and limitations. Mark as **pre-release** because it is a research protocol, not validated software.
3. In Zenodo, enable the public repository under GitHub integration before publishing the GitHub release, or deposit a reviewed snapshot manually.
4. Confirm Zenodo created an archive and DOI; update citation metadata in a **subsequent** versioned commit, not by silently changing the release tag.

**DOI:** Pending; no DOI has yet been issued or verified.
