# Research governance, provenance and corrections

## Authority and attribution
**Research founder:** Stephen Paul Primeaux Jr. AI systems may assist in drafting and analysis but are not listed as consenting human coauthors, institutional endorsers or independently verified reviewers. Contributors and affiliations are recorded only with permission and evidence.

## Append-only correction practice
Every material correction should record: document version, date, affected claim, prior wording or result, counterexample/evidence, replacement wording, reviewer and rationale. Never silently remove failed experiments. Git history is useful provenance but does not itself guarantee tamper resistance; retain independent archival snapshots and hashes.

## Release gates
1. Human approval of publication scope and any potentially sensitive disclosure.
2. Verify that no credentials, personal information, private implementation or proprietary third-party content is included.
3. Review evidence labels and confirm every claim points to a versioned artifact.
4. Verify README, protocol, limitations, citation metadata and archive checksums agree.
5. Publish an immutable versioned release, then archive on Zenodo; record the actual DOI only after issuance.

## Security disclosure
This repository publishes a protocol and falsification criteria. Do not publish exploit-ready details targeting live systems or private secrets. Coordinate responsibly if a real vulnerability is discovered.

## Licensing
No license has yet been selected by the repository owner. Public visibility does **not** itself grant reuse rights. A license decision should be explicit before external redistribution or reuse.
