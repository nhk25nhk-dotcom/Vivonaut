# Vivonaut — Resources, Sources and Tools

**Project:** Vivonaut – Your Intelligent Health Companion in Space
**Challenge:** Create Health Monitoring Software for Astronauts on Space Missions
**Event:** NASA Space Apps Challenge 2026
**Version:** 15 November 2026 (final record, build up to Phase 10A)

This file lists everything the team used to build Vivonaut: AI tools, scientific and institutional sources, and technical resources. Sources are grouped by purpose. Codes (S, M, I, D, E, R, X) are the codes shown on the application's Sources page.

---

## 1. AI tools used

| Tool | Provider | How it was used |
|---|---|---|
| Claude (including Claude Sonnet 5.5) | Anthropic | Development assistant under team direction, used in two ways: (1) build phases, run by a team member in a Claude Project: planning, writing and testing the application code (single `index.html`); (2) project support: drafting and merging the project documents (project brief, build prompts, science map, Viva dialogue scripts, submission checklist), independent browser tests of each build, and review of scientific wording and safety rules. The full phase-by-phase record is in `AI_USE_LOG.md`. |
| ChatGPT | OpenAI | Generated the reference UI mockup image (dashboard concept) used only as a visual guide for the interface design. The image is not part of the application. Any use of it in the presentation carries a visible AI-generated watermark. |
| Gemini | Google | Used occasionally for light consultation (quick questions and idea checks). No content of the application, its code, its text or its images was generated with it. |

AI-generated output was reviewed by the team. Concept, research direction, design decisions, testing and review are by Team Vivonaut. Scientific statements in the application are tied to the sources below; thresholds that are not sourced are labelled DEMO in the application. No AI service is used while the application runs: it works offline with a rule-based engine and prepared text.

---

## 2. Scientific and institutional sources used by the application

### 2.1 Radiation (S)

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

### 2.2 Gravity fields, bone, muscle, cardiovascular, vision, vestibular (M)

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

### 2.3 Isolation, sleep, behavioral health (I)

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

### 2.4 Distance from Earth, communication, medical operations (D)

- D1 Communication Delays, Disruptions, and Blackouts for Crewed Mars Missions (ASCEND, NASA NTRS 20220013418). https://ntrs.nasa.gov/api/citations/20220013418/downloads/ASCEND-Communication%20Delays%2C%20Disruptions%2C%20and%20Blackouts%20for%20Crewed%20Mars%20Missions.pdf
- D2 Parisi et al. Crew autonomy and communication delay, AHFE 2024 (NASA Ames HSI). https://hsi.arc.nasa.gov/publications/AHFE_2024_Parisi.pdf
- D3 NASA. Deep Space Healthcare, Houston We Have a Podcast (2020), transcript with NASA medical experts; direct institutional source for ISS two-way video support and onboard ultrasound. Supplement: NASA, Ultrasound Scans in Space Transform Medicine on Earth (2022), for remotely guided crew examinations. https://www.nasa.gov/podcasts/houston-we-have-a-podcast/deep-space-healthcare/ ; https://www.nasa.gov/missions/station/ultrasound-scans-in-space-transform-medicine-on-earth/
- D4 Integrated Medical Model / exploration medical capability (NASA NTRS 20170004604). https://ntrs.nasa.gov/api/citations/20170004604/downloads/20170004604.pdf
- D5 Same direct NASA sources as D3. Source replacement supports telemedicine and ultrasound; does not establish an exhaustive equipment inventory or guarantee that no physician is on a particular crew.
- D6 Crew Medical Officer interview study, 10 former CMOs (NASA NTRS 20230013415). https://ntrs.nasa.gov/api/citations/20230013415/downloads/IWS_CMO.pdf
- D7 Exploration Medical Officer KSA poster (NASA NTRS 20230007088). https://ntrs.nasa.gov/api/citations/20230007088/downloads/ExMO%20KSA%20Poster.pdf

### 2.5 Hostile closed environment, nutrition, microbiome (E)

- E1 NASA HRP. Hazard: Hostile Closed Environments. https://www.nasa.gov/hrp/hazard-hostile-closed-environments
- E2 NASA Office of the Chief Health and Medical Officer. CO2 technical brief. https://nasa.gov/wp-content/uploads/2023/03/co2-technical-brief-ochmo.pdf
- E3 NASA OCHMO. Spacecraft acoustic limits, conditions and countermeasures (technical brief). https://www.nasa.gov/sites/default/files/atoms/files/acoustics_technical_brief_ochmo_0.pdf
- E4 Tierney et al. Longitudinal multi-omics analysis of host microbiome architecture and immune responses during short-term spaceflight. Nature Microbiology 9:1661–1675 (2024), published 11 June 2024. Peer-reviewed original study, four Inspiration4 participants; replaces preprint. https://www.nature.com/articles/s41564-024-01635-8 ; https://doi.org/10.1038/s41564-024-01635-8
- E5 NASA NTRS. Clinical nutrition assessment of ISS astronauts (Expeditions 1–12). https://ntrs.nasa.gov/api/citations/20060049121/downloads/20060049121.pdf
- E6 NASA. Nutritional Biochemistry, sections Studying the Role of Nutrition in Spaceflight and Operational Goals. Already a direct NASA source; canonical URL replaces the opaque page-ID link. Confirms ISS Food Intake Tracker first deployed in 2016. https://www.nasa.gov/directorates/esdmd/hhp/nutritional-biochemistry/
- E7 NASA NTRS. HERA meal-replacement bar study. https://ntrs.nasa.gov/api/citations/20170009922/downloads/20170009922.pdf

### 2.6 Reference ranges (R)

- R1 MedlinePlus. Vital signs. https://medlineplus.gov/ency/article/002341.htm
- R2 2025 AHA/ACC multisociety Guideline for the Prevention, Detection, Evaluation and Management of High Blood Pressure in Adults, section 2.1, Table 4. Circulation. DOI: 10.1161/CIR.0000000000001356; parallel JACC publication DOI: 10.1016/j.jacc.2025.05.007. Primary guideline replaces HCPLive. https://www.ahajournals.org/doi/10.1161/CIR.0000000000001356 ; https://www.jacc.org/doi/10.1016/j.jacc.2025.05.007 . Official AHA category/emergency chart: https://www.heart.org/en/health-topics/high-blood-pressure/the-facts-about-high-blood-pressure
- R3 MedlinePlus. Pulse oximetry. https://medlineplus.gov/lab-tests/pulse-oximetry/
- R4 NIDDK. Diabetes tests and diagnosis (table attributed to the American Diabetes Association). https://www.niddk.nih.gov/health-information/diabetes/overview/tests-diagnosis
- R5 MedlinePlus. Hypoglycemia. https://medlineplus.gov/hypoglycemia.html
- R6 NASA NTRS. Clinical nutrition assessment of ISS astronauts. https://ntrs.nasa.gov/api/citations/20060049121/downloads/20060049121.pdf

### 2.7 Project rationale (X)
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

### 2.8 Blood results demo (Phase 6B) and research basis

These references are the research basis for the simulated Blood results screen. The screen embeds no NASA data. In the application they are shown on the Blood results screen with local codes R1 to R5, D1 and D4, which are different from the R and D codes above.

- **R1** NASA Glenn: In-situ Lab Analysis. [Official page](https://www.nasa.gov/glenn/glenn-expertise-space-exploration/human-health-performance/exploration-medical-technologies/in-situ-lab-analysis/)
- **R2** NASA: Protecting Astronaut Health with the Prick of a Finger. [Official article](https://www.nasa.gov/humans-in-space/protecting-astronaut-health-with-the-prick-of-a-finger/)
- **R3** NASA ISS Daily Summary, 18 January 2021. [Official operations report](https://www.nasa.gov/blogs/stationreport/2021/01/18/iss-daily-summary-report-1-18-2021/)
- **R4** NASA NTRS HemoCue technical material. [2021 presentation, ID 20210000516](https://ntrs.nasa.gov/citations/20210000516); [results and lessons learned, ID 20210026808](https://ntrs.nasa.gov/citations/20210026808)
- **R5** Rea et al. (2024), Single drop cytometry onboard the International Space Station. Nature Communications 15, 2634. [DOI](https://doi.org/10.1038/s41467-024-46483-6); [full text](https://pmc.ncbi.nlm.nih.gov/articles/PMC10963801/); [NASA NTRS record](https://ntrs.nasa.gov/citations/20230012750)
- **D1** NASA OSDR, OSD-569 / LSDS-7. [Study page](https://osdr.nasa.gov/bio/repo/data/studies/OSD-569)
- **D4** NASA: I4 Mission Datasets. [Official overview](https://www.nasa.gov/osdr-latest-news-i4-mission-datasets/); [Inspiration4 data access through the NASA Open Science Data Repository](https://www.nature.com/articles/s41526-024-00393-5)

The research proposal behind this screen (team member Marialena, 14 November 2026) also describes NASA OSDR Inspiration4 datasets (OSD-569, OSD-575, https://osdr.nasa.gov/) as a possible future data source. The build does not use them.

---

## 3. Additional background references

These references informed the choice of health domains, indicators and monitoring approach. They are listed for context; the codes in section 2 are the ones cited by the application's rules and texts.

#### NASA Human Research Program — Spaceflight Hazards and Risks

- B1 NASA Human Research Program (HRP). https://www.nasa.gov/hrp/
- B2 NASA — Risks of Human Spaceflight. https://www.nasa.gov/hrp/risks/
- B3 NASA Human Research Roadmap — Risks. https://humanresearchroadmap.nasa.gov/Risks/
- B4 NASA Human Research Roadmap — Evidence Reports. https://humanresearchroadmap.nasa.gov/Evidence/
- B5 NASA Human Research Roadmap. https://humanresearchroadmap.nasa.gov/
- B6 NASA — Human Health and Performance: Keeping Astronauts Safe and Productive on a Mission to Mars. https://www.nasa.gov/wp-content/uploads/2024/01/human-health-and-performance.pdf
- B7 NASA — Fundamentals of Human Health. https://www.nasa.gov/reference/fundamentals-of-human-health/
- B8 NASA — Human System Risks. https://www.nasa.gov/hhp/human-system-risks/

#### Health Monitoring and Standard Measures

- B9 NASA — Spaceflight Standard Measures. https://www.nasa.gov/reference/standard-measures/
- B10 NASA — Spaceflight Standard Measures: Characterizing How Humans Adapt in Space. https://www.nasa.gov/humans-in-space/spaceflight-standard-measures-characterizing-how-humans-adapt-in-space/
- B11 NASA Technical Reports Server — Standard Measures During Spaceflight. https://ntrs.nasa.gov/citations/20210022783
- B12 NASA Technical Reports Server — Standard Measures and Human Spaceflight Research. https://ntrs.nasa.gov/citations/20230014025
- B13 NASA — Cardiovascular and Vision Research. https://www.nasa.gov/directorates/esdmd/hhp/cardiovascular-and-vision/
- B14 NASA — Health and Medical Care. https://www.nasa.gov/reference/3-0-health-and-medical-care/
- B15 NASA — Appendix E: Health and Medical Care Technical Requirements. https://www.nasa.gov/reference/appendix-e-health-and-medical-care-technical-requirements/
- B16 NASA Technical Reports Server — Standard Measures Mapped to Human Research Program Risks. https://ntrs.nasa.gov/api/citations/20200001331/downloads/20200001331.pdf

#### Cardiovascular Health and Orthostatic Intolerance

- B17 NASA — Risk of Cardiovascular Adaptations. https://www.nasa.gov/reference/risk-of-cardiovascular-adaptations/

#### Spaceflight-Associated Neuro-Ocular Syndrome (SANS)

- B18 NASA — Risk of Spaceflight-Associated Neuro-Ocular Syndrome (SANS). https://www.nasa.gov/reference/risk-of-spaceflight-associated-neuro-ocular-syndrome-sans/
- B19 Lee et al. — Spaceflight-Associated Neuro-ocular Syndrome (SANS). PubMed Central (PMC). https://pmc.ncbi.nlm.nih.gov/articles/PMC7005826/

#### Bone, Muscle, and Physical Deconditioning

- B20 NASA — Risk of Spaceflight-Induced Bone Changes. https://www.nasa.gov/reference/risk-of-spaceflight-induced-bone-changes/
- B21 NASA Human Research Roadmap — Bone Risk Evidence. https://humanresearchroadmap.nasa.gov/risks/risk.aspx?i=77
- B22 Scientific Review — Bone Loss and Spaceflight. PubMed Central (PMC). https://pmc.ncbi.nlm.nih.gov/articles/PMC8274610/

#### Sleep, Circadian Rhythm, and Cognitive Performance

- B23 NASA — Risk of Inadequate Sleep and Irregular Schedules. https://www.nasa.gov/reference/risk-of-inadequate-sleep-and-irregular-schedules
- B24 NASA — Risk of Performance Decrements and Adverse Health Outcomes Resulting from Sleep Loss, Circadian Desynchronization, and Work Overload. https://www.nasa.gov/directorates/esdmd/hhp/risk-of-performance-decrements-and-adverse-health-outcomes-resulting-from-sleep-loss-circadian-desynchronization-and-work-overload/

#### Behavioral Health, Psychological Well-Being, and Team Performance

- B25 NASA — Behavioral Health Risk. https://www.nasa.gov/directorates/esdmd/hhp/behavioral-health-risk/

#### Immune System and Host-Microorganism Interactions

- B26 NASA — Risk of Altered Immune System Responses. https://www.nasa.gov/reference/risk-of-altered-immune-system-responses/
- B27 NASA — Immune Biomarkers. https://www.nasa.gov/reference/immune-biomarkers/

#### Space Radiation

- B28 NASA — Risk of Radiation Carcinogenesis. https://www.nasa.gov/directorates/esdmd/hhp/risk-of-radiation-carcinogenesis/
- B29 NASA — Space Radiation. https://www.nasa.gov/directorates/esdmd/hhp/space-radiation/

#### Spacecraft Environment, Hypoxia, and Carbon Dioxide

- B30 NASA — Risk of Hypoxia. https://www.nasa.gov/reference/risk-of-hypoxia/
- B31 NASA — Carbon Dioxide Risk. https://www.nasa.gov/directorates/esdmd/hhp/carbon-dioxide-risk/

#### Sensorimotor and Vestibular Function

- B32 NASA — Risk of Altered Sensorimotor and Vestibular Function. https://www.nasa.gov/reference/risk-of-altered-sensorimotor-and-vestibular-function/

#### Nutrition, Hydration, and Urinary Health

- B33 NASA — Risk of Inadequate Food and Nutrition. https://www.nasa.gov/reference/risk-of-inadequate-food-and-nutrition/
- B34 NASA — Urinary Health. https://www.nasa.gov/ochmo-mtb-003-urinary-health-2/

#### Medical Operations, Crew Training, and Spaceflight Standards

- B35 NASA Spaceflight Human-System Standard, Volume 2: Human Factors, Habitability, and Environmental Health. https://standards.nasa.gov/node/237
- B36 NASA — Health and Medical Requirements for Human Space Exploration. https://nodis3.gsfc.nasa.gov/displayAll.cfm?Internal_ID=N_PR_8900_0001_&page_name=all

#### Scientific Reviews and Research Literature

- B37 Fundamental Biological Features of Spaceflight: Advancing the Field to Enable Deep-Space Exploration. Cell (2020). https://doi.org/10.1016/j.cell.2020.10.050
- B38 Spaceflight Standard Measures is a Multidisciplinary Study That Systematically Monitors Risks to Astronaut Health and Performance. PubMed Central (PMC). https://pmc.ncbi.nlm.nih.gov/articles/PMC12612093/

#### NASA Research Data Repositories

- B39 NASA Open Science Data Repository (OSDR). https://osdr.nasa.gov/
- B40 NASA Life Sciences Data Archive (LSDA). https://lsda.jsc.nasa.gov/
- B41 NASA Technical Reports Server (NTRS). https://ntrs.nasa.gov/
- B42 NASA Earthdata. https://www.earthdata.nasa.gov/

---

## 4. NASA Space Apps Challenge references

- N1 NASA Space Apps Challenge. Official website. https://www.spaceappschallenge.org/
- N2 NASA Space Apps Challenge. Legal information. https://www.spaceappschallenge.org/legal/

---

## 5. Technologies and assets

- Application: HTML, CSS and vanilla JavaScript in one self-contained file. No external libraries, no CDN, no server, no paid API. Viva's free-text answers use a local keyword and rule engine; there is no language model and no network call.
- Voice output (optional, off by default): the browser's built-in Web Speech API, SpeechSynthesis. https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis
- Fonts: system fonts only.
- Images and icons: all drawn by the team as inline SVG. The Vivonaut logo and the Viva avatar are original designs. No NASA logo or insignia is used.
- Data: all crew members, readings and events in the demo (Mark Anderson, Sebastian, "Demo Mars transit mission") are fictional and simulated.
- Testing tools (used during the build, not part of the application): Playwright with headless Chrome, https://playwright.dev ; Node.js, https://nodejs.org

---

## 6. Notes on the use of these references

- NASA Human Research Program and Human Research Roadmap resources were the primary framework for the spaceflight hazards and the health risks they cause.
- NASA Standard Measures resources were consulted to understand how astronaut health and performance are assessed in flight.
- Where a news article or other secondary summary was first used, it was replaced by the original study or the institutional source. Some codes are kept for compatibility and say so explicitly (for example, two codes that point to the same original study).
- A source being listed does not mean every measurement or procedure it describes is implemented in Vivonaut.
- Reference ranges for general health indicators come from the sources in section 2.6. Rules and thresholds that are not directly sourced are prototype rules, labelled DEMO in the application, and are not validated clinical criteria.
- Radiation doses shown in the application are simulated unless entered from a dosimeter.
- Future ideas (such as real point-of-care blood analysis and a simulated ground-team view) are roadmap concepts or simulations. The Blood results screen uses a fictional fixture and is clearly labelled as a simulated analyzer. They are not implemented medical functions, and Vivonaut does not analyse blood or connect to real devices.
- Vivonaut is an educational and health-monitoring prototype. It is not a certified medical device and does not replace professional medical assessment, the crew medical officer, flight surgeons or approved spacecraft medical procedures.

---

## 7. Licences of the materials used

- Vivonaut's own code, text and original SVG graphics are released under the Apache License 2.0 (see `LICENSE`), an open source licence as defined by the Open Source Initiative.
- The application contains no third-party code, library, font, image, audio or dataset. The sources in sections 2 to 4 are cited as references and are not copied or redistributed; the application links to them only when the user clicks.
- The reference UI mockup generated with ChatGPT is not part of the application or of this repository.
