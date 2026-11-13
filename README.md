# design-directions-full

A Claude skill for web design: a site, landing page, redesign, dashboard, or UI mockup. It uses a reference-first method that produces five directions, then audits the page for signs it looks AI-made. Honesty, accessibility, and mobile checks from antislop are built into that pass. It also applies when someone asks whether a page looks generated.

## Layout

- `design-directions-full.skill` is the original package, ready to upload into Claude. The folder beside it is that same package, unpacked.
- `design-directions-full/SKILL.md` is the skill instructions.
- `design-directions-full/references/` holds the bundled notes, plus `LICENSE-antislop` and `LICENSE-web-quality-skills`.
- `design-directions-full/scripts/contrast-check.py` checks WCAG contrast for a pair of colors.

## Install

Claude.ai: open Settings, then Capabilities/Skills, and upload `design-directions-full.skill`.

Claude Code: copy the `design-directions-full` folder into `~/.claude/skills/`.

## Credits

The notes in `design-directions-full/references/` keep the licenses they shipped with.

Antislop notes on accessibility, copy, core rules, the delivery gate, mobile layout, and UI are covered by the MIT license in `design-directions-full/references/LICENSE-antislop`. Copyright (c) 2026 Miqdad Badjuber (antislop). The accessibility, copywriting, core rules, layout, and UI notes are adapted from [miqdadbadjuber/anti-slop](https://github.com/miqdadbadjuber/anti-slop) v3.2.26.

Web Baseline, Core Web Vitals, the WCAG 2.2 quick reference, and the accessibility code patterns are adapted from Addy Osmani's [web-quality-skills](https://github.com/addyosmani/web-quality-skills). Copyright (c) 2026 Addy Osmani, MIT. See `design-directions-full/references/LICENSE-web-quality-skills`.
