# RateMyDOT trust ledger

Daily Merkle roots anchoring RateMyDOT's append-only review chain (reviews,
revisions, moderation actions, carrier responses). Published here — a
repository outside RateMyDOT's application infrastructure — so that neither
carriers nor RateMyDOT itself can silently alter or remove a published review
(chain design: PRD-08; Invariant 3).

- One file per day under `anchors/YYYY-MM-DD.json`: `{anchor_date, merkle_root, prev_root}`.
- `prev_root` must equal the previous day's `merkle_root` — a broken link is a red flag.
- Independent verification: `scripts/rmd-verify.ts` in the main repo recomputes
  every published review's content hash and the anchor chain from public data
  alone. No key, no account.

This ledger proves alteration-freedom of what was published. It does not — and
cannot — prove completeness.
