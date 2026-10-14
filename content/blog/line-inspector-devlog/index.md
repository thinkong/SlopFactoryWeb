---
title: "Line Inspector Devlog: A Rulebook That Changes Every Shift"
date: 2026-10-14T07:00:00.000Z
slug: "line-inspector-devlog"
aliases:
  - /blog/line-inspector-devlog-1-the-idea/
  - /blog/line-inspector-devlog-2-setting-up/
  - /blog/line-inspector-devlog-3-first-playable/
  - /blog/line-inspector-devlog-4-look-and-feel/
  - /blog/line-inspector-devlog-5-testing/
  - /blog/line-inspector-devlog-6-launch/
summary: "How we built Line Inspector: a rulebook tested by bots before any art, toys drawn in code, colour-blind patterns, a reactive soundtrack and the bugs a code read found."
tags: ["line inspector","devlog","html5 games","game design","game testing","indie dev"]
game: "line-inspector"
cover: "line-inspector-devlog-streak-confetti-phone.png"
---
[Line Inspector](/games/line-inspector/) puts you at the end of a toy factory line. Wind-up Robots, Bouncy Critters and Pocket Rockets roll under your lamp one at a time, and you make one call on each: swipe right to approve it into the box, or left to reject it down the trapdoor. What counts as faulty is written in the rulebook, and the rulebook changes every shift. Three mistakes and the line stops.

This post covers the decisions behind it: designing levels out of rules, testing those rules with bots before any art existed, the code-drawn factory and its soundtrack, and the bugs we only found by reading the code. Every screenshot comes from a real build of the game.

![Shift 4 on a phone: a green dotted rocket over the open trapdoor, with confetti, a "5 IN A ROW!" banner, +40 and +50 score pops, and an orange STREAK 5 ×5 badge under the score](line-inspector-devlog-streak-confetti-phone.png)

*Five right calls in a row. The green rocket breaks "No green paint", so down the trapdoor it goes.*

## The rulebook is the level design

Most of the design work in Line Inspector is in the rules. There are eight of them, each checking one easy-to-see part of a toy: eyes, antennas, arms, paint colour or accessory. Each shift is ten toys, and between shifts the rulebook changes in one of three ways.

- **Rules get added**, so there's one more thing to look at.
- **Rules get changed.** "Exactly two eyes" becomes "two or three eyes", and "No green paint" becomes "No yellow paint". Your hands have learned the old rule, and now you have to unlearn it. That's where the game gets interesting.
- **Rules get retired**, so the rulebook never grows past six lines.

Meanwhile the clock tightens, from 4 seconds per toy in shift 1 down to 1.6 seconds from shift 9 on.

![The SHIFT 7 briefing clipboard on a phone: five rules, with "No yellow paint." highlighted orange as CHANGED and "Critters ship without antennas." highlighted green as NEW, "No longer checked: Hats must face forward.", "2.2 s per unit" and a START SHIFT button](line-inspector-devlog-briefing-shift7-phone.png)

*The shift 7 briefing. Green paint is fine again, yellow isn't, and you can stop worrying about hats.*

Since unlearning is the hard part, we teach the change, not just the rule. Every briefing tags rules as NEW, CHANGED or NO LONGER CHECKED, the full rulebook stays on screen as a strip while you play, and right after a change the changed rule is the one most likely to come down the belt. It's a test of attention and speed, not memory.

## Every mistake has a reason

We made the player one promise that everything else depends on: a faulty toy always breaks **exactly one** rule. That way, when you get a strike, the game can always tell you which rule you missed.

![Shift 9 on a phone: a green dotted Pocket Rocket with two antennas and a backwards cap under the lamp with a yellow TIME! stamp, a STRIKE 1 banner reading "Too slow. It passed every rule.", one lit strike light, and a five-rule rulebook ending in "Four arms are for robots only." marked NEW](line-inspector-devlog-shift9-timeout-strike-phone.png)

*A strike for hesitating in shift 9. Green paint and a backwards cap were trouble a few shifts ago; now this rocket passes everything.*

Our first toy maker built random toys and kept trying until one broke the rule it wanted. That nearly always worked, but "nearly" isn't a promise. The part kit can build 1,620 different toys, so now the game lists them all once at startup and, for each toy it needs, shortlists only those that break exactly the target rule (or none, for a good toy). The promise is true by design, and our tests check that no shortlist is ever empty. The smallest one still has 36 toys in it.

When the third strike lands, the game-over card lists every mistake with a drawing of the toy and the rule it broke. A game that tells you *why* you lost is one you want to play again.

## Rules first, art second

We wrote the whole game as plain logic before drawing anything: parts, rules, the shift schedule, the timer, strikes and scoring. Each rule is one line holding the text the player reads next to the check the game runs, so the two can't drift apart.

```ts
noGreen: { text: "No green paint.",
  pass: (u) => u.paint !== "green" },
hatForward: { text: "Hats must face forward.",
  pass: (u) => u.accessory !== "hat" || !u.hatBackwards },
```

That meant bots could play the game before it had graphics. Our level check plays 300 random runs, 45,000 toys in all, and fails the build if anything looks wrong. A perfect inspector has to survive every shift, even with a slow 1.2-second reaction time, so no shift is impossible. A bot that never answers must lose on exactly three timeouts. A "human" bot reads rules at a realistic speed and makes the occasional mistake; at the fastest timer it took a typical 1.09 of the 1.6 seconds, which felt tense but fair. The check even measures details on a small phone screen and fails if any rule's detail gets too small to see.

The game also reused our engine from Orbit Hop without changing a byte. The engine only knows one button; left and right live in the game's own controls file, so the engine stays the same for every game.

## A factory drawn in code, with a groove

There are no image or audio files in Line Inspector. Every toy, gear, box and stamp is drawn by code, and the whole game is a single script of about 84 KB. The look is chunky toys with thick outlines against a steel-blue factory wall, with hazard stripes, inked rubber stamps and clipboards for the menus.

![The prototype inspection screen in shift 1: a flat yellow robot under a grey light cone, a plain belt and a simple OK box](line-inspector-devlog-belt-before-phone.png)

*Before: shift 1 in the prototype. It played well, but it didn't feel like a place.*

![The production inspection screen in shift 1: a striped yellow critter in a backwards blue cap under the lamp, gears on the wall, a belt with rollers and chevrons, a dashed trapdoor outline, a cardboard OK box with a green tick and a STREAK 2 ×2 badge under the score](line-inspector-devlog-belt-after-phone.png)

*After: the same moment in the finished game, with gears, a moving belt, a trapdoor and a proper OK box.*

Several rules are about paint, so colour alone wasn't enough. Every paint now has a pattern too: yellow gets stripes, green gets dots. A test simulates the most common type of colour blindness and fails the build if two paints would look alike and share a pattern. It cost very little and makes the game playable for a lot more people.

The sound is synthesised live as well. The stamp is a wooden thud and a paper slap, approvals ding higher as your streak grows, and a strike is a two-tone buzzer. The music is a short factory groove with a plucked bass, wood block and marimba. A kick drum and hi-hat join when you're on the belt, a shaker and a second melody come in at a streak of five, and every shift nudges the tempo up, from 104 to a cap of 130 beats per minute, so the music keeps pace with the shrinking timer.

## Four browser engines, and what reading the code found

For testing, a bot opens the game in Chrome, Edge, Firefox and WebKit (the engine behind Safari) at desktop, phone, sideways-phone and tablet sizes, with real touch input on touch sizes. It plays three full shifts correctly, then makes three mistakes on purpose, one of each kind, and checks that the game-over card and best score come out right. All 192 checks pass.

The bots passed everything. Reading the code by hand still found seven bugs. Our favourite: the big TRY AGAIN button on the game-over card sits almost exactly where APPROVE and REJECT were a moment earlier.

![The SHIFT OVER card on a phone: three strikes, 47 units inspected, a score of 2000 with NEW BEST!, a best streak of 36, the share line, and a large yellow TRY AGAIN button low on the screen, about where the call buttons sit during play](line-inspector-devlog-game-over-try-again-phone.png)

*The TRY AGAIN button lands right under the thumb that was just making calls.*

A tap a fraction of a second late could throw you into a new run before you'd seen why you lost. Our bot waits politely for each screen; a flustered player doesn't. The card now ignores taps for its first 0.6 seconds, and the bot has a new job: tap early and check that the card stays put. Another fix: older iPhones only switch sound on if a sound actually starts during your first tap, so that tap now plays one silent sample to wake the audio up.

## What we learned

Starting from a tested engine let us spend the first stage on the rulebook instead of plumbing, and that's where this game's design lives. Bots are brilliant at checking a rulebook thousands of times, but they should play a little like people, clumsy taps included, and somebody still has to read the code.

Line Inspector runs in any modern browser, on phone or desktop. [Clock in for a shift](/games/line-inspector/) and see how far down the belt you get.
