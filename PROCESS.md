# Process

## Starting idea

I have been playing ukulele for years, but always with standard tuning. I recently got a baritone ukulele, which has different tuning to the others, and it has been frustrating to find out that my go-to GuitarTuna app does not have an option for baritone ukes. So, I first thought of a tuner like GuitarTuna just for baritone ukuleles. I'm quite inexperienced and had about a week, so I looked at the risks. Listening through the microphone and detecting pitch is the hardest part and the hardest to debug. I narrowed the idea to a reference-tone tuner where the user plays a note and sees a visual response, and I kept microphone listening as a stretch goal I didn't get to.

I chose baritone ukulele because I play one, and many tuners are built for standard ukulele tuning. That gave the project a specific user and a clear purpose.

## Changes I made

First version: four plain circles (D, G, B, E) that played a note and sent out ripples.

Redesign: I wanted the page to look and feel more like an instrument, and to be more interesting visually. The second version had a 60s psychedelic theme and a headstock with tuning pegs and strings that vibrate. I then noticed the layout didn't match my real baritone, so the pegs, their sides and the string spacing were changed to fit a real instrument.

My own tweaks, made by editing the code myself:
- I added yellow to the background gradient because it felt too much like the Instagram logo with only pink and purple
- I changed the title colors to match the string colors so it was more cohesive
- I chose the Fredoka font to replace the one given by Claude for the status text and shortcuts because I wanted rounder, smoother shapes to match the psychedelic aesthetic.
- I made it so the status text takes the colour of the string played to add an extra feeling of interaction.
- I set a speed for each string so the ripples feel even
- I changed the wave counts because D and G looked square

**One thing that went wrong:** After I changed how the ripples wobble, the whole ukulele head disappeared, but the title, background and button stayed. That pattern was the clue: the page was fine, but the script that draws the head had stopped. My guess was that I'd left the old line next to the new one, so the same name was declared twice, which makes the whole script fail. I fixed it by replacing the entire ripple function in one go instead of editing individual lines, and the head came back. It taught me that when only the drawn part disappears, the problem is in the script.

## User trial

**What I changed:** The tester triggered a lot of ripples at once and I noticed they seemed to disappear behind an invisible rectangle at the top, level with the pegs and text. The drawing area only covered the space below the title, so ripples were cut off at its edge. I changed the canvas to cover the whole window, put the title and button on top of it, and made the head's position depend on where the title ends. The ripples now spread across the whole page.
**Who and how:** TODO (for example, a friend who doesn't play ukulele. I gave no instructions and watched. Which device?)

**What I observed:** TODO (what did they click first? Where did they hesitate? Did the sound and visuals make sense to them? Did they understand the pegs and strings were clickable?)

**What I changed, or why I kept the design:** TODO (one improvement based on what you saw, or why you left it as it was).

## AI tools

I used Claude (Anthropic) to:
- help me choose a scope I could finish, and talk through the options
- write the first working version of `index.html`, and the redesigned headstock, pegs and strings
- explain Git, GitHub Pages and VS Code steps
- suggest edits to the code while I tuned the design, such as ripple speeds and wave counts

**A suggestion I kept:** Claude suggested building a click-to-play version first and treating microphone listening as an optional extra. I kept this because I'm inexperienced and had about a week, and pitch detection would have been the hardest part to debug. It gave me a working project early, so I could spend the rest of the time on the design and on understanding my code.

** Two suggestions I changed:** 

- Claude's first ripple speeds were calculated from each note's pitch, which made B and E too fast to watch. I replaced them with a speed that I set for each string. When Claude's first attempt left a much bigger gap between D and G than between the other strings, I pointed it out and asked for even steps, then adjusted E by eye until it felt right. I also changed the wave counts in the ripples, because with only 3 and 4 waves the D and G rings looked square.
- Claude's first headstock design had the pegs in the wrong places for a real baritone ukulele. I noticed because I play one, so I asked for the layout to be changed so the pegs, their sides and the string spacing matched my instrument.
