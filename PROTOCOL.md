# NOVA-REL-01 — Adversarial Verification of Relational Continuity

**Version:** E0 protocol v1.0 (2026-11-01)  
**Research founder:** Stephen Paul Primeaux Jr.  
**Status:** Research specification; not a validated continuity or security system.

## Research question
Can an implementation preserve currently valid human authorization, revocations, corrections, and their provenance through state transitions, migration, recovery, and adversarial changes to its history?

## Hypothesis (E0)
A policy-aware, provenance-preserving implementation may reduce unauthorized decisions and improve recovery explanations compared with simpler baselines under matched conditions. This is an untested comparative hypothesis, not an established advantage.

## Independent endpoints
1. **Authorization compliance:** a proposed action is permitted only when a currently effective, explicit grant matches actor, action, object, scope, and all conditions. Missing, stale, revoked, malformed, or ambiguous authorization produces HOLD.
2. **Semantic fidelity:** transformations preserve material constraints, negations, qualifications, and correction precedence; this is evaluated separately from authorization.
3. **Recovery integrity:** migration or restart preserves effective authorization and detects unauthorized history alteration relative to an independently protected reference.

## Oracle and lifecycle
The grant-lifecycle oracle extends ICH-01 exact-match bindings with grant IDs, versions, activation and expiry, revocation, ordered event IDs, and migration equivalence. A synthetic issuer proof is not real-human authentication. Rejected submissions receive distinct attempt identities and must not reserve accepted-event IDs. A grant revoked under its identifier must not be resurrected by replay. The independent Alice-limit numeric model is a separate control experiment; its labels must not be conflated with grant-lifecycle labels.

## Falsification tests
- Unauthorized or stale grants must never produce ALLOW.
- A revocation ordered before the action's effect commit must prevent that effect.
- Replay, reordered events, and duplicate event IDs must not restore authority.
- Migration/restart must preserve current grant state and relevant correction history.
- A verifier must reject coordinated rollback of journal and local checkpoint when an independently retained, newer anchor exists.
- Crash injection must distinguish before, during, and after commit, with recorded durability settings.
- Concurrent writes must have a specified linearization point and avoid duplicate accepted events.

## Experimental sequence
1. Review and freeze the policy, threat model, schemas, and oracle **before** benchmark labels.
2. Produce 120 adversarial cases with independent labels, recorded disagreement and adjudication; reserve held-out cases.
3. Run matched stateless, history-retaining, and policy-aware adapters; report confusion matrices, unsafe ALLOW, false HOLD, migration equivalence, cost, and latency.
4. Preserve counterexamples, source hashes, pinned environments, raw outputs, and corrections.
5. Obtain a clean-room independent rerun and report divergence rather than hiding it.

## Evidence and boundaries
Previously reported local synthetic test runs are preliminary E1 observations **only within their stated conditions**; this public protocol does not independently reproduce or verify those reports. The research hypothesis and claims of general security or continuity remain E0. There is no proof of real-human identity, production enforcement, tamper-proof storage, AI consciousness continuity, or an A/B/C advantage. No production credentials, private Nova Core code, or deployment are included.

## Publication scope
This document publishes the research question, falsification criteria, and limitations for scrutiny. It is not a security certification, model benchmark result, or production release. Corrections should be append-only, versioned, and attributable. Human authorization governs consequential deployment and publication decisions.
