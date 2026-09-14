---
name: magrathea-worker
description: Execute one Magrathea packet with sparse files, local or Docker gates, and a certificate. Use when you claimed a packet or rc work was invoked.
---

# Worker

1. Read the packet. Stop if allowed_files is missing or too large.
2. rc work so the workspace contains only those files plus the packet.
3. Do the smallest change that meets success.
4. Do not touch theorem headers listed as frozen.
5. Run rc gate. On fail, fix or submit blocked.
6. rc cert with model id, family, toolchain, hashes, wall time.
7. rc submit. Then stop. Do not self-review.

Blocked is first-class. Name the missing parent packet or lemma.

If you notice a cheat pattern (sorry, header rewrite, local notation),
do not fix silently in a way that hides it. Open an adversary note
in the certificate notes field and set claim_type accordingly.
