# Zian's Christening

An interactive, phone-first Hot Wheels christening invitation, styled as a die-cast toy package on a `#f7f6f0` page. Everything lives in `index.html`, with the photo and logo in `assets/`.

What guests can do:

- Open the invite: it starts on a sealed toy package with Zian's photo. **Tap to open** runs the start lights and engine sound, then the package rolls up and the invite drives in
- Tap **Start your engines** for a start-light countdown with engine sound and confetti
- Tap the car to rev it, or swipe it sideways to send it racing
- Tap Zian's photo to see it bigger
- Tap the **Photo finish** stack to shuffle through the race-day photos
- See the ceremony and reception details, the dress code (tap a shirt to spin it), the Ninongs and Ninangs, and a live countdown to the ceremony
- Swipe through **Lap by lap**, Zian's first 12 months, while a little car drives along the track to the checkered flag
- Add the event to Google Calendar, or open directions to the church and the reception in Google Maps
- RSVP: type their name, set how many are coming, tap **Coming!** or **Can't make it**, then **Send on Messenger**: the family's chat opens in the Messenger app with the message already copied, so they paste it and tap Send. Without a Messenger username set, the button is **Copy message** and they paste it to the family themselves

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
  },
  messenger: ""              // the family's username from their Facebook profile link
};
```

- `place` is what the invite shows (`\n` starts a new line); `map` is what Google Maps searches for.
- `messenger` is the part after `facebook.com/` in the family's profile link. RSVPs then open that chat with an `m.me` link, which phones hand to the Messenger app on Android and iPhone. Messenger doesn't let a website type or send a message, so the guest pastes the copied message and taps Send.
- The weekday, calendar entry, directions, countdown and RSVP message are all worked out from these values.

The Ninongs and Ninangs are listed directly in the HTML, in the section with the heading "Ninongs & Ninangs". The dress code is in the HTML too, in the section with the heading "Dress code".

## Monthly milestones

The **Lap by lap** cards come from the `MILESTONES` list just below `PARTY`, one line per month from the 1st to the 12th. Each card shows Zian's monthly photo (`assets/month-1.webp` to `assets/month-12.webp`) with a short line about it.

```js
{ text: "A 2nd-month cake from Kuya", photo: "assets/month-2.webp" },
```

- `text` is the line under the card.
- `photo` is the picture in `assets/`. The cards are portrait (4:5), so crop a new photo to that shape with Zian in frame. With `""` (or if the file is missing) the card shows the month number in a tire instead.

## The link to send

Send guests **https://natashbi.github.io/ZIAN/youre-invited/**. In Messenger and on Facebook it shows a "You're invited to Zian's Christening!" preview with Zian's photo (`assets/share.jpg`), then opens the invite. The plain `https://natashbi.github.io/ZIAN/` link still works and shows the same preview.

The preview's words are in the `og:` lines at the top of both `index.html` and `youre-invited/index.html`; if the date changes, change both and remake `assets/share.jpg` (1200 × 630). Messenger keeps a copy of a link's preview for a while, so a change can take time to show on links already sent.

## Personal links (optional)

The plain link shows no guest name, so the same link can go to everyone. To greet one person by name, add it to the end of the link (dashes become spaces). The card and the opening screen then show "Special invite for" with that name, and the name is filled in on the RSVP:

- `https://natashbi.github.io/ZIAN/youre-invited/#Ninong-Jerald` shows **Ninong Jerald**

## Photo and logo

- `assets/zian-photo.webp`: Zian's photo, shown inside the tire in the toy package. Use a square image with the face centered; a transparent background works best.
- `assets/zian-logo.webp`: the ZIAN flame logo at the top of the card and on the opening screen.
- `assets/zian-race-1.webp` and `assets/zian-race-2.webp`: the race-day photos. The first one is also on the opening screen. Both are landscape (3:2).

Replace either file with one of the same name to change it. If a file is missing, the page shows the first letter of the name in the tire and the name as text instead of the logo.

## Put it online

1. In the repo on GitHub, open **Settings → Pages**.
2. Under "Build and deployment", pick **Deploy from a branch**, then choose the branch and the `/ (root)` folder.
3. GitHub gives you a link like `https://<user>.github.io/ZIAN/` to share.
