# Write a research brief on how one person can run a reliable multi-agent coding workstation that surv

- Mode: plan
- Date: 2026-10-28
- Limits: maxAgents 20, maxDepth 4, minDepth 0, branching 4, effort low, mergeEffort medium
- Stats: agents 5, splits 1, leaves 4, deepest 1, failed 0
- Tokens: 268,070

## Goal

Write a research brief on how one person can run a reliable multi-agent coding workstation that survives losing their laptop: backup, cloud workstations, agent coordination, cost control.

## Outline

```
1 Root [split 4]
  1.1 Backup and laptop-loss recovery [leaf]
  1.2 Cloud workstations for agent workloads [leaf]
  1.3 Coordinating multiple coding agents [leaf]
  1.4 Cost control for agents and infrastructure [leaf]
```

## Every node

### 1 Root (split, depth 0)

**Task:** Write a research brief on how one person can run a reliable multi-agent coding workstation that survives losing their laptop: backup, cloud workstations, agent coordination, cost control.

**Why:** The four areas need separate research with different sources, and they can be written independently and merged afterward.

### 1.1 Backup and laptop-loss recovery (leaf, depth 1)

**Task:** Research how a solo developer running multi-agent coding setups (e.g. Claude Code, Codex) can survive losing their laptop. Cover: what state to protect (git repos, uncommitted work, agent configs such as CLAUDE.md/AGENTS.md, skills, MCP configs, dotfiles, secrets); tools (git remotes, restic/borg/Backblaze, dotfile managers like chezmoi, secret managers like 1Password/Bitwarden CLI); how often to back up; and a tested restore runbook that targets under one hour to a new machine. Deliverable: a Markdown brief section with recommendations, a restore checklist, and limitations.

**Why:** One agent can cover this focused backup-and-restore topic in one sitting, so splitting it would only add overhead.

The work starts with a list of the state a solo multi-agent developer must protect: git repos and uncommitted or stashed work, CLAUDE.md/AGENTS.md, skills, MCP configs, dotfiles and secrets. Each item is then mapped to a tool: git remotes with WIP branches or push hooks, restic or borg to Backblaze B2, chezmoi for dotfiles and agent configs, and the 1Password or Bitwarden CLI for secrets. Backup frequency is set per tier (continuous push, hourly snapshots, daily offsite). The output is a Markdown brief section with recommendations, a timed restore checklist aimed at a working machine in under one hour (bootstrap script, chezmoi init, secret injection, repo clone, agent auth), and limitations: agent session history is not portable, OAuth re-login is manual, the restore has to be drilled to count as tested, and backups need encryption-key escrow.

### 1.2 Cloud workstations for agent workloads (leaf, depth 1)

**Task:** Research cloud workstation options for one person running several coding agents at once: GitHub Codespaces, Gitpod/Ona, Coder, DevPod, plain VMs (Hetzner, AWS, GCP) with Tailscale, and hosted agent sessions (e.g. Claude Code cloud sessions). Compare setup effort, persistence, reproducibility (devcontainers, Nix), access from any device, security, and how well each runs long agent jobs unattended. Deliverable: a Markdown brief section with a comparison table and a recommended setup.

**Why:** This is one comparison of a known set of options along fixed criteria, and one agent can do it in a single sitting.

Research each option: Codespaces, Gitpod/Ona, Coder, DevPod, VMs on Hetzner, AWS or GCP reached over Tailscale, and hosted Claude Code cloud sessions. Use their current docs and pricing pages, and score each one on setup effort, persistence, reproducibility (devcontainer or Nix support), access from any device, security model, and how well it runs long unattended agent jobs (idle timeouts, tmux, session limits). The output is a Markdown brief section with a comparison table and short notes on each option. It ends with a recommended setup: a devcontainer or Nix-defined Hetzner or cloud VM reached over Tailscale, running agents in tmux or worktrees, with hosted agent sessions for burst work, and states the cost and failure-mode tradeoffs.

### 1.3 Coordinating multiple coding agents (leaf, depth 1)

**Task:** Research how one developer can run several AI coding agents in parallel reliably: git worktrees, per-agent branches, task queues or issue-driven workflows, orchestration tools (tmux, subagents, workflow scripts), avoiding conflicts, review and CI gates, logging and session transcripts, and recovery when an agent or machine dies mid-task. Deliverable: a Markdown brief section with recommended patterns, failure modes, and mitigations.

**Why:** One agent can cover this coherent topic in one sitting, and splitting it would only add overhead.

The work means researching current practice for running parallel AI coding agents: one git worktree and branch per agent, issue- or queue-driven task assignment, orchestration options (tmux, subagents, workflow scripts, cloud sessions), and ways to avoid conflicts such as file ownership, small scoped tasks and frequent rebases. It then covers review and CI gates, logging and transcript retention, and checkpointing so work can resume after an agent or the machine dies, using pushed WIP branches, task state kept outside the laptop, and idempotent tasks. The output is one Markdown brief section that pairs each recommended pattern with its failure modes and their fixes, plus a short recommended setup for a solo developer.

### 1.4 Cost control for agents and infrastructure (leaf, depth 1)

**Task:** Research cost control for a solo developer running multi-agent coding: LLM pricing (subscription plans vs API), prompt caching, model tiering (cheaper models for subtasks), token budgets and usage monitoring, plus cloud compute and storage costs (auto-stop idle VMs, spot instances, backup storage pricing). Deliverable: a Markdown brief section with example monthly budgets for light, medium and heavy use, ways to cut cost, and dated pricing caveats.

**Why:** One researcher can cover LLM and cloud cost control in a single section; splitting it would only add overhead to merge the parts.

Doing this means looking up current pricing, each figure dated: Claude/OpenAI subscription plans against API per-token rates, prompt-caching discounts, batch pricing and cheaper model tiers. It also covers usage monitoring and budget tools (for example ccusage, console spend limits, per-agent token caps) and cloud costs: small VM hourly rates, spot discounts, auto-stop for idle machines (Codespaces, GCP Workstations, Coder) and backup storage pricing (B2, R2, S3 Glacier). The output is one Markdown brief section with light, medium and heavy monthly budget tables, a ranked list of ways to cut cost, and a dated caveats box noting that prices change often.
