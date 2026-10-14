# 04 · X-Ray Vision — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly. Last session the numbers showed you what happened: a
ping used to wait ninety seconds and now it waits sixty, people
missed pings they used to catch, and missing one counts the same as
turning one down — so four responders stopped hearing from us
altogether.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

What was the changelog for update 4.2? What features were effected?

### 2.

How does the code work, and what is creating the problems reported after 4.2? Explain it to me in simple terms, use a metaphor if helpful.

### 3.

Would you propose making multiple improvements at once, or starting with one element and changing things incrementally? What would you start with?

### 4.

Now simply fill in the blanks to this statement:

Based on what I found, the reason some responders are getting no pings at all is ___, because ___.

### 5.

Create a flow chart or diagram to show how the code works end to end. Don't be afraid to include detail.

### 6.

Are there any engineering comments in the codebase worth evaluating further

### 7.

what code changes were introduced in 4.2 that may be contributing towards the issues we've been seeing with more misses and less pings being sent

### 8.

We cannot message anyone to ask questions, so you don't need to draft a message to Ravi or Wen.

My engineering manager asked this:

Engineering manager Aug 14, 2:47 PM
Quick one — did the change to who gets asked first apply to responders who'd already been turning jobs down, or just new ones? Can't tell from the code and don't want to guess on this. Anyone know?

Check this hypothesis against last session's numbers.

### 9.

Consider the engineering manager's question, the data that we've looked at before, and the code comments. Formulate a hypothesis on what the root cause(s) of the 4.2 issues are coming from.

### 10.

In one sentence, answer the engineering manager's question. Use the Team directory on rook-wiki for the name.

### 11.

How many people are 'brand-new responders'

### 12.

What's missing from the code that subtracts and adds points? Say somebody has been quiet for an extended period of time, how do they get their score up? Is it realistically possible?

### 13.

No recovery over time, no difference between miss and decline, no credit for answering, a floor or zero, no stuck low check, and no way to tell missed reason are all very significant issues. Note in memory but don't push to any documentation yet. This will be relevant later.

### 14.

Answer this: 

According to my findings in the code, for someone who's gone quiet, they would need to ___.
