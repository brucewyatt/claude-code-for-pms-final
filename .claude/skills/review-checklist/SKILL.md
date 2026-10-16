---
name: review-checklist
description: Reviews a product brief against the PM's standing checklist before it goes any further. Use when the user says "review this brief", "run the review checklist", "check this brief", or points at a brief file or page and asks whether it's ready.
---

# Brief review checklist

Run the same six checks, in the same order, on any brief the user points at. Do not rewrite the brief. Report what passes, what doesn't, and the smallest fix for each gap.

## Before you start

1. Identify the brief: a file path, a wiki page title, or pasted text. If it's unclear which, ask once.
2. Read the whole brief, start to end, before judging anything.

## The six checks

For each check, give a verdict of **Pass**, **Partial** or **Fail**, quote the line that supports it (or say it's missing), and, if not a Pass, give one concrete fix.

1. **Owner.** The brief names who owns it: a specific person or role accountable for it, not just "the team". Look for who owns the outcome as well as who writes it.
2. **How we'll know it worked.** There is a stated measure of success, with a metric, a target or threshold, and ideally a time frame. "Improve the experience" is a Fail.
3. **Scope matches.** Compare the scope stated at the start (goals, what's in and out) with the scope at the end (deliverables, next steps, asks). List anything that appears at the end but not the start, and anything promised at the start that never comes back. Any mismatch is a Partial at best.
4. **Problem before fix.** The problem is explained before any solution is proposed. Flag solution language ("we'll build", "add a", "change X to") that shows up ahead of the problem statement, or a problem that is really just the solution restated.
5. **Data point with a source.** The brief cites at least one data point (a number, a verbatim quote, or another concrete form of evidence) and says where it came from. Check the source is named well enough to find it again: a page title, table, interview, ticket set, report or date. A number with no source is a Fail. If you can verify the source with the tools you have, say whether it matches; if you can't, say it's unverified rather than assuming it's right.
6. **Why it matters, and what success looks like.** The brief says why the problem matters (who is affected, what it costs, what it blocks) and describes what success looks like in terms of the people or outcome, not just the feature shipping. Check this is separate from check 2: a metric alone doesn't say why it matters.

## Output format

Start with a one-line verdict: **Ready**, **Ready with fixes** or **Not ready**, with a count such as "4 of 6 pass".

Then a table:

| # | Check | Verdict | Evidence (quote or "missing") | Fix |
|---|-------|---------|-------------------------------|-----|

After the table, add:

- **Biggest gap**: the one fix that matters most before the brief goes further.
- **Unverified**: any claim, number or source you could not confirm.

Keep it short. Do not praise the brief, pad the table, or add checks beyond these six. If the user wants a rewrite after seeing the review, they will ask.
