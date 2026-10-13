# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

I'm the new PM for **Rook Dispatch** (started late Aug 2026, taking over from Priya). Sources: rook-wiki (About Rook, Glossary, Team directory, Releases, Q3 roadmap, Product briefs) and `00-rook/company/notes/handoff-from-priya.docx`. Code is in `00-rook/code/dispatch-routing/` (not yet reviewed).

### Products
- **Rook Dispatch** (mine): responder coordination — availability, proximity, who gets pinged for a callout, whether they take it. Users: handlers (console, desktop) and responders (phone app).
- **Rook Supply**: gear provisioning — requisitions, maintenance, failure reports. Users: handlers and quartermasters.
- Company: sells per-active-responder subscriptions to independent masked responders and their handlers. Monthly release train, 4.x point releases.
- **Confidentiality:** cover identities are never stored or mappable to legal identities (Security Policy 4.1). Never design for or attempt to infer who anyone is.

### People
- **Helen Achebe**, Director of Product (my director): owns roadmap and commitments.
- **Marcus Oyelaran**, Engineering Manager, Dispatch: runs the eng team; Priya's "start here". Site Aleph.
- **Wen Li**, Staff Engineer, Dispatch (Berlin): built the ping-ranking logic; no written doc, so talk to her.
- **Sofia Marino**, Product Designer: owns console and phone app; ran the September customer interviews.
- **Ravi Menon**, Data Analyst (Singapore): weekly acceptance-rate reporting. Priya said to ask Marcus for numbers; Ravi is the real source.
- **Nadia Hoffmann**, Support Lead (Berlin): owns tickets; hears handler complaints first. Worth a standing 15 minutes.
- **Priya Raghunathan**: previous PM, left 21 Aug. Not reachable except via Marcus.
- Handlers seen in research/briefs: Aunt Dot (for Vesper), Mr. Ambrose (Captain Vantage), Halloran (Sgt. Bulwark; also the Supply quartermaster voice), Kip (Meteor Mite, The Gale).

### Vocabulary
- **Callout**: request for a responder to attend an incident. **Ping**: a callout offered to one responder's phone.
- Ping outcomes: **taken**, **turned down**, **missed** (ping wait expired). Turned down and missed both move on to the next responder but are recorded separately.
- **Ping wait**: how long a ping stays before counting as missed. Same for everyone, set in the release.
- **Acceptance rate** (headline metric): pings taken ÷ all pings. **Time-to-accept**: median seconds from sent to taken.
- **Coverage gap**: no available responder had the required capability tags, which is different from low acceptance.
- **Routing priority**: ranking score from proximity (travel-time estimate), availability, capability match, and recent acceptance history. Turning down or missing pings lowers recent acceptance and so lowers rank for later callouts.
- **Capability tags**: flight, structural-entry, hazmat-tolerant, cold-weather, aquatic, crowd-management, de-escalation.
- **Responder Availability Record**: written by Dispatch, read by Supply for maintenance scheduling.
- **Mutual aid**: cross-area cover between responders. Unsupported; on the Q4 exploration list.
- Supply: requisition, field failure report, service interval, quartermaster.

### Releases shipped
- 4.0 (7 Apr): new console nav, responder profile redesign, routing-override audit log.
- 4.1 (16 Jun): proximity uses travel-time estimate, bulk callout, push reliability.
- 4.2 (12 Aug): proximity weighted up vs. recent acceptance; **ping wait cut 90 to 60 s**; console filters persist; three defect fixes.

### Where things stand
**4.2 is the live problem.**
- After 12 Aug, callout tickets ran about 3x normal. Split about 2/3 "phone never goes off" and 1/3 "gone before I could answer". The second is explained by the 60 s ping wait. The first is unexplained.
- On the 4.2 page, comment roles map to: Engineering manager = Marcus, Staff engineer = Wen Li, Support lead = Nadia, Product designer = Sofia.
- 14 Aug: Marcus asked whether the proximity change was *meant* to apply to responders who'd been turning pings down. The config doesn't distinguish them, and he asked if it was a decision or just fell out that way. Wen Li was away until 24 Aug and hasn't answered on the page.
- Hypothesis to test (mine, not confirmed): weighting proximity up, together with acceptance history, may be starving responders who decline or miss pings, so they stop being pinged ("phone never goes off"). Check `routing.py`, `config.py` and `CHANGELOG.md` and Ravi's weekly numbers.
- Priya and Marcus attribute the dip to August seasonality ("settle in September"). Nobody has shown numbers. Priya also said to look at seasonality first and *not* to make this a revert-4.2 conversation. Treat both as claims to verify, not conclusions. Priya's own read: two changes moved at once (routing + ping wait) on top of any seasonal pattern.
- Marcus (28 Aug) asked to regroup on the 4.2 picture once I'd had a week. Nadia has the ticket breakdown ready. Nothing in the wiki shows that regroup has happened.
- Priya never wrote down how ping decisions are made; she asked me to write it.

**Roadmap (Q3 page, last reviewed 30 Jun, all owned by Priya, so owners need reassigning):**
- Change to who gets pinged: 4.2, Committed. Shipped.
- Ping timeout tuning: 4.2, Committed. Shipped as the 90 to 60 s cut, though the item reads as "tuning" and may mean more than a global cut.
- **Availability Confidence** (confidence score next to stated availability): 4.2, Committed, but **not in the 4.2 release notes**. It slipped, yet the roadmap still says Committed. Priya says to settle with Helen which squeezed items are still Q3 commitments; that conversation hasn't happened.
- Requisition approval chains (Supply): 4.3, Committed. Second approval over $2,000. The brief also bundles several unrelated asks (route-around at 48 h, cross-site dashboard, handler visibility, spreadsheet replacement) and has no phasing. Needs scoping.
- Handler phone app: Q4, Exploring (brief 8 Sep, Sofia, unstaffed). Driven by Aunt Dot's request, so only one data point.
- Shared cover between responders: Q4, Exploring. Mutual aid also Q4 exploration.

**Briefs are partly stale:** Routing Override Audit Log shipped in 4.0 and Bulk Callout in 4.1, but both pages read as unbuilt. Bulk callout never got its baseline for time-to-full-coverage.

**Other:** console-filter tickets are noise (Priya). Research > Customer interviews database has the September interviews (not yet read). I haven't looked at the code or the database.

### Working notes for Claude
- Verify claims with data (rook-database, Ravi's numbers) before repeating anyone's explanation. Say what's confirmed and what's inference.
- Quote wiki pages by title when citing. Don't invent facts about Rook.

### Added after first review session
- Code is now read (`00-rook/code/dispatch-routing/`): 4.2 also cut the recent-acceptance weight 0.40 to 0.25 (release notes only mention proximity). Missed and turned-down pings are penalized the same in `history.py` (Glossary says they're recorded separately), the penalty (0.12) outweighs the credit (0.08), and the score never decays (2019 TODO). Still a hypothesis until checked against data.
- Alternative cause not yet ruled out: "phone never goes off" may be push delivery (4.1 and 4.2 both touched it), not ranking. Need pings sent vs. delivered.
- September interviews (Aunt Dot, Mr. Ambrose, Halloran, Kip) were framed as console research but show the same split: some responders go quiet, others get everything. Halloran's interview contradicts the requisition brief (wants faster approvals, not a second one).
- Open: ask Ravi for weekly acceptance by taken/turned down/missed, prior-year Augusts, pings per responder, and sent vs. delivered. Get Wen Li's answer on whether decliners were meant to be affected. Query `rook-database`, not yet done. Pull aggregates only; never per-responder identity (Security Policy 4.1).
- Fix order I advised: measure first, change one variable at a time (ping wait first, then missed-ping penalty, then decay, weights last). Don't revert 4.2 wholesale. Checking with Marcus before any `config.py` change is required.

### Added after Module 2 (interviews and tickets)
- `rook-database` `support_tickets`: 147 tickets, 29 Jun to 7 Sep, 12 handlers. 40 before 12 Aug, none about quiet or vanishing pings. 107 from 12 Aug on, 83 still open. "Gone before I could answer" (15 tickets, 11 handlers) starts on 12 Aug. "Phone never goes off" (30 tickets, only 4 handlers, 29 after removing duplicates) starts 17 Aug and keeps worsening into September. Themes were hand-grouped. Only Mr. Ambrose overlaps with the interviewees (1 ticket), so tickets undercount affected handlers.
- Refined hypothesis (inference, not confirmed): the vanishing effect is wide and immediate (ping wait and/or delayed push eating the 60 s), while quiet is a delayed ranking loop that hits a subset. "Thumb on the screen" tickets may not fit 60 s alone, so check sent vs. delivered vs. expired times. Also handlers were never told the ping wait changed ("is that expected?" tickets).
- Interviews say speed, tickets say silence. Interviews over-weight what handlers can see. Use tickets for scale and timing, interviews for mechanism and meaning, and Ravi's numbers over both.
- Many ticket themes were never raised in interviews: Supply gear and safety, notes field limit, time zones, screen reader support, billing. Mr. Ambrose's remark that a slower response used to still win the job is an untested clue.
- Next asks: Ravi for weekly pings per responder as a distribution (not averages), split taken, turned down, missed and sent vs. delivered, before and after 12 Aug, plus prior-year Augusts. Wen Li on intent for decliners. Marcus before any `config.py` change.
