---
name: ig-account
description: >-
  Set up, list and switch between the user's Instagram accounts, so every other
  skill in the pack works from the right voice, swipe file, log and plan. Use
  when the user says "add an account", "switch to X", "which account", "list my
  accounts", "I run more than one Instagram", or names an account the pack has
  not seen before.
---

# ig-account

Every other skill in this pack reads and writes files about one account: how
it sounds, what is working in its niche, what it has posted, what it plans to
post. Two accounts sharing those files is how the founder's voice ends up in
the brand's captions. So each account gets its own folder, and nothing is
shared between them.

## The layout

```
~/.claude/instagram/
  active                 one line: the name of the account in use
  pullsy/
    account.md           who it is, what it sells, themes, audience, engage list
    voice.md             how it sounds (templates/voice.md)
    swipe.md             written by /ig-viral
    log.md               written by /ig-reel, /ig-comment, read by /ig-audit
    plan.md              written by /ig-plan
  personal/
    ...
```

The account name is a short lowercase slug the user picks: `pullsy`,
`personal`, `client-acme`. It is not the handle. The handle lives in
`account.md`, because handles change and folder names should not.

## Which account a request is for

Every skill resolves the account the same way, in this order:

1. **Named in the request.** "for pullsy", "on @pullsy.app", "personal
   account". Match the folder name or the handle in any `account.md`.
2. **The active account.** The name in `~/.claude/instagram/active`.
3. **The only account.** If exactly one account folder exists, use it.
4. **Ask.** Never guess, and never fall back to another account's files
   because the right one is missing something.

Naming an account in a request does not change `active`. Only this skill does.

Every skill states the account on the first line of its output, so a wrong one
is caught before anything is written:

```
ACCOUNT  pullsy  (@pullsy.app)
```

## What this skill does

**Add.** Ask in one batched message:

1. A short name for the folder, and the handle.
2. What the account sells, and to whom.
3. The three or four themes it wants to be known for.
4. Where the audience is (country and timezone) and whether it is consumers,
   creators or businesses.
5. Roughly how many followers it has today. `/ig-viral` uses this to pick
   accounts within 10x of its size.
6. Three of its own reels or captions, to write `voice.md` from. If it has
   none yet, ask how it should sound instead.

Write `account.md` from `templates/account.md` and `voice.md` from
`templates/voice.md` in the account's folder. Leave a field blank rather than
inventing it. If it is the first account, also write its name to `active`.

**List.** Show every account folder with its handle, which one is active, and
which files exist in it. A missing `voice.md` is worth pointing out, because
every writing skill falls back to asking without it.

**Switch.** Write the new name to `active` and confirm with the account line.

**Rename.** Move the folder and update `active` if it pointed at the old name.

**Move legacy files.** If `voice.md`, `swipe.md`, `log.md` or `plan.md` sit
directly in `~/.claude/instagram/`, they predate accounts. Ask which account
they belong to, move them into its folder, and say what moved. Until they are
moved, treat them as an account called `default`.

## Never

Do not copy one account's voice, swipe file or log into another's, even as a
starting point, unless the user asks for it in so many words. Two accounts in
the same niche still have different evidence.

Do not log into Instagram to read an account. The user pastes or screenshots
what it needs.
