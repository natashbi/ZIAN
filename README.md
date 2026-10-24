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
- RSVP: type their name, set how many are coming, and tap **Coming!** or **Can't make it**. With the family's Google Form set up, that's it: the answer goes straight into the guest list (see "Guest list" below). Without it, guests finish on Messenger: **Send on Messenger** opens the family's chat with the message copied (when `messenger` is set), or **Copy message** lets them paste it to the family

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
  messenger: "",             // the family's username from their Facebook profile link
  rsvpForm: { action: "", name: "", attending: "", guests: "" }   // see "Guest list" below
};
```

- `place` is what the invite shows (`\n` starts a new line); `map` is what Google Maps searches for.
- `messenger` is the part after `facebook.com/` in the family's profile link. RSVPs then open that chat with an `m.me` link, which phones hand to the Messenger app on Android and iPhone. Messenger doesn't let a website type or send a message, so the guest pastes the copied message and taps Send.
- The weekday, calendar entry, directions, countdown and RSVP message are all worked out from these values.

The Ninongs and Ninangs are listed directly in the HTML, in the section with the heading "Ninongs & Ninangs". The dress code is in the HTML too, in the section with the heading "Dress code".

## Guest list (Google Form)

With a Google Form connected, a guest's tap on **Coming!** or **Can't make it** goes straight into the family's guest list: no copying, pasting or Messenger. The family sees every answer in the form's **Responses** tab (and can get an email for each one).

1. Go to [forms.google.com](https://forms.google.com) and start a **Blank form**, e.g. "Zian's Christening RSVP".
2. Add three questions, all **Short answer**: **Name**, **Attending**, **How many**.
3. Leave **Collect email addresses** and **Limit to 1 response** off in **Settings**, so guests don't have to sign in.
4. Open the ⋮ menu, choose **Get pre-filled link**, type anything in the three answers, tap **Get link**, then **Copy link**.
5. From that link, fill in `PARTY.rsvpForm`: `action` is the form address with `viewform…` replaced by `formResponse`, and `name`, `attending` and `guests` are the `entry.…` numbers of the three questions, in order.
6. In the **Responses** tab, turn on **Get email notifications for new responses** in the ⋮ menu, and tap **Link to Sheets** for a spreadsheet of who's coming.
7. Send one test RSVP from the live link, check that it shows up under **Responses**, then delete it.

Each answer arrives as Name, Attending ("Coming" or "Can't make it") and How many (0 for Can't make it). A guest who changes their answer sends a new one; the latest counts. If a guest's phone can't reach Google, the invite offers **Try again** and the Messenger way as a backup.

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

- `assets/zian-face.webp`: Zian's face, shown inside the tire in the toy package and in the photo pop-up. Use a square image with the face centered.
- `assets/zian-logo.webp`: the ZIAN flame logo at the top of the card and on the opening screen.
- `assets/zian-race-1.webp` and `assets/zian-race-2.webp`: the race-day photos. The first one is also on the opening screen. Both are landscape (3:2).

To change a picture, save the new one under a new file name and change that name in `index.html`. Phones keep a saved copy of each picture for a while, so a new picture under an old name can keep showing the old one. If a file is missing, the page shows the first letter of the name in the tire and the name as text instead of the logo.

## Put it online

1. In the repo on GitHub, open **Settings → Pages**.
2. Under "Build and deployment", pick **Deploy from a branch**, then choose the branch and the `/ (root)` folder.
3. GitHub gives you a link like `https://<user>.github.io/ZIAN/` to share.
