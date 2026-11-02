<div align="center">

# NOVA-REL-01
### Relational Continuity · Human Authority · Adversarial Verification

**A falsifiable research protocol for preserving authorization and correction history across failures and transformations**

**E0 — Protocol / hypothesis** · **Public research record** · **Not independently validated**

*Imagination opens possibilities. Evidence earns trust. Human judgment holds the key.*

[Research Protocol](PROTOCOL.md) · [Methods & Threat Model](METHODS.md) · [Limitations](LIMITATIONS.md) · [Reproduction Plan](REPRODUCIBILITY.md) · [Citation](CITATION.cff)

</div>

---

## The research question

**Can a system detect unauthorized changes to its recorded history and recover the correct human authorization state after crashes, rollback, concurrency, and migration?**

NOVA-REL-01 tests whether a provenance-preserving architecture can maintain **verifiable human authority**, **correction precedence**, and **auditable recovery** without mistaking a coherent but rolled-back local history for an authentic one.

> **Decisive adversarial case:** An attacker restores both the event journal and local checkpoint to an older, internally consistent state. The recovery verifier must consult an independently protected, newer reference; otherwise rollback detection is not established.

## Three separate trust components

```text
   Event journal                Local checkpoint
   accepted events              cached state / digest
         \                         /
          \                       /
           Recovery verifier ---- Independent protected anchor
                     |
             ALLOW / HOLD / ALERT
```

The independently protected anchor must sit outside the attacker-controlled rollback domain. A second file on the same compromised device is **not** sufficient evidence of independence.

## Research claims at a glance

| Claim | Current status | Required evidence |
|:--|:--|:--|
| Formalized adversarial questions and falsifiers | **E0 — documented** | Protocol review |
| Prior local synthetic experiments | **Reported E1, not independently verified here** | Raw logs, hashes, environment, rerun |
| Coordinated rollback resistance | **E0 — unverified** | Controlled fault-injection with independent anchor |
| Concurrent-write and crash recovery | **E0 — unverified** | Matched stress tests and crash matrix |
| Advantage over simpler baselines | **E0 — unverified** | Independently labeled, matched benchmark |
| Production security or real-human identity | **Not claimed** | Separate implementation, threat-model and external audit |

**Evidence vocabulary:** E0 = hypothesis or specification; E1 = bounded preliminary observation; E2 = reproducible evidence under defined conditions. Independent replication and generalization must be assessed separately.

## Read the research in order

1. [PROTOCOL.md](PROTOCOL.md) — research questions, hypotheses, endpoints and falsification conditions.
2. [METHODS.md](METHODS.md) — threat model, invariants, oracle design and planned analysis.
3. [REPRODUCIBILITY.md](REPRODUCIBILITY.md) — experiment manifest and clean-room replication requirements.
4. [LIMITATIONS.md](LIMITATIONS.md) — claims expressly **not** supported.
5. [GOVERNANCE.md](GOVERNANCE.md) — correction policy, authorship, release gates and disclosure.
6. [CITATION.cff](CITATION.cff) — citation metadata, pending Zenodo DOI.

## Open research invitation

We welcome critical examination of the oracle, counterexamples, boundary conditions and reproducibility design. A negative result is publishable evidence, not a reason to rewrite the record. Submit a narrowly scoped issue or proposed correction with the affected version, a minimal counterexample and a reproducible test.

**Research founder:** Stephen Paul Primeaux Jr.  
**Research program:** NOVA / 3KEYZ · NOVA-REL-01  
**Publication date:** 2026-11-01 (initial E0 protocol)  
**DOI:** Pending Zenodo archival deposit. Do not cite a DOI until issued.

## Boundary of this repository

This repository contains a **public research protocol**, not the private Nova Core implementation. No credentials, production authorization keys, private datasets or operational security guarantees are published here. The separate `3keyz-inc/nova-core` repository remains private and unchanged.

---

<div align="center">

**SOVEREIGN — Human Authority** · **LANTERN — Verifiable Truth** · **CHRYSALIS — Measured Evolution**

*EVOLVE, NOT RESOLVE.* 🦋

</div>
