# Kidpedia: a shared family page for your child, built with Claude

Kidpedia is a single shared page that parents and caregivers open from their phones to check, ask about and update everything about a child: allergies, medicine, contacts, sizes, routines, appointments and to-dos. Every morning it can also suggest what the child should wear, based on the local weather forecast.

You don't write any code. You paste the prompts below into a chat with Claude, and Claude builds and publishes the page for you.

## What you get

- **Ask box:** type a question like "Shoe size?" or "When is the next dentist visit?" and get a short answer from your saved information.
- **Add or update box:** write like a text message, e.g. "Dentist Tue 21 Oct 10:00, bring the vaccination card, shoe size now 23". Claude sorts it into info, events and to-dos, and shows a preview before saving.
- **Must know:** age (calculated automatically), allergies, medicine, height and weight at the top.
- **To-do, Upcoming and Info tabs:** shared to-do list, upcoming events with a one-tap "Add to Google Calendar" link, and all saved info grouped into sections.
- **History:** when you change something, the old version is kept, so you can ask "What was the shoe size a month ago?". Removed entries can be restored.
- **Live sync:** everyone with access sees the same data, along with who added or changed what.
- **Today's outfit (optional):** a daily card with the weather and a clothing list based on your own clothing rules and the clothes your child actually has.

## What you need

- A Claude account for each person who edits or reads the page (a free account is enough to view).
- Claude features used: published artifacts with shared storage and built-in AI, plus scheduled tasks for the daily outfit. Availability can depend on your Claude plan.

## How to use it

1. Open a new chat in Claude.
2. Copy **Prompt 1**, replace everything in `[BRACKETS]`, and send it. Claude builds and publishes the page.
3. Optional: send **Prompt 2** in the same chat to add a clothing guide, then **Prompt 3** for the daily outfit card.
4. Share the page and add it to your phone (see "After setup").

---

## Prompt 1: Build the page

```text
Build me a shared, mobile-first web page (a published Claude artifact) called "[CHILD NAME]pedia". It is where parents and caregivers keep, look up and update information about our child [CHILD NAME], born [YYYY-MM-DD]. We live in [CITY, COUNTRY]. Each parent uses their own Claude account, mostly on a phone. It must look good in light and dark mode.

DATA AND ACCESS
- Store everything in the artifact's shared database (not browser storage), so everyone with access sees the same live data on every device.
- Use the viewer's identity to show who added or changed each item.
- People with edit access can change things; people with view access (e.g. grandparents) can read and ask questions but see no editing controls.
- Use Claude's built-in AI from the page for the Ask and Add/update features.

LAYOUT, TOP TO BOTTOM
1. Header with the page name.

2. One input box with a toggle: "Ask" and "Add or update". No suggested-question chips.
   - Ask: typing filters and highlights matching entries instantly without AI. The Ask button sends the saved info (including earlier versions), upcoming events, open to-dos and today's outfit to Claude, and shows a 1-4 sentence answer in the same language as the question. Answers must use only saved information and say when something isn't recorded yet.
   - Add or update: the user writes naturally, in any language, with several things in one message. Claude turns it into:
     * info entries (update an existing entry on the same topic instead of adding a duplicate),
     * events (resolve relative dates like "next Tuesday" against today),
     * to-dos (things to buy, pay, bring, book, sign; optional due date).
     Show a preview of all changes, with a remove button on each, and only save when the user confirms.

3. "Today's outfit" card, shown only when a daily outfit has been saved (see the scheduled task below): a weather line, the clothes as a bullet list labeled Inner / Middle / Outer / Head / Neck / Hands / Feet, an optional "Sandbox" line and an optional "Later" line. If the saved outfit isn't for today, say so.

4. "Must know" box: first the child's age, calculated automatically from the birth date (e.g. "1 year, 2 months"), then all entries marked important (allergies, medicine, health conditions, height and weight).

5. Three tabs, in this order, opening on To-do:
   - To-do: quick add with an optional due date (empty is fine). Tick to mark done, showing who did it and when. Overdue items in red. Items with a due date first. Done items behind a "Show done" toggle.
   - Upcoming: events in date order with a date tile, title, time (or "All day") and notes. Each event has an "Add to Google Calendar" link that opens Google Calendar's new-event page pre-filled (calendar.google.com/calendar/render?action=TEMPLATE with title, dates and time zone), plus an "In calendar" checkbox. Events can be edited and deleted. Past events behind a toggle.
   - Info: entries grouped into sections: Health & allergies, Medication, Contacts, School & activities, Routines & food, Sizes & clothes, Other. Tap an entry to edit it; each section has "+ Add".

6. Footer: a small "Edit children" control for the children's names.

HISTORY: NEVER LOSE OLD INFORMATION
- When an entry changes, keep the previous version with the dates it was valid (from/to) and who changed it. Show these under "Earlier versions" on the entry.
- The AI uses this history to answer questions about the past, e.g. "What was the shoe size a month ago?".
- "Remove" moves an entry to a "Removed" list at the bottom of Info with a Restore button; nothing is permanently deleted.

HEIGHT AND WEIGHT
- Keep exactly one important entry titled "Height and weight" with text like "Current height 77 cm, weight 9.7 kg, updated YYYY-MM-DD". When I add a new measurement, update that entry (keeping the old value in its history) instead of creating a new one.

AFTER PUBLISHING
- Save [CHILD NAME] as the child's name and [YYYY-MM-DD] as the birth date.
- Leave everything else empty; we will fill it in ourselves.
- Tell me how to share it with my partner so they can edit, and how to add it to my phone's home screen.
```

---

## Prompt 2 (optional): Clothing guide

Send this in the same chat. Replace the brackets with your child's real clothes and situation.

```text
Add a clothing guide to [CHILD NAME]pedia, saved as entries in "Sizes & clothes".

About my child: [AGE], [walking / not walking yet], mostly [in the stroller / walking around] outdoors. We live in [CITY] and are usually outdoors in [AREA]. Our home is [21-23]°C.

Clothes my child has: [e.g. thin waterproof overall, thick windproof winter overall, raincoat + rain pants, fleece overall, fleece jacket, cotton shirt + pants, wool inner layer, thin and thick hat, neck warmer, waterproof thick gloves, thin and thick socks, waterproof footcovers].

Create three entries:
1. "Clothes he/she has": the list above, grouped as Outer / Middle / Inner / Hats / Neck / Hands / Feet, plus anything missing for the coming season.
2. "What to wear by weather": an outfit for each temperature band (over 15°C, 10-15, 5-10, 0-5, -5 to 0, below -5, below -10), using only clothes from the list. Include these rules:
   - A child sitting still in a stroller needs one layer more than an adult. Check warmth on the neck or back, not the hands.
   - Windy or damp: dress as if it is 5°C colder. Rain, slush or wet ground: waterproof layer on top.
   - Inner layer: cotton above 5°C, wool at 5°C and below, and also wool for long outings, outdoor naps and wet, windy days.
   - [If not walking yet:] no shoes; socks (thin or thick by temperature) plus footcovers.
   - Active play: one layer less. Indoors: open the overall and take off the hat.
   - Add short local notes for [CITY]'s climate (typical winter, slush, wind near water).
3. "Sandbox play": the same bands for sitting in damp sand. A waterproof layer on the bottom always, no layer removed for sitting and digging, time limits when it's cold, and a dry check afterwards.
```

---

## Prompt 3 (optional): Daily outfit card

Send this in the same chat, after Prompt 2.

```text
Set up a scheduled task that runs every morning at [06:20] [TIME ZONE, e.g. Europe/Stockholm] and updates the "Today's outfit" card on [CHILD NAME]pedia:
1. Look up today's forecast for [CITY / NEIGHBOURHOOD] (e.g. yr.no or the national weather service): morning and afternoon temperature, "feels like", rain/snow and when, wind, and whether the ground is likely wet. Never guess the weather; if no forecast is found, say so.
2. Read the clothing guide, the sandbox guide and the list of clothes my child has from the page's saved data, and follow them strictly, using only clothes my child owns. [If not walking yet: never suggest shoes.]
3. Save today's outfit with: date, a one-line weather summary, the clothes as a list (Inner / Middle / Outer / Head / Neck / Hands / Feet, skipping what isn't needed), one or two sentences for sandbox play, and one sentence on what to change later in the day. No packing list.
Run it once now so I can see today's card.
```

---

## After setup

**Share with your partner (can edit)**
- Open the page, tap **Share**, invite the email they use for Claude, and set them as **Editor**.
- Don't also turn on a public link: while it's on, invited editors can't save changes.

**Grandparents or babysitters (read only)**
- They need a Claude account (free is fine). Invite them as **Viewer**.

**Add it to your phone**
- iPhone: open the page in Safari while signed in to claude.ai, then **Share → Add to Home Screen**.
- Custom icon with your child's photo: in the **Shortcuts** app, create a shortcut with the action **Open URLs** and paste the page link, then **Add to Home Screen** and choose a photo as the icon.

**Update it quickly**
- Use **Add or update** and the keyboard's microphone: "Shoe size now 23, dentist next Thursday 9:00, buy winter boots".
- You can also ask Claude in any chat to update the page by pasting its link.

**Change or extend it later**
- Continue the same chat, or paste the page link into a new chat, and describe what you want. Your saved data stays untouched when the page design changes.

## Privacy

- The page is private until you share it. Anyone you share it with can see everything on it.
- Don't store full personal identity numbers or passport numbers; note where documents are kept instead.
- Questions and updates are processed by Claude, and use the asking person's own Claude usage.
