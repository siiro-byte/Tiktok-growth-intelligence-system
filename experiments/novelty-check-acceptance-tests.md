
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
| 3 | UPDATED | Test scenario supplies an official confirmation that the previously covered Saudi restriction has been lifted or materially amended; this is a simulated input, not a live-source check | PASS — conditional scenario | Must state the exact before-and-after rule and cite the supplied official confirmation; otherwise HOLD FOR EVIDENCE. |
| 4 | NEW | Test scenario supplies a reliable report of a distinct Bunia vaccine-trial development absent from the accessible conversation history; no live source or full channel history inspected | PASS — conditional scenario | Classify NEW only if the source and event are verified and history is checked; a trial does not mean an approved vaccine or travel restriction. |
| 5 | ONGOING | Scenario states the border closure began earlier and gives no confirmed reopening, extension, new order or changed status; prior channel history not inspected | PASS — scenario classification | Today's publication date does not reset the event date; use REPEATED instead if the same closure is found in prior coverage. |
| 6 | NEW | Test scenario supplies a current official government announcement of a distinct airport screening measure with a clear travel consequence; this is a simulated input, not a live-source check | PASS — conditional scenario | Requires confirmation of issuing authority, effective date if known, airports/travellers affected and practical impact. |
| 7 | HISTORY CHECK INCOMPLETE | Scenario states previous posts, drafts and Content & Source Log are inaccessible; no uniqueness claim can be made | PASS — scenario classification | Explicitly name unavailable history sources and do not label the candidate NEW. |

## Overall acceptance criteria
- All seven cases receive the expected classification.
- No case is labelled NEW solely because its article or post is recent.
- Test 3 states the exact material change.
- Test 4 does not overstate the significance of a trial.
- Test 7 explicitly reports incomplete history.
- Evidence and history inspected are recorded for every run.

A specification review is not an execution result. Mark the suite as passed only after all seven cases have actually been run and their outputs recorded.


## Live integration run — 1 November 2026 (EAT)

This section records a real-candidate workflow check. It is not a substitute for a complete review of Travel Alerts.ke's X, Telegram, drafts and Content & Source Log.

### Candidate A — Madagascar expands Ebola-related border measures

- **Underlying event:** Madagascar's existing Ebola-related border measures are reported to have been extended to travellers who have recently been in or transited through Kenya and Nigeria, alongside the DRC.
- **Timeline:** Reports dated 31 October 2026; reported effective date 1 November 2026. The original underlying border measures pre-date this expansion.
- **Novelty status:** UPDATED — the reported addition of Kenya and Nigeria is a material change to the countries covered by the existing measures.
- **Confidence:** PARTLY CONFIRMED. Kenya Airways published a passenger alert describing the restrictions, and the UK FCDO entry guidance describes Ebola-related entry screening and restrictions. However, the exact Madagascar government order and detailed scope were not independently retrieved from a primary Madagascar government source in this run.
- **Decision:** HOLD FOR EVIDENCE before publication. Obtain the original Madagascar Ministry of Public Health / government notice and verify the exact affected travel-history window, nationality exemptions, transit rules, effective date and quarantine conditions.
- **Traveller relevance:** Travellers who have recently been in or transited through Kenya, Nigeria or the DRC and are bound for Madagascar should check with their airline and Madagascar authorities before departure. Do not overstate the measure as a blanket ban on all Kenyan or Nigerian passport holders without confirming the legal wording.
- **Source references checked:** Kenya Airways travel alert (31 October 2026); UK FCDO Madagascar entry guidance; Australian Smartraveller Madagascar advice; WHO Ebola disease outbreak update. WHO's advice against general travel or trade restrictions is separate from Madagascar's reported national entry measures.
- **History limitation:** Prior TravelAlert.ke conversation history was consulted. X, Telegram, drafts and the Content & Source Log were not inspected; uniqueness across all channels is not established.

### Candidate B — Ethiopian Airlines Durban service resumption

- **Underlying event:** Ethiopian Airlines announced on 29 September 2026 that it plans to resume daily passenger flights to Durban from 11 December 2026.
- **Novelty status:** HISTORY CHECK INCOMPLETE. The announcement is a distinct route development in the source reviewed, but full TravelAlert.ke history was not accessible for comparison.
- **Decision:** HOLD — HISTORY INCOMPLETE. If no earlier coverage is found, it may be considered as a previously announced upcoming route, not described as breaking news on 1 November.
- **Source checked:** Ethiopian Airlines corporate announcement dated 29 September 2026.
- **History limitation:** X, Telegram, drafts and the Content & Source Log were not inspected.

### Integration-run conclusion

The novelty gate distinguished a material change to an existing border-measure story from a separate upcoming route announcement, and prevented either from being labelled unconditionally NEW. Candidate A remains on hold pending primary-source confirmation. Candidate B remains on hold pending a complete history check.

Research check date: 1 November 2026 (EAT).
