# Adventure Escape SA

A working front-end prototype of the Adventure Escape SA website, built from the group's
wireframes (Home, About Us, Overview, Package Detail, Fees, Contact Us).

Plain HTML, CSS and JavaScript — no build step, no framework, no backend. Open
`index.html` in a browser and it runs.

---

## Group

**Task 1, Phase 2/3 — Chosen scenario: Adventure Escape SA**

| Name              | Student Number | Role                          |
|-------------------|-----------------|-------------------------------|
| Rayan Bvulani      | ST10497168      | Team leader                   |
| Itumeleng Ndlovu   | ST10515918      | Team secretary                 |
| Asukia Ebuta       | ST10531063      | Member / designer & researcher |

---

## Running it

No installation needed.

1. Unzip the folder.
2. Double-click `index.html` (or right-click → Open with → your browser).

That's it — the whole app runs client-side straight off disk.

**To view it on a phone, tablet emulator, or a real device on the same network**, serve
the folder instead of opening the file directly:

```bash
cd AdventureEscapeSA-app
python3 -m http.server 8000
```

Then visit:
- `http://localhost:8000` on the same computer
- `http://10.0.2.2:8000` from an Android Studio emulator
- `http://<your-computer's-local-IP>:8000` from a phone on the same Wi-Fi

---

## What's in the box

```
index.html        the entire app — markup, styles and script in one file
images/            the 10 illustrations the app uses
  hero.jpg                       Home page banner
  about-cliff.jpg                About Us — founder photo
  about-group.jpg                About Us — mission photo
  corporate-team-challenge.jpg   package card + detail photo
  mountain-adventure.jpg         package card + detail photo
  ultimate-adventure-day.jpg     package card + detail photo
  family-explorer.jpg            package card + detail photo
  ziplining-adventure.jpg        activity card + detail photo
  kayaking-experience.jpg        activity card + detail photo
  rock-climbing-session.jpg      activity card + detail photo
```

`index.html` references every image by a relative path (`images/...`), so the two must
stay in the same folder together — if you move `index.html` elsewhere, bring the
`images` folder with it.

---

## Pages / screens

The app is a single page that swaps its content based on the URL hash (`#home`,
`#about`, `#overview`, `#package/<id>`, `#fees`, `#contact`), so the back/forward
buttons work and a page can be bookmarked or linked to directly.

| Screen | What it does |
|---|---|
| **Home** | Hero banner, "View Packages" / "Get Quote" buttons, 3 featured packages |
| **About Us** | Founder story and mission, matching the wireframe's two-column layout |
| **Overview** | All / Packages / Individual Activities filter tabs, full catalogue |
| **Package Detail** | Photo gallery (click thumbnails), collapsible Description / What's Included / Meeting Point / Cancellation Policy, date picker, Book Now, Add to Quote |
| **Fees** | Add/remove any package or activity; subtotal, discount tier and total recalculate live |
| **Contact Us** | Name / email / phone / package / message form with validation and a sent confirmation |

### Discount rule (Fees page)
Matches the wireframe exactly:
- 1 booking → no discount
- 2 bookings → 5%
- 3 bookings → 10%
- more than 3 → 15%

---

## Notes on the data

- All activity names, prices, durations and descriptions are written to match the
  original wireframes and are easy to find and edit — they live in the `ACTIVITIES`
  array near the top of the `<script>` block in `index.html`.
- "Add to Quote" and the Fees page share state via the browser's `localStorage`, so a
  quote survives a page refresh on the same device/browser. It does **not** sync
  between devices or get sent anywhere — there's no backend.
- The Contact form and the booking/quote buttons show an on-screen confirmation but
  don't actually send an email or make a booking. Wiring that up would need a backend
  (e.g. a form-handling service or a small server) — ask if you'd like help adding one
  for the final submission.
- The images are generated illustrations (gradient skies, silhouette landscapes, and
  small figures doing each activity) rather than real photography, since this is a
  student prototype. They're easy to swap for real photos later: just replace the
  matching file in `images/` with another image of the same name.

---

## Customising

- **Colours** — defined once as CSS variables at the top of the `<style>` block
  (`--forest`, `--canyon`, `--sand`, etc.), so the whole palette can be changed from
  one place.
- **Fonts** — Fraunces (headings) and Inter (body text), loaded from Google Fonts.
- **Content** — package/activity details are in the `ACTIVITIES` array; nav links,
  footer text and the Contact page's business info are plain HTML in the relevant
  `screen...()` function.

---

## Known limitations

- No backend — nothing is actually booked, paid for, or emailed.
- No login/accounts.
- Images are illustrated placeholders, not real location photography.
- Not a native mobile app (no `.apk`/`.ipa`) — it's a responsive website that works in
  any mobile browser, including inside an emulator's browser.
