# DESIGN — HIGGSFREE (Cinema Studio)

> Style contract for the single-file HTML studio. Read before any visual edit.
> Version reviewed: v11 CINEMA STUDIO on branch `feat/v10-bluffant` (commit `b5553c4`).
> Branch HEAD also carries v10 "BLUFFANT" effects, disabled in v11 via
> `.marquee,#boot,#cur,#curR{display:none!important}`.

## Identity
- **The one feeling:** a private Higgsfield-grade cinema studio — obsidian, electric
  lime, brutalist-luxe. Cold, precise, expensive. Never playful, never rounded-soft.
- **Signature / peak:** the obsidian+lime hero with the original SVG eclipse poster
  ("UNE IDÉE. UN FILM. EN GRAND.") and the 7-step fabrication pipeline.
- **Register:** build (dense, utilitarian, monospace labels).

## Tokens (verbatim from shipped CSS)

```css
:root {
  --bg:#060608; --bg-soft:#0A0A0C; --panel:#111113; --panel-2:#17171A; --panel-3:#1E1E21;
  --line:rgba(255,255,255,0.07); --line-strong:rgba(255,255,255,0.13);
  --ink:#F2F0EB; --ink-2:#E8E6E1; --dim:#9A9AA0; --muted:#6B6B70; --faint:#3A3A3E;
  --accent:#E8FF42; --accent-2:#C8E600; --accent-ink:#060608;
  --accent-glow:0 0 0 1px rgba(232,255,66,0.18), 0 12px 40px rgba(232,255,66,0.14);
  --violet:#8B5CF6; --orange:#FF4D12; --ok:#22C55E; --er:#FF3B30;
  --mono:'JetBrains Mono', ui-monospace, monospace;
  --sans:'Inter', system-ui, -apple-system, sans-serif;
  --display:'Space Grotesk', Inter, system-ui, sans-serif;
  --radius:18px; --radius-sm:12px; --radius-pill:999px;
  --ease:cubic-bezier(.16,1,.3,1);
}
```

- Hairlines: `--line` = 7% white (the Higgsfield signature). Never raise above 13%
  (`--line-strong`) for resting borders.
- Grain: body `::after` feTurbulence opacity `.035`; poster grain filter opacity `.22`.
- Glass: `backdrop-filter:blur(16px) saturate(1.2)` on header; `blur(10px)` modals.
- Easing: single custom `--ease` for all motion. No other curves.

## Typography
- **Display:** Space Grotesk 600/700, negative tracking (`-0.02em` to `-0.085em`),
  uppercase for hero (`clamp(54px,7.3vw,106px)`). Used for titles, KPIs, logo.
- **Text:** Inter 400/500/600, 13.5–15px body, line-height 1.5–1.6, measure ~390px max.
- **Mono:** JetBrains Mono 400/500/600, 8.5–13px, uppercase, letter-spacing 0.06–0.22em.
  Used for labels, steps, chips, metadata, buttons.
- Pairing axis: display vs mono (bold statement vs technical metadata). Inter is the
  quiet bridge. No new fonts.

## Color rules
- Commitment tier: **restrained** — lime carries ~3% of surface (CTA, active states,
  glows, selected chips). Everything else is obsidian/ink.
- Semantic roles: lime = primary action/progress/selection; violet = secondary halo;
  orange = warning/attention; green `#22C55E` = success/running; red `#FF3B30` = error.
- Forbidden: warm neutrals, multi-color gradients as decoration, accent on large
  surfaces, light-mode as default (`.light` is opt-in only).
- Contrast (measured on `#060608`): ink `#F2F0EB` 17.8:1, dim `#9A9AA0` 7.2:1,
  accent 18.1:1, violet 4.8:1, green 8.9:1, red 5.7:1. **Muted `#6B6B70` is 3.8:1
  — below AA for small text. Faint `#3A3A3E` 1.8:1 is decorative only.**

## Motion vocabulary
- Families (keep ≤3): (1) `fadeIn` 0.4s on cards/hero, (2) `rise` 0.5s with
  60/120ms stagger on `main>*`, (3) `tin` 0.35s on toasts. Plus `pulse` for status
  dots and `boot`/`mq` (disabled in v11).
- Hover: `translateY(-1px)` to `-2px`, 0.16–0.18s. Press: `scale(0.98)` on coarse
  pointers. Focus: ring `0 0 0 4px rgba(232,255,66,0.10)`.
- `prefers-reduced-motion`: disables marquee/boot/rise + poster/CTA transitions.
  **Gap: `pulse`, spinner `r`, `fadeIn`, `tin` are not covered.**

## Layout patterns
- Grid: header `auto 1fr auto` (desktop) → `1fr` stacked (≤980px). Main
  `max-width:1240px` (1400px in cinema mode), padding 32/20.
- Breakpoints: 980 (header stack), 700 (single column, 42px touch), 390, 340.
- Hero: 2-col `1fr .92fr` → 1-col ≤680px. Cards: `auto-fill minmax(280px,1fr)`.
- Scroll: steps horizontal with `scroll-snap-type:x proximity` on coarse pointers;
  cinema pipeline `repeat(7,72px)` with snap.

## Component patterns
- Buttons: pill `999px`, mono 11px uppercase, 11/16 padding. Primary `.big` lime on
  ink. Secondary glass. `.sm` 36px min-height (mobile).
- Cards `.cd`: 18px radius, 1px hairline, hover lift + shadow. `.ch` choice cards.
- Modals: bottom-sheet on phone (20px radius top, 92vh), centered desktop.
- Toasts: lime left border 3px, animated entry.
- Inputs: 12/14 padding, 12px radius, mono 13.5px, 16px on mobile (anti-zoom).

## Responsive requirements (iPhone first)
- `viewport-fit=cover`, `maximum-scale=5`. Safe-area insets on header/main/toast/console.
- Inputs ≥16px on mobile. Touch targets 42–44px (currently `.st` 34px, `.gc button`
  38px, `.sm` 36px — **below target**). Header stacks, steps scroll-snap.
- `overflow-x:hidden` on html/body; images/videos `max-width:100%`.

## Accessibility requirements
- Visible focus ring (currently `outline:0` globally with no `:focus-visible`
  replacement — **keyboard users lose focus indication**).
- Reduced-motion must cover all animated properties (see gap above).
- `muted`/`faint` text must not carry essential info at small sizes.
- No skip link to `#main`. ARIA present on hero/poster/pipeline; form labels
  associated. Theme toggle persists via `localStorage`.

## Acceptance criteria (review checklist)
- [ ] Obsidian `#060608` + lime `#E8FF42` + hairlines 7% respected.
- [ ] Space Grotesk display + JetBrains Mono labels; no new fonts.
- [ ] Header stacks ≤980px; steps scroll-snap on touch.
- [ ] Inputs 16px on mobile; touch targets ≥42px.
- [ ] Safe-area insets applied (notch/Dynamic Island).
- [ ] Reduced-motion respected for all animations.
- [ ] Focus visible for keyboard navigation.
- [ ] Empty/loading/error/success/long-text/narrow-screen states verified.
- [ ] No v10 decorative effects in production path (marquee/cursor/boot hidden).
- [ ] Contrast: muted text only for non-essential metadata.

## Rejected (already decided, do not reintroduce)
| Tried | Why it lost | What is there instead |
|---|---|---|
| v10 marquee "Soul Cinema" | Decorative spectacle, no task value | Disabled; pipeline + hero carry the page |
| v10 custom lime cursor | Desktop-only gimmick, accessibility risk | Native cursor; spotlight disabled |
| v10 card spotlight `--mx/--my` | Motion noise, perf cost | Static cards with hover lift |
| v10 boot screen 2.6s | Delays content, blocks interaction | Disabled; page renders immediately |
| v10 cascade `rise` on every step | Distracting on navigation | Kept once on `main>*` only |
| Generic indigo/violet theme (v8) | Off-brand vs Higgsfield | Obsidian + lime locked |
| Light mode as default | Breaks cinema identity | Dark default, `.light` opt-in |

## Review verdict (designer)
**Approved with conditions.** DA is coherent and on-brand (Higgsfield obsidian/lime,
brutalist-luxe, Space Grotesk + JetBrains Mono, glass, 7% hairlines). Responsive
iPhone-first foundations are in place and match the documented spec.

Conditions to clear before prod promotion (hand off to builder):
1. Touch targets: raise `.st` (34→44px), `.gc button` (38→44px), `.sm` (36→42px)
   on mobile, or document 34px as intentional compact chips.
2. Focus: replace global `outline:0` with a visible `:focus-visible` ring.
3. Reduced-motion: extend the media query to `pulse`, spinner `r`, `fadeIn`, `tin`.
4. Contrast: `--muted` 3.8:1 — restrict to non-essential metadata or darken to
   `#8A8A90` (≥4.5:1).
5. Confirm v10 leftover (hidden via CSS) is removed from production bundle to
   avoid dead weight, or keep as archived fallback (current approach acceptable).
6. README badge still says "v11_CINEMA_STUDIO" while task scope is v10 — reconcile
   versioning before release notes.

No blocking visual defect found; hero, pipeline, workbar and forms render correctly
at desktop 1280px with no console errors.
