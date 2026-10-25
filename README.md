# Baritone Ukulele Tuner

<!-- One or two sentences: what is it and who is it for? -->
A reference-tone tuner for baritone ukulele (D-G-B-E) with visuals that respond to each note.

**Live link:** <!-- add your GitHub Pages link here once it's set up, or delete this line -->

![Screenshot](screenshot.png)
<!-- Take a screenshot of the working page, save it as screenshot.png in this folder -->

## The idea

<!-- Why did you make this? E.g. many tuners are built for standard ukulele tuning, and I play baritone. -->

## Who it's for

<!-- E.g. baritone ukulele players who tune by ear and want a clear reference for each string. -->

## How to use it

1. Click a circle, or press 1-4 (or the letters D, G, B, E), to hear that string's note.
2. Tune your ukulele string until it sounds the same as the note.
3. Click "Stop and clear" to silence the sound and clear the ripples.

<!-- Explain what the visuals mean: lower notes make thick, slow ripples; higher notes make thin, fast ones. -->

## How to run it

No installs or dependencies. Either:

- Open `index.html` in a browser, or
- In VS Code, right-click `index.html` and choose "Open with Live Server", or
- Run `python3 -m http.server` in this folder and go to `http://localhost:8000`.

<!-- Add which browsers you tested in. -->

## What happens when something goes wrong

<!-- List the mistakes you handle. Delete any you don't actually handle. -->
- Browsers block sound until the first click, so audio only starts after the user clicks or presses a key.
- Clicking empty space shows a message telling the user to click a circle.
- Clicking a string repeatedly restarts the note instead of stacking sounds.
- If the browser can't play sound, a message says so.

## Known limitations

<!-- Be honest. E.g. it plays reference tones only and doesn't listen to the microphone, so it can't tell you how far off your string is. -->

## Credits

<!-- Credit everything you didn't write yourself. -->
- Initial version of the code was written with help from Claude (Anthropic). See PROCESS.md.
- Note frequencies: standard equal-temperament values for D3, G3, B3 and E4.
- <!-- Course examples, tutorials, fonts, anything else -->
