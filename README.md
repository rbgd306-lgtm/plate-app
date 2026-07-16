# Plate — turn this into a phone app (free, ~10 minutes)

This is now a **PWA (Progressive Web App)**. You host it once, then anyone
(including you) can "Add to Home Screen" on iPhone or Android and it opens
full-screen like a real app — no App Store, no Google Play, no fees.

## What changed from your original file
- `window.storage` → replaced with `localStorage` (works outside Claude.ai)
- Added a ⚙️ settings button so you can paste in your **own Anthropic API key**
  (needed because the app now calls Claude's API directly, without Claude.ai's
  built-in proxy)
- Added `manifest.json` + `sw.js` so it installs like an app and works offline
  for the UI (the AI calls still need internet)

## Step 1 — Get an Anthropic API key
Go to https://console.anthropic.com → API Keys → Create Key.
Keep this page open, you'll paste it into the app after it's live.

⚠️ Note: this key will live in the app's code path exposed to whoever uses
your phone/browser (it's stored in `localStorage`, only on your device — not
shared with anyone else, but don't share this app link publicly with your key
already saved in it).

## Step 2 — Host it for free with GitHub Pages
You already have a GitHub repo (`rbgd306-lgtm/Calories`). Easiest is a **new
folder** in that repo, or a **new repo** — either works. Steps for a fresh repo:

1. On GitHub, create a new repository (e.g. `plate-app`)
2. Click **"Add file" → "Upload files"**
3. Drag in all 5 files from this folder: `index.html`, `manifest.json`,
   `sw.js`, `icon-192.png`, `icon-512.png`
4. Commit directly to `main`
5. Go to **Settings → Pages** (left sidebar)
6. Under "Source", choose **Deploy from a branch** → branch `main` → folder `/ (root)` → Save
7. Wait ~1 minute, then GitHub shows you a live URL like:
   `https://rbgd306-lgtm.github.io/plate-app/`

## Step 3 — Install on your phone
Open that URL on your phone's browser.

**iPhone (Safari):** tap the Share icon → "Add to Home Screen"
**Android (Chrome):** tap the ⋮ menu → "Add to Home Screen" / "Install app"

## Step 4 — Add your API key
Open the app from your home screen, tap the ⚙️ icon at the top, paste your
API key. It's saved on your device — you won't need to enter it again.

That's it — you now have a real installed app, for €0, with no app store
review process.

## If you'd rather have a "real" native app later
This same file can be wrapped into an actual iOS/Android build using Expo +
`react-native-webview` and the EAS workflow you were already setting up —
that gets you a proper App Store / Play Store listing, but costs $99/year
for an Apple Developer account (Android-only stays free). Happy to help with
that path too if you want to go further down the line.
