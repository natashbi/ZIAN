# Zian's Christening

An interactive, phone-first Hot Wheels christening invitation, styled as a die-cast toy package on a `#f7f6f0` page. Everything lives in `index.html`, with the photo and logo in `assets/`.

What guests can do:

- Tap **Start your engines** for a start-light countdown with engine sound and confetti
- Tap the car to rev it, or swipe it sideways to send it racing
- Tap Zian's photo to see it bigger
- See the ceremony and reception details, the Ninongs and Ninangs, and a live countdown to the ceremony
- Add the event to Google Calendar, or open directions to the church and the reception in Google Maps
- RSVP with one tap: type their name, set how many are coming, and tap **Coming!** or **Can't make it**

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
  messenger: "",             // the family's Messenger username (after facebook.com/ or m.me/)
  rsvpForm: { action: "", name: "", attending: "", guests: "", link: "" }   // see "Guest list" below
};
```

- `place` is what the invite shows (`\n` starts a new line); `map` is what Google Maps searches for.
- The weekday, calendar entry, directions, countdown and RSVP message are all worked out from these values.
- With `messenger` set, **Send on Messenger** opens the family's chat directly. Left empty, it opens the Messenger app and guests pick the chat.

The Ninongs and Ninangs are listed directly in the HTML, in the section with the heading "Ninongs & Ninangs".

## Guest list for the family (Google Form)

With a Google Form connected, a guest's one tap goes straight into the family's guest list: they get an email for every answer, and the Responses tab shows who's coming and how many. Without it, guests finish by sending their answer on Messenger.

1. Go to [forms.google.com](https://forms.google.com) and start a blank form, e.g. "Zian's Christening RSVP".
2. Add three questions, all **Short answer**: **Name**, **Attending**, **How many**.
3. In **Settings**, turn off anything that requires guests to sign in.
4. In the **Responses** tab, open the ⋮ menu and turn on **Get email notifications for new responses**. Tap **Link to Sheets** to get the list as a spreadsheet too.
5. Send the form's link to whoever maintains the invite; they fill in `PARTY.rsvpForm` (`action` is the form address ending in `/formResponse`, and each question's `entry.…` number comes from the form's "Get pre-filled link").
6. Send one test RSVP from the live link and check that it shows up under **Responses**.

Sending to the form works when the invite is on a normal website such as GitHub Pages; the claude.ai preview blocks it, so guests there finish on Messenger.

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
