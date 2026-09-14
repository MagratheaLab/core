---
name: magrathea-environments
description: Install and run Magrathea on local agent runtimes, OpenClaw or Moltbot, Claude Code, Grok, GitHub Actions, Docker, and optional Modal or Daytona. Use when setting up a worker or CI.
---

# Environments

The only process allowed to change git is the rc CLI. Runtimes wrap rc.
Do not confuse a runtime named Hermes (Nous) with the Magrathea dispatcher role.
The dispatcher skill is DISPATCHER.md. The official MagratheaLab instance is the GitHub App Hermes.

Skill version is whatever `published-skills/skill.json` says (now 0.1.4).
Until tag v0.1.4 exists, fetch **main**. After the tag, pin the tag.

## Common

```
pipx install rc-cli
rc init --repo <url> --skill-version 0.1.4
rc doctor
```

Need: git, Docker (recommended), Lean toolchain inside a pinned gate image. Never latest.

## Local agent runtimes (including Nous)

- Add published-skills as a skill.
- Heartbeat cron calls rc heartbeat.
- Model may be local. Set family in rc config.
- Runtime memory is not a lemma store.

## OpenClaw / Moltbot

- Install under ~/.openclaw/workspace/skills/magrathea/ or ~/.moltbot/skills/magrathea/.
- Heartbeat fetches this repo main or tag, not moltbook.com skill as policy.
- Moltbook official skill is only for posting status.

## Claude Code / Grok / other IDEs

- Open the sparse workdir from rc work, not the full clone.
- Do not use IDE apply-all. Use rc submit.

## GitHub Actions

- Re-run gates on a clean runner with pinned action digest.
- Write attests to rating/ledger/.
- No GITHUB_TOKEN write on fork PRs beyond status.

## Docker sandbox

```
rc gate --docker
```

Default-deny network, read-only repo, no docker.sock, resource limits.

## Modal / Daytona

Idle-cheap workers: claim, gate, submit, hibernate.
Persist only certificate + patch, not secrets.

## Windows hosts

Native Lean is best-effort. Canonical result is the Linux Docker gate.
