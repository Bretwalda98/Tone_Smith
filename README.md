ToneSmith is a lightweight, offline-ready guitar tuner web-app that fits any mobile screen and leaves room for an in-page advert slot.

# ToneSmith – Offline Guitar Tuner
*(single‑page HTML app)*

## Table of contents
1. About
2. Features
3. Quick start
4. Building an Android APK
5. Customising
6. Folder structure
7. Licensing

## About
ToneSmith turns any device with a microphone and modern browser into an accurate chromatic tuner.
The entire UI is plain HTML + CSS + JS—no build tools, frameworks or external libraries—so it runs offline once cached and is trivial to embed in a WebView for native distribution.

## Features
* **Accuracy** – Autocorrelation‑based pitch detection (≈ ±1 cent in quiet conditions).
* **Six‑string panel** – Per‑string note selector, editable target frequency, live cents display and coloured bar.
* **Custom concert A** – Slider / number input (300–500 Hz).
* **Safe‑area aware** – Adds `env(safe-area-inset-top)` plus 24 px so nothing hides beneath a notch or status bar.
* **Advert slot** – Pre‑styled `div.advert-box` (`min-height: 200 px`)—drop in AdSense or a banner.
* **Fully offline** – All assets are inline; works in aeroplane mode after first load.
* **Responsive & compact** – Shrinks fonts and scales sections below 500 px wide.

## Quick start
1. Download `tone_smith.html`.
2. Open it in any Chromium‑based or Firefox browser (desktop or mobile).
3. Tap **Start tuner → “Allow microphone”**.
4. Select a string, pluck, tune.

### Replacing the advert placeholder
```html
<div class="advert-box">
  <!-- Google AdSense example -->
  <script async src="https://pagead2.googlesyndication.com/pagead/js/adsbygoogle.js"></script>
  <ins class="adsbygoogle" style="display:block"
       data-ad-client="ca-pub-XXXXXXXXXXXX"
       data-ad-slot="YYYYYYYYYY"
       data-ad-format="auto"></ins>
  <script>(adsbygoogle = window.adsbygoogle || []).push({});</script>
</div>
```

## Building an Android APK
1. **Android Studio** → *New Project* → Empty Activity  
   *Package*: `com.yourname.tonesmith`, *Language*: **Kotlin**, *Min SDK*: 23
2. Copy `tone_smith.html` into `app/src/main/assets/`.
3. Use a full‑screen WebView in `activity_main.xml`, then:
   ```kotlin
   web.loadUrl("file:///android_asset/tone_smith.html")
   ```
4. Add `RECORD_AUDIO` permission to `AndroidManifest.xml`.
5. **Build → Build APK(s)** or **Generate Signed APK**.

## Customising
| Task | Where |
|------|-------|
| Change colours | Edit CSS `:root` variables. |
| Safe‑area gap | Adjust `--top-gap` in `<style>`. |
| UI scale | Tweak base `font-size` or the `@media` scale factor. |
| Default tuning | Modify `DEFAULT_STRINGS` array in JS. |
| More strings | Extend array and grid column widths. |

## Folder structure
```
tone_smith.html
assets/
└─ icon512.png   (optional)
```

## Licensing
Released under the **MIT License**.  Pull requests and forks welcome!
