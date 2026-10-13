# 250K with Mrs. K: campaign site

A one-page site in `site/`, made of plain HTML, CSS and JS with no build step. Everything in `site/` is the website.

## Preview locally

```bash
python3 -m http.server 4173 --directory site
```

Then open http://localhost:4173.

## Live at 250kwithmrsk.com

This repo ([LazarRyan/250kwithmrsk](https://github.com/LazarRyan/250kwithmrsk)) is connected to a Cloudflare Pages project. Every push to `main` goes live in about 30 seconds. The project has no build command, and its build output directory is `site`. To ship a change:

```bash
git add -A && git commit -m "Update site" && git push
```

The share preview and the Share button use absolute `https://250kwithmrsk.com/` URLs (4 places in `index.html`).

The old link, `ryanlazar.dev/250k`, permanently redirects here. The redirect is a `_redirects` file in the ryanlazar.dev repo, so links already shared keep working.

## Before launch

- **Media:** to swap a file, replace it with one of the same name.
  - `site/images/jonyull.jpg`: the portrait beside his story. It's shown with a warm tint, so black-and-white or color both work. A portrait crop around 1000×1500 is ideal.
  - `site/images/sharon.jpg`: the snapshot in Sharon's section. A landscape photo is best, since it sits in a photo-print frame.
  - `site/media/training.mp4` and `training.jpg`: the vertical training reel in "Built for this", plus its still frame. Keep it muted and under about 5 MB. Phone clips usually need re-encoding to get there.
- **Sponsor contact:** search `index.html` for `TODO`. The "For companies" link points to the @250KwithMrsK Instagram until there's an email.
- **Facebook:** the link goes to `facebook.com/250KwithMrsK`. Check that it works once the page exists.
- **GoFundMe link:** used 6 times. To change it, find and replace `https://gofund.me/09f36297f`.
## Race day: countdowns and live tracking

- **Countdowns** (section 05 and the hero badge) tick to:
  - **Marathon des Sables Stage 1:** Sunday, April 4, 2027 at 7:00 AM Sahara time. The time is an estimate taken from 2026's Stage 1 start. In the final 60 days, the page asks LiveTrail for the official 2027 start, and once that's published it switches over automatically.
  - **Honolulu Marathon:** Sunday, December 13, 2026 at 5:00 AM HST. This card hides itself a day after the race.
- **Live tracking** reads LiveTrail, the official MdS tracker. **When Jonyull gets his race number,** set it on the tracker in `index.html`, for example `data-bib="1234"`, then deploy. That's the only change race week needs.
  - From then on, the panel shows his kilometer, a stage-by-stage progress bar, last checkpoint, race time and overall rank. It refreshes every minute and links to his page on LiveTrail and the GPS map.
  - Until the 2027 event goes live on LiveTrail, the panel stays in its "race week" state, even with a bib set.
  - LiveTrail calls each event a tenant, and the page assumes the 2027 one is named `marathondessables_2027`, following 2026's pattern. If tracking doesn't appear on race day, check that name against the tracker page's network requests.
  - **To preview the live panel now,** add `?tracker-preview=2026-791` to the URL. It shows a real finisher from the 2026 race. `?tracker-preview=2026-5` shows a runner who withdrew.

## Motion and accessibility

The race section pins in place and "runs" 0 → 250 km as you scroll, and text lights up word by word. For visitors with **Reduce Motion** turned on, all of it turns off and the page renders as a normal static page with every fact visible.

## Hard rule for any future edits

Never name or reference a specific hospital or program as a partner or beneficiary, anywhere on the site: copy, alt text, titles or metadata. The content brief lists the exact names to avoid. Describe the cause only as **cancer rehabilitation care** or **cancer rehabilitation support**. Quick check (no output means you're clean):

```bash
grep -rniE "icare|hospital|foundation|rehab([^i]|$)" site/
```
