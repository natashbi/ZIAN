# Zian's Christening

An interactive, phone-first Hot Wheels christening invitation, styled as a die-cast toy package on a `#f7f6f0` page. Everything lives in `index.html`, with the photo and logo in `assets/`.

What guests can do:

- Tap **Start your engines** for a start-light countdown with engine sound and confetti
- Tap the car to rev it, or swipe it sideways to send it racing
- Tap Zian's photo to see it bigger
- See the ceremony and reception details, the Ninongs and Ninangs, and a live countdown to the ceremony
- Add the event to Google Calendar or open directions to the church and the reception in Google Maps
- RSVP, then send the answer to the host with one tap on Viber, WhatsApp, Messenger or text message. The message is already written, so guests only press send (for Messenger they paste it, since Messenger can't pre-fill messages).

## Edit the event details

Open `index.html` and change the `PARTY` block near the top of the `<script>`:

```js
const PARTY = {
  name: "Zian",
  event: "Christening",
  // Times include the UTC offset: +08:00 is Philippine time
  ceremony:  { start: "2026-11-07T10:00:00+08:00", place: "", map: "" },
  reception: {
    start: "2026-11-07T12:00:00+08:00",
    end: "",                            // optional; without it only the start time shows
    place: "Lety's Place Private Pool and Event Center\nPurok 2, Brgy. Sto. Rosario Young, Zaragoza, Nueva Ecija\nAt the back of GM Blu Carwash",
    map: "Lety's Place Private Pool and Event Center, Zaragoza, Nueva Ecija"
  },
  host: "Amy",
  phone: "123.123.1234",                // shown on the invite and used for text messages
  whatsapp: "11231231234",              // country code + number, digits only; "" hides the button
  viber: "+11231231234",                // number with country code; "" hides the button
  messenger: ""                         // Messenger username (m.me/username); "" hides the button
};
```

The weekday, the times, the calendar link, the directions, the countdown and the RSVP message are all worked out from these values. `place` is what the invite shows (`\n` starts a new line); `map` is what Google Maps searches for. An empty church `place` shows "Church details to follow" and hides the church directions button. If the reception is at the church, the second directions button hides itself.

The Ninongs and Ninangs are listed directly in the HTML, in the section with the heading "Ninongs & Ninangs".

## Automatic RSVP (Google Form)

With a Google Form connected, guests only tap **Submit**: their answer goes straight to the form, you get an email for each one, and all answers collect in one list. Without it, guests get the one-tap Viber / WhatsApp / Messenger / text buttons instead.

1. Go to [forms.google.com](https://forms.google.com) and start a blank form.
2. Add these questions, all as **Short answer**: Name, Attending, Kids, Adults, Message, Invite link.
3. In **Settings**, turn off anything that requires guests to sign in or collect email addresses.
4. In the **Responses** tab, open the ⋮ menu and turn on **Get email notifications for new responses**. You can also link the responses to a Google Sheet.
5. Fill in `PARTY.rsvpForm` in `index.html`: `action` is the form address ending in `/formResponse`, and each question needs its `entry.…` number (shown in the form's "Get pre-filled link" URL).
6. Before sharing, send one test RSVP from the live link and check that it appears under **Responses**. The page can't see Google's reply, so a form that needs sign-in or has the wrong entry numbers would drop answers quietly. After "Sent!", guests can still tap "Send it on Viber or WhatsApp too" as a backup.

Automatic sending works when the invite is on a normal website such as GitHub Pages. The claude.ai preview link blocks pages from sending data out, so there the send buttons appear instead.

## Personal links (optional)

The plain link shows no guest name, so the same link can go to everyone. To greet one person by name, add it to the end of the link (dashes become spaces) and the card shows "Special invite for" with that name:

- `https://<your-site>/#Ninong-Jerald` shows **Ninong Jerald**
- `https://<your-site>/?to=Maya%20and%20family` shows **Maya and family**

## Photo and logo

- `assets/zian-photo.webp`: Zian's photo, shown inside the tire in the toy package. Use a square image with the face centered; a transparent background works best.
- `assets/zian-logo.webp`: the ZIAN flame logo at the top of the card.

Replace either file with one of the same name to change it. If a file is missing, the page shows the first letter of the name in the tire and the name as text instead of the logo.

## Put it online

1. In the repo on GitHub, open **Settings → Pages**.
2. Under "Build and deployment", pick **Deploy from a branch**, then choose the branch and the `/ (root)` folder.
3. GitHub gives you a link like `https://<user>.github.io/ZIAN/` to share.
