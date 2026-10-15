# DevDuo Studio - update guide

## What is in this folder
| File | Where it goes in your GitHub repo |
|---|---|
| index.html | repo root (replaces your current index.html.html) |
| favicon.svg | repo root (same folder as index.html) |
| favicon.ico | repo root |
| apple-touch-icon.png | repo root |
| changes/1-head-favicon-tags.html | piece: paste inside <head> |
| changes/1b-head-js-flag.html | piece: paste inside <head>, just BEFORE the <style> tag (needed for the scroll animations) |
| changes/2-styles.css | piece: replaces everything between <style> and </style> |
| changes/3-nav.html | piece: replaces the <nav>...</nav> in the masthead |
| changes/4-body-sections.html | piece: replaces everything from the old About section to the closing </footer> |
| images/bill-tracker.webp | NEW: upload the whole `images` folder to the repo root (same place as index.html). It is the Bill Tracker picture. |
| changes/6-add-picture-to-another-project.html | how to add a picture to any other project |
| changes/5-script-reveal.html | piece: paste just BEFORE </body> (scroll-reveal animation script) |
| alt-D-monogram/ | OPTIONAL: a beige-on-brown "D" favicon (same 3 file names). The main favicon files are your yellow DevDuo logo. |

## Route 1 - replace the whole file (fastest)
1. GitHub -> your repo -> click `index.html.html` -> pencil icon (Edit).
2. In the filename box at the top, change `index.html.html` to `index.html`.
3. Ctrl+A, delete, paste the full contents of the new `index.html`.
4. Commit changes.

## Route 2 - change one piece at a time
Do the pieces in this order, committing after each.
1. changes/1-head-favicon-tags.html -> paste after the `<link rel="canonical" ...>` line.
   changes/1b-head-js-flag.html -> paste just before the `<style>` tag.
2. changes/2-styles.css -> select everything between `<style>` and `</style>`, replace it.
3. changes/3-nav.html -> replace the old `<nav>...</nav>` (4 links) with the 6-link version.
4. changes/4-body-sections.html -> delete from `<section id="about"` down to (and including) `</footer>`, paste this file there. Keep the closing `</div>` that follows, then paste changes/5-script-reveal.html just before `</body>`.

## Upload the favicon files
Repo main page -> Add file -> Upload files -> drag favicon.svg, favicon.ico, apple-touch-icon.png -> Commit. They must sit in the same folder as index.html (the root).

## Make your own favicon.ico / apple-touch-icon.png from favicon.svg
- Website: realfavicongenerator.net -> upload favicon.svg -> download the package.
- Or ImageMagick:
    magick -background none favicon.svg -define icon:auto-resize=48,32,16 favicon.ico
    magick -background none -density 1200 favicon.svg -resize 180x180 apple-touch-icon.png
  (For apple-touch-icon use a full square image with no transparency; iPhones round the corners themselves.)

## Test
1. Wait 1-2 minutes after committing, then hard refresh (Ctrl+Shift+R).
2. Open https://devduostudio.com/favicon.svg directly - you should see the D icon.
3. Favicons are cached hard: check in a private window, or close and reopen the tab.
4. Chrome DevTools (F12) -> phone icon -> try 390px wide: no sideways scroll, nav wraps to two lines, cards stack.
5. Click every nav link: it should jump to its section.
6. Order down the page: hero, 01 How we work (brown), 02 Projects (beige), 03 Automation & AI (brown), 04 Client Reviews (beige), 05 About us (brown), Let's talk (beige).

## Change the colours later
Top of the CSS, in `:root`: `--bg-light` and `--bg-dark`. To flip a section, swap `section--light` / `section--dark` on its <section>.

## 3D figures and animations (new)
- All animations are pure CSS (sections 8, 8b and 9 of the CSS).
- "How we work": each step now has a small animated screen instead of 3D shapes - (1) a ledger of bills/stock/guests/dues being scanned, (2) code typing itself out, (3) a growth chart drawing upward. Size: `--vw` on `.viz`. They sit under the text on phones.
- NEW: "Automation stack" in the Automation & AI section - four floating layers (DATA, WORKFLOW, AI, APP) with a point of light travelling up through them. It sways gently so the labels stay readable. Size: `--plate` and `--gap` on `.stack3d`. Change the labels in the four `.plate` divs.
- Scroll animations: any element with class `reveal` fades up when it scrolls into view. Add `class="reveal"` to animate more things.
- Hover lifts on cards and reviews, nav-link underline slide, hero text fade-in.
- Visitors whose device is set to "reduce motion" get no spinning or sliding.
- Reviews: R Prasad and S Jaiswal are the two featured cards at the top. Their quotes are DRAFT wording - replace with their real words before promoting.

## Project pictures (new)
- Projects is now a card grid. Each card has a picture gallery (swipe, arrows or dots).
- 10 pictures live in the `images` folder (upload the whole folder to the repo root, next to index.html).
- Real screenshots: bill-tracker-1/2/3, expense-tracker-1/2/3 (sample data) and restaurant-inventory-intro (intro slide), restaurant-inventory-1/2 (your real app, vendor phone numbers blurred). Illustrations: work-together-1/2/3, invoice-reminder-1/2 (they say "Illustration" in the corner).
- Restaurant Inventory and Invoice Reminder are not linked on purpose (a client's live system and a private n8n login).
- Websites tour: three cards (Hotel Mahal, Hotel Red Velvet, Charitable Project). Their pictures (site-*.webp) are stand-in wireframes. Replace them with real screenshots of the sites (same file names, 1040 x 660) when you have them.
- Restaurant Inventory now uses 2 real screenshots (images/restaurant-inventory-1.webp and -2.webp). Work Together still has 3 illustrations - replace with real screenshots when you have them.

## Websites tour (new, 3D, curated)
- Hotel Mahal and Hotel Red Velvet each get a floating, tilted 3D browser window that glides through 6 hand-picked sections of the site (soft crossfade + slow zoom), with a section label and a progress bar. Click a bar segment to jump. It tilts toward the mouse and pauses on hover.
- Pictures are clean stills taken from your screen recordings (browser tabs and mouse cursor removed): images/tour-hotel-mahal-1..6.webp, images/tour-hotel-red-velvet-1..6.webp.
- Shyam Smriti Magazine is a small, quiet card with 2 pictures (images/tour-shyam-smriti-1..2.webp).
- No videos are needed. Upload the whole `images` folder (about 1 MB for the tour). If an old `videos` folder was uploaded earlier, you can delete it.
- Note: on the live Hotel Mahal hero, the word "celebrate" and the small "Chinsurah, West Bengal" line are very dark on the dark photo - worth checking the colour on the live site.
