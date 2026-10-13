# Zian's Birthday Race

An interactive, phone-first Hot Wheels birthday invitation. Everything lives in one file: `index.html`.

What guests can do:

- See their own name on the card ("Special invite for …")
- Tap **Start your engines** for a 3-2-1-GO start-light countdown with engine sound and confetti, or tap the car to rev it
- Watch a live countdown to the party
- Add the party to Google Calendar or open directions in Google Maps
- RSVP (number of kids and grown-ups, plus a message for the birthday kid). This builds a ready-made message to send to the host on WhatsApp or by text, or to copy.

## Edit the party details

Open `index.html` and change the `PARTY` block near the top of the `<script>`:

```js
const PARTY = {
  name: "Zian",
  age: 3,
  start: "2026-12-24T14:00:00-05:00",   // date, start time, venue UTC offset
  end:   "2026-12-24T16:00:00-05:00",
  place: "1234 Name Street, Miami FL 5678",
  host: "Amy",
  phone: "123.123.1234",
  whatsapp: "11231231234",              // country code + number, digits only; "" hides the button
  guestPlaceholder: "Guest Name"
};
```

The weekday, the times, the calendar link, the countdown and the RSVP message are all worked out from these values.

## Photo and logo

- `assets/zian-photo.webp`: the birthday kid's photo, shown inside the tire frame. Use a square image with the face centered; a transparent background works best.
- `assets/zian-logo.webp`: the ZIAN flame logo used as the title.

Replace either file with one of the same name to change it. If a file is missing, the page shows the first letter of the name in the tire and the name as text instead of the logo.

## Colors

The page uses one calm palette: paper `#f7f6f0` as the main color, warm ink for text, and the logo's red and yellow as small accents. The colors are defined once at the top of the `<style>` block.

## Personal link for each guest

Add the guest's name to the end of the link. Dashes become spaces:

- `https://<your-site>/#Maya-and-family` shows **Maya and family**
- `https://<your-site>/?to=Maya%20and%20family` does the same

With no name in the link, the card shows the `guestPlaceholder` text.

## Put it online

1. In the repo on GitHub, open **Settings → Pages**.
2. Under "Build and deployment", pick **Deploy from a branch**, then choose the branch and the `/ (root)` folder.
3. GitHub gives you a link like `https://<user>.github.io/ZIAN/` to share.
