<div align="center">
<br/>

# 💱 CurrencyPro

Professional real-time currency converter
160+ currencies · Live charts · Watchlist · Conversion history

[![Version](https://img.shields.io/badge/version-1.0.0-10B981?style=flat-square&labelColor=0D1117)](https://github.com/emaanzehra/Currency-Pro)
[![React](https://img.shields.io/badge/React-18.2.0-61DAFB?style=flat-square&logo=react&logoColor=61DAFB&labelColor=0D1117)](https://react.dev)
[![License](https://img.shields.io/badge/license-MIT-10B981?style=flat-square&labelColor=0D1117)](LICENSE)
[![No Build](https://img.shields.io/badge/build-none%20required-8B949E?style=flat-square&labelColor=0D1117)](#quick-start)
[![Live API](https://img.shields.io/badge/rates-live%20API%20%2B%20fallback-D29922?style=flat-square&labelColor=0D1117)](#architecture)
[![Currencies](https://img.shields.io/badge/currencies-160%2B-34D399?style=flat-square&labelColor=0D1117)](#supported-currencies)

<br/>

A fully client-side currency converter with a professional dark UI,
animated 3D globe hero, live ticker tape, interactive 30-day charts,
a watchlist and auto-saved conversion history.

**No backend · No build tool · No npm install**

Open `index.html` in any browser and it works immediately.

<br/>

[View Repository](https://github.com/emaanzehra/Currency-Pro) &nbsp;·&nbsp;
[Quick Start](#quick-start) &nbsp;·&nbsp;
[How to Use](#how-to-use-the-app) &nbsp;·&nbsp;
[Customise](#customisation) &nbsp;·&nbsp;
[FAQ](#faq)

<br/>
</div>

---

## Table of Contents

- [Features](#features)
- [Supported Currencies](#supported-currencies)
- [Quick Start](#quick-start)
- [Architecture](#architecture)
- [Component Reference](#component-reference)
- [Key Utility Functions](#key-utility-functions)
- [How to Use the App](#how-to-use-the-app)
- [Customisation](#customisation)
- [FAQ](#faq)
- [Project Structure](#project-structure)
- [License](#license)

---

## Features

| Feature | Description |
|---|---|
| **Live converter** | Instant conversion with animated result flip, one-click copy and confetti burst |
| **30-day chart** | Hover-to-inspect SVG chart per pair with gradient fill, grid lines and date labels |
| **Full rates table** | 160+ currencies with country flags, USD rate, sparklines and a quick-convert shortcut |
| **Watchlist** | Six tracked pairs with live trend direction, percentage change and sparkline per pair |
| **Conversion history** | Auto-saves every conversion with timestamp and lets you repeat any entry instantly |
| **3D animated globe** | CSS-orbiting currency symbols on a pulsing sphere with animated wave background |
| **Live API rates** | Fetches from ExchangeRate-API on load and falls back to static rates when offline |
| **Auth flow** | Sign-in and Create Account tabs with validation, show/hide password and guest access |
| **Smart search** | Search 160+ currencies by name or ISO code across all dropdowns |
| **Responsive layout** | Works on desktop, tablet and mobile with a horizontally scrollable tab bar |
| **Slate and Emerald theme** | Professional dark base with rich green accents, customisable via CSS variables |

---

## Supported Currencies

160+ world currencies covering Africa, Asia, Americas, Europe, Middle East and Oceania.
Every entry includes a country flag emoji, ISO 4217 code, full name and currency symbol.

| Flag | Code | Name | Region |
|:----:|:----:|------|--------|
| 🇺🇸 | `USD` | US Dollar | Americas |
| 🇪🇺 | `EUR` | Euro | Europe |
| 🇬🇧 | `GBP` | British Pound | Europe |
| 🇯🇵 | `JPY` | Japanese Yen | Asia |
| 🇵🇰 | `PKR` | Pakistani Rupee | Asia |
| 🇮🇳 | `INR` | Indian Rupee | Asia |
| 🇨🇳 | `CNY` | Chinese Yuan | Asia |
| 🇦🇪 | `AED` | UAE Dirham | Middle East |
| 🇸🇦 | `SAR` | Saudi Riyal | Middle East |
| 🇰🇼 | `KWD` | Kuwaiti Dinar | Middle East |
| 🇧🇷 | `BRL` | Brazilian Real | Americas |
| 🇰🇷 | `KRW` | South Korean Won | Asia |
| 🇳🇬 | `NGN` | Nigerian Naira | Africa |
| 🇿🇦 | `ZAR` | South African Rand | Africa |
| 🇷🇺 | `RUB` | Russian Ruble | Europe |
| 🇹🇷 | `TRY` | Turkish Lira | Europe |
| 🇮🇩 | `IDR` | Indonesian Rupiah | Asia |
| 🇵🇭 | `PHP` | Philippine Peso | Asia |
| 🇧🇩 | `BDT` | Bangladeshi Taka | Asia |
| 🇨🇱 | `CLP` | Chilean Peso | Americas |

> 160+ currencies in total. Add new ones by appending an object to the `CURR` array in `index.html`.

---

## Quick Start

### Prerequisites

| Requirement | Details |
|---|---|
| Browser | Chrome 90+, Firefox 88+, Safari 14+, Edge 90+ |
| Node.js | v18+ only needed if you want a local dev server |
| Internet | Required for CDN assets and live exchange rates |
| Backend | None |

### Run instantly

```bash
git clone https://github.com/emaanzehra/Currency-Pro.git
cd Currency-Pro

open index.html       # macOS
start index.html      # Windows
xdg-open index.html   # Linux
```

### With a local server (recommended)

Running on `localhost` enables the clipboard Copy feature.

```bash
# Node.js
npx serve .
# http://localhost:3000

# Python
python -m http.server 8080
# http://localhost:8080

# VS Code
# Install the Live Server extension
# Right-click index.html and choose Open with Live Server
```

> **Note:** Browsers block clipboard access on `file://` origins. If the Copy button
> does nothing, switch to a local server.

---

## Architecture

CurrencyPro is a single-file React 18 application loaded entirely from CDN.
No bundler, no build step, no server required.

### External dependencies

| Library | Version | CDN host |
|---|---|---|
| React + ReactDOM | 18.2.0 | cdnjs.cloudflare.com |
| Tabler Icons webfont | 2.44.0 | cdn.jsdelivr.net |
| Inter | 300-700 | fonts.googleapis.com |
| JetBrains Mono | 400-500 | fonts.googleapis.com |
| ExchangeRate-API | v4 free tier | api.exchangerate-api.com |

### State management

All state uses React built-in hooks: `useState`, `useEffect`, `useRef` and `useMemo`.
No Redux, no Zustand, no Context API.
State lives inside `Login` and `Converter`, coordinated by a single `user` string in `App`.

---

## Component Reference

### Page components

| Component | Description |
|---|---|
| `App` | Root. Holds `user` state. Renders `Login` when null, `Converter` otherwise. |
| `Login` | Animated globe hero, sign-in and create-account tabs with validation and guest access. Calls `onLogin(email)` on success. |
| `Converter` | Main dashboard. Fetches live rates on mount. Renders the white pill tab bar and five content panels. |

### UI components

| Component | Props | Description |
|---|---|---|
| `Drop` | `value`, `onChange`, `exclude`, `R` | Searchable dropdown with 160+ currencies. Closes on outside click. |
| `Spark` | `from`, `to`, `ht`, `wd`, `R` | Mini SVG sparkline. Green if trending up, red if down. Shape is seeded per pair. |
| `Chart` | `from`, `to`, `R` | 30-point hover-inspectable SVG chart with gradient fill, Y-axis labels and date row. |

### Visual and animation components

| Component | Description |
|---|---|
| `BG` | Fixed SVG wave paths with CSS animation, dot-grid overlay and radial emerald gradient. Renders at z-index 0. |
| `Globe` | Six currency badge symbols orbiting a pulsing sphere via CSS `@keyframes`. Radii range from 50 px to 92 px. |
| `Ticker` | 12-pair rates marquee using a doubled string for a seamless CSS loop. Updates once the live API responds. |
| `Confetti` | Twelve staggered particles launched upward on copy. Auto-dismissed after 1.8 seconds. |

---

## Key Utility Functions

```js
/**
 * Convert an amount from one currency to another.
 * Returns a formatted string or "" for invalid input.
 *
 * @param {string} amount  numeric value from the input field
 * @param {string} from    ISO 4217 source currency code
 * @param {string} to      ISO 4217 target currency code
 * @param {object} R       live rates map { code: rateVsUSD }
 * @returns {string}
 */
function cvt(amount, from, to, R) {}

/**
 * Get the formatted exchange rate between two currencies.
 * Values >= 1000 use comma formatting. Others use 4 decimal places.
 *
 * @param {string} from
 * @param {string} to
 * @param {object} R
 * @returns {string}
 */
function rate(from, to, R) {}

/**
 * Look up a currency object by ISO 4217 code.
 * Returns the USD entry as a fallback for unknown codes.
 *
 * @param {string} code
 * @returns {{ code, name, flag, sym }}
 */
function byCode(code) {}

/**
 * Seeded pseudo-random number generator.
 * Returns a closure () => number in [0, 1].
 * Produces deterministic sparkline shapes per currency pair.
 *
 * @param {number} seed
 * @returns {() => number}
 */
function seeded(seed) {}
```

```js
// Conversion formula used inside cvt()
const result = (parseFloat(amount) / R[from]) * R[to];

// Display formatting
result >= 1000
  ? result.toLocaleString("en-US", { maximumFractionDigits: 2 })
  : result.toFixed(4);
```

---

## How to Use the App

**Step 1: Sign in or continue as guest**

Enter any email and a password of at least 4 characters, then click Sign In.
Tap Continue as Guest to skip. All five features are available without an account.

**Step 2: Convert**

Click either currency dropdown and search by name or ISO code.
Type your amount in the From field and the result updates instantly.
Hit Swap to reverse direction. Tap a Quick Pair chip for one-click access to common pairs.
Click Copy to copy the result to your clipboard.

**Step 3: Rates**

The Rates tab lists every currency vs USD with flag, full name, current rate and sparkline.
Use the search box to filter the list. Click Go to load that pair into the converter.

**Step 4: Chart**

The Chart tab shows a 30-day indicative trend for the currently selected pair.
Hover anywhere on the line to see the exact rate for that day.
Four stat cards below show the current rate, inverse rate, 24-hour change and volatility.

**Step 5: Watchlist**

Six pre-configured pairs with rate, trend percentage and sparkline.
Click any row to open that pair directly in the converter.

**Step 6: History**

Every conversion is auto-saved with a timestamp as soon as the amount or currencies change.
Click any row to restore it in the converter. Tap Clear to delete all entries.

---

## Customisation

### Change the colour theme

All colours live in the `:root` block at the top of `index.html`.
Swap the three accent values to change the entire theme in one go.

```css
:root {
  /* Slate backgrounds */
  --s900: #0D1117;
  --s800: #161B22;
  --s700: #1C2330;
  --s600: #21262D;
  --s500: #30363D;

  /* Accent: swap these three to change the theme */
  --e500: #10B981;
  --e400: #34D399;
  --e300: #6EE7B7;
}

/* Ready-made preset alternatives */
/* Royal Blue   --e500:#3B82F6; --e400:#60A5FA; --e300:#93C5FD; */
/* Amber Gold   --e500:#F59E0B; --e400:#FBBF24; --e300:#FCD34D; */
/* Soft Violet  --e500:#8B5CF6; --e400:#A78BFA; --e300:#C4B5FD; */
/* Rose Pink    --e500:#F43F5E; --e400:#FB7185; --e300:#FDA4AF; */
```

### Add a new currency

```js
// 1. Append to CURR[] in the <script> tag
{ code: "XYZ", name: "Example Dollar", flag: "🏳️", sym: "$" }

// 2. Add a fallback rate to FALLBACK{}
FALLBACK["XYZ"] = 1.234; // means 1 USD = 1.234 XYZ
```

### Edit the watchlist pairs

```js
// Find const wl inside the Converter function
const wl = [
  ["USD", "EUR"],
  ["USD", "GBP"],
  ["EUR", "JPY"],
  ["USD", "PKR"],
  ["GBP", "INR"],
  ["USD", "AED"],
];

// Replace or add pairs using ["FROM_CODE", "TO_CODE"]
// Both codes must already exist in CURR[]
```

### Persist history across sessions

By default, history resets on page refresh. Add localStorage support like this:

```js
// Replace the hist useState inside Converter()
const [hist, setHist] = useState(() => {
  try {
    return JSON.parse(localStorage.getItem("cp_history") || "[]");
  } catch {
    return [];
  }
});

// Add this useEffect below the useState
useEffect(() => {
  localStorage.setItem("cp_history", JSON.stringify(hist));
}, [hist]);
```

### Deploy to a static host

| Host | Steps |
|---|---|
| GitHub Pages | Push `index.html` to repo root, go to Settings, enable Pages, choose branch main and folder / |
| Netlify | Drag and drop `index.html` onto the Netlify dashboard |
| Vercel | Run `vercel --prod` with no framework preset selected |
| Cloudflare Pages | Connect repo, leave the build command blank, set the output directory to `/` |

---

## FAQ

**Are the exchange rates real-time?**

On page load the app fetches live rates from ExchangeRate-API, which is free and requires no API key.
If the fetch fails or there is no internet connection, the app silently falls back to the static
reference values baked into the file. The status bar at the top of the converter tells you which
mode is currently active.

**Does the app store any user data?**

No data leaves the browser. There is no backend, no database and no analytics.
Conversion history lives in React state and resets on page refresh.
The login form is UI-only and credentials are never transmitted anywhere.

**Why does the chart look the same shape for the same pair every time?**

Charts use a seeded pseudo-random generator keyed to the currency pair code.
The shape is deterministic per pair but simulated, not real historical data.
Replace `seeded()` with a call to a real historical rates API for production use.

**The Copy button does not work. Why?**

Clipboard access requires a secure context such as `https://` or `localhost`.
Opening the file via `file://` blocks clipboard writes silently.
Run a local server as described in the Quick Start section.

**Can I use this in a production app?**

The UI is production-ready. Before going live, connect a real exchange rates API,
add server-side authentication if needed, persist history to localStorage or a backend,
and add React error boundaries around the main components.

**Can I deploy this to GitHub Pages, Netlify or Vercel?**

Yes. It is a single HTML file with no build step and no output directory configuration needed.
Just point the host at the root of the repository.

---

## License

MIT: free to use, modify and distribute. Attribution appreciated but not required.

---

<div align="center">

Made with care by **[Emaan Zehra](https://github.com/emaanzehra)**

[![GitHub](https://img.shields.io/badge/GitHub-emaanzehra-181717?style=flat-square&logo=github&labelColor=0D1117)](https://github.com/emaanzehra)
[![Repo](https://img.shields.io/badge/Repo-Currency--Pro-10B981?style=flat-square&logo=github&labelColor=0D1117)](https://github.com/emaanzehra/Currency-Pro)

Built with [React 18](https://react.dev) · [Tabler Icons](https://tabler.io/icons) · [Inter](https://rsms.me/inter/) · [JetBrains Mono](https://www.jetbrains.com/lp/mono/)

Zero build tooling · Zero backend · Zero npm install

</div>
