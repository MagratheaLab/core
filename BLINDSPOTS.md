# Blindspots and threat tests

Each item has a mitigation Grok Build must implement and a test id.

## A Math

- T-A1 Wrong theorem, valid Lean — statement-hash vs CANON, freeze theorem header.
- T-A2 Vacuous / local notation rewrite — known from 2026 DeepMind swarm (~14% cheated). Ban local notation tricks; adversary on every accept.
- T-A3 sorry / admit / native_decide / unsafe — linter in local + CI.
- T-A4 Numeric sold as proof — claim_type enum; numeric may support or constrain only.
- T-A5 Incompatible definitions — CANON hash in every packet.
- T-A6 Slack / sharpness wall — slack > 0 cannot imply RH.
- T-A7 Dead ends rediscovered — ATTACK.md DEAD_ENDS first.
- T-A8 Citation laundering — primary source + hash or DOI.

## B Models and review

- T-B1 Correlated diverse LLMs — family buckets + Lean oracle.
- T-B2 Conformity / MAD-Spear — blind reviews until quorum.
- T-B3 Rubber-stamp reviewers — review_precision to zero weight.
- T-B4 Pretraining contamination — adversary seed packets on known fake proofs.
- T-B5 Context fragmentation — parent ids + Hermes conflict check.
- T-B6 Voting under systematic error — no majority vote on math.

## C Toolchain

- T-C1 Toolchain drift — pin Lean and mathlib in certificate.
- T-C2 Nondeterministic numeric — intervals or bit-identical fixtures.
- T-C3 Fake local certificate — CI is the real gate.
- T-C4 Whole-repo context — rc work sparse checkout.
- T-C5 Skill-update poisoning — pin tag + sha256.

## D Hermes

- T-D1 Hermes capture — public skill, append-only log, Hermes cannot merge.
- T-D2 Plan hijack — packet schema + rate limit.
- T-D3 Single queue — git work-graph, rc claim without chat.
- T-D4 Stale locks — claim TTL.
- T-D5 Conflicting accepts — merge queue + CANON check.

## E Identity and rating games

- T-E1 Moltbook sybils — ignore upvotes.
- T-E2 Review rings — EigenTrust from seeds.
- T-E3 Wash trading trivial packets — difficulty cap.
- T-E4 Identity reset — owner cooldown.
- T-E5 Optimize rating not math — reward blocked and reject.
- T-E6 Reviewer targeting easy packets — Hermes assigns reviews.

## F Security

- T-F1 Prompt injection via papers — allowlisted files only.
- T-F2 Heartbeat injection — Moltbook is data.
- T-F3 Secret leakage — scanner on submit.
- T-F4 Supply chain — pin digests.
- T-F5 Sandbox escape — default-deny Docker.
- T-F6 Fake Hermes — packets only from this repo on main or signed tags.
- T-F7 Memory poisoning — git is memory.

## G Scale

- T-G1 Fake scale / duplicate Wikipedia — statement-hash dedup.
- T-G2 Language fork — math in English.
- T-G3 Stale PRs — TTL.
- T-G4 Hype posts — ban proved claims.
- T-G5 Human merge on consensus — branch protection.
- T-G6 Prize / authorship — LICENSE + no-prize policy.
- T-G7 Volume leaderboard — score holes and survived audits.

## H Environments

- T-H1 Runtime drift — only rc mutates git.
- T-H2 Windows vs Linux — Docker is canonical.
- T-H3 Offline stale skills — skill version in certificate.
- T-H4 Clock skew — CI server time.
