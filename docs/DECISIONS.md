# Decision log

Newest first. Each entry: what was decided, why, and what was rejected. These are the talking points for the case study.

## 2026-11-13: Bubbles added to Option B; shared database planned before testing

**Why:** owner liked B's sticker-press look and wanted A's bubbles in it. B now has the ambient drifting bubbles and a fizz of bubbles when a chore is ticked (still switched off for people who set "reduce motion").
**Sync plan (proposed, not yet built):** Firebase Firestore, a hosted database that pushes changes to every phone live. Anonymous sign-in (no login screen, keeps "join by link and first name"). Each house is one document under an unguessable ID carried in the invite link. Runs from GitHub Pages with no build step.
**Rejected:** Supabase (also good, but its free projects pause after a week of inactivity, which would break a test mid-way); keeping data in each phone (what we have now, nothing syncs); a custom server (more to run for no gain).
**Trade-off:** anyone holding the link can edit that house. Fine for a friends test; revisit before public launch.

## 2026-11-13: Option B built, "Sticker press", from Inspo references

**What:** `design/option-b.html`, a copy of the live app with a style layer on top, added to the compare page. Buttons, chips and tick circles have a hard offset shadow and physically press down on tap (shadow collapses, element drops 3px). The streak pill and the "is done" heading become tilted yellow stickers with a dark edge. Cards get a dark outline and a solid shadow.
**Why:** Mobbin was unavailable, so research used Inspo (inspomcp.dev), an archive of real website captures. Playful references (MoMoney, Analogue, Hey, Buttondown) share chunky offset shadows, sticker-like labels, big rounded type and one full-width action. Those became the cues. Option A is about ambient motion; B is about how touch feels, so the two are distinct to compare.
**Limit to be honest about:** Inspo holds marketing websites, not in-app screens, so B borrows visual attitude, not app-flow patterns. It cannot tell us how chore apps handle handoffs. Mobbin would.
**Guard rails:** nothing loops; press is 90ms; reduced motion switches transitions off. Colour and type unchanged so only feel differs. Dark outlines on cards are heavier than "calm first" may want, so that is the main thing to judge.
**Rejected:** copying a site's layout (they are landing pages); adding new colours (yellow stickers are the only addition and would need to become a token if kept).
**Open:** owner picks between current, A and B (or mixes: A's bubbles with B's press).

## 2026-11-13: Interaction explored as two options beside the live app

**Why:** the owner likes the current onboarding and wants to compare alternatives before committing. Option A ("Living bubbles") and Option B (shaped by Mobbin references) are separate files in `design/`, so the live `index.html` is untouched. Both keep the blue palette and Bricolage type so only interaction differs, the same fair-comparison rule as the visual directions.
**Option A, built:** bubbles drift in a fixed layer outside the app, because the app rebuilds the whole screen on every tap and that would restart any animation inside it. Entry animations play only when the view actually changes. Motion lengths are named values (fast 150ms, base 300ms, slow 500ms), a preview of phase 2 tokens. Bubbles are fainter inside the app than on the welcome screen ("calm first"), pause when the tab is hidden, and switch off under reduced motion.
**Guard rails:** nothing loops except the bubbles and the mascot bob; no animation delays a tap.
**Rejected:** animating inside the rebuilt screen (restarts on every tap); a heavier bubble effect on every screen (distracts from the chores).
**Open:** Option B waits on Mobbin, whose connector was failing and is not available in this session.

## 2026-11-12: Visual directions compared on real screens, with only colour and type changing

**Why:** a palette on its own says little. Putting three options (Splash, Marmalade, Grape soda) on the same Chores and Chore done screens, with identical content and layout, makes the comparison fair and lets each be judged against the brief's principles. Each direction is just a set of variables, which previews how tokens will work in phase 2.
**Also decided:** in every direction the main button and selected states use the brand colour, not black, to honour "black is for text only".
**Rejected:** mood boards or swatch sheets alone, and changing layout between options, which would muddle what is being compared.
**Research added after the first draft:** the options were first drawn from the brief alone. A look at 11 competing apps (`docs/RESEARCH.md`) then showed blue and green dominate, purple is not rare, and many competitors sell competition. That corrected the claim that violet was the most distinctive option and confirmed type as the place to stand out.
**Open:** which direction the owner picks.

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

## 2026-11-13: Live sync with Firebase (Firestore + anonymous sign-in)

**What:** each house is one Firestore document keyed by a 20-character random code. Phones sign in anonymously (no passwords). The invite link is `#house=<code>`. Which member you are ("me") stays on your own device.
**Why:** free tier, live updates between phones, works with a plain HTML site (no build step), and the owner wanted a public link for testing.
**Rejected:** Supabase (more setup for no gain at this size); keeping the whole house inside the URL (phones never stayed in step).
**Trade-offs:** the last phone to save wins if two people edit within a second, which is fine for four housemates. Anyone holding the code can edit that house. Rules are in `firebase/firestore.rules`.

## 2026-11-14: Visual and interaction direction: Option B, sticker press

**What:** Option B (`design/option-b.html`) is the direction for the app. It is already shipped as `index.html`, with the ambient bubble layer and tick fizz ported in from Option A.
**Why:** the owner chose it after reviewing it live. It gives chores a tactile, rewarding press without making the app feel like a game, which fits the principle "a house, not a competition".
**Rejected:** the previous look (current prototype), and Option A (living bubbles) as the main style. Its bubbles live on inside B as a light ambient layer.

## 2026-11-14: Invite links show an "Opening your house" state and visible errors

**What:** tapping an invite link on a phone with no house now shows "Opening your house…" instead of Welcome. If sign-in fails, the lookup hangs (12 s) or the house is missing, the same screen shows a message with Try again and Start over.
**Why:** a housemate tapped a link and saw onboarding with no explanation. The code only displayed join errors on the paste screen, and Welcome drew before the cloud connection was ready.
**Rejected:** a bare spinner with no timeout (hangs forever on a bad connection); keeping the invite in sessionStorage (does not fix the silent failure).
**Not yet confirmed:** the exact cause on the owner's phone. Check which app opened the link and whether the house was created before live sync. See `docs/FLOWS.md`.

