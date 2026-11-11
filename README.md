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
