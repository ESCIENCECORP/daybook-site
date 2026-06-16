# Updating the Daybook AI website

The site is a static site. **Editing any file and pushing to `main` auto-deploys to https://daybook-ai.com within ~30 seconds** (Render builds on every push). No build step, no backend.

```
git clone https://github.com/ESCIENCECORP/daybook-site
# edit files
git commit -am "update copy"
git push            # → live in ~30s
```

## Where things are
- `index.html` — the whole landing page. Each section is marked with an HTML comment (`<!-- 4 · AI... -->`). Copy lives in plain text between the tags — edit it directly.
- `privacy.html`, `terms.html`, `press.html` — the sub-pages.
- `styles.css` + `tokens/*.css` — colors, fonts, spacing (rarely need editing).
- `fonts/` — self-hosted Inter (don't touch).
- `assets/` — `brand/` (icon), `badges/` (store badges), `shots/` (app screenshots), `og/` (social card).

## Common edits

**Change wording:** open `index.html`, find the section by its comment, edit the text. Headlines are in `<h1>`/`<h2>`, body in `<p>`, bullet lists in `<li>`.

**Swap the Google Play link:** it appears as `https://play.google.com/store/apps/details?id=com.escienceapps.daybook` — search & replace if the listing URL changes.

**Turn on the App Store badge when iOS ships:** find the `badge-soon` spans (hero + final CTA) and replace each with a real App Store link, e.g.
`<a class="badge-play" href="https://apps.apple.com/app/idXXXXXXXX"><img src="/assets/badges/app-store.png" alt="Download on the App Store"></a>`
(add the official Apple badge PNG to `assets/badges/`). Also flip the "iOS — coming soon" lines in the Platforms section and FAQ.

**Show pricing (when Pro launches):** pricing is currently an HTML comment in `index.html` (search for `9 · PRICING`). Replace the comment with a real Free-vs-Pro module and set the final tiers/prices.

**Replace the fold animation with the real video:** in the `★ FOLDABLE SHOWCASE` section there's a comment `SWAP-IN POINT`. Replace the `.foldstage` block with:
`<video class="foldstage" autoplay muted loop playsinline poster="/assets/.../poster.jpg"><source src="/assets/.../fold.webm" type="video/webm"><source src="/assets/.../fold.mp4" type="video/mp4"></video>`

**Update screenshots:** drop new PNGs into `assets/shots/` (same filenames) and push.

## Privacy / analytics
There is **no analytics, no tracking, no cookies, no third-party requests** — by design (it's the brand). Inter is self-hosted; the only external script is the Lucide icon CDN. Keep it that way unless there's a deliberate decision to add privacy-respecting (cookieless) analytics.
