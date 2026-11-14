# PROMPTS.md – Vivonaut build prompts (version 4.0, 14 Nov 2026)
Use ONLY from Saturday Nov 14, 2026, 9:00 am (Team Owner's local time). Before that: research and planning only.

Changes from v2: new phase order (onboarding and empty states first; context check, follow-up and handover added); Health Index removed; baseline frozen; "Ask Viva" offline instead of an API chat; voice off by default; test voice and offline early; each phase says exactly which files to attach (saves free-plan quota).

Changes from v3.1 (final record): Phase 6B (Blood results, simulated analyzer) and Phase 6C (Viva Intelligence) were added between Phase 6 and Phase 7 and run as written below; the TIP-02 tip was hidden instead of kept as a placeholder; the build order actually used was 0, 1, 2, 3, 4, 5, 6, 6B, 6C, 7.

Changes from v3: work happens inside a Claude Project (the four reference files live in Project Knowledge; STATE.md and index.html are attached per chat); relay rules for two Claude accounts (A.10); blood-analysis roadmap card added to Phase 7; optional Phase 10 (Ground Medical Dashboard); Phase 9 output saved as index_final_v9.html; new teammate tasks. Dashboard-first entry (14 Nov): Phase 1 no longer builds a welcome screen; the app opens on the dashboard with Viva's greeting and Start a Health Check in her panel, a Guided Demo button and a Help (?) button in the top bar.

---

## A. How to work (read once)
1. Start a new chat inside the Claude Project. `PROJECT_BRIEF.md`, `PROMPTS.md`, `SCIENCE_MAP.md` and `VIVA_SCRIPTS.md` are already in Project Knowledge, so you do not attach them again: the "Attach" line of each phase tells Claude which parts to use (for example "use SCIENCE_MAP.md Parts C and D"). ALWAYS attach `STATE.md`, and from Phase 2 on the latest working `index.html` (these two change after every phase, so they are NOT in the Project). Phases 0 and 1 also need the mockup image.
2. Paste ONE phase prompt. Open the result in a browser (and once with the network off) and test it against the "Done when" line.
3. If OK: ask "Give me the updated STATE.md", save it, save `index_vN.html`, go to the next phase.
4. If broken: paste the error or describe the bug, ask for a fix of that module only.
5. Limit reached: new chat, same attachments + latest working `index.html`, then the RESUME prompt.
6. Always say: "Return only the changed modules, complete, with their marker comments." This saves quota and prevents regressions.
7. Never ask for the full file unless you must replace the whole thing (end of Phase 9).
8. If the AI offers extra features, say "not now, follow the phase".
9. Never let the AI invent a threshold. Numbers and rules come from `SCIENCE_MAP.md`; anything else is labelled DEMO.
10. **Two Claude accounts (relay):** keep ONE main version. When you stop or hit a limit, send the latest `index_vN.html` and the updated `STATE.md` to your teammate; they paste the RESUME prompt and continue. Save every result as a new numbered file and never overwrite the last working version. Nobody edits the code by hand. If phases 5, 6 and 7 run in parallel, each person returns only their own modules and the Team Owner merges them.

## B. Suggested schedule (about 39 hours; adjust to your sleep)
| When (local) | Work |
|---|---|
| Sat 09:00-10:00 | Phase 0 (plan check) + Phase 1 (skeleton, dashboard-first entry, voice test) |
| Sat 10:00-14:00 | Phase 2 (data, validation, context check, charts) |
| Sat 14:00-18:00 | Phase 3 (rules engine, status, follow-up) |
| Sat 18:00-22:00 | Phase 4 (body map and dashboard wiring) |
| Sat night | Sleep. Teammates deliver reviews and source checks |
| Sun 08:00-11:00 | Phase 5 (Viva, Ask Viva, voice) |
| Sun 11:00-14:00 | Phase 6 (handover and emergency) |
| Sun 14:00-17:00 | Phase 7 (guided demo, environments, vision) |
| Sun 17:00-19:00 | Phase 8 (tasks and extras) |
| Sun 19:00-22:00 | Phase 9 (sources, QA, README, final test on 2 devices) |
| Sun 22:00-23:30 | Submit (never wait for the last minute) |
**If late, cut in this order:** Phase 10 (Ground Medical Dashboard) -> decoration and animation -> Phase 8 -> P2 items -> P1 depth in Phases 5 and 7. **Never cut:** validation, context check, rules engine with "How Viva decided", handover, guided demo, body map, Sources page.

## C. RESUME prompt (new chat or after a limit)
Read PROJECT_BRIEF.md and STATE.md. The current working file is attached. Continue from "Next step" in STATE.md. Do not rewrite finished modules. Do not add features outside the current phase. Do not invent thresholds: use SCIENCE_MAP.md or label DEMO. Return only changed modules, complete, with their marker comments, then the updated STATE.md. If you must stop early, finish the current module cleanly so the file still runs.

---

## PHASE 0 – Architecture check (10 minutes, no code)
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Parts A, C, D), mockup image.
Prompt: Read the attachments. Do NOT write code yet. Reply in under 100 lines with: (1) a 10-line product summary to confirm understanding; (2) the **data flow** from a typed reading to Viva's reply, step by step (validation, context check, rules, alerts, follow-up, dashboard, handover); (3) what can be built with plain HTML, CSS, JS and inline SVG, with no libraries, and what cannot; (4) the shared state object shape (JSON): profiles (new/demo), readings, baselines, assessments, alerts, follow-ups, handovers, tasks, mission settings, privacy flags; (5) the event bus names; (6) the module list with the function names each will export; (7) CSS variable names; (8) any conflict or risk you see (especially voice, offline, storage); (9) the exact build order and how you will keep each phase testable.
Done when: you approve the architecture and paste it into STATE.md.

## PHASE 1 – Skeleton, design system, dashboard-first entry, profiles, voice test
Attach: PROJECT_BRIEF.md, STATE.md, VIVA_SCRIPTS.md (Part 1A only), mockup image.
Prompt: Build the first runnable `index.html` per PROJECT_BRIEF.md.
- CONFIG, DATA_MODEL (state; two fictional profiles Mark Anderson and Sebastian; a NEW profile with empty health values and a DEMO profile placeholder; "Demo Mars transit mission, Mission Day 124"), UI_LAYOUT (dashboard grid, top bar with profile switcher, mission name, link status, UTC clock, a DEMO MODE badge, a clearly visible **Guided Demo** button and a **Help (?)** button; navigation; Emergency access always visible), CSS variables (dark space theme; status colors with icon and text: Stable, Watch, Needs assessment, Alert, No data grey).
- ONBOARDING (dashboard-first, no welcome screen, no launch overlay): the app opens directly on the Dashboard with the DEMO profile (Mark Anderson). Viva's panel shows her first message (WEL-01, WEL-02) with the chips **Start a Health Check** and **Ask Viva** (Ask Viva is a placeholder until Phase 5). **Start a Health Check** makes Viva ask which crew profile (FTE-06) and opens it as a NEW empty profile (FTE-10, FTE-11). The **Guided Demo** button in the top bar is a placeholder until Phase 7 (it opens a "coming in Phase 7" message). The **Help (?)** button opens an optional, dismissible panel (FTE-01 to FTE-03, FTE-05, FTE-07, FTE-08, CAR-04); it never opens by itself. Voice stays off by default.
- Empty states for every card exactly as in Part 1A (EMP-01 to EMP-09). In a new profile nothing shows a value, a status or an alert.
- Screens as placeholders: Dashboard, Vitals, Trends, Handover, Challenges, Settings, Vision, Sources.
- A small **voice test button** in Settings that speaks one sentence with `speechSynthesis`, lists the available voices, and shows a message when none exist (SYS-06).
- Original logo and avatar (SVG). No NASA insignia, no external assets, no CDN. Fully responsive. Marked modules.
Note: the steady demo data arrives in Phase 2, so until then the demo profile also shows "No data" on its cards.
Done when: opens offline by double-click (test with the network off), the app opens directly on the dashboard with Viva's greeting in her panel, Start a Health Check opens an empty profile showing only "No data", the Guided Demo and Help (?) buttons are visible in the top bar and the Help panel opens and closes, the voice test works or shows the no-voice message, no console errors, navigation works at 360 px and 1440 px.

## PHASE 2 – Data, validation, context check, measurement guidance, charts
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Parts A7, C, D3), VIVA_SCRIPTS.md (Parts 3, 4, 6.7, 6.9), latest index.html.
Prompt: Implement DATA_MODEL additions, VALIDATION (including the measurement-context check), MEASUREMENT_GUIDE, CHARTS and the Vitals screen for the **P0 indicators** in SCIENCE_MAP.md A7.
- Entry form with units. Each reading stores value, unit, timestamp, source, data-confidence label (Complete / Needs verification / Incomplete / Simulated), measurement context (posture, recent exercise, method), crew, mission day, environment.
- VALIDATION: plausibility limits from SCIENCE_MAP.md C1; impossible values rejected with SYS-01; unusual but possible values ask to confirm and are saved as unconfirmed (SYS-02); systolic must exceed diastolic (SYS-05); stale readings (SYS-03); missing measurements (SYS-04).
- **Context check** (CTX-1 to CTX-6): when a reading departs from the baseline spread or the reference, label it "Needs verification" and run the CTX-01 to CTX-10 dialogue before the engine interprets it.
- **Baseline**: median of the first 5 valid calm readings on different days, with spread; frozen; changed only by "Recalibrate baseline" with a logged reason (SYS-08). Until then: "Baseline: not available yet".
- MEASUREMENT_GUIDE: per indicator a help card (EXP lines, MEA steps, reference chip with its type tag, source) and original SVG pictograms for the Tier-1 devices. Photo option with `<input type="file" accept="image/*" capture>`: show the image, the user types the number (MEA-01, SYS-12). No video, no OCR, no electrode diagrams.
- CHARTS: hand-built SVG line charts with 1D/1W/1M ranges, baseline band, colored zones, tooltip; sparklines; "No data" empty states.
- "Load demo data": 124 days of believable SIMULATED data in two datasets: **steady** (the default dashboard) and **drift** (heart rate rising, sleep falling, fatigue rising; for demo scenario 2). Label "Simulated Data" everywhere.
Done when: entering a value validates, saves, and updates sparklines and charts; an exercise-flagged high reading triggers the context check and does not change the status; a new profile still shows "No data".

## PHASE 3 – Rules engine, Monitoring Status, alerts, follow-up
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Parts C, D, E), VIVA_SCRIPTS.md (Part 6), latest index.html.
Prompt: Implement RULES_ENGINE and FOLLOWUP exactly from the rule catalogue in SCIENCE_MAP.md Part D (rule IDs RAD, GRV, ISO, DST, ENV, VIT, DATA, CTX, FUP, HND) for the P0 indicators; implement P1 rules only if the indicator exists.
- Four statuses: Stable / Watch / Needs assessment / Alert. The **fixed emergency screen** is a separate path opened only by P0 symptoms and the two P1 values (blood pressure above 180 and/or 120 with symptoms; SpO2 at 88% or lower). Radiation values raise the highest Alert but never open the emergency screen.
- Three analyses: baseline deviation, trend (slope over days), multi-indicator rules (e.g. heart rate up + sleep down + fatigue up = "recovery strain pattern"; the radiation symptom rule with its 72-hour window; nausea timing: radiation rule has priority after a solar-event alert).
- Each result carries: plain message (VIVA_SCRIPTS WRN lines), recommended action, when to repeat, when to contact crew or flight surgeon, linked hazard, source tag, type tag (SOURCED / DEMO / BASELINE) and "How Viva decided" listing rule IDs and values.
- **Monitoring Status** counts (Stable, Watch, Needs assessment, Alert, No data). NO Health Index percentage.
- Priority and conflicts exactly as SCIENCE_MAP.md D1. Missing data never counts as Stable (DATA-1, DATA-5, DATA-6).
- **Follow-up loop** (FUP-1 to FUP-3): every Watch or higher creates a follow-up (action, reassess time, evaluation with before and after and the sentence "This shows a change. It cannot show what caused it").
- Link-status rules DST-1 (Live / Delayed / Blackout) from Settings.
- Alerts card: severity order, acknowledge, history. Update everything through the event bus.
- A hidden developer panel to inject values and run each rule, plus a unit-test list I can read (rule ID, input, expected result).
Done when: editing values changes states and alerts coherently, every alert explains itself, no data means no status, and the developer panel shows each rule firing as expected.

## PHASE 4 – Body map and dashboard wiring
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Part A), latest index.html.
Prompt: Implement BODY_MAP and connect the dashboard. Original inline-SVG human figure (front view, glowing outline) with clickable zones: Brain, Heart, Lungs, Bones and muscles, Immune, Eyes. Each zone shows a status color from the linked indicators (grey when no data), a callout, and opens a plain-language card: current linked values or "No data", What does this mean? What should you do? Linked hazard, Source, type tags, and the disclaimer "Illustrative; status reflects linked indicators, not real organ condition". Hover, focus and keyboard support; subtle animation (off for reduced motion). Clicking a zone offers the relevant quick check. Wire the dashboard: Monitoring Status counts, indicator cards with sparklines and type tags, alerts, trend chart. **Do not copy these mockup contradictions:** "All Systems Nominal" beside an active alert, a Health Index percentage, "Brain Healthy" or "Immune Good" without data, Emergency Mode when nothing is triggered. A hidden developer toggle forces each zone to any status for testing.
Done when: every zone opens the right card, new-profile zones are grey, and body map, status counts and alerts always agree.

## PHASE 5 – Viva: scripted assistant, Ask Viva, voice, reminders
Attach: PROJECT_BRIEF.md, STATE.md, VIVA_SCRIPTS.md (all), latest index.html.
Prompt: Implement VIVA_ASSISTANT using the lines and IDs in VIVA_SCRIPTS.md stored in ONE data object (not scattered in code).
- Original animated SVG robot (idle, talking, concerned), chat panel with quick-reply chips.
- First load: Viva's panel greeting (WEL-01, WEL-02) and the chips Start a Health Check and Ask Viva, built as static text in Phase 1, are now driven by the dialogue manager.
- Scripted dialogue manager: greets by name and mission day, runs the scheduled measurement, explains how, waits for the value, runs the context and symptom questions, summarizes, adapts to engine state; WRN, STA, RTN, CAR and FUP lines as written. Viva never mentions a value she has not been given.
- **Ask Viva (offline)**: suggested question buttons plus simple local keyword matching, ASK-00 to ASK-11. No API, no internet, no speech recognition.
- **Voice**: `speechSynthesis` with captions; **off by default**; a Listen button on each message; mute, voice picker, rate; the Guided Demo start prompt "Play with voice?"; SYS-06 when no voice exists. Spoken forms from VIVA_SCRIPTS.md part 1 (SpO2, mmHg, etc.).
- Reminder scheduler following the mission-day schedule plus a "simulate time forward" control. Missed measurements never penalized (RTN-06, RTN-17).
- CONNECT tips (TIP-01 to TIP-07) labelled as wellness tips; hide TIP-02 (no visible placeholder) until the exact Openness wording is confirmed.
Done when: a morning check-in runs by text, voice works only when turned on, Ask Viva answers all suggested questions with the network off, and the dashboard updates from the conversation.

## PHASE 6 – Health Handover and Emergency Center
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Parts D, E), VIVA_SCRIPTS.md (Parts 6.11, 7), latest index.html.
Prompt: Implement HANDOVER_REPORTS and EMERGENCY.
- **Health Handover** (HND-1, HND-2, HND-01 to HND-09): a "Generate Health Handover" button builds a real report from the app data: current indicators, changes from baseline, alerts so far, measurements repeated, actions tried, symptoms reported, missing or unconfirmed data, questions for the ground team. Psychological answers only with explicit consent. Stored locally as "ready and queued, not sent". Printable view. Shows link state (Live / Delayed / Blackout) and the delay wording (DST-1).
- **Emergency Center**: full-screen red mode, big buttons, **fixed text only** (EMG-01 to EMG-17), label "Educational simulation, not a medical protocol". Flow: chest pain -> "stop what you are doing" -> call the nearest crewmate -> contact crew medical officer and ground flight surgeon -> ground link simulation with delay -> incident log with timestamps -> report ready and queued. Include the behavioral emergency screens (EMG-11 to EMG-15). No oxygen, drug or procedure unless I paste a cited first-aid source for it. Voice only if voice is on; otherwise captions and a large Listen button. Runs by clicks only.
Done when: the scenario runs end to end and produces a report; the handover is generated from real data and states what is missing; nothing says "sent" except the simulated demo send.

## PHASE 6B: Blood Results (simulated analyzer), isolated module

Attach: STATE_phase6.md, index_v6.html, and the excerpt of the blood-biomarker research (sections 4, 5.1, references R1-R5, D1, D4, line BIO-08). In the excerpt, "The software" = Vivonaut and "agent" = Viva.

Goal: add ONE optional screen "Blood results" that demonstrates, with simulated data, how a result from a future portable blood analyzer (concept inspired by NASA's HemoCue WBC DIFF and rHEALTH ONE demonstrations) would flow into Vivonaut: result card, Viva explanation, trend, local Health Handover attachment.

Rules (non-negotiable):
- New module `/* ===== MODULE: BIOMARKER_DEMO ===== */`, namespace Vivo.Bio, switch ENABLE_BIOMARKER_DEMO = true (easy to set false). Everything else must behave exactly as in v6.
- Offline, no libraries, no network, no Bluetooth/USB/serial. No "Connected" indicator. Permanent banner on the screen: "Simulated analyzer. No device is connected. Demo data, not astronaut measurements."
- Panel: WBC only (total WBC, absolute neutrophils, absolute lymphocytes), units x10^9/L or cells/uL, with specimen "capillary whole blood (simulated)", method, timestamp, quality status (available / missing / unverified / assay_failed). Fictional fixture for Mark Anderson across mission days; clearly labelled fictional. Missing = null, never 0.
- Button "Load simulated analyzer result" adds the next fixture result. One fixture row has a missing value and one has assay_failed, to show the failure behaviour.
- Viva explains only; no diagnosis, no cause inference, no advice, no supplements. Use these lines (max 3 sentences): BIO-02 "This demonstration uses fictional results. No blood analyzer is connected." BIO-03 "This result describes the number of white blood cells in a blood sample. It does not tell us the cause of a change on its own." BIO-04 "The differential separates white blood cells into types. A cell count does not show every aspect of immune function." BIO-05 "There is no result available for this sample. I will leave it marked as missing." BIO-07 "I can add the result, its source and any missing information to the local handover." BIO-08 "A future version could receive results from a validated portable blood analyzer. Device integration is not implemented."
- Blood results NEVER create alerts, never change Monitoring Status counts, never open the emergency path, never trigger P0. Urgent symptoms never wait for a blood result.
- Handover: optional attachment (consent-filtered like HND-09), includes value, unit, specimen, "simulated", "No device connected", missing info. Keep "ready and queued, not sent".
- Privacy: profile switch behaviour and hidden private data stay correct.
- Show a small, honest "Why this matters / NASA precedent" card: NASA tested HemoCue WBC DIFF on the ISS with control solutions (not astronaut blood) and the rHEALTH ONE drop cytometer in microgravity (test particles). State plainly this does not validate an all-purpose finger-prick analyzer. Do not claim the device measures glucose, vitamin D, cytokines, platelets or hemoglobin.
- Add the references R1-R5, D1, D4 to SOURCES (titles and URLs exactly as in the excerpt; do not invent any).
- Add tests to the dev panel (missing stays null, assay_failed not rendered as a value, no alert/count change, handover filter, switch off => nothing visible). All 77 existing tests must still pass.
- Deliver index_v6b.html + STATE_phase6b.md, then verify in a browser: console errors 0, external requests 0.
Done when: the screen works offline with the switch on and disappears completely with it off; nothing says a device is connected; the existing developer-panel tests and the new ones pass; console errors 0 and external requests 0.

## PHASE 6C: Viva Intelligence (context-aware, on-device, explainable)

Attach: STATE_phase6b.md, index_v6b.html, VIVA_SCRIPTS.md.

Goal: make Viva feel like a capable assistant while staying offline, scripted-by-rules and safe. Do NOT call it an AI model anywhere in the UI. Subtitle: "Context-aware assistant. Runs on this device."

Build (extend the VIVA_ASSISTANT module; keep the existing LINES object as the only place for wording):
1. Free-text input ("Ask Viva anything about your health data...") on the Ask Viva screen.
2. Intent engine: normalise text (lowercase, trim, remove punctuation), fix common typos (edit distance <= 1 on keywords), match synonyms and short phrases to intents: heart rate, blood pressure, SpO2/oxygen, temperature, sleep, mood/stress/fatigue, radiation, cabin environment, hydration/food, exercise, symptoms, baseline, alerts/status, handover/report, blood results (6B), reminders, help, greetings, thanks. Score by keyword weight; choose the best intent, or ask "Did you mean ...?" with 2-3 buttons if confidence is low.
3. Data-grounded answers: for a metric, answer from the stored readings and the frozen baseline (latest value, change vs baseline, trend, last-reading age, class VALID/PROVISIONAL/HELD/STALE). Template sentences with filled values, e.g. "Your last sleep record was 5.2 h, 1.8 h below your baseline. This shows a change. It cannot show what caused it." No data => say there is no data and offer to add a reading. Never invent values.
4. Conversation memory (session only, cleared on profile switch): remember the last metric and intent, so follow-ups like "and yesterday?", "what does that mean?", "why?", "is that normal?" resolve to it. After each answer offer 1-2 relevant follow-up buttons.
5. Safety layer (runs BEFORE intent matching): emergency phrases (chest pain, cannot breathe, shortness of breath, fainting, severe bleeding, suicidal thoughts, etc., plus obvious misspellings) open the Emergency path with the existing wording. Requests for diagnosis, medication/dose, or treatment get a fixed refusal: "I can't diagnose or recommend treatment. I can show how your readings changed and help prepare a handover for the medical team." Out-of-scope or unclear text gets: "I can help with your health readings, check-ins, reminders and handover. Try one of these:" plus buttons.
6. Privacy: respect hidden private data (mood/stress/fatigue) after a profile switch; Viva must not mention or count hidden data.
7. Answers max 3 sentences, plain language, no diagnosis, no cause inference, no treatment advice. All new wording goes in LINES with IDs (INT-xx) and is listed in STATE for review.
8. Add a small "Why this answer?" link on each data answer that shows which readings and baseline were used (explainability).
9. Tests in the dev panel: at least 60 phrasing cases (typos, synonyms, follow-ups, emergency phrases, diagnosis requests, gibberish, empty input), no-data answers, profile-switch memory clearing, hidden-data not leaked. All previous tests must still pass.
10. No libraries, no network, no speech recognition. Voice stays off by default. Deliver index_v6c.html + STATE_phase6c.md; verify console errors 0 and external requests 0.
Done when: typed questions (typos, synonyms, follow-ups, emergency phrases, diagnosis and dose requests, gibberish) behave as specified; the developer-panel tests pass; console errors 0 and external requests 0.

## PHASE 7 – Guided demo, mission environments, vision
Attach: PROJECT_BRIEF.md (including section 10A), STATE.md, SCIENCE_MAP.md (Part E), VIVA_SCRIPTS.md (Parts 8 and 8B), latest index.html.
Prompt: Implement GUIDED_DEMO (launched from the Guided Demo button in the top bar; three scenarios in PROJECT_BRIEF.md section 11, DEM-01 to DEM-07; captions, progress strip, Pause / Skip / Replay; "Play with voice?" prompt defaulting to no; scenario 2 includes the context check, the follow-up and ends by generating the Health Handover), MISSION_ENV (Space station / Spacecraft in transit / Lunar base / Mars base: gravity note, mass-measurement wording, delay, evacuation reference, equipment, emphasized hazards per SCIENCE_MAP.md Part E; values marked "verify" stay labelled), and VISION_ROADMAP (constellation: bright = working, pulsing = prototype, dim = roadmap; tap cards; "Connect device (roadmap)" and "Peer awareness (roadmap)"; the roadmap list in PROJECT_BRIEF.md section 10) and the **Point-of-Care Blood Analysis Concept** card (PROJECT_BRIEF.md 10A; dim star, concept only; no device, no blood analysis, no biomarker in the analysis; exact wording VIS-01 to VIS-04 in VIVA_SCRIPTS.md Part 8B).
Done when: a judge understands the whole project in 3 minutes with zero reading, and the default dashboard raises no alert by itself.

## PHASE 8 – Mission tasks, extras (cut first if late)
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Part A7), VIVA_SCRIPTS.md (Parts 3, 4, 5), latest index.html.
Prompt: Implement TASKS_GAMIFICATION (daily tasks with progress like 4/5, weekly streak, personal progress timeline, exercise and sleep goals; tasks complete from real actions; rewards for consistent and honest reporting, never for good numbers; no punishment when unwell; "Viva learns your normal as you check in"), TIMELINE, and then the **P1 indicators** one by one (reaction check labelled "simplified demo, not validated", vision questions, food and fluid intake, headache, feeling connected, motion sickness, dizzy on standing, optional glucose: manual entry only, built only if time allows, never at the expense of the P0 core), each with its explanation, steps and rules from SCIENCE_MAP.md. Stop at any point where the file would become unstable.
Done when: tasks and streak respond to real use, and each added indicator works through validation, engine and Viva.

## PHASE 9 – Sources, About, QA, polish
Attach: PROJECT_BRIEF.md, STATE.md, SCIENCE_MAP.md (Parts F, G, H), latest index.html.
Prompt: Implement SOURCES_ABOUT: all sources from SCIENCE_MAP.md Part H, tools (none external), assets (original SVG, system fonts), AI-use disclosure (exact text in PROJECT_BRIEF.md section 20), medical disclaimer, what is simulated, limits, roadmap, remote-communities note. Then QA against the 12 required test cases in PROJECT_BRIEF.md section 19, plus every screen at 360 and 1440 px, keyboard only, reduced motion. Fix bugs, remove dead code, optimize. Provide the final `README.md` and final STATE.md. Return the full final `index.html` only now, and save it as `index_final_v9.html` (the submission candidate). In Sources, list a reference for the roadmap blood-analysis card only if the science member verified it.
Done when: zero console errors; every button works or clearly says "roadmap"; all 12 test cases pass.

---

## PHASE 10 – Ground Medical Dashboard (OPTIONAL, only after Phase 9 is saved)
Attach: PROJECT_BRIEF.md (sections 5, 10A, 15), STATE.md, SCIENCE_MAP.md (Part E only), VIVA_SCRIPTS.md (Parts 6.11 and 8B), latest `index_final_v9.html`.
Start only if Phase 9 passed and at least 2 hours remain before the deadline. Work on a COPY. If it is not stable within 30 minutes, drop it and submit `index_final_v9.html`.
Prompt: Implement GROUND_DASHBOARD: a small, read-only, simulated view of the ground team reviewing the Health Handover. No new rules, no new thresholds, no network, no server, no chat.
- A "Ground view (simulation)" button on the Handover screen. A permanent label: "Simulated ground view. No real transmission." (GND-01).
- It shows: link status (Live / Delayed / Blackout) from Mission Settings; the latest queued Health Handover (open it); the astronaut summary, current Monitoring Status, active alerts and changes from baseline, missing or unconfirmed data, and follow-ups. Reuse existing data and components.
- Link behaviour (GND-02 to GND-05): Live, the report appears at once; Delayed, it appears after a simulated countdown using the environment's delay; Blackout, it stays "ready and queued, waiting for contact". The simulated "received" wording appears only here. Private wellbeing answers appear only if consent was given in the handover (GND-06).
- The app gives no medical advice from the ground side. Mention the simulation in Sources/About.
Done when: from the Handover screen the ground view shows the queued report with the correct link state; nothing says "sent" except the simulated "received"; no console errors; the 12 Phase 9 test cases still pass.

---

## D. Judge-test checklist (run yourself before submitting)
- [ ] Opens offline from a double-click with the network off; no CDN, no console errors.
- [ ] Opens directly on the dashboard; Viva greets in her panel; Guided Demo button visible in the top bar; Start a Health Check inside Viva's panel; Help (?) panel optional and dismissible; voice off.
- [ ] Guided demo plays all three scenarios without breaking.
- [ ] The default dashboard raises no alert on its own; a new profile shows only "No data".
- [ ] Every P0 indicator: help card, validation, context check, type tag, source.
- [ ] No Health Index percentage anywhere; Monitoring Status counts agree with the body map and alerts.
- [ ] Every alert shows "How Viva decided" with rule IDs.
- [ ] Follow-up shows before and after and says it cannot show cause.
- [ ] Handover is generated from real data and says "ready and queued, not sent".
- [ ] Emergency scenario playable end to end, labelled "Educational simulation, not a medical protocol".
- [ ] Ask Viva answers all suggested questions offline; typed questions work; emergency, diagnosis and dose requests are handled by the safety layer.
- [ ] Vision screen separates working / prototype / roadmap.
- [ ] Simulated data labelled everywhere; radiation dose says "Simulated".
- [ ] The blood-analysis card says "Concept. Not built." and nothing claims blood analysis or a device. If Phase 10 exists: "Simulated ground view. No real transmission."
- [ ] Private cards hidden after a profile switch.
- [ ] Sources page complete; AI use disclosed.
- [ ] Tested on a phone and a laptop; two browsers; with no voices available.

## E. Submission checklist (Team Owner)
- [ ] Project file/link works from a clean browser.
- [ ] All data, tools, resources, code, text, images listed.
- [ ] No copyrighted or restricted material (no NASA insignia, no stock photos, no real mission names with fictional crew).
- [ ] AI assistance disclosed.
- [ ] README included.
- [ ] Submitted before Sunday 11:59 pm, with a safety margin.
- [ ] Only the Team Owner submits.

## F. Teammate tasks (can start NOW; none of them is building)
- **Science member:** (1) replace secondary sources by primary NASA or journal pages (list: SCIENCE_MAP.md Part G item 1); (2) confirm Stage 2 blood-pressure thresholds from AHA/ACC; (3) verify "Medical-701" and the 2025 Standard Measures paper before anyone cites them; (4) confirm the exact CONNECT "Openness" wording; (5) find a public first-aid source (e.g. Red Cross, AHA) for any step beyond calling help in the emergency flow; (6) if possible, a clinician reviews the DEMO rules and the emergency and behavioral lines.
- **Content member:** review VIVA_SCRIPTS.md for tone and clarity (keep sentences short, no diagnosis).
- **Marialena:** (1) prepare the presentation slides and share the first version with the Team Owner for review; (2) research the Point-of-Care Blood Analysis Concept (candidate markers, NASA study pages) and send sources to the science member for verification; nothing enters the app until verified.
- **QA/docs member:** collect devices and browsers; test `speechSynthesis` voices on each; test with the network off; prepare the README structure and the AI-use log.
Do NOT build or generate app code before Saturday 9:00 am.
