# Brief: a way back in for responders who've gone quiet

Draft for Helen Achebe · Rook Dispatch · working draft, not a commitment

## The problem, in one line
A responder whose pings are missed or turned down drops in rank. A lower rank means fewer pings. With fewer pings there's almost no chance to recover, because the score only goes up when a ping is *taken*. Today, being quiet is what keeps someone quiet.

## Who it's for
1. **Responders who've gone quiet** (R-labels in our data: four of 16 saw pings fall about 70% after 12 Aug, with over half of the remaining pings missed). Reached through the phone app.
2. **Their handlers** (Kip, Aunt Dot and others), who currently learn about it only when the responder complains or a ticket gets filed. Reached through the console.

## What changes once it ships
**Responder.** The app tells them plainly what's happening instead of silence: "You haven't been offered a callout in 6 days." They get a one-tap "I'm ready" that confirms they're reachable. Then the system gives them a real chance: a bounded number of re-entry offers on callouts near them, so a good answer can pull their rank back up.

**Handler.** The console shows a "gone quiet" marker on the responder's card, with the reason split out (pings sent, missed, turned down), so Kip sees it in days, not after a ticket. From there they can confirm the responder is ready or flag that something is wrong, such as a phone problem.

**System, underneath.** A missed ping stops being scored the same as a turned-down one (today both cost 0.12, per `history.py`). Silence stops being treated as a verdict.

## What it does not do
- **Doesn't revert 4.2** or change proximity weighting. The change was asked for, and the weights amplify the loop rather than cause it.
- **Doesn't just change a number.** A lighter penalty alone slows the slide but gives a stuck responder no way back.
- **Doesn't force anyone to accept** or guarantee anyone a callout. Re-entry offers are limited, and responders can still decline.
- **Doesn't touch the ping wait** (90 to 60 s). That gets its own test, one variable at a time.
- **Doesn't change `current_record()`.** Supply reads the Responder Availability Record, and its shape stays as is.
- **Doesn't identify anyone.** No cover-to-legal mapping (Security Policy 4.1). Reporting is aggregate or R/H labels only.
- **Isn't mutual aid** or Availability Confidence. They're related, and Availability Confidence is still marked Committed for 4.2 though it didn't ship, so it needs deciding with you separately.

## What we know, and what we don't
- *Confirmed in the data:* missed pings stepped from 2.3% to 18.0% on 12 Aug, including the 90 to 60 s change. Take rate on answered pings stayed flat (about 78%), so willingness didn't change.
- *Confirmed in the code:* nothing in `history.py` raises a score except a taken ping, and the 2019 decay TODO was never built.
- *Not yet known:*
  - Whether the quiet four are a delivery problem (sent vs delivered). Their first misses came right at the release, before any ranking loop could build.
  - How production stores scores (Wen Li).
  - Why out-of-area pings rose from 17% to 39% (Wen Li).

## How we'd know it worked
Quiet responders get pinged again within days, not weeks. The share of responders with 3+ days of no pings falls. Missed-ping tickets ("phone never goes off", 17 Aug onward) stop growing. Overall acceptance does not drop.

## Next steps
Before building: sent-vs-delivered from Ravi, Wen Li's intent on decliners, Marcus on feasibility. Sofia designs the two screens. I can also turn this into a clickable mockup of the phone card and the console marker.
