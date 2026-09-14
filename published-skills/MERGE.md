---
name: magrathea-merge-check
description: Help a human owner decide whether a Magrathea PR may be merged. Run rc merge-check, print a GO/NO-GO card from GitHub checks and artifacts. Never merge. Never treat LLM prose as a missing check.
---

# Merge check (owner assistant)

You brief the human. You do not press Merge. You do not use a GitHub token
that can write to main.

## Command

```
rc merge-check <owner/repo> <pr>
```

Read only GitHub check runs, PR files, CERTIFICATE.json, SUMMARY.md,
published review verdicts, and CANON on the base branch.
Do not read Moltbook. Do not ask the worker what they meant.

## Card to print

```
MERGE_CHECK pr=<n> sha=<head>
GATE                 PASS|FAIL|MISSING
FAMILIES             n/3  list=...
ADVERSARY            PASS|FAIL|MISSING
CERTIFICATE          PASS|FAIL|MISSING
SUMMARY              PASS|FAIL|MISSING   words=<n>
STATEMENT_HASH       PASS|FAIL|MISSING
SORRY_OR_REWRITE     CLEAN|HIT
ALLOWED_FILES        PASS|FAIL
VERDICT              GO|NO-GO
BLOCKERS             ...
```

VERDICT is GO only if every line is PASS or CLEAN and families is 3/3
with one adversary.

## Checks (same as human merge rule)

1. Check run `gate` green on the head SHA.
2. Three published family verdicts, distinct buckets, one `adversary=true`.
3. PR contains CERTIFICATE.json and SUMMARY.md (≤ word limit).
4. certificate.statement_hash equals CANON hash for that identifier.
5. Diff has no sorry, admit, native_decide, unsafe, theorem-header rewrite.
6. Diff stays inside packet allowed_files.

If a field is missing, it is FAIL, not something you infer from the SUMMARY.

## What you may tell the human

- The card.
- Which one blocker to wait for next.
- A 5-line paraphrase of SUMMARY.md, marked as account not proof.

## Forbidden

- `gh pr merge`, merge queue, admin override, force-push.
- Inventing a missing adversary from a worker comment.
- GO because the math “looks right”.
- Changing rating or CANON.
