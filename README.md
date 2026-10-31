# Baritone Ukulele Tuner

A reference-tone tuner for baritone ukulele (D-G-B-E) with psychedelic visuals that respond to each note.

**Live link:** https://1indes.github.io/baritone-ukulele-tuner/

<img width="2861" height="1560" alt="Screenshot of the tuner with ripples spreading from a tuning peg" src="https://github.com/user-attachments/assets/345abf91-b623-4e13-9c6c-86480dfac8c7" />

## The idea

I play a baritone ukulele, and many tuners are built around standard ukulele tuning. I wanted a tuner made for baritone, showing its four strings (D, G, B, E) in the layout of a real headstock. I also wanted it to look good to use, so I gave it a 1960s psychedelic style where each string has its own colour and the visuals change with the pitch.

## Who it's for

Baritone ukulele players who tune by ear and want a clear reference tone for each string.

## How to use it

1. Click a tuning peg or a string, or press 1-4 (or the letters D, G, B, E), to hear that string's note.
2. Turn your real tuning peg until your string sounds the same as the note.
3. Click "Stop and clear" to silence the sound and clear the ripples.

What the visuals mean:
- Each string has its own colour, and the status line takes the colour of the string you played.
- The string wobbles and fades like a plucked string, and the tuning peg spins while the note rings.
- Ripples spread out from the peg. Higher notes make more waves in each ripple, and the ripples start as circles and become wavier as they grow.

The notes are D3 (146.83 Hz), G3 (196.00 Hz), B3 (246.94 Hz) and E4 (329.63 Hz).

## How the main interaction works

A click or key press calls `playString(i)`. It creates a Web Audio oscillator at that string's frequency with a 3-second fade, and marks the string as "ringing". Every frame, the drawing code checks which strings are ringing. For each one it wobbles the string, spins the peg, and sends out ripples. Each string's entry in the `STRINGS` list sets its note, colour, ripple speed and number of waves, and higher notes send out ripples more often. A ripple starts as a circle and gets wavier the further it travels. So the user's action sets both the sound and the visuals, and feedback appears immediately.

## How to run it

There are no dependencies and nothing to install. Either:

- open the live link above, or
- download or clone the repo and double-click `index.html` to open it in a browser, or
- in VS Code, right-click `index.html` and choose "Open with Live Server" (if you have that extension).

The page loads two fonts from Google Fonts, so it needs an internet connection to look as intended. Offline, it falls back to Georgia.

Tested in: Chrome on a MacBook

## What happens when something goes wrong

- Browsers block sound until the user interacts with the page, so audio only starts after the first click or key press.
- Clicking empty space shows a message telling the user to click a peg or string.
- Clicking a string repeatedly restarts its note cleanly instead of stacking sounds.
- If the browser can't play Web Audio, the status line says so.
- "Stop and clear" silences everything and resets the display.

## Known limitations

- It plays reference tones only. It doesn't listen through the microphone, so it can't tell you how far off your string is.
- The sound is a simple synthesised tone, not a recording of a real ukulele.
- The layout is vertical, so it uses space differently on a laptop than on a phone. 
- The headstock shows two pegs per side, which is common on baritones but not on every model.

## Credits

- The first version of the code, and help with later changes, came from Claude (Anthropic). See PROCESS.md for what I used it for and what I changed.
- Fonts: Shrikhand and Fredoka, from Google Fonts (open licences).
- Note frequencies: standard equal-temperament values for D3, G3, B3 and E4.
