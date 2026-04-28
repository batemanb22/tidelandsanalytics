# Tidelands Analytics — Quarto Website (v2)

This is the source for [tidelandsanalytics.com](https://tidelandsanalytics.com), built with [Quarto](https://quarto.org) and deployed via GitHub Pages.

## What's new in v2

- **Hero section** on homepage with gradient background and clear CTAs
- **Service cards with icons** — Font Awesome icons for visual interest
- **Toolbox badges** — visual list of technologies
- **Featured work section** on homepage with screenshots
- **Restructured Portfolio page** focused on two flagship dashboards with multiple views
- **App screenshots integrated** — your four uploaded screenshots are wired in
- **Blog system** — `/posts/` directory with one published post and one draft
- **Polished services page** with section icons and process steps
- **Refined contact page** with icons
- **Improved theme** — better typography, spacing, hover effects

## Project structure

```
tidelands-site/
├── _quarto.yml          # Site config (nav, theme, metadata)
├── index.qmd            # Home page (with hero)
├── apps.qmd             # Portfolio (Shiny app showcase)
├── services.qmd         # Services page
├── blog.qmd             # Blog landing/listing page
├── contact.qmd          # Contact page
├── theme.scss           # Custom styling (colors, fonts, layouts)
├── styles.css           # Extra CSS polish
├── posts/               # Blog posts live here
│   ├── _metadata.yml    # Default post settings
│   ├── welcome/
│   │   └── index.qmd    # First published post
│   └── excel-stops-being-enough/
│       └── index.qmd    # Draft post (set `draft: false` to publish)
├── assets/              # Logos, screenshots, images
│   ├── logo.png         # ← YOU need to add this
│   ├── app-pharma-1.png # Screenshots already added
│   ├── app-pharma-2.png
│   ├── app-pharma-3.png
│   └── app-micro-1.png
├── CNAME                # Custom domain config
└── .github/workflows/   # Auto-deploy on git push
```

## Getting started

If this is your first time setting up the project, see the migration guide section below. If you're upgrading from v1, just replace your old project files with these (keeping your `assets/logo.png`).

To preview locally:

```bash
cd tidelands-site
quarto preview
```

To build the site:

```bash
quarto render
```

## Writing blog posts

### Option A — write your own

1. Create a new folder under `posts/`, e.g. `posts/my-new-post/`
2. Create `index.qmd` inside it with this frontmatter:

   ```yaml
   ---
   title: "Your Post Title"
   description: "One-line summary that shows in the listing"
   author: "Bryan Bateman"
   date: "2026-04-27"
   categories: [analytics, r]
   reading-time: true
   ---

   Your post content in Markdown...
   ```

3. Save, preview, and push to deploy.

### Option B — AI-drafted with your review

Once the agent infrastructure is set up (after migration), the workflow becomes:

1. You: "Write a blog post about choosing the right chart type"
2. Agent: drafts a post, commits it as a **draft** (`draft: true` in frontmatter)
3. You: review the draft locally, edit as needed
4. You: change `draft: false` and push
5. Site auto-deploys with the new post

The `draft: true` flag in the frontmatter is what keeps a post hidden until you're ready. Notice the second example post (`excel-stops-being-enough`) is set as a draft — it won't show in the blog listing until you flip that to `false`.

## Customization tips

### Adjusting the hero section
Edit `index.qmd` — the hero text, subtitle, and CTAs are at the top.

### Changing colors
Edit `theme.scss` — the brand colors are defined at the top:
- `$primary` — main blue
- `$accent` — bright teal for highlights
- `$dark-blue` — darker shade for gradients

### Reordering sections
Each homepage section is wrapped in a `:::` block in `index.qmd`. Cut and paste them in any order.

### Changing the navbar logo size
In `theme.scss`, find `.navbar-brand img { max-height: 80px; }` and adjust.

## Migration runbook (if not yet deployed)

See the v1 README for the full step-by-step migration from GoDaddy. The same steps apply.

Quick summary:
1. Install Quarto, Git, and create a GitHub account
2. `quarto preview` to test locally
3. Create a GitHub repo, push the code
4. Enable GitHub Pages in repo settings (use GitHub Actions)
5. Update DNS at GoDaddy to point to GitHub
6. Verify the site works on your custom domain
7. Cancel the GoDaddy Website Builder subscription

## Troubleshooting

**Hero looks broken / no styling.** Make sure `theme.scss` is in the project root and `_quarto.yml` references it.

**Icons don't show up.** The Font Awesome CDN link is included in each page's frontmatter. If you create a new page that uses icons, copy the `include-in-header` block from `index.qmd`.

**Blog post not showing.** Check the frontmatter — `draft: true` will hide it. Also make sure the date is not in the future.

**Screenshots not displaying.** Verify the files exist at the exact paths referenced (e.g., `assets/app-pharma-1.png`).

## What an AI agent can do once this is on GitHub

- **Draft blog posts** based on prompts you give it
- **Update the portfolio** when you build new Shiny apps
- **Refresh content** based on changes you describe
- **Fix typos and improve copy** across pages
- **Generate case studies** from project notes you provide
- **Monitor the site** for broken links, performance issues
- **Update SEO metadata** based on best practices

We'll wire this up after the migration is complete.
