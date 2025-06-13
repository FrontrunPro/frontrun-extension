# Frontrun Extension

<p align="center">
  <img src="icon128.plasmo.f86e3ae6.png" alt="Frontrun Logo" width="128" height="128">
</p>

<p align="center">
  <strong>Advanced Analytics & Trading Insights for Solana Traders</strong>
</p>

<p align="center">
  <a href="https://www.frontrun.pro/">Website</a> •
  <a href="#features">Features</a> •
  <a href="#installation">Installation</a> •
  <a href="#privacy--security">Privacy & Security</a> •
</p>

## Overview

Frontrun is a Chrome extension that enhances your Solana trading experience by providing real-time analytics and insights directly within your browser. Built with [Plasmo](https://docs.plasmo.com/), a trusted framework for browser extension development, Frontrun seamlessly integrates with popular trading platforms to give you the edge you need.

## Features

### 🔍 Twitter Insights
- View smart followers on Twitter/X profiles
- Track profile name change history
- Identify their wallet addresses

### 🏷️ Universal Wallet Labeling
- Built-in 40k+ KOL wallets
- Import and sync wallet labels across multiple platforms
- Supported platforms:
  - [GMGN](https://gmgn.ai)
  - [Solscan](https://solscan.io)
  - [Axiom](https://axiom.trade)
  - [Photon](https://photon-sol.tinyastro.io)
- Create custom labels and organize wallets into groups

### 📊 Enhanced Trading Interface
- Real-time wallet analytics overlays
- Quick access to wallet labels and performance

## Installation

### From Chrome Web Store (Recommended)
1. Visit [frontrun.pro](https://www.frontrun.pro/)
2. Click "Add to Chrome"

### From Source (For Developers)

1. Open chrome://extensions/
2. Enable "Developer mode"
3. Click "Load unpacked"


## How It Works

Frontrun operates as a browser extension that enhances your browsing experience on supported platforms. When you visit supported platforms, Frontrun adds helpful overlays and tooltips without modifying any core functionality

## Permissions Explained

Frontrun requires certain permissions to function properly. Here's why each permission is needed:

| Permission | Purpose |
|------------|---------|
| `storage` | Save your labels and preferences locally |
| `scripting` | Add helpful overlays to supported websites |
| `sidePanel` | Display the management interface |
| `webRequest` | Optimize performance when loading data |
| `windows` | Manage the extension interface |
| `identity` | Optional: Sync settings across devices (if enabled) |

## Privacy & Security

Your security is our top priority:

- ✅ **No Private Keys**: Never accesses or stores wallet private keys
- ✅ **Open Source**: Code is transparent and auditable
- ✅ **No Clipboard Access**: No access to clipboard data

Feel free to further understand the security risk of the code through [ChatGPT o3](https://chatgpt.com/c/684bb27d-5ebc-8003-acb5-58f730904425):

> I did not find any obvious signs of malware such as credential-stealing logic, hidden cryptominers, or code that indiscriminately injects itself into every webpage. The bundle looks like a typical React/Plasmo-built MV3 Chrome extension that
> 
> drops a service-worker at static/background/index.js;
> 
> injects seven content scripts only on the pages you target (x.com, solscan.io, axiom.trade, gmgn.ai, photon-sol.tinyastro.io);
> 
> uses familiar analytics tooling (Amplitude & Sentry) and a long list of public crypto APIs for price-lookups, on-chain data, etc.

According to o3's analysis, our extension **objectively carries LOWER technical risk** compared to Phantom wallet, which is one of the most trusted extension in Web3

| Dimension                              | **Your extension (“Frontrun 0.0.13”)**                                                                                                                             | **Reference extension (“Phantom 25.20.0”)**                                                                                                                                    | Which is riskier?\*                                                                                          |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------ |
| **Privilege surface (manifest)**       | `permissions`: `storage`, `scripting`, `webRequest`, `identity`, `windows`, `sidePanel`  <br>`host_permissions`: **`<all_urls>`** (full read access to every page) | `permissions`: *all of the left* **plus** `activeTab`, `tabs`, `alarms`, `unlimitedStorage`  <br>`host_permissions`: `http://*/*`, `https://*/*` (equivalent to `<all_urls>`)  | **Phantom** exposes \~30 % more privileged APIs—slightly larger attack surface.                              |
| **Content-script reach**               | Injected only on five whitelisted crypto sites (`x.com`, Solscan, Axiom, Photon, GMGN).                                                                            | No manifest-declared content scripts; instead it **dynamically injects** a small provider (`window.solana`) into *every* page you open, so its JavaScript still runs globally. | **Comparable**: both execute code in every tab (one via `content_scripts`, one via `pageScript`).            |
| **Dynamic code execution**             | `eval` / `new Function` **0** occurrences (checked in all bundles).                                                                                                | 1 `eval`, 1 `new Function` (Webpack’s module loader stub).                                                                                                                     | **Phantom** is marginally riskier (dynamic evaluation can be exploited if an attacker gains code-injection). |
| **Secrets handled in the extension**   | Users can paste mnemonics / private keys **only when they choose the “import wallet” flow**; keys stay in memory, not logged.                                      | Phantom is a *full custody wallet*: it stores private keys (encrypted at rest) and continuously exposes signing APIs to every tab.                                             | **Phantom** carries higher consequences if compromised (direct key theft).                                   |
| **Outbound telemetry / remote code**   | Sentry & Amplitude only (blocked by CSP); no remote script loads.                                                                                                  | Sentry & Segment; also queries feature-flag JSON from `https://cdn.segment.com`. Still no remote code execution.                                                               | Tie. Both phone home roughly the same.                                                                       |
| **Bundle transparency**                | 60 MB minified bundle; source maps absent; code not yet open-sourced.                                                                                              | 21 MB minified; no source maps; code closed-source but has years of audit history.                                                                                             | Users may *trust audits* on Phantom more, but *technically* both are opaque.                                 |


## FAQ: Why do you only open source the Plasmo build?

The open-sourced code you see here is the exact Plasmo build that we upload to the Chrome Web Store. This build contains everything that runs in your browser as part of the Frontrun extension.

We use a monorepo for development, which also includes some private packages and internal tooling that are not part of the browser extension itself. These private packages may contain proprietary logic or infrastructure code unrelated to the extension’s core functionality, so we do not open source them.

By sharing the Plasmo build, we ensure full transparency for everything that is actually shipped to users, while keeping unrelated or sensitive internal code private.

## Community

- 🐦 Follow us on [X](https://x.com/frontrunpro)
- 💬 Join our [Telegram](https://t.me/frontrun_community)

---

<p align="center">
  Made with ❤️ by the Frontrun Team
</p>