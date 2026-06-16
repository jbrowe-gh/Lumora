# LUMORA — Cine Light Meter

**Version 3.2**

LUMORA is a browser-based light meter and shot planner for the **RED Komodo X** and **Sony A7S III**. Point your phone at a scene (or feed it a photo), and it reads the available light and dials in a coherent starting recipe: ISO, color temperature, aperture, shutter, a depth-of-field look for your lens, and a two-light bi-color lighting plan. It runs as a single HTML file — no install, no account, nothing to download to your camera.

It is a *starting point*, not a replacement for your camera's own tools. Always confirm against the on-camera false color and histogram before you roll. The "Why the numbers aren't gospel" section below explains the honest limits.

---

## Quick start

1. Open the hosted link in a mobile browser (see *Running it* for why this has to be HTTPS).
2. Pick your camera with the toggle in the **top-right** — Komodo X (red) or A7S III (gold).
3. Choose **Live camera** or **From photo**.
4. Set your shoot parameters: resolution, frame rate, quality, look, lighting mood, lens.
5. Tap **Analyze light** (live) or **Choose photo**.
6. Read the recommendation. Adjust anything and the numbers update instantly.

---

## The two input modes

**Live camera** opens your rear camera, overlays a framing reticle, and shows a running readout of EV, estimated color temperature, and estimated lux. Tap **Analyze light** and it averages several frames for a stable reading, then freezes the frame and produces the full recommendation.

**From photo** lets you pick any image from your camera roll and runs the identical analysis on it. Use this when you can't get the live camera working, or to plan from a reference shot taken at the location in the same light.

---

## What each result means

**ISO** — Tuned to each camera's real behavior. The Komodo X has a single native ISO of 800 (EI 250–12800); LUMORA holds 800 in usable light and climbs only when the scene is genuinely dark. The A7S III, in Rec.709/Standard, rides its clean base ISO 80 in bright light and reaches for higher values in the dark. (If you switch the Sony to S-Log3 on the camera, its base shifts to the dual-native 640/12800 pair — the app notes this where relevant.)

**Color temp (Kelvin)** — Estimated from the scene's measured color balance, with a warm-to-cool pointer. This is the white balance to set so whites stay neutral.

**Aperture** — A single number that drives the whole shot (see *How aperture works* below). The Camera Look section and the top Aperture card always agree.

**Shutter** — Locked to a natural 180° shutter for your chosen frame rate (24fps → 1/48, 60fps → 1/120, and so on), with a note about cutting flicker.

**Exposure balance** — A meter showing whether the chosen aperture exposes correctly for the metered light, plus the **Meter trim** slider.

**Camera look** — Focal length, aperture, subject distance, and a depth-of-field readout to achieve a chosen look (shallow, natural portrait, deep focus, wide establishing) on a specific lens.

**Exposure at f/X** — The reconciliation card. Shows whether your chosen aperture matches the light, and if not, offers three ways to fix it.

**Lighting plan** — Per-fixture Kelvin and output percentage for a bi-color key and fill (and an auto hair/rim light for moodier setups).

**Record format** — A summary of camera, resolution, frame rate, and codec/compression, with a warning if your frame rate exceeds what the resolution allows.

---

## How aperture works (important)

Earlier versions showed two different apertures and it was confusing. As of v3.2 there is **one aperture** for the whole shot, and it is driven by your look (or by a manual choice). Here is the model:

- Pick a **look** (or a specific **aperture** from the dropdown). That f-stop becomes the aperture for the entire recommendation — the top card and the Camera Look card show the same value.
- The **Exposure at f/X** card then tells you whether that aperture actually exposes correctly for the light LUMORA measured.
- If it doesn't — for example, you opened the Sirui to f/1.2 in a bright room and you're several stops over — the card offers three fixes and lets you choose:
  - **ND filter** — the cleanest fix; holds your exact look and depth of field. Best outdoors.
  - **ISO** — changes noise.
  - **Shutter** — changes motion blur (and breaks the 180° rule).

This mirrors how exposure actually works on set: depth of field and brightness pull against each other, and ND is how you keep both.

### Manual aperture

The **Aperture** dropdown in Camera Look lets you override Auto and dial any stop the selected lens supports — the list is clamped to that lens's real range (e.g. T1.2–T16 on the Sirui, f/2.8–f/22 on the zooms). Pick one and the depth of field and the exposure reconciliation both update.

---

## Lenses

The lens list changes with the selected camera. **Auto** picks the best lens in the kit for your chosen look; you can override to any specific lens.

**Komodo X (Super 35):**
- Sirui Night Walker 24mm T1.2 — S35 cine prime, manual focus. The fastest glass in the kit and the low-light / shallow-DoF hero.
- Canon RF 24-70mm f/2.8L IS — full-frame standard zoom; the do-everything lens.
- Canon RF 15-35mm f/2.8L IS — full-frame ultra-wide; establishing shots and tight spaces.

**A7S III (full-frame):**
- Sony FE 24-70mm f/2.8 GM II — standard zoom; everyday workhorse.
- Sony FE 70-200mm f/2.8 GM — telephoto; the strongest compression and shallow-DoF tool.
- Tamron 11-20mm f/2.8 Di III-A — APS-C ultra-wide. **Note:** on the full-frame A7S III this forces Super 35 crop mode, which records 1080-only (no 4K) and acts roughly 1.5× longer; full-frame use vignettes. The app flags this whenever the lens is selected and still gives you the look settings.

Depth of field is computed against each body's correct sensor size, so the same lens reads differently on the Komodo X (S35) than on the A7S III (full-frame) — as it does in reality.

---

## Lighting plan

After analysis, LUMORA suggests a bi-color two-light setup (key + fill, plus an auto hair/rim light for moody, dramatic, or high-contrast scenes). Each fixture gets a **Kelvin** and an **output percentage**.

- The **key** matches the scene's measured color temperature so your added light blends with the ambient.
- The **fill** runs at a percentage of the key set by the **Lighting mood** control: High-key (≈75%, soft), Natural (≈50%, ~1 stop under), Moody (≈25%, ~2 stops), Dramatic (≈12%, ~3 stops).
- The **hair/rim** light runs cooler than the key for subject separation.

The percentages are *relative panel output*, not a calibrated brightness standard — bi-color panel brands report output differently, so match by eye against the camera's histogram.

---

## Meter trim and why the numbers aren't gospel

Your phone is not a calibrated light meter. Before LUMORA ever sees a frame, the phone auto-exposes, auto-white-balances, tone-maps, and applies noise reduction. The practical effect: a dim room is brightened to look pleasant, so it can read brighter (higher EV/lux) than it truly is, and color casts get neutralized, which fights the Kelvin estimate.

Two things follow:

1. **Treat the reading as a relative starting point** and confirm against the camera's false color and histogram. The app says this on screen.
2. **Use the Meter trim slider** (±3 EV, in the Exposure balance card) to correct a reading you know is off — for instance, pull it down a stop or two when the phone has obviously over-brightened a dark scene. The trim shifts the exposure math one-for-one in stops.

LUMORA is also not a light meter for hazardous or safety-critical work, and it is not a substitute for metering a key with a real incident meter when precision matters.

---

## Running it

LUMORA is a single `index.html` file. The **live camera requires a secure (HTTPS) page** — browsers block camera access on `file://` and plain `http://`. You have a few options:

- **Hosted (recommended):** put `index.html` on any static HTTPS host. GitHub Pages and Netlify Drop both work. With Pages, name the file `index.html` and your URL is `https://USERNAME.github.io/REPO/`.
- **From photo only:** if you just open the file locally without HTTPS, the live camera won't start, but the **From photo** tab works anywhere and runs the same analysis.

### If the camera says "blocked"

- Check the address bar. `file://` or `http://` means you need HTTPS — host it.
- On HTTPS but still blocked: a permission was denied earlier. On iOS, clear it under Settings → Safari → Camera, or via the "aA" menu → Website Settings → Camera → Allow, then reload.
- Use a normal (non-private) tab and tap **Start camera** directly.

---

## Deploying an update (GitHub Pages)

1. In your repo, **Add file → Upload files**, drag in the new `index.html` (same name overwrites the old one).
2. Commit with a clear message, e.g. `v3.2 — unified aperture, manual override, ND reconciliation`.
3. Pages redeploys in a minute or two.
4. Open the URL and hard-refresh (close the tab and reopen, or pull-to-refresh) to beat the browser cache.
5. **Confirm the version badge** in the top-left matches what you shipped. That's its job — if it shows the old number, you're seeing a cached copy or the build hasn't finished.

Writing what changed in each commit gives you a free revision history under the repo's **Commits** tab, and you can roll back to any previous version if an update breaks something.

---

## Version history

- **v3.2** — Unified aperture (look drives exposure; top card and look card always agree). Manual aperture override per lens. Exposure reconciliation card with ND / ISO / shutter options. Meter trim (±3 EV) and phone-meter honesty note.
- **v3.1** — Six real lenses (three per camera) with auto-pick + manual override; APS-C-on-full-frame crop warning for the Tamron.
- **v3.0** — Bi-color lighting planner (key + fill + auto rim) and camera-looks engine with depth-of-field.
- **v2.0** — Sony A7S III support, camera toggle, frame-rate / resolution / quality controls, version badge.
- **v1.0** — Initial Komodo X light meter.

---

## A note on accuracy

Camera specs (native ISO, frame-rate ceilings, codec options) and lens specs (focal range, maximum aperture, mount, sensor coverage, minimum focus distance) were drawn from manufacturer spec sheets and manuals. Depth of field is calculated from focal length, aperture, subject distance, and each sensor's circle of confusion. The exposure math is internally consistent — the aperture LUMORA considers "correct" reconciles to zero stops of error. None of that makes the *scene reading* itself precise, for the phone-sensor reasons above. Plan with LUMORA; expose with your camera's tools.
