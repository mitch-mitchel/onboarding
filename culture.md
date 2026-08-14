# Culture

## Open Source by Default

Everything we build is public. Our repos, issues, PRs, and discussions are open for anyone to see and contribute to. This means:

- Write commit messages and PR descriptions as if a stranger will read them (they might)
- Don't put secrets, credentials, or internal-only information in code or issues
- Treat community contributors with the same respect as teammates

## Async-First Communication

We're a distributed team. Async is the default, not a compromise. You don't owe anyone an immediate response, and nobody owes you one. Get to messages during your next working block and trust that others will do the same.

**You never need to apologize for being offline.** "Sorry it took me so long, I was off yesterday" — you don't need to say that here. You were off, and that's completely fine. Set your Slack status proactively so people have context, and pick up where you left off.

### Keep knowledge in the open

We're an open-source org — our communication culture should match. GitHub is the paper trail. Decisions, context, and technical discussions belong in issues and PRs where they're searchable, public, and permanent. That way everyone benefits, including future teammates and the broader community.

- **GitHub Issues/PRs (preferred)** — Work items, technical discussions, decisions, anything someone might need to find later. This is the permanent record.
- **Slack** — Quick questions, social chat, day-to-day coordination. Ephemeral by nature — if something important comes out of a Slack conversation, move it to an issue or PR.
- **Email** — External contacts, HR, things that don't fit Slack or GitHub.

If a decision happens in a call or Slack thread, summarize it in the relevant issue or PR. The standard is: someone who wasn't in the conversation should be able to find and understand the decision later.

### Urgency escalation

Not everything is the same priority. Use the right level:

1. **Async (default)** — Post in Slack, email, or GitHub. The other person gets to it during their working hours. No expectation of a fast reply. This covers 95% of communication.
2. **Bump** — Need an answer and it's been a day or so? Send a friendly nudge. This is normal and encouraged — it's not passive-aggressive, it's good communication. "Hey, just bumping this when you get a chance" is always fine.
3. **Urgent** — Something is actively blocking you or a deadline is real and imminent. Say so clearly: "Need this by EOD" or "Blocked on X, can you take a look today?" If you can't reach someone, escalate to your manager — that's what they're there for.
4. **Emergency** — Production is down, security incident, something is on fire. Call or text your manager directly. This is the only tier where phone contact is expected.

If you're the one sending a message, **state the urgency up front.** "No rush" and "need by EOD" are both useful signals. Absence of a signal means async.

### Flex your day

We trust you to manage your own time. The expectations are simple:

- **Get your work done.** Deliver on your commitments.
- **Make your meetings.** Be present when the team needs synchronous time.
- **Put in your hours.** How you distribute them across the day is up to you.

Beyond that, structure your day however works for you. Early bird, night owl, midday gym break, school pickup at 3pm — all fine. You don't need to justify your schedule.

### Signal availability, don't explain absence

- **Use your Slack status.** "Heads down," "Out today," "Back at 2pm" — a quick status saves everyone from wondering.
- **Block focus time on your calendar** so meetings don't eat your deep work.
- **Turn off notifications outside your hours.** This is expected, not rude. Nobody should feel pressure to monitor Slack on evenings, weekends, or days off.
- **If you'll be slow to respond,** a quick heads-up helps: "Deep in a refactor today, slow on Slack." That's a courtesy, not an obligation.

### Meeting culture

- **Default to async first.** Before scheduling a meeting, ask: could this be a Slack thread or GitHub issue? If yes, do that instead.
- **Meetings need agendas.** Even a few bullet points help everyone come prepared and make the best use of the time together.
- **Summarize outcomes.** Decisions from calls go into the relevant issue or PR so nobody has to have been there to stay informed.
- **Record when practical** so teammates in different schedules can catch up.

## Code Review Culture

<!-- DRAFT skeleton — needs review before this is real. -->

<!-- TODO: turnaround expectations — same no-SLA async norm as everything else, or something firmer? -->

**Giving feedback:**

<!-- TODO:
- Blocking vs. non-blocking comments — do we mark which is which (e.g. a "nit:" prefix)?
- Any house convention for phrasing so feedback reads as collaborative, not personal?
-->

**Receiving feedback:**

<!-- TODO: pushback is normal and welcome — how do disagreements get resolved if reviewer and author don't converge? Third reviewer? Manager? -->

**Who reviews?**

<!-- TODO: day-one.md already flags that requested-vs-assigned reviewers varies by team — does this doc need an org-wide default, or just point there? -->

## Work, Right, Fast

Our development philosophy follows three stages, in order:

1. **Work** - Make it functional. Get a working solution first.
2. **Right** - Make it correct. Clean up the code, handle edge cases, add tests.
3. **Fast** - Make it performant. Optimize only after it works and is correct.

Each stage builds on the last. A working solution gives you confidence to refactor, and clean code gives you confidence to optimize.

## How Decisions Get Made

- **Technical decisions** happen in GitHub issues and PRs. Propose, discuss, build consensus.
- **Architecture decisions** involve the team. Open an issue, describe the options, tag people for input.
- **Small decisions** - if it's easily reversible, just do it. Open a PR and get feedback.

When in doubt, bias toward action. It's easier to iterate on something that exists than to debate something theoretical.

## Where to Ask Questions

| What                          | Where                                          |
| ----------------------------- | ---------------------------------------------- |
| Quick questions, social chat  | Slack                                          |
| Bug reports, feature requests | GitHub Issues on the relevant repo             |
| Code-level questions          | PR comments or GitHub Discussions              |
| HR, policies, time off        | [HR wiki](https://wiki.free.law/c/hr) or Slack |

No question is too basic. We all started somewhere, and asking early often saves everyone time.

**Timebox before asking for help.** If you're stuck, give it 30–60 minutes, then reach out to a teammate or set up a pairing session. A 5-minute conversation can often unblock hours of solo debugging — and that's a win for the whole team.

## When Things Get Difficult

<!-- DRAFT skeleton — needs review before this is real. -->

Our [Code of Conduct](CODE_OF_CONDUCT.md) applies to teammates and community contributors alike.

<!-- TODO: if a GitHub thread or Slack conversation turns unproductive —
- Move to a call instead of continuing in text?
- Give it a cooling-off period?
- Loop in a manager at what point?
-->

**Reporting a concern:** <!-- TODO: who do you go to, and how? -->

## Data Handling

See [Data Handling](data-handling.md) for where the "open source by default" line sits relative to the data our tools work with — code and discussion are public, but not everything that touches real records is.
