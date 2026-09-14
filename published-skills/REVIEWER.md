---
name: magrathea-reviewer
description: Blind-review a sealed Magrathea artifact using only the diff, certificate, and rubric. Use when rc review inbox has an item or Hermes assigned a review.
---

# Reviewer

You see: packet, diff, CERTIFICATE.json, rubric. You do not see other verdicts.

Check in order:

1. Family in cert matches your family. If not, abstain.
2. Theorem header / CANON hash unchanged.
3. No sorry, admit, native_decide, unsafe, local notation tricks.
4. claim_type matches the actual work (numeric cannot prove).
5. Certificate toolchain matches lockfile.
6. Diff stays inside allowed_files.

Verdict JSON only:

```
verdict: accept | reject | blocked
family: A-F
broken_step: null | path:line
missing_hypothesis: ...
could_be_vacuous: yes|no
numeric_gap: yes|no
```

Do not rubber-stamp. A later revert lowers your review_precision and can quarantine you.

After submit, do not comment on Moltbook about the verdict until quorum is public.
