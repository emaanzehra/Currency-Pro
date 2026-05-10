<div align="center">

# 💱 CurrencyPro

### Professional real-time currency converter — 160+ currencies, live charts, watchlist & history

[![Version](https://img.shields.io/badge/version-1.0.0-10B981?style=flat-square&labelColor=0D1117)](https://github.com/emaanzehra/Currency-Pro)
[![React](https://img.shields.io/badge/React-18.2.0-61DAFB?style=flat-square&logo=react&labelColor=0D1117)](https://react.dev)
[![License](https://img.shields.io/badge/license-MIT-10B981?style=flat-square&labelColor=0D1117)](LICENSE)
[![No Build](https://img.shields.io/badge/build-none%20required-8B949E?style=flat-square&labelColor=0D1117)](#quick-start)
[![Live API](https://img.shields.io/badge/rates-live%20API%20%2B%20fallback-D29922?style=flat-square&labelColor=0D1117)](#architecture)
[![Currencies](https://img.shields.io/badge/currencies-160%2B-34D399?style=flat-square&labelColor=0D1117)](#supported-currencies)

A fully client-side currency converter with a professional dark UI, animated 3D globe hero,
live ticker tape, interactive 30-day charts, a watchlist, and auto-saved conversion history.

**No backend · No build tool · No npm install** — just open the HTML file.

[🔗 View Repository](https://github.com/emaanzehra/Currency-Pro) · [🚀 Quick Start](#quick-start) · [📖 How to Use](#how-to-use-the-app) · [🎨 Customise](#customisation)

</div>

---

## 📋 Table of Contents

1. [✨ Features](#features)
2. [🌍 Supported Currencies](#supported-currencies)
3. [🚀 Quick Start](#quick-start)
4. [🏗️ Architecture](#architecture)
5. [🧩 Component Reference](#component-reference)
6. [🔧 Key Utility Functions](#key-utility-functions)
7. [📱 How to Use the App](#how-to-use-the-app)
8. [🎨 Customisation](#customisation)
9. [❓ FAQ](#faq)
10. [📄 License](#license)

---

## ✨ Features

| Feature | Description |
|---|---|
| **Live converter** | Instant conversion with animated result flip, one-click copy and confetti burst |
| **Interactive 30-day chart** | Hover-to-inspect SVG chart per pair with gradient fill, grid lines and date labels |
| **Full rates table** | 160+ currencies with country flags, USD rate, sparklines and quick-convert shortcut |
| **Watchlist** | Six tracked pairs with live trend direction, % change and sparkline per pair |
| **Conversion history** | Auto-saves every conversion with timestamp — tap any entry to repeat it |
| **3D animated globe** | CSS-orbiting currency symbols on a pulsing sphere with animated wave background |
| **Live API rates** | Fetches from ExchangeRate-API on load — silently falls back to static rates offline |
| **Auth flow** | Sign-in / Create Account tabs with full validation, show/hide password, guest access |
| **Smart search** | Search 160+ currencies by name or ISO code across all dropdowns |
| **Responsive layout** | Works on desktop, tablet and mobile — tab bar scrolls horizontally on small screens |
| **Slate & Emerald theme** | Professional dark base with rich emerald accents, fully customisable via CSS variables |

---

## 🌍 Supported Currencies

160+ world currencies across every region — Africa, Asia, Americas, Europe, Middle East and Oceania.
Every entry includes a country flag emoji, ISO 4217 code, full name and currency symbol.

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

> **160+ currencies total.** Add new ones by appending an object to the `CURR` array in `index.html`.

---

## 🚀 Quick Start

### Prerequisites

| Requirement | Details |
|---|---|
| Browser | Chrome 90+, Firefox 88+, Safari 14+, Edge 90+ |
| Node.js | v18+ — only needed if you want a local dev server |
| Internet | Required for CDN assets (React, Icons, Fonts) and live rates |
| Backend | None — fully client-side |

### Run instantly (single file)

```bash
git clone https://github.com/emaanzehra/Currency-Pro.git
cd Currency-Pro
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

### With a local server (recommended for clipboard support)

```bash
# Option 1 — Node.js
npx serve .
# → http://localhost:3000

# Option 2 — Python
python -m http.server 8080
# → http://localhost:8080

# Option 3 — VS Code
# Install "Live Server" → right-click index.html → Open with Live Server
```

> ⚠️ **Note:** Do not open via `file://` if you need the clipboard **Copy** feature.
> Browsers block clipboard access on `file://` origins. Use a local server instead.

---

## 🏗️ Architecture
┌─────────────────────────────────────────────────────────────────┐
│                         index.html                              │
│                                                                 │
│  ┌─────────────┐  ┌──────────────────┐  ┌───────────────────┐  │
│  │   <style>   │  │    <link> CDN    │  │   <script> CDN   │  │
│  │ CSS vars    │  │ Tabler Icons     │  │  React 18 UMD    │  │
│  │ @keyframes  │  │ Inter font       │  │  ReactDOM 18 UMD │  │
│  │ Slate theme │  │ JetBrains Mono   │  │                  │  │
│  └─────────────┘  └──────────────────┘  └───────────────────┘  │
│                                                                 │
│  ┌──────────────────────── <script> App ───────────────────┐   │
│  │                                                          │   │
│  │  DATA LAYER                                              │   │
│  │  ├── FALLBACK{}     Static rates (160+ currencies)      │   │
│  │  ├── CURR[]         Currency objects {code,name,flag,   │   │
│  │  │                  sym} — 160+ entries                  │   │
│  │  ├── cvt()          Convert amount → formatted string    │   │
│  │  ├── rate()         Get rate between two currencies      │   │
│  │  ├── byCode()       Look up currency by ISO code         │   │
│  │  └── seeded()       Deterministic PRNG for chart shapes  │   │
│  │                                                          │   │
│  │  VISUAL LAYER                                            │   │
│  │  ├── BG             Fixed wave + grid background         │   │
│  │  ├── Ticker         Scrolling 12-pair live rates bar     │   │
│  │  ├── Globe          3D CSS-orbiting currency symbols     │   │
│  │  ├── Spark          Mini SVG sparkline per pair          │   │
│  │  ├── Chart          30-point hover-inspectable SVG chart │   │
│  │  ├── Drop           Searchable currency dropdown         │   │
│  │  └── Confetti       Copy-confirmation particle burst     │   │
│  │                                                          │   │
│  │  PAGE LAYER                                              │   │
│  │  ├── Login          Globe hero + auth form               │   │
│  │  ├── Converter      White pill tabs + 5 panels           │   │
│  │  │   ├── Convert    Amount input, swap, result           │   │
│  │  │   ├── Rates      Full 160+ rate table + search        │   │
│  │  │   ├── Chart      30-day trend + stat cards            │   │
│  │  │   ├── Watchlist  6 tracked pairs + sparklines         │   │
│  │  │   └── History    Auto-saved conversions + repeat      │   │
│  │  └── App            Root — toggles Login ↔ Converter     │   │
│  │                                                          │   │
│  │  API LAYER (on mount)                                    │   │
│  │  └── fetch(ExchangeRate-API) → live rates                │   │
│  │      └── catch() → FALLBACK static rates                 │   │
│  └──────────────────────────────────────────────────────────┘   │
│                                                                 │
│  ReactDOM.createRoot('#root').render(<App />)                   │
└─────────────────────────────────────────────────────────────────┘
### External dependencies — CDN only, nothing to install

| Library | Version | CDN host |
|---|---|---|
| React + ReactDOM | 18.2.0 | cdnjs.cloudflare.com |
| Tabler Icons webfont | 2.44.0 | cdn.jsdelivr.net |
| Inter | 300–700 | fonts.googleapis.com |
| JetBrains Mono | 400–500 | fonts.googleapis.com |
| ExchangeRate-API | v4 (free) | api.exchangerate-api.com |

### State management

All state uses React built-in hooks (`useState`, `useEffect`, `useRef`, `useMemo`).
No Redux, no Zustand, no Context API. State lives entirely inside `Login` and `Converter`,
coordinated by a single `user` string in the root `App` component.

---

## 🧩 Component Reference

### Page components

| Component | Description |
|---|---|
| `App` | Root. Holds `user` state. Renders `Login` when null, `Converter` otherwise. |
| `Login` | Animated globe hero, sign-in / create-account tabs with validation, guest access. Calls `onLogin(email)`. |
| `Converter` | Main dashboard. Fetches live rates on mount. White pill tab bar with five panels. |

### UI components

| Component | Props | Description |
|---|---|---|
| `Drop` | `value`, `onChange`, `exclude`, `R` | Searchable dropdown — 160+ currencies, closes on outside click |
| `Spark` | `from`, `to`, `ht`, `wd`, `R` | Mini SVG sparkline. Emerald if up, red if down. Seeded per pair |
| `Chart` | `from`, `to`, `R` | 30-point hover-inspectable SVG chart with gradient fill and dates |

### Visual / animation components

| Component | Description |
|---|---|
| `BG` | Fixed SVG wave paths (CSS animated), dot-grid overlay, radial emerald gradient |
| `Globe` | Six currency badges orbiting via CSS `@keyframes`. Radii: 50–92 px. Durations: 3.8–6.5 s |
| `Ticker` | 12-pair rates marquee. Doubled string for seamless CSS loop. Shows live rates once API loads |
| `Confetti` | 12 staggered particles launched upward on Copy. Auto-dismissed after 1.8 s |

---

## 🔧 Key Utility Functions

```js
/**
 * Convert an amount from one currency to another.
 * @param {string} amount - Numeric string from the input field
 * @param {string} from   - ISO 4217 source currency code
 * @param {string} to     - ISO 4217 target currency code
 * @param {object} R      - Live rates object { code: rateVsUSD }
 * @returns {string}      - Formatted result or "" for invalid input
 */
function cvt(amount, from, to, R) { … }

/**
 * Get the formatted exchange rate between two currencies.
 * Values >= 1000 are comma-formatted; others are fixed to 4 decimal places.
 */
function rate(from, to, R) { … }

/**
 * Look up a currency object by ISO 4217 code. Falls back to USD.
 * @returns {{ code, name, flag, sym }}
 */
function byCode(code) { … }

/**
 * Seeded pseudo-random number generator.
 * Produces deterministic, reproducible sparkline shapes per pair.
 * @returns {() => number}
 */
function seeded(seed) { … }
```

```js
// Conversion formula
const result = (parseFloat(amount) / R[from]) * R[to];

// Display formatting
result >= 1000
  ? result.toLocaleString("en-US", { maximumFractionDigits: 2 })
  : result.toFixed(4);
```

---

## 📱 How to Use the App

**Step 1 — Sign in or continue as guest**
Enter any email and a password of at least 4 characters, then click **Sign In**.
Or tap **Continue as Guest** — all five features are available without an account.

**Step 2 — Convert**
Click either currency dropdown and search by name or ISO code. Type your amount in the
**From** field — the result updates instantly. Hit **Swap** to reverse direction.
Tap a **Quick Pair** chip for one-click access. Click **Copy** to copy the result.

**Step 3 — Rates**
The **Rates** tab lists every currency vs USD with flag, full name, rate and sparkline.
Use the search box to filter. Click **Go** to load that pair into the converter.

**Step 4 — Chart**
The **Chart** tab shows a 30-day indicative trend. Hover anywhere on the line to see the
exact rate in a tooltip. Four stat cards show: current rate, inverse, 24h change and volatility.

**Step 5 — Watchlist**
Six pre-configured pairs with rate, trend % and sparkline. Click any row to open that
pair directly in the converter.

**Step 6 — History**
Every conversion is auto-saved with a timestamp. Click any row to restore it. Tap **Clear** to delete all entries.

---

## 🎨 Customisation

### Change the colour theme

```css
:root {
  /* Slate backgrounds — keep these */
  --s900: #0D1117;  --s800: #161B22;  --s700: #1C2330;
  --s600: #21262D;  --s500: #30363D;

  /* Accent — swap these three to change the entire theme */
  --e500: #10B981;  /* main accent   */
  --e400: #34D399;  /* lighter shade */
  --e300: #6EE7B7;  /* highlight     */
}

/* Ready-made presets — uncomment one block to apply */
/* Royal Blue  */ /* --e500:#3B82F6; --e400:#60A5FA; --e300:#93C5FD; */
/* Amber Gold  */ /* --e500:#F59E0B; --e400:#FBBF24; --e300:#FCD34D; */
/* Soft Violet */ /* --e500:#8B5CF6; --e400:#A78BFA; --e300:#C4B5FD; */
/* Rose Pink   */ /* --e500:#F43F5E; --e400:#FB7185; --e300:#FDA4AF; */
```

### Add a new currency

```js
// 1. Append to CURR[] in the <script> tag
{ code: "XYZ", name: "Example Dollar", flag: "🏳️", sym: "$" }

// 2. Add the rate to FALLBACK{}
FALLBACK["XYZ"] = 1.234; // 1 USD = 1.234 XYZ
```

### Edit the watchlist pairs

```js
// Find const wl inside Converter()
const wl = [
  ["USD", "EUR"],
  ["USD", "GBP"],
  ["EUR", "JPY"],
  ["USD", "PKR"],   // ← add your pair as ["FROM", "TO"]
  ["GBP", "INR"],
  ["USD", "AED"],
];
// Both codes must exist in CURR[]
```

### Persist history across sessions

```js
// Replace the hist useState inside Converter()
const [hist, setHist] = useState(() => {
  try { return JSON.parse(localStorage.getItem("cp_history") || "[]"); }
  catch { return []; }
});

// Add this useEffect
useEffect(() => {
  localStorage.setItem("cp_history", JSON.stringify(hist));
}, [hist]);
```

### Deploy to a static host

| Host | Steps |
|---|---|
| **GitHub Pages** | Push `index.html` → Settings → Pages → branch: main, folder: / |
| **Netlify** | Drag-and-drop `index.html` onto the Netlify dashboard |
| **Vercel** | `vercel --prod` with no framework preset selected |
| **Cloudflare Pages** | Connect repo, build command blank, output dir `/` |

---

## ❓ FAQ

<details>
<summary><strong>Are the exchange rates real-time?</strong></summary>
<br>
On page load, the app fetches live rates from ExchangeRate-API (free, no API key needed).
If the fetch fails or there is no internet, it silently falls back to static reference values.
The status bar at the top of the converter shows which mode is active.
</details>

<details>
<summary><strong>Does the app store any user data?</strong></summary>
<br>
No data leaves the browser. There is no backend, no database, and no analytics.
Conversion history lives in React state and resets on page refresh. The login form is
UI-only — credentials are never transmitted anywhere.
</details>

<details>
<summary><strong>Why does the chart look the same for a pair every time?</strong></summary>
<br>
Charts use a seeded pseudo-random generator keyed to the currency pair code — deterministic
per pair but simulated, not real historical data. Replace <code>seeded()</code> with a real
historical API call for production use.
</details>

<details>
<summary><strong>The Copy button doesn't work — why?</strong></summary>
<br>
Clipboard access requires a secure context (<code>https://</code> or <code>localhost</code>).
Opening via <code>file://</code> blocks clipboard writes silently. Run a local server as
shown in Quick Start.
</details>

<details>
<summary><strong>Can I use this in a production app?</strong></summary>
<br>
The UI is production-ready. Before going live: (1) verify the live API is connected,
(2) add real server-side authentication if needed, (3) persist history to localStorage
or a backend, (4) add React error boundaries around the main components.
</details>

<details>
<summary><strong>Can I deploy to GitHub Pages / Netlify / Vercel?</strong></summary>
<br>
Yes — it is a single HTML file with no build step. No build command, no output directory
configuration. Just point the host at the root of the repository.
</details>

---

## 📁 Project Structure

Currency-Pro/
├── index.html    ← entire application (~700 lines, single file)
└── README.md     ← this file

---

## 📄 License

MIT — free to use, modify and distribute. Attribution appreciated but not required.

---

<div align="center">

**Made with ❤️ by [Emaan Zehra](https://github.com/emaanzehra)**

[![GitHub](https://img.shields.io/badge/GitHub-emaanzehra-181717?style=flat-square&logo=github)](https://github.com/emaanzehra)
[![Repo](https://img.shields.io/badge/Repo-Currency--Pro-10B981?style=flat-square&logo=github)](https://github.com/emaanzehra/Currency-Pro)

*Built with [React 18](https://react.dev) · [Tabler Icons](https://tabler.io/icons) · [Inter](https://rsms.me/inter/) · [JetBrains Mono](https://www.jetbrains.com/lp/mono/)*

*Zero build tooling · Zero backend · Zero npm install*

</div>


CurrencyPro is a **single-file React 18 application** loaded entirely from CDN.
No bundler, no build step, no server required.
