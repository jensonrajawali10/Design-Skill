---
name: "design-directions-full"
description: "Use instead of design-directions for any web design: the reference-first five-directions method plus the vibecoded-tells audit, with antislop's honesty, accessibility and mobile gates built in. Before any site, landing page, redesign, dashboard or UI mockup (incl. \"bikin website\", \"desain ulang\"), or when asked if a page looks AI-made."
---

# Design Directions

One rule above all others: **do not one-shot a design.** Producing a single page and
presenting it as "the design" is the failure mode this skill exists to prevent. The user cannot
tell you what they want until they see options side by side, and neither can you.

Method adapted from Chase AI, "Turn Claude Into A Design GENIUS In 3 Simple Steps"
(youtube.com/watch?v=7FU98O0JLHs). When the page will be published as an Artifact, also load
`artifact-design` before writing it; it owns the page contract. For everything else, execution
craft lives in `frontend-design`; read both.

The antislop filter (miqdadbadjuber/anti-slop v3.2.26, MIT) is built into the steps below: the
honesty, function and accessibility hard failures in Step 6, the Design Read dials in Steps 1-3,
and the click-through, keyboard, contrast and tap-target checks in Step 5. Rule numbers (R-XX)
point to `references/antislop-core-rules.md`. Read the deeper references when the step calls for
them, not upfront:

| Reference | Read it when |
|---|---|
| `references/antislop-ui.md` | Building or reviewing any page: every visual and structural tell with its fix |
| `references/antislop-accessibility.md` | Step 5, and whenever colour pairs or controls are in doubt (contrast checker inside) |
| `references/antislop-layout-mobile.md` | Step 5, and whenever a layout must reflow from 360px up |
| `references/antislop-copywriting.md` | Writing or reviewing the page's copy |
| `references/antislop-core-rules.md` | The full R-01 to R-40 text, the dials, and the levers |
| `references/antislop-delivery-gate.md` | The user asks for a production-ready page or a full antislop gate report |

## Step 0 — build the taste library first

Never design from memory. Memory is where generic output comes from. Go look at what is
actually shipping, this week, before choosing anything.

- **recent.design** (formerly godly.website) — current type and poster treatments
- **land-book.com** — real landing pages, filterable by section type
- **Pinterest search URLs** — `https://www.pinterest.com/search/pins/?q=<url-encoded query>`.
  Search per *ingredient*, not per vibe: lighting, type treatment, composition, mark. One broad
  "motivational design" search returns mush; four narrow ones return a system.

If the user has an existing brand, **look at it before designing.** Open the live site and the
social accounts. The gap between what a brand looks like on Instagram and what it looks like on
its own site is very often the most useful thing you will find all session.

Report what you took and from where. Every direction should trace to something you actually saw.

## Step 0b — when the user names a site: read it as a system

"Make it feel like Linear" is not a vibe request. It is a request to reproduce a specific set of
mechanics. Open the site, screenshot it at three scroll depths, and write down the answers to
these before you write any CSS:

| Question | Why it decides everything downstream |
|---|---|
| How are sections separated? | Full-bleed colour blocks vs 1px hairlines vs whitespace alone |
| What is the type scale and tracking? | 110px at -0.035em reads nothing like 58px at -0.03em |
| What weight is the headline? | Medium at huge size ≠ bold at huge size. Most premium sites use medium |
| Border, radius, shadow language? | None at all / 1px at 8% white at 11px / 2px black with hard offset |
| Button shape? | Full pill vs 8px radius vs square. This alone dates a design |
| What is the section rhythm? | One idea per screen vs dense information per screen |
| What is the signature tell? | The thing nobody copies. Find it and use it |
| What does the product visual do? | Screenshot in a frame / device bleeding across a boundary / none |

**Three worked examples, all read from the live sites, kept here so you don't have to re-derive
them.** The first two are near-opposites, which makes them a useful pair to reason between.

**Revolut** — separation by full-bleed colour block, zero borders or hairlines anywhere. One
idea per block, alternating hero-colour / black / white / brand-colour. Headline ~110px,
geometric grotesque (Aeonik; Figtree is the closest on Google Fonts), weight 600 not 800,
tracking about -0.035em, leading under 1. Then a *small bold* sub-paragraph, then exactly one
fully-rounded pill button. Device visual bleeds past the section boundary into the next block.
Segmented pill toggles for choices. Nav: wordmark, four text links, "Log in", filled pill.

**Linear** — the inverse. Near-black `#08090a`, separation by 1px borders at 8% white, radius
~11px. Two faint vertical hairlines running the full page height marking the container edges,
which is their signature tell and almost nobody copies it. Type is *small*: headline only ~58px
at medium weight, body 15px, secondary grey `#8a8f98`. Buttons are 8px radius, not pills. One
large bordered app window as the hero visual doing all the selling. Inter, tight tracking,
`font-feature-settings:'cv02','cv03','cv04','cv11'`.

**SuperAI (superai.com/next-hackathon)** — a third pole, for event and hackathon pages. Pure
black, one lime accent, Manrope at weight 500 for headlines, no hairlines anywhere, dark
rounded panels `#0b131c` at 14px, pill buttons, stepped checkerboards pinned to the outer screen
edges, a full-bleed lime band with one huge number, partner logos on white tiles at a fixed ratio
with a small accent role label under each. Its signature is the margin art; everything inside
the column is restrained.

Note what this implies: Revolut sells by *asserting*, Linear sells by *showing the product*,
SuperAI sells by *occasion*. If the user's product has a number or a screen worth showing,
Linear's system does more work.

## Step 1 — write the four-part brief

Four things, stated plainly, shown to the user:

1. **Aesthetic** — which families you are exploring, and why those
2. **Reference** — what you are matching, on *feel* only. Never layout, never content
3. **Intent** — what the page is, who it is for, the one action it must produce
4. **Guardrails** — what must never appear

Baseline guardrails, always on unless overridden: no purple-on-white gradients, no Inter or
Roboto or system-font defaults, no 3D SaaS blobs, no floating browser-chrome mockups, no stock
photography, no Space Grotesk.

Honesty guardrails, always on and **not** overridable by style (antislop Hard Gate): no invented
numbers, testimonials, customer or partner logos, team members, or security, compliance or
performance claims (R-17, R-18, R-36, R-38); ask before inventing a logo, avatars, statistics or
the nav structure, otherwise use a visible placeholder like `[LOGO]` or `[REAL DATA]` (R-23); no
em dashes in page copy (R-02); no generic CTAs such as Get started, Learn more, Try now, Explore,
Discover (R-15). If the user's own direction asks for one of these, name it and the rule it
breaks, and ask whether to keep it.

The Inter ban has one legitimate exception: when the user names a reference site that *uses*
Inter, matching it is correct. State the exception out loud so it doesn't read as an oversight.

## Step 2 — five families, side by side

Generate **five**, not one, not three, then build a comparison harness so all five can be seen
at once. Each must differ from the others on at least **four** of these axes:

| Axis | Not enough | Enough |
|---|---|---|
| Type | two different sans | serif vs mono vs slab vs expanded grotesque |
| Colour | two dark themes | dark warm vs paper vs two-ink flat vs full colour block |
| Density | slightly tighter | dense grid vs enormous airspace |
| Voice | reworded | authoritative vs technical vs devotional vs loud |
| Imagery | different gradient | generated data vs dither vs vector mesh vs none at all |
| Format | different padding | broadsheet vs terminal vs poster vs document |

If two of your five could plausibly be variations of each other, you have four families and a
duplicate. Replace it.

Give every family its own **Design Read**, one line, before building it (antislop Part 3):

> Reading this as: `<page kind>` for `<audience>`, in a `<visual language>` style, dial ENERGY `n` / RHYTHM `n` / MOTION `n`.

Each dial is 1 (calm), 2 (balanced) or 3 (bold). ENERGY is how hard the page says hello, RHYTHM is
how much sections change from one another, MOTION is how much moves and why. Spread the five
across the dials: five families all at ENERGY 2 / RHYTHM 2 / MOTION 2 have converged even if
their fonts differ. The build must honour its own dials: a RHYTHM 3 family with uniform sections,
or a MOTION 1 family that fades everything in, fails (R-05, R-19). If there is no direction at
all and you cannot ask, say so, and mark the set as drafts without direction.

### The anti-convergence rule

**Do not reach for the user's existing visual language unless they asked you to.** If they have
a house style, a reel template, a deck theme, or a brand you built with them earlier in the
session, that is exactly the thing that will feel safe and exactly the thing that makes the
exercise worthless. Naming your system something new does not make it new. If you are using
their existing display font and their existing layout device, you have restyled, not designed.
Ban the house ingredients explicitly in the guardrails line so the constraint is visible.

Same rule applies to yourself across a session: if today's variant 3 looks like this morning's
variant 3, you are converging on your own defaults.

### The comparison harness

Five isolated designs cannot share a stylesheet. Use `iframe srcdoc` — each variant is a
complete document, so their CSS cannot collide.

```js
card.querySelector('iframe').srcdoc = variantHtml;   // full <!DOCTYPE html> string
function fit(){                                       // scale 1440px into a card preview
  document.querySelectorAll('.wrap').forEach(w=>{
    w.querySelector('iframe').style.transform = 'scale(' + (w.clientWidth/1440) + ')';
  });
}
```

Wrap in `position:relative; overflow:hidden; aspect-ratio:16/11`, `transform-origin:top left`
on the iframe. Add click-to-open-full-width and arrow-key paging. Inside a template literal
write `<\/script>` for any closing script tag or the outer script dies.

Label every card with name, one-line genre, its dials, an honest two-sentence note on what it is
good and bad at, and the reference it came from. Say which is the safe commercial answer and
which is the memorable one.

## Step 3 — narrow, do not restart

Once they pick, generate **three variations of that one family**, varying body layout and
density, not aesthetic. They pick again. Only then hero imagery, only then colour. The chosen
family's dials are now locked; every variation and every later step holds them unless the user
asks to change them.

Order: family → layout → hero → colour → detail. Working colour before layout wastes
everything downstream.

## Step 4 — ship a tweaks bar

Every finished page gets a floating panel driving CSS variables live. The user finds their
preference by moving sliders instead of asking for ten rebuilds.

```css
:root{ --acc:#d4562a; --hfont:'Anton',sans-serif; --warm:22; --grain:.2; --rad:0px; --motion:1 }
```
```js
const R=document.documentElement.style;
const bind=(id,fn)=>document.getElementById(id).addEventListener('input',e=>fn(e.target.value));
bind('fWarm', v=>R.setProperty('--warm', v));
```

Expose accent (swatches), display font (3-4 real options), tracking, backdrop warmth, grain,
radius, motion kill switch, plus a reset calling `removeProperty` on every variable. Ask which
settings they landed on and bake those in as the new defaults. Mark it as a dev control to
delete before shipping. Skip it when the host forbids JavaScript. Give every slider and swatch a
visible label, and let `prefers-reduced-motion` win over the motion slider (R-39).

## Step 5 — verify, then actually look

Never claim a page renders without having rendered it. Chromium is available:

```python
from playwright.sync_api import sync_playwright
with sync_playwright() as p:
    b=p.chromium.launch(); pg=b.new_page(viewport={"width":1440,"height":900})
    errs=[]; pg.on("pageerror", lambda e: errs.append(str(e)))
    pg.goto("file:///abs/path/index.html"); pg.wait_for_timeout(4000)
    pg.screenshot(path="check.png")
    print(pg.evaluate("document.documentElement.scrollWidth>window.innerWidth+2"))  # overflow
    print(errs or "none")
```

Check every route. Check horizontal overflow at 360, 768, 1280, 1440, 1536 and 1900 (Windows
laptops at 125% scaling are 1536 CSS px and are the common case). Assert element counts (cards
rendered, filters returning the right subset). Measure the elements you changed with
`getBoundingClientRect()` and print the numbers; eyeballing a screenshot misses 8px offsets.
Then **read the screenshot** — a page with no console errors can still be visually broken, and
every bug in the catalogue below passed the error check.

Then check that the page works for people, not just that it renders (antislop R-03, R-25 to R-27,
R-32, R-35, R-39, R-40). Details and fixes are in `references/antislop-accessibility.md` and
`references/antislop-layout-mobile.md`.

- **Click-through.** Exercise every link, button, form, tab, accordion, modal and toggle, one at
  a time, and record what each did ("Register -> scrolls to #register", "empty form -> shows
  validation", "menu -> opens, Escape closes"). Anything that does nothing is removed or labelled
  "Coming soon"; `href="#"` is not a destination. A claimed pass without the list is not a pass.
- **Keyboard.** Tab through the whole page: order follows the visual order, every stop has a
  visible focus ring, Enter and Space activate, Escape closes dialogs. `outline:none` with no
  replacement fails.
- **Mobile hands.** At 360px, buttons and nav controls are at least 44px tall and not crowded;
  nothing depends on hover; the viewport does not block zoom.
- **Contrast.** Every text and background pair you have not verified goes through
  `python3 <skill folder>/scripts/contrast-check.py "#fg" "#bg"`: 4.5:1 for body text, 3:1 for
  18px and up. For text over a photo or gradient, test the lightest point it crosses.
- **States.** Anything that shows data (dashboards above all) has an empty, a loading and an
  error state.
- **Semantics.** Actions are `<button>`, navigation is `<a href>`; icon-only controls have an
  `aria-label`; images have `alt`; fields have visible labels; one `h1`, `lang` on `<html>`.
- **Performance mechanics.** Images carry `width` and `height`, the hero image is not lazy and
  has `fetchpriority="high"`, no third-party script blocks the `<head>`. Never report a Lighthouse
  or Web Vitals number you did not measure.

```python
pg.set_viewport_size({"width":360,"height":800})
print(pg.evaluate("""[...document.querySelectorAll('button,nav a,[role=button],input,select')]
  .map(e=>[e.textContent.trim().slice(0,24)||e.outerHTML.slice(0,40),e.getBoundingClientRect()])
  .filter(([_,r])=>r.width&&r.height<44).map(([n,r])=>[n,Math.round(r.height)])"""))  # small targets
for _ in range(20):                                                              # tab order + focus
    pg.keyboard.press("Tab")
    print(pg.evaluate("""(()=>{const e=document.activeElement,s=getComputedStyle(e);
      return [e.tagName,(e.textContent||'').trim().slice(0,24),s.outlineStyle,s.boxShadow!=='none']})()"""))
```

Google Fonts fail to load in a sandboxed container and fall back. Expected — but say so, rather
than letting the user think the fallback is the design.

## Step 6 — the vibecoded-tells audit

Run this on every page before presenting it, and run it as a review whenever someone asks "does
this look AI-made?" A designed page can trip one or two of these; a vibecoded page trips ten at
once, and people who have seen a lot of generated sites recognise the cluster in under a second.
Report by tell, with the exact element, and fix by **replacing with something specific**, never
by deleting and leaving a hole.

### Structure tells

- The default order, regardless of what the thing is: hero → logo strip → three features →
  how it works → testimonials → pricing → FAQ → CTA → footer. A hackathon page does not need
  pricing. A restaurant does not need "how it works".
- Every section gets the same weight and the same padding (`py-24` everywhere). Real pages
  spend three screens on the thing that matters and one line on the rest.
- Everything centred, nothing bleeds, nothing overlaps, no margins used. Symmetry all the way
  down is the single strongest tell.
- Nav: logo left, five anchor links, ghost "Sign in" plus filled "Get started", sticky with
  backdrop blur. Footer: four columns of links that go nowhere, newsletter box, social icon
  row, "© 2024 Company. All rights reserved."
- Sections named `#hero #features #pricing #faq #contact` with `<!-- Hero Section -->`
  comments. Buttons that are `<a href="#">`.
- "How it works" as exactly three numbered steps with round icons, whatever the real process is.
  Pricing as three columns with the middle one badged "Most popular", whatever the real pricing
  is. A bento-grid mosaic as the default section. A fake terminal window as the hero visual.
- The only variation between sections is flipping the background colour every other block.

### Visual tells

- Purple/indigo-to-pink gradient, gradient text on the headline, glow blobs behind the hero,
  glassmorphism cards with blur, noise overlay on everything.
- Tailwind default palette read straight off the swatch: `slate-900`, `indigo-500 #6366f1`,
  `violet-600`, `emerald-500`; `rounded-2xl shadow-xl` on every card.
- Inter, Roboto, Poppins, Space Grotesk; one font at three weights; headline at 800 weight.
  Premium sites run medium weight at large size.
- Icon-in-rounded-square + title + two-line blurb, three across, all identical. Emoji as
  section icons. Lucide/Heroicons on everything.
- Fake proof: "10k+ users / 99.9% uptime / 24/7 support" stats, testimonials with invented
  names and initial-circle avatars, a "Trusted by" strip of made-up logos, 5-star rows.
- Unsplash laptops and handshakes, 3D blobs, floating browser mockups showing fake UI,
  "AI" imagery of brains and circuits, wave SVG dividers, gradient hairlines.
- Motion: every block fades up on scroll with the same delay, every card scales 1.05 on
  hover, typewriter hero, particles, a cursor-following gradient blob, bobbing floaters.
- A dark-mode toggle nobody asked for. The default favicon. A dark theme chosen only because it
  looks "tech"; if a toggle does ship, both modes must be fully checked (R-34).
- A pill parked above the H1 repeating the headline's category; capsule badges ("AI Powered",
  "Beta", "New") with dot, glow and uppercase all at once; a thin coloured stripe on the left edge
  of cards; an arrow (→ ↗) on every button; uppercase labels with wide tracking ("HOW IT WORKS");
  monospace headings for a "terminal" feel.
- Grid, dot or blueprint backgrounds; glow on cards, buttons, icons and borders at once; every
  element pill-shaped; five or more colours with no system behind them.
- Grey skeleton bars standing in for the product screenshot.
- The sterile default, which is the opposite failure: flat white, thin grey borders, small
  radius, a generic font, no accent, nothing that belongs to this product. Removing tells and
  stopping there produces this; the fix is direction and one committed device, not more bans.

### Copy tells

- "Elevate", "Seamless", "Empower", "Unlock", "Supercharge", "Transform your workflow",
  "Built for modern teams", "Lightning fast", "Ready to get started?", "Powered by AI".
- Headlines that are benefit triplets ("Fast. Secure. Reliable."), three bullets under every
  card, a checkmark list inside every pricing tier.
- Vague attribution and invented specifics: numbers with no source, quotes with no person,
  "industry-leading", "world-class". Placeholders left in (`[Company]`, `lorem`, `2025-xx-xx`).
- FAQ answers to questions nobody asked, written to fill the accordion.
- Em dashes in the copy. Generic CTAs: Get started, Learn more, Try now, Explore, Discover.
- AI rhythm: "Not just X. It's Y.", stacked one-line fragments for drama, "Let that sink in",
  "In today's fast-paced world" openers, Title Case On Every Bullet, emoji in headings. More
  patterns with before-and-after fixes are in `references/antislop-copywriting.md`.

### What reads as designed instead

- One signature device the page commits to (a margin wordmark, edge checkerboards, a hairline
  pair, a colour-block rhythm) and restraint everywhere else.
- One focal point per screen: exactly one element is clearly the most important and the rest
  defer to it.
- The number of items is decided by the content: five eligible groups because there are five,
  three tracks because there are three. Never three because three looks complete.
- Real material: the organiser's own photos, the actual partner logos with their real roles,
  copy quoted from the official source, numbers with a source or no numbers.
- One accent colour, medium-weight type, uneven section lengths, at least one element that
  breaks the column (bleeds, overlaps, sits in the margin).
- Specific, checkable details in every section, and nothing that exists only to fill a slot.

### Hard failures (antislop Hard Gate)

These are not tells to count. Any one of them blocks presenting until it is fixed, however few
other tells the page has, because each one makes the page dishonest or unusable:

- Invented proof: numbers without a source, testimonials, customer or partner logos, team
  members, ratings, or security, compliance or performance claims nobody supplied (R-17, R-18,
  R-36, R-38). Replace with the real thing, a visible `[REAL DATA]` placeholder, or nothing.
- Invented assets presented as final: a logo, avatars, people photos (R-23).
- Dead controls: buttons or links that do nothing, `href="#"`, nav items pointing to sections
  that do not exist (R-24, R-26).
- Text below WCAG AA contrast (R-25).
- Not usable by keyboard, or focus made invisible (R-32).
- Horizontal overflow, clipped text or under-44px controls on mobile (R-03).
- A data view with no empty, loading or error state (R-27).
- Controls with no accessible name, clickable `div`s, images with no `alt`, fields with no
  label, motion that ignores reduced-motion, zoom blocked (R-39).
- A shipped theme where one mode breaks (R-34); a feature patched in by a script that rewrites
  the CSS (R-33); a performance number that was never measured (R-40).

### Scoring

Count the tells. Zero to two: fine, name them anyway. Three to five: fix before presenting.
Six or more: the family is wrong, not the details; go back to Step 2. Hard failures sit outside
the count: fix every one regardless. When reviewing someone else's page, list every hard failure
first, then give the count, the five worst tells with element references, and the one change
that removes the most tells at once (usually: cut the fake proof row and the three-card grid).
Number the findings and mark hard failures HIGH, so the user can say which numbers to fix; change
nothing on their page until they do.

## Bug catalogue — all of these render clean and look wrong

- **CSS animation silently overrides an SVG `transform` attribute** on the same element. Two
  mirrored shapes stack on top of each other. Fix: mirror on an outer `<g>`, animate an inner one.
- **Keyframes override a static `transform` on the same element.** Centre with
  `margin-left:-.5em`, not `translateX(-50%)`, when the element is also animated.
- **A CSS grid child won't shrink below its content width.** A fixed-width inner grid forces its
  track wide and pushes the next column out of frame. Fix: `min-width:0` on the grid children.
- **`Math.sin(i*12.9898)*43758.5453` bands at integer steps.** The classic GLSL hash is not
  random over `i = 0,1,2,…`. An LCG with a poor multiplier correlates in the low bits too. Use
  xorshift32.
- **Every cell tinted with the same hue at different alphas reads as one solid block**, not as
  data. Base level must be near-neutral, roughly 12% not 20%.
- **A "faint background glow" at large radius becomes an object.** A galaxy core drawn as a
  bright radial gradient reads as a moon. Build luminous things out of many small elements, not
  one big soft one.
- **`overflow:hidden` on a section clips any device meant to bleed into the next section.**
  Revolut-style overhang needs `overflow:visible` plus `z-index` plus padding on the next block.
- **`writing-mode: vertical-rl` centres glyphs differently on Windows Chrome than on Linux.**
  The user sees letters pushed outward and clipped; your render is perfect. Use horizontal text
  rotated with `transform`, one element per repeat, so horizontal metrics decide placement.
- **A single rotated element longer than ~16,000px does not paint** in Chrome. Chunk it.
- **`50vw` includes the scrollbar, `50%` does not.** Windows has a 17px scrollbar. Mixing the
  two in one layout drifts by 8px; use `%` for positions, `vw` only for font-size with slack.
- **`%` inside `font-size` is the parent font size, not the width.**
- **Margin art positioned off the screen edge with its own formula drifts against content
  positioned off the column.** Anchor every margin element to one shared reference (the column
  edge or the motif's centre) so they land together at every width.
- **A media query written above the base rule loses.** Append overrides at the end of the
  stylesheet.
- **Gradient checkerboards seam and look crooked.** Use DOM cells with `nth-child` colouring and
  a two-row `translateY` loop.
- **A scroll-driven animation with no time-based fallback freezes** when the host strips it or
  the browser lacks `animation-timeline`. Always give it a real duration outside `@supports`.

## Scaling the method

- **"Quick mockup"** — three families, skip the tweaks bar, still never one.
- **"Redesign my site"** — not a restyle. Audit the information architecture first. If the nav
  promises six destinations and they are all anchors into one scroll, the structure is the
  problem and no amount of new typography fixes it.
- **"Make it like that site"** — run Step 0b, then build one faithful interpretation rather than
  five. The user has already chosen the family; your job is accuracy to their reference.
- **"Does this look AI-made?"** — run Step 6 only, on their page or screenshot, and report.
- **"Just build X"** with the spec fixed — skip the directions and build it: load
  `artifact-design` first if it will be published as an Artifact, otherwise go straight to
  `frontend-design`. Still declare a Design Read, and still run Steps 5 and 6 before presenting.

## What to say when presenting

Lead with what you took and from where. Name the safe option and the memorable option, and be
willing to say which you would pick. Flag every piece of copy you invented and every image slot
that is a placeholder. Report the bugs you hit and fixed and the tells you removed — it tells
the user which parts were actually verified. Close by asking them to pick one, not by asking
whether they like it.

For a finished page (not the five-family comparison), add a short check report after it: each
hard failure from Step 6 with its evidence from Step 5 (the click-through list, the widths
checked for overflow, the contrast ratios, the keyboard pass), the tell count, the Design Read
and dials, and every placeholder still waiting for real data. Keep it to what the user can act
on or trust; this is not a wall of checkboxes.