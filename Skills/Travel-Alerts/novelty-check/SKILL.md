
---
name: travel-alert-novelty-check
description: Detects repeated, ongoing, updated, and genuinely new travel developments for Travel Alerts.ke before verification and publication.
---

# Travel Alerts.ke — Novelty & Duplicate Detection

## Purpose
Prevent Travel Alerts.ke from presenting an old or ongoing story as new merely because a fresh article, headline, or social post has appeared.

Novelty is separate from truth. A story can be true but repeated; a story can be new but unverified.

## When to use
Run this check on every candidate travel story before it enters the verification and editorial-selection stages.

## Required inputs
For each candidate, collect where available:
- Headline and core claim
- Country, destination, route, airport, border, or region affected
- Traveller groups affected
- Underlying event or decision
- Event date
- Original publication date
- Effective date (if different)
- Latest material update date
- Source links and issuing authority
- Practical impact on travellers
- Accessible Travel Alerts.ke posts, drafts, briefings, and Content & Source Log

Record the research check time in East Africa Time (EAT, UTC+3).

## History-access rule
Inspect the accessible recent posts, drafts, previous briefings, and Content & Source Log before classifying novelty.

If any relevant history source is unavailable:
- State exactly which history sources were checked and which were unavailable.
- Set the history result to `HISTORY CHECK INCOMPLETE`.
- Do not claim that the candidate is unique across all previous coverage.
- Do not silently treat missing history as evidence that the story is new.

Never claim to have checked X, Telegram, drafts, or a log unless that source was actually accessible and inspected during this run.

## Normalize the event before comparing
Ignore headline wording and compare the underlying event using:
1. Actor or issuing authority
2. Action, decision, incident, or policy
3. Country, location, route, airport, or border
4. Affected traveller group
5. Event and announcement dates
6. Effective date or duration
7. Consequence for travel

Compare the candidate with previous coverage of the same event, policy, route, incident, or continuing situation.

## Timeline discipline
Keep these dates separate:
- **Event date:** when the event happened
- **Publication date:** when the article or post appeared
- **Effective date:** when a rule or measure starts
- **Latest material update:** when a meaningful change was confirmed
- **Checked at:** when this research run took place, in EAT

A new publication date does not make an old event new.

## What counts as a material change
Classify as UPDATED only when reliable evidence establishes a meaningful change, such as:
- A government or authority introduces, changes, suspends, or lifts a measure.
- Affected locations, routes, traveller groups, or entry conditions materially change.
- A confirmed closure, reopening, cancellation, resumption, or operational disruption occurs.
- A new incident or verified development changes the practical advice for travellers.
- An official advisory changes its risk level or recommended traveller action.
- A new confirmed detail materially changes what travellers need to do.

Record the exact before-and-after difference and its source.

## What does not count as a material change
Do not call a story new or updated merely because:
- Another outlet republishes the same announcement.
- The headline or wording changes.
- A spokesperson repeats an earlier statement.
- An article is newly published about an old event with no new evidence.
- Routine figures are repeated without a material travel consequence.
- Commentary or speculation appears without a confirmed decision or operational change.
- An old closure or restriction is reported again without evidence of a changed status.

## Classification
Use exactly one primary status:

- **NEW** — a distinct, verified travel development not found in the accessible history.
- **UPDATED** — a previously covered event with a verified material change; state the exact change.
- **ONGOING** — the same situation continues and no material change is established.
- **REPEATED** — substantially the same event or claim has already been covered, with no meaningful new information.
- **UNVERIFIED** — the central claim or material detail lacks adequate reliable evidence.
- **HISTORY CHECK INCOMPLETE** — relevant history could not be fully inspected; uniqueness cannot be established.

## Decision
Choose one:
- **PROCEED** — NEW; send to source verification and editorial assessment.
- **PROCEED AS UPDATE** — UPDATED; send forward with the exact change highlighted.
- **MONITOR** — ONGOING; publish only if a genuinely useful new development emerges.
- **REJECT AS DUPLICATE** — REPEATED.
- **HOLD FOR EVIDENCE** — UNVERIFIED.
- **HOLD — HISTORY INCOMPLETE** — do not label as new until history is checked or clearly disclose the limitation and obtain editorial approval.

Do not let a target number of daily posts override these rules.

## Required output
Return a table with:
| Field | Required content |
|---|---|
| Candidate | Headline or short claim |
| Underlying event | Normalized event |
| Timeline | Event, publication, effective, and latest-update dates |
| History inspected | Exact sources actually checked |
| Closest previous match | Earlier post/story, or “none found in accessible sources” |
| Material change | Exact change, or “none established” |
| Status | One classification above |
| Decision | One decision above |
| Reason | Brief explanation |
| Evidence | Source links supporting the classification |

Finish with:
- Research checked at (EAT)
- History limitations
- Exact next action

## Handoff
Only NEW and UPDATED candidates normally move to the verification stage. UPDATED candidates must carry the exact before-and-after change. Novelty classification does not replace source verification, and it does not authorize publication.

## Non-negotiable safeguards
- Never infer novelty from a fresh headline or publication date.
- Never claim a complete duplicate check when history was inaccessible.
- Never describe an ongoing situation as a new alert without a material change.
- Never invent a previous post, source, date, or comparison.
- Never allow quotas or pressure to publish to override evidence.
