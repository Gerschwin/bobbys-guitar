# Bobby’s Guitar

A beginner guitar chord trainer that runs in the browser and installs as an app on your phone.

- **Chords:** big chord diagrams for 26 chords, hear each one strummed or picked, and check your own playing with the microphone.
- **Play along:** chords scroll past with a bouncing ball. In *Wait for me* mode it waits until it hears the right chord; in *Keep going* mode it scores the chord and the timing of every strum.
- **Strum patterns** from one strum per chord up to down-up eighths, a **song library** (the `songs/` folder: traditional songs with lyrics, and well-known songs as chords and sections only), and **your own songs** with per-chord lengths, sections and lyrics, shareable as a link.
- **Practice:** tuner, one-minute chord changes with pivot-finger hints, a Name-that-chord ear quiz, practice tracking, and an experimental strum-direction lab.
- **On Tour:** earn fans for clean changes, on-time strums and practice to climb from the Bedroom to the Stadium, with daily setlists, combos, 24 stickers for your guitar case, gig-poster level-ups and unlockable guitar finishes.
- Works offline once installed. Everything stays on your device.

**Use it:** https://gerschwin.github.io/bobbys-guitar/ — on a phone, use *Install* (Android) or *Share → Add to Home Screen* (iPhone).

## Developing

`app.html` is the single source file. `./build.sh` turns it into `index.html` and `sw.js` (the offline cache, named after `APP_VERSION`). Bump `APP_VERSION` in `app.html` with every change.

**Test mode:** tap the version number 5 times. Everything for it sits between `TEST-MODE-START` / `TEST-MODE-END` markers, and `build.sh` strips it automatically once `APP_VERSION` reaches 1.0.

To run it locally (the microphone needs `localhost` or HTTPS):

```bash
./build.sh && python3 -m http.server 8000
```

## Credits

Background blur and backdrops (live shows): Google [MediaPipe](https://github.com/google-ai-edge/mediapipe) tasks-vision 1.1.0 and the selfie segmenter model, Apache 2.0 (see `vendor/mediapipe/LICENSE`).

Crowd sounds (live shows): applause and cheering from [BigSoundBank](https://bigsoundbank.com), CC0 (public domain).

Guitar samples: steel-string acoustic guitar from the FluidR3 GM soundfont by Frank Wen, licensed [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/), via [gleitz/midi-js-soundfonts](https://github.com/gleitz/midi-js-soundfonts).

## Adding songs

Drop a JSON file into `songs/` and run `./build.sh` (it rebuilds `songs/index.json`). The format:

```json
{"title": "Song name", "artist": "Who", "bpm": 90, "capo": 0, "level": 1, "pattern": "beat",
 "note": "Shown under the song picker",
 "sections": [{"name": "Verse", "repeat": 2, "chords": [["G", 4, "optional lyric"], ["C", 2], ["D", 2]]}]}
```

Chord names are the app's chord ids (`G`, `Am`, `Fmini`, `Cadd9`…), the number is beats, and `pattern` is one of `beat`, `change`, `eighths`, `folk`, `push`. Only include lyrics that are out of copyright.
