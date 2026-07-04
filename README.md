<img width="1902" height="1073" alt="Screenshot 2026-07-03 182916" src="https://github.com/user-attachments/assets/cd2b1dd9-dc26-438b-834f-5cc668b123ac" />
# ORBITAL — Satellite Intelligence Dashboard

A real-time 3D satellite tracking dashboard that visualizes the live positions of thousands of Earth-orbiting objects, propagated from actual orbital element data.

**[Live Demo →](#)** *(https://jmarin357.github.io/orbital-dashboard/)*

![screenshot](screenshot.png)
*(optional — drop a screenshot or GIF here; see instructions below)*

## What it does

- Pulls live TLE (Two-Line Element) catalog data from [CelesTrak](https://celestrak.org)
- Propagates real-time positions for thousands of satellites using the SGP4 orbital model
- Renders everything on an interactive 3D globe with day/night lighting and a procedural starfield
- Click any satellite for a full profile: general info, live telemetry (altitude, velocity, illumination state, days in orbit), and a historical orbit replay with scrubber controls
- Full-screen Constellations view comparing fleets (Starlink, OneWeb, GPS, weather, etc.) by orbital class and count
- Conjunctions view — a sortable close-approach screening queue (clearly labeled as simulated demonstration data, since real conjunction assessment requires restricted CDM/SOCRATES feeds)
- Pass prediction — opt-in browser geolocation used to compute the next visible pass of a selected satellite over your location (coordinates never leave the browser)

## Tech stack

- **CesiumJS** — 3D globe rendering, camera control, terrain/atmosphere lighting
- **satellite.js** — SGP4/SDP4 orbital propagation from TLE data
- **Chart.js** — fleet distribution histograms
- **Vanilla JS / HTML / CSS** — no framework, no build step, single file

## Data integrity notes

This project only displays information that's actually derivable from public orbital element data:
- Orbital parameters (altitude, velocity, inclination, period, apogee/perigee) are computed directly from SGP4 propagation — genuinely real.
- Fields like operator, country, and launch year are heuristic estimates inferred from satellite naming conventions and COSPAR designators, and are explicitly labeled "est." in the UI.
- Fields not derivable from TLE data (launch vehicle, manufacturer, launch site) are shown as "not available" rather than guessed.
- The Conjunctions view is clearly marked as simulated screening data for demonstration purposes.

## Run it locally

It's a single self-contained HTML file — no build step, no dependencies to install.

```bash
git clone https://github.com/YOUR_USERNAME/orbital-dashboard.git
cd orbital-dashboard
# just open index.html in a browser, or serve it locally:
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Why I built this

I built a satellite tracking dashboard that visualizes real-time satellite data from CelesTrak, enabling live monitoring of all objects in orbit along with enhanced analytical insights.
