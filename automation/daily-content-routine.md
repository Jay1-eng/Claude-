# Daily Content Routine

A scheduled Routine wakes the original setup session (the Claude Code cloud session that built this repo)
every morning and has it write the next day's content pack into this repo, so there is always a fresh,
ready-to-record script waiting on GitHub.

## What it does each run
1. Pulls the latest `main`, then reads `calendar/30-day-calendar.md`, `content/log.md`, and the two most
   recent packs (to avoid repeating facts/hooks).
2. Writes the **next missing day's** pack to `content/week-XX/day-XX.md` following
   `templates/daily-pack-template.md` and the rules in `plan/01-channel-blueprint.md` and `plan/04-brand-kit.md`.
   On Tuesdays and Saturdays the pack also includes the long-form script.
3. If the calendar has run out, it appends 7 new ideas to the calendar first, across the five series,
   avoiding topics already used.
4. Adds a row to `content/log.md`, commits, and pushes to `main`.

It runs one day ahead: Day 8 (11 Oct) was written on 3 Oct, so packs stay about a week in front of the posting date.

## Where to find it / how to pause
- Listed in the Claude app under **Routines** (name: "Daily YouTube content pack"). Schedule: 04:51 UTC daily.
- Pause / resume: toggle it there. Delete it from the same place.
- Change the time: edit the schedule in the Routines list.
- Change the niche or style: edit the files in `plan/`. The routine reads them on every run.
- Each run's reply (day, file, what to double-check) appears in the setup session's conversation.

## Why it runs inside the setup session
Routines that spawn a brand-new session do not get this repo attached, so their push fails with a 403
(this was tested). The setup session already holds the repo, so the routine is bound to it instead.
If that session is ever archived or deleted, recreate the routine from a new session that has this repo
open, using the prompt in `templates/script-prompts.md` as the basis.

## If a run fails
Open the setup session in the Claude app: the pack is in its last reply even if the push failed.
Fix the GitHub access (Settings → Connectors → GitHub) and the next run catches up automatically,
because it always writes the lowest missing day.

## Manual fallback
Paste the prompt in `templates/script-prompts.md` into any AI assistant with the next calendar topic.
