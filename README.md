# Rigpop Talk 🐸🎙️

**Make doodles talk.** Drop in a voice note and a doodle character lip-syncs it, blinks, and bobs along. Export a 9:16 reel with sound, all in your browser. No server, no sign-up, no API key.

![Rigpop Talk demo](docs/demo.gif)

## How it works

1. **Pick a character:** Swapnil (the maker, drawn in blue-ink comic style), Mochi the bunny-cat, or Froggo.
2. **Add a voice:** upload audio (mp3, wav, m4a, or even a video file), record from your mic, or go **Live mic** and watch the character copy you in real time.
3. **Style it:** background colour or your own image, dots or stars pattern, an optional title sticker, 9:16 / 1:1 / 16:9.
4. **Export:** you get an MP4 (Safari, newer Chrome) or WebM video with the audio baked in.

## Under the hood

- **Lip sync:** the Web Audio API reads loudness and three frequency bands every frame and picks a mouth shape: rest, **A** (open), **O** (round), **E** (wide/teeth). Shapes are held for at least 70 ms so the mouth doesn't flicker.
- **Life:** random blinks every 2 to 5.5 s, breathing, and a head bob that follows how loud you are.
- **Characters:** each one is a transparent base picture plus small mouth and blink patches that sit exactly over the face (`characters/characters.json` holds the positions).
- **Export:** `canvas.captureStream()` plus the audio track goes into `MediaRecorder`.

Keep the tab open and visible while exporting; browsers pause drawing in background tabs.

## Run it

It's a single `index.html`. Serve the folder with any static server (`npx serve .`) or deploy it on GitHub Pages or Vercel. Opening the file directly works for preview, but export needs it served over http(s).

## Add your own character

Put `name_base.png` (transparent) plus `name_A.png`, `name_O.png`, `name_E.png` and `name_blink.png` patches in `characters/`, then add the patch positions to `characters/characters.json` and the `CHARS` list in `index.html`. An in-app uploader is coming in v0.2.

## Roadmap

- **v0.2:** bring your own character in the app, word-by-word captions (Hindi + English), scene presets (podcast, news anchor, classroom), type a script and it speaks (your own TTS key)
- **v0.3:** two characters in a conversation

Sibling of [Rigpop](https://github.com/swapagrawal14/rigpop) and [WowKit](https://github.com/swapagrawal14/wowkit). Made with 🌷 by [Swapnil Agrawal](https://github.com/swapagrawal14). MIT licensed.
