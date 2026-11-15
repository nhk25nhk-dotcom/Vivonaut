 # Vivonaut – SCIENCE_MAP.md

Merged science map for the NASA Space Apps Challenge 2026 project "Vivonaut – Your Intelligent Health Companion in Space".
Merges: 01 Radiation, 02 Gravity fields (microgravity), 03 Isolation and confinement, 04 Distance from Earth, 05 Hostile and closed environments, 00 Reference ranges.

Status: all five NASA hazards researched; reference ranges done. Planning material, allowed before the hackathon starts. Written 10 Nov 2026. Revised the same day (v1.1) after the team review: radiation values no longer open the emergency screen, data-state and measurement-context rules added, MVP build set added.

**Final status (15 Nov 2026):** this file was the source of every number, rule and source code used in the application. Part G lists the source checks and their status at the time of writing. A rule without a verified source is labelled DEMO in the application and is never attributed to NASA. Simulated values (including radiation dose) are always labelled as simulated.
Revision v1.2 — 13 November 2026: Part G items 1–2 reviewed; source codes retained, direct NASA/journal references substituted, associated claims corrected. See Part I for the audit trail and limitations.
Revision v1.5 — 14 November 2026 (final record): Part J added for the simulated Blood results screen (Phase 6B) and the Viva Intelligence wording rules (Phase 6C). No number, threshold, rule or source code in Parts A to I was changed.
Revision v1.3 — 14 November 2026: Part G item 18 and one rule in F1 added for the roadmap-only Point-of-Care Blood Analysis Concept. No number, threshold or source code was changed; the DATA-4 wording follows the dashboard-first entry.

This file is the implementation reference. The six detail files and their sources stay in the project as the evidence. If an error is found in a number or a source, correct this file and cite the source; never ignore the source. Part G lists every reconciliation made when merging.

## How to use this file

- At build time (from 14 Nov, 9:00 am) give Claude: PROJECT_BRIEF.md, STATE.md and this file. The targeted source audit below covers Part G items 1–2; other open questions still require review.
- The app's Sources page must list every source code used in the UI (Part H).
- Every number that appears in the app carries one of three type tags:

| Tag | Meaning | Rule |
|---|---|---|
| **SOURCED** | Published by a named source (NASA, MedlinePlus, NIDDK, AHA/ACC, study) | Shown as "Reference: <source>". General Earth-adult values are **not** spaceflight-validated unless the source says so |
| **DEMO** | A value or rule we chose to make the prototype work | Always shown with "Demo rule". Never attributed to NASA. Not clinically validated |
| **BASELINE** | The astronaut's own normal from their own readings | Used for change detection only |

Source-code prefixes: S = radiation, M = gravity fields, I = isolation, D = distance, E = closed environment, R = reference ranges.

---

# Part A – Master matrix

Chain required by the brief: hazard → health concern → indicator → monitoring method → action → source → feasibility.
Tier: 1 = Core MVP, 2 = Extended prototype, 3 = Future roadmap (shown honestly as roadmap).

## A1. Hazard 1 – Space radiation

| Concern | Indicator | Monitoring method | Viva action (cautious) | Sources | Tier |
|---|---|---|---|---|---|
| Cancer risk (late, years) | Cumulative dose (mSv) vs 600 mSv career limit | Typed from dosimeter, or **simulated** (always labelled) | Planning notice at 50/80/100% of limit; notify flight surgeon and mission planners | S1, S3, S7 | 1 |
| Acute radiation syndrome after a large solar event | SPE alert state, event dose (mSv), early symptom checklist | Button in demo, typed dose, tap symptoms | Go to shelter, log symptoms with times, contact flight surgeon; any drug treatment follows mission protocol | S7, S10–S13 | 1 |
| Central nervous system effects | Reaction check vs own baseline (demo) | Touch game | Trend only; persisting change → flight-surgeon review | S1, I10, I12 | 1 (demo) |
| Degenerative tissue (heart, cataract) | Vision questionnaire; HR and BP trend | Tap, typed | Long-term trend only; persistent change → review | S4 | 1 |

## A2. Hazard 2 – Gravity fields (microgravity and partial gravity)

| Concern | Indicator | Monitoring method | Viva action | Sources | Tier |
|---|---|---|---|---|---|
| G1 Bone loss | Exercise minutes (bone density cannot be self-measured); optional back or bone pain | Typed or tap | Exercise reminder; show bone loss as educational context only | M1–M5, M8 | 1 / optional |
| G2 Muscle atrophy | Exercise minutes per week | Typed or tap | Friendly reminder, never punishment | M6–M8, M12 | 1 |
| G3 Cardiovascular deconditioning, orthostatic intolerance | Resting HR and BP with posture; "dizzy when standing?" | Typed, tap | Sit or lie down, ask crew for help, follow mission protocol | M9, M14–M16 | 1 |
| G4 Spaceflight-associated eye changes (SANS) | Vision questionnaire (near blur vs mission start, double vision, flashes) | Tap | New or worsening change → Needs assessment, contact flight surgeon. No score, no diagnosis | M17, M18 | 1 |
| G5 Space motion sickness, balance | Motion-sickness scale 0–10 in first days and after landing | Tap | "Common adaptation, monitor"; radiation rule has priority after a solar-event alert | M19–M21 | 1 |
| G6 Body mass loss | Body **mass** (kg), not weight | Typed (mass device in orbit) | Compare with baseline; combine with exercise and intake | M22–M25, R6 | 1 |

## A3. Hazard 3 – Isolation and confinement

| Concern | Indicator | Monitoring method | Viva action | Sources | Tier |
|---|---|---|---|---|---|
| I-1 Sleep loss, circadian disruption | Sleep hours, sleep quality 1–5 | Slider, tap | Non-drug tips, ask how they feel | I8–I11 | 1 |
| I-2 Fatigue, reduced alertness | Fatigue 1–5, reaction check (demo) | Tap, touch | Avoid critical tasks, ask a crewmate to double-check, contact flight surgeon | I8, I10, I12–I14 | 1 |
| I-3 Stress and workload | Stress 1–5, workload 1–5 | Tap | Gentle suggestions, CONNECT tip | I10, I1 | 1 |
| I-4 Mood, loneliness | Mood 1–5, "feeling connected" 1–5 (CONNECT-inspired, not a validated scale) | Tap | CONNECT tip of the day; prompt next private conference | I1, I2, I15–I17 | 1 |
| I-5 Team strain | Crew conflict this week: none / minor / significant | Tap | Suggest a calm conversation; ground behavioral support. No blame, no scoring of crewmates | I6, I7 | 1 |
| I-6 Behavioral emergency | Self-harm or "not wanting to be here" statement | Tap or text | Fixed supportive screen, stay with a crewmate, contact crew medical officer and ground flight surgeon. Same priority as chest pain | I3–I5, I23 | 1 |

## A4. Hazard 4 – Distance from Earth

| Concern | Feature | Monitoring method | Viva action | Sources | Tier |
|---|---|---|---|---|---|
| D-1 Delayed or lost expert advice | Link status panel: Live / Delayed / Blackout | **Simulated** by demo selector | Delay-aware wording; say what is known now and that the report is queued | D1, D2 | 1 |
| D-6 Silent decline between contacts | Trend memory (own history) | Automatic | Show slow changes | own reasoning | 1 |
| D-1, D-4 | "Report to Earth" queue (plain summary stored locally, "ready to send") | Automatic | Prepare the summary for ground | D1, D4 | 1 |
| D-2 Care by non-physicians | Crew Medical Officer handover card | Selectable role | Concise card: values, baseline, status, rule fired, symptoms | D6, D7 | 2 |
| D-4 No evacuation | Evacuation context in the environment selector | Display | Labelled reference | D7 | 2 |
| D-3 Limited diagnostics and supplies | On-board equipment checklist | Demo content | Flagged DEMO | D3, D4 | 3 |

## A5. Hazard 5 – Hostile and closed environments

| Concern | Indicator | Monitoring method | Viva action | Sources | Tier |
|---|---|---|---|---|---|
| C-1 CO2 | Cabin CO2 (mmHg) plus headache 0–10 | Typed or simulated (optional) | Check ventilation, report. Never says "CO2 caused it" | E2 | 2 (headache 1) |
| C-2 Noise | Noise level (dBA), sleep-area noise | Typed or simulated (optional) | Report; possible explanation for poor sleep | E3 | 2 |
| C-3 Immune change, microbes | Illness symptoms, body temperature, crew cluster flag | Checkboxes, typed, automatic | Share with Crew Medical Officer | E1, E4 | 1 / 2 / 3 |
| C-5 Low food intake | Food and fluid intake (% of plan), appetite 1–5 | Tap or slider | Neutral tone: low intake is common in flight | E5–E7 | 1 |
| C-4, C-6 Skin, comfort | Comfort rating 1–5 | Tap | Report | E1, E4 | 3 |

## A6. Cross-cutting vital signs (support all five hazards)

| Indicator | Reference (type) | Hazard links | Sources | Tier |
|---|---|---|---|---|
| Resting heart rate | 60–100 bpm (SOURCED, general adult) | microgravity, stress, late radiation | R1 | 1 |
| Blood pressure | General resting range from R1; AHA/ACC 2025 categories from R2 (normal: systolic <120 AND diastolic <80 mmHg) | microgravity fluid shift, stress | R1, R2 | 1 |
| SpO2 | 95–100% normal; ≤92% contact provider; ≤88% immediate attention (SOURCED) | closed environment | R3 | 1 |
| Body temperature | 36.5–37.3 °C (SOURCED) | immune change | R1 | 1 |
| Blood glucose | Fasting ≤99 normal (SOURCED); **optional** indicator | nutrition, stress | R4, R5 | 1 optional |
| Not in MVP | ECG, ultrasound, OCT, bone density, wearables, dosimeter feed, voice input | — | — | roadmap |

## A7. Build set inside Tier 1 (48-hour reality)

Not every indicator in this map is built in 48 hours. Everything unbuilt stays documented here and appears honestly on the Vision screen.

| Priority | Indicators | Note |
|---|---|---|
| P0 (must work end to end) | Resting heart rate, blood pressure, SpO2, body temperature, body mass, sleep (hours and quality), mood/stress/fatigue, symptoms checklist, exercise minutes, radiation dose (simulated), link status (simulated) | Full chain: input, validation, context check, engine, dashboard, Viva, handover |
| P1 (if time allows) | Reaction check (demo), vision questions, food and fluid intake, headache, feeling connected, motion-sickness scale, dizzy on standing, blood glucose (optional) | |
| P2 (simple card or roadmap) | Cabin CO2, noise, comfort rating, crew illness cluster flag, equipment checklist | Show as roadmap or as a read-only demo card |

---

# Part B – Hazard digests (facts the app may quote, with tags)

## B1. Space radiation (detail: 01)
- Hazard: galactic cosmic rays (GCR) and solar particle events (SPE) beyond Earth's magnetosphere; damage mostly by breaking DNA [S1–S3].
- NASA's four risk groups: cancer, central nervous system effects, degenerative tissue (heart, cataract), acute radiation syndrome [S1–S5].
- **Limits:** career < 600 mSv effective dose; single SPE 250 mSv [S7, S8]. NASA career limit also confirmed in the direct standard [S9]. The former Earth-background and other-agency comparisons are withheld pending appropriately scoped primary references. 1.5 mSv/day is an **illustrative** Mars-transit rate: label it "simulated" and verify [S7].
- Early (prodromal) symptoms: nausea, vomiting, appetite loss, diarrhoea, fatigue, headache, short skin reddening; onset about 1 hour to 72 hours; **non-specific**, shared with many illnesses [S10–S12]. Exploration modelling expects mainly prodromal symptoms if the crew reaches shelter [S13].
- Honesty: the 2021 published review reported no astronaut cancer diagnosis attributable to space radiation at that time [S6]. This is a historical statement, not a verified 2026 surveillance result or evidence of zero risk. Ground experiments and models inform risk estimates; translating them to astronauts remains uncertain [S6]. Vivonaut tracks exposure and early warning only.

## B2. Gravity fields (detail: 02)
- Fluid shift about 2 L headward [M9]; plasma volume can fall about 10–15% [M14].
- Bone mineral density falls on average 1–1.5% per month on 4–6 month missions; no validated fracture-predicting percentage [M1]. Lang et al. (2004; 14 crewmembers) reported a 2.55%/month reduction in a CT-derived femoral-neck bending-strength index [M2, M3]. Keyak et al. (2009) reported mean modeled strength losses of 2.6%/month under stance loading and 2.0%/month under fall loading [M4]. These are study-specific estimates, not a uniform loss or a validated fracture threshold; the former “at least 14%” claim is removed.
- Muscle: knee extensors −6% to −12%, plantar flexors −6% to −24% in long missions [M6]. ISS exercise about 2 to 2.5 h/day [M4–M7]; about 600 min/week did not fully protect function in 46 astronauts [M8].
- Orthostatic intolerance after return to gravity: more than 60% [M9], up to 64% [M15].
- Eyes (SANS): defining signs disc edema, globe flattening, retinal folds, hyperopic shift above 0.75 diopters [M17]; NASA’s current risk summary reports about 70% with at least one hallmark sign; this is not the proportion with severe symptoms or visual disability [M18]. Cannot be self-diagnosed.
- Vestibular: nearly 70% impaired within 3–4 days and again after landing; about 50% have some motion sickness [M19, M20]. EVAs restricted before flight day 3 [M19].
- Body mass measured by mass-measurement devices (NASA SLAMMD, Russian BMMD) because weight is about zero [M22, M23].
- Mars gravity about 3/8 g, long-term effects unknown [M10, M11].

## B3. Isolation and confinement (detail: 03)
- NASA splits this into three risks: behavioral conditions, team, sleep [I3, I6, I8].
- Sleep: about 8.5 h scheduled; measured averages 5.96 h (shuttle) and 6.09 h (ISS); ≥7 h on only 12% and 24% of nights [I9]. Under 6 h linked to slower reactions, higher stress and workload (24 ISS astronauts) [I10].
- Tools NASA uses: Reaction Self-Test about 3 minutes [I10, I12]; WinSCAT [I13]; Cognition battery of 10 tests, about 16 minutes [I14]. Vivonaut's 20-second tap game is a **simplified demo, not validated**.
- Mars-500: 520 days, six crew, 20-minute delay built in; mood generally stable with frequent negative episodes; weekly psychological assessments and 3-minute PVT-B sessions in the Basner study [I15–I17].
- **Third-quarter phenomenon is not consistently supported** [I19–I22]. Do not hard-code a mid-mission dip.
- ISS private psychological conference about every two weeks, typically 15–20 minutes in the 2017 NASA operational presentation [I23, I24].
- Reporting may under-count real problems; protect privacy and reward honesty [I25].
- CONNECT: Community, Openness, Networking, Needs, Expeditionary mindset, Countermeasures, Training [I1, I2]. A wellness tip, never treatment. Take the exact wording of "Openness" from NASA's page before using text.

## B4. Distance from Earth (detail: 04)
- Mars one-way delay up to about 22 minutes (15–21 min while at Mars), so a question and answer take up to about 44 minutes [D1, D2].
- Solar conjunction blackout: about 11.75 days on average at a 2° threshold; every representative mission has one disruption of roughly 2–3 weeks; repeats about every 26 months [D1].
- Artemis (Moon): anticipated round-trip delay 4–14 seconds [D2].
- ISS: ground flight surgeons can support crew through two-way video, and ultrasound examinations can be performed onboard with remote guidance [D3]. The previous absolute “no onboard doctor” claim and the exhaustive imaging-equipment claim are not retained on this evidence.
- Crew Medical Officer is a "healthcare extender to ground-based flight surgeons"; former officers want a physician and more training for exploration [D6].
- Evacuation: ISS under 24 h; lunar orbit up to 2 weeks; Mars may not be feasible [D7].
- NASA says on-board diagnostic and knowledge tools need to be more autonomous [D4]; Mars crews must respond to safety-critical anomalies without real-time ground support [D2].

## B5. Hostile and closed environments (detail: 05)
- NASA's factors: temperature, pressure, lighting, noise, space, habitat design, microbes and immune response [E1]. NASA's page does not cover air or water quality.
- CO2: ISS requirement ≤ 3 mmHg one-hour average (about 3,950 ppm is a conversion, not NASA's figure) [E2]. Headaches reported by 19 of 49 astronauts, mostly attributed to fluid shift [E2].
- Noise: hazardous below 85 dBA; work areas NC-50; sleep areas NC-40; alarms below 95 dBA; personal audio 115 dBA or less [E3].
- Immune and microbiome: changes seen, mechanisms unclear; no reactivation rates to quote [E1, E4]. The Inspiration4 study is peer-reviewed (Nature Microbiology, 2024), but includes only four participants on a three-day flight; it does not establish long-duration clinical thresholds.
- Nutrition: ISS crew average energy intake 74 ± 11% of the WHO recommendation, body weight lower after flight, vitamin D 27% lower despite supplements [E5]. Food Intake Tracker app used by crew since 2016 [E6].

---

# Part C – Reference ranges for the MVP indicators (embedded from 00)

### C0. How to read this file (very important)

Every value in the app belongs to exactly one of three types, and the UI must show which one:

| Type | Label in the UI | Meaning |
|---|---|---|
| **SOURCED** | "Reference: <source>" | A value or category published by a named source (MedlinePlus, NIDDK, AHA/ACC, NASA). It is a general **Earth-adult** reference, not a spaceflight-validated limit, unless the source says otherwise. |
| **DEMO** | "Demo rule" | A value we chose to make the prototype behave. **Not clinically validated. Never attributed to NASA.** A specialist must review before any real use. |
| **BASELINE** | "Your baseline" | The astronaut's own normal, built from their first valid readings (see C2). Used for change detection, not for diagnosis. |

Three rules:
1. A SOURCED value is shown as general reference information. Viva never says "you have a condition".
2. A DEMO value never appears without the words "Demo rule" next to it.
3. Nothing here is a medical protocol, and no value is a NASA flight rule unless a NASA source says so. The only NASA-sourced numbers in this file are marked with a NASA tag.

### C1. Valid-entry limits (plausibility checks)

These are **input validation limits**, not health thresholds. They only catch typing mistakes (e.g., heart rate 700). All are DEMO. If a value is outside the limit, the app asks "Did you mean this?" and does not store it until confirmed.

| Indicator | Unit | Accepted range (DEMO) | Behaviour outside range |
|---|---|---|---|
| Heart rate | bpm | 20–250 | Ask to re-enter |
| Systolic BP | mmHg | 60–260 | Ask to re-enter |
| Diastolic BP | mmHg | 30–160 | Ask to re-enter; systolic must be higher than diastolic |
| SpO2 | % | 50–100 | Ask to re-enter |
| Body temperature | °C | 30.0–43.0 | Ask to re-enter |
| Blood glucose | mg/dL | 20–600 | Ask to re-enter |
| Body mass | kg | 30–200 | Ask to re-enter |
| Sleep | hours | 0–16 | Ask to re-enter |
| Questionnaire scales | 1–5 or 0–10 | fixed | Not possible to enter outside |

### C2. Personal baseline rules (BASELINE type)

| Item | Rule |
|---|---|
| Calibration period | Demo: first **5 valid readings** per indicator, taken at rest, on different days (in the guided demo these are pre-loaded as "mission days 1–5"). |
| Baseline value | Median of the calibration readings. The median is then **frozen**. |
| Spread | Largest minus smallest calibration value, used to avoid flagging normal day-to-day variation. |
| Recalibration | Only by an explicit action ("Recalibrate baseline"), which writes an entry in the audit log with date and reason. It never happens automatically. |
| Unreliable data | A reading flagged "unconfirmed" or "stale" is not used for the baseline. |
| Why frozen | A slowly worsening condition must not become the new normal. |

All numbers in this section (5 readings, median) are DEMO design choices.

### C3. The MVP reference table

How the three types combine for each indicator. "Change rule" rows are DEMO unless stated.

#### C3.1 Heart rate (resting)

| Item | Value | Type | Source / note |
|---|---|---|---|
| General adult resting reference | 60–100 beats per minute | SOURCED | MedlinePlus, Vital signs [R1] |
| Personal change (Watch) | Resting rate above baseline by more than 15 bpm on 2 readings | DEMO | Our choice; clinical value not established |
| Trend (Watch) | Rising on 3 consecutive days | DEMO | |
| Context | Measure after at least a few minutes of rest; exercise, stress and posture change it | DEMO guidance | |
| Hazard links | Microgravity, stress, late radiation effects | Design link | See files 01–03 |

#### C3.2 Blood pressure (systolic/diastolic)

| Item | Value | Type | Source / note |
|---|---|---|---|
| General adult resting reference | R1 gives a broad resting range of 90/60 to 120/80 mmHg; use R2 for category boundaries | SOURCED | These are not equivalent definitions: AHA normal requires BOTH systolic <120 and diastolic <80 [R1, R2] |
| AHA/ACC 2025 categories | Normal: systolic <120 AND diastolic <80; Elevated: systolic 120–129 AND diastolic <80; Stage 1: systolic 130–139 OR diastolic 80–89, unless Stage 2 applies | SOURCED | Primary guideline, section 2.1, Table 4 [R2]; use the higher category when the two components differ |
| Stage 2 — CONFIRMED | Systolic ≥140 mmHg OR diastolic ≥90 mmHg | SOURCED | 2025 AHA/ACC guideline, Table 4 [R2]; either component is sufficient. This threshold is retained from the 2017 framework |
| Interpretation | Classify the reading, not the person; diagnosis requires clinical confirmation | SOURCED context | General nonpregnant adult office-BP categories, ordinarily based on averages of ≥2 careful readings on ≥2 occasions [R2]. Not spaceflight-validated |
| App behaviour | Non-severe, asymptomatic above-reference reading → rest and repeat in 15 minutes | DEMO | Prototype timing only; does not apply to emergency symptoms or severe readings |
| Very high reading | Systolic >180 OR diastolic >120 mmHg with concerning symptoms (e.g., chest pain, shortness of breath, weakness, vision change, difficulty speaking) → fixed emergency screen | SOURCED threshold + DEMO action | [R2]; the action is a demo simulation |
| Personal change | More than 20 mmHg systolic above baseline on 2 readings | DEMO | |
| Context | Always ask posture (seated/lying) and rest time; posture matters in microgravity | DEMO guidance | See 02_MICROGRAVITY_RESEARCH.md |

Note: Earth guideline categories are not validated for crews in weightlessness. The app says so.

#### C3.3 Oxygen saturation (SpO2)

| Item | Value | Type | Source / note |
|---|---|---|---|
| Normal range | 95–100% | SOURCED | MedlinePlus, Pulse oximetry [R3] |
| Contact provider | 92% or lower | SOURCED | [R3] (general public guidance) |
| Seek immediate attention | 88% or lower | SOURCED | [R3] |
| Accuracy limits | Readings can differ from true value by about 2–4%; nail polish, artificial nails, cold skin, poor circulation, skin pigmentation can affect results | SOURCED | [R3] |
| App behaviour | Below 95%: ask to re-measure after warming the hand and removing polish; ≤92% twice → Needs assessment; ≤88% → Alert and emergency screen | DEMO action built on sourced numbers | |
| Cabin link | Show cabin CO2 context if available | Design link | See 05_CLOSED_ENV_RESEARCH.md |

#### C3.4 Body temperature

| Item | Value | Type | Source / note |
|---|---|---|---|
| General adult reference | 36.5–37.3 °C (97.7–99.1 °F), average 37 °C | SOURCED | MedlinePlus, Vital signs [R1] |
| Watch | 37.8 °C or higher | DEMO | Our choice for the prototype |
| Needs assessment | 38.0 °C or higher, or with other symptoms | DEMO | Our choice; not a NASA threshold |
| Context | Method (oral, ear, forehead) is recorded because methods differ | DEMO guidance | |

#### C3.5 Blood glucose (optional; reason stated)

Why optional: glucose is listed because the team's dashboard idea includes it and nutrition/stress affect it. It is not a core NASA hazard indicator, so if time is short it is the first indicator to cut, and the UI says "Optional demo indicator".

| Item | Value | Type | Source / note |
|---|---|---|---|
| Fasting normal | 99 mg/dL or below | SOURCED | NIDDK, citing American Diabetes Association [R4] |
| Fasting prediabetes range | 100–125 mg/dL | SOURCED | [R4] |
| Fasting diabetes range | 126 mg/dL or above | SOURCED | [R4] |
| Low glucose | Below 70 mg/dL in people with diabetes; typically below 55 mg/dL in people without diabetes | SOURCED | MedlinePlus Hypoglycemia [R5] |
| Symptoms listed | Shaking, sweating, anxiety, irritability or confusion, dizziness, hunger | SOURCED | [R5] |
| App behaviour | Ask "fasting or after a meal?"; only apply fasting categories to fasting readings. Low reading with symptoms → "Needs assessment" | DEMO | The app never gives insulin or treatment advice |

#### C3.6 Body mass

| Item | Value | Type | Source / note |
|---|---|---|---|
| General reference range | None. Healthy mass depends on the person | — | |
| Personal change (Watch) | Loss of 2% or more from baseline | DEMO | No NASA threshold found [see 02_MICROGRAVITY_RESEARCH.md] |
| Context | In orbit mass is measured with a mass-measurement device; on the Moon or Mars a scale must be calibrated to local gravity (our own reasoning, needs a source) | Design note | |
| Link | ISS crew average energy intake was 74% of the WHO recommendation and body weight was lower after flight | SOURCED (NASA NTRS) | [R6] (see 05 file) |

#### C3.7 Sleep, mood, stress, fatigue (questionnaires)

| Item | Value | Type | Source / note |
|---|---|---|---|
| Scheduled sleep | NASA schedules about 8.5 hours | SOURCED (NASA) | See 03_ISOLATION_RESEARCH.md [I9] |
| Observed ISS sleep | about 6 hours average | SOURCED (NASA study) | [I9, I10] |
| Short sleep | Under 6 hours linked to slower response and higher stress | SOURCED (study) | [I10] |
| Watch (our rule) | Under 6 hours on 3 nights, or 1.5 hours below own baseline | DEMO | |
| Mood, stress, fatigue (1–5) | No clinical cut-offs | BASELINE only | Compare with own baseline and trend |
| Weekly check-in | Weekly psychological measures; PVT-B sessions lasted 3 minutes in Mars500 | SOURCED | [I17], methods section 2.2.2.2. A 10-minute total app check-in would be DEMO, not this study’s validated duration |

#### C3.8 Reaction-time test

| Item | Value | Type | Source / note |
|---|---|---|---|
| Real NASA tool | Reaction Self-Test, about 3 minutes | SOURCED | [I10, I12] |
| Our version | 20-second tap game, compared only with the user's own baseline | DEMO, not validated | Label: "Simplified demo inspired by the idea; not equivalent to NASA tools" |
| Watch | Median response slower than baseline by more than 20% on 2 sessions | DEMO | |

#### C3.9 Symptoms checklist and vision questionnaire

| Item | Value | Type | Source / note |
|---|---|---|---|
| Symptom list | Radiation prodromal symptoms (nausea, vomiting, fatigue, headache) and others | SOURCED lists | See 01_RADIATION_RESEARCH.md |
| Emergency symptoms | Chest pain, severe breathing difficulty, loss of consciousness, self-harm statement | DEMO routing | Always shown the fixed emergency screen first |
| Vision change | Blurred or double vision, new discomfort | Questionnaire, no cut-off | Link to SANS, see 02 file |

#### C3.10 Radiation dose (always labelled simulated unless from a dosimeter)

| Item | Value | Type | Source / note |
|---|---|---|---|
| Career limit | 600 mSv | SOURCED (NASA) | See 01_RADIATION_RESEARCH.md |
| Single event reference | 250 mSv | SOURCED (NASA) | See 01 file |
| Tiers | 50%, 80%, 100% of 600 mSv; single event Watch above 50, Alert above 150, urgent Alert at 250 or more (never the emergency screen) | DEMO tiers built on sourced limits | See 01 file |
| Display | The label "Simulated" always appears unless the number came from a dosimeter | Rule | |

#### C3.11 Exercise minutes

| Item | Value | Type | Source / note |
|---|---|---|---|
| Reference | About 600 minutes per week on the ISS | SOURCED (NASA reference in file 02; verify) | See 02_MICROGRAVITY_RESEARCH.md |
| Watch | Less than 70% of the person's weekly plan | DEMO | |

### C4. Status mapping (how the engine labels results)

The dashboard shows **Monitoring Status** counts, not a health percentage.

| Status | Typical trigger (summary) |
|---|---|
| Stable | Within baseline spread and no sourced threshold crossed |
| Watch | One DEMO change rule fired, or a trend over several days |
| Needs assessment | Sourced contact threshold crossed (e.g., SpO2 ≤92%), or two indicators plus symptoms |
| Alert / Emergency | Alert: high-tier rule fired (e.g., career dose above 80%, event dose above 150 mSv). Emergency: emergency symptoms, blood pressure crisis with symptoms, or SpO2 at 88% or lower; only these open the fixed emergency screen (see Part D) |
| No data | The indicator has not been measured. Shown as its own count in Monitoring Status; never treated as Stable |

Every status shows "How Viva decided": the rule, the values, the type tag (SOURCED / DEMO / BASELINE), and the disclaimer "Reference information, not a diagnosis".

---

# Part D – Rule catalogue and priority (for the rules engine)

Every rule shows in "How Viva decided": rule ID, the values used, the type tag, and "Reference information, not a diagnosis". Status names: **Stable / Watch / Needs assessment / Alert**; the fixed **emergency screen** opens only for P0 and P1 rules.

## D1. Priority order and conflict handling

1. **P0 – Emergency symptoms** (chest pain, severe breathing difficulty, loss of consciousness, self-harm or "not wanting to be here" statement): fixed emergency screen, skip questionnaires, overrides every other rule and the link state.
2. **P1 – Two sourced emergency-level values only**: blood pressure above 180 and/or 120 with symptoms (VIT-3), and SpO2 at 88% or lower (VIT-5): fixed emergency screen. Radiation values never open the emergency screen by themselves (see RAD-2 and RAD-3); they raise the highest Alert and tell the crew to contact the ground.
3. A **solar-event alert in the last 72 hours** gives the radiation symptom rules priority over the motion-sickness rule for nausea, vomiting and fatigue. Without an alert, nausea in the first 1–5 days after launch, transit start or landing is labelled "common adaptation, monitor". Wording is always "may be related to".
4. Otherwise the **highest status among fired rules wins**; all fired rules are listed.
5. Unconfirmed, stale or simulated readings cannot raise a status above Watch by themselves; the app asks to re-measure. A reading that departs from the person's baseline or the reference first gets the measurement context check (CTX rules, D3) and the label "Needs verification". Symptoms are never ignored. (DEMO design choice.)
6. Missing measurements: continue with what exists and say what is missing.
7. The baseline is frozen after calibration and changes only by an explicit, logged "Recalibrate baseline" action (see C2).

## D2. Rules

| ID | Trigger | Result | Type | Basis |
|---|---|---|---|---|
| EMG-1 | Emergency symptoms above | Emergency screen (fixed, pre-written text labelled "Educational simulation, not a medical protocol"); ask for nearest crewmate; queue report | DEMO routing | I5, I23 |
| RAD-1 | Career dose: <50% of 600 mSv Stable; 50–80% Watch; 80–100% Alert; >100% Alert with planning notice (not the emergency screen) | Notify flight surgeon and mission planners | DEMO tiers on SOURCED limit | S7 |
| RAD-2 | Event dose: >50 mSv Watch; >150 Alert; ≥250 urgent Alert (highest tier; no emergency screen) | Shelter guidance, contact ground now | DEMO tiers on SOURCED 250 mSv | S7, S8 |
| RAD-3 | ≥2 symptoms within 72 h of an SPE alert → Alert; vomiting plus another symptom → urgent Alert: contact flight surgeon now (no emergency screen unless P0 symptoms appear) | Rest in shelter, log with times, contact flight surgeon | DEMO | S10–S13 |
| RAD-4 | Single symptom without an SPE | Log, trend only | DEMO | S12 |
| GRV-1 | Body mass ≥2% below baseline, or downward trend over several weeks with low exercise | Watch | DEMO (no NASA threshold found) | M24, R6 |
| GRV-2 | Weekly exercise well under about 600 min (several weeks), or under 70% of own plan | Watch, friendly reminder | DEMO on SOURCED reference | M8 |
| GRV-3 | New or worsening near-vision blur versus mission start, double vision, flashes | Needs assessment: contact flight surgeon | DEMO | M17, M18 |
| GRV-4 | Dizzy or faint on standing right after arriving in a gravity environment | Sit or lie down, ask crew; repeated or severe escalates | DEMO | M9, M15 |
| GRV-5 | Nausea or vomiting in first 1–5 days or after landing, no SPE alert | "Common adaptation, monitor" | DEMO | M19 |
| ISO-1 | Sleep <6 h on 3 of last 5 nights (or 1.5 h below own baseline) | Watch; non-drug tips | DEMO on SOURCED finding | I10 |
| ISO-2 | Short sleep + rising fatigue + reaction check slower than own baseline | Needs assessment; "avoid critical tasks if you can, ask a crewmate to double-check, contact the flight surgeon" | DEMO | I8, I10 |
| ISO-3 | Mood down and stress up over about 2 weeks with low connection | Watch; CONNECT tips; prompt next private conference | DEMO | I1, I23 |
| ISO-4 | Significant crew conflict reported | Suggest calm conversation and ground behavioral support; no sharing without consent | DEMO | I6 |
| ISO-5 | Self-harm statement | See P0 | DEMO | I5 |
| ISO-6 | Emergency Mode wording | First lines very short and clear (sleep inertia) | Design | I8 |
| DST-1 | Link state: Live → suggest contacting flight surgeon now for Watch or higher; Delayed → guidance now, report sent, reply may take up to about 44 min round trip at Mars distance; Blackout → "autonomy mode": reference guidance only, confirm with Crew Medical Officer and crew, queue summary | Behaviour of the simulated link, not medical thresholds | DEMO | D1, D2 |
| DST-2 | Any status ≥ Watch | Add to "Report to Earth" queue (stored locally) | Design | D1, D4 |
| DST-3 | Crew Medical Officer role selected | Handover card (who, when, values, baseline, status, rule fired, symptoms) | Design | D6, D7 |
| ENV-1 | Cabin CO2 > 3 mmHg (one-hour average) | "Above the ISS requirement. Check ventilation, report" | SOURCED limit | E2 |
| ENV-2 | CO2 > 3 mmHg and headache ≥5 on 2 readings | Watch | DEMO | E2 |
| ENV-3 | Noise ≥85 dBA | Watch; report | SOURCED limit | E3 |
| ENV-4 | Sleep quality ≤2 for 3 nights and noise logged above sleep-area limit | Suggest reporting | DEMO | E3 |
| ENV-5 | Intake <75% of plan for 3 days | Watch, neutral tone (ISS average is 74%) | DEMO | E5 |
| ENV-6 | Two profiles with the same symptom within 48 h | "Share with Crew Medical Officer" | DEMO | E1, E4 |
| VIT-1 | Resting HR >15 bpm above baseline on 2 readings, or rising 3 consecutive days | Watch | DEMO | R1 |
| VIT-2 | Non-severe, asymptomatic above-reference BP reading | Rest and repeat in 15 minutes; classify by the higher component | DEMO action, SOURCED categories | R2 |
| VIT-2S | Systolic >180 OR diastolic >120 mmHg, without concerning symptoms | Repeat after at least 1 minute; if still this high, promptly contact the flight surgeon. Concerning symptoms take priority under VIT-3/P0 | SOURCED Earth guidance + DEMO mission adaptation | R2 |
| VIT-3 | Systolic BP >180 OR diastolic BP >120 mmHg with concerning symptoms (e.g., chest pain, shortness of breath, weakness, vision change, difficulty speaking) | Emergency screen (P1) | SOURCED threshold + DEMO action | R2 |
| VIT-4 | Systolic >20 mmHg above baseline on 2 readings | Watch | DEMO | — |
| VIT-5 | SpO2 <95%: re-measure (warm hand, no nail polish); ≤92% twice: Needs assessment; ≤88%: Alert plus emergency screen (P1) | As stated | SOURCED numbers, DEMO action | R3 |
| VIT-6 | Temperature ≥37.8 °C Watch; ≥38.0 °C or with other symptoms Needs assessment | As stated | DEMO | — |
| VIT-7 | Glucose: fasting categories only for fasting readings; low reading with symptoms → Needs assessment; no treatment advice | As stated | SOURCED categories, DEMO action | R4, R5 |
| VIT-8 | Reaction median >20% slower than baseline on 2 sessions | Watch | DEMO | I10 |

## D3. Data-state, measurement-context, follow-up and handover rules (design rules, DEMO)

| ID | Rule | Type |
|---|---|---|
| DATA-1 | No reading: the indicator shows "No data". No status, no alert, grey body-map zone. Viva never mentions a value she has not been given | Design |
| DATA-2 | Baseline is "not established" until 5 valid calm readings exist (or a pre-mission baseline is provided). Until then compare only with the general reference and say so | DEMO |
| DATA-3 | A new profile holds profile information only; health values are empty. The demo profile holds pre-loaded data labelled "Simulated Data" | Design |
| DATA-4 | The default dashboard shows the demo profile and raises no new alerts unless the user enters a reading or starts a scenario | Design |
| DATA-5 | Monitoring Status shows counts: Stable, Watch, Needs assessment, Alert, plus No data | Design |
| DATA-6 | If any P0 indicator is unmeasured today, Viva says "based on the data available" and never says all is steady | Design |
| CTX-1 | A reading that departs from the baseline spread or the reference is labelled "Needs verification". Before interpreting it Viva asks: exercise in the last 30 minutes? posture? technique? first or repeated reading? any symptoms? | Design; the 30-minute window is a DEMO choice |
| CTX-2 | The context check applies first to blood pressure, heart rate, SpO2 and temperature | Design |
| CTX-3 | If the context explains the reading (exercise, posture, technique): ask to rest and repeat, and do not raise the status | DEMO |
| CTX-4 | If the repeat confirms the change, or the context is normal: continue with the normal rules (VIT-x) | DEMO |
| CTX-5 | P0 symptoms always skip the context check and open the emergency screen | Design |
| CTX-6 | "Data Confidence" means quality and completeness of the measurement: Complete, Needs verification, Incomplete, Simulated. It is never a probability of illness | Design |
| FUP-1 | Every Watch or higher creates a follow-up: an action, a reassess time (non-severe asymptomatic blood pressure 15 minutes; severe BP follows VIT-2S/VIT-3; sleep next night; body mass next weekly check), then an evaluation | DEMO |
| FUP-2 | The evaluation shows before and after values and the sentence "This shows a change. It cannot show what caused it" | Design |
| FUP-3 | If the evaluation is worse, raise the status one level and add it to the handover | DEMO |
| HND-1 | "Generate Health Handover" builds a report from app data only: current indicators, changes from baseline, alerts so far, measurements repeated, actions tried, symptoms reported, missing or unconfirmed data, questions for the ground team. Stored locally as "ready and queued, not sent" | Design; D1, D4 |
| HND-2 | Psychological answers are included only with explicit consent | Design; I25 |
| PRV-1 | Mood, stress and symptom cards are private to the profile owner: after a profile switch they sit behind "Private – tap to view" and are shared only by consent | Design; I25 |

---

# Part E – Mission environment table (for the selector)

| Environment | Gravity | Mass measurement | One-way delay | Evacuation | Support / emphasis |
|---|---|---|---|---|---|
| Space station (LEO) | microgravity | mass-measurement device [M22] | Two-way video support [D3]; exact latency and availability not established by this source | under 24 h [D7] | Live flight-surgeon video link [D3]; private psychological conference about every 2 weeks [I23]. Emphasis: all gravity concerns, sleep, workload, team |
| Spacecraft in transit (Mars) | microgravity | mass-measurement device [M22] | up to about 22 min [D1, D2]; blackout 2–3 weeks [D1] | not stated in sources read | Delayed messages only; self-guided support, CONNECT, message queue [I25, D1] |
| Lunar base | about 1/6 g (verify) | scale calibrated for local gravity (our reasoning, verify) | about 1–2 s; Artemis round trip 4–14 s [D2] | up to 2 weeks from lunar orbit [D7] | Near-real-time contact; transition symptoms, exercise. Lunar isolation and sleep specifics unverified |
| Mars base | about 3/8 g [M10] | scale calibrated for local gravity (our reasoning, verify) | up to about 22 min; blackout 2–3 weeks [D1] | may not be feasible [D7] | Long-term bone and muscle, exercise, arrival orthostatic symptoms, autonomy [D2] |

---

# Part F – Honesty rules and cross-hazard overlaps

## F1. What the app must never do
- Never diagnose. Viva is a health companion that helps astronauts understand their health data and follow approved guidance; not a doctor, not a therapist.
- Never attribute a DEMO value to NASA, and never show a DEMO value without "Demo rule".
- Always label radiation dose "Simulated" unless it came from a dosimeter.
- Never claim that Vivonaut analyses blood or saliva or connects to a device. The blood-analysis idea is a roadmap concept (Part G item 18).
- Always say general Earth reference ranges are not validated for spaceflight.
- Body-map colours reflect linked indicators, not real organ condition.
- Emergency steps are fixed, pre-written, sourced text; no oxygen, drug or procedure without a source.
- Do not hard-code a mid-mission mood dip. Do not claim a NASA self-vision check, NASA mood cut-offs, or a NASA body-mass-loss threshold.
- Label the reaction check "simplified demo, not validated".
- Do not quote: "up to 20% muscle loss in 5–11 days" (unverified), "3 minutes" as Mars minimum delay (unconfirmed), virus reactivation rates, Crew Medical Officer training hours.
- Mental-health data stays on the device by default; sharing is a consent-based action. Honest reporting is rewarded; low days are never punished.

## F2. Symptoms that mean different things in different hazards

| Symptom | Possible links | How the engine separates them |
|---|---|---|
| Nausea, vomiting | Space motion sickness (G5); radiation prodrome (R4) | Timing: solar-event alert within 72 h → radiation rule; first 1–5 days or after landing → adaptation |
| Headache | Fluid shift and SANS (G3, G4); CO2 (C-1); radiation prodrome | Never state one cause; show CO2 reading and ask to report |
| Fatigue | Sleep loss (I-1); radiation prodrome; CO2; low intake (C-5) | Combine indicators in the multi-indicator assessment |
| Poor sleep | Isolation (I-1); noise (C-2); CO2 | Ask about noise and cabin air |
| Blurred vision | SANS (G4); radiation (cataract concern, late) | Questionnaire only; any new change goes to flight surgeon |
| Body mass loss | Microgravity muscle loss (G2); low intake (C-5) | Show mass together with exercise and intake |
| Heart rate, BP change | Fluid shift (G3); stress (I-3); late radiation effects | Always record posture and rest |
| Slow reactions, poor attention | Sleep (I-1); radiation CNS concern (R2); CO2 | Compare with own baseline, demo label |

---

# Part G – Open questions (consolidated, for the science teammate)

Priority A = fix before submission. B = improves credibility. C = optional.

| # | Priority | Question | Source file |
|---|---|---|---|
| 1 | A — addressed | Direct NASA/journal references substituted for every listed code; E6 canonicalized. Some replacements support narrower claims; S6 is a published review, not original research. See Part I for changes and withheld claims | all |
| 2 | A — confirmed | Stage 2: systolic ≥140 OR diastolic ≥90 mmHg. Verified against the 2025 AHA/ACC primary guideline, Table 4, and official AHA chart; R2 and C3.2 corrected | 00 |
| 3 | A | A clinician reviews every DEMO rule before any use beyond the hackathon | 00 |
| 4 | B | Spaceflight-specific values for resting HR and BP in flight (none found; until then "general adult reference") | 00 |
| 5 | B | Confirm exercise reference (about 600 min/week) in NASA source M8 | 00, 02 |
| 6 | B | Confirm current GCR dose rates for ISS, lunar surface and Mars transit (the 1.5 mSv/day figure is illustrative) | 01 |
| 7 | B | Lunar gravity (about 1/6 g), scale calibration on Moon and Mars, and Moon delay (about 1.3 s, our calculation): NASA pages | 02, 04 |
| 8 | B | Exact wording of NASA's "Openness" principle before using text in the app | 03 |
| 9 | B | Confirm "up to about 22 min" and find the minimum Mars delay; the common "3 minutes" was not confirmed | 04 |
| 10 | B | Hypoxia, oxygen, humidity, temperature and air-contaminant thresholds were not covered by any source read; show "not covered" | 05 |
| 11 | B | Newer ISS nutrition data to confirm the 2006 figures (74% intake, vitamin D) | 05 |
| 12 | C | Any NASA reference ranges for cognitive tests (WinSCAT, Cognition battery) | 01 |
| 13 | C | Body-mass change threshold; temperature thresholds and methods | 00, 02 |
| 14 | C | Lunar isolation specifics (delay, long lunar day and sleep) | 03 |
| 15 | C | Medical-conference frequency with the flight surgeon, Crew Medical Officer training hours, evacuation procedures: not found; do not state. (The ISS private **psychological** conference about every 2 weeks is sourced [I23].) | 04 |
| 16 | C | CO2 ppm conversion (about 3,950 ppm) to verify | 05 |
| 17 | A | A — verified for scoped citation | Medical-701 and Hardy et al. (2025) checked against the original NASA record and journal publication; the 2026 author correction was also checked. References X1–X3 are listed in Part H7. These sources support project rationale, not validation of Vivonaut or its DEMO rules. | review |
| 18 | C — delivered | Point-of-Care Blood Analysis Concept: research delivered 14 Nov; see Part J (simulated screen, no new thresholds). Original task: (roadmap card only). Marialena researches candidate markers (bone turnover markers, vitamin D, inflammatory markers, glucose) and the NASA study pages to check (candidate names: Immune Biomarkers, Omics Archive, Altered Immunity; Tempus Pro is a commercial device, never an endorsement). Nothing enters the rules engine, the reference tables or Part H until verified | team, 13 Nov |

Reconciliations made in this merge: (a) career dose above 100% is an Alert with a planning notice, not an emergency screen, because 01 calls it planning guidance; (b) the body-mass rule combines the 2% DEMO rule (00) with the trend-plus-low-exercise rule (02); (c) the Mars delay is stated as "up to about 22 minutes" [D1, D2] and the older secondary “about 20 minutes” wording was removed; I26 now cites NASA directly for the hazard framework; (d) all numbering of reference-range sections is prefixed with C; (e) radiation values no longer open the emergency screen (team review): only emergency symptoms, a blood pressure crisis with symptoms and SpO2 at 88% or lower do; (f) "No data" is a monitoring count, not a health state; (g) the build set in A7 narrows Tier 1 for the 48-hour limit.

---

# Part H – Source list (all codes must appear on the app's Sources page)

Source-quality note: targeted references in Part G item 1 now use direct NASA pages, original journal articles, or the published S6 review. Direct institutional provenance is not the same as original experimental research. See Part I; this is not a full audit of every source or DEMO rule.

## H1. Radiation (S)

- S1 Huff, Patel, Simonsen. Space Radiation and Risks to Human Health. NASA NTRS 20140004045. https://ntrs.nasa.gov/citations/20140004045
- S2 NASA HRP. Space Radiation is Risky Business for the Human Body (19 September 2017). Direct NASA institutional article. https://www.nasa.gov/humans-in-space/space-radiation-is-risky-business-for-the-human-body/
- S3 NASA. Risk of Radiation-Induced Cancers. https://www.nasa.gov/reference/risk-of-radiation-induced-cancers
- S4 NASA NTRS. Evidence Report: Risk of Cardiovascular Disease and Other Degenerative Tissue Effects from Radiation Exposure (20150016006). https://ntrs.nasa.gov/citations/20150016006
- S5 NASA. The Five Hazards of Human Spaceflight. https://www.nasa.gov/hrp/hazards
- S6 Chancellor et al. Everything you wanted to know about space radiation but were afraid to ask. Journal of Environmental Science and Health, Part C 39(2):113–128 (2021). Published review, not original cohort research; replaces the arXiv version. https://doi.org/10.1080/26896583.2021.1897273
- S7 NASA OCHMO. Radiation Protection Technical Brief (Rev E, 2022). https://www.nasa.gov/wp-content/uploads/2023/03/radiation-protection-technical-brief-ochmo.pdf
- S8 NASA OCHMO Standards Overview (2021). https://www.nasa.gov/sites/default/files/atoms/files/ochmo_standards_overview_sept_15_2021_francisco.pdf
- S9 NASA-STD-3001, Volume 1, section 4.8, Space Permissible Exposure Limit for Spaceflight Radiation Exposure; especially requirement V1 4030 (career effective dose <600 mSv). Direct NASA standard text. Replaces the news summaries for NASA limits; does not support a universal Earth-background value or a blanket claim about other agencies. https://www.nasa.gov/reference/4-0-human-performance/
- S10 Prodromal symptoms of ARS (Int J Radiat Biol 2020). https://informahealthcare.com/doi/abs/10.1080/09553002.2020.1820603
- S11 Sanzari et al., SPE proton radiation and emesis. https://pmc.ncbi.nlm.nih.gov/articles/PMC3837533
- S12 NASA THREE (JSC). Acute effects of radiation. https://three.jsc.nasa.gov/articles/SeedAcuteEffects.pdf
- S13 Blue et al. Challenges in clinical management of radiation-induced illnesses during exploration spaceflight. Aerosp Med Hum Perform 2019;90(11):966-977. https://ntrs.nasa.gov/citations/20170009925
- S14 Simonsen et al. ASCEND paper, NASA NTRS 20250006168. https://ntrs.nasa.gov/api/citations/20250006168/downloads/ASCEND%20Simonsen%20draft%201.pdf

## H2. Gravity fields (M)

- M1 NASA HRP Evidence Report: Risk of Bone Fracture due to Spaceflight-induced Changes to Bone (2017). https://ntrs.nasa.gov/api/citations/20170004597/downloads/20170004597.pdf
- M2 Lang et al. Cortical and Trabecular Bone Mineral Loss From the Spine and Hip in Long-Duration Spaceflight. Journal of Bone and Mineral Research 19(6):1006–1012 (2004). Original study, 14 crewmembers. https://doi.org/10.1359/JBMR.040307
- M3 Same original Lang et al. (2004) study as M2; retained code replaces the EurekAlert release, not independent evidence. https://doi.org/10.1359/JBMR.040307
- M4 Keyak et al. Reduction in proximal femoral strength due to long-duration spaceflight. Bone 44(3):449–453 (2009). Original finite-element study. https://doi.org/10.1016/j.bone.2008.11.014 ; journal page https://www.sciencedirect.com/science/article/abs/pii/S8756328208009095 ; abstract https://pubmed.ncbi.nlm.nih.gov/19100348/
- M5 NASA. Astronaut Exercise (Science in Space: May 2024). Direct NASA article replacing the Phys.org republication. https://www.nasa.gov/general/astronaut-exercise/
- M6 Review of skeletal muscle atrophy and exercise countermeasures, Extreme Physiology and Medicine. https://extremephysiolmed.biomedcentral.com/track/pdf/10.1186/2046-7648-1-12
- M7 ESA. Staying strong in orbit with ARED. https://www.esa.int/ESA_Multimedia/Images/2026/07/Staying_strong_in_orbit_with_ARED
- M8 Scott et al. Effects of exercise countermeasures on multisystem function in long duration spaceflight astronauts, npj Microgravity 2023. https://www.nature.com/articles/s41526-023-00256-5
- M9 NASA. Ensuring Astronaut Health (Cardiovascular Laboratory). https://www.nasa.gov/?p=207552
- M10 NASA HRP. 5 Hazards of Human Spaceflight, Gravity Fields section (Mars: three-eighths Earth gravity). Direct institutional source; same page as M11. https://www.nasa.gov/hrp/hazards/
- M11 NASA. The Five Hazards of Human Spaceflight. https://www.nasa.gov/hrp/hazards
- M12 NASA. Astronaut Exercise. Same direct source as M5, not independent evidence. https://www.nasa.gov/general/astronaut-exercise/
- M13 Entering a new era for exercise countermeasures in human spaceflight, Experimental Physiology 2025. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC13394428/
- M14 Silburn. Counteracting microgravity: preserving cardiovascular health in low Earth orbit, Military Medical Research 2025. https://pmc.ncbi.nlm.nih.gov/articles/PMC12403249
- M15 Fluid loading effects on cardiovascular responses to head-down tilt, Aerosp Med Hum Perform. https://meridian-asma-published.prime-prod-local.pubfactory.com/downloadpdf/view/journals/amhp/86/2/article-p88.pdf
- M16 NASA Spinoff. Health and Medicine (orthostatic intolerance). https://spinoff.nasa.gov/node/11107
- M17 Lee et al. Spaceflight associated neuro-ocular syndrome (SANS) and the neuro-ophthalmologic effects of microgravity: a review and an update, npj Microgravity 2020. https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7005826/
- M18 NASA Human Research Roadmap. Risk of Spaceflight Associated Neuro-ocular Syndrome (SANS), risk 105. Direct NASA risk summary: about 70% show one or more hallmark signs; not a rate of severe visual impairment. Replaces the older Healio summary. https://humanresearchroadmap.nasa.gov/Risks/risk.aspx?i=105
- M19 Review, Frontiers in Neurology 2025 (vestibular, space motion sickness). https://frontiersin.org/journals/neurology/articles/10.3389/fneur.2025.1556553/full
- M20 NASA Ames. Psychophysiology Research Laboratory. Direct NASA source for approximately 50% experiencing space sickness and for Autogenic Feedback Training Exercise; replaces the third-party mirror of NASAexplores. https://www.nasa.gov/human-systems-integration-division/psychophysiology-research-laboratory/
- M21 NASA NTRS. Neuro-Vestibular Examination During and Following Spaceflight (2026 HRP workshop abstract). https://ntrs.nasa.gov/citations/20260002549
- M22 Body mass changes during long-duration spaceflight. Aviation, Space, and Environmental Medicine 85(9):897–904 (2014). Original research; describes Russian BMMD spring oscillation and NASA SLAMMD acceleration-based measurement. https://doi.org/10.3357/ASEM.3979.2014 ; abstract https://pubmed.ncbi.nlm.nih.gov/25197887/
- M23 Same original body-mass study as M22; replaces the Smithsonian secondary explanation. https://doi.org/10.3357/ASEM.3979.2014
- M24 Same original body-mass study as M22; replaces the Gulf News example for general measurement context. Does not validate the app’s 2% DEMO threshold or document that specific UAE astronaut demonstration. https://doi.org/10.3357/ASEM.3979.2014
- M25 Frontiers, Neural Circuits 2021. Challenges to the Vestibular System in Space. https://www.frontiersin.org/articles/10.3389/fncir.2021.760313

Source quality note: the flagged entries in this section have been replaced; duplicate codes are retained for compatibility and explicitly identified above.

## H3. Isolation (I)

- I1 NASA. Isolation: What Can We Learn From the Experiences of NASA Astronauts? https://www.nasa.gov/humans-in-space/isolation-what-can-we-learn-from-the-experiences-of-nasa-astronauts
- I2 NASA Houston We Have a Podcast, Ep. 162, CONNECT During Social Isolation. https://www.nasa.gov/johnson/HWHAP/connect-during-social-isolation
- I3 NASA HSRB. Risk of Adverse Cognitive or Behavioral Conditions and Psychiatric Disorders. https://www.nasa.gov/directorates/esdmd/hhp/risk-of-adverse-cognitive-or-behavioral-conditions-and-psychiatric-disorders
- I4 NASA NTRS. Evidence Report: Risk of Adverse Cognitive or Behavioral Changes and Psychiatric Disorders (2025), 20250001454. https://ntrs.nasa.gov/citations/20250001454
- I5 NASA NTRS. Risk of Adverse Cognitive or Behavioral Conditions and Psychiatric Disorders: Evidence Report (2016), 20160004365. https://ntrs.nasa.gov/citations/20160004365
- I6 NASA. Team Risk. https://www.nasa.gov/directorates/esdmd/hhp/team-risk/ and https://www.nasa.gov/reference/risk-of-inadequate-teamwork
- I7 NASA NTRS. Team Risk Evidence Report 2022, 20220007465. https://ntrs.nasa.gov/citations/20220007465
- I8 NASA NTRS. Evidence Report: Risk of Performance Decrements and Adverse Health Outcomes Resulting from Sleep Loss, Circadian Desynchronization, and Work Overload, 20160003864. https://ntrs.nasa.gov/citations/20160003864
- I9 Barger et al. Prevalence of sleep deficiency and use of hypnotic drugs in astronauts before, during, and after spaceflight: an observational study. Lancet Neurology 13(9):904–912 (2014). Original study; press-release link removed. https://doi.org/10.1016/S1474-4422(14)70122-X ; full author manuscript https://pmc.ncbi.nlm.nih.gov/articles/PMC4188436/
- I10 Jones et al. Sleep deficiency in spaceflight is associated with degraded neurobehavioral functions and elevated stress in astronauts on six-month missions aboard the ISS. Sleep 2022. https://pmc.ncbi.nlm.nih.gov/articles/PMC8919197
- I11 Flynn-Evans et al. Astronaut sleep duration varies by timing of scheduled sleep (poster), NASA NTRS 20230003916. https://ntrs.nasa.gov/api/citations/20230003916/downloads/AsMA%20Poster.pdf
- I12 NASA Spinoff 2013. Reaction Self-Test (PVT-B). https://spinoff.nasa.gov/Spinoff2013/hm_1.html ; Penn research page https://www.med.upenn.edu/uep/past_research.html
- I13 NASA NTRS. Cognitive Assessment During Long-Duration Space Flight (WinSCAT), 20100036584. https://ntrs.nasa.gov/citations/20100036584
- I14 University of Pennsylvania. Cognition Test Battery. https://www.med.upenn.edu/uep/cognition.html ; acceptability paper https://pmc.ncbi.nlm.nih.gov/articles/PMC8601114
- I15 ESA. Mars500 study overview. https://www.esa.int/Our_Activities/Human_Spaceflight/Mars500/Mars500_study_overview
- I16 Wang et al. Characteristics of mood state during 520 days isolation and confinement (Mars500), IAC-13. https://iafastro.directory/iac/archive/browse/IAC-13/A1/1/17045/
- I17 Basner et al. Psychological and Behavioral Changes during Confinement in a 520-Day Simulated Interplanetary Mission to Mars. PLOS ONE 9(3):e93298 (2014). Original Mars500 study: six men, weekly psychological measures and 3-minute PVT-B sessions. https://journals.plos.org/plosone/article?id=10.1371/journal.pone.0093298
- I18 Same original Mars500 study as I17; replaces WHYY coverage for the behavioral findings, not independent evidence. https://doi.org/10.1371/journal.pone.0093298
- I19 Stuster. Behavioral Issues Associated With Long Duration Space Expeditions: Review and Analysis of Astronaut Journals, NASA NTRS 20100026549. https://ntrs.nasa.gov/api/citations/20100026549/downloads/20100026549.pdf
- I20 Kanas, Gushin, Yusupova. Whither the Third Quarter Phenomenon? Aerosp Med Hum Perform 2021;92(8):689-691. https://asma.kglmeridian.com/downloadpdf/view/journals/amhp/92/8/article-p689.pdf
- I21 Lunar Palace 1 study, Aerosp Med Hum Perform 2015;86(9):819. https://asma.kglmeridian.com/downloadpdf/view/journals/amhp/86/9/article-p819.pdf
- I22 Think like a team: shared mental models in space analogs (review of Bell et al.). https://atlas.northwestern.edu/wp-content/uploads/2024/02/2023-Think-like-a-team-Shared-mental-models-predict-creativity-and-problem-solving-in-space-analogs.pdf
- I23 NASA NTRS. JSC Behavioral Health and Performance Operations (private psychological conferences, support services), 20170003866. https://ntrs.nasa.gov/api/citations/20170003866/downloads/20170003866.pdf
- I24 Beven. Behavioral Health and Performance Operations at the NASA Johnson Space Center (2017), NASA NTRS 20170003866. Same direct NASA presentation as I23; replacement evidence for the retained conference/support claim, not an identification of the original SpaceRef status report. Slide 15: conferences every two weeks, typically 15–20 minutes. https://ntrs.nasa.gov/citations/20170003866
- I25 Mental health in deep space: automated psychotherapy (review). Interact J Med Res 2024;13:e58803. https://pmc.ncbi.nlm.nih.gov/articles/11499717
- I26 NASA. 5 Hazards of Human Spaceflight. Replaces IANS coverage for the hazard framework. For numerical Mars communication delays use the dedicated NASA studies D1 and D2, not the old 20-minute news rounding. https://www.nasa.gov/hrp/hazards/
- I27 Same original Barger et al. (2014) study as I9; replaces NBC coverage, not independent evidence. https://doi.org/10.1016/S1474-4422(14)70122-X
- I28 NASA. Isolation – What Can We Learn From the Experiences of NASA Astronauts? Direct source for CONNECT; same as I1. https://www.nasa.gov/humans-in-space/isolation-what-can-we-learn-from-the-experiences-of-nasa-astronauts/

Source quality note: the flagged entries in this section have been replaced; duplicate codes are retained for compatibility and explicitly identified above.

## H4. Distance (D)

- D1 Communication Delays, Disruptions, and Blackouts for Crewed Mars Missions (ASCEND, NASA NTRS 20220013418). https://ntrs.nasa.gov/api/citations/20220013418/downloads/ASCEND-Communication%20Delays%2C%20Disruptions%2C%20and%20Blackouts%20for%20Crewed%20Mars%20Missions.pdf
- D2 Parisi et al. Crew autonomy and communication delay, AHFE 2024 (NASA Ames HSI). https://hsi.arc.nasa.gov/publications/AHFE_2024_Parisi.pdf
- D3 NASA. Deep Space Healthcare, Houston We Have a Podcast (2020), transcript with NASA medical experts; direct institutional source for ISS two-way video support and onboard ultrasound. Supplement: NASA, Ultrasound Scans in Space Transform Medicine on Earth (2022), for remotely guided crew examinations. https://www.nasa.gov/podcasts/houston-we-have-a-podcast/deep-space-healthcare/ ; https://www.nasa.gov/missions/station/ultrasound-scans-in-space-transform-medicine-on-earth/
- D4 Integrated Medical Model / exploration medical capability (NASA NTRS 20170004604). https://ntrs.nasa.gov/api/citations/20170004604/downloads/20170004604.pdf
- D5 Same direct NASA sources as D3. Source replacement supports telemedicine and ultrasound; does not establish an exhaustive equipment inventory or guarantee that no physician is on a particular crew.
- D6 Crew Medical Officer interview study, 10 former CMOs (NASA NTRS 20230013415). https://ntrs.nasa.gov/api/citations/20230013415/downloads/IWS_CMO.pdf
- D7 Exploration Medical Officer KSA poster (NASA NTRS 20230007088). https://ntrs.nasa.gov/api/citations/20230007088/downloads/ExMO%20KSA%20Poster.pdf
- Isolation links to this hazard: see 03_ISOLATION_RESEARCH.md [I6, I25, I26].

## H5. Closed environment (E)

- E1 NASA HRP. Hazard: Hostile Closed Environments. https://www.nasa.gov/hrp/hazard-hostile-closed-environments
- E2 NASA Office of the Chief Health and Medical Officer. CO2 technical brief. https://nasa.gov/wp-content/uploads/2023/03/co2-technical-brief-ochmo.pdf
- E3 NASA OCHMO. Spacecraft acoustic limits, conditions and countermeasures (technical brief). https://www.nasa.gov/sites/default/files/atoms/files/acoustics_technical_brief_ochmo_0.pdf
- E4 Tierney et al. Longitudinal multi-omics analysis of host microbiome architecture and immune responses during short-term spaceflight. Nature Microbiology 9:1661–1675 (2024), published 11 June 2024. Peer-reviewed original study, four Inspiration4 participants; replaces preprint. https://www.nature.com/articles/s41564-024-01635-8 ; https://doi.org/10.1038/s41564-024-01635-8
- E5 NASA NTRS. Clinical nutrition assessment of ISS astronauts (Expeditions 1–12). https://ntrs.nasa.gov/api/citations/20060049121/downloads/20060049121.pdf
- E6 NASA. Nutritional Biochemistry, sections Studying the Role of Nutrition in Spaceflight and Operational Goals. Already a direct NASA source; canonical URL replaces the opaque page-ID link. Confirms ISS Food Intake Tracker first deployed in 2016. https://www.nasa.gov/directorates/esdmd/hhp/nutritional-biochemistry/
- E7 NASA NTRS. HERA meal-replacement bar study. https://ntrs.nasa.gov/api/citations/20170009922/downloads/20170009922.pdf
- Related: 02_MICROGRAVITY_RESEARCH.md (headache/vision, body mass, bone), 03_ISOLATION_RESEARCH.md (sleep).

## H6. Reference ranges (R)

- R1 MedlinePlus. Vital signs. https://medlineplus.gov/ency/article/002341.htm
- R2 2025 AHA/ACC multisociety Guideline for the Prevention, Detection, Evaluation and Management of High Blood Pressure in Adults, section 2.1, Table 4. Circulation. DOI: 10.1161/CIR.0000000000001356; parallel JACC publication DOI: 10.1016/j.jacc.2025.05.007. Primary guideline replaces HCPLive. https://www.ahajournals.org/doi/10.1161/CIR.0000000000001356 ; https://www.jacc.org/doi/10.1016/j.jacc.2025.05.007 . Official AHA category/emergency chart: https://www.heart.org/en/health-topics/high-blood-pressure/the-facts-about-high-blood-pressure
- R3 MedlinePlus. Pulse oximetry. https://medlineplus.gov/lab-tests/pulse-oximetry/
- R4 NIDDK. Diabetes tests and diagnosis (table attributed to the American Diabetes Association). https://www.niddk.nih.gov/health-information/diabetes/overview/tests-diagnosis
- R5 MedlinePlus. Hypoglycemia. https://medlineplus.gov/hypoglycemia.html
- R6 NASA NTRS. Clinical nutrition assessment of ISS astronauts. https://ntrs.nasa.gov/api/citations/20060049121/downloads/20060049121.pdf
- I9, I10, I12, I17: see 03_ISOLATION_RESEARCH.md. Radiation: 01_RADIATION_RESEARCH.md. Microgravity and exercise: 02_MICROGRAVITY_RESEARCH.md. Closed environment: 05_CLOSED_ENV_RESEARCH.md.

## H7. Project rationale (X)
- X1 NASA Human Research Roadmap. Research gap Medical-701.
  https://humanresearchroadmap.nasa.gov/gaps/gap.aspx?i=716
  Accessed 13 November 2026.

- X2 Hardy JG, Theriot CA, Oswald T, Clément G. (2025).
  Spaceflight Standard Measures programme review.
  npj Microgravity 11, 78.
  https://doi.org/10.1038/s41526-025-00532-6
  Relevant sections: Data archiving, Data analysis, Limitations.
  Accessed 13 November 2026.

- X3 Hardy et al. (2026). Author correction to X2.
  npj Microgravity 12, 25.
  https://doi.org/10.1038/s41526-026-00584-2
  Checked alongside the updated original article.

---

# Part I – Targeted source audit, 13 November 2026 (v1.2)

Scope: Part G items 1–2 and directly affected claims. The six underlying detail files were not supplied and have not been edited. Their reference lists and copied numbers should be synchronized with this file. Unrelated open questions and DEMO rules remain subject to their existing review requirements.

## I1. Replacement register

| Codes | Previous source/version | Direct replacement and disposition |
|---|---|---|
| S2 | News-Medical | NASA’s 2017 radiation article |
| S6 | arXiv | Final 2021 journal review; historical cancer statement date-qualified |
| S9 | National Academies news / MSK | NASA standard §4.8 for the career limit; generic Earth-background and other-agency figures withheld |
| M2, M3 | Universe Today / EurekAlert | Lang et al. 2004, DOI 10.1359/JBMR.040307; one study, two retained codes |
| M4 | Space.com | Keyak et al. 2009, DOI 10.1016/j.bone.2008.11.014; replace “at least 14%” with loading-specific mean rates |
| M5, M12 | Phys.org | NASA Astronaut Exercise; M5 updated as the duplicate underlying M12 |
| M10 | Sakshi Post | NASA Five Hazards, Gravity Fields |
| M18 | Healio | NASA SANS risk summary; older 15%/60% split replaced with about 70% having one or more signs |
| M20 | Third-party NASAexplores mirror | NASA Ames Psychophysiology Research Laboratory |
| M22, M23, M24 | Space.com / Smithsonian / Gulf News | Original 2014 body-mass paper; M23 also updated to remove the overlapping secondary source |
| I9, I27 | EurekAlert / NBC | Original Barger et al. 2014 study; retain full manuscript and final DOI |
| I17, I18 | Newswise / WHYY | Original Basner et al. 2014 Mars500 study; weekly battery, 3-minute PVT-B; no sourced 10-minute total |
| I24 | SpaceRef status report | NASA Beven 2017 presentation for the retained support/conference claim; typically 15–20 min every two weeks |
| I26 | IANS / India TV | NASA hazard framework; D1/D2 remain the sources for numerical delays |
| I28 | SpaceDaily | NASA’s original CONNECT article |
| D3, D5 | Healthcare IT News | NASA healthcare transcript and NASA ultrasound article; narrower supported wording |
| E4 | Preprint | Tierney et al., Nature Microbiology (2024), DOI 10.1038/s41564-024-01635-8 |
| E6 | NASA page-ID URL | Already institutional; replaced with descriptive NASA Nutritional Biochemistry URL |
| R2 | HCPLive | 2025 AHA/ACC guideline §2.1, Table 4, plus official AHA chart |

## I2. Blood-pressure implementation notes

- Stage 2 uses **OR**, with inclusive boundaries: `systolic >= 140 || diastolic >= 90`. Thus 140/75 and 125/90 are both Stage 2-range readings.
- Assign the higher category if systolic and diastolic differ. A reading of 120/80 is Stage 1-range under this framework, not normal.
- Stage 2 alone is not a hypertensive emergency. Evaluate the separate severe-reading/symptom pathway first.
- A single reading does not diagnose hypertension. The app should say “reading in the Stage 2 range”; general office-BP categories and the mission-specific DEMO actions must remain visibly distinct.
- The original 15-minute repeat rule is a DEMO choice. It must not delay assessment of concerning symptoms or replace the separate severe-reading pathway.

## I3. Evidence limitations

- A direct NASA educational article is an institutional source, not automatically a primary experiment. S6 remains a review even though its final journal page replaces the preprint.
- Some publisher pages restricted direct full-text access. Bibliographic identities and retained numerical findings were checked using accessible original-article abstracts/manuscripts, publisher-indexed text, or matching official institutional sources. No claim of having read every full paper is made.
- Replacements such as I24, M18 and D3 are evidence for the revised retained claim; they are not necessarily the exact historical document reported by the former news article.
- Removed/withheld wording is documented above rather than silently assigned to an unrelated primary source.
- This audit does not clinically validate the app or close the other Part G items.

## I4. Additional verification — Part G item 17

Completed 13 November 2026.
Original sources and the linked correction were checked.
References: X1–X3.
The completion applies only to the stated citation scope.

---

# Part J – Blood results demo and Viva Intelligence (added 14 Nov 2026, v1.5)

## J1. Simulated Blood results screen (Phase 6B)
- **What it is:** one optional screen with a **fictional** white-blood-cell fixture for the demo crew member. It shows how a result from a future portable blood analyzer could flow into Vivonaut: result card with units, specimen, method, time and quality status, a Viva explanation, a trend, and an optional attachment to the local Health Handover.
- **What it is not:** Vivonaut does not analyse blood, does not connect to a device and embeds no NASA data. The permanent banner reads "Simulated analyzer. No device is connected. Demo data, not astronaut measurements."
- **No new thresholds.** No reference range, alert level or rule was added. Results never create alerts, never change Monitoring Status counts and never open the emergency path (Part D1 is unchanged). Missing values stay missing, never zero; failed assays are not shown as values.
- **What NASA actually tested (the limits the app must keep):** HemoCue WBC DIFF was demonstrated on the ISS with control solutions, not astronaut blood; the rHEALTH ONE drop cytometer flew with test particles. Neither demonstration validates an all-purpose finger-prick analyzer, and neither is shown as measuring glucose, vitamin D, cytokines, platelets or hemoglobin.
- **Not used by the build:** the Inspiration4 datasets (OSD-569, OSD-575) described in the research proposal are cited as background only; no values from them are in the app. If they are ever used, the proposal's file-level checks (hemoglobin unit, missing-value tokens, serum CO2 versus cabin CO2, race-labelled eGFR exclusion) apply.

### Sources for the Blood results screen
The Blood results screen lists these with the codes below. These codes are local to that screen and are different from the R (reference ranges) and D (distance) codes in Part H.

- **R1** NASA Glenn: In-situ Lab Analysis. [Official page](https://www.nasa.gov/glenn/glenn-expertise-space-exploration/human-health-performance/exploration-medical-technologies/in-situ-lab-analysis/)
- **R2** NASA: Protecting Astronaut Health with the Prick of a Finger. [Official article](https://www.nasa.gov/humans-in-space/protecting-astronaut-health-with-the-prick-of-a-finger/)
- **R3** NASA ISS Daily Summary, 18 January 2021. [Official operations report](https://www.nasa.gov/blogs/stationreport/2021/01/18/iss-daily-summary-report-1-18-2021/)
- **R4** NASA NTRS HemoCue technical material. [2021 presentation, ID 20210000516](https://ntrs.nasa.gov/citations/20210000516); [results and lessons learned, ID 20210026808](https://ntrs.nasa.gov/citations/20210026808)
- **R5** Rea et al. (2024), Single drop cytometry onboard the International Space Station. Nature Communications 15, 2634. [DOI](https://doi.org/10.1038/s41467-024-46483-6); [full text](https://pmc.ncbi.nlm.nih.gov/articles/PMC10963801/); [NASA NTRS record](https://ntrs.nasa.gov/citations/20230012750)
- **D1** NASA OSDR, OSD-569 / LSDS-7. [Study page](https://osdr.nasa.gov/bio/repo/data/studies/OSD-569)
- **D4** NASA: I4 Mission Datasets. [Official overview](https://www.nasa.gov/osdr-latest-news-i4-mission-datasets/); [Inspiration4 data access through the NASA Open Science Data Repository](https://www.nature.com/articles/s41526-024-00393-5)

## J2. Viva Intelligence safety rules (Phase 6C)
1. The safety layer runs before intent matching: emergency phrases open the Emergency path with the existing wording; requests for a diagnosis, a drug, a dose or treatment get the fixed refusal.
2. Answers come only from stored readings and the frozen baseline, in at most three sentences, with a "Why this answer?" list. No data means "no data", never an invented value.
3. The words "normal" and "stable" are used only when the rules engine produced that status.
4. Hidden private data (mood, stress, fatigue) is never mentioned or counted while hidden.
5. DEMO rules introduced in this phase: "close to your baseline" means within the indicator's effective spread (the larger of the observed spread and the minimum-spread floor); the trend uses the last five valid readings. Both are labelled DEMO and are not clinically validated.
6. Memory is session-only and is cleared on profile switch.
