# HAI Clinical Platform — Hiba Avatar Build

Hiba now appears in-app as her **real photo** (the one you uploaded, cropped to a clean portrait), embedded directly in `index.html` as a base64 image — no separate image file to host, still a single-file deploy.

## Why not a hand-drawn cartoon?
An earlier pass tried to recreate her as a fully hand-coded SVG illustration. It looked cartoonish and didn't resemble her — that was a mistake in approach, not a technical necessity. Using her actual photo is simply better.

## What's animated (and what isn't, on purpose)
- **Idle breathing** — a continuous, subtle scale pulse on the photo, always running.
- **Listening** — a gentle tilt plus a soft pulse ring around the photo while the mic is active.
- **Speaking** — a soft gold glow around the photo, an animated voice-waveform badge in the corner, and the live caption bubble showing exactly what she's saying.
- **No fake mouth-flap on the photo.** A single flat photo can't open and close its mouth convincingly with CSS — trying it looks worse than not doing it (uncanny, glitchy). The waveform + glow + captions communicate "she's talking" clearly without faking a real lip movement.

## If you want true lip-sync later
That needs either:
1. **Segmented layers** — cut the photo into mouth/eye/arm pieces (as originally scoped) so real viseme shapes can swap in, or
2. **A talking-avatar/lip-sync service** (e.g. D-ID, HeyGen, or similar) that generates a video or frame sequence driven by the audio.

The code already exposes clean hooks (`hibaSay()`, and the `.speaking` / `.listening` classes on `#hibaAvatar`) so either approach can be wired in without restructuring the app.

## Voice & recognition
`speechSynthesis` (speaking) and `SpeechRecognition` (listening) remain browser-native and optional, with manual form fields as a fallback throughout.

## Quick start
Static single-file app — open `index.html` directly, or deploy as-is (`vercel.json` rewrites all routes to `index.html`).
