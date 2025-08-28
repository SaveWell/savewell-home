# SaveWell static site (GitHub Pages)

A simple, multi‑page static site using plain HTML + Tailwind via CDN.

## Quick start

1. Create a new GitHub repo and enable **GitHub Pages** (Settings → Pages → Branch: `main`, folder `/root`).  
2. Add these files to the repo.  
3. Put the provided logo at `assets/savewell-logo.png` (already included here).  
4. Commit and push. Visit your Pages URL to view the site.

## Notes
- Tailwind is loaded via the CDN to keep setup simple; you can swap to a build step later.
- The **search results** page (`results.html`) reads `?specialty=…&zip=…` and filters a small in‑page dataset to demo behavior.
- The **featured carousel** on the home page is a tiny vanilla‑JS slider you can replace with your preferred library later.
- Colors are approximations of the SaveWell palette used in the one‑pager for inspiration. Update them by editing the inline Tailwind config.
