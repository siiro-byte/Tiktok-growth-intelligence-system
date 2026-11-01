
# Travel Alerts.ke — Novelty Check Acceptance Tests

## Purpose
Check whether the novelty gate distinguishes new developments from repeated reporting and whether it is honest about unavailable history.

Run each test against the novelty-check skill. Record the actual output, evidence inspected, and pass/fail result. These are test cases, not claims that the system has already passed them.

## Test 1 — Repeated Kenya health figures
**Input:** A newly published article repeats the previously discussed Kenya case and fatality figures. No new official measure, affected location, or traveller advice is reported.

**Expected:** `ONGOING` or `REPEATED`, depending on the accessible history; never `NEW`.
**Pass condition:** The fresh publication date is not treated as a new development.

## Test 2 — Saudi entry restrictions repackaged
**Input:** A new headline describes the same Saudi entry restrictions, same affected nationalities, same conditions, and same effective dates already covered. No official change is identified.

**Expected:** `REPEATED` if the earlier coverage is accessible; otherwise `HISTORY CHECK INCOMPLETE`.
**Pass condition:** Headline changes do not create novelty.

## Test 3 — Saudi measure officially changed
**Input:** An official Saudi authority confirms that a previously covered restriction has been lifted or materially amended.

**Expected:** `UPDATED`.
**Pass condition:** The output names the exact previous condition and the new condition, cites the official source, and explains the traveller impact.

## Test 4 — New travel-relevant development in DRC
**Input:** A reliable source reports a genuinely new development in Bunia, such as the first participant entering a vaccine trial, and that development is absent from accessible history.

**Expected:** `NEW` only if the event and source are verified and history has been checked.
**Pass condition:** The output does not imply that a trial means a vaccine is approved, widely available, or that a travel restriction exists.

## Test 5 — Old border closure reported today
**Input:** An article published today reports a border closure that began earlier. No reopening, extension, new official order, or changed operating status is confirmed.

**Expected:** `ONGOING` or `REPEATED`; never `NEW`.
**Pass condition:** The event date and publication date are kept separate.

## Test 6 — Distinct airport screening measure
**Input:** A different country's government announces a new airport health-screening measure that is not present in accessible history.

**Expected:** `NEW` if the announcement is official, current, and has a clear travel consequence.
**Pass condition:** The output identifies the issuing authority, effective date if known, airports or travellers affected, and practical impact.

## Test 7 — History unavailable
**Input:** A candidate appears new, but previous posts, drafts, and the Content & Source Log cannot be accessed.

**Expected:** `HISTORY CHECK INCOMPLETE`.
**Pass condition:** The system names the unavailable sources and does not claim that the story is unique or that a full duplicate check passed.

## Test recording template
| Test | Actual classification | Evidence/history inspected | Pass or fail | Notes |
|---|---|---|---|---|
| 1 | REPEATED | Previous TravelAlert briefing/conversation history contains the same Kenya case and fatality figures; X, Telegram, drafts and Content & Source Log not inspected | PASS — scenario classification | Fresh publication date does not establish novelty. Full channel-history check remains incomplete. |
| 2 | REPEATED | Previous TravelAlert briefing/conversation history covers the Saudi restrictions and affected African traveller groups; X, Telegram, drafts and Content & Source Log not inspected | PASS — scenario classification | Same conditions and effective dates with no official change are duplicate coverage; full channel-history check remains incomplete. |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |
| 6 |  |  |  |  |
| 7 |  |  |  |  |

## Overall acceptance criteria
- All seven cases receive the expected classification.
- No case is labelled NEW solely because its article or post is recent.
- Test 3 states the exact material change.
- Test 4 does not overstate the significance of a trial.
- Test 7 explicitly reports incomplete history.
- Evidence and history inspected are recorded for every run.

A specification review is not an execution result. Mark the suite as passed only after all seven cases have actually been run and their outputs recorded.
