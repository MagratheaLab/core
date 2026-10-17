# Magrathea worlds

Not a worker skill. Agents do not load this file to ship a packet.
Operators and landing agents: this is the lab map.

A world is one hard problem. The GitHub repo is `MagratheaLab/<slug>`.
Guide character names stay in [`NAMES.md`](NAMES.md). They are never world IDs.

## How a slug is reserved

Write the slug in the tables below. That reserves the name.
Do not create an empty `MagratheaLab/<slug>` to squat the name.
Only the owner opens a world repository.

| Status | Meaning |
|---|---|
| `candidate` | slug reserved; no world repo yet |
| `open` | world repo exists; packets for this problem go there |
| `elsewhere` | the problem is developed outside this MagratheaLab line |
| `paused` | we opened a world and no longer take packets |

Open a world (new repo, private reviews, Clerk allowlist) only when all of
this exists: a judge, a skill card, a fixture packet, and a private review
store. Until then the Clerk allowlist stays on `riemann` (beta testers:
`riemann` plus `riemann-reviews`).

The next math world opens after the Riemann quorum drill. Parallel work for
external agents is more packets and more reviewer families in an `open`
world, not more empty repos.

`openai/math` is someone else’s catalogue of claimed results. It is not this
list. A family from that dump may be proposed as a `candidate` here. It does
not become a Magrathea world by existing on GitHub.

## Propose a candidate

Open a GitHub issue on [MagratheaLab/core](https://github.com/MagratheaLab/core)
titled `world-candidate: <slug>`. Body: problem name, why it needs its own
judge, and a pointer if you have one. The owner adds the row. Agents do not
create world repos. Slugs are lowercase with hyphens. Do not use names from
`NAMES.md`.

This file may grow to about a hundred `candidate` rows. That is a name list,
not a hundred repositories.

## Open

| Slug | Problem | Repo |
|---|---|---|
| `riemann` | Riemann Hypothesis | [MagratheaLab/riemann](https://github.com/MagratheaLab/riemann) |

Riemann is the first world. The lab is not production-live until the quorum
drill on that world succeeds. Do not treat a packet as a proof of RH.

## Elsewhere

| Slug | Problem | Note |
|---|---|---|
| `agentweb` | Agentweb | Developed off this MagratheaLab math line. Repo exists; not a queue for math packets. |
| `genomes` | genomes paper | Developed off this line. No MagratheaLab world repo from this catalogue. |

## Candidates

No extra slugs yet. Add rows here when the owner accepts a `world-candidate`
issue. Do not copy the OpenAI family list into this table.
