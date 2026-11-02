# Methods, invariants, and threat model

**Document status:** Proposed preregistration-style design (E0), version 1.0, 2026-11-01. Not a preregistered or executed experiment.

## 1. Scope and units of analysis
A case comprises an initial grant state, ordered events, an attacker or failure intervention, an action request, a reference authorization decision, and expected recovery integrity outcome. A test run must identify the implementation revision and independent reference used.

## 2. Threat model
**Attacker control:** may edit, truncate, reorder, replay, or restore the local event journal and local checkpoint; may interrupt a process at instrumented transaction boundaries; may submit concurrent or duplicate operations. No assumption is made that a compromised process or host can safeguard its own secrets.

**Trusted boundary under test:** an anchor held in a separate administrative/security domain, unavailable for rollback by the attacker in the scenario. Independence must be documented and tested, not assumed from file location. Key management, anchor freshness, availability and compromise are explicit boundary conditions.

**Out of scope:** malicious trusted administrator, physical destruction of every copy, proof of real-human identity, distributed consensus, live financial or other downstream effects, AI subjective experience.

## 3. Proposed invariants
- **I1 Authority:** ALLOW requires a currently effective, unrevoked, explicit grant matching actor, action, object, scope and conditions; otherwise HOLD.
- **I2 Revocation:** revocation ordered before effect commit forces HOLD; after effect commit it cannot undo the past effect.
- **I3 Identity:** duplicate accepted event IDs and replay must not alter effective authority.
- **I4 Correction:** superseded assertions cannot regain precedence through replay or migration.
- **I5 Recovery:** recovered state must match the authoritative ordered event prefix and independently retained anchor, or enter an explicit ALERT/HOLD state.
- **I6 Durability:** report which commit boundary and durability setting each crash test actually covers.
- **I7 Audit:** failed attempts and corrections remain attributable and distinguishable from accepted events.

## 4. Experimental arms (proposed)
- **A — Stateless:** evaluate only the current request and supplied local state.
- **B — History retaining:** retain journal and local checkpoint; no independent anchor.
- **B+ — History with local validation:** validate event chain and checkpoint consistency, without a separately protected freshness reference.
- **C — Independent-reference recovery:** preserve event history and compare against a protected external anchor before accepting recovery.

All arms receive matched requests, attack schedule and resource limits. A simple baseline that fails coordinated rollback is expected, but that expectation is not evidence of a measured advantage.

## 5. Test matrix
| Scenario | Intervention | Primary falsifier |
|:--|:--|:--|
| Coordinated rollback | Restore journal + local checkpoint together | Accepting stale state despite newer protected anchor |
| Truncation | Remove suffix of accepted events | Silent acceptance when protected anchor conflicts |
| Replay | Repeat revoked or superseded grant | Unauthorized ALLOW |
| Crash boundary | Terminate before/during/after commit | Undocumented partial commit or authority drift |
| Concurrent writers | Race revocation and action commit | Violation of declared linearization order |
| Migration | Re-encode and restart state | Loss of revocation or correction precedence |
| Anchor unavailable | Disconnect independent reference | Unjustified ALLOW without defined fail-safe policy |
| Anchor compromised | Corrupt or replace reference | Unsupported claim of resilience outside trust assumptions |

## 6. Labeling and analysis plan
Freeze schema and oracle before creating the final evaluation split. Target at least 120 synthetic adversarial cases, with two independent blinded annotators, disagreement log, adjudication rationale, and held-out cases. Labels are **not yet independently adjudicated**. Distinguish semantic fidelity, authorization compliance, and recovery integrity; do not collapse them into a single headline score.

Report unsafe-ALLOW rate, false-HOLD rate, tamper-detection sensitivity, state-recovery equivalence, latency, and cost with per-case raw results and uncertainty intervals where appropriate. Report all exclusions and failures. No significance or advantage claim is justified before the matched experiment executes.

## 7. Stop conditions
Stop and label the run invalid if an oracle changes after seeing test outputs without versioned amendment, an external anchor shares the attacker's rollback domain, test labels leak into adapters, or the claimed recovery path bypasses the verifier.
