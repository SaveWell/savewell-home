# SaveWell Website — Architecture & Navigation Summary

**Domain:** savewellnow.com
**Hosting:** Static site (GitHub Pages via CNAME)
**Stack:** Plain HTML + Tailwind CSS (CDN) + vanilla JavaScript — no build step, no framework


## Site Map

```
savewellnow.com
├── index.html            ← Homepage / landing page
├── how-it-works.html     ← Detailed program explainer + FAQ
├── search.html           ← Provider search (specialty & ZIP)
├── contact.html          ← Contact form + phone/email info
├── privacy.html          ← Privacy policy
├── terms.html            ← Terms & conditions
├── data/
│   └── providers.json    ← Provider directory (fetched at runtime)
└── assets/
    ├── savewell-logo.png
    ├── favicon.png
    ├── medicare-people.png
    ├── belong-health-logo-trim.png
    ├── belong-health-logo-trim2.png
    └── hero/
        ├── pennywise-peter.png
        └── pennywise-peter-waist.png
```


## Navigation Structure

### Primary Nav (sticky header, all pages)

Visible on desktop (`md:flex`); collapses to hamburger menu on mobile.

| Link             | Target              |
|------------------|---------------------|
| Logo (SaveWell)  | `index.html`        |
| How it Works     | `how-it-works.html` |
| Search Providers | `search.html`       |
| Contact Us       | `contact.html`      |
| Phone CTA        | `tel:5107364332`    |

### Footer (all pages, 4-column grid)

| Column   | Links                                              |
|----------|----------------------------------------------------|
| Brand    | Logo + tagline                                     |
| Learn    | How it Works, Search Providers                     |
| Legal    | Terms & Conditions (`terms.html`), Privacy (`privacy.html`) |
| Contact  | Contact Us, hello@savewellnow.com, (510) 736-4332 |


## Page-by-Page Breakdown

### 1. Homepage (`index.html`)

The main landing page with six vertically stacked sections:

1. **Hero** — Headline ("Earn rewards for choosing trusted doctors"), two CTAs (Search Providers → `search.html`, How it Works → `#how-it-works` anchor), trust badges, and a hero image.
2. **How It Works** (`#how-it-works`) — 3-step card grid: Find a doctor → Get care → Save money.
3. **Specialties** (`#providers`) — Grid of 10 specialty cards (Cardiology, Dermatology, Endocrinology, Gastroenterology, Hematology & Oncology, Neurology, OB/GYN, Orthopedic Surgery, Rheumatology, Surgical Centers) + "Search Providers Now" CTA.
4. **Benefits** — Dark navy section with 3 cards: Free to Join, Automatic Rewards, Quality Doctors.
5. **Testimonials** — 5 testimonial cards from members (Mary J., Robert K., Patricia L., James M., Dorothy H.), all Wisconsin-based.
6. **CTA Banner** — Teal gradient with "Ready to Start Saving?" and Search Providers button.

### 2. How It Works (`how-it-works.html`)

Long-form educational page with these content blocks:

- **Hero banner** — Teal gradient header.
- **Program overview** — What SaveWell is and how rewards work.
- **6-step timeline** — Visual timeline from "You need specialist care" through "See your savings."
- **Covered services** — List of 10 medical specialties.
- **Eligibility** — Must have Medicare Part A & B + Medigap plan + be in a covered area.
- **Provider selection criteria** — Clinical quality, patient outcomes, satisfaction, board certification.
- **FAQ accordion** — 6 questions covering savings amounts, appointment process, reward timing, out-of-network use, area availability, and paperwork.
- **Bottom CTA** — "Ready to Start Earning Rewards?" with Search Providers link.

### 3. Search Providers (`search.html`)

Interactive provider directory powered by client-side JavaScript:

- **Search form** — Dropdown for specialty (10 options + "All") and ZIP code input. Requires at least one field.
- **Results grid** — Cards showing provider name, specialty, address, premium savings badge, and call button. Loaded from `data/providers.json` via `fetch()`.
- **Sorting** — Results sorted by premium savings (descending), then alphabetically.
- **No results state** — Friendly empty state encouraging users to try a nearby ZIP or broaden specialty.

### 4. Contact Us (`contact.html`)

Two-column layout:

- **Left column** — Embedded JotForm (`form.jotform.com/jsform/260485416999070`) with a hidden success confirmation message.
- **Right column** — Phone card ((510) 736-4332), email card (hello@savewellnow.com), and office hours (Mon–Fri, 9 AM – 5 PM CT).

### 5. Privacy Policy (`privacy.html`)

Static content page covering data collection, cookie usage, and contact for data deletion requests.

### 6. Terms & Conditions (`terms.html`)

Scrollable container with full legal text (14 sections), last updated September 3, 2025. Covers access, accounts, prohibited uses, IP, third-party links, availability, data privacy, warranties, liability, indemnification, arbitration (JAMS, Orange County), class action waiver, termination, and general terms.


## User Flow

```
                    ┌──────────────┐
                    │   Homepage   │
                    │  index.html  │
                    └──────┬───────┘
               ┌───────────┼───────────┐
               ▼           ▼           ▼
       ┌───────────┐ ┌──────────┐ ┌──────────┐
       │How it Works│ │  Search  │ │ Contact  │
       │  (learn)   │ │Providers │ │   Us     │
       └─────┬─────┘ └────┬─────┘ └──────────┘
             │             │
             └──────┬──────┘
                    ▼
            ┌──────────────┐
            │  Call / Book │
            │  a Provider  │
            └──────────────┘
```

The primary conversion path is: **Homepage → Search Providers → Call a doctor**. The "How it Works" page serves as an educational detour for users who need more information before searching. The Contact page handles inbound questions and waitlist interest.


## Technical Notes

- **No build system** — All pages are standalone HTML. Tailwind is loaded from CDN (`cdn.tailwindcss.com`) with a custom config defined inline on each page.
- **Custom colors** — `saveTeal` (#0b7a7c), `saveWine` (#8a0052), `saveTealDark` (#065e60), `saveWineDark` (#6c0041).
- **Font** — Inter (Google Fonts), weights 400–800.
- **Provider data** — `data/providers.json` is a flat JSON array. Each entry has: `id`, `name`, `specialty`, `zip`, `city`, `state`, `address`, `phone`, `premium_savings`. Search filtering and sorting happen entirely client-side.
- **Form handling** — Contact form uses an embedded JotForm script (no custom backend).
- **Mobile responsive** — Hamburger nav on `< md` breakpoint. Hero image hidden on mobile. Grids collapse to single column.
- **Icons** — Inline SVGs throughout (no icon library dependency).
- **Shared scripts** — Each page has its own inline `<script>` for the year display and mobile menu toggle. No shared JS file.
- **SEO** — All pages include Open Graph and Twitter Card meta tags with canonical URLs.
