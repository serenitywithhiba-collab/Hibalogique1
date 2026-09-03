# HAI Clinical Platform — Hiba Interactive Avatar Build

Hiba lives directly inside `index.html` as an inline SVG/CSS character — no external photo/image file is used or required. She is full body (head to shoes), dressed in a red blazer, white blouse, black trousers and gold "H" accents, and stays inside the clinical interview panel at all times.

## What's animated
- **Breathing** — a continuous, subtle chest scale loop runs at all times (idle, listening, and speaking).
- **Blinking** — eyes blink at randomized intervals (~2.5–6s) independent of speech state.
- **Hair & folder sway** — long hair and the folder she's holding drift gently for a lived-in feel.
- **Mouth / lip-sync** — the mouth cycles through four viseme shapes (`rest`, `open`, `wide`, `small`). While `speechSynthesis` is speaking, the browser's word-boundary events (`onboundary`) pick a viseme based on the vowel being spoken; if a browser doesn't fire boundary events reliably, a timed fallback keeps her mouth moving naturally instead of freezing.
- **Gesture** — her arms rotate gently from the shoulder while she's talking (tied to the `speaking` CSS class), plus an ambient waving-hand icon near the scene.
- **Listening state** — when the microphone is active, her head tilts slightly and a soft pulse ring appears around her; this also fixed a previous bug where the listening indicator never activated (an `id` mismatch in the JS).

## Voice & recognition
Everything voice-related — `speechSynthesis` for speaking and `SpeechRecognition` for listening — is browser-native and optional. Availability varies by browser/OS, so manual form fields remain a fallback throughout.

## Quick start
This is a static, single-file app. Open `index.html` directly in a browser, or deploy as-is (see `vercel.json`, which rewrites all routes to `index.html`).
