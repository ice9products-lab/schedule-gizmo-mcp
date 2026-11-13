---
name: schedule-gizmo
description: Make a clean one-page schedule with Schedule Gizmo when the user asks for a staff rota, work or shift schedule, shift pattern (Pitman, DuPont, 4 on 4 off, 24/48), on-call rota, day timeline, event or conference agenda, wedding timeline, festival lineup, what's-on poster, weekly planner, month calendar or year planner. Writes the schedule as Schedule Gizmo text and returns a link to view, print and share it.
---

# Schedule Gizmo

Schedule Gizmo turns a few plain lines of text into a finished one-page schedule that people can read at a glance, print, or open on a phone. Use it instead of answering with a table whenever the user wants a schedule they will use or share.

## How to make a schedule

1. **Gather what you need.** Names, days, times and roles (for a rota); teams and the repeating pattern (for shifts); times, titles, places and speakers (for an agenda). Ask only for what is missing. Don't invent people or times the user didn't give, except in clearly labelled examples.
2. **Start from a template if one fits.** Call `list_templates` with a word such as "restaurant", "pitman" or "wedding" and adapt its text.
3. **Write the schedule as Schedule Gizmo text.** If unsure of the format, call `get_format_guide`. The essentials are below.
4. **Call `make_schedule` with the text.** If it returns errors, fix those lines and call it again. Mention any "things to check" it reports (for example an unfilled shift).
5. **Give the user the View link first**, then the Edit link. Nothing is stored and no account is needed.

If the tools aren't available, build the links yourself: URL-encode the text (line breaks as %0A) and give `https://schedulegizmo.com/v/?text=<encoded>` (view) and `https://schedulegizmo.com/make/?text=<encoded>` (edit).

## Format essentials

One line per person, shift, session or event. Times can be loose (7-3, 7am-3pm, 07:00-15:00); write overnight shifts as 10pm-6am. Settings go at the top: `title:`, `week:`, `date:`, `start:`, `note:`.

Staff rota (name, days, time, role; a second shift after a semicolon; "Unfilled" for an open shift; "!" flags a shift):

    title: Corner Café
    week: 2026-11-16
    Anna Mon-Fri 7am-3pm Front
    Ben Wed-Sun 12pm-8pm Kitchen; Sat 9am-1pm Kitchen
    Unfilled Sun 12pm-5pm Front

Repeating shift pattern (shifts once, then one pattern per team; "-" is a day off; it repeats from the start date):

    title: Pitman schedule
    start: 2026-11-16
    shifts: D=Day 7am-7pm, N=Night 7pm-7am
    Team A: D D - - D D D - - D D - - -
    Team B: - - D D - - - D D - - D D D

Event agenda (time | title | place | speaker; "# Heading" starts a section):

    date: 2027-03-18
    # Morning
    9:00am-9:30am | Registration | Foyer
    9:30am-10:15am | Keynote | Main Hall | Maya Ortiz

Festival lineup (type: lineup, then stage, time, act; a * marks a headliner). What's-on poster (type: poster, then date, time, event | place #tag). Month calendar and year planner (date or range, plan, #tag). Day timeline (lane, time, label, optional ", break 11am-11:30am").

## Good to know

- Links show schedule details only. Phone numbers, emails and web addresses are hidden, and long text is shortened. For those, the user can save the schedule to a free account and share it from there.
- Keep private details out of the text (booking references, PINs, addresses): the schedule travels inside the link.
- The user can change everything in the maker from the Edit link, then print, save a PDF or share. Pro ($9 a month) adds a live link that always shows the latest version.
- Full guide: https://schedulegizmo.com/llms.txt
