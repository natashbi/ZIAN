# Zian's Christening

An interactive, phone-first Hot Wheels christening invitation, styled as a die-cast toy package on a `#f7f6f0` page. Everything lives in `index.html`, with the photo and logo in `assets/`.

What guests can do:

- Tap **Start your engines** for a start-light countdown with engine sound and confetti
- Tap the car to rev it, or swipe it sideways to send it racing
- Tap Zian's photo to see it bigger
- See the ceremony and reception details, the Ninongs and Ninangs, and a live countdown to the ceremony
- Add the event to Google Calendar, or open directions to the church and the reception in Google Maps
- RSVP: type their name, set how many are coming, tap **Coming!** or **Can't make it**, then **Copy message** and paste it to the family on Messenger

## Edit the event details

Open `index.html` and change the `PARTY` block near the top of the `<script>`:

```js
const PARTY = {
  name: "Zian",
  event: "Christening",
  // Times include the UTC offset: +08:00 is Philippine time
  ceremony: {
    start: "2026-11-07T10:00:00+08:00",
    place: "St. Vincent Ferrer Parish\nBrgy. San Vicente, Zaragoza, Nueva Ecija",
    map: "St. Vincent Ferrer Parish, Zaragoza, Nueva Ecija"
  },
  reception: {
    start: "2026-11-07T12:00:00+08:00",
    end: "",                 // optional; without it only the start time shows
    place: "Lety's Place Private Pool and Event Center\nPurok 2, Brgy. Sto. Rosario Young, Zaragoza, Nueva Ecija\nAt the back of GM Blu Carwash",
    map: "Lety's Place Private Pool and Event Center, Zaragoza, Nueva Ecija"
  }
};
```

- `place` is what the invite shows (`\n` starts a new line); `map` is what Google Maps searches for.
- The weekday, calendar entry, directions, countdown and RSVP message are all worked out from these values.

The Ninongs and Ninangs are listed directly in the HTML, in the section with the heading "Ninongs & Ninangs".

## Personal links (optional)

The plain link shows no guest name, so the same link can go to everyone. To greet one person by name, add it to the end of the link (dashes become spaces). The card then shows "Special invite for" with that name, and the name is filled in on the RSVP:

- `https://<your-site>/#Ninong-Jerald` shows **Ninong Jerald**

## Photo and logo

- `assets/zian-photo.webp`: Zian's photo, shown inside the tire in the toy package. Use a square image with the face centered; a transparent background works best.
- `assets/zian-logo.webp`: the ZIAN flame logo at the top of the card.

Replace either file with one of the same name to change it. If a file is missing, the page shows the first letter of the name in the tire and the name as text instead of the logo.

## Put it online

1. In the repo on GitHub, open **Settings → Pages**.
2. Under "Build and deployment", pick **Deploy from a branch**, then choose the branch and the `/ (root)` folder.
3. GitHub gives you a link like `https://<user>.github.io/ZIAN/` to share.
