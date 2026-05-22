# ¡Wepa Run! — itch.io Deployment Guide

## What's in the ZIP

```
wepa-run.zip
└── index.html   (364 KB uncompressed, 148 KB compressed)
```

Single self-contained HTML file. The only external dependency is the
**Press Start 2P** font loaded from Google Fonts — itch.io's CDN and
iframe sandbox both allow this without any extra configuration.

---

## Step-by-Step Upload

### 1. Create the game page

1. Go to **https://itch.io/game/new**
2. Fill in the fields below (see "Suggested Page Settings")

### 2. Upload the file

1. Under **Uploads**, click **Upload files**
2. Select `wepa-run.zip` from this folder
3. In the file row that appears:
   - Check **This file will be played in the browser**
   - Leave the other toggles (Android/Windows/etc.) unchecked

### 3. Set embed dimensions

Under **Embed options** (appears after you mark the file as browser-playable):

| Setting | Value |
|---|---|
| Viewport width | `480` |
| Viewport height | `700` |
| Mobile friendly | ✅ checked |
| Fullscreen button | ✅ checked |
| Scrollbars | ☐ unchecked |

> Why 480×700? The canvas is 480×620 and the HUD adds ~44px. 700px gives
> breathing room and keeps the arcade carousel's fixed nav dots visible.
> On mobile the game auto-scales to fill the screen via `100dvh`.

### 4. Save & publish

Click **Save & view page** to preview, then **Publish** when ready.

---

## Suggested Page Settings

### Basic info

| Field | Value |
|---|---|
| **Title** | ¡Wepa Run! |
| **Short description** | 9 Puerto Rican arcade games — dodge guaguas, serve piraguas, and more. |
| **Classification** | Games |
| **Kind of project** | HTML |
| **Release status** | In development *(or Released if launching Guagua Rush only)* |

### Description (paste into the editor)

```
¡WEPA RUN! — Puerto Rican Arcade Collection

🚌 GUAGUA RUSH — Available NOW!
Dodge traffic, catch guaguas, rack up distance. Endless runner with 
power-ups, flans to collect, and a full high-score board.

🕹️ 8 MORE GAMES — Coming Soon
Pedro's Piragua Taxi, Piragua Snake, Abuela's Flan Defense, 
Dominoes Boricua, Boxing Legends, La Familia Dinner, 
Coquí Hop, La Placita Party.

CONTROLS
• Tap / Click  — jump & interact
• Arrow keys   — navigate menus
• Swipe        — carousel navigation (mobile)
• Escape       — back / pause

No downloads. No accounts. Pure retro fun. ¡Wepa!
```

### Tags

```
arcade, endless-runner, mobile, puerto-rico, html5, retro, pixel-art, 
one-button, casual, singleplayer
```

### Genre

`Action` (primary) — optionally also tag `Platformer`

### Pricing

- **Free** recommended for launch (builds audience)
- Add a "Name your own price" option with a $0 floor if you want to
  accept optional tips — itch.io keeps 10% and you keep the rest

### Cover image / screenshots

- Recommended cover: **315×250 px** (itch.io card size)
- Screenshots: at least **2** at **1280×720** or **640×480**
- Capture: the arcade carousel, the game title screen, and mid-run gameplay

---

## Things to Know Before Launch

### Google Fonts dependency
The game loads **Press Start 2P** from `fonts.googleapis.com`. itch.io's
iframe does not block this. Works online; falls back to `monospace` offline.
If you want a fully offline build in the future, the font can be base64-
embedded into the HTML (~50 KB extra).

### itch.io file size limits
Free accounts: **1 GB** per file. Your ZIP is **148 KB** — no issue.

### iframe sandbox
itch.io runs HTML games inside a sandboxed iframe. The game uses the
Web Audio API and `localStorage` (for high scores). Both work inside
itch.io's iframe by default — no special permissions needed.

### Mobile fullscreen
On iOS Safari the game uses `100dvh` so it fills the screen correctly
inside itch.io's mobile embed. The "Fullscreen button" setting on itch.io
adds a ⛶ button that expands to native fullscreen on Android.

### Adding future games
When a new game is ready, update `index.html` (flip `playable: false` → 
`true` for that game entry in the `games` array) and re-upload the ZIP.
itch.io lets you replace files without changing the page URL.
```javascript
// In index.html — games array, find the entry and set:
playable: true
```
Then re-zip and upload as a new version on the same page.
