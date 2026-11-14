# PROJECT_BRIEF.md – VIVONAUT
NASA Space Apps Challenge 2026 · Challenge: "Create Health Monitoring Software for Astronauts on Space Missions"
**Version 4.0** (14 Nov 2026, final project record). In the Claude Project this file is always available. At the start of EVERY new chat, attach STATE.md and the latest index.html (they change after every phase, so they are not stored in the Project).

Changes from v2: Health Index replaced by Monitoring Status; baseline frozen after calibration; Viva is a companion, not "doctor-like"; three entry modes (Guided Demo, Explore, Health Check); empty-data rules; measurement-context check; follow-up loop; Earth-independent Health Handover as the signature feature; offline "Ask Viva" instead of an API chatbot; voice off by default; privacy between profiles; build priorities P0/P1/P2; science map complete.

Changes from v3 (13-14 Nov team decisions): new section 10A (Point-of-Care Blood Analysis Concept = roadmap card only; Earth-independent Health Handover confirmed as core; Ground Medical Dashboard = optional simulated demo, Phase 10, built last); safety rule 15.13; module GROUND_DASHBOARD; team workflow for two Claude accounts and the presentation slides (section 18). Dashboard-first entry (14 Nov): no welcome screen and no launch overlay; the app opens directly on the dashboard, Viva's panel carries the introduction and the Start a Health Check entry, the Guided Demo is a button in the top bar, and an optional dismissible Help panel replaces the intro screens (section 12). Blood glucose stays optional, manual entry only, built only if time allows.

Changes from v3.1 (14 Nov 2026, final build): the blood-analysis idea grew from a roadmap card into an isolated, clearly simulated **Blood results** screen (Phase 6B, module BIOMARKER_DEMO, switch ENABLE_BIOMARKER_DEMO); Viva gained a free-text **Viva Intelligence** layer that stays on-device and rule-based (Phase 6C); Phases 6, 6B, 6C and 7 were built and tested (254 developer-panel tests). Where a section below says "roadmap card only" for blood analysis, section 10A item 2 is the current rule.

---

## 0. How to read this document
- Sections 1-4: what we are building and why.
- Sections 5-9: how it works (intelligence, data, guidance, emergency, engagement).
- Sections 10-12: scope, demo, entry experience, screens.
- Sections 13-15: hard technical, design and safety rules (non-negotiable).
- Sections 16-20: science inputs, hackathon rules, workflow, tests, documentation.
If a rule here conflicts with a convenient shortcut, the rule wins. If this file and SCIENCE_MAP.md disagree on a number or a rule ID, SCIENCE_MAP.md is the reference for the numbers; fix this file.

---

## 1. Identity
**Product:** Vivonaut – "Your Intelligent Health Companion in Space".
**Team:** Vivonaut (Universal Event, 4 members; one Team Owner submits).
**Assistant persona:** **Viva** – a health companion that helps astronauts understand their health data and follow approved guidance. She is **not a doctor and not a therapist**, and she says so. She talks to the astronaut by name. Demo crew (fictional): Mark Anderson and Sebastian.
**Identity (decision C, hybrid):** a personal daily health companion that, when something changes, becomes a **follow-up and handover** partner: it verifies the measurement, explains the change, guides the next step, checks back, and prepares a structured summary for the ground team. We say "supports crew autonomy". We never say "medical decision-making system" or "replaces the flight surgeon".
**One-sentence definition:** Vivonaut is an interactive astronaut health companion that monitors physical and mental well-being, verifies and interprets changes against the astronaut's own baseline, guides the next step with explainable rules, follows up on it, and prepares an Earth-independent health handover when contact is delayed or lost.
**Design philosophy:** Make complex health information simple, visual, interactive and actionable. Astronauts are not doctors, so explain in plain words.
**Core promise:** Not a dashboard of numbers. A companion that asks, verifies, explains, follows up and hands over.

## 2. The challenge, decoded
Problem: long missions (Moon, Mars) mean delayed or absent contact with Earth, no physician aboard on stations today, and astronauts must spot health changes in themselves. NASA HRP lists five hazards: space radiation; isolation and confinement; distance from Earth; gravity fields; hostile closed environments.
Official objective: a **visual tool** that helps astronauts assess their own health and gives guidance on improvement. Any input is allowed (keyboard, mouse, camera), any health indicator is allowed.
Official questions the app must visibly answer:
1. Which measurements can be done in space, and how?
2. Why is each measurement needed?
3. How do spaceflight hazards affect each indicator?
4. When does a result need the crew or ground flight surgeons?
5. What actions prevent a critical condition?
The official video adds: assess own health, guide the response in an emergency, explain how to take each measurement, why it matters and what to do when a value looks abnormal, remind the crew to measure, adapt to spacecraft / station / lunar base, remember astronauts are not doctors. Example emergency: a crewmate on the way to Mars feels sharp chest pain and collapses.
Optional ideas named by organizers (we cover them): different environments, measurement reminders, gamification, dynamic charts, color coding, simple instructions, clickable human figure.
Extra angle: lessons can help remote communities on Earth with limited health services. Mention in About.

## 3. Winning strategy
Judges open the project alone (no live presentation). So:
1. **First 10 seconds:** the app opens directly on a striking dashboard (body map, Viva, status colors). Viva's panel greets the visitor and offers Start a Health Check, and a clear Guided Demo button sits in the top bar (section 12).
2. **First 3 minutes:** the **Guided Demo** (top-bar button, recommended) plays three prepared scenarios with captions.
3. **Depth when they dig:** every value has an explanation, a type tag (Sourced Reference / Personal Baseline / Simulated Data), a "How Viva decided" panel and a source.
4. **Signature feature:** the **Earth-independent Health Handover**: one button generates a real structured report from the data in the app. This is the strongest tie to the "distance from Earth" hazard.
5. **Honesty:** a Vision/Roadmap screen shows exactly what works, what is prototype and what is future.
6. **Science credibility:** all five hazards mapped to indicators with sources (SCIENCE_MAP.md).
7. **Complete documentation:** sources, tools, assets, AI use, simulated data.
Judging dimensions (typical Space Apps): impact, creativity, scientific validity, technical execution, clarity.
**Positioning rule:** never claim NASA "overlooked" something. Medical-701 and the Standard Measures publication have been checked; see SCIENCE_MAP.md Part H7, X1–X3, and the verification note in Part I4. Use these references only within that documented scope.

---

## 4. The five systems (big picture)
1. **Health Monitoring** – collect indicators periodically.
2. **Intelligent Health Analysis** – baseline, trends, multi-indicator reasoning, measurement checks.
3. **Interactive Health Companion (Viva)** – text (and optional voice) conversation, reminders, questions, explanations, offline "Ask Viva".
4. **Emergency Response** – detect warning signs, switch to fixed, pre-written guidance.
5. **Mission-aware Health Management** – adapt to environment, mission day, equipment, communication delay and autonomy.

---

## 5. Intelligence loop: "From Monitoring to Decision"
Six steps for every reading:
1. **Observe (Collect)** – manual entry, questionnaire, touch, photo (concept). Record time, source, method.
2. **Verify (Validate)** – unit and plausible-range check; missing fields; stale data; then the **measurement context check**: if the reading departs from the person's baseline or the reference, label it "Needs verification" and ask context (recent exercise, posture, technique, first or repeated, symptoms) before interpreting. "Data Confidence" = quality and completeness of the measurement, **never** a probability of illness.
3. **Interpret (Analyze + Assess)** – baseline comparison, trend, multi-indicator rules. States: **Stable / Watch / Needs assessment / Alert**; the fixed **emergency screen** is a separate path (section 8).
4. **Guide** – Viva explains in plain words, asks follow-ups, says when to re-measure and when to contact crew or the flight surgeon.
5. **Follow up** – every Watch or higher creates a follow-up: action, reassess time, then an evaluation that shows before and after and says "this shows a change; it cannot show what caused it".
6. **Hand over** – a structured summary for the ground team, stored locally ("ready and queued, not sent").
Rules:
- A **transparent rule-based engine**: explainable, testable, offline. Never presented as clinical AI. Every assessment has a "How Viva decided" list of the exact rule IDs fired (rule catalogue: SCIENCE_MAP.md Part D).
- A risk pattern is **not a diagnosis** or a prediction. Use "pattern worth assessing", "may be related to".
- No language model decides anything. Any conversational layer only rephrases engine output (and in the MVP it is scripted).
- Priority: P0 emergency symptoms and P1 (blood pressure crisis with symptoms; SpO2 at 88% or lower) open the fixed emergency screen and bypass questionnaires. Radiation values never open it; they raise the highest Alert. Details: SCIENCE_MAP.md D1.
- Dangerous combinations matter more than single values: e.g. heart rate above baseline + sleep down + fatigue up + exercise adherence down = "recovery strain pattern".
- **No data is not "normal".** See 6.4.

## 6. Data design
### 6.1 Three kinds of data (always distinguishable in the UI)
| Kind | Source | Tag shown | Use |
|---|---|---|---|
| Simulated | generated by us, realistic | **Simulated Data** | run the interface and scenarios |
| Reference | NASA and medical sources (SCIENCE_MAP.md) | **Sourced Reference**, or **DEMO rule** for our own thresholds | interpret indicators |
| User | typed by the crew member | **Personal Baseline** (own usual) / "Entered by you" | profile and change over time |
NASA's resources released on 13 Nov are reviewed when available, but the design does not depend on them, and they are not assumed to contain crew medical records.

### 6.2 Profiles
- Two fictional crew profiles (Mark Anderson, Sebastian), switchable from the top bar. A **new** profile holds profile information only (name, role, environment, mission day, start date); every health value is empty. The **demo** profile holds pre-loaded simulated data (124 days).
- Demo mission is fictional: "Demo Mars transit mission, Mission Day 124". Do not use real mission names (no "Artemis-III") with fictional crew.
- **Privacy between profiles:** mood, stress, symptom and other private cards are hidden behind "Private. Tap to view." after a profile switch, and are shared (with ground, with the handover) only by explicit consent. Mental-health data stays on the device.

### 6.3 Baseline
- Baseline = the astronaut's own usual value. Source: a pre-mission baseline if provided, otherwise the **median of the first 5 valid, calm readings on different days** (DEMO rule), plus the spread (max minus min).
- Baseline is **frozen** after calibration and changes only by an explicit "Recalibrate baseline" action that writes a log entry with date and reason. Unconfirmed or stale readings are never used.
- Until a baseline exists: "Baseline: not available yet", and only the general reference is used, with that stated.

### 6.4 Empty-data rules (no fake alarms)
- No reading: the indicator shows "No data". No status, no alert, grey body-map zone, no claim by Viva.
- Never show "all steady" if a P0 indicator was not measured today: say "based on the data available".
- The default dashboard (demo profile) uses the steady demo dataset and raises **no new alerts** unless the user enters a reading or starts a scenario.
- Rules DATA-1 to DATA-6 in SCIENCE_MAP.md D3.

### 6.5 Input types
| Input | Used for | Notes |
|---|---|---|
| Keyboard | numeric readings | with validation and units |
| Mouse / touch | body map, symptom chips, quick answers, reaction check | main interaction |
| Camera / photo | **concept**: `<input type="file" accept="image/*" capture>`; shows the image; user types the number and confirms | no OCR, no `getUserMedia` |
| Voice out | Viva speaks via `speechSynthesis` | **off by default**; captions always on |
| Voice in | **not in MVP** (browser speech recognition sends audio to outside servers: breaks the offline and privacy rules). Roadmap only | |
| Device / sensor | **roadmap** ("Connect device" card) | |
| Scheduled questionnaire | mood, stress, fatigue, sleep, symptoms | Viva asks |

### 6.6 Record structure
Each reading stores: indicator id, value, unit, timestamp, source (manual / questionnaire / photo-confirmed / simulated), data-confidence label (Complete / Needs verification / Incomplete / Simulated), measurement context (posture, recent exercise, method), crew id, mission day, environment. User-typed and sensor-fed data are never treated as equally reliable.

### 6.7 Measurement guidance (two levels, no video)
1. **Quick Instructions**: 3-5 short steps with icons.
2. **Visual Guide**: original SVG pictograms in sequence plus optional Viva voice.
Video is roadmap only. Each indicator help card answers: How do I measure? / Why does it matter? / What if it looks abnormal? / Which space hazard affects it? / Source. Wording: VIVA_SCRIPTS.md parts 3 and 4. Always add "Follow your mission medical procedure". Do not ask for an ECG just to know heart rate; ECG and ultrasound are roadmap cards without electrode diagrams.
Body **mass** (not weight): mass-measurement device in orbit or transit; on the Moon or Mars a scale calibrated to local gravity (our reasoning; needs a source).

### 6.8 Indicator build set (from SCIENCE_MAP.md A7)
- **P0 (must work end to end):** resting heart rate, blood pressure (with posture), SpO2, body temperature, body mass, sleep (hours and quality), mood/stress/fatigue, symptoms checklist, exercise minutes, radiation dose (always labelled "Simulated" unless from a dosimeter), link status (simulated).
- **P1:** reaction check (demo, "simplified, not validated"), vision questions, food and fluid intake, headache, feeling connected, motion-sickness scale, dizzy-on-standing, blood glucose (optional, manual entry only; built if time allows, never at the expense of the P0 core; first P1 item to cut).
- **P2 (card or roadmap):** cabin CO2, noise, comfort, crew illness cluster, equipment checklist.
All reference values, DEMO thresholds and rule IDs: SCIENCE_MAP.md Parts C and D. Never present a DEMO value as clinically validated or as a NASA value.

## 7. Conversation: Viva
- A **scripted dialogue manager** driven by engine state, using the lines in VIVA_SCRIPTS.md (IDs, variables). Every sentence Viva says is pre-written; she does not generate text.
- **Voice is off by default.** Viva speaks only after the user turns voice on (Settings or the Guided Demo prompt) or taps **Listen** on a message. Captions always stay on.
- Viva greets by name and mission day, asks the scheduled measurement, explains how, waits for the value, asks context and symptom follow-ups, summarizes, updates the dashboard. Quick-reply chips; tone adapts (calm for Stable, caring for Watch, firm and clear for Alert).
- **Ask Viva and Viva Intelligence (offline, on-device):** suggested question buttons plus a free-text box. A local intent engine (keyword and synonym matching with typo repair, session-only memory for follow-ups such as "and yesterday?") answers from the app's own readings, baseline and rules, with a "Why this answer?" list. A safety layer runs first: emergency phrases go to the Emergency path, and requests for a diagnosis, a drug or a dose get a fixed refusal. No API, no internet, no keys, no language model, and the UI never calls Viva an AI model. Wording: VIVA_SCRIPTS.md part 6B and part 9.
- **Never** say "your blood pressure is high" before a reading exists. With no data: "Let's start with your first health check."

## 8. Emergency Response Mode
Official example: severe chest pain, then the crewmate collapses.
Principles: do not wait for forms; take over the screen (high contrast, big buttons, few words); the lines are **fixed, pre-written text** (VIVA_SCRIPTS.md part 7), never generated; ask a nearby crewmate for help; contact crew medical officer and ground flight surgeon; log the incident; prepare a structured report ("ready and queued, not sent"); always "Follow your mission medical procedure". Every emergency screen is labelled **"Educational simulation, not a medical protocol."**
Triggers: P0 symptoms (chest pain, severe breathing difficulty, loss of consciousness, self-harm statement) and the two P1 values (SCIENCE_MAP.md D1).
Flow for the main scenario: chest pain -> immediate Emergency Mode -> "stop what you are doing" -> call nearest crewmate -> if the crewmate must check responsiveness or breathing, use only steps taken from a cited public first-aid source and mark them with it -> ground link simulation showing delay -> incident log with timestamps -> report.
Rules: no oxygen, drug or medical procedure unless a cited source or a protocol step justifies it; never infer hypoxia from the body picture. Scenario is marked "Illustrative emergency scenario".
Behavioral emergency (self-harm or "not wanting to be here"): skip questionnaires; calm supportive speech; stay with a crewmate; contact the crew medical officer and ground flight surgeon; no diagnosis; same priority as chest pain.

## 9. Engagement: "Mission Wellness"
Elements: daily health check, exercise missions, sleep goals, hydration reminder, weekly streak, personal progress timeline, daily task progress (e.g. 4/5).
Principles: reward consistent and **honest** reporting, never "good numbers"; never punish missed tasks or low days; no pressure to hide symptoms; "Viva learns your normal as you check in". Mission health tasks follow the mission schedule and respect crew time (adaptive monitoring is a stretch goal: do not ask for questionnaires without a reason).

---

## 10. Scope and priorities (honest in the UI)
**P0 – Core (must work end to end):**
1. Dashboard-first entry: the app opens on the dashboard (demo profile, steady data, no alerts); Viva's first message and the Start a Health Check chip in her panel; Guided Demo button and Help (?) button in the top bar; two profiles (new = empty, demo = simulated).
2. Manual entry of the P0 indicators with validation and the measurement-context check.
3. Dashboard with **Monitoring Status** counts and source tags; time-series charts with baseline band.
4. Rule-based engine (SCIENCE_MAP.md Part D) with "How Viva decided".
5. Viva: scripted flow, measurement explanations, Ask Viva (offline).
6. Follow-up loop.
7. **Health Handover** generator.
8. Interactive body map linked to indicators.
9. Guided Demo (three scenarios).
10. Sources/About page.
**P1:** voice output (Listen button, voice off by default); the simulated Blood results screen (Phase 6B); Mission Wellness tasks; emergency scenario fully playable; mission environment selector (Space station / Spacecraft in transit / Lunar base / Mars base); vision/roadmap constellation; P1 indicators.
**P2 / stretch:** adaptive monitoring, advanced cross-hazard insights, timeline polish, printable report, P2 indicators.
**Roadmap (shown, not built):** wearables and device integration; point-of-care blood analysis concept (10A); automatic OCR; validated machine learning; speech input; a language-model chat layer (needs internet, keys and a privacy design); mission-approved protocols; secure transmission to flight surgeons; delay-tolerant sync; 3D anatomy; ECG/ultrasound guidance; peer-awareness alerts; video instructions.
**Vision screen ("constellation"):** stars for features. Bright = working. Pulsing = prototype. Dim = roadmap. Tap shows what it is, how it will work, why it matters, and that it needs development time and funding.
**Cut order if late:** Ground Medical Dashboard (Phase 10) -> decoration and animation -> P2 -> P1 depth -> P1 items; never cut P0 validation, analysis, guidance, handover, guided demo, sources.

### 10A. Added team decisions (13-14 Nov 2026)
**1. Earth-independent Health Handover stays CORE** (already P0, item 7 above): the report is created from app data, stored locally when contact is lost or delayed, and prepared for sending when contact returns. Status wording stays "ready and queued, not sent".

**2. Point-of-Care Blood Analysis Concept: roadmap card ONLY.**
- Shown on the Vision/Roadmap screen as a dim star (VIVA_SCRIPTS.md VIS-01 to VIS-04). Not a required feature. No code beyond the card.
- Idea: in the future a tiny finger-prick blood or saliva sample could be read by a compact point-of-care device on board, for markers such as bone turnover markers, vitamin D, inflammatory markers and glucose.
- Vivonaut does NOT analyse blood or saliva, does not read biomarkers, and does not connect to any device. The research (Marialena's blood-biomarker proposal, 14 Nov) is delivered; the references on the Blood results screen are the ones in that proposal (SCIENCE_MAP.md Part G item 18).
- **Isolated simulated demo (Phase 6B, decided 14 Nov):** one optional **Blood results** screen shows a fictional white-blood-cell fixture for Mark Anderson with the permanent banner "Simulated analyzer. No device is connected. Demo data, not astronaut measurements." It never creates alerts, never changes Monitoring Status counts, never opens the emergency path, can be attached to the local handover only with consent, and can be switched off (ENABLE_BIOMARKER_DEMO). No NASA data is embedded and no biomarker is added to the rules. HemoCue WBC DIFF and rHEALTH ONE are cited only as the research basis, with the limits NASA's own tests had (control solutions and test particles, not astronaut blood).
- The optional glucose indicator (P1) stays a manual entry typed by the user. It is not part of this concept.
- Candidate NASA study names to check on NASA's pages before any citation: Immune Biomarkers, Omics Archive, Altered Immunity. Tempus Pro is a commercial telemedicine device: name it only as an example, never as an endorsement.

**3. Ground Medical Dashboard: OPTIONAL simulated demonstration (PROMPTS.md Phase 10).**
- A read-only simulated view of the ground team reviewing the Health Handover that Vivonaut created: the report, astronaut data, alerts and changes from baseline, and the link state (Live / Delayed / Blackout, taken from Mission Settings).
- No real sending, no server, no real-time communication, no new rules or thresholds. Always labelled "Simulated ground view. No real transmission." (GND-01).
- Built only after Phase 9 is complete and saved, in a copy of the file. It is the first thing cut. If it is not finished and stable, it is not submitted.
- Module name: GROUND_DASHBOARD.

## 11. The three guided-demo scenarios
All data labelled "Simulated Data". Each scenario has captions, a progress strip, Pause / Skip / Replay. Start prompt asks "Play with voice?" (default no).
1. **Routine Monitoring – "A normal day in space":** Viva greets Mark, asks for blood pressure, shows the steps, Mark enters a value, the checks pass, body map and charts update, task progress rises. Proves: monitoring, interaction, usability.
2. **Early Warning – "Something is changing":** resting heart rate drifts above baseline, sleep falls, fatigue rises. A reading triggers "Needs verification"; Viva asks context; the pattern across indicators is shown with "How Viva decided"; a follow-up is created; the evaluation shows the change; the story ends by generating the **Health Handover**. Proves: baseline, trend, measurement intelligence, follow-up, handover.
3. **Emergency – "An emergency onboard":** chest pain, then unresponsive; fixed emergency screen; crew help; ground link with delay; log; report ready and queued. Proves: emergency response, crew support.

## 12. Entry experience, screens and layout
**Entry (dashboard-first, decided 14 Nov):** the app opens directly on the main Dashboard: demo profile Mark Anderson, steady demo data, no alerts, DEMO MODE badge visible. There is no separate welcome screen and no overlay at launch.
- **Viva's panel carries the introduction:** her first message (WEL-01, WEL-02) with the chips **Start a Health Check** and **Ask Viva**.
- **Start a Health Check** (inside Viva's panel): Viva asks which crew profile (Mark Anderson or Sebastian) and opens it as a NEW empty profile (FTE-06, FTE-10, FTE-11). The top-bar profile switcher returns to the demo data.
- **Guided Demo:** a clearly visible button in the top bar, always available. It asks "Play with voice?" before starting (default No).
- **Help panel:** optional and dismissible, opened by a "?" button in the top bar, never opened automatically (FTE-01 to FTE-03, FTE-05, FTE-07, FTE-08, CAR-04, WEL-12).
- Voice stays off by default; the choice is offered at the start of the Guided Demo and in Settings (FTE-09). Empty states and context-aware responses: VIVA_SCRIPTS.md part 1A.
Navigation: Dashboard, Vitals, Trends, Handover/Reports, Challenges, Settings (mission), Vision, Sources/About, plus Emergency access always visible. The top bar also holds the **Guided Demo** button and the **Help (?)** button.
**Dashboard (hero):** top bar (logo, crew member switcher, mission name, Mission Day, link status, UTC clock, DEMO MODE badge, Guided Demo button, Help button) / left: **Monitoring Status** (counts: Stable, Watch, Needs assessment, Alert, No data) and key indicator cards with sparklines and type tags / center: glowing human figure with callouts (Brain, Lungs, Heart, Bones and muscles, Immune; Eyes optional) / right: Viva panel (original robot face, greeting in a speech bubble, chips Start a Health Check and Ask Viva, Listen button) and Alerts card / bottom: trends, mission tasks, emergency card.
Avoid the contradictions of the reference mockup: no "All Systems Nominal" next to an active alert; no Health Index percentage; no "Brain Healthy" or "Immune Good" without measured data; Emergency Mode only when triggered.
**Body map:** clickable; status colors; click opens a plain-language card: current value (or "No data"), What does this mean? What should you do? Linked hazard, Source, and "Illustrative; status reflects linked indicators, not real organ condition".
**Mission Settings:** environment, mission day, available equipment, communication (Live / Delayed / Blackout), schedule. Changing the environment changes gravity note, mass-measurement wording, delay and emphasized hazards (SCIENCE_MAP.md Part E).
**Handover:** "Generate Health Handover" builds the report from app data (HND-1), shows missing and unconfirmed data, and stores it as ready and queued.
Reference mockup image is provided separately (dark space HUD); reinterpret it, do not copy it.

---

## 13. Hard technical rules
1. One self-contained `index.html`: HTML + CSS + vanilla JS inline. Opens by double-click, any device, **truly offline** (test with the network off).
2. NO external CDN, NO API keys, NO server, NO paid services, NO external fonts, NO external images, NO speech recognition. Charts, body map, icons, Viva robot, pictograms = original inline SVG/Canvas.
3. English only.
4. Voice output = `speechSynthesis`; voices vary by device, so test it **early** (Phase 1 and Phase 5), keep captions on, provide mute, voice and rate controls, and show SYS-06 when no voice exists.
5. State in JS + `localStorage` wrapped in try/catch; the app must run if storage fails. Simulated data always labelled.
6. Marked modules (each phase edits only its module): `/* ===== MODULE: NAME ===== */ ... /* ===== END MODULE: NAME ===== */`.
   Modules: CONFIG, DATA_MODEL, VALIDATION (includes the context check), MEASUREMENT_GUIDE, RULES_ENGINE, FOLLOWUP, UI_LAYOUT, ONBOARDING, BODY_MAP, CHARTS, VIVA_ASSISTANT (includes ASK_VIVA and voice), TASKS_GAMIFICATION, EMERGENCY, MISSION_ENV, TIMELINE, HANDOVER_REPORTS, VISION_ROADMAP, GUIDED_DEMO, SOURCES_ABOUT, and the optional GROUND_DASHBOARD (Phase 10).
7. Modules communicate through one shared state and an event bus: reading saved -> Validation + context check -> Rules Engine -> Alerts + Follow-up -> Dashboard / Body Map / Charts -> Viva (caption, optional voice) -> Handover data.
8. Responsive 360 px to 1920 px. `prefers-reduced-motion`. Keyboard accessible. Good contrast. Never color alone (icon + text).
9. Performance: instant load, no heavy loops.
10. Any library used must be open-source and listed. Preferred: none.
11. Viva's lines live in one data object (IDs from VIVA_SCRIPTS.md), not scattered through code.

## 14. Design rules
- Dark deep-space HUD, cyan/blue glow, glass cards, rounded corners, subtle motion.
- Status colors, always with icon and text: Stable = cyan/green, Watch = yellow, Needs assessment = orange, Alert = red; No data = grey. The emergency screen is its own full-screen red mode.
- No NASA logo or insignia and no real-person photos. Original avatar (initials) and original Viva robot. All visuals original.
- Viva expressions: idle, talking, concerned.
- Big readable type in emergencies.

## 15. Medical and scientific safety rules (non-negotiable)
1. Never state a diagnosis. Never claim clinical validity.
2. Every assessment shows "Reference information, not a diagnosis" and, for DEMO rules, "Demo rule. Not clinically validated."
3. **Every threshold needs source, unit and context.** If it has none, label it DEMO and never attribute it to NASA.
4. Body map colors reflect indicators linked to a system, not real organ condition.
5. Emergency steps are fixed, pre-written, sourced or protocol-referenced, and labelled "Educational simulation, not a medical protocol". No oxygen, drug or procedure without a source.
6. Radiation dose is always "Simulated" unless from a dosimeter.
7. General adult reference ranges are not validated for spaceflight; say so.
8. Gamification never rewards hiding symptoms and never punishes illness or low days.
9. Camera does not measure blood pressure, glucose or SpO2. Faces are not used for diagnosis.
10. Mental-health data is private by default; sharing needs consent.
11. Glucose is optional and says why (nutrition and stress; not a core NASA indicator).
12. Do not quote unverified claims listed in SCIENCE_MAP.md F1 and Part G.
13. Never claim that Vivonaut analyses blood or saliva, reads biomarkers, or connects to a real device or to a real ground team. The blood-analysis idea is a roadmap concept; the Ground Medical Dashboard is a simulation and nothing is transmitted.

## 16. Science inputs (complete)
Status: **all five hazards researched; reference ranges done.**
- `SCIENCE_MAP.md` – merged map: hazard -> concern -> indicator -> method -> action -> source -> feasibility; reference ranges with SOURCED / DEMO / BASELINE tags; rule catalogue with IDs and priorities; environment table; honesty rules; open questions; all sources.
- Detail files (keep, with sources): `01_RADIATION_RESEARCH.md`, `02_MICROGRAVITY_RESEARCH.md`, `03_ISOLATION_RESEARCH.md`, `04_DISTANCE_RESEARCH.md`, `05_CLOSED_ENV_RESEARCH.md`, `00_REFERENCE_RANGES.md`.
- `VIVA_SCRIPTS.md` – every line Viva says, with IDs.
Open science tasks (teammate): replace secondary sources with primary NASA or journal pages; confirm the Stage 2 blood-pressure thresholds; verify the two unverified claims (SCIENCE_MAP.md item 17); clinician review of DEMO rules if possible; the Point-of-Care Blood Analysis research was delivered by Marialena on 14 Nov (SCIENCE_MAP.md Part G item 18) and is reflected only as described in section 10A; Completed source verification Medical-701 and the Standard Measures publication, including its linked correction; see SCIENCE_MAP.md Part G item 17 and X1–X3.

## 17. Hackathon rules (official GitHub discussions)
- Official hackathon **Nov 14-15, 2026**, starts **Saturday 9:00 am** in the Team Owner's local time. **Do not start building before then.** Research, planning, team formation, reading resources are allowed.
- **Deadline: Sunday Nov 15, 11:59 pm** Team Owner local time. Use the full time.
- Universal Event: **no live presentation**; only the submission is judged. Only the Team Owner submits.
- Libraries must be open-source. List **all data, resources, tools, code, text and images** used. Copyrighted material needs permission.
- If a new domain is registered, complete the Fortiguard web filter form.
- When unsure, ask the organizers in the GitHub Discussions.
- NASA resources are released Friday Nov 13; review them, but do not depend on them.

## 18. Team workflow
- **One code owner** (the Team Owner) holds `index.html`. Others never edit code.
- Teammates produce **content**: science member (sources, verification), content member (Viva wording review), QA/docs (tests, README, credits, AI-use log).
- Everything funnels into `STATE.md`. Save a numbered copy of `index.html` after every phase.
- If the AI chat hits a limit: wait, or resume in a new chat using STATE.md + latest working file + the RESUME prompt in `PROMPTS.md`.
- **Two Claude accounts (Team Owner and Ailime, who has Claude Pro):** there is always ONE main version of index.html. Whoever stops (limit reached or phase finished) sends the latest `index_vN.html` and the updated `STATE.md` to the other, who continues with the RESUME prompt. Nobody edits the code by hand. If phases 5, 6 and 7 are run in parallel, each person returns only their own modules and the Team Owner merges them into the main file.
- **Presentation slides:** Marialena prepares the slides and shares the first version with the Team Owner for review.
- **Optional Phase 10** (Ground Medical Dashboard) starts only after Phase 9 is saved as `index_final_v9.html`.

## 19. Required test cases (run before submitting)
1. Invalid value (e.g. heart rate 700): rejected with a friendly message.
2. Unusual but possible value: asks to confirm, saved as unconfirmed, cannot raise an alert above Watch.
3. Missing measurements: the app continues and says what is missing; never "all steady".
4. Stale data: asks to re-measure, no alert from it.
5. Gradual rise over days: trend and multi-indicator rule fire; follow-up created.
6. Emergency symptoms before the measurements are finished: the emergency screen opens immediately.
7. Context check: exercise answered "yes" leads to rest and repeat, status unchanged.
8. New profile: all values "No data", no alerts, no body-map colors.
9. Profile switch: private cards hidden.
10. Offline with the network off and no voices available: everything works with captions.
11. localStorage blocked: the app still runs.
12. Handover: generated from real data, shows missing and unconfirmed items, says "ready and queued, not sent".

## 20. Documentation and disclosure (mandatory)
In the app (Sources/About) and in `README.md`:
- "This project was built with assistance from Claude (Anthropic), an AI assistant. Concept, research direction, design decisions, testing and review by Team Vivonaut."
- Sources (from SCIENCE_MAP.md Part H), tools (none external), assets (all original SVG, system fonts), what is simulated, medical disclaimer, limits, roadmap, remote-communities note.
- Keep a simple AI-use log: date, phase, what was generated, and which team member's Claude account ran it.
