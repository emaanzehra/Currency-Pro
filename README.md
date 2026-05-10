# CurrencyPro

> Professional real-time currency converter — 160+ currencies, live charts, watchlist & history

![Version](https://img.shields.io/badge/version-1.0.0-10B981)
![React](https://img.shields.io/badge/React-18.2.0-61DAFB)
![License](https://img.shields.io/badge/license-MIT-green)
![No Build](https://img.shields.io/badge/build-none%20required-lightgrey)

A fully client-side currency converter with a professional dark UI, animated 3D globe
hero, live ticker tape, interactive 30-day charts, a watchlist, and auto-saved conversion
history. No backend, no build tool, no npm install — just open the HTML file.

---

## Table of Contents

1. [Features](#features)
2. [Supported currencies](#supported-currencies)
3. [Quick start](#quick-start)
4. [Architecture](#architecture)
5. [Component reference](#component-reference)
6. [Key utility functions](#key-utility-functions)
7. [How to use the app](#how-to-use-the-app)
8. [Customisation](#customisation)
9. [FAQ](#faq)
10. [License](#license)

---

## Features

| Feature | Description |
|---|---|
| **Live converter** | Instant conversion between 160+ currencies with animated result flip and one-click copy |
| **Interactive 30-day chart** | Hover-to-inspect SVG chart per pair with gradient fill, grid lines and date labels |
| **Full rates table** | All 160+ currencies with country flags, USD rate, sparklines and a quick-convert shortcut |
| **Watchlist** | Six tracked pairs with live trend direction, % change and sparkline per pair |
| **Conversion history** | Auto-saves every conversion with timestamp — tap any entry to repeat it |
| **3D animated globe** | CSS-orbiting currency symbols on a pulsing sphere with animated wave background |
| **Auth flow** | Sign-in / Create Account tabs with full validation, show/hide password, guest access |
| **Smart search** | Search currencies by name or ISO code across all dropdowns |
| **Responsive layout** | Works on desktop, tablet and mobile — tab bar scrolls horizontally on small screens |
| **Slate & Emerald theme** | Professional dark slate base with rich emerald accents, fully customisable via CSS variables |

---

## Supported currencies

160+ world currencies spanning every region. A sample:

| Flag | Code | Name | Region |
|------|------|------|--------|
| 🇺🇸 | USD | US Dollar | Americas |
| 🇪🇺 | EUR | Euro | Europe |
| 🇬🇧 | GBP | British Pound | Europe |
| 🇯🇵 | JPY | Japanese Yen | Asia |
| 🇵🇰 | PKR | Pakistani Rupee | Asia |
| 🇮🇳 | INR | Indian Rupee | Asia |
| 🇨🇳 | CNY | Chinese Yuan | Asia |
| 🇦🇪 | AED | UAE Dirham | Middle East |
| 🇸🇦 | SAR | Saudi Riyal | Middle East |
| 🇰🇼 | KWD | Kuwaiti Dinar | Middle East |
| 🇧🇷 | BRL | Brazilian Real | Americas |
| 🇰🇷 | KRW | South Korean Won | Asia |
| 🇳🇬 | NGN | Nigerian Naira | Africa |
| 🇿🇦 | ZAR | South African Rand | Africa |
| 🇷🇺 | RUB | Russian Ruble | Europe |
| 🇹🇷 | TRY | Turkish Lira | Europe |
| 🇮🇩 | IDR | Indonesian Rupiah | Asia |
| 🇵🇭 | PHP | Philippine Peso | Asia |
| 🇧🇩 | BDT | Bangladeshi Taka | Asia |
| 🇨🇱 | CLP | Chilean Peso | Americas |

> Full list covers Africa, Asia, Americas, Europe, Middle East and Oceania. Every entry
> includes the country flag emoji, ISO 4217 code, full name, currency symbol and exchange
> rate vs USD.

---

## Quick start

### Prerequisites

| Requirement | Details |
|---|---|
| Browser | Any modern browser (Chrome 90+, Firefox 88+, Safari 14+, Edge 90+) |
| Node.js | v18+ — only needed if you want to run a local dev server |
| Internet | Required for CDN-loaded React, Tabler Icons and Google Fonts |
| Backend | None — fully client-side |

### Run instantly

```bash
git clone https://github.com/your-username/currencypro.git
cd currencypro
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

### With a local server (recommended)

```bash
# Option 1 — Node.js
npx serve .
# → http://localhost:3000

# Option 2 — Python
python -m http.server 8080
# → http://localhost:8080

# Option 3 — VS Code
# Install "Live Server" → right-click index.html → "Open with Live Server"
```

> **Note:** Do not open the file via `file://` if you need the clipboard Copy feature.
> Browsers block clipboard access on `file://` origins. Use a local server instead.

---

## Architecture

CurrencyPro is a **single-file React 18 application** loaded entirely from CDN.

```
index.html
  ├── <style>        CSS variables + keyframe animations (Slate & Emerald theme)
  ├── <link>         Tabler Icons 2.44.0 webfont  (cdn.jsdelivr.net)
  ├── <link>         Google Fonts — Inter + JetBrains Mono
  ├── <script>       React 18 UMD  (cdnjs.cloudflare.com)
  ├── <script>       ReactDOM 18 UMD  (cdnjs.cloudflare.com)
  └── <script>       App source (all inline)
       ├── CURR[]         Currency data (160+ entries: code, name, flag, sym, rt)
       ├── RATES{}        Derived lookup map  { "USD": 1, "EUR": 0.9215, … }
       ├── cvt()          Convert amount between two currencies → string
       ├── getRate()      Get formatted rate between two currencies → string
       ├── byCode()       Look up currency object by ISO code
       ├── seeded()       Deterministic PRNG for reproducible sparkline shapes
       ├── Background     Fixed wave/grid SVG layer
       ├── Ticker         Scrolling live rates bar
       ├── Globe          3D CSS-animated orbiting globe
       ├── Spark          Mini SVG sparkline
       ├── FullChart      Interactive 30-day SVG chart
       ├── CurrDrop       Searchable currency dropdown
       ├── Confetti       Copy confirmation particle burst
       ├── LoginPage      Hero + auth form
       ├── ConverterPage  Tab dashboard (Convert / Rates / Chart / Watchlist / History)
       └── App            Root — toggles Login ↔ Converter via user state
```

### External dependencies (CDN only, no install)

| Library | Version | Host |
|---|---|---|
| React + ReactDOM | 18.2.0 | cdnjs.cloudflare.com |
| Tabler Icons webfont | 2.44.0 | cdn.jsdelivr.net |
| Inter | 300–700 | fonts.googleapis.com |
| JetBrains Mono | 400–500 | fonts.googleapis.com |

### State management

All state uses React built-in hooks (`useState`, `useEffect`, `useRef`, `useMemo`).
No Redux, no Zustand, no Context API. State lives entirely within `LoginPage` and
`ConverterPage`, coordinated by a single `user` string in the root `App` component.

---

## Component reference

### Page components

| Component | Description |
|---|---|
| `App` | Root. Holds `user` state. Renders `LoginPage` when null, `ConverterPage` otherwise. |
| `LoginPage` | Animated globe hero, sign-in/create-account tabs with validation, guest access. Calls `onLogin(email)` on success. |
| `ConverterPage` | Main dashboard. Solid-white pill tab bar with five panels: Convert, Rates, Chart, Watchlist, History. |

### UI components

| Component | Props | Description |
|---|---|---|
| `CurrDrop` | `value`, `onChange`, `exclude` | Searchable dropdown — 160+ currencies, closes on outside click. |
| `Spark` | `from`, `to`, `ht`, `wd` | Mini SVG sparkline. Emerald if up, red if down. Seeded per pair. |
| `FullChart` | `from`, `to` | 30-point hover-inspectable SVG chart with gradient fill, Y-axis labels and date row. |

### Visual / animation components

| Component | Description |
|---|---|
| `Background` | Fixed layer: SVG wave paths (CSS animated), subtle dot-grid, radial emerald gradient. |
| `Globe` | Six currency badge symbols orbiting a pulsing sphere via independent `@keyframes`. Radii: 50–92 px. Durations: 4–6.5 s. |
| `Ticker` | Marquee of 14 pair rates scrolling continuously via `animation: ticker`. Doubled string for seamless loop. |
| `Confetti` | 12 particles launched upward on Copy, staggered `animation-delay`, auto-dismissed after 1.8 s. |

---

## Key utility functions

```js
/**
 * Convert an amount from one currency to another.
 * Returns a formatted string, or "" for invalid/empty input.
 *
 * @param {string} amount  - Numeric string from the input field
 * @param {string} from    - ISO 4217 source currency code
 * @param {string} to      - ISO 4217 target currency code
 * @returns {string}
 */
function cvt(amount, from, to) { … }

/**
 * Get the formatted exchange rate between two currencies.
 * Values >= 1000 are comma-formatted; others are fixed to 4 decimal places.
 *
 * @param {string} from - Source currency code
 * @param {string} to   - Target currency code
 * @returns {string}
 */
function getRate(from, to) { … }

/**
 * Look up a currency object by ISO 4217 code.
 * Returns the USD entry as a fallback for unknown codes.
 *
 * @param {string} code
 * @returns {{ code, name, flag, sym, rt }}
 */
function byCode(code) { … }

/**
 * Seeded pseudo-random number generator.
 * Returns a closure () => number in [0, 1].
 * Used to produce deterministic, reproducible sparkline shapes per pair.
 *
 * @param {number} seed
 * @returns {() => number}
 */
function seeded(seed) { … }
```

### Conversion formula

```js
const result = (parseFloat(amount) / RATES[from]) * RATES[to];

// Display formatting
result >= 1000
  ? result.toLocaleString("en-US", { maximumFractionDigits: 2 })
  : result.toFixed(4);
```

---

## How to use the app

### 1 — Sign in or continue as guest

Enter any email and a password of at least 4 characters, then click **Sign In**.
Or tap **Continue as Guest** to skip — all five features are available without an account.

### 2 — Convert

On the **Convert** tab, click either currency dropdown and search by name or ISO code.
Type your amount in the "From" field — the result updates instantly.
Hit **Swap** to reverse the direction, or tap a **Quick Pair** chip for one-click access.
Click **Copy** next to the rate row to copy the result to your clipboard.

### 3 — Rates

The **Rates** tab lists every currency vs USD with a flag, full name, rate and sparkline.
Use the search box to filter. Click **Go** to load that pair into the converter.

### 4 — Chart

The **Chart** tab shows a 30-day indicative trend for the currently selected pair.
Hover anywhere on the line to see the exact rate in a tooltip.
Four stat cards below show: current rate, inverse, 24h change and volatility.

### 5 — Watchlist

The **Watchlist** tab displays six pre-configured pairs with rate, trend % and sparkline.
Click any row to open that pair directly in the converter.

### 6 — History

Every conversion is auto-saved with a timestamp as soon as you change the amount or currencies.
Click any history row to restore that exact conversion. Tap **Clear** to delete all entries.

---

## Customisation

### Change the colour theme

All colours are in the `:root` CSS block at the top of the file.
Replace the emerald values to switch themes:

```css
:root {
  /* Slate backgrounds */
  --s900: #0D1117;   /* darkest background  */
  --s800: #161B22;   /* card background     */
  --s700: #1C2330;   /* input background    */
  --s600: #21262D;   /* surface             */
  --s500: #30363D;   /* border              */

  /* Primary accent — swap these three to change the theme */
  --e500: #10B981;   /* main emerald        */
  --e400: #34D399;   /* lighter shade       */
  --e300: #6EE7B7;   /* highlight           */
}
```

Example swap themes:

```css
/* Royal Blue  */ --e500:#3B82F6; --e400:#60A5FA; --e300:#93C5FD;
/* Amber Gold  */ --e500:#F59E0B; --e400:#FBBF24; --e300:#FCD34D;
/* Soft Violet */ --e500:#8B5CF6; --e400:#A78BFA; --e300:#C4B5FD;
/* Rose Pink   */ --e500:#F43F5E; --e400:#FB7185; --e300:#FDA4AF;
```

### Add a new currency

Append an object to the `CURR` array at the top of the `<script>`:

```js
{
  code: "XYZ",               // ISO 4217 three-letter code
  name: "Example Dollar",    // Full English name
  flag: "🏳️",                // Country flag emoji
  sym:  "$",                 // Currency symbol shown in inputs
  rt:   1.234                // Rate: 1 USD = rt XYZ
}
```

### Connect a live rates API

Replace static `rt` values with a `fetch` on mount. Example using ExchangeRate-API:

```js
const [liveRates, setLiveRates] = useState(RATES); // static fallback

useEffect(() => {
  fetch("https://api.exchangerate-api.com/v4/latest/USD")
    .then(r => r.json())
    .then(data => setLiveRates(data.rates))
    .catch(() => console.warn("Rate fetch failed — using static fallback"));
}, []);
```

Free providers: ExchangeRate-API · Open Exchange Rates · Fixer.io · CurrencyFreaks

### Edit the watchlist

Find the `wl` constant inside `ConverterPage` and edit the pairs:

```js
const wl = [
  ["USD", "EUR"],
  ["USD", "GBP"],
  ["EUR", "JPY"],
  ["USD", "PKR"],   // ← add your pair here as ["FROM", "TO"]
  ["GBP", "INR"],
  ["USD", "AED"],
];
```

Both codes must exist in the `CURR` array.

### Persist history across sessions

History currently resets on page refresh (React state only).
To persist it, add a `localStorage` layer inside `ConverterPage`:

```js
// Initialise from storage
const [history, setHistory] = useState(() => {
  try { return JSON.parse(localStorage.getItem("cp_history") || "[]"); }
  catch { return []; }
});

// Save on every change
useEffect(() => {
  localStorage.setItem("cp_history", JSON.stringify(history));
}, [history]);
```

### Deploy to a static host

Since the app is a single HTML file with no build step, deployment is trivial:

| Host | Steps |
|---|---|
| GitHub Pages | Push `index.html` to the repo root, enable Pages from the Settings tab |
| Netlify | Drag-and-drop `index.html` onto the Netlify dashboard |
| Vercel | `vercel --prod` with no framework preset selected |
| Cloudflare Pages | Connect the repo, set build command to blank and output dir to `/` |

---

## FAQ

**Are the exchange rates real-time?**

The rates in this build are static reference values baked into the source file.
Connect a free API (see Customisation above) to get live rates.

**Does the app store any user data?**

No data leaves the browser. There is no backend, no database, and no analytics.
Conversion history lives in React state and clears on page refresh.
The login form is UI-only — credentials are never transmitted.

**Why does the chart look the same shape for each pair every time?**

Charts use a seeded pseudo-random generator keyed to the currency pair code,
making the shape deterministic per pair but simulated — not real historical data.
Replace `seeded()` with a real historical API call for production use.

**Can I use this in a production app?**

The UI and architecture are production-ready. Before going live:
1. Connect a real exchange rates API
2. Implement proper server-side authentication if needed
3. Persist history to `localStorage` or a backend
4. Add React error boundaries around the main components

**The Copy button doesn't work — why?**

Clipboard access requires a secure context (`https://` or `localhost`).
Opening the file via `file://` protocol blocks clipboard writes silently.
Run a local server as shown in Quick Start.

**How do I add more pairs to the watchlist?**

Edit the `wl` array inside `ConverterPage`.
Add any pair as a `["FROM", "TO"]` tuple using codes from the `CURR` array.

**Can I deploy this to GitHub Pages / Netlify / Vercel?**

Yes — it's a single HTML file. No build command, no output directory configuration.
Just point the host at the root of the repository.

---

## Project structure

```
currencypro/
├── index.html    ← entire application (single file, ~800 lines)
└── README.md     ← this file
```

---

## License

MIT — free to use, modify and distribute. Attribution appreciated but not required.

---

Built with [React 18](https://react.dev) · [Tabler Icons](https://tabler.io/icons) ·
[Inter](https://rsms.me/inter/) · [JetBrains Mono](https://www.jetbrains.com/lp/mono/)

Zero build tooling · Zero backend · Zero dependencies to install