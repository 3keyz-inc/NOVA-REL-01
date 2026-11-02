# Limitations and disclosure

- **E0:** This is a proposed research protocol, not a validated implementation.
- Earlier E1 local observations were reported in separate disposable environments; this publication does not contain independently verified raw runs.
- Synthetic HMAC issuer proofs demonstrate test-key possession, not a real human's approval.
- Hash-linked logs alone cannot detect coordinated rollback of both the log and a local checkpoint.
- An independently protected anchor, trustworthy recovery policy, and explicit threat model are required to evaluate rollback resistance.
- Crash-after-commit tests are not equivalent to power-loss or mid-transaction fault injection.
- Sequential multi-connection tests are not simultaneous concurrency tests.
- No real downstream effects, independent replication, held-out A/B/C benchmark, production deployment, or security assurance is claimed.
- The 120-case benchmark is **unfrozen**; no independent gold labels have been certified.
- The protected `3keyz-inc/nova-core` repository is intentionally excluded and remains private.
