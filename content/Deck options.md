---
tags:
  - ✅
published: true
sr-due: 2025-08-02
sr-interval: 792
sr-ease: 285
---

⬅️ [[Deep dive into Anki]]


Deck options are accessed by:
- Clicking the gear icon on the Decks screen.
- Selecting a deck on the Decks screen, and then clicking Options at the bottom of the screen.
- Clicking on More > Options while in review mode.
- Pressing o while in review mode.

## Presets
- By default, all newly created decks use the same preset.
- you can change/add/delete the preset inside deck options

## Subdecks
- If your deck has subdecks, each deck can optionally be assigned a different preset.

## Daily limits
- Studying new cards will temporarily increase the number of reviews you need to do a day, as freshly learnt material needs to be repeated a number of times before the delay between repetitions can increase appreciably.
-  If you are consistently learning 20 new cards a day, you can expect your daily reviews to be roughly about 200 cards/day.
-  It is recommended you hold off on new cards until you catch up instead, as introducing more new cards when you're behind will only make the backlog worse.

## Maximum Reviews/Day
- Allows you to set an upper limit on the number of reviews to show each day. 
- When this limit is reached, Anki will not show any more review cards for the day, even if there are some waiting.

## New Cards
- Controls the number of learning repetitions, and the delay between them.
- Each time you press `Good` during review, the card moves to the next step.

## Intervals
Graduating Interval: 
- The delay in days between answering "Good" on a learning card with no steps left, and seeing the card again as a review card. 

Easy interval:
- The delay between answering Easy on a learning card, and seeing it in review mode for the first time.
- The `Easy` button immediately turns a learning card into a review card, and assigns it the delay you have configured. 
- It should always be at least as long as the _graduating interval_, and typically a few days longer.

## Lapses
- When you forget a review card, it is said to have 'lapsed', and the card must be relearnt.
-  The default behaviour for lapsed reviews is to reset the interval to 1 (i.e. make it due tomorrow), and put it in the learning queue for a refresher in 10 minutes. 

## Display order
New Card Gather Priority:
- Controls how Anki gathers cards from each subdeck.

Interday Learning/Review Priority
- Whether learning cards with a 1+ day delay should be mixed in with reviews, or shown before or after them

Review Sort Order
- The default order prioritizes cards that have been waiting longer, which works well when you are up to date, or when you only have a small backlog.

## Advanced
Maximum Interval:
- Allows you to place an upper limit on the time Anki will wait to reshow a card. The default is 100 years;

Starting ease:
- Controls the easiness that cards start out with. It is set when a card graduates from learning for the first time.
-  It defaults to 2.50, meaning that once you have finished learning a card, answering `Good` on subsequent reviews will increase the delay by approximately 2.5x

Easy bonus:
- With the default value of 1.30, Easy will give an interval that is 1.3 times the Good interval

Interval modifier:
- An extra multiplier that is applied to all reviews. At its default of 1.00 it does nothing. If you set it to 0.80, though, for example, intervals will be generated at 80% of their normal size (so a 10 day interval would become 8 days).
- Once you have an idea about retention rate, [fiddle with settings](https://docs.ankiweb.net/deck-options.html#interval-modifier)

Hard interval:
- what happens when you press `Hard`

New interval:
- what happens when you press `Again`
- The default 0.00 means that a review card's delay is reset to zero when you forget it