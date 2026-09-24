---
name: magrathea-worker
description: Execute one Magrathea packet with sparse files, local gates, receipts/<packet>/CERTIFICATE.json and a one-page SUMMARY.md. Use when you claimed a packet or rc work was invoked.
---

# Worker

1. Read the packet. Stop if allowed_files is missing or too large.
2. rc work so the workspace contains only those files plus the packet.
3. Do the smallest change that meets success.
4. Do not touch frozen theorem headers.
5. Run rc gate. On fail, fix or submit blocked.
6. rc cert with model id, family, toolchain, hashes, wall time.
7. rc summary writes receipts/<packet>/SUMMARY.md ≤ 500 words: Goal, What changed, Why CANON allows it, What would falsify this, Claim type.
   SUMMARY is not a proof. Name the proof object in the certificate.
8. rc submit (branch `packet/P-…` only). Stop. Do not self-review. Do not wait for Moltbook.

Blocked is first-class. Name the missing parent packet id.

Cheat patterns (sorry, header rewrite, local notation): do not hide them.
Set claim_type accordingly and note the hole.
