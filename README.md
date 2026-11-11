# TidyMate

Shared chores for housemates. No account, no download.

An interactive prototype built for user testing: one mobile-first web app that runs in any phone or desktop browser and can be added to the home screen.

## The happy path

1. Name your home and add housemates by first name.
2. Pick a few starter chores. They repeat weekly and take turns.
3. Send one invite link to the group chat. Housemates open it and tap their name.
4. Tick chores off, pick dates, and nudge whoever is up next through the phone's share sheet.

## Design decisions

- **No login.** A household is joined through a link, and people are identified by first name only. Sign-up is the biggest drop-off point for a shared-chore app, since every housemate has to get through it.
- **Nudges use the share sheet.** Reminders go to the chat app the house already uses, so no notification permission is needed.
- **One primary action per screen.** Chores, Activity, Home. Nothing else.
- **Privacy by default.** No tracking, analytics, ads, or server. Data is stored only in the browser (`localStorage`). An invite link carries a copy of the chores and first names in the URL fragment, which browsers do not send to any server.

- **The handoff is the hook.** Ticking a chore off plays a tick animation, names who is up next, and offers one tap to tell them. The app does the reminding so housemates don't have to.
- **One shared streak, no leaderboard.** The house keeps a single count of chores finished on time in a row. Everyone protects the same number, so nobody gets ranked or shamed.
- **Up to 4 people per house** for this test round.

The mascot image is a low-resolution stand-in cropped from a design mockup and should be replaced with the exported artwork. Type is Bricolage Grotesque (SIL Open Font License), self-hosted so no font request leaves the site.

## Known limits of this prototype

- Each device keeps its own copy. Changes do not sync live; re-sending the invite link shares an update.
- Nudges are sent manually. There are no scheduled push notifications.

Live sync needs a small backend and is the next step after user testing.

## Run locally

Open `index.html`, or serve the folder:

```bash
python3 -m http.server 4174
```

Plain HTML, CSS and JavaScript. No build step, no dependencies.
