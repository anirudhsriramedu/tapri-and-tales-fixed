# ☕ TAPRI & TALES — The Campus Chai Simulator

**Purani Tapri, Naya Andaaz.** A browser-first virtual chai stall for the OWASP NIE Vibe Sprint. Build your stall, buy ingredient stock, price chai, serve customers, record real sales, and survive the Day 2 milk supply shock.

## Start

Requires **Node.js 20+**. No paid services, database, API keys or `.env` files. The project deliberately uses zero third-party runtime dependencies.

```bash
npm install
npm run dev
```

Open **http://localhost:5173**. Use `npm test` for the finance-engine tests. `npm run build` performs syntax checks and tests; no compilation is needed.

The app is a normal static HTML/CSS/JavaScript browser application served by a tiny Node server for development. For hosting, upload `index.html` and `src/` to any static site host. Do not open index.html directly using `file://` because browser ES module loading may be blocked.

## Demo for judges

1. Choose **Judge Mode** on the landing page. Choose and purchase ingredient packs (or skip purchasing to use the starter inventory). Go to **Menu & Pricing** and adjust a price.
2. Go to **Customer Rush**, open the stall, and click **Quick Day**, then show **Daily Report** (sales revenue, COGS, expenses, gross profit, net profit and closing cash).
3. Choose **Next Day**. The milk cost doubles from ₹60/L to ₹120/L. Compare **Raise Prices**, **Accept Lower Profit**, and **Change the Menu**; commit one strategy and run another Quick Day.

## Game mechanics

- Cash begins at ₹2,000; fictional starter stock is separately valued as inventory.
- Purchases reduce cash but do not directly reduce profit. Cost of ingredients is recognized upon consumption.
- Supplier prices are illustrative. Milk shock doubles **new supplier price** and preserves old stock cost basis.
- Day 2 is gated behind one of three crisis decisions. A deterministic seeded simulation lets judges replay scenarios.
- Language switch covers navigation and main business labels; some decorative game copy remains in English/Hinglish.
- Progress persists in localStorage. Reset game under Settings.

## Project files

`src/engine.js` pure financial/game rules; `src/main.js` UI and interactions; `src/style.css` responsive game design; `server.mjs` dependency-free local development server; `tests/engine.test.js` tests; `docs/DEMO.md` judge script.

## Known limitations

- This is a **functional browser-first MVP**, not a full implementation of every optional master-prompt feature. Advanced Udhaar Khata, interactive Kadak Meter, extra events, and real sound are not implemented.
- The immersive stall is made with HTML/CSS and emoji rather than detailed commissioned vector illustrations.
- No player authentication, backend or external data sources (by challenge design).
- Default seeded simulation is deterministic; interactive service depends on the player's choices.
- Hindi support is partial, not a complete localized translation of all narrative copy.
- A full automated browser interaction test is not included; pure-engine tests are included.
