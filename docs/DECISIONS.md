# Decision log

Newest first. Each entry: what was decided, why, and what was rejected. These are the talking points for the case study.

## 2026-11-12: Code tokens are the source of truth; Figma mirrors them

**Why:** one place to change a value, and the owner learns how design and code connect. Names are identical in both so a token can be discussed without translating.
**Rejected:** designing in Figma first and hand-copying values into code, which drifts as soon as either side changes.

## 2026-11-12: Black-heavy look dropped in favour of vibrant colour

**Why:** owner feedback. The brief asks for calm and playful; large black areas read as stark. Black stays for text.
**Open:** exact palette, chosen in phase 1.

## 2026-11-11: The handoff is the core interaction

**Why:** the problem is a communication gap, so finishing a chore names who is next and offers one tap to tell them.
**Rejected:** reminders only, which still leave someone to do the nagging.

## 2026-11-11: One shared house streak, no leaderboard

**Why:** principle "a house, not a competition". Competing apps rank housemates with points, which invites the drama this app is meant to remove.
**Rejected:** per-person points and a weekly winner.

## 2026-11-11: No login; join by link and first name

**Why:** every housemate has to get through sign-up for a shared app to work, so sign-up is the biggest drop-off risk.
**Trade-off:** without accounts or a server, each phone keeps its own copy and changes do not sync live. Accepted for the prototype.

## 2026-11-11: Nudges go through the phone's share sheet

**Why:** reaches people in the chat app they already use and needs no notification permission.
**Trade-off:** nudges are manual, not scheduled.

## 2026-11-11: Web app, not a native app

**Why:** one build runs on every phone and desktop, opens from a link, and needs no app store.
**Rejected:** a native iOS app, which could not ship quickly and would exclude Android housemates.

## 2026-11-11: A house holds up to four people

**Why:** matches the first test house and keeps layouts simple for now. Revisit after testing.
