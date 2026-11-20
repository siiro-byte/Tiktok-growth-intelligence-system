
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

## Shared decision rules

Use the [canonical incident deduplication procedure](https://github.com/siiro-byte/Chatgpt.-Md/blob/main/TRAVELALERTS_RESEARCH.md#hard-stop-story-level-deduplication-2026-11-16). Run the history lookup early, then apply final novelty labels once confidence and material impact have been checked. Record claim confidence separately. Reject known repeats even with incomplete history. If no prior match is found and history is incomplete, assign `HISTORY_UNVERIFIED`; hold it outside the fresh shortlist and refer it to the editor.

Use canonical decisions in new results. Historical test labels map as follows:

| Historical label | Current decision |
|---|---|
| NEW | NEW_VERIFIED, after source verification and history checks |
| UPDATED | MATERIAL_UPDATE_VERIFIED, after verifying the exact before-and-after change |
| REPEATED | DUPLICATE_REJECTED |
| ONGOING | MONITOR_ONLY, or STALE_REJECTED if the item fails freshness |
| UNVERIFIED | MONITOR_ONLY, with claim confidence UNVERIFIED |
| HISTORY CHECK INCOMPLETE | HISTORY_UNVERIFIED when no match is found and relevant history is missing |

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
| Status | Canonical incident decision plus separate claim confidence |
| Decision | Shortlist, reject, monitor, or refer to the editor |
| Reason | Brief explanation |
| Evidence | Source links supporting the classification |

Finish with:
- Research checked at (EAT)
- History limitations
- Exact next action

## Handoff
Only `NEW_VERIFIED` and `MATERIAL_UPDATE_VERIFIED` enter the fresh shortlist. Carry the verified before-and-after change for updates. A shortlist decision does not authorize publication.

## Non-negotiable safeguards
- Never infer novelty from a fresh headline or publication date.
- Never claim a complete duplicate check when history was inaccessible.
- Never describe an ongoing situation as a new alert without a material change.
- Never invent a previous post, source, date, or comparison.
- Never allow quotas or pressure to publish to override evidence.
