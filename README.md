# Puerto Vallarta 2026

Shareable trip page for **Tijuana → Puerto Vallarta, Sept 30 – Oct 5, 2026**.

Live link (once GitHub Pages is on): `https://<your-username>.github.io/puerto-vallarta-2026/`

## How it works

One self-contained file: `docs/index.html`. React and Babel load from a CDN, so there's
no build step and no `npm install`. Double-click the file to open it locally, or push it
and GitHub Pages serves it.

## Updating the trip

Everything renders from data constants at the top of `docs/index.html`, between the
`TRIP DATA` and `end of editable data` comments. Edit those, commit, push — the page
updates within a minute or two.

| Constant | What it controls |
|---|---|
| `TRIP` | Title, trip dates, and the countdown target |
| `FLIGHTS` | Both legs. Fill in `airline`, `flightNo`, `confirmation`, `seats` as you get them — blank fields show as dashed "TBD" pills |
| `STAYS` | Hotel/rental. Uncomment the example and fill it in; the address auto-links to Google Maps |
| `TRAVELERS` | Who's coming. Leave `[]` and the section hides itself |
| `DAYS` | Day-by-day plan. Add to any day's `items` array |
| `IDEAS` | Shortlist of restaurants and activities not yet committed |
| `PACKING` | Checklist groups |
| `KNOW_BEFORE` | The "Good to know" cards |

### Adding an itinerary item

```js
{ time: "7:30 PM", type: "food", title: "Dinner at ___", note: "Reservation under Diaz" }
```

`time` is optional — untimed items sort to the bottom of the day. `type` picks the icon:
`flight`, `food`, `beach`, `tour`, `drive`, `rest`, `event`.

## Notes

- **Times are local to each airport.** Puerto Vallarta is on CST (UTC−6) year-round since
  Mexico dropped daylight saving in 2022; Tijuana is on PDT (UTC−7) until Nov 1. PVR is
  1 hour ahead for this whole trip.
- **Packing checkboxes are per-device.** They're stored in `localStorage`, so the page is
  static and nothing syncs between people. Everyone gets their own list.
- **The repo has to be public** for GitHub Pages to serve it on a free account. Don't put
  anything in here you wouldn't want findable — full confirmation numbers and phone
  numbers are worth thinking twice about.
