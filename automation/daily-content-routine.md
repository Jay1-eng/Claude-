# Daily Content Routine

A scheduled Routine (a Claude Code cloud session that runs on a timer) writes the next day's content pack into
this repo every morning, so there is always a fresh, ready-to-record script waiting.

## What it does each run
1. Reads `calendar/30-day-calendar.md`, `content/log.md`, and the most recent packs (to avoid repeating facts/hooks).
2. Writes **tomorrow's** pack to `content/week-XX/day-XX.md` following `templates/daily-pack-template.md`
   and the rules in `plan/01-channel-blueprint.md` and `plan/04-brand-kit.md`.
   On Tuesdays and Saturdays the pack also includes the long-form script.
3. If the calendar has run out (after Day 30), it appends 7 new ideas to the calendar first, in the five series,
   avoiding topics already used.
4. Adds a row to `content/log.md`, commits, and pushes to `main`.
5. Sends a push notification when done.

## Where to find it / how to pause
- The routine is listed in the Claude app under **Routines** (name: "Daily YouTube content pack").
- Pause: toggle it off there. Resume: toggle it on. Delete it from the same place.
- Change the time: edit the schedule in the Routines list. It is currently set to run early each morning
  (04:51 UTC) so the pack is waiting whatever your time zone.
- Change the niche or style: edit the files in `plan/`. The routine reads them on every run.

## If a run fails
The routine uses the same GitHub access as this repo. If a push fails, the pack is still written in that
session's transcript; open the Routine's last run to copy it. Fix the access (GitHub connector) and the next
run will catch up by checking which day is missing in `content/`.

## Manual fallback
Paste the prompt in `templates/script-prompts.md` into any AI assistant with the next calendar topic.
