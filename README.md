# RS3 Farming Timers — Alt1 Plugin

Track your RuneScape 3 farming patches with visual countdown progress bars.

---

## What This Plugin Does

- Select a crop and patch type from the dropdown
- Give it a label (e.g. "North Falador", "Catherby")
- Click **PLANT** — a countdown timer with a progress bar starts immediately
- Bar turns **orange** when <10% time remains
- Bar turns **green** and pulses when the crop is ready to harvest
- Timers are saved automatically so they survive page refreshes

---

## How to Install in Alt1 (Step-by-Step)

### Option A — Host it locally with a simple web server

This is the recommended beginner approach.

1. **Install Node.js** from https://nodejs.org (LTS version)

2. **Open a terminal** (Windows: press `Win + R`, type `cmd`, press Enter)

3. **Install a simple server** by typing:
   ```
   npm install -g serve
   ```

4. **Navigate to your plugin folder:**
   ```
   cd C:\path\to\rs3-farming-timer
   ```
   (Replace with wherever you saved the files)

5. **Start the server:**
   ```
   serve .
   ```
   It will say something like `Serving! Local: http://localhost:3000`

6. **Open Alt1**, click the **+** button to add a new app

7. Paste in: `http://localhost:3000/appconfig.json`

8. Click **Add App** — your farming timer should appear!

---

### Option B — Use GitHub Pages (free, permanent hosting)

If you want your plugin available without running a server:

1. Create a free account at https://github.com
2. Create a new repository (e.g. `rs3-farming-timer`)
3. Upload `index.html` and `appconfig.json`
4. Go to **Settings → Pages** and enable GitHub Pages on the `main` branch
5. Your URL will be: `https://yourusername.github.io/rs3-farming-timer/appconfig.json`
6. Add that URL in Alt1

---

## File Structure

```
rs3-farming-timer/
├── index.html       ← The plugin UI and all logic
├── appconfig.json   ← Tells Alt1 about your plugin
└── README.md        ← This file
```

---

## Customising Crop Timers

All crop durations are defined in the `<select>` dropdown in `index.html`.
To add a new crop, find the relevant `<optgroup>` and add a line like:

```html
<option value="PatchType|CropName|DurationInMinutes">Display Name (X min)</option>
```

For example:
```html
<option value="Herb|Arbuck|80">Arbuck (80 min)</option>
```

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Alt1 says "cannot connect" | Make sure your local server (`serve .`) is running |
| Timers disappear on refresh | This is normal if you clear browser storage — timers are saved in localStorage |
| Plugin looks tiny | Right-click the plugin in Alt1 and adjust the size |

---

## Notes on Alt1 & Screen Reading

This plugin currently works as a **manual timer** — you tell it when you plant.
Future versions could use Alt1's pixel-reading API to detect the farming patch
interface automatically. The `alt1` global object is already checked in the code
and the `appconfig.json` requests the right permissions (`pixel`, `gamestate`).
