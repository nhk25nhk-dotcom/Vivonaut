# Vivonaut – Your Intelligent Health Companion in Space

**NASA Space Apps Challenge 2026** · Challenge: *Create Health Monitoring Software for Astronauts on Space Missions*

**Live demo:** [add the GitHub Pages link here after Phase 9]
**Run it locally:** download `index.html` and open it in any modern browser. It works offline, with no installation, no server and no account.

> **Educational simulation.** Vivonaut is a prototype. It is not a certified medical device and does not replace a crew medical officer, flight surgeons or approved mission procedures. All crew members, readings and events in the demo are fictional and simulated.

---

## What is Vivonaut?

On long missions far from Earth, astronauts carry much of the responsibility for noticing health changes in themselves. Vivonaut is an offline health companion that helps a crew member **collect** health indicators, **validate** the measurement, **analyze** it against a personal baseline, **assess** the status, **guide** the next step, and **track** the follow-up. Its assistant, **Viva**, explains every alert and what evidence supports it, and prepares a **Health Handover** report that is stored locally and ready to send when contact with the ground returns.

## How it answers the challenge

[Fill after Phase 9. Map each NASA hazard to what the app actually does, using only features that were tested.]

| NASA hazard / health risk | What Vivonaut does |
|---|---|
| Space radiation | [ ] |
| Isolation and confinement | [ ] |
| Distance from Earth | [ ] |
| Gravity fields | [ ] |
| Hostile closed environment | [ ] |

## Features

[List only what was implemented and tested. Do not list roadmap ideas here.]

## How it works

- One self-contained `index.html` (HTML, CSS, vanilla JavaScript). No libraries, CDN, API, server or AI service at runtime.
- A rule-based engine with a frozen personal baseline, a measurement-context check, and explainable statuses (Stable, Watch, Needs assessment, Alert, No data). Every status shows why it appeared.
- Viva speaks from prepared, reviewed text. Voice output is optional and off by default; captions are always on.
- Thresholds are tagged **SOURCED**, **DEMO** or **BASELINE**. DEMO rules are prototype choices and are never attributed to NASA.

## What is real and what is simulated

- **Simulated:** all crew, readings, events and radiation doses shown in the demo.
- **Real:** the logic, the explanations, and the references behind the sourced reference ranges.
- **Not implemented:** connection to any real device or ground team; blood or saliva analysis.

## Roadmap (concepts, not built)

- Wearables and device integration.
- Point-of-Care Blood Analysis Concept: in the future, a small sample read by a compact on-board device. Vivonaut does not analyse blood today.
- [If Phase 10 was completed: Ground Medical Dashboard, a simulated ground-team view. No real transmission.]

## Sources and credits

All data, resources, tools, code, text and images used are listed in [`docs/RESOURCES.md`](docs/RESOURCES.md). The scientific references and the rules behind each threshold are in [`docs/science/SCIENCE_MAP.md`](docs/science/SCIENCE_MAP.md).

- Fonts: system fonts only. Images and icons: original inline SVG. No NASA logo or insignia is used.

## AI assistance disclosure

This project was built with assistance from Claude (Anthropic), an AI assistant. Concept, research direction, design decisions, testing and review by Team Vivonaut. The reference UI mockup was generated with ChatGPT (OpenAI). [Add Gemini if used.] The AI-use log is in [`docs/AI_USE_LOG.md`](docs/AI_USE_LOG.md).

## Limits

- Prototype built in one hackathon weekend. Not clinically validated.
- Measurements are entered by the user or simulated; the app does not read sensors.
- Voice depends on the voices installed on the device.

## Team

Team Vivonaut: [names and roles]

## License

[Choose with the team, for example MIT, then add a LICENSE file.]
