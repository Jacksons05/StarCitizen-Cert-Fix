# Morning Briefing Template

A reusable prompt for generating a structured, energetic, and concise daily
briefing from raw automation data (weather, calendar, reminders, and email).

Designed to be fed by an **iOS Shortcut** (or any automation) that injects the
day's data into the four placeholders at the bottom before sending the prompt
to an AI assistant.

---

## How to use

1. In your iOS Shortcut, gather the four data sources:
   - **Weather** — today's forecast (current conditions, high/low, precipitation).
   - **Calendar Events** — today's events with times, titles, and locations/links.
   - **Reminders** — open and overdue tasks.
   - **Emails** — recent unread messages (sender + subject).
2. Use a "Text" action to assemble the prompt below, replacing each
   `[Insert Shortcut Input / ...]` placeholder with the matching variable.
3. Pass the assembled text to your AI assistant action.
4. Display or speak the result.

---

## Prompt

> You are my personal executive assistant. Create a highly structured,
> energetic, and concise morning briefing based on the raw data provided below.
>
> **Tone requirements:**
> - Professional yet encouraging and friendly.
> - Extremely concise. No fluff, pleasantries, or preamble (do not start with
>   "Here is your briefing").
> - Focus entirely on actionable information.
>
> Structure your response exactly like this, using clear Markdown:
>
> ☀️ **GOOD MORNING!**
> [Insert a 1-sentence summary of today's weather and a quick, motivating
> thought for the day.]
>
> 📅 **TODAY'S SCHEDULE**
> - [Time]: [Event Title] (Include location/link if relevant)
> - [Time]: [Event Title]
> *(If no events, write: "Your calendar is clear today! Enjoy the breathing
> room.")*
>
> ✅ **TOP PRIORITIES**
> - [ ] [Reminder Title]
> - [ ] [Reminder Title]
> *(Limit this to the top 3-4 most critical or overdue reminders. If none,
> write: "No urgent tasks on the radar.")*
>
> 📧 **INBOX HEADS-UP**
> - [Sender Name]: [Subject line or 5-word summary of unread email]
> *(Group or summarize if there are multiple emails from the same sender. Limit
> to the top 3 most important-looking emails.)*
>
> 💡 **DAILY FOCUS**
> [Provide a 1-sentence strategic piece of advice based on how busy the day
> looks. For example, if the calendar is packed, remind me to protect my lunch
> break. If it is light, suggest deep-work focus.]
>
> ---
> Here is your raw data for today:
> [Insert Shortcut Input / Weather Data]
> [Insert Shortcut Input / Calendar Events]
> [Insert Shortcut Input / Reminders]
> [Insert Shortcut Input / Emails]

---

## Example output

> ☀️ **GOOD MORNING!**
> Sunny and 72°F with a light breeze — a perfect day to make momentum work in
> your favor.
>
> 📅 **TODAY'S SCHEDULE**
> - 9:00 AM: Standup with Engineering (Zoom)
> - 12:30 PM: Lunch with Dana (Cafe Luca)
> - 3:00 PM: Q3 Roadmap Review (Conf Room B)
>
> ✅ **TOP PRIORITIES**
> - [ ] Submit expense report (overdue)
> - [ ] Review and sign the vendor contract
> - [ ] Prep talking points for roadmap review
>
> 📧 **INBOX HEADS-UP**
> - Dana: Confirming lunch + agenda
> - Finance: Reminder — expense deadline today
> - GitHub: 2 PRs awaiting your review
>
> 💡 **DAILY FOCUS**
> Three meetings back-to-back this afternoon — block 30 minutes this morning to
> prep so you can stay present in each.

---

## Notes

- The four placeholders are filled at runtime by the automation; this file
  documents the template, it does not contain live data.
- Adjust the emoji headers or section order to taste — the AI follows whatever
  structure you specify in the prompt.

---

## Free, no-fuss setup (iPhone)

This setup uses only free, built-in tools — **no paid apps and no API keys**.
You'll build one Shortcut, then have it run itself every morning and deliver
the briefing as a notification.

### What you need (all free)
- **Shortcuts** app (built into iOS) — gathers your data.
- A **free AI app** with a Shortcuts action — the **ChatGPT** app's
  *"Ask ChatGPT"* action or the **Claude** app's equivalent. Just install and
  sign in; the free tier is plenty for a daily briefing.

### Step 1 — Build the Shortcut
Open **Shortcuts → +** (new shortcut) and add these actions in order:

1. **Get Current Weather** → then **Get Details of Weather Conditions** (pull
   the bits you want: conditions, high, low, chance of rain).
2. **Find Calendar Events** → set *Start Date is Today*. (Sort by start time.)
3. **Find Reminders** → set *Is Completed is No*. (Optionally filter by due
   date / list.)
4. **Find Email** *(Mail app)* → *Unread is Yes*, limit to ~10.
5. **Text** action — paste the **Prompt** from above, then drag each variable
   from steps 1–4 into the matching `[Insert Shortcut Input / ...]` slot at the
   bottom.
6. **Ask ChatGPT** (or **Claude**) — set its input to the **Text** from step 5.
7. **Show Notification** (or **Show Result** / **Speak Text**) — set its input
   to the AI's response.

Tip: name the shortcut something like **"Morning Briefing"** and give it a sunny
icon.

### Step 2 — Make it run automatically every morning
1. In Shortcuts, tap the **Automation** tab → **+** → **Create Personal
   Automation**.
2. Choose **Time of Day** → set e.g. **7:00 AM**, **Daily**.
3. **Run Immediately** → turn **OFF** *"Ask Before Running"* so it's hands-free.
4. Add action **Run Shortcut → Morning Briefing**.

That's it — each morning the briefing arrives on its own as a notification.

### Optional — put it on your home screen
- **Tap-to-run icon:** open the shortcut → share/settings → **Add to Home
  Screen**. Tapping it runs the briefing on demand.
- **Shortcuts widget:** long-press the home screen → **+** → **Shortcuts** →
  pick *Morning Briefing*. (Note: the widget *launches* the shortcut; the
  briefing text shows in the result sheet/notification, not on the widget face.)

### Notes & gotchas
- First run will ask permission for Calendar, Reminders, Mail, and the AI app —
  allow each once.
- If you don't use Apple Mail, swap step 4 for whatever your mail app exposes to
  Shortcuts, or drop the Inbox section.
- Everything here stays on free tiers; no subscription or developer account
  required.
