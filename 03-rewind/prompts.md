# 03 · Rewind — prompts

**Context:** You joined Rook two weeks ago as PM on Dispatch.
Release 4.2 shipped on 12 August, just before you arrived, and
landed badly.

Last session you read four conversations and every support ticket
since 4.2 — and found the two piles did not agree.

At the end of the session, type wrap up, and Claude Code saves the
prompts you wrote yourself below — not the starter prompt — updates
CLAUDE.md, and saves your work to GitHub. By Module 6 this file is a
prompt library built from your own questions.

---

### 1.

Did this happen to everyone, or did it happen to some people much more than others? More specifically, looking at it as a time series—did individuals see more misses after they missed at least one? Did that rate increase as time went on?

### 2.

Is there anything else about these responders that stands out or would indicate why they are suffering disproportionately?

### 3.

I really want to build towards a single number that I can deliver to leadership that signifies this issue without needing to explain more. What would this one number be? Please verify this number and critique it to make sure that it is 'bulletproof'/

### 4.

Compare this to missed rates, taken, and turned down rates. I want to try to insulate the 90-60s change and see if there are trends that I can use to show that there is still a consistent environment. Focus on %s but also individual rows. Split by handlers and responders as well. Mess around, group different ways, mine for findings.

### 5.

So right now I have four primary findings:

* Responder's willingness is unchanged. The change in time naturally increases miss rates.
* The effect is uniform across time. 
* The 12 typical responders move together. 
* The out-of-area group from the four outliers appears to be a significant change. 


Check this plot out. Let me know your thoughts. Then, produce a concise less than 4 sentence final findings for reporting out to leadership.

### 6.

Compare the support_tickets table on rook-database against the pings table. Do they agree with each other? When did people start writing in, and when do the numbers actually move?

### 7.

Despite the previous PM saying things were quiet, what does the relative silence in tickets indicate? Use the ping data in conjunction with the ticket data to tell the story of 'silence'.

### 8.

Create a table that visualizes each responder and handler, their tickets, sentiment, misses, calls, and any other relevant data. I want to have an individual level visualization here.

### 9.

Make a plot that you think best tells the story of what the table is communicating here.

### 10.

Pick one responder from the file who went quiet. Follow their behavior week by week through July to present, in plain english. Show me pings, successes, misses, and any complaints.

### 11.

When this individual has gone quiet, what would need to happen for them to be pinged again?

### 12.

Why did this responder go quiet in the first place? What led to them being essentially deprioritized by the system?

### 13.

What product adjustments should happen (DO NOT MAKE ANY REAL CHANGES) to help 'level the playing field' and avoid this scoring collapse in the future?

### 14.

What is R07's name? Explain what happened to her in a single sentence to be reported to leadership.

### 15.

If I'd only asked for the number, not the rows, what would I have missed?
