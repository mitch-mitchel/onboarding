# Day One

A numbered path from a fresh machine to your first open pull request. Half a day is a realistic target, and "done" means **productive on a first change** — not "finished reading."

Every step below has a **pass condition**, so you always know whether you're actually done with it. Work top to bottom.

| #                                     | Step                       | Done when                                                                        |
| ------------------------------------- | -------------------------- | -------------------------------------------------------------------------------- |
| [0](#0-fire-all-access-requests)      | Fire all access requests   | One batched message sent — then keep going while you wait                        |
| [1](#1-confirm-your-accounts)         | Accounts confirmed         | GitHub org (2FA on), Slack, Google Workspace, password manager                   |
| [2](#2-set-up-git)                    | Git setup                  | `ssh -T` greets your FLP user; git identity in your FLP directory is `@free.law` |
| [3](#3-install-your-toolchain)        | Toolchain                  | Python, Node, and Docker all answer from your shell                              |
| [4](#4-wire-up-your-editor)           | Editor                     | Saving a `.py` file reformats it with ruff                                       |
| [5](#5-set-up-claude-code)            | Claude Code                | `claude` starts authenticated; `/help` lists your FLP skills                     |
| [6](#6-clone-your-repo-and-bootstrap) | Clone your repo, bootstrap | The test suite passes locally                                                    |
| [7](#7-open-your-first-pr)            | First PR                   | CI green, open for review                                                        |

Steps 3–5 name **requirements**, not commands — "Python at the version your repo pins," rather than a specific installer. The per-repo pin files are the source of truth, which keeps this path workable on any OS, editor, and toolchain. FLP's common defaults get named; equivalents are welcome.

## 0. Fire all access requests

Access is the only thing here gated on another human, so send the requests first and keep working while they land. One batched message to your manager or onboarding buddy covers it:

- **GitHub** — invite to the [freelawproject org](https://github.com/freelawproject) and the team for your project
- **Slack** — workspace invite
- **Google Workspace** — your `@free.law` account
- **Password manager** — vault access
- **Claude Code** — a seat on the FLP team plan
- **Project credentials** — anything your repo needs that isn't public (staging access, API keys); your manager will know

**Done when:** the message is sent. Move on to step 1 and circle back as invites arrive.

## 1. Confirm your accounts

As each invite lands, sign in and finish setup:

- **GitHub** — accept the org invite and enable two-factor authentication; the org requires it
- **Slack** — set your display name, photo, and timezone, then introduce yourself in the team channel
- **Google Workspace** — send yourself a test message from your `@free.law` address
- **Password manager** — unlock the shared vault

**Done when:** you can sign in to all four, and your GitHub account shows as a member of the FLP org with 2FA on.

The other two requests from step 0 land later: your Claude Code seat gets used in step 5, and project credentials in step 6, when the repo's own setup docs tell you which ones it needs.

## 2. Set up git

Work through [Git Setup](git-setup.md) — SSH keys, global config, and hooks. If you use GitHub for personal projects too, the host-alias section keeps the two accounts from stepping on each other.

**Done when** all three of these pass:

- `ssh -T git@github.com-flp` greets your FLP GitHub username (use `ssh -T git@github.com` if you only have one account)
- `git config user.email`, run from a repo inside your FLP directory, prints your `@free.law` address — that confirms the `includeIf` include is resolving
- a commit whose message doesn't follow [Conventional Commits](https://www.conventionalcommits.org/) is rejected, which confirms the shared `commit-msg` hook is actually firing

That last check is worth doing deliberately. A hook that never fires looks identical to a hook that passes until a reviewer points it out.

## 3. Install your toolchain

Three tools need to be installed and callable from your shell. Use whichever manager you like — the goal is that versions come from each repo's pin files, so you never hand-pick a version per project.

- **Python** through a version manager that reads pin files. Repos declare theirs in `.python-version` or `requires-python` in `pyproject.toml`. Repos with a `uv.lock` install fastest with [uv](https://docs.astral.sh/uv/); `pyenv` and `mise` read the same pin files.
- **Node** resolved automatically on `cd`. FLP commonly uses [fnm](https://github.com/Schniz/fnm) (`eval "$(fnm env --use-on-cd)"` in your shell config); `nvm` and `mise` work the same way against `.node-version` or `.nvmrc`.
- **Docker** running locally. Several projects — CourtListener especially — run their services in containers. Docker Desktop covers macOS and Windows; on Linux, start the daemon as a service and add yourself to the `docker` group so you can run it without `sudo`.

These checks confirm the tools work — you're not matching any specific repo's version yet, since you clone in step 6.

**Done when:**

- `python --version` answers from your shell (some systems reserve bare `python`, so `python3 --version` counts too — a version manager typically gives you both)
- your Node manager switches versions on `cd` — make a scratch directory, drop a `.node-version` in it holding a version you don't currently have, and `cd` in
- `docker run hello-world` prints its success message

Step 6 is where you confirm these versions against the repo you actually work in. Right now the point is having the tools installed and wired into your shell.

## 4. Wire up your editor

We use [ruff](https://docs.astral.sh/ruff/) for Python linting and formatting, configured per repo in `pyproject.toml`. Any editor with a ruff integration is fine — VS Code with the [Ruff extension](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff) is the common setup, and PyCharm, Neovim, Zed, and Helix all have one.

Turn on format-on-save so formatting stops being something you think about.

**Done when:** you add some sloppy spacing to a `.py` file inside your repo, hit save, and ruff reformats it.

## 5. Set up Claude Code

FLP has a team plan for [Claude Code](https://docs.claude.com/en/docs/claude-code). Install it, then:

1. Run `claude` — first launch walks you through OAuth in the browser. Already installed from another account? Use `/login` inside the CLI to switch to your FLP seat.
2. Clone [claude-starter](https://github.com/freelawproject/claude-starter) and follow its README. It carries FLP's baseline: permission settings, the shared `commit-msg` hook from step 2, and skills like `/commit` and `/review-pr`.
3. Customize from there — the starter is a floor, not a ceiling.

**Done when:** `claude` starts without prompting you to log in, and `/help` lists the skills you installed.

A few working norms: read AI-generated code before you commit it, run the tests rather than assuming they pass, and keep sensitive data out of prompts. You own what you ship, the same as any code you typed yourself.

## 6. Clone your repo and bootstrap

Your manager will tell you which repo you're starting in. Clone it over SSH, using whichever host you configured in step 2:

```bash
# Multi-account setup — the host alias picks your FLP key
git clone git@github.com-flp:freelawproject/<repo>.git

# Single GitHub account — plain host, no alias
git clone git@github.com:freelawproject/<repo>.git
```

Using the alias when you didn't set one up gives you `Could not resolve hostname github.com-flp`. If you see that, you want the plain-host form.

From there, **the repo's own README and wiki are the source of truth** for setup — dependency install, services, environment variables, database seeding. Follow them rather than anything on this page; they're maintained by the people working in that code every day.

**Done when:** the repo's test suite passes on your machine.

If it doesn't, that's worth pausing on. Ask in Slack — and if the blocker turns out to be a gap or a stale step in that repo's setup docs, you've just found your first PR.

## 7. Open your first PR

One small PR exercises everything above at once: your SSH key, your git identity, the `commit-msg` hook, the test suite, CI, and the review flow. Doing it on day one means a misconfiguration surfaces now, in a throwaway change, instead of on day three in something that matters.

**Good first PR:** fix something you hit while following these docs — a stale command, a missing prerequisite, a broken link. You're the only person on the team who can see this repo with fresh eyes, and that view is worth capturing while you have it.

These invariants hold org-wide, on every FLP repo:

1. **Start from a filed issue.** No unfiled work. If there's no issue for what you're about to do, open one first — it's where the context and discussion live.
2. **Branch off `main`.** Nobody pushes directly to `main`.
3. **Conventional commits** — `type(scope?): description`.
4. **Reference the issue with a closing keyword** in the PR description (`Closes #123`) so it closes on merge.
5. **At least one review** before merge.
6. **CI green** before merge. Run lint and tests locally first; it's faster than waiting on the pipeline.

Some mechanics vary by team — board columns and statuses, branch-name shape, whether reviewers are requested or assigned, deploy and release flow. Your team's repo docs and your onboarding buddy are the guide there, and it's a good thing to ask about in your first week.

**Done when:** your PR is open, CI is green, and a review is requested.

## What's next

You're up and running. From here:

- Read [Culture](culture.md) — how we communicate, how decisions get made, urgency tiers, and flexing your day. It's day-two reading, and worth doing before your first week is out.
- Skim your repo's `CLAUDE.md` and `CONTRIBUTING.md` if it has them. That's where team-specific conventions live.
- Check the [HR section of the wiki](https://wiki.free.law/c/hr) for policies, benefits, and time off.
- Take the [Foundations of Legal Research](https://elearning.aallnet.org/products/foundations-of-legal-research) course — ask your manager or onboarding buddy about access. Good to knock out sometime in your first week. Take time to actually sit with the material rather than speed-running it — it'll shape how you think about the data our tools work with.

Anything on this page that didn't hold up for you is a bug in this page. Open an issue or a PR.
