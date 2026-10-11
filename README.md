# First Frets

A beginner guitar chord trainer that runs in the browser and installs as an app on your phone.

- **Chords:** big chord diagrams for 26 chords, hear each one strummed or picked, and check your own playing with the microphone.
- **Play along:** chords scroll past with a bouncing ball. In *Wait for me* mode it waits until it hears the right chord; in *Keep going* mode it scores the chord and the timing of every strum.
- **Strum patterns** from one strum per chord up to down-up eighths, and **your own songs** built from the chord list.
- Works offline once installed. Everything stays on your device.

**Use it:** https://gerschwin.github.io/first-frets/ — on a phone, use *Install* (Android) or *Share → Add to Home Screen* (iPhone).

## Developing

`app.html` is the single source file. `./build.sh` turns it into `index.html` and `sw.js` (the offline cache, named after `APP_VERSION`). Bump `APP_VERSION` in `app.html` with every change.

To run it locally (the microphone needs `localhost` or HTTPS):

```bash
./build.sh && python3 -m http.server 8000
```

## Credits

Guitar samples: steel-string acoustic guitar from the FluidR3 GM soundfont by Frank Wen, licensed [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/), via [gleitz/midi-js-soundfonts](https://github.com/gleitz/midi-js-soundfonts).
