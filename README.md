# Puerto Vallarta 2026

Shareable trip page for **Tijuana → Puerto Vallarta, Sept 30 – Oct 5, 2026**.

Live: **https://justinediaz099-dotcom.github.io/puerto-vallarta-2026/**

Two tabs: **Overview** (countdown, flights, hotel) and **Itinerary** (day by day).

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
| `STAYS` | Hotel(s), shown in the Overview's Hotel section. The address auto-links to Google Maps. Set `flag` to a string to surface an open question on the card, `null` to hide it |
| `TRAVELERS` | Who's coming. Leave `[]` and the section hides itself |
| `DAYS` | Day-by-day plan. Add to any day's `items` array |

### Adding an itinerary item

```js
{
  time: "7:30 PM", type: "food",
  title: "Dinner at ___",
  note: "How to get there, or anything worth knowing.",
  address: "Full address",              // renders a 📍 Map link
  phone: "322 000 0000",                // renders a 📞 tap-to-call link
  phoneDial: "+523220000000",           // what the call link actually dials
  confirmation: "OpenTable #12345",
}
```

Only `title` is required. `time` is optional — untimed items sort to the bottom of the day.
`type` picks the icon: `flight`, `food`, `beach`, `tour`, `hotel`, `drive`, `rest`, `event`.

## The background photo

`docs/img/sunset-1280.jpg` (desktop) and `docs/img/sunset-900.jpg` (phones) are the same
Puerto Vallarta sunset, self-hosted so nothing breaks if an external site goes down. It's
[this photo](https://commons.wikimedia.org/wiki/File:Puerto_Vallarta,_Mexico_-_March_2023_-_015.jpg)
by **Another Believer**, licensed **CC BY-SA 4.0** — that license requires the credit to
stay visible, which is why it appears in the corner of the header and in the footer.

To swap the image: drop replacements at the same two paths and update the `PHOTO` constant
with the new author and license. The framing is controlled by `background-position` on
`.hero` (currently `center 22%`, which keeps the sun in frame at any hero height).

## Notes

- **Times are local to each airport.** Puerto Vallarta is on CST (UTC−6) year-round since
  Mexico dropped daylight saving in 2022; Tijuana is on PDT (UTC−7) until Nov 1. PVR is
  1 hour ahead for this whole trip.
- **The repo is public**, which is what makes the free Pages link work. Everything here is
  findable, including the booking confirmation numbers — that's a deliberate choice.
