# dredd-generator

A standalone character generator for **Judge Dredd & The Worlds of 2000 AD**
(the WOIN / N.E.W. tabletop system by EN Publishing, under license from
Rebellion / 2000 AD). Built as a community fan tool.

Single self-contained static page: `index.html` (no build step, no
dependencies, no CDN - all CSS, JS and game data are inline).

## The engine (WOIN N.E.W.)

Unlike the POTA generator (D6 Magnetic) and the Space: 1999 generator (2d20),
this game runs on EN Publishing's **N.E.W.** ruleset:

- **d6 dice pools** - attribute dice + skill dice, rolled and summed (exploding
  6s) against a target number.
- **Life-path creation** - a character is grade 0 (species), then takes an
  ordered sequence of **career "grades"**. Each career adds +1 to its listed
  attributes, 2 skill picks, and 1 exploit. A typical starting character is
  grade 5. Judges follow Cadet -> two Academy of Law programs -> Rookie -> a
  Judge career (Med / Psi / Street / Tek), then optional Speciality careers.

All species (7), the D66 mutation table (36), origins, 22 civilian + 19 perp
careers, the full Judge tree, 69 universal exploits, 37 traits, the WOIN skill
list, derived-stat formulas, age and advancement rules are transcribed verbatim
from the Core Rulebook character-creation chapter.

## Hosting

Deployed as its own Vercel project. It is surfaced at
`https://thetapestry.distemperverse.com/dredd-generator` via a proxy rewrite in
the TheTapestry app (that app rewrites `/dredd-generator` to this deployment),
so the public URL is unchanged while the code lives here, out of the commercial
TheTapestry repo (per that repo's AGENTS.md rule against mixing in unrelated
projects).

Because the rewrite is a proxy, the page runs on the
`thetapestry.distemperverse.com` origin, so the built-in visit beacon (bottom of
`index.html`) posts a `page='/dredd-generator'` visit to the shared `log-visit`
edge function - the `/dredd-generator-log` dashboard in TheTapestry reads those.

## Features

- Light (parchment / official-sheet) and Dark (Mega-City night) themes, saved to
  `localStorage` and applied before paint to avoid a flash.
- Print output (`@media print`) replicates the official 2-page character sheet.
- Randomise / Auto-Judge for quick builds; prerequisite gating on careers.
- Fully self-contained: inline everything, ASCII-only source, min 12px fonts.

## Notes

- Visit logging respects the owner opt-out (`localStorage tapestry_no_log = '1'`).
- Copyright: Judge Dredd (R) and (C) 2018 Rebellion 2000 AD Ltd. The WOIN /
  N.E.W. system is (C) EN Publishing, published under license from Rebellion.
  Unofficial fan tool, not affiliated with or endorsed by the rights holders.
  (EN Publishing's 2000 AD license lapsed in Nov 2021; the line is out of print.)
