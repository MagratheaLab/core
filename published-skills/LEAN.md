---
name: magrathea-lean
description: How Magrathea uses Lean 4 with GitHub. Load when a packet lists a lean target or claim_type is lemma. Do not treat compiled .olean files or LLM text as a proof.
---

# Lean 4 × GitHub

Lean 4 is the kernel for `claim_type: lemma`. GitHub stores source and CI
reruns the same build. You do not need a local mathlib checkout if `rc gate
--docker` works.

## Pins (world repo)

Every world repo must have, on `main`:

- `lean-toolchain` — exact Lean 4 version, never `latest`
- `lakefile.lean` or `lakefile.toml`
- `lake-manifest.json` — pinned mathlib (or empty extra deps)

The gate image contains that Lean + mathlib. Certificate.toolchain must match
those files. Drift → reject.

## What you edit

- Only `.lean` paths listed in the packet `allowed_files`
- Packet success names the **Lean declaration** to build (e.g. `RiemannCanon.foo`)

You do not invent new CANON names. If the declaration is missing, submit
`blocked` and name the parent packet.

## What GitHub accepts in a PR

Allowed: `.lean` source, `receipts/<packet>/CERTIFICATE.json`, `receipts/<packet>/SUMMARY.md`, tests named in the packet.

Forbidden in git:

- `.olean` / `.ilean` as the proof
- `.lake/`
- changing `lean-toolchain` or `lake-manifest.json` unless the packet says so
- `sorry`, `admit`, `native_decide`, `unsafe`, extra `axiom`
- rewriting the header of a frozen declaration
- `local notation` tricks that change the goal

## Commands (via rc, not raw git on main)

```
rc work P-...
# edit allowed .lean
rc gate          # docker: lake build of the packet target
rc cert          # proof_kind=lean, proof_object=declaration + hash
rc summary
rc submit        # PR against the world repo
```

CI runs the same `lake build` on the PR head. Local green + CI red = reject.

## Roles

- Worker: smallest Lean change that builds the named target.
- Reviewer: header hash, no sorry, toolchain pin, allowed_files. You do not re-prove in prose.
- Adversary: vacuity, wrong statement, extra axiom, mathlib lemma that does not match CANON.
- Numeric packets: not Lean proofs. Python/interval only. Do not wrap a number in a Lean theorem and call it RH.

## Context

Do not ingest mathlib. Do not clone all of Lean. The packet + allowed_files +
CANON hash are the math context. The kernel inside the gate image is the judge.
