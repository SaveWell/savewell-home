# Repository Guidelines

## Project Structure & Module Organization
The repository is a static site with individual HTML pages at the root (`index.html`, `about.html`, etc.). Shared assets (logos, favicons, imagery) live under `assets/`. Data-driven widgets read from `data/providers.json`; keep derived tables or CSVs beside that file. 

## Build, Preview, and Data Scripts
No build step is required because Tailwind loads via CDN. For local preview run `python3 -m http.server 8000` from the repo root and visit `http://localhost:8000/index.html`. If you prefer Node tooling, `npx serve .` works as well.

## Coding Style & Naming Conventions
Author HTML with semantic tags, 2-space indentation, and lowercase filenames using hyphens when multiple words are needed (e.g., `preferred-specialists.html`). Organize Tailwind utility classes from layout → spacing → color to match existing pages. Put any custom CSS in a scoped `<style>` block near the head and keep inline scripts minimal and vanilla JS.

## Testing & QA
There is no automated test suite. After changes, load the page in both desktop and mobile widths, click the homepage carousel, and verify the `search.html` specialty/ZIP filter still works with the updated data.

## Commit & Pull Request Guidelines
Recent history uses short descriptive messages; continue that pattern but prefer present-tense imperatives such as `Update results filters`. Group related asset and content updates into one commit. PRs should include: bullet summary of changes, affected pages, screenshots or screen recordings for visual tweaks, and links to any tracking tickets. Note manual test steps in the description so reviewers can replay them quickly.
