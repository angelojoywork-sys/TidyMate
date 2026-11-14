# Plan: Google sign-in, easy invites, and a free public launch

## Context
Today the app uses Firebase **anonymous** sign-in. Each phone is a random ghost user, so we can't tell who is who, invites are just a secret 20-character code in the link (`#house=<code>`), and anyone with the code can edit the house (`firebase/firestore.rules`, `index.html` ~lines 305-345, 638-654). To sell this later it needs real identity, safe sharing, a stable address, and to feel like an app without a download.

Owner decisions (2026-11-14): Google **or** guest sign-in; link joins instantly; host on Firebase Hosting (free domain); first public version includes PWA install, push nudges, multiple houses per person, and leave/delete account.

## Key idea (plain language)
Firebase already has an anonymous user per phone. "Linking" upgrades that same user to Google **without changing their ID**, so guests keep their house when they later sign in. That is why "Google or guest" is cheap here. (A term for GLOSSARY: *account linking*.)

## What "production-ready for a sellable product" means
1. **Identity**: who is this person (Google or guest).
2. **Authorization**: only house members can read or write a house (today: anyone with the code).
3. **Sharing**: one link, works from WhatsApp/iMessage, owner can revoke it.
4. **Reach**: stable URL, installable, works on a flaky connection.
5. **Trust**: privacy policy, delete-my-data, no surprise costs.
6. **Observability**: know when it breaks (errors, usage), without tracking people.

## Data model (new)
- `users/{uid}`: `{name, photo, houses: [houseId], createdAt}`
- `houses/{houseId}`: existing fields + `ownerUid`, `memberUids: [uid]` (max 4 today), each member entry gets `uid`
- `invites/{code}`: `{houseId, home, createdBy}`. Link becomes `/#join=<code>`. Owner can "reset link" (delete the invite, create a new one).
- Joining = a write that adds your uid to the house, allowed by rules only if a valid invite exists. Unauthorised people can't read the house first.
- Migration: existing test houses (a handful) are re-created or reset; rewrite is not worth a migration script. Confirm with owner before wiping.

## Security rules (replace `firebase/firestore.rules`)
- house read/write: `request.auth.uid in resource.data.memberUids`
- join: update only adds your own uid, and a matching `invites/{code}` exists
- owner-only: remove another member, reset invite, delete house
- users: you read/write only `users/{yourUid}`
- Keep the existing size/shape limits. Turn on **App Check** (reCAPTCHA) later to block scripted abuse.

## Onboarding flow (replaces Welcome screen)
1. Welcome: **Continue with Google** (primary) · **Continue as guest** (secondary text button).
2. If arriving via invite link: show "You're invited to *<house>*" first, then sign-in, then pick your name (pre-filled from Google), then in.
3. Create house: name house, add housemates, share link (existing flow, now owner = you).
4. Guest banner in House tab: "Save your spot: sign in with Google" (links the account).
5. House tab: members list with photos, owner can remove, **Leave house**, **Delete my account**, **Reset invite link**, house switcher.
6. Known trap: Google blocks sign-in inside WhatsApp/Instagram in-app browsers (`disallowed_useragent`). Detect it and show "Open in Safari/Chrome" with guest as the fallback. This is the strongest argument for keeping guests.

## Phases (each one session; update roadmap after each)
- **A. Hosting + domain** (Firebase Hosting, `tidymate-ce977.web.app`, `firebase.json`, authorised domains, redirect GitHub Pages to it). Keep pushing from `main` via GitHub Action or `firebase deploy`.
- **B. Auth + data model + rules** (Google provider, linking, `users`, `memberUids`, new rules, rules tests with the Firebase emulator).
- **C. Onboarding + invite UX** (screens above, in-app-browser detection, member avatars, leave/remove/reset). Design the new screens first using existing tokens/components; ask owner before changing visuals.
- **D. PWA**: complete `manifest.json` (icons 192/512, maskable), service worker for offline shell, install prompt, iOS "Add to Home Screen" hint.
- **E. Push nudges**: FCM web push; "your turn" and "chore done" notifications. Needs a server step (Cloud Function) = **Firebase Blaze plan (pay-as-you-go, needs a card, free tier is generous, set a budget alert)**. iPhone push only works after install to Home Screen (iOS 16.4+). Decision needed at start of this phase.
- **F. Launch hardening**: privacy policy + terms pages, Google OAuth consent screen set to "In production" (basic scopes need no review; otherwise capped at 100 test users), budget alerts, Crashlytics-style error logging (or none), cost check, e2e tests (Playwright, already in roadmap Phase 5).
- **G. Later (when selling)**: custom domain, field-level writes instead of last-writer-wins, plans/billing (Stripe), App Store wrapper only if needed.

## Free-tier reality (Spark plan, no card)
Firestore: 1 GB, 50k reads + 20k writes per day. Hosting: 10 GB/month. Auth: Google sign-in free. Enough for hundreds of houses. Push (phase E) is the first thing that needs a card.

## Tension to record in DECISIONS.md
- Principle 5 "Nothing to sign up for" becomes "Joining is one tap; Google or just a first name".
- Privacy note in House tab ("No account, email or password") must be rewritten: we now store Google name, photo, and email only to identify members.
- Analytics: PRODUCT says no tracking. Decide separately; default is none.

## Critical files
`index.html` (module script + sync + onboarding views), `firebase/firestore.rules`, `manifest.json`, `PRODUCT.md`, `docs/DECISIONS.md`, `docs/ROADMAP.md`, `docs/FLOWS.md`, new `firebase.json`, `sw.js`, `privacy.html`.

## Owner actions needed (I can't do these)
Firebase console: enable Google provider, add support email, add authorised domain, (later) upgrade to Blaze. Log in to `firebase` CLI once (`firebase login`).

## Verification
Serve with `python3 -m http.server 4174`; Firebase emulator for rules tests (non-owner cannot read/write; joiner needs valid invite; reset invite kills old link); two real phones: Google sign-in, guest join via WhatsApp link, guest→Google upgrade keeps house, leave/delete; Lighthouse PWA check; check at 375px.
