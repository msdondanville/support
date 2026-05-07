# Stuut Support — Mintlify docs

This folder is a complete Mintlify documentation site converted from the original `support.html` proof-of-concept. Push it to a GitHub repo, connect to Mintlify, and you're live.

## Folder structure

```
mintlify-docs/
├── docs.json              # Site config (branding, navigation, colors)
├── introduction.mdx       # Landing page
├── videos.mdx             # Video Walkthroughs (12 Loom embeds)
├── collections/           # 📂 Collections theme
│   ├── daily-workflow.mdx
│   ├── emails-and-drafts.mdx
│   ├── ai-call-agent.mdx
│   ├── promise-to-pay.mdx
│   ├── disputes.mdx
│   └── payment-portal.mdx
├── cash-app/              # 💵 Cash App theme
│   ├── cash-application.mdx
│   └── payments.mdx
├── platform/              # 🖥 Platform theme
│   ├── getting-started.mdx
│   ├── customers-invoices.mdx
│   ├── troubleshooting.mdx
│   └── glossary.mdx
└── logo/                  # Mascot SVGs (light/dark/favicon)
    ├── light.svg
    ├── dark.svg
    └── mascot.svg
```

## Deploy in 7 steps

### 1. Create a GitHub repository
Name it something like `stuut-support-docs`. Make it private if you want.

### 2. Push these files to the root of the repo
```bash
cd mintlify-docs
git init
git add .
git commit -m "Initial Mintlify docs"
git branch -M main
git remote add origin git@github.com:<your-org>/stuut-support-docs.git
git push -u origin main
```

### 3. Sign up at mintlify.com
Use GitHub SSO so the repo connection is one click.

### 4. Connect the repo
In the Mintlify dashboard: **Settings → Source repository → Connect GitHub** → pick `stuut-support-docs`. Mintlify reads `docs.json` and builds automatically.

### 5. Preview the site
You'll get a URL like `https://stuut.mintlify.app` (or whatever subdomain Mintlify assigns). Open it and click around.

### 6. Custom domain (optional)
**Settings → Custom domain → Add `support.stuut.co`**. Mintlify gives you a CNAME to add to your DNS provider. Once propagated (usually < 1 hour), your docs are live at `support.stuut.co`.

### 7. Enable Mintlify Chat (optional, paid plan)
**Settings → AI → Chat → Enable**. Mintlify will automatically index every MDX file as the knowledge base. No additional config — it replaces the custom chatbot from the HTML site with a much smarter, more accurate one.

## Local preview (optional)

To preview before pushing:

```bash
npm i -g mint
cd mintlify-docs
mint dev
```

Opens at `http://localhost:3000`.

## What's in each file

- **`docs.json`** — site name, colors, logo paths, navigation groups (3 themes), navbar buttons, footer
- **`introduction.mdx`** — landing page with theme cards
- **Topic `.mdx` files** — frontmatter + `<AccordionGroup>` with all FAQs from that topic. Callouts use Mintlify's `<Note>`, `<Tip>`, `<Warning>` components
- **`videos.mdx`** — all 12 Loom embeds in `<CardGroup>` grids per theme
- **Logo SVGs** — your robot mascot, sized for the header

## Updating content

Just edit any `.mdx` file and push to `main`. Mintlify rebuilds automatically. Pull requests show preview deploys (Vercel-style) so you can review changes before merging.

## Re-running the converter

If you make more edits to the original `support.html` and want to regenerate, run:

```bash
cd ..  # back to Support Site/
python3 convert_to_mintlify.py
```

Files are overwritten; commit the changes.
