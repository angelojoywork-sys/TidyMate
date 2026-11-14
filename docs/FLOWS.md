# User flows and smoke checklist

A **user flow** is the path a person takes to finish one goal. Each flow below has a start state, the steps, the expected result and the ways it can fail. Use them to plan usability tests (Phase 5) and as a 5-minute check on real phones after each release.

## 1. Create a house
Start: no saved house. Welcome → Get started → house name and your name → add housemates (up to 4 total, can skip) → pick starter chores → Today.
Expect: Today shows the chores, assigned in rotation.
Fails: empty names (form blocks), more than 4 people (blocked, "full house").

## 2. Invite and join (tap a link)
Start: housemate has a link from House → Invite.
Steps: tap link → "Opening your house…" → "Join <house>" → pick your name or add yours → Today.
Failure branches (each now shows a message, never a silent Welcome):
- No connection or blocked sign-in: "Couldn't reach the house" with Try again / Start over.
- Lookup hangs: same message after 12 seconds.
- House not found (wrong code, never uploaded): "We couldn't find that house" on the Join screen from Paste.
- House full (4): join screen says so.
- Phone already has another house: link is handled after load; check the result.
- Link was cut by the chat app (the `#house=` part is missing): opens Welcome. Use flow 3.

## 3. Join by pasting
Welcome → Join house → paste link → Join screen. Fails: text that is not an invite shows an error.

## 4. Daily use
Complete a chore → rotates to next person → second phone shows it within a few seconds.

## 5. Housemate changes
Add, edit, delete a chore; add or remove a member; leave or reset the house.

## 6. Return visit
Reopen with a saved house → Today. After clearing browser storage the phone forgets who "me" is and must join again with the link.

## Smoke checklist (real phones, ~5 min)
- [ ] iPhone: tap a fresh invite link in WhatsApp → Join screen appears (not Welcome)
- [ ] Android: same
- [ ] Airplane mode, tap link → "Couldn't reach the house", Try again works once online
- [ ] Complete a chore on phone A, see it on phone B
- [ ] Create a house from scratch at 375px width, no clipped text
