# Fashion World

A complete single-player fashion-business strategy game for the browser. Start with $8,000 and 250 followers, then build your label across a 12-week season.

## Play

- Design polos, sweatshirts, and jackets with three natural-fiber options and four colorways.
- Set production quantities and retail prices. Production is paid immediately.
- React to weekly market trends and events, and choose a marketing campaign.
- Launch each week to sell inventory, grow an audience, and pay operating costs.
- Reprice unsold inventory, review financial results, and aim for a breakout label.

Progress autosaves to the current browser using localStorage. No account, server, payment, API key, or AI inference is needed to play. Clearing browser storage removes the saved season. Art shows silhouette references; selected colors and fabrics affect the simulation rather than recoloring the image.

## Run locally

Requires Python 3 to serve files. Requires Node.js 20+ only for tests.

```sh
python3 -m http.server 8080 --directory dist
```

Open http://localhost:8080. Serve through HTTP; browser ES modules may not load through file://.

```sh
npm test
```

There are no npm dependencies and no build step. `dist/` contains the authored game, not generated build output.

## Structure

- `dist/engine.js`: pure simulation functions, seeded demand, economics, season events, save validation.
- `dist/app.js`: rendering, input handling, local saves, optional synthesized sound.
- `dist/style.css`: responsive desktop and mobile presentation.
- `dist/assets/editorial.webp`: original AI-generated editorial artwork.
- `tests/`: simulation/accounting tests and a lightweight UI event/render smoke test.

The font stylesheet is loaded from Google Fonts, with local font fallbacks. Gameplay and artwork are self-contained. Tests verify financial conservation, inventory accounting, campaign completion, invalid actions, overproduction risk, deterministic randomness, saving, and basic UI event flows. Browser layout and touch interactions have not been manually verified.

## Hosting

Serve `dist/` on any static host. A private playable Sites release is configured in `.openai/hosting.json`. That file identifies this deployment and should be removed when making an independent fork. A future GitHub Pages setup can publish `dist/` with a Pages workflow.

## Game balance

Demand responds to price relative to perceived quality, trends, reputation, audience, marketing, the event decision, and seeded variation. Multiple active designs compete for the same audience. Operating profit accounts for cost of goods sold; cash also reflects upfront production. All business numbers are fictional gameplay rules.
