# Vivonaut – VIVA_SCRIPTS.md

All the words Viva says and shows: welcome messages, indicator explanations, measurement instructions, routine alerts, warnings, emergency screens and system messages.
Built on SCIENCE_MAP.md (numbers, rule IDs, source codes) and PROJECT_BRIEF.md (persona, safety rules). Version 1.4, 14 Nov 2026 (final record: updated to match the build up to Phase 7; Part 10 lists the wording added during the build). English only.

Status: draft scripts. The wording is ours; every number comes from SCIENCE_MAP.md and keeps its tag (SOURCED, DEMO, BASELINE). A clinician and a behavioral-health specialist should review Parts 6 and 7 before any use beyond the hackathon.

---

## 0. How to use this file

- Each line has an **ID**. The app stores these as one data object in the VIVA_ASSISTANT module, so Viva can pick a line by ID and fill the `{variables}`.
- Every line is shown as **caption text**. **Voice is off by default.** Viva speaks only after the user turns voice on (Settings, or the prompt at the start of the Guided Demo) or presses **Listen** on a message. Captions always stay on. If voice is unavailable, see SYS-06.
- Variables: `{name}` crew member name (demo: Mark, Sebastian), `{day}` mission day, `{value}`, `{unit}`, `{baseline}`, `{pct}`, `{hours}`, `{minutes}`, `{env}` mission environment, `{link}` link state, `{time}`.
- Lines marked **[2 variants]** or **[3 variants]** are rotated so Viva does not repeat herself.

## 1. Voice and style rules for Viva

**Who Viva is:** a health companion that helps astronauts understand their health data and follow approved guidance. Not a doctor, not a therapist.

| Rule | Do | Do not |
|---|---|---|
| Short | Maximum 3 short sentences per message; about 12 words per sentence | Long paragraphs, nested clauses |
| Plain | "your heart rate", "a little high" | Medical jargon without a plain explanation |
| Calm | Steady, warm, same tone in every status | Exclamation marks (except small celebrations), ALL CAPS, alarm language outside Emergency |
| Honest | "may be related to", "I can't be sure" | "you have", "this is caused by", "diagnosis" |
| Personal | Compare with "your usual" (baseline) | "normal" for a personal change; comparing with other crewmates |
| One ask | One clear action per message | Three instructions in one breath |
| Protocol | "Follow your mission medical procedure" on every health instruction | Giving drug, oxygen or treatment advice |
| Respect | Treat the astronaut as trained and capable | Talking down, scolding, punishing missed tasks |
| Privacy | "Stays on this device unless you choose to share" | Sharing mental-health data without consent |
| Demo honesty | Label simulated, demo and DEMO values | Presenting a demo rule as a NASA limit |

**Words Viva never uses:** diagnose / diagnosis (except in "I can't diagnose"), disease names as conclusions, "dangerous" or "critical" without a number and a reason (the phrase "critical tasks" in WRN-11 is the one exception), "you are fine" as a medical statement (use "your numbers look steady").

**Spoken forms** (the code replaces symbols before speaking):

| Written | Spoken |
|---|---|
| SpO2 | S P O two |
| mmHg | millimeters of mercury |
| bpm | beats per minute |
| mSv | millisieverts |
| dBA | decibels |
| CO2 | C O two |
| kg | kilograms |
| °C | degrees Celsius |
| mg/dL | milligrams per deciliter |
| 120/80 | one twenty over eighty |

---

## 1A. First-time experience and interaction flow

What a visitor sees when they open the app with nobody explaining it. Rule for everything below: **Viva never mentions a value she has not been given.** No data means no claim.

### 1A.1 Help panel (optional and dismissible; opened by the "?" button; never opens by itself)
| ID | Text |
|---|---|
| FTE-01 | Title: "Meet Viva." Subtitle: "Your intelligent health companion for space missions." |
| FTE-02 | "Hello, I'm Viva. I help you understand your health readings, notice changes, and follow mission-approved guidance." |
| FTE-03 | "I'm a health companion, not a replacement of your medical team." |

### 1A.2 Entry points (no welcome screen: the app opens directly on the dashboard)
Viva's first message in her panel uses WEL-01 and WEL-02, with the chips "Start a Health Check" and "Ask Viva". The Guided Demo is a button in the top bar.

| ID | Where | Text |
|---|---|---|
| FTE-04 | Top-bar button "Guided Demo" (tooltip) | "Watch three prepared scenarios and see how Viva responds to different health situations." |
| FTE-05 | Help panel, about the default dashboard | "This dashboard opens with demo data. Explore the indicators, charts and Viva. No surprise alerts." |
| FTE-06 | Viva's reply after the chip "Start a Health Check" (chips: crew names) | "Choose a crew profile and begin with your own measurements. Viva analyzes what you insert." |

### 1A.3 Demo explanation and voice choice
| ID | Where | Text |
|---|---|---|
| FTE-07 | Help panel; tooltip on the DEMO MODE badge | "All crew, readings and events in this demo are simulated. Nothing here is real medical data." |
| FTE-08 | Help panel | "Look for the tag on each value: Sourced Reference, Personal Baseline or Simulated Data." |
| FTE-09 | Start of the Guided Demo ("Play with voice?", default No); Settings | "Would you like Viva to speak? Voice is off by default. You can change this any time in Settings." |

### 1A.4 First health check
| ID | Text |
|---|---|
| FTE-10 | "Let's start with your first health check." |
| FTE-11 | "Pick a measurement, follow the short steps and type your result. I'll check it before I interpret it." |
| FTE-12 | After the first save: "I've saved your {indicator} reading. Let's compare it with the reference values available." |

### 1A.5 Empty states (no data)
| ID | Where | Text |
|---|---|---|
| EMP-01 | Dashboard | "No measurements yet. Let's start with your first health check." |
| EMP-02 | Baseline | "Baseline: not available yet. Your usual values appear after five calm measurements." |
| EMP-03 | Chart | "No data yet. Charts appear after your first reading." |
| EMP-04 | Trend | "Trend analysis: waiting more measurements." |
| EMP-05 | Indicator card | "No data. This indicator has not been measured." |
| EMP-06 | Radiation | "Radiation dose: no data. Enter a dosimeter reading, or use the simulated dose." |
| EMP-07 | Handover | "Not enough data for a handover yet." |
| EMP-08 | Viva panel | "I'm ready when you are. What would you like to check first?" |
| EMP-09 | Body map | "Zones change colour when a linked indicator has data. Grey means no data." |

### 1A.6 Context-aware responses
| ID | Situation | Text |
|---|---|---|
| CAR-01 | Reading saved, no baseline yet | "I've saved your {indicator} reading. I can't compare it with your usual yet, so I'm using the general reference." |
| CAR-02 | Reading matches baseline | "Your {indicator} matches your usual. Thank you." |
| CAR-03 | Reading departs from baseline | Start the measurement context check (CTX-01 in 6.9) |
| CAR-04 | Dashboard with demo data (default view; Help panel; when returning to the demo profile) | "You're exploring with demo data. I won't raise alerts unless you enter a reading or choose a scenario." |
| CAR-05 | Profile switched | "You're now viewing {name}'s profile. Private answers stay hidden unless their owner shares them." |

### 1A.7 Voice controls
| ID | Text |
|---|---|
| VOX-01 | Button: "Listen" |
| VOX-02 | Setting: "Voice: Off (default)" |
| VOX-03 | When turned on: "Voice is on. I'll speak new messages. Tap the speaker to stop me." |
| VOX-04 | "Captions always stay on." |
| VOX-05 | Emergency screen: if voice is on, Viva speaks the emergency lines; if off, captions plus a large Listen button. |

---

## 2. Welcome messages

| ID | When | Text |
|---|---|---|
| WEL-01 | First launch, Viva's panel, message 1 | "Hello, {name}. I'm Viva, your health companion for this mission. I help you understand your health data and follow approved guidance." |
| WEL-02 | First launch, Viva's panel, message 2 | "I'm not a doctor, and I never replace your crew medical officer or flight surgeon. When something needs a human intervention, I'll say so clearly." |
| WEL-03 | Help panel; also at the first health check | "Each day I'll ask for a few quick measurements. I compare them with your own usual values, not with other people measurements." |
| WEL-04 | Help panel, privacy; also before the first mood or stress question | "Your mental health answers stay on this device. You decide if and when to share them." |
| WEL-05 | Baseline start | "To learn your usual values, I need five calm measurements on different days. Until then, I use general reference ranges and say so." |
| WEL-06 | Morning, mission day known [3 variants] | (a) "Good morning, {name}. It's mission day {day}. Ready for your morning check?" (b) "Good morning, {name}. Mission day {day}. A few quick measurements first?" (c) "Morning, {name}. Day {day} begins. Let's check in together." |
| WEL-07 | Afternoon | "Good afternoon, {name}. A quick check now keeps your picture up to date." |
| WEL-08 | Evening [2 variants] | (a) "Good evening, {name}. Let's close the day with a short check-in." (b) "Evening, {name}. How did today feel?" |
| WEL-09 | Returning after a gap | "Welcome back, {name}. It has been {hours} hours since your last check. Let's catch up." |
| WEL-10 | Environment selected | "You're on the {env} today. I've adjusted my questions and guidance for it." |
| WEL-11 | Demo mode banner (always visible) | "Demo mode: all data is simulated for crew member Mark Anderson. Not medical advice." |
| WEL-12 | Judge welcome (Help panel) | "Welcome to Vivonaut, built for the NASA Space Apps Challenge 2026. Start the Guided Demo from the top bar, or explore on your own." |
| WEL-13 | Sign-off at end of check | "Thank you, {name}. Your check is saved. I'll remind you at the next scheduled time." |

---

## 3. Indicator explanations (maximum 3 simple sentences)

Shown on each indicator's help card, under "Why does it matter?". Each is followed by a **reference chip** and a **source tag** (not counted as sentences). The reference chip shows the type: SOURCED, DEMO or BASELINE. Only Tier 1 indicators are in the MVP; Tier 2 are marked.
**Build set (what is actually implemented):** P0 = EXP-01, 02, 03, 04, 06, 07, 08, 10, 13, 14, 21. P1 = EXP-05, 09, 11, 12, 15, 16, 17, 18. P2 = EXP-19, 20 (simple card or roadmap). The other lines stay as reference text. This matches SCIENCE_MAP.md, part A7.


| ID | Indicator | Explanation | Reference chip and source |
|---|---|---|---|
| EXP-01 | Resting heart rate | "Your resting heart rate shows how hard your heart works when you are calm. In space, fluid shifts and stress can change it. I compare it with your own usual rate." | General adult reference 60 to 100 beats per minute (SOURCED, R1) |
| EXP-02 | Blood pressure | "Blood pressure is the force of blood against your vessel walls. In weightlessness, fluids move toward your head, so readings can change. Always tell me if you were sitting or lying." | General adult reference about 90/60 to 120/80 (SOURCED, R1, R2) |
| EXP-03 | SpO2 | "SpO2 estimates how much oxygen your blood is carrying. Poor air or breathing problems can lower it. The reading can be off by a few points, so measure again if it looks low." | Normal 95 to 100 percent (SOURCED, R3) |
| EXP-04 | Body temperature | "Body temperature can rise when your body fights an infection. Germs spread easily in a closed cabin. Tell me which method you used, because methods differ." | General adult reference 36.5 to 37.3 degrees Celsius (SOURCED, R1) |
| EXP-05 | Blood glucose (optional) | "Blood glucose is the sugar in your blood, and it changes with food and stress. I ask if you are fasting, because the reference is different. I never give treatment advice." | Fasting 99 mg/dL or below (SOURCED, R4). Optional demo indicator |
| EXP-06 | Body mass | "Body mass shows whether you are eating enough and keeping your muscle. In orbit a mass device is used, because weight is almost zero. I follow your trend over weeks, not one number." | Your own baseline (BASELINE); change rule is DEMO |
| EXP-07 | Sleep | "Sleep lets your body and mind recover. Astronauts often sleep about six hours, less than the planned eight and a half. Under six hours is linked to slower reactions and more stress." | Observed ISS average about 6 hours (SOURCED, I9, I10) |
| EXP-08 | Mood, stress, fatigue | "These quick ratings show how you feel. They are not a test or a score. Long missions can change mood, stress and energy." | Your own baseline (BASELINE) |
| EXP-09 | Feeling connected | "Staying connected to people you care about helps on long missions. This question is inspired by NASA's CONNECT idea, and it is not a medical scale. A low answer is just a signal to reach out." | Your own baseline (BASELINE), I1 |
| EXP-10 | Symptoms | "Symptoms help me see the full picture next to your numbers. Many, like nausea or headache, can have more than one cause. Timing matters, so tell me when it started." | Not a score |
| EXP-11 | Reaction check | "This short tap game shows how alert you are right now. It is a simplified demo, not a NASA test. I compare it only with your own earlier results." | Your own baseline (BASELINE); DEMO, not validated |
| EXP-12 | Vision questions | "Some astronauts notice changes in near vision on long missions. Only a medical exam can find the cause. Tell me about any new or worsening change." | No score (SOURCED context, M17, M18) |
| EXP-13 | Radiation dose | "Radiation dose adds up over a mission. NASA's career limit is 600 millisieverts. In this demo the dose is simulated unless it comes from a dosimeter." | Career limit 600 mSv (SOURCED, S7); tiers are DEMO |
| EXP-14 | Exercise minutes | "Exercise helps protect bones and muscles in space. ISS crews train about two hours a day. I only help you stay on your own plan." | About 600 minutes per week on ISS (SOURCED, M8) as an illustrative target |
| EXP-15 | Motion sickness | "Nausea and dizziness are common in the first days in space and after landing. They usually fade within days. Rate how strong it feels and when it began." | Scale 0 to 10 (SOURCED context, M19) |
| EXP-16 | Dizzy when standing | "After arriving in gravity, many astronauts feel dizzy when they stand. Your blood needs time to adjust. Stand up slowly and tell me if it happens." | SOURCED context (M9, M15) |
| EXP-17 | Food and fluid intake | "Astronauts often eat less than they need in space. Eating enough protects your muscles and bones. Tell me how much of your meal plan you ate." | ISS average about 74 percent of recommended intake (SOURCED, E5) |
| EXP-18 | Headache | "Headaches are common in space and can have several causes. Cabin air, fluid shifts and tiredness can all play a part. Rate it so I can follow the pattern." | Scale 0 to 10 (SOURCED context, E2) |
| EXP-19 | Cabin CO2 (Tier 2) | "CO2 is the gas we breathe out. High levels can make the air stuffy and cause headaches. The station requirement is 3 millimeters of mercury or less." | Requirement 3 mmHg (SOURCED, E2) |
| EXP-20 | Cabin noise (Tier 2) | "Constant noise can harm hearing and sleep. NASA keeps harmful noise below 85 decibels. Crews can stop noticing noise, so measuring helps." | Below 85 dBA (SOURCED, E3) |
| EXP-21 | Link status (simulated) | "This shows how quickly you can reach Earth right now. At Mars distance a reply can take up to about 44 minutes. When contact is slow, I help you now and prepare a report." | Up to about 22 minutes one way (SOURCED, D1, D2) |

---

## 4. Measurement instructions

Format: **Quick Instructions** (3 to 5 short steps with an icon) for simple measures; **Visual Guide** (original SVG pictograms in sequence plus Viva's voice) for steps that benefit from pictures. No video. Every card ends with the same footer line, MEA-00.

| ID | Text |
|---|---|
| MEA-00 | Footer on every card: "Follow your mission medical procedure and the instructions of your device." |
| MEA-01 | Photo option (all numeric cards): "You can take a photo of the device screen to keep with the record. I can't read it, so please type the number you see." |

### 4.1 Resting heart rate (Quick, Tier 1)
| Step | Text | Pictogram |
|---|---|---|
| MEA-HR-1 | "Rest calmly for about five minutes." | person resting |
| MEA-HR-2 | "Find your pulse on the inside of your wrist, or use your device." | hand and wrist |
| MEA-HR-3 | "Count the beats for 30 seconds, then double it. Or count for a full minute." | stopwatch |
| MEA-HR-4 | "Type the number in beats per minute." | keypad |

### 4.2 Blood pressure (Quick, Tier 1)
| Step | Text | Pictogram |
|---|---|---|
| MEA-BP-1 | "Rest for about five minutes, and stay still and quiet." | person resting |
| MEA-BP-2 | "Tell me your position: sitting, lying, or secured in place." | posture icons |
| MEA-BP-3 | "Put the cuff on your bare upper arm, level with your heart, as your device instructs." | arm with cuff |
| MEA-BP-4 | "Start the device and keep your arm relaxed until it finishes." | device |
| MEA-BP-5 | "Type both numbers, the top number first." | keypad |

### 4.3 SpO2 (Quick, Tier 1)
| Step | Text | Pictogram |
|---|---|---|
| MEA-SP-1 | "Rest calmly and warm your hands if they feel cold." | hands |
| MEA-SP-2 | "Remove nail polish or an artificial nail from the finger you will use." | finger |
| MEA-SP-3 | "Clip the sensor on and keep your hand still." | finger clip |
| MEA-SP-4 | "Wait until the number stops changing, then type it." | keypad |

(Nail polish, artificial nails, cold skin and poor circulation can affect the reading, which may be a few points off: R3.)

### 4.4 Body temperature (Quick, Tier 1)
| Step | Text | Pictogram |
|---|---|---|
| MEA-TE-1 | "Wait a few minutes after exercise, a hot drink or a meal." | clock |
| MEA-TE-2 | "Choose your method: mouth, ear or forehead." | method icons |
| MEA-TE-3 | "Measure as your thermometer instructs." | thermometer |
| MEA-TE-4 | "Type the number and confirm the method." | keypad |

### 4.5 Blood glucose (Quick, Tier 1 optional)
| Step | Text | Pictogram |
|---|---|---|
| MEA-GL-1 | "Tell me if you are fasting or if you have eaten." | meal icon |
| MEA-GL-2 | "Wash and dry your hands." | hands |
| MEA-GL-3 | "Use your approved meter and supplies, as your mission procedure says." | meter |
| MEA-GL-4 | "Type the number in milligrams per deciliter." | keypad |

### 4.6 Body mass (Quick, Tier 1; wording depends on environment)
| Step | Text |
|---|---|
| MEA-BM-1 (orbit or transit) | "Use the mass measurement device. Secure yourself as its instructions say." |
| MEA-BM-2 (orbit or transit) | "Stay still until the device finishes. Type your mass in kilograms." |
| MEA-BM-3 (Moon or Mars surface) | "Use a scale set for local gravity. A normal Earth scale would read wrong." (verify: Part G item 7 in SCIENCE_MAP.md) |
| MEA-BM-4 | "Measure at the same time of day, with similar clothing, so the trend is fair." |

### 4.7 Sleep (Tier 1, questionnaire)
| Step | Text |
|---|---|
| MEA-SL-1 | "How many hours did you sleep last night? Count only the time you were asleep." |
| MEA-SL-2 | "How well did you sleep? One is poor, five is very good." |
| MEA-SL-3 | "How sleepy do you feel now? One is wide awake, five is very sleepy." |

### 4.8 Mood, stress, workload, connection (Tier 1, questionnaire)
| Step | Text |
|---|---|
| MEA-MO-1 | "A few quick feelings, one to five. There are no right or wrong answers." |
| MEA-MO-2 | "These answers stay on this device unless you choose to share them." |

### 4.9 Reaction check (Visual, Tier 1 demo)
| Step | Text | Pictogram |
|---|---|---|
| MEA-RC-1 | "Sit comfortably with your finger over the circle." | hand and circle |
| MEA-RC-2 | "When the circle turns green, tap it as fast as you can." | green circle |
| MEA-RC-3 | "Don't tap early. It lasts about 20 seconds." | stopwatch |
| MEA-RC-4 | "This is a simplified demo, compared only with your own results." | label |

### 4.10 Symptoms and vision questions (Tier 1)
| Step | Text |
|---|---|
| MEA-SY-1 | "Tap anything you feel now. You can pick several." |
| MEA-SY-2 | "For each one, tell me when it started." |
| MEA-VI-1 | "Compared with the start of the mission, is your near vision blurrier?" |
| MEA-VI-2 | "Any double vision, flashes or new discomfort in your eyes?" |

### 4.11 Exercise, radiation dose, intake, headache
| Step | Text |
|---|---|
| MEA-EX-1 | "How many minutes did you exercise today? Include all training." |
| MEA-RA-1 | "Read your cumulative dose from your dosimeter and type it in millisieverts." |
| MEA-RA-2 | "No dosimeter in this demo? I'll show a simulated dose and label it Simulated." |
| MEA-FI-1 | "How much of your planned meals and drinks did you have today? Slide from none to all." |
| MEA-HA-1 | "Rate any headache from zero to ten. Zero is none, ten is the worst you can imagine." |
| MEA-CO-1 | "Type the cabin CO2 reading in millimeters of mercury, if your sensor shows it." |
| MEA-NO-1 | "Type the noise level in decibels from your sound meter, if you have one." |

---

## 5. Routine alerts and reminders

All gentle. Missed tasks are never penalized. Honest reporting is always welcomed.

| ID | When | Text |
|---|---|---|
| RTN-01 | Morning vitals due | "{name}, it's time to measure your blood pressure. Sit comfortably and follow the steps on your screen." |
| RTN-02 | Another scheduled vital [3 variants] | (a) "{name}, it's time to check your heart rate." (b) "{name}, a quick SpO2 check now, please." (c) "{name}, it's time to check your blood sugar, if it is on your plan." |
| RTN-03 | Evening check-in | "Time for your evening check-in. It takes about two minutes." |
| RTN-04 | Re-measure after rest (used by VIT-2) | "Let's measure again in {minutes} minutes. Rest until then, and I'll remind you." |
| RTN-05 | Re-measure reminder fires | "{name}, it's time for your repeat measurement. Same position as before, please." |
| RTN-06 | Missed measurement, soft [2 variants] | (a) "No problem, {name}. Whenever you're ready, I'm here." (b) "Your check is still waiting. A minute now keeps your picture complete." |
| RTN-07 | Weekly check-in | "It's your weekly check-in, about ten minutes. Sleep, mood, stress, connection and your team." |
| RTN-08 | Body mass weekly | "It's time for your weekly body mass. Same time of day as last time, please." |
| RTN-09 | Exercise reminder | "You have {minutes} exercise minutes left on your plan this week. A short session today would help." |
| RTN-10 | Next private conference | "Your next private conference is in {days} days. Would you like me to prepare a short summary, only if you choose?" |
| RTN-11 | Baseline progress | "Calibration {n} of 5 is saved. Thank you, {name}." |
| RTN-12 | Baseline complete | "Your usual values are set. From now on I'll compare each reading with them." |
| RTN-13 | Measurement saved | "Saved. Thank you, {name}." |
| RTN-14 | All steady (only if every P0 indicator was measured today) | "All your readings look steady today. Nothing needs your attention." |
| RTN-14b | Some indicators not measured | "Based on the data available today, your readings look steady. {list} not measured yet." |
| RTN-14c | Nothing measured yet | "Nothing measured yet today. Let's start with your first check." |
| RTN-15 | Honest reporting reward | "Thank you for being honest about how you feel. That helps me help you." |
| RTN-16 | Streak (small celebration, allowed one exclamation) | "{n} days of checks in a row! Nice rhythm, {name}." |
| RTN-17 | Low day, no penalty | "Some days are heavier than others. Your streak is safe, and I'm here." |

### CONNECT tip of the day (wellness tip, never treatment)

Label on every tip: "Wellness tip inspired by NASA's CONNECT reminder [I1]". Own words, not NASA's wording.

| ID | Theme | Text |
|---|---|---|
| TIP-01 | Community | "Think about who benefits from your work today. Your mission matters to many people." |
| TIP-02 | Openness | Withheld: not shown in the app until NASA's exact wording of this principle is confirmed. |
| TIP-03 | Networking | "Send a message or plan a call with someone you care about." |
| TIP-04 | Needs | "Keep your basics steady today: movement, a proper meal, your sleep schedule and a little free time." |
| TIP-05 | Expeditionary mindset | "Look after yourself and your crew. Small kindnesses carry far in a small space." |
| TIP-06 | Countermeasures | "Try two minutes of journaling or slow breathing. It can help you step back from stress." |
| TIP-07 | Training and preparation | "Remember the practice you did before launch. You have prepared for this." |

---

## 6. Status messages and warnings

Four statuses: **Stable**, **Watch**, **Needs assessment**, **Alert**. Every message below is followed by the "How Viva decided" button, showing the rule ID, values, type tag and the line "Reference information, not a diagnosis." Buttons are listed in brackets.

### 6.1 Status headers (shown on chips)
| ID | Status | One-line header |
|---|---|---|
| STA-01 | Stable | "Steady. Your readings match your usual." |
| STA-02 | Watch | "Worth watching. Something is changing a little." |
| STA-03 | Needs assessment | "Needs a human look. Please contact your flight surgeon." |
| STA-04 | Alert | "Important. Please act on the next step now." |

### 6.2 Vital signs
| ID | Rule | Status | Text | Buttons |
|---|---|---|---|---|
| WRN-01 | VIT-1 | Watch | "{name}, your resting heart rate is {value}, a little above your usual {baseline}. Please rest and measure again later." | [Remind me] [Why?] |
| WRN-02 | VIT-2 | Watch | "{name}, your blood pressure is a little high. Please sit and rest, then measure again in 15 minutes and record it." | [Start timer] [Why?] |
| WRN-03 | VIT-4 | Watch | "Your top blood pressure number is above your usual on two readings. I'll keep watching, and I suggest you tell your medical officer." | [Add to report] |
| WRN-04 | VIT-5 (below 95) | Watch | "Your SpO2 reads {value}. Let's measure again after warming your hand and removing nail polish." | [Measure again] |
| WRN-05 | VIT-5 (92 or lower, twice) | Needs assessment | "Your SpO2 is {value} on two readings, which is low. Please contact your flight surgeon and tell a crewmate." | [Contact] [Why?] |
| WRN-06 | VIT-6 (37.8 or higher) | Watch | "Your temperature is {value} degrees. Please rest and measure again later." | [Remind me] |
| WRN-07 | VIT-6 (38.0 or higher, or with symptoms) | Needs assessment | "You have a raised temperature and other symptoms. Please tell your crew medical officer, and follow your mission procedure." | [Contact] [Add to report] |
| WRN-08 | VIT-7 (low glucose with symptoms) | Needs assessment | "Your glucose reading is low and you feel unwell. Please follow your mission medical procedure and get a crewmate now." | [Contact] |
| WRN-09 | VIT-8 | Watch | "Your reaction check was slower than your usual, two times in a row. Please rest, and tell me how you slept." | [Log sleep] |

### 6.3 Sleep, mood and team
| ID | Rule | Status | Text | Buttons |
|---|---|---|---|---|
| WRN-10 | ISO-1 | Watch | "You slept under six hours on three of the last five nights. A regular schedule and dim light before sleep may help. How do you feel?" | [Tips] [I feel fine] |
| WRN-11 | ISO-2 | Needs assessment | "Short sleep, more tiredness and slower reactions together. Please avoid critical tasks if you can, ask a crewmate to double-check, and contact your flight surgeon." | [Contact] [Add to report] |
| WRN-12 | ISO-3 | Watch | "You've seemed more tired and stressed lately. Would you like some tips, or to talk to your flight surgeon?" | [Tips] [Talk to someone] |
| WRN-13 | ISO-4 | Watch | "Thanks for telling me about the tension. A calm talk can help, and ground behavioral support is there if you want it. I won't share this without your OK." | [Calm-talk tips] [Ground support] |

### 6.4 Gravity-related
| ID | Rule | Status | Text | Buttons |
|---|---|---|---|---|
| WRN-14 | GRV-1 | Watch | "Your body mass is lower than your usual over several weeks. Let's look at your eating and exercise together." | [See trend] |
| WRN-15 | GRV-2 | Watch | "You're behind on exercise this week. Even a short session helps your bones and muscles." | [Plan a session] |
| WRN-16 | GRV-3 | Needs assessment | "A new change in your vision should be checked by your flight surgeon. I can't judge it from here. Please contact them and write down what you notice." | [Contact] [Add to report] |
| WRN-17 | GRV-4 | Watch | "Please sit or lie down now. Ask a crewmate to stay with you until you feel steady." | [I'm steady] [Need help] |
| WRN-18 | GRV-5 | Stable | "Nausea in the first days is common while your body adapts. I'll keep watching. Tell me if it gets stronger." | [Rate again later] |

### 6.5 Radiation
| ID | Rule | Status | Text | Buttons |
|---|---|---|---|---|
| WRN-19 | RAD-1 (50 to 80%) | Watch | "Your simulated total dose is {pct} percent of the 600 millisievert career limit. This is for planning, not an emergency." | [See dose chart] |
| WRN-20 | RAD-1 (80 to 100%) | Alert | "Your simulated total dose is {pct} percent of the career limit. Please tell your flight surgeon and mission planners." | [Add to report] |
| WRN-21 | RAD-1 (above 100%) | Alert | "Your simulated total dose is above the career limit. This is a planning notice. Please inform your flight surgeon and mission planners." | [Add to report] |
| WRN-22 | SPE alert | Alert | "Solar particle event alert. Move to the storm shelter now and follow your mission protocol." | [I'm in shelter] |
| WRN-23 | RAD-2 (above 150) | Alert | "Your simulated dose from this event is {value} millisieverts. Stay in the shelter and contact the ground." | [Contact] |
| WRN-24 | RAD-3 (two or more symptoms) | Alert | "You reported several symptoms after the solar alert. Rest in the shelter, write down times, and contact your flight surgeon." | [Contact] [Log times] |
| WRN-25 | RAD-4 | Stable | "I've logged that symptom. One symptom alone is not a sign of radiation. I'll keep watching." | [OK] |

### 6.6 Distance and closed environment
| ID | Rule | Status | Text | Buttons |
|---|---|---|---|---|
| WRN-26 | DST-1 Live | per status | "Contact is live. For any Watch or higher status, I suggest you talk to your flight surgeon now." | [Contact] |
| WRN-27 | DST-1 Delayed | per status | "Contact is delayed, about {minutes} minutes each way. I'll guide you now and send your report. A reply may take up to about 44 minutes round trip." | [Send report] |
| WRN-28 | DST-1 Blackout | per status | "Contact is blacked out. I'm in autonomy mode. Please confirm with your crew medical officer, and I'll queue your report for Earth." | [Queue report] |
| WRN-29 | ENV-1 | Watch | "Cabin CO2 is above the station requirement. Please check ventilation and report it to your crew." | [Report] |
| WRN-30 | ENV-2 | Watch | "Headaches together with high cabin CO2. I can't say what causes them. Please check the air and rate your headache again later." | [Report] [Rate again] |
| WRN-31 | ENV-3 | Watch | "Noise is above 85 decibels. Please report it, and move away from the source if you can." | [Report] |
| WRN-32 | ENV-4 | Watch | "You've slept poorly for three nights, and your sleep area is noisy. It may help to report the noise." | [Report] |
| WRN-33 | ENV-5 | Watch | "You've eaten less than planned for three days. This is common in space, and it matters for your muscles and bones. Is something making it hard?" | [Tell me why] [Meal tips] |
| WRN-34 | ENV-6 | Watch | "Two crew members reported the same symptoms. Please share this with your crew medical officer." | [Share] |

### 6.7 Data quality and system messages
| ID | Situation | Text |
|---|---|---|
| SYS-01 | Value outside plausible limit | "That number looks unusual: {value}. Did you mean it? Please check and re-enter." |
| SYS-02 | Unusual value, confirmed | "Thank you. I've saved {value}, marked as unconfirmed." |
| SYS-03 | Stale reading | "This reading is {hours} hours old. I won't raise an alert from it. Please measure again." |
| SYS-04 | Missing measurements | "I'm missing {list}. I'll use what I have and tell you what I can't judge." |
| SYS-05 | Systolic lower than diastolic | "The top number should be higher than the bottom number. Please check both." |
| SYS-06 | Voice unavailable | "Voice is unavailable on this device. I'll show captions instead." |
| SYS-07 | Offline | "You're offline. Everything works on this device, and nothing is lost." |
| SYS-08 | Recalibrate confirmation | "This will reset your usual values and write a note in your log. Why are you recalibrating?" |
| SYS-09 | Share with ground | "You're choosing to share this with the ground team. You can stop sharing any time. Continue?" |
| SYS-10 | Report queued | "Your report is queued for Earth. It's stored on this device." |
| SYS-11 | Report sent (simulated) | "Demo only: this report is shown as sent. In a real mission it would go at the next contact." |
| SYS-12 | Photo saved | "Photo saved with this record. Please type the number you see." |
| SYS-13 | Disclaimer footer (every result) | "Reference information, not a diagnosis." |
| SYS-14 | Disclaimer for demo rules | "Demo rule. Not clinically validated." |

### 6.8 "How Viva decided" template
"Rule {rule_id}. I used {values}. Your usual is {baseline}. The reference is {reference} ({type}, source {source}). This is reference information, not a diagnosis."

### 6.9 Measurement context check ("Needs verification")

Applies first to blood pressure, heart rate, SpO2 and temperature (SCIENCE_MAP.md, CTX rules). Data Confidence means the quality and completeness of the measurement. It is **not** the chance that someone is ill.

| ID | Moment | Text | Chips |
|---|---|---|---|
| CTX-01 | Reading departs from baseline | "I noticed this {indicator} reading is {higher or lower} than your usual. Before I interpret it, I need to check the measurement context." | |
| CTX-02 | Question 1 | "Did you exercise in the last 30 minutes?" | [Yes] [No] |
| CTX-03 | Question 2 | "Were you sitting, lying down, or secured in place?" | [Sitting] [Lying] [Secured] |
| CTX-04 | Question 3 | "Did you follow the steps and use the device as instructed?" | [Yes] [Not sure] |
| CTX-05 | Question 4 | "Is this your first reading like this, or has it happened before?" | [First] [Repeated] |
| CTX-06 | Question 5 | "Do you feel any symptoms now, like chest pain, dizziness or breathlessness?" | [None] [Yes] |
| CTX-07 | Context explains it | "Thanks. Exercise can change this reading, so please rest and measure again in {minutes} minutes." | [Start timer] |
| CTX-08 | Repeat confirms change | "The change is still there. I'll mark it as Watch and add it to your report." | |
| CTX-09 | Technique doubtful | "Let's repeat the measurement with the steps on screen." | [Show steps] |
| CTX-10 | "Why measure again?" | "A single reading can be affected by posture, activity, or measurement technique. Repeating it helps us check whether the change persists." | |

Data Confidence labels shown on a reading: **Complete**, **Needs verification**, **Incomplete**, **Simulated**.

### 6.10 Follow-up loop (Detect, Explain, Act, Reassess, Evaluate)

| ID | Stage | Text |
|---|---|---|
| FUP-01 | Act | "Here's a next step: {task}. I'll check back {when}." |
| FUP-02 | Reassess | "It's time to check back on your {indicator}. Let's measure again." |
| FUP-03 | Evaluate, improved | "Since the alert, your {indicator} moved from {before} to {after}. This shows a change. It cannot show what caused it." |
| FUP-04 | Evaluate, unchanged | "Your {indicator} is still {value}. I'll keep watching and add this to your report." |
| FUP-05 | Evaluate, worse | "Your {indicator} has moved further from your usual. Please contact your flight surgeon. I'll add this to your report." |
| FUP-06 | Close | "Thanks. I've closed this follow-up and kept it in your timeline." |

### 6.11 Health handover (report for the ground team)

| ID | Text |
|---|---|
| HND-01 | Button: "Generate Health Handover" |
| HND-02 | Title: "Health Handover, prepared on this device" |
| HND-03 | "This summary is for your crew medical officer and the ground flight surgeon. It uses only data recorded in this app." |
| HND-04 | Section labels: Current indicators / Changes from your usual / Alerts so far / Measurements repeated / Actions tried / Symptoms reported / Missing or unconfirmed data / Questions for the ground team |
| HND-05 | "Not measured: {list}. Unconfirmed: {list}." |
| HND-06 | "Your handover is ready and queued. It has not been sent." |
| HND-07 | "Demo only: in a real mission this would be sent at the next contact." |
| HND-08 | "Prepared by Vivonaut. Reference information, not a diagnosis. Demo rules are not clinically validated." |
| HND-09 | "Your mood and stress answers are private. Include them in this handover?" [Include] [Leave out] |

### 6.12 Privacy
| ID | Text |
|---|---|
| PRV-01 | Hidden card: "Private. Tap to view." |
| PRV-02 | "You switched profile. Private answers stay hidden unless their owner shares them." |
| PRV-03 | Sharing: see SYS-09 |

---

## 6B. Ask Viva (offline questions)

Ask Viva works offline with prepared questions and local keyword matching. It answers from this app's rules and science notes, not from the internet or a language model. Voice input is roadmap.

| ID | Question button | Answer (max 3 sentences) |
|---|---|---|
| ASK-00 | Label under the box | "Ask Viva uses keyword and rule matching on this device, with your stored readings. It uses no language model and no internet." |
| ASK-01 | "Why do I need to measure again?" | "A single reading can be affected by posture, activity, or measurement technique. Repeating it helps us check whether the change persists." |
| ASK-02 | "Why is my status Watch?" | "I use the rules in 'How Viva decided'. It shows the values and the rule behind this status." |
| ASK-03 | "What is my baseline?" | "Your baseline is your own usual value. It is set from your first five calm readings and stays fixed unless you recalibrate." |
| ASK-04 | "Is this a diagnosis?" | "No. I show reference information and patterns worth checking. A person from your medical team makes any diagnosis." |
| ASK-05 | "What do the tags mean?" | "Sourced Reference comes from a named source. Personal Baseline is your own usual. Simulated Data is made up for this demo." |
| ASK-06 | "Who can see my answers?" | "Your mental health answers stay on this device. They are shared only if you choose." |
| ASK-07 | "What if contact with Earth is lost?" | "I keep recording and applying the rules on this device. I prepare a handover for when contact returns." |
| ASK-08 | "What works without internet?" | "Measurements, checks, alerts, reports and captions all run on this device. Voice depends on what your device provides." |
| ASK-09 | "What is Demo mode?" | "All crew, readings and events in this demo are simulated. Nothing here is real medical data." |
| ASK-10 | "I feel unwell" | "Tell me what you feel. Tap the symptoms that apply." (opens the symptom chips; emergency symptoms go to Emergency mode) |
| ASK-11 | Retired in Phase 6C | Replaced by INT-03 (see Part 10): a polite fallback with example buttons. |

---

## 7. Emergency mode (fixed, pre-written, never generated)

Every emergency screen carries the label: **"Educational simulation, not a medical protocol."** No drug, oxygen or procedure is ever named. First lines are very short, because people woken suddenly think slowly (sleep inertia, I8). Viva's voice is calm and slower.

### 7.1 Physical emergency (chest pain, severe breathing difficulty, loss of consciousness; also P1 values)
| ID | Text | Screen element |
|---|---|---|
| EMG-01 | "{name}, stop what you are doing." | Large banner |
| EMG-02 | "Call the nearest crewmate now." | Button: Call crewmate |
| EMG-03 | "Stay still and stay with them." | Icon |
| EMG-04 | "Contact your crew medical officer and the ground flight surgeon." | Button: Contact |
| EMG-05 | "Follow your mission medical procedure." | Static line |
| EMG-06 | "I'm preparing a report with your readings." | Progress |
| EMG-07 | "Educational simulation, not a medical protocol." | Footer, always visible |

### 7.2 If the person asking for help is the crewmate (demo scenario)
| ID | Text |
|---|---|
| EMG-08 | "{crewmate}, {name} needs help. Please go to them now." |
| EMG-09 | "Stay with them and call the crew medical officer." |
| EMG-10 | "I'll keep recording. Tell me what you see." |

### 7.3 Behavioral emergency (self-harm or "not wanting to be here")
Skips all questionnaires. Warm, slow, short. Does not diagnose, does not argue, does not say the feeling makes sense.

| ID | Text | Screen element |
|---|---|---|
| EMG-11 | "I'm glad you told me, {name}. You don't have to carry this alone." | Soft banner |
| EMG-12 | "Please stay with a crewmate now. I'd like you not to be alone." | Button: Call crewmate |
| EMG-13 | "Contact your crew medical officer and the ground flight surgeon now." | Button: Contact |
| EMG-14 | "I'm preparing an urgent message. You choose what it says." | Button: Review message |
| EMG-15 | "I'm here with you. The next step is a person." | Static line |

### 7.4 Resolution
| ID | Text |
|---|---|
| EMG-16 | "Thank you, {name}. Your report is ready and queued. It has not been sent." |
| EMG-17 | "When you're ready, we can go back to your check. There's no hurry." |

---

## 8. Guided demo narration (three scenarios)

Short intro and outro for each scenario. Spoken by Viva or shown as a caption banner.

| ID | Scenario | Text |
|---|---|---|
| DEM-01 | Intro: Routine | "Scenario one: a routine day for Mark Anderson. Watch how Viva asks, checks and explains." |
| DEM-02 | Outro: Routine | "All readings were steady. Viva compared each one with Mark's own usual values." |
| DEM-03 | Intro: Early Warning | "Scenario two: something is changing. Mark's resting heart rate drifts up, his sleep drops and fatigue rises." |
| DEM-04 | Outro: Early Warning | "No single number looked alarming. Viva noticed the pattern across indicators, and showed why." |
| DEM-05 | Intro: Emergency | "Scenario three: an emergency. Viva shifts to short, calm steps, and asks Mark to call a crewmate." |
| DEM-06 | Outro: Emergency | "This is an educational simulation, not a medical protocol. Real emergencies follow mission procedures." |
| DEM-07 | End of demo, roadmap | "These are the ideas we built. Wearables, ECG and a link to Earth are part of our future roadmap." |

---

## 8B. Vision cards and optional ground view

### Vision/Roadmap card: Point-of-Care Blood Analysis (concept)

| ID | Where | Text |
|---|---|---|
| VIS-01 | Card title | "Point-of-Care Blood Analysis (concept)" |
| VIS-02 | Card text | "In the future, a tiny blood or saliva sample could be read by a compact medical device on board. It could look at markers linked to bones, vitamin D, inflammation and glucose. This is an idea for the future. Vivonaut does not analyse blood today." |
| VIS-03 | Card status | "Concept. Not built. It would need a certified device, scientific validation and funding." |
| VIS-04 | Why it matters | "Far from Earth, there is no hospital lab. Reading a small sample on board could help the crew and flight surgeons notice changes earlier." |

### Ground Medical Dashboard (optional, Phase 10, simulation only)

| ID | Where | Text |
|---|---|---|
| GND-01 | Label, always visible | "Simulated ground view. No real transmission." |
| GND-02 | Link Live | "Link: Live. The report appears on the ground screen at once (simulation)." |
| GND-03 | Link Delayed | "Link: Delayed. The report will arrive in about {minutes} minutes (simulation)." |
| GND-04 | Link Blackout | "Link: Blackout. The report stays ready and queued, waiting for contact." |
| GND-05 | Received (simulated) | "Demo only: the ground team is shown receiving the report." |
| GND-06 | Private data note | "Private wellbeing answers are shown here only if the crew member agreed to share them." |

---

## 9. Pre-submission checks for this file

1. Every number in this file matches SCIENCE_MAP.md (ranges, limits, rule thresholds).
2. Every explanation in Part 3 has at most 3 sentences (checked by script on 10 Nov).
3. No line gives a drug, oxygen or procedure.
4. No line says "you have" a condition, or presents a DEMO value as a NASA limit.
5. Voice is off by default; no line starts speaking by itself (VOX-02).
6. No line says a report was "sent" unless it is explicitly the simulated demo send (SYS-11, HND-07).
7. No line mentions a value, a status or a trend for an indicator that has no data (Part 1A rule, DATA-1 in SCIENCE_MAP.md).
8. The CONNECT tip TIP-02 ("Openness") stays hidden in the app until NASA's exact wording is confirmed.
9. Body-mass wording for the Moon and Mars (MEA-BM-3) needs a source.
10. The emergency screens (Part 7) and the behavioral-emergency lines should be reviewed by a clinician or behavioral-health specialist.
11. VIS-01 to VIS-04: no line claims that Vivonaut analyses blood or reads a device.
12. GND-01 to GND-06: nothing says a report was "sent"; only GND-05 may say "receiving", and it is labelled demo.

---

## 10. Final wording used in the build (generated from index_v7.html)

The application stores every line in one data object. The table lists each line ID that appears in the final build and is not in Parts 1 to 8B above (new lines from Phases 5 to 7: Health Handover, Emergency Center, incident log, Blood results BIO-xx, Viva Intelligence INT-xx, guided demo, and wording changes). Where an ID appears in both places, the build wording is the final one. `{variables}` are filled by the app.

| ID | Text |
|---|---|
| ASK-01q | Why do I need to measure again? |
| ASK-02n | Nothing is at Watch or higher right now. |
| ASK-02q | Why is my status Watch? |
| ASK-02w | Right now, {title} is at {status}, from rule {rule}. |
| ASK-03q | What is my baseline? |
| ASK-04q | Is this a diagnosis? |
| ASK-05q | What do the tags mean? |
| ASK-06q | Who can see my answers? |
| ASK-07q | What if contact with Earth is lost? |
| ASK-08q | What works without internet? |
| ASK-09q | What is Demo mode? |
| ASK-10q | I feel unwell |
| BIO-02 | This demonstration uses fictional results. No blood analyzer is connected. |
| BIO-03 | This result describes the number of white blood cells in a blood sample. It does not tell us the cause of a change on its own. |
| BIO-04 | The differential separates white blood cells into types. A cell count does not show every aspect of immune function. |
| BIO-05 | There is no result available for this sample. I will leave it marked as missing. |
| BIO-07 | I can add the result, its source and any missing information to the local handover. |
| BIO-08 | A future version could receive results from a validated portable blood analyzer. Device integration is not implemented. |
| CTX-01b | I noticed this {indicator} reading is {dir} than the general reference. I don't have your usual yet, so I need to check the measurement context. |
| CTX-06b | Which one is closest? Tap it and I'll log it. |
| CTX-08a | The change is still there. I've kept both readings, and I'll apply my rules to it now. |
| CTX-11 | Thanks. Your answers look normal, so I've saved the reading as Complete. |
| CTX-12 | Thanks for telling me. I've logged that with this reading. Please follow your mission medical procedure. |
| CTX-13 | I've saved the reading as Needs verification. It won't change any status until we repeat it. |
| DEM-S1a | Viva greets Mark and asks for a blood pressure reading. |
| DEM-S1b | The guide shows the steps. Mark measures and types his result. |
| DEM-S1c | Viva checks the reading against Mark's own usual values. It matches, so it is saved. |
| DEM-S1d | The dashboard updates from the new reading. |
| DEM-S2a | The dashboard shows each status. Every status can explain itself in How Viva decided. |
| DEM-S2b | A new heart rate reading is higher than Mark's usual. Viva checks the measurement context first. |
| DEM-S2c | Viva asks about exercise, position, technique and symptoms. The demo answers for Mark. |
| DEM-S2d | Viva has opened follow-ups, so she can check back on each change. |
| DEM-S2e | Later, Mark measures again. The follow-up compares it with the reading at the time of the alert. |
| DEM-S2f | Viva builds the Health Handover from the recorded data. It is ready and queued, not sent. |
| DEM-S3a | Mark reports chest pain. Viva opens the fixed emergency screen. |
| DEM-S3b | Mark then becomes unresponsive. Viva asks the crewmate to go to him and stay. |
| DEM-S3c | The link to Earth is simulated and delayed. Viva logs each step. |
| DEM-S3d | The report is ready and queued. It has not been sent. |
| DEM-T1 | Routine monitoring: a normal day in space |
| DEM-T2 | Early warning: something is changing |
| DEM-T3 | Emergency: an emergency onboard |
| DEM-end | Demo finished. The app is back to your own data, exactly as it was. |
| DLG-01 | Next: your {indicator}. |
| EMG-L1 | Chest pain, breathing or fainting |
| EMG-SC | Illustrative emergency scenario |
| FTE-01b | Your intelligent health companion for space missions. |
| FTE-09t | Play with voice? |
| FUP-07 | Your {indicator} is {value} now. This shows a change. It cannot show what caused it. I'll keep watching. |
| HND-QA | Is any further action needed for: {title}? |
| HND-QM | Should {list} be measured before the next contact? |
| HND-QN | No open questions from the data recorded in this app. |
| HND-QS | Please review the symptoms listed in this handover. |
| HND-QU | Should {list} be measured again before the next contact? |
| HND-S1 | Current indicators |
| HND-S5 | Actions tried |
| HND-10 | Private answers are hidden on this screen, so this handover leaves them out. Tap the private card first if you want to choose. |
| HND-11 | Shared by your choice |
| HND-12 | No usual values to compare yet, so only the general reference applies. |
| HND-13 | No handover yet. Generate one when you are ready. |
| HND-14 | None recorded. |
| HND-15 | Urgent contact requested by {name}. |
| HND-16 | Demo only: this is a simulated send. Nothing left this device. |
| INC-01 | Emergency screen opened. |
| INC-01a | Emergency screen opened: {label}. |
| INC-02 | Nearest crewmate called (simulated). |
| INC-03 | Contact started with the crew medical officer and the ground flight surgeon (simulated). |
| INC-04 | Link is live (simulation). Contact can start at once. |
| INC-05 | Link is delayed (simulation). A reply could take about {minutes} minutes each way. |
| INC-06 | Link is blacked out (simulation). Your report waits, ready and queued. |
| INC-07 | Report prepared and queued on this device. It has not been sent. |
| INC-08 | Emergency screen closed. |
| INC-09 | Urgent message reviewed by the crew member. |
| INT-f1 | What does that mean? |
| INT-f2 | Compare with my baseline |
| INT-f3 | Show the trend |
| INT-f4 | And yesterday? |
| INT-f5 | Compare with the reference range |
| INT-f6 | Open Handover |
| INT-f7 | Open Blood results |
| INT-f8 | Open Emergency Center |
| INT-f9 | Something else |
| INT-h1 | What was my last heart rate? |
| INT-h2 | How is my blood pressure? |
| INT-h3 | How did I sleep? |
| INT-h4 | What is my status? |
| INT-h5 | Prepare a handover |
| INT-h6 | When is my next check-in? |
| INT-ph | Ask about your readings |
| INT-sub | Context-aware assistant. Runs on this device. |
| INT-w0 | Why this answer? |
| INT-w1 | Reading used: {what}, {value}, {when}, {cls}. |
| INT-w2 | Baseline used: {base} (frozen). |
| INT-w3 | Reference used: {range} ({tag}, source {src}). |
| INT-w4 | Method: keyword and rule matching on this device. No language model and no internet. |
| INT-w5 | No {what} readings were available to use. |
| INT-w6 | Valid readings used: {n} of {what}, from {from} to {to}. |
| INT-w7 | Data used: the simulated blood results loaded on this device. No device is connected. |
| INT-w8 | Reading used: {what} from {when}, {value}. |
| INT-w9 | No baseline was used. |
| INT-01 | Hello, {name}. Ask me about your readings, check-ins, reminders or handover. |
| INT-02 | You're welcome. |
| INT-03 | I can help with your health readings, check-ins, reminders and handover. Try one of these: |
| INT-04 | I have no {what} readings stored yet, so I can't answer that from your data. You can add one in a check-in. |
| INT-05 | I can't diagnose or recommend treatment. I can show how your readings changed and help prepare a handover for the medical team. |
| INT-06 | I'm not sure which one you mean. Did you mean one of these? |
| INT-07 | Which reading do you mean? Pick one, or ask again with its name. |
| INT-08 | Your last {what} reading was {value}, {age} ago, {rel}. |
| INT-08m | Your last {what} reading was {value}, {age} ago. |
| INT-08n | Your last {what} reading was {value}, {age} ago. I have no frozen baseline for it yet, so I can't show a change. |
| INT-09 | This shows a change. |
| INT-09b | This is within the usual spread of your baseline. |
| INT-10 | It cannot show what caused it. |
| INT-10b | A single reading cannot show more than that. |
| INT-11 | This reading is {cls}, so I treat it with caution. Measuring again would help. |
| INT-12 | Your last {what} reading was {value}, {rel}. The reference range is {range} ({tag}). |
| INT-12n | Your last {what} reading was {value}, {rel}. This app has no sourced reference range for it, so your own baseline is the comparison ({tag}). |
| INT-13 | Your last {n} valid {what} readings moved from {first} to {last}, {chg}. It cannot show what caused it. |
| INT-13n | I have {n} valid {what} reading(s), which is too few to show a trend. |
| INT-13s | Your last {n} valid {what} readings stayed within the usual spread, from {first} to {last}. It cannot show what caused it. |
| INT-14 | On {when} your {what} reading was {value}, {rel}. Your latest reading is {latest}, {age} ago. |
| INT-14n | I have no {what} reading from yesterday. Your last one was {latest}, {age} ago. |
| INT-15 | Your {what} baseline is {base}, set from calm readings and kept fixed. Your last reading was {value}, {rel}. |
| INT-15c | Your {what} baseline is still being set. It is fixed after enough calm readings. |
| INT-16 | Mood, stress and fatigue ratings are private. I only show them after you choose to view them. |
| INT-17 | I can't tell you why a reading changed. I can show which readings and baseline I used. |
| INT-18 | I don't track food or water in this app. Body mass is the closest reading I have. |
| INT-19 | Cabin air is not tracked here. I only record your own health readings. |
| INT-19c | Your latest cabin {what} was {value}, {age} ago. {ref}. |
| INT-20 | Your next check-in is the {label} at {when}. Reminders are {state}. |
| INT-21 | I can help prepare a handover for the medical team. It uses only data recorded in this app, and nothing is sent unless you choose. |
| INT-22 | No simulated blood results are loaded yet. You can load the next sample on the Blood results screen. |
| INT-23 | {n} of {total} simulated samples are loaded; the latest white blood cell count is {value}. |
| INT-23m | {n} of {total} simulated samples are loaded; the latest white blood cell result is marked {status}. |
| INT-25 | Thanks for telling me. Here is what your records show. |
| RTN-02a | {name}, it's time to check your heart rate. |
| RTN-02b | {name}, a quick SpO2 check now, please. |
| RTN-06a | No problem, {name}. Whenever you're ready, I'm here. |
| RTN-06b | Your check is still waiting. A minute now keeps your picture complete. |
| RTN-14p | Based on the data you can see, your readings look steady. A private indicator is hidden. |
| STA-05 | Needs verification. I'm waiting for a repeat measurement. |
| SYS-01b | I need a number here. Please check it and type it again. |
| SYS-01c | No problem. Please check the number and type it again. |
| SYS-01d | Please choose {what} so I can check the reading in context. |
| SYS-02b | An unconfirmed reading can't raise a status above Watch by itself. Measuring again will help. |
| SYS-04b | Every core measurement has a recent reading. |
| SYS-08b | Your usual values were reset. I'll set new ones from your next five calm readings. |
| SYS-15 | Storage is unavailable in this browser. The app still works, but nothing will be saved after you close it. |
| SYS-16 | Demo data loaded: {set}. Every value is simulated. |
| TIP-00 | Wellness tip of the day |
| TIP-label | Wellness tip inspired by NASA's CONNECT reminder [I1] |
| VOX-02on | Voice: On |
| VOX-06 | Viva's voice is your browser's built-in text-to-speech (speechSynthesis). It is not a custom AI-generated voice, and it sounds different on each device. |
| WEL-06a | Good morning, {name}. It's mission day {day}. Ready for your morning check? |
| WEL-06b | Good morning, {name}. Mission day {day}. A few quick measurements first? |
| WEL-06c | Morning, {name}. Day {day} begins. Let's check in together. |
| WEL-08a | Good evening, {name}. Let's close the day with a short check-in. |
| WEL-08b | Evening, {name}. How did today feel? |
| WEL-11b | Demo mode: values you type stay on this device. Nothing here is real medical data. Not medical advice. |
| WRN-D2 | Your {indicator} has been outside the general reference on two readings. I don't have your usual yet, so I'm using the general reference only. |
| WRN-EM1 | {name}, you reported {symptom}. The emergency steps are open. Please call the nearest crewmate now. |
| WRN-EM2 | I'm glad you told me, {name}. Please stay with a crewmate, and contact your crew medical officer and the ground flight surgeon now. |
| WRN-02b | Your blood pressure is very high. Please sit, rest, and measure again after at least a minute. If it is still this high, contact your flight surgeon promptly. |
| WRN-02s | Your blood pressure is above the reference and you feel unwell. Please sit and rest, tell a crewmate, and contact your flight surgeon. |
| WRN-03e | Your blood pressure is very high and you reported symptoms. The emergency steps are open. Please call the nearest crewmate now. |
| WRN-05b | Your SpO2 is {value}, which is very low. The emergency steps are open. Please stay with a crewmate. |
| WRN-07b | Your temperature is {value} degrees, which is raised. Please tell your crew medical officer, and follow your mission procedure. |
| WRN-10b | You slept about {hours} hours, well below your usual {baseline}. A regular schedule and dim light before sleep may help. How do you feel? |
| WRN-14b | Your body mass is {pct} percent below your usual. Let's look at your eating and exercise together. |
| WRN-23u | Your simulated dose from this event is {value} millisieverts. Stay in the shelter and contact the ground now. |
| WRN-23w | Your simulated dose from this event is {value} millisieverts. Please stay alert and follow your mission protocol. |
| WRN-24u | You reported vomiting and another symptom after the solar alert. Please contact your flight surgeon now, and rest in the shelter. |
| WRN-35 | Your resting heart rate is up, you're sleeping less and you feel more tired. No single number is alarming, but together they look like a recovery strain pattern. Please rest, and tell me how you feel. |
| WRN-35s | Your resting heart rate is up, you're sleeping less and you feel more tired, and you reported symptoms. Please contact your flight surgeon and tell a crewmate. |
