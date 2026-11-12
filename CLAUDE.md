# Tidy mate: project guide for Claude

Read this first each session. It exists so a new session can start working without re-reading the whole codebase or asking the owner to repeat context.

## What this is

A shared chore tracker for housemates. Static web app (plain HTML, CSS, JavaScript, no build step), published with GitHub Pages from the `main` branch.

- Live: https://angelojoywork-sys.github.io/TidyMate/
- Repo: https://github.com/angelojoywork-sys/TidyMate

## The owner

A visual designer moving into product and UX design, using this project to learn design systems, Figma variables and the design-to-code workflow. It is also a portfolio case study.

- Explain design and system decisions in plain language as you make them. Define a term the first time it appears.
- Record every meaningful decision in `docs/DECISIONS.md` (what, why, what was rejected). The owner will talk through these in interviews.
- Keep answers short. The owner wants to keep usage low.

## Where things live

| File | Purpose |
|---|---|
| `PRODUCT.md` | Who it is for, the problem, principles, voice. Check design choices against it. |
| `DESIGN.md` | The design system: tokens, components, rules. Created in phase 2. |
| `docs/ROADMAP.md` | Phases and current status. Start here to see what is next. |
| `docs/DECISIONS.md` | Decision log. |
| `docs/RESEARCH.md` | Research notes with sources and limits. |
| `docs/GLOSSARY.md` | Plain-language definitions of terms used in this project. |
| `index.html` | The current prototype (single file, pre design system). |

## How we work

1. One roadmap phase per session where possible. Read `docs/ROADMAP.md`, do the next unchecked item, update the roadmap at the end.
2. Design tokens in code are the source of truth. Figma variables mirror them with the same names. Never hard-code a colour, size or radius in a component once tokens exist.
3. Build a component once, document its variants and states, then reuse it. If a screen needs something new, add it to the system first.
4. Check the result at phone width (375px) before calling it done.
5. Commit after each finished piece of work with a message that says what changed and why. Push only work the owner has asked to ship.

## Practical notes

- The app's own preview server cannot read the Documents folder. Serve locally with `python3 -m http.server 4174` run from the project folder, then open `http://localhost:4174/`.
- The mascot in `assets/mascot.png` is a low-resolution stand-in. Final artwork is deferred; do not spend time on it.
- Live sync and deployment for real usability testing are deferred until the owner raises them.
