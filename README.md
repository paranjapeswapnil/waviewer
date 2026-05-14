# WhatsApp Chat Viewer

A fully offline-capable PWA that renders WhatsApp `.txt` exports in an
authentic chat interface. Installs to your iPhone home screen from Safari.

---

## Deploy to GitHub Pages (5 minutes)

### 1. Create a GitHub repo

1. Go to [github.com/new](https://github.com/new)
2. Name it anything, e.g. `wa-viewer`
3. Set it to **Public** (required for free GitHub Pages)
4. Click **Create repository**

### 2. Upload the files

**Option A — GitHub web UI (no git needed)**
1. On your new repo page, click **"uploading an existing file"**
2. Drag the entire contents of this folder into the upload area
   *(enable hidden files in Finder with `Cmd+Shift+.` so `.nojekyll` and `.github/` are included)*
3. Click **Commit changes**

**Option B — git CLI**
```bash
cd wa-pwa
git init
git add .
git commit -m "initial"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/wa-viewer.git
git push -u origin main
```

### 3. Enable GitHub Pages

1. In your repo go to **Settings → Pages**
2. Under *Source* select **GitHub Actions**
3. Save — the workflow in `.github/workflows/deploy.yml` runs automatically

### 4. Get your URL

After ~60 seconds your app is live at:
```
https://YOUR_USERNAME.github.io/wa-viewer/
```
GitHub shows the exact URL under **Settings → Pages** once deployed.

---

## Install on iPhone

1. Open your GitHub Pages URL in **Safari** (not Chrome)
2. Tap the **Share** button → **"Add to Home Screen"**
3. Tap **Add**

The app installs with a green icon and runs fullscreen like a native app.
It caches itself on first load and works fully offline after that.

---

## Opening a chat export

**Directly from WhatsApp:**
1. Open a chat → tap the name at the top → **Export Chat** → Without Media
2. In the share sheet tap **"WA Viewer"** and it opens straight in the app

**From the Files app:**
1. Tap **Choose .txt file** inside the app
2. Navigate to your exported file and tap it

---

## Features

- Parses both Android and iOS WhatsApp export formats
- 1-on-1 and group chats with colour-coded sender names
- Search messages
- Jump to any date (grouped by month)
- Dark / light mode toggle
- Media placeholders (photo, video, audio, document, sticker)
- Fully offline after first load
- 100% local — no data ever leaves your device

---

## File structure

```
wa-pwa/
├── .nojekyll                      ← tells GitHub not to run Jekyll
├── _config.yml                    ← minimal Jekyll config
├── .github/
│   └── workflows/
│       └── deploy.yml             ← auto-deploys on every push to main
├── index.html                     ← the full app
├── manifest.json                  ← PWA metadata (name, icons, theme colour)
├── sw.js                          ← service worker (offline cache)
└── icons/
    ├── apple-touch-icon.png       ← iOS home screen icon
    ├── icon-152.png
    ├── icon-180.png
    ├── icon-192.png
    ├── icon-512.png
    └── ...
```

---

## Updating the app

Push any change to `main` and GitHub Actions redeploys automatically.
To force users to get a fresh cache, bump the version string in `sw.js`:
`const CACHE = 'wa-viewer-v2';`
