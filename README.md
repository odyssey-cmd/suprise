# Sound Garden

A tiny instrument that cannot play a wrong note.

Plant flowers in a circle. A sun sweeps around it, and every flower it touches sings. Near the centre is low, the edge is high, and the position around the circle is when the note plays. Every note is drawn from one scale, so anything you plant sounds good together.

Open `index.html` in a browser. It is one file, with no install, no build step and no network requests.

## Playing

| Do this | And this happens |
| --- | --- |
| Tap or click inside the circle | Plants a flower (you hear it straight away) |
| Drag | Paints a run of flowers, or clears them if you started on one |
| Tap the glowing centre, or press Space | Pause and play |
| **Pentatonic / Hirajoshi / Lydian** (S) | Changes the scale and the garden's colours |
| **bpm** (T) | Cycles through 72, 90, 108 and 126 bpm |
| **Dream** (D) | The garden plants and lets go of flowers by itself, so the tune slowly drifts |
| **Shuffle** (R) | Grows a new random melody |
| **Clear** (C) | Clears the garden, with an Undo |
| **Share** | Copies a link that holds the whole garden |
| Arrow keys, then Enter | Plants without a mouse |
| P | Saves a picture of the garden |

It respects the "reduce motion" setting by turning off the pollen and keeping pulses small.

## How it works

- The circle is a 16-step sequencer with 8 rings. Each ring is one note of the current scale.
- Notes are scheduled slightly ahead on the Web Audio clock, so timing stays tight even when the page is busy. The sun's position comes from that same clock, so what you see lines up with what you hear.
- Each note is a sine wave, a soft triangle wave an octave up and a short bell-like overtone, passed through a closing filter. Everything then goes through a feedback delay and a reverb built from noise at start-up.
- A shared garden is stored in the URL itself (`#v1.<16 bytes as base64>.<scale>.<tempo>`), so nothing is ever uploaded.
