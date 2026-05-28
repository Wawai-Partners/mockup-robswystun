# Design Notes — Rob Swystun Website Preview · v3
**Client:** Rob Swystun Content Marketing & Ghostwriting Inc.
**Date:** 2026-05-26
**Files:** `index.html` · `about.html` · `ghostwriting.html` · `styles.css` · `design-system.html` (system reference) · `archive/v1-*` + `archive/v2-*` (preserved)

This is the **third pass**, rebuilt on the Rob Swystun design system (v0.3 · May 2026)
the user provided. The new system is a quieter, more conventional editorial register:
white page, single deep-blue accent, Source Serif + Inter, no uppercase anywhere,
ochre-soft highlight behind one italic word per view.

---

## 1. What changed from v2

| Dimension | v2 (book-as-website) | v3 (design system) |
|---|---|---|
| Page | Foxed paper `#efe7d6` | Pure white `#FFFFFF` (warm off-white `#FBF7EC` for alt sections) |
| Accent | Oxblood `#6b2a1f` + forest `#1e4d3a` | Single deep-blue `#1F3A68` |
| Highlight | None | Warm-soft `#FBF1D2` marker tint behind one italic word per view |
| Display type | EB Garamond | Source Serif 4 |
| Body type | EB Garamond (serif body) | **Inter** (sans body) — the system's intentional change |
| Meta type | IBM Plex Mono | JetBrains Mono |
| Section labels | `PLATE Ⅴ — ON THE MATTER OF AI` (uppercase Roman) | `04 / On the matter of artificial intelligence` (sentence case, mono) |
| Cards | Forbidden | Permitted, with light borders on warm off-white |
| Quote treatment | Flush-right epigraph with mono attrib | Left-border pull quote (2px accent rule) |
| Stats | Spelled-out italic numerals | Arabic numerals with `+` in accent blue |
| Section break | Hairline rule | Hairline with two ochre dots flanking a sentence-case label |

**Preserved from v2:**
- Editorial / quiet register
- Asymmetric two-column grid with marginalia gutter
- Reversed ink section for the AI policy (kept; recoloured to white-on-ink with ochre highlight)
- Reservation slip on Ghostwriting
- Signed signature on About
- Five-paragraph essay with `¶ N of 5` marginalia counters
- Hairlines instead of shadows; no rounded corners on cards

**Removed from v2:**
- Roman-numeral "Plate" labels (the system says no all caps)
- Oxblood rubrication colour
- Foxed paper background
- EB Garamond body type

---

## 2. The recurring brand signal

**One italic word per view, set with the warm-soft `#FBF1D2` highlight tint.**
Per design-system rule: "Used in the masthead behind the name. Avoid in body paragraphs."

| Page | Highlighted word | Where |
|---|---|---|
| Home masthead | `hand` | "Writing books, and writing for businesses — by *hand*" |
| Home / 04 — On AI | `human` | "Every word ... composed by a *human*" |
| About masthead | `habit` | "A writer, by training and by *habit*" |
| About / 05 — Closing | `you` | "Let us write something that sounds like *you*" |
| Ghostwriting masthead | `your voice` | "I will write it in *your voice*" |
| Ghostwriting / 05 — Booking | `minutes` | "One call. Sixty *minutes*." |

Always exactly one per page view (allowing for two highlighted words on long pages with a hero plus a closing CTA — masthead + dark CTA section count as separate views).

---

## 3. Page inventory

### Home (`index.html`)

| # | Anchor | Section | Components |
|---|---|---|---|
| — | — | Masthead — H1 with `<em class="mark">hand</em>`, dek, two CTAs, frontispiece marginalia | `.masthead`, `.book` grid, `.marginalia` |
| — | — | Stats row — 4-up (20+, 13+, 90+, 120+) with `+` in accent blue | `.stats`, `.stat` |
| 01 | `#about` | A note from the person on the other side of the email — running prose, drop cap | `.dropcap`, `.eyebrow` |
| break | — | Two-dot section break "Two practices" | `.section-break` |
| 02 | `#services` | Two practices, one writer — two editorial cards with tags, prices, link CTAs | `.editorial-card`, `.tag` |
| 03 | `#endorsements` | Three readers, three industries — three pull quotes | `.pull-quote` |
| 04 | `#ai` | On the matter of artificial intelligence — reversed dark section | `.section--dark` + `.mark` on `human` |
| 05 | `#correspondence` | Write to me — giant `mailto:` link + catalog list of paths | `.btn--link` at display size + `.cat-list` |

### About (`about.html`)

| # | Anchor | Section |
|---|---|---|
| — | — | Masthead — `<em class="mark">habit</em>` |
| 01 | — | The long version, in five paragraphs — drop cap + per-paragraph marginalia + signature |
| break | — | "A short timeline" |
| 02 | — | Twenty years, in four notes — `.timeline` (year + title + body) |
| 03 | `#memberships` | In good company — `.register` (5 rows) |
| 04 | `#more-endorsements` | Three more endorsements — pull quotes |
| 05 | — | Closing matter (dark) — `<em class="mark">you</em>` |

### Ghostwriting (`ghostwriting.html`)

| # | Anchor | Section |
|---|---|---|
| — | — | Masthead — `<em class="mark">your voice</em>` + reservation slip in right column |
| break | — | "Suited for" |
| 01 | — | Four kinds of book project — 2×2 editorial cards |
| 02 | `#process` | The process — 3 `.phase` rows with deliverables |
| 03 | — | Statement of scope — 2-col `.scope` (in / out) |
| 04 | — | Common questions, plainly answered — 5 `.entry` accordions |
| 05 | `#booking` | Reservation (dark) — `<em class="mark">minutes</em>` + reservation slip |

---

## 4. Token map — design system → `tokens.css`

Add or override in `src/styles/tokens.css`:

```css
:root {
  /* Surfaces — replaces v1's --color-paper */
  --color-paper:        #FFFFFF;
  --color-cream:        #FBF7EC;

  /* Ink scale */
  --color-ink:          #111111;     /* slight change from v1's #182126 */
  --color-charcoal:     #3D3D3D;     /* was #454648 */
  --color-fog:          #6B6B6B;     /* was #86827d */

  /* Rules */
  --color-rule:         #E4E4E1;
  --color-rule-strong:  #C8C8C4;

  /* Single accent — REPLACES forest */
  --color-accent:       #1F3A68;
  --color-accent-deep:  #142545;
  --color-accent-soft:  #E8EEF7;

  /* Warm secondary — used sparingly */
  --color-warm:         #D4A93B;
  --color-warm-deep:    #A8841C;
  --color-warm-soft:    #FBF1D2;

  /* Type — replaces all v1/v2 font tokens */
  --font-display: 'Source Serif 4', Georgia, 'Times New Roman', serif;
  --font-sans:    'Inter', -apple-system, BlinkMacSystemFont, 'Helvetica Neue', Arial, sans-serif;
  --font-mono:    'JetBrains Mono', ui-monospace, SFMono-Regular, Menlo, monospace;
}
```

The brief's lead palette (forest, paper, ink, fog, moss) is **partially overridden** by
the new design system:
- `forest` → replaced by `--color-accent` (deep editorial blue)
- `paper` → now pure white, not warm cream
- `ink`, `fog` → minor hex shifts but role intact
- `moss` → not used; the accent blue replaces it for kickers/eyebrows
- Sage / blue / pink section backgrounds from brief §5 → not used; the system uses one warm off-white (`#FBF7EC`) for alt sections only

**The brief is overridden by the design system on colour.** Confirm with the PM before
Claude Code locks tokens.

---

## 5. Components → component-patterns.md mapping

| New component | Closest existing pattern | Notes |
|---|---|---|
| `.masthead` | Pattern 2 (Hero) — *modified* | Meta strip + H1 with `.mark` highlight + dek + CTAs |
| `.stats` row | Pattern 8 (Marquee) — *replaced* | Use serif numerals with `+` in accent |
| `.editorial-card` | Pattern 5 (Card grid) | Light border, mono section number, serif title, sans body, optional tags |
| `.pull-quote` | New | Left 2px accent border, italic serif body, sans cite block |
| `.section-break` | New | Hairline with two ochre dots — use between major sections |
| `.section--dark` | New | Black background section with white + ochre-soft tint highlight |
| `.slip` (reservation) | New | Light-bordered card with field rows |
| `.timeline` | New | Year + title + body, hairline-separated rows |
| `.register` | New | Numbered list of memberships / catalog entries |
| `.phase` | New | Phase label column + content with deliverables list |
| `.scope` (in/out) | New | Two columns, hairline-separated lists with "Included"/"Not" prefix labels |
| `.entry` (FAQ) | New | `<details>` with mono number, serif italic toggle ("Read"/"Close") |
| `.cat-list` | Pattern 5 — *as list* | Catalog row: num + title + desc + see-link |

---

## 6. Anti-pattern audit — v3

All seven anti-patterns called out in v2 stay fixed. New checks against the design system:

| System rule | Compliance |
|---|---|
| No uppercase anywhere | ✓ All headings, nav, captions, eyebrows are sentence case. The only mono-uppercase remnant was in section labels; replaced with `01` / `02` mono numbers |
| One blue accent, used sparingly | ✓ Wordmark period, eyebrows, `+` in stats, pull-quote rule, link hover, dropcap, FAQ toggle. Not in body text. |
| Warm-soft highlight = **once per view** | ✓ 6 instances across 3 pages (Home masthead, Home AI, About masthead, About closing, Ghostwriting masthead, Ghostwriting booking) |
| No icon sets / glass panels / gradients | ✓ Zero icons, zero gradients, zero glow |
| Inter for body, Source Serif for display | ✓ |
| 8pt spacing grid | ✓ |
| Hairlines on rule colour, not pure black | ✓ All borders use `--rule` `#E4E4E1` |
| 12-col grid, asymmetric 5/7 or 4/8 | ✓ `.book` is 12-col; content uses 7/5 split |
| Focus states use 2px ink ring | TODO — currently default browser focus. Production needs explicit `:focus-visible` rules |

---

## 7. Open questions for the PM

1. **Direction confirmation.** v3 is the design-system implementation. v2 (literary, oxblood, foxed paper) is preserved in `archive/v2-*` if the system's quieter direction needs to be pushed back to v2's louder one.
2. **Highlight count.** Some pages have *two* highlighted phrases — once in the masthead, once in the closing dark CTA. The design system says "once per view." Is a long page reasonably two views, or should the second instance be plain italic?
3. **Calendar tool.** Confirm `/book-online` is Acuity / Calendly / Amelia.
4. **Focus rings.** v3 uses browser defaults. Production needs the system's specified 2px ink ring on `:focus-visible`.
5. **Stat numerals.** v3 uses Arabic with accent-blue `+`. The design system's stats card matches this. Confirm Rob wants "20+", not "Twenty" (v2's choice).

---

## 8. Files in this delivery

```
/index.html              · Home — masthead + 5 sections
/about.html              · About — masthead + 5 sections
/ghostwriting.html       · Ghostwriting — masthead + 5 sections
/styles.css              · v3 design-system implementation
/design-system.html      · Reference — the source design system v0.3
/design-notes.md         · this file
/archive/v1-*            · First pass (pastel sage / blue / pink)
/archive/v2-*            · Second pass (foxed paper / oxblood / Garamond)
```
