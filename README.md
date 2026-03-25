# Maxroll → pobb.in

**A Chrome extension for Path of Exile players.**

Detects any `maxroll.gg/poe/pob/` link, silently scrapes the Path of Building code in the background, and automatically redirects to pobb.in with the code pre-filled and submitted — turning a 3-step manual process into a single click.

![Promo](https://raw.githubusercontent.com/wounded-deer-meliorne/maxroll-to-pobb.in/main/promo_1200x800.png)

---

## How it works

1. You click any `maxroll.gg/poe/pob/*` link
2. A loading screen covers the page instantly — you never see maxroll load
3. The extension scrapes the POB code from the page in the background
4. The tab redirects to `pobb.in` with the code auto-filled and the Create button clicked
5. Your shareable build link is ready

---

## Installation

### From the Chrome Web Store
*Coming soon.*

### Manual (Developer Mode)
1. Download or clone this repo
2. Go to `chrome://extensions` in Chrome
3. Enable **Developer mode** (top-right toggle)
4. Click **Load unpacked** and select this folder

---

## Files

| File | Purpose |
|------|---------|
| `manifest.json` | Extension config, permissions, content script rules |
| `background.js` | Stores POB code in local storage, triggers tab redirect |
| `content_maxroll.js` | Scrapes POB code from maxroll.gg using MutationObserver + polling |
| `content_pobb.js` | Injects POB code into pobb.in and auto-clicks Create |
| `icon128.png` | Extension icon |

---

## Troubleshooting

### POB code not found
If the extension fails to scrape, open DevTools (F12) on a `maxroll.gg/poe/pob/*` page and check the Console for `[maxroll-to-pobb]` log lines. The confirmed selector is `textarea.poe-textarea` — if Maxroll changes their markup, update this in `content_maxroll.js`.

### pobb.in input not filling
Open DevTools on `pobb.in` and check the Console. The extension targets `textarea[aria-label="Path of Building buildcode"]`. If pobb.in updates their markup, update the selector in `content_pobb.js`.

---

## Contributing

PRs welcome. If Maxroll or pobb.in update their DOM and break the selectors, please open an issue with the new element structure and I'll patch it quickly.

---

## Disclaimer

This extension is not affiliated with Maxroll, pobb.in, or Grinding Gear Games. Path of Exile is a trademark of Grinding Gear Games.

---

## License

[MIT](LICENSE)
