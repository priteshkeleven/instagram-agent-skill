---
name: ig-plan
description: >-
  Build the week on Instagram - what to post, which format, when, and who to
  engage with. Use when the user says "plan my week", "what should I post",
  "content calendar", "I have nothing to post about", or wants a posting
  schedule and an engagement list.
---

# ig-plan

The control room. Everything else in this pack executes; this decides what gets
executed. Run it once a week, on the same day.

## Account

This pack can run several Instagram accounts, each in its own folder at
`~/.claude/instagram/<account>/`. Work out which one this request is for
before anything else: the account named in the request, otherwise the name in
`~/.claude/instagram/active`, otherwise the only account folder there is.
If none of those settles it, ask. Never guess, and never read one account's
files for another. If there is no account folder yet, set one up with
`/ig-account` first.

Reads `account.md`, `voice.md`, `swipe.md` and `log.md`. Writes `plan.md`.

Put the account on the first line of the output: `ACCOUNT  pullsy  (@handle)`.

## Input

Read the account's `account.md`, `voice.md`, `swipe.md` and `log.md`, whichever
exist. The swipe file is the user's own evidence from `/ig-viral` about which
formulas are landing in their niche right now, and it outranks anything in
this file. The log stops the plan repeating a theme from the last fortnight.

`account.md` should already hold what the account sells and to whom, its three
or four themes, its audience's timezone, and the ten accounts worth being
visible to. Ask for whichever of those is missing and write the answers into
`account.md`, not into the plan, so next week starts with them.

Then ask, every week, for the one thing no file can hold: what actually
happened this week. A client call, a number, a mistake, a thing they built, an
argument they had. This is where posts come from.

## What to post

Four to five posts a week, and at least three of them Reels. Reels are the only
format on Instagram that reliably reaches people who do not follow the account.
Carousels go deep with the people who already do. Stories are daily and are
planned separately.

Mix across the week, never two of the same type back to back:

| type | share | job |
| --- | --- | --- |
| **Proof** | 1 per week | something that happened, with a number. Reel. |
| **Teach** | 1 to 2 per week | one thing the viewer can do today. Reel or carousel. |
| **Opinion** | 1 per week | a position that could lose you followers. Reel. |
| **Story** | 1 per fortnight | a scene with a cost. Reel. |
| **Offer** | 1 per fortnight | what you sell, said plainly, no apology. Carousel or stories. |

For each slot give: the theme, the specific angle from what actually happened
this week, the format, and the hook formula number from `ig-reel/hooks.json`.
Not a topic, an angle. "AI" is not a plan. "The proposal we lost because the
draft had an em dash in it" is a Reel.

## When to post

Post when the user's audience is awake and not at work. For most consumer
audiences that is early evening local time; for a business audience, early
morning.

But say this plainly: **the hour matters far less than the first two seconds.**
Instagram will keep showing a Reel for days if it performs, and will bury a
well-timed one that does not. If the user is optimising posting times before
their hooks work, they are polishing the wrong thing, and you should say so.

Anchor times to the audience's timezone, not the user's, if those differ.

## The engagement round, which is not optional

20 minutes a day, before posting, not after. Build a list of 10:

- **5 reach** - accounts with an audience the user wants, where a good comment
  gets seen. Comment early, before the thread is 200 deep.
- **3 peers** - same size, same field. This is the group that reciprocates.
- **2 buyers** - people who could actually buy. Comment for weeks before any
  DM, and never pitch in a comment.

Hand the list to `/ig-comment`.

## Output

```
ACCOUNT  pullsy  (@pullsy.app)
WEEK OF SEP 15

MON  engage only  (20 min, list below)
TUE  7:30pm  REEL      PROOF    #5  Time Collapse   - 5hr proposal to 20 min
WED  stories only + engage
THU  7:00pm  CAROUSEL  TEACH    Job B caption       - the 4-slide clause breakdown
FRI  7:30pm  REEL      OPINION  #2  Negative Command - stop doing discovery calls
SAT  -
SUN  6:00pm  REEL      STORY    #21 Mid-Sentence    - the refund email

STORIES  every day, 3 to 5 frames, question box on Thursday.

ENGAGE  (5 reach / 3 peers / 2 buyers)
  ...

Say "write Tuesday" and I will draft it.
```

Write the plan to `~/.claude/instagram/<account>/plan.md` so the other skills can read
it. Nothing is scheduled or posted anywhere. This is a plan and the user runs
it.
