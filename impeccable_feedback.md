# Impeccable Redesign Log — SaveWell Homepage

## 1. /critique — Design Audit (Starting Point)

### Design Health Score: 23/40 (Moderate)

| # | Heuristic | Score | Key Issue |
|---|-----------|-------|-----------|
| 1 | Visibility of System Status | 2 | No current-section indicator in sticky nav |
| 2 | Match System / Real World | 3 | Clear Medicare-appropriate language |
| 3 | User Control and Freedom | 2 | No back-to-top; smooth scroll forced without reduced-motion |
| 4 | Consistency and Standards | 2 | Dark benefits section breaks visual language |
| 5 | Error Prevention | 3 | Content page, few interactive elements |
| 6 | Recognition Rather Than Recall | 3 | Nav visible, CTAs labeled |
| 7 | Flexibility and Efficiency | 1 | No skip-to-content, no keyboard shortcuts |
| 8 | Aesthetic and Minimalist Design | 2 | 10-item specialty grid + 5 testimonials = bulk |
| 9 | Error Recovery | 3 | N/A for this page |
| 10 | Help and Documentation | 2 | No FAQ, no help element |

### AI Slop Verdict: Moderately AI-generated appearance

Tells found:
- **Inter font** — the #1 AI-generated font
- **Identical card grids repeated 3x** — How It Works, Specialties, Benefits all use centered icon/number + heading + paragraph
- **Everything centered** — every section header, card, CTA
- **Large icons above every heading** — "icon hat" pattern on benefits and steps
- **Pill eyebrow badges** on every section
- **Rounded rectangles with identical shadows** — `border-radius: 1rem` + `box-shadow: 0 4px 20px rgba(0,0,0,0.06)` applied uniformly

Not present (good): No dark mode, no glassmorphism, no gradient text, no neon accents, no nested cards, no side-stripe borders.

### Automated Scan: 11 issues
- 10 low-contrast violations (white on teal gradients at 3.1:1, white-on-white at 1.0:1)
- 1 overused font (Inter)

### Priority Issues Identified

1. **[P1] Inter font** — zero personality, signals "AI template"
2. **[P1] Contrast failures** — WCAG AA not met in multiple places
3. **[P2] Dark navy benefits section** — violates light-mode-only principle
4. **[P2] No `prefers-reduced-motion`** — non-negotiable accessibility requirement
5. **[P2] Monotonous card-grid repetition** — every section identical structure

### What Was Working
- Hero value proposition clear above the fold
- 3-step "How it Works" genuinely simple
- Phone number in sticky header (smart for 65+ audience)

---

## 2. /arrange — Layout & Structure Redesign

### Problems Addressed
- Every section followed identical pattern: centered pill → centered title → card grid
- 10-item specialty grid was a wall before trust signals
- "100% Free" buried in 4th section
- 5 Wisconsin testimonials for a Las Vegas launch
- Dark benefits section broke light-mode identity
- No FAQ/objection handling for skeptical audience

### Structural Changes

**Removed:**
- 10-item specialty card grid (already on search page)
- Dark navy benefits section
- 5 identical testimonial cards
- Repetitive centered-pill → centered-title → card-grid pattern
- Footer image overlap issue
- Forced `scroll-behavior: smooth` (wrapped in `prefers-reduced-motion`)

**New page structure (6 sections, down from 7):**

1. **Hero** — "100% Free — No Cost, No Catch" badge elevated to first visible element. Secondary CTA changed to "Call Us" (better for 65+). Trust items without divider line.

2. **"What's the catch?"** — Addresses skepticism head-on. Left-aligned header. 2×2 grid of promise points (not cards). Explains *why* it's free. Benefits content woven in here instead of a separate dark section.

3. **"Three steps. That's it."** — Left-aligned numbered list with horizontal rows separated by rules. Not centered cards. Header brevity matches process brevity.

4. **Testimonials** — One large featured quote (the skeptic-turned-advocate) + two smaller supporting quotes. 2-column asymmetric layout. Locations updated to Las Vegas/Henderson.

5. **FAQ** — Accordion addressing top 5 objections. 40/60 asymmetric layout (sidebar header + content). "What specialties?" links to search page.

6. **CTA** — Side-by-side (text left, buttons right). Two actions: search and call.

### Layout Principles Applied
- No two sections share the same layout structure
- Left-aligned headers throughout
- Varied spacing rhythm: tight within groups, generous between sections
- Asymmetric compositions (40/60 FAQ, featured/secondary testimonials)
- Page significantly shorter and more focused

---

## 3. /typeset — Typography Overhaul

### Problems Addressed
- Inter is the #1 AI-generated font — zero personality
- Body text at 16px, below 18px accessibility target
- Sizes too close together (1rem, 1.02rem, 1.05rem, 1.08rem — all within 2px)
- Single font family for everything — no heading/body contrast
- Weight 800 on all headings was heavy-handed

### Font Selection Rationale

**Process followed (from impeccable font selection procedure):**

1. Brand voice words: "warm, reassuring, plain-spoken"
2. Reflex fonts rejected: Lora, Fraunces, DM Serif — all on the banned list
3. Physical object metaphor: "a letter from a local community health organization — well-designed brochure at your doctor's office that feels personal, not mass-produced"
4. Cross-check: Bitter (slab serif) is not the reflex pattern for "warm" (that would be Lora/Fraunces). Source Sans 3 is genuinely warmer than Inter, not just the next default.

**Initial pairing:**
- Headings: Bitter (slab serif) + Body: Source Sans 3 (humanist sans)

**Font exploration — 5 options tested:**
After the initial implementation, explored alternatives to find the best fit:
- **Option A**: Vollkorn + Atkinson Hyperlegible — warm/bookish + maximum accessibility
- **Option B**: Zilla Slab + Nunito — open/friendly slab + rounded warmth
- **Option C**: Brygada 1918 + Karla — elegant serif + quirky grotesque
- **Option D**: Petrona + Libre Franklin — expressive serif + editorial sans
- **Option E**: Bitter + Nunito — grounded slab + rounded warmth

**Final pairing (user selected Option E):**
- **Headings: Bitter** (slab serif) — warm, grounded, trustworthy. Designed for screen reading. Slab serifs are inherently "established and reliable." Feels like something a trusted local organization would use.
- **Body: Nunito** (rounded sans) — subtly rounded terminals give it a friendly, approachable feel without being childish. Extremely readable at 18px. Warmer than Source Sans 3, the rounded forms echo the "neighborly" brand personality.

### Type Scale (1.25 ratio)

| Role | Size | Ratio step |
|------|------|------------|
| Caption | 0.875rem (14px) | — |
| Badge | 0.9375rem (15px) | — |
| Secondary body | 1.0625rem (17px) | — |
| Body / FAQ questions | 1.125rem (18px) | Base |
| Subheading (h3) | 1.25rem (20px) | ×1.11 |
| Blockquote | 1.375rem (22px) | ×1.22 |
| h2 (section) | clamp(1.75rem, 3.5vw, 2.5rem) | Fluid |
| h1 (display) | clamp(2.25rem, 5vw, 3.5rem) | Fluid |

### Weight Strategy
- Bitter 700 for h1/h2 (serifs carry weight, don't need 800)
- Bitter 600 for h3 subheadings
- Bitter 400 italic for blockquote
- Source Sans 3 400 for body
- Source Sans 3 600 for labels/emphasis/badges
- Source Sans 3 700 for button text

### Other Changes
- Line heights widened to 1.7 for body (generous for older eyes)
- Heading line-height at 1.12–1.18 (tight for display text)
- Letter-spacing -0.01em on headings (tighter, more polished)
- Body text at 18px meets accessibility target
- Georgia as Bitter fallback for similar metrics during FOUT
- Only 3 weights loaded per font (performance)

---

## 4. /colorize — Color Palette Evolution

### Problems Addressed
- Pure gray neutrals (#f3f4f6, #e5e7eb, #6b7280, #4b5563) had no warmth
- Cool teal + cool navy + cool mint = "clinical fintech" feel
- Wine accent (#8a0052) was stark corporate magenta
- 10 contrast violations from automated scan
- Design context called for "softer, warmer tones — possibly pastels"

### New Palette — Warm Sage Neutrals

All neutrals tinted toward the brand's teal/sage hue for subconscious cohesion:

| Token | Old Value | New Value | Purpose |
|-------|-----------|-----------|---------|
| `--cream` | #fff | #faf8f6 | Warm off-white page background |
| `--surface` | #f3f4f6 | #f2f4f2 | Sage-tinted section backgrounds |
| `--border` | #e5e7eb | #dce2dd | Sage-tinted borders |
| `--text-body` | #4b5563 | #4d5753 | Warm sage body text (7.5:1 — AAA) |
| `--text-muted` | #6b7280 | #697568 | Warm sage muted text (4.9:1 — AA) |
| `--heading` | #1e3a5f | #243837 | Dark sage headings (~12:1 — AAA) |
| `--sage-pale` | #e6f7f7 | #eaf1ec | Warm sage for badges/icon bgs |
| `--sage-light` | #ecfdf5 | #f0f5f1 | Warm sage for hero badge |
| `--sage-accent` | #d1fae5 | #c8ddd0 | Warm sage accent |

### Brand Accent Changes

| Color | Old | New | Rationale |
|-------|-----|-----|-----------|
| saveWine (hover) | #8a0052 (stark magenta) | #8a4f60 (dusty berry) | Warmer, more "neighborly." 6.4:1 contrast on white. |
| saveTealDark | #065e60 | #07635e | Slightly warmer dark teal |
| CTA gradient | #0b7a7c → #065e60 | #0a706d → #085c58 | Warmer, better white-text contrast |

### Contrast Verification
- `--heading` (#243837) on white: ~12:1 (AAA)
- `--text-body` (#4d5753) on white: 7.5:1 (AAA)
- `--text-muted` (#697568) on white: 4.9:1 (AA)
- `saveWine` (#8a4f60) on white: 6.4:1 (AA+)
- White on CTA gradient (#0a706d): 5.5:1+ (AA)
- White on saveTeal button (#0b7a7c): 5.3:1 (AA)

### Automated Scan Result: 0 issues (was 11)

---

## 5. /audit + /harden + /adapt + /normalize + /polish — Combined Pass

### Audit Score: 11/20 (Acceptable) — before fixes

| # | Dimension | Score | Key Finding |
|---|-----------|-------|-------------|
| 1 | Accessibility | 2 | No skip-to-content; broken mobileMenu HTML; incomplete FAQ ARIA |
| 2 | Performance | 2 | Tailwind CDN is dev-only tool |
| 3 | Theming | 2 | Tokens exist but hard-coded hex values remain |
| 4 | Responsive | 2 | Touch targets too small on phone link and nav |
| 5 | Anti-Patterns | 3 | Clean — distinctive fonts, varied layouts |

### All fixes applied in one pass:

**P0 — Blocking:**
- Fixed broken HTML on mobileMenu div (missing `>` on opening tag)

**P1 — Major:**
- Added skip-to-content link (first focusable element, visually hidden until focused)
- Added `id="main"` to `<main>` tag as skip target
- Added `aria-expanded` and `aria-controls` to mobile menu button
- Updated mobile menu JS to toggle `aria-expanded` state
- Increased phone number link padding from `px-1 py-1` to `px-3 py-2` (meets 44×44px)
- Fixed CTA paragraph: replaced `opacity: 0.92` with solid `color: #e2eeeb` for full contrast control
- Completed FAQ ARIA pattern: added `id`, `aria-controls`, `role="region"`, `aria-labelledby` to all 5 Q&A pairs

**P2 — Minor:**
- Increased nav link touch targets: added `py-2 px-3 rounded-md`, reduced gap from `gap-6` to `gap-1`
- Hero image now shows on mobile (140px width) instead of `display: none`
- Replaced ALL hard-coded hex colors with CSS variable tokens:
  - Added `--primary: #0b7a7c`, `--primary-dark: #1a5c52`, `--cta-from`, `--cta-to`
  - Replaced all `var(--navy)` → `var(--heading)`, `var(--gray-600)` → `var(--text-body)`, etc.
  - Removed all 7 legacy alias variables
- Added footer link touch targets (`inline-block py-1`)

**P3 — Polish:**
- Added JSON-LD structured data: Organization schema + FAQPage schema (all 5 questions)
- HTML validates clean (tag nesting check passes)

### Automated scan after fixes: 2 false positives
Both are from the static analyzer unable to resolve text colors against gradient backgrounds (CTA section). Actual rendered contrast passes AA.

### Note on Tailwind CDN
The `cdn.tailwindcss.com` script remains — this is a production deployment concern that requires a build step change, not a code fix. Flagged for future migration to Tailwind CLI or a static CSS build.
