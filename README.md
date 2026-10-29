# The Map and the Flood

An interactive visual essay about automation and work. Explore 38 roles on a terrain map, adjust a scenario horizon, and inspect the assumptions behind each role's position.

[Explore the map](https://bmc-inc.github.io/flood-map/) · [Explore a role](https://bmc-inc.github.io/flood-map/career-survival-score.html)

## Two ways to explore

- **Terrain map:** move the scenario slider to compare roles across six sectors. Select a role to read its assumptions, and toggle labels for a clearer view.
- **Career Scenario Explorer:** search for a role, adjust the horizon, and download or share a PNG of the resulting scenario index. Role selection works with a pointer or keyboard.

This is a working, browser-based editorial demo. It is designed to make assumptions visible and discussable; it is not a validated labor-market forecast or a career assessment.

## Model and limitations

Each role has an author-assigned elevation between 0 and 100. A separate, hand-authored timeline maps years to an increasing automation level. These inputs are illustrative assumptions, not observations fitted to employment data.

The role explorer maps the difference between elevation and scenario level to a smooth index:

```text
index = 100 / (1 + exp(-(elevation - scenario_level) / 8))
```

The index ranges from 0 to 100. **It is not a measured probability of job survival.** A midpoint crossing means the scenario level has reached the assigned elevation; it is not a predicted date of job loss. Role descriptions explain the scenario's reasoning rather than document current adoption statistics.

The model does not incorporate regional labor markets, wages, employment counts, individual skills, policy changes, adoption costs, uncertainty estimates, or new jobs created by technology. Its scenario dates span 2023–2060 for the map and 2026–2060 for the role explorer. There is no live data feed.

## Run locally

The two pages use plain HTML, CSS, JavaScript, and SVG. There are no packages to install or API keys to configure.

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

Open [localhost:8000](http://localhost:8000) or [the role explorer](http://localhost:8000/career-survival-score.html). Stop the server with `Ctrl+C`.

Calculations and PNG generation happen in the browser. Google Fonts supplies the optional typefaces; system fonts provide a fallback. Using a device's native share sheet sends the generated image to the destination you select.

## Repository guide

| File | Contents |
| --- | --- |
| [`index.html`](index.html) | Terrain, job assumptions, timeline, and map interactions |
| [`career-survival-score.html`](career-survival-score.html) | Role search, scenario index, trend chart, and PNG sharing |

The existing role-page filename is retained so previously shared links continue to work. If changing role assumptions, keep both pages consistent. Check slider extremes, search, keyboard selection, touch targets, and image download before publishing.

## Feedback and reuse

[Open an issue](https://github.com/BMC-INC/flood-map/issues) for a visualization bug or a proposed model improvement. Include a reproducible example and sources for any empirical claim.

No repository-wide open-source license is currently included. Public source visibility does not grant a general reuse license.
