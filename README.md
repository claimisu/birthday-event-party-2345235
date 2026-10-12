# Birthday Night — invitation site

No build step. Open `index.html` in a browser (or run `python3 -m http.server` in this folder and visit localhost:8000).

## Edit
- **All text, date, time, venue, address, colours, motion:** `js/siteConfig.js` (one file, commented).
- **Photos:** `images/`. Replace a file with the same name, or change the path in `siteConfig.js` (`images` and `gallery`). Gallery order = order of the list.
- **Date/time:** `event.dateISO` ("2026-12-12") and `event.startTime` ("20:00"). The calendar button works as soon as both are set.
- **Maps button:** paste a share link into `event.mapsUrl`, or just fill venue + address.
- **Turn sections off:** `sections: { gallery: false }`.
- **Calmer/stronger motion:** `motion.intensity` (0.5–1.5) or `motion.enabled: false`.

## RSVP (honest options)
1. Nothing set: works visually, tells the guest it is preview mode (nothing saved).
2. `rsvp.email`: opens the guest's mail app with the answer pre-filled.
3. `rsvp.endpoint`: real saving. Easiest = Google Form: create a form with 3 short-answer questions, open "Get pre-filled link" to read the `entry.XXXX` ids, put them in `fieldNames`, and use the form's `.../formResponse` URL as `endpoint` (keep `noCors: true`). Formspree/Basin/Getform URLs also work (set `noCors: false`).

## Publish
Drag this folder onto Netlify Drop (app.netlify.com/drop), Vercel, or GitHub Pages. You get a shareable URL.

## Better photos
The pool image was low-resolution, so crops are soft. Drop in full-size originals (JPG, ~2000px wide, under 400 KB each) with the same file names for a sharper result.

## Extra animations (v2)
All can be switched off one by one in `siteConfig.js` → `motion.effects`:
spotlight (lamp light follows the pointer), ballProgress (8-ball rolls along the bottom as you scroll), rackBreak (playable pool break — tap the table to shoot), scramble (date/venue decode), tickerVelocity (ticker reacts to scroll speed/direction), cardTilt, heroParallax, confetti (on "I'm in"). Hero/section titles also enter letter by letter.

## Countdown + VIP pass
Section near the end (countdown to `event.dateISO` + `event.startTime`, plus a ticket). Texts live in `siteConfig.js` → `ticket`. Turn off with `sections.ticket: false`. The square code on the ticket is decorative, not a real QR.

## Fonts
Headings: Archivo (condensed, heavy sans) via `--display` at the top of `css/style.css`; body: Jost; red pass page: Anton. To change one, edit the Google Fonts link in `index.html` and the `--display` / `--sans` variables. The handwritten "Let's play" uses `--script`.
