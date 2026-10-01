# 📅 Crow Calendar Card

A calendar card for [Home Assistant](https://www.home-assistant.io/) that brings all your calendars together in one place. Each calendar has its own colour, and you can view them as an Agenda list, Day Columns or a Month grid. Events show countdowns, a live progress bar while they're on, clash badges when they overlap, and join buttons for online meetings. Tap an event to see its details, edit it, or delete it. You can add new events, search, and export to PDF, a calendar file, a spreadsheet or JSON. Choose the Classic solid look or a liquid-glass look in light or dark. Optional AI features add a summary of your day, questions about your calendars, typed quick-add, spoken rundowns and tips for each event. Everything can be set up without writing any YAML.

> ✨ **AI features are optional.** Nothing AI-powered runs until you turn on AI features and choose a conversation agent in the editor (see [AI Features Setup](#-ai-features-setup-optional) below). Without an agent, the card works fully as a calendar card, and **Plain answers** gives you most of the same tools worked out from your calendar alone.

---

## ✨ Features

### Views
- **Agenda**: a list, day by day, with the date down the side and today in a coloured circle.
- **Day Columns**: a column for each day, side by side, which you can scroll sideways.
- **Month**: a calendar grid with coloured dots under busy days. Tap a day to see its events, and use ‹ › and **Today** to move between months.
- **Look ahead** from 1 to 28 days, with optional week labels, quiet days and today's earlier events.
- **‹ › buttons** to look at the days before or after, with **Today** to come back (Agenda and Day Columns).
- **Search box** (optional) under the header: type to find events from the last month to six months ahead, shown right on the card.

### Events
- **Several calendars**, each with its own colour bar and an optional short label in front of its event names.
- **Times** in 12-hour, 24-hour or your Home Assistant setting, with or without the finish time.
- **Starts-in badge**, such as "in 25m", and a **Now** badge with a live progress bar while an event is on.
- **Clash badges** on events that overlap, even when they're in different calendars. Tap one to see how they overlap.
- **Online meetings**: a green **Join** button for meeting links, with the meeting ID and passcode shown separately with copy buttons.
- **Place and notes** on the card.
- **Remove duplicates** when the same event is in more than one calendar.
- **Show first** keeps the card short, with a "12 more events" button for the rest.

### Event details
Tap an event to open its details, or set it to open a link instead, such as the iPhone Calendar app, Google Calendar or Outlook on that day:
- The date, time and length, and whether it's coming up, on now or finished.
- **Join online meeting**, the meeting ID and passcode, and a **Directions** button for the address.
- Notes with tappable links, phone numbers and email addresses.
- **Show only this calendar**, which filters the card to that calendar until you clear it.
- **Edit** to change the title, place, times, meeting details and notes, or delete the event. Repeating events can be changed for one event or all future events.
- **Duplicate** copies the event into a New Event form, ready to change the date and save.

### Adding events
- The **+** button opens a **New Event** form for any of your calendars that accept new events.
- The **Location** box suggests your Home Assistant zones and places you've used before.

### Menu
Tap **•••** in the header, or press and hold the card:
- **Search** finds any event by its name, place or notes, from the last month to six months ahead.
- **Week ahead** shows the next 7 days at a glance: how many events, hours booked, the busiest and quietest days, time booked per calendar and any clashes.
- **Find a free slot** lists your free times this week or next, between 8:00 and 21:00, for 30 minutes to 3 hours. Tap one to add an event there.
- **Export** saves or shares the days on the card, or the next 30 or 90 days, as:
  - a **PDF** agenda, with a preview first
  - a **calendar file (.ics)** that opens in any calendar app
  - a **spreadsheet (.csv)** for Excel or Numbers
  - **data (.json)** for backups or other tools

### Forecast
- A weather icon and the day's high temperature under each date in the Agenda and Day Columns views, from any Home Assistant weather entity.

### Appearance
- **Style**:
  - **Classic** is a plain solid card.
  - **Glass** is a frosted, see-through surface with blur and soft highlights.
- **Event panels**: show each event in its own rounded panel, or turn them off for a simpler list with just the colour bar.
- **Theme**: Auto (follows Home Assistant), Light or Dark.
- **Glass** slider, from clear to frosted.
- **Text size**: Standard, or Larger for wall tablets.
- **Height**: grow to fit your events, or fill its spot on the dashboard and scroll inside.
- **Colour scheme** presets, or your own colours for today's date, the Now badge and weekends.
- Respects **Reduce Motion** on your device.

### AI features (optional)
You need a Home Assistant conversation agent for these:
- **Your day**: a short "Rest of today" note in today's row, saying what's still to come or when your next event is. Off by default.
- **Ask**: ask a question about your calendars, such as "When am I free this week?", or tap a suggestion. It understands the people in your Home Assistant, so "What has Alex got this week?" lists just their events, and each person gets a suggestion of their own.
- **Week summary**: a short written summary at the bottom of Week ahead.
- **Quick add**: type something like "Dentist next Tuesday at 3", or paste a whole booking email or invitation. The title, time, place, reference numbers and online meeting details are filled in for you. You check it before it's saved, or open it in the full form first.
- **Announce**: a spoken rundown of today or tomorrow, played on the speakers you tick. Speakers are grouped by area, and unavailable speakers and TVs are hidden. It uses Home Assistant's text-to-speech and also works with Music Assistant speakers.
- **About this event**: a button in an upcoming event's details, with tips on what to bring or prepare and a warning if the time around it is tight.
- **Fix a clash**: tap a Clash badge for ideas on sorting it out, and a suggested new time that's checked to be free. Tap **Move it** to move the event there.

Each feature has its own toggle in the editor. Your calendar events are only sent to the agent when you use a feature, apart from Your day, which updates at most once an hour while it's on. Event text is treated as data, never as instructions, and everything is escaped before it's shown.

If the AI can't answer, every feature shows a plain answer worked out from your calendar instead, with a **Try again** button.

**Plain answers without AI**: with AI off, you can still switch on Your day, Ask (the suggested questions), Week summary and Announce, with answers worked out from your calendar alone. Nothing is sent anywhere.

---

## Configuration

Add the card from the card picker, then choose your calendars, view and style in the built-in visual editor. You don't need to write any YAML. The README lists every YAML option.

---

## 🤖 AI Features Setup (Optional)

AI features stay off until you turn them on and choose a conversation agent. **Google Gemini** is the recommended and best-tested agent:

### Step 1 — Enable the Generative Language API

1. Go to [console.cloud.google.com](https://console.cloud.google.com) and sign in
2. Create a new project (or select an existing one)
3. Go to **APIs & Services → Library**
4. Search for **Generative Language API** and click **Enable**

> ⚠️ Don't skip this step. An API key won't work until the Generative Language API is enabled; it will return errors straight away.

### Step 2 — Create an API Key

1. In Google Cloud Console go to **APIs & Services → Credentials**
2. Click **+ Create Credentials → API key** and copy the key

### Step 3 — Add Google Generative AI to Home Assistant

1. In Home Assistant go to **Settings → Devices & Services → + Add Integration**
2. Search for **Google Generative AI** and select it
3. Paste your API key and click Submit
4. The recommended model settings work fine. If you choose a model yourself, pick a **current Flash model**, because Google retires older models regularly.

### Step 4 — Configure the Card

In the card's visual editor, open **AI Features**, turn on **Enable AI features**, and choose your Google AI agent under **Conversation agent**. Then switch on the features you want.

### Rate limits

Free-tier limits vary by model and change over time, so check Google AI Studio for your current quota. The card caches every answer: Your day updates at most once an hour, and everything else only runs when you open it. You're unlikely to reach the limit in normal use. If you do see a quota message, it resets the next day.

If the agent can't answer, the card retries once automatically, then shows a plain answer worked out from your calendar, the reason in plain English and a **Try again** button.

---

## 🌐 Where the Data Comes From

- **Events** come from your Home Assistant `calendar` entities, such as Local Calendar, Google Calendar or CalDAV.
- **Adding, editing and deleting** use Home Assistant's own calendar services, so they work with calendars that allow it. Calendars that can add and delete but not edit are edited by saving a new copy and removing the original. Read-only calendars show their events but can't be changed.
- **The forecast** comes from your Home Assistant weather entity.
- **Location suggestions** come from your Home Assistant zones and the places in your own events. Nothing is looked up online.
- **Directions** open the address in Apple Maps.
- **PDF export** loads the jsPDF library from cdnjs.cloudflare.com the first time you make a PDF. The other export formats are made on your device.
