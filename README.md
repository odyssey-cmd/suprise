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
| **Glass / Sine / Music box / Marimba / Harp / Flute / Warm pad** (I) | Changes the instrument |
| **bpm** (T) | Cycles through 72, 90, 108 and 126 bpm |
| **Dream** (D) | The garden plants and lets go of flowers by itself, so the tune slowly drifts |
| **Shuffle** (R) | Grows a new random melody |
| **Clear** (C) | Clears the garden, with an Undo |
| **Share** | Copies a link that holds the whole garden |
| Arrow keys, then Enter | Plants without a mouse |
| P | Saves a picture of the garden |

Every ring is labelled with its note (G3, A3, B3…), and the labels change with the scale. When a flower sings, a ♪ rises from it with the note's name, or ♫ when it plays as part of a chord. Point at an empty spot and you see the note you would plant there.

It respects the "reduce motion" setting by turning off the pollen and keeping pulses small.

## How it works

- The circle is a 16-step sequencer with 8 rings. Each ring is one note of the current scale.
- Notes are scheduled slightly ahead on the Web Audio clock, so timing stays tight even when the page is busy. The sun's position comes from that same clock, so what you see lines up with what you hear.
- Every instrument is synthesized live, with no sample files. Glass, Sine, Music box and Marimba are stacks of sine partials, each decaying at its own rate (a marimba bar rings two octaves up, and a music-box tine has a quick metallic tick). Harp is a Karplus-Strong plucked string rendered once per pitch. Flute is a sine wave with vibrato that arrives late plus filtered breath noise, and Warm pad is two detuned sawtooth waves through a low-pass filter. Everything goes through a feedback delay and a reverb built from noise at start-up.
- A shared garden is stored in the URL itself (`#v1.<16 bytes as base64>.<scale>.<tempo>.<instrument>`), so nothing is ever uploaded.
