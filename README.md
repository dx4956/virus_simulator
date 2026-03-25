# Epidemic Simulator

An interactive, browser-based educational tool that visualizes how infectious diseases spread through populations using real-time particle physics and epidemiological modeling.

![Epidemic Simulator](https://img.shields.io/badge/type-educational-blue) ![Tech](https://img.shields.io/badge/tech-vanilla%20JS%20%7C%20Phaser3%20%7C%20Plotly-green)

## Overview

The simulator models individuals as moving particles in a contained environment. When infected particles contact susceptible ones, disease spreads probabilistically based on configurable parameters. The result is a visual, real-time demonstration of epidemic dynamics including herd immunity, quarantine effects, and waning immunity.

## Features

- **12 Pre-configured Disease Scenarios** — Classic SIR, COVID-19, Ebola, Influenza, Black Death, Zombie Virus, SARS-CoV-1, Measles, Spanish Flu, Smallpox, MERS-CoV, and Rabies
- **Physics-based particle simulation** — individuals move, collide, and transmit disease via contact
- **Live statistics dashboard** — day counter, active infections, peak infections, deaths, and estimated R₀
- **Real-time population graph** — Plotly chart tracking susceptible, infected, recovered, and deceased over time
- **Advanced disease mechanics** — asymptomatic carriers, waning immunity, zombie reanimation mode, adaptive quarantine
- **Fully configurable parameters** — population size, infection rate, death rate, recovery rate, vaccination %, quarantine threshold, and social distancing level

## Disease Scenarios

| Scenario | Description |
|---|---|
| Classic SIR | Standard textbook epidemiological model |
| COVID-19 | Waning immunity + asymptomatic carrier dynamics |
| Ebola | High mortality, slow spread |
| Influenza | Fast spread, seasonal immunity loss |
| Black Death | Medieval plague, no precautions |
| Zombie Virus | Dead individuals reanimate and rejoin infected pool |
| SARS-CoV-1 | 2003 outbreak model |
| Measles | Highly contagious, herd immunity showcase |
| Spanish Flu | 1918 pandemic, high mortality rate |
| Smallpox | Historical eradication via vaccination |
| MERS-CoV | High fatality, low transmission |
| Rabies | Near-100% fatality, minimal spread |

## Getting Started

No installation or build step required — this is a pure client-side web app.

1. Clone or download the repository
2. Open `index.html` in any modern browser
3. Select a disease scenario from the cards at the top
4. Adjust parameters with the sliders (optional)
5. Click **RUN SIMULATION**

## Parameters

| Parameter | Range | Effect |
|---|---|---|
| Population | 10 – 350 | Number of individuals in the simulation |
| Initial Infected | 1 – 20 | Starting infected count |
| Infection Rate | 0 – 100% | Base probability of transmission on contact |
| Precautions | 0 – 10 | Social distancing level; reduces infection rate by 3% per level |
| Vaccination % | 0 – 100% | Share of population pre-immunized at start |
| Quarantine Threshold | 0 – 100% | Infection % at which movement slows by 40% |
| Recovery Rate | 0 – 100% | Speed of recovery; affects illness duration |
| Death Rate | 0 – 100% | Probability infected individuals die rather than recover |

## Tech Stack

| Component | Library |
|---|---|
| Physics & rendering | [Phaser 3](https://phaser.io/) |
| Charts | [Plotly.js](https://plotly.com/javascript/) |
| UI/styling | Vanilla CSS (dark terminal aesthetic) |
| Logic | Vanilla JavaScript (ES6) |

## Project Structure

```
virus_simulator/
├── index.html          # App shell and layout
├── css/
│   └── style.css       # Dark terminal UI styling
├── js/
│   ├── scenarios.js    # Disease scenario definitions
│   ├── input.js        # Parameter binding and UI initialization
│   ├── simulation.js   # Phaser game loop, physics, infection mechanics
│   ├── graph.js        # Plotly chart rendering
│   ├── phaser.min.js   # Phaser engine (bundled)
│   └── plotly.js       # Plotly library (bundled)
└── sprite/             # Particle sprite assets
```

## How It Works

- **Infection**: When an infected particle overlaps a susceptible one, transmission is tested probabilistically. The base infection rate is reduced by precautions level, asymptomatic status (60% reduction), and quarantine mode (40% reduction).
- **Recovery / Death**: After 3–15 seconds (based on recovery rate), infected individuals either recover or die according to the death rate.
- **Waning Immunity**: Recovered individuals lose immunity after ~15 simulation seconds and re-enter the susceptible pool.
- **R₀ Estimation**: Computed daily as `(new infections / previously infected) × 2`, smoothed with a 60/40 exponential weighted average.
- **Zombie Mode**: Deceased individuals reanimate and re-enter the infected population.

## License

MIT
