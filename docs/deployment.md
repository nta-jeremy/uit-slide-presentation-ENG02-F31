# Deployment

## Platform: Vercel

## URL: https://uit-eng02-f31-08-volunteering.vercel.app

## Deploy Command
```bash
vercel --prod --yes
```

## Project
- Static site, no build step (framework: none)
- Vercel project: `tunganh252s-projects/uit-eng02-f31-volunteering`
- Linked to GitHub repo: `nta-jeremy/uit-slide-presentation-ENG02-F31`
- Domain `uit-eng02-f31-08-volunteering.vercel.app` aliased to the production deployment (see `vercel.json`)

## Structure
- `index.html` — landing page linking to slide deck and speaker notes (reachable at `/index.html`, not at `/`)
- `topic8-volunteering-slides.html` — slide deck; also served at `/` via redirect
- `speaker-notes.html` — speaker notes & cue sheet
- `images/` — slide assets; each `NN.png` has a `NN.webp` sibling (generated with `cwebp -q 82`), served via `<picture>` with WebP as the primary source and PNG as fallback. Regenerate the `.webp` file whenever a `.png` is replaced.
- `vercel.json` — redirects `/` to `/topic8-volunteering-slides.html`; `/speaker-notes.html` is served directly (no redirect); sets a 1-year immutable `Cache-Control` on `/images/*`

## Environment Variables
None.

## Custom Domain
Not configured. `uit-eng02-f31-08-volunteering.vercel.app` is a Vercel-managed alias (not a custom domain), added via `vercel alias set`. Old alias `uit-eng02-f31-volunteering.vercel.app` was removed.

## Deployment Protection
SSO protection (Vercel Authentication) disabled via `vercel project protection disable --sso` so the site is publicly accessible without a Vercel login.

## Rollback
```bash
vercel rollback [deployment-url]
```
