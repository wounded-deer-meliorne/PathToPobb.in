# PathToPobb.in

**A Path of Exile browser extension for Chrome and Firefox.**

Automatically redirects PoE build links from Maxroll and Mobalytics to pobb.in — with the Path of Building code pre-filled and submitted instantly.

![Promo](https://raw.githubusercontent.com/wounded-deer-meliorne/PathToPobb.in/main/promo_1200x800.png)

---

## Supported sources

| Site | URL pattern | How it works |
|------|-------------|--------------|
| Maxroll (POB page) | `maxroll.gg/poe/pob/*` | Scrapes POB code from the page |
| Maxroll (Build guide) | `maxroll.gg/poe/build-guides/*` | Finds the PoB Link button and follows it |
| Mobalytics | `mobalytics.gg/poe/builds/*` | Reads the pobb.in URL directly from the page |

---

## How it works

1. You click any supported build link
2. A loading screen covers the page — you never see the source site load
3. The extension grabs the POB code or pobb.in URL silently in the background
4. The tab redirects to pobb.in with the code auto-filled and Create clicked
5. Your shareable build link is ready

---

## Installation

### Chrome

**From the Chrome Web Store**
*Coming soon*

**Manual install (Developer Mode)**
1. Download the latest release zip from the [Releases](https://github.com/wounded-deer-meliorne/PathToPobb.in/releases) page and unzip it
2. Open Chrome and go to `chrome://extensions` in the address bar
3. Enable **Developer mode** using the toggle in the top-right corner
4. Click **Load unpacked**
5. Navigate into the unzipped folder and select the `chrome/` folder
6. The extension is now active — you'll see the PathToPobb.in icon in your toolbar

---

### Firefox

**From Firefox Add-ons**
*Coming soon*

**Temporary install (for testing)**
1. Download the latest release zip from the [Releases](https://github.com/wounded-deer-meliorne/PathToPobb.in/releases) page and unzip it
2. Open Firefox and go to `about:debugging` in the address bar
3. Click **This Firefox** in the left sidebar
4. Click **Load Temporary Add-on**
5. Navigate into the unzipped folder, open the `firefox/` folder, and select `manifest.json`
6. The extension is now active — note that it will need to be reloaded each time Firefox restarts

**Permanent Firefox install**
For a permanent install on regular Firefox, the extension needs to be signed by Mozilla. A signed version will be available on the Firefox Add-ons store once submitted.

---

## Repository structure

```
PathToPobb.in/
├── chrome/               Chrome extension (Manifest V3)
│   ├── manifest.json
│   ├── background.js
│   ├── content_maxroll.js
│   ├── content_buildguide.js
│   ├── content_mobalytics.js
│   ├── content_pobb.js
│   └── icon128.png
├── firefox/              Firefox extension (Manifest V2)
│   ├── manifest.json
│   ├── background.js
│   ├── content_maxroll.js
│   ├── content_buildguide.js
│   ├── content_mobalytics.js
│   ├── content_pobb.js
│   └── icon128.png
├── README.md
├── LICENSE
└── .gitignore
```

The content scripts are functionally identical between browsers. The only differences are `manifest.json` (MV3 vs MV2) and `background.js` (`chrome.*` vs `browser.*` API).

---

## Files

| File | Purpose |
|------|---------|
| `manifest.json` | Extension config, permissions, content script rules |
| `background.js` | Stores POB code in local storage, triggers tab redirect |
| `content_maxroll.js` | Scrapes POB code from maxroll.gg/poe/pob/* |
| `content_buildguide.js` | Finds PoB Link button on maxroll.gg build guides |
| `content_mobalytics.js` | Reads pobb.in URL from mobalytics.gg build pages |
| `content_pobb.js` | Injects POB code into pobb.in and auto-clicks Create |
| `icon128.png` | Extension icon |

---

## Troubleshooting

Open DevTools (F12) on any supported page and check the Console for `[PathToPobb.in]` log lines. If a build page shows the "No POB link found" error, the build likely doesn't have a POB link available on that page.

---

## Contributing

PRs welcome. If any source site updates their DOM and breaks the selectors, open an issue with the new element structure.

---

## Disclaimer

Not affiliated with Maxroll, Mobalytics, pobb.in, or Grinding Gear Games. Path of Exile is a trademark of Grinding Gear Games.

---

## License

[MIT](LICENSE)

---

## Support

If this saved you some time, feel free to buy me a coffee — it helps keep the project going.

☕ [ko-fi.com/woundeddeermeliorne](https://ko-fi.com/woundeddeermeliorne)
