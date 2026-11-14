# Roadmap

Each phase is sized to fit one working session. Tick items as they finish. The "You learn" line says what the owner should understand by the end of the phase.

## Phase 0: Prototype and setup (done)

- [x] Working prototype live on GitHub Pages
- [x] Product brief (`PRODUCT.md`)
- [x] Project guide, roadmap, decision log, glossary

## Phase 1: Visual direction

- [x] Two or three colour and type directions shown side by side on real screens (`design/directions.html`)
- [x] Owner picks one: Option B (2026-11-14, see decision log)

You learn: how a brief turns into a visual direction, and how to judge options against principles instead of taste.

## Phase 1b: Interaction direction (exploration beside phase 1)

- [x] Option A, living bubbles (`design/option-a.html`)
- [x] Compare page with current, A and B slot (`design/options.html`)
- [x] Option B, sticker press (`design/option-b.html`), researched with Inspo because Mobbin was unavailable; built before the owner check-in, so review it
- [x] Bubbles ported into B (ambient layer plus tick fizz)
- [x] Owner picks: Option B (2026-11-14, see decision log)

You learn: how motion changes the feel of an app, and how to keep it from distracting.

## Phase 2: Design tokens

- [ ] Token file in code: colour, type, spacing, radius, shadow, motion
- [ ] Two layers: raw values (primitives) and named roles (semantic tokens)
- [ ] Same tokens created as Figma variables in a new Figma file
- [ ] `DESIGN.md` written

You learn: what tokens and variables are, why there are two layers, how code and Figma stay in step.

## Phase 3: Components

- [ ] Button, chip, input, avatar, chore row, sheet, toast, tab bar, empty state
- [ ] Each with its variants and states (default, hover, pressed, focus, disabled)
- [ ] Style guide page on the site showing every component
- [ ] Matching Figma components with variants

You learn: component anatomy, variants, states, and how to add a new component without breaking the system.

## Phase 4: Rebuild the app on the system

- [ ] Screens rebuilt from components only
- [ ] Two-person rotation for couples (from the brief)
- [ ] Accessibility pass: contrast, keyboard, labels, tap target size
- [ ] Key screens laid out in Figma

You learn: how screens are assembled from a system, and what an accessibility check covers.

## Phase 5: Usability testing

- [x] User flows and phone smoke checklist (`docs/FLOWS.md`); invite-link failure states fixed
- [ ] Automated e2e tests (Playwright, needs owner OK to add dev tooling)
- [ ] Test plan and tasks for four or five friends
- [ ] Decide how testers reach the app. Housemates need live sync: Firebase Firestore plan in `docs/DECISIONS.md` (2026-11-13). Firebase project `tidymate-ce977` is created.
- [ ] Findings captured and prioritised
- [ ] Changes made through the design system

You learn: how to plan and run a small usability test and turn findings into changes.

## Phase 6: Case study

- [ ] Competitor review with sources
- [ ] Write-up: problem, process, decisions, system, testing, outcome
- [ ] Figma file tidied for presentation

You learn: how to tell the story of a project for a product design portfolio.
