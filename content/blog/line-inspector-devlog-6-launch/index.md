---
title: "Line Inspector Devlog #6: The Line Is Open"
date: 2026-10-14T06:00:00.000Z
slug: "line-inspector-devlog-6-launch"
summary: "Line Inspector 1.0 is out. A tour of the finished game, the numbers behind it, and what we learned building our second game."
tags: ["line inspector","devlog","html5 games","game launch","postmortem","indie dev"]
game: "line-inspector"
cover: "line-inspector-devlog06-title-best-tablet.png"
---
Hello, and welcome to the last Line Inspector devlog! In [Devlog #5](../line-inspector-devlog-5-testing/) we tested the game in four browser engines, let a bot play full runs in every one of them, and fixed seven bugs that only showed up when we read the code.

That was the last stage. Line Inspector 1.0 is finished, and you can [play it now](/games/line-inspector/). In this post we'll take one more walk down the line, share the numbers behind the game, and look back at what we learned making our second game.

![The Line Inspector 1.0 title screen on a tablet: a yellow LINE sign and a white INSPECTOR stamp, the tagline "Approve or reject. The rulebook changes every shift.", "BEST 1640 · 41 UNITS" in yellow, a green dotted critter and a three-eyed red robot in blue caps on the belt, and START SHIFT, HOW TO PLAY and CREDITS buttons above "v1.0.0"](line-inspector-devlog06-title-best-tablet.png)

*Version 1.0 on a tablet. The best score under the title was set by our test bot. It's there to be beaten.*

## The game, start to finish

If you've just arrived, here's Line Inspector in a paragraph. You're the quality inspector at the end of a toy factory line. Wind-up Robots, Bouncy Critters and Pocket Rockets roll under your lamp one at a time. Check each one against the rulebook. If it passes, swipe right (or press → or D) to APPROVE it into the box. If it breaks a rule, swipe left (or press ← or A) to REJECT it down the trapdoor. Three mistakes and the line stops.

The catch is in the tagline: the rulebook changes every shift. Each shift is ten toys, and each new shift adds a rule, changes one or drops one. A clipboard briefing shows you exactly what's different before the belt starts.

![The SHIFT 7 briefing clipboard on a phone: five rules, with "No yellow paint." highlighted orange as CHANGED and "Critters ship without antennas." highlighted green as NEW, "No longer checked: Hats must face forward.", "2.2 s per unit · 3 mistakes and you're off the line", and a START SHIFT button](line-inspector-devlog06-briefing-shift7-phone.png)

*The shift 7 briefing. Green paint is fine again, yellow isn't, critters lose their antennas, and you can stop worrying about hats.*

The time you get for each toy shrinks too: 4 seconds in shift 1, 0.3 seconds less every shift after that, down to 1.6 seconds from shift 9 on. By then the rulebook has five rules, and none of them is the one you started with.

![Shift 9 on a phone: a green dotted Pocket Rocket with two antennas and a backwards cap under the lamp with a yellow TIME! stamp, a STRIKE 1 banner reading "Too slow. It passed every rule.", one lit strike light, and a five-rule rulebook ending in "Four arms are for robots only." marked NEW](line-inspector-devlog06-shift9-timeout-phone.png)

*Shift 9, and a strike for hesitating. Green paint and a backwards hat would both have been trouble a few shifts ago. Now this rocket passes everything.*

## The end of the shift

When your third strike lands, the game-over card tells you exactly why you were stopped. Every mistake is listed with a drawing of the toy, its serial number, and the rule it broke, or the fact that it broke none.

![The SHIFT OVER clipboard on a desktop, with "The supervisor would like a word." under the title, three strikes for a Wind-up Robot, a Pocket Rocket and a Bouncy Critter, 45 units inspected, a score of 1810 with NEW BEST!, a best streak of 32, the share line with eight green and two red squares, and TRY AGAIN, COPY RESULT and MENU buttons](line-inspector-devlog06-game-over-desktop.png)

*A bot run on desktop. The supervisor's line changes from run to run; this time they'd like a word.*

Under that are your stats and a share line. COPY RESULT copies your toy count, your last ten calls as green and red squares, and your score, ready to paste into a chat. Your best score is saved in your browser and shown on the title screen.

## By the numbers

- **About 84 KB.** The whole game is a single script file.
- **Three files** to publish: a web page, the game script and a small icon. It also runs straight from your disk with a double-click.
- **Zero image or audio files.** Every toy, gear, stamp, sound effect and note of music is made by code while you play. The only outside asset is the free, open-licensed Orbitron font.
- **3 product lines, 10 rules, 9 rulebooks.** After shift 9 the rulebook stays put and only the clock keeps tightening.
- **1,620 different toys** the part kit can build, from eye count and antennas to paint, hats, bow ties and badges.
- **About 600 lines** of reusable engine code, carried over from Orbit Hop, plus about 3,150 lines for Line Inspector itself.
- **192 out of 192** automated checks passing in Chrome, Edge, Firefox and WebKit, at four screen sizes.
- **Six devlog posts**, and every screenshot in them came from a real build of the game.

## What we learned

**1. The second game starts faster.** We began Line Inspector with Orbit Hop's engine, screenshot tool and testing setup already in hand. That let us write and test the whole rulebook before drawing a single toy, instead of spending the first stage on plumbing.

**2. Make every mistake explainable.** Each faulty toy breaks exactly one rule, by design. That one decision is what lets the game-over card name the rule you missed, and a game that tells you *why* you lost is one you want to play again.

**3. Teach the change, not just the rule.** In a game like this, the hard part isn't learning a rule, it's unlearning one you've followed for three shifts. So the briefing highlights what's NEW, what's CHANGED and what's no longer checked, and right after a change, the changed rule is the one most likely to come down the belt.

**4. Don't rely on colour alone.** Several rules are about paint, so every paint has a pattern too, and a test fails the build if two colours could be confused. It cost us very little and makes the game playable for a lot more people.

**5. Bots should play like people, at least a bit.** A bot that plays a full run with real taps found nothing wrong. A bot that taps too early, the way a flustered person does, would have found our nastiest bug. We now write that kind of clumsy behaviour into our test bots on purpose.

**6. Somebody still has to read the code.** Just like on Orbit Hop, the most important bugs came from a careful read-through, not from automated tests. Robots check what you ask them to. People notice what you forgot to ask.

## Where to play

Line Inspector 1.0 is live, and you can [play it here](/games/line-inspector/). It runs in any modern browser on desktop, tablet or phone: swipe on a touch screen, or use the arrow keys, A and D, or drag with your mouse on a computer. No download and no account needed.

If you post a share line, we'd love to see how far down the belt you got.

## What we've got

- A finished swipe-and-sort game for desktop and mobile browsers
- A rulebook that changes every shift, with clear briefings and a game-over card that explains every mistake
- Colour-blind patterns, saved best scores and a share line
- Code-made art, music and sound effects in about 84 KB
- A reusable engine and project template, now tested in four browser engines
- Six devlog posts telling the whole story

## What's next

Line Inspector was the second game through our studio's pipeline, and it went more smoothly than the first. Now we're writing up what we changed and what we'd tweak again, so the next game starts faster still. When it does, we'll be back with a brand new devlog series.

Thanks for following along!
