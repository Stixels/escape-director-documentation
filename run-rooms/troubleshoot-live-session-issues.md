---
description: Fix common live-session issues involving Live View, media, cache status, audio, timer, and saved statistics.
---

# Troubleshoot Live Session Issues

Use this page for the most common operational issues during setup or live play.

## Live View Does Not Open

Check:

* You opened the correct room from `All Rooms`
* The browser allowed the new window or tab to open
* The player-facing display is still connected
* Live View was not already opened elsewhere

If Live View opens on the wrong monitor or display, move it to the correct screen and test again before starting.

## Live View Looks Wrong On The Room Screen

If the room screen does not match what you expected from the editor:

* Recheck timer size and position
* Recheck live message position and width
* Recheck clue counter visibility and placement
* Recheck background media for readability problems

The real room display matters more than the editor preview. Adjust the setup based on what players actually see.

## Audio Does Not Play

Check:

* The room actually has audio uploaded
* The station volume and browser volume are not muted
* The `Audio Mixer` volume is not set to `0%`
* The correct audio asset is attached to the room

If needed, use `Audio Mixer` to preview, pause, or reset the audio track before continuing.

## Media Is Missing During A Session

If you cannot send image, video, or audio from the Room Dashboard:

* Confirm that media of that type was uploaded to the room
* Confirm the asset still appears in the room editor
* Confirm the station loaded the correct room
* Confirm cache status is not warning about missing assets you depend on

If the room depends on that media, pause and verify the asset before continuing.

## Cache Status Shows A Warning

`Cache Warning` usually means some room media failed to cache or caching is unavailable in the current environment.

What to do:

* Keep the room open a little longer if caching is still in progress
* Manually verify the media you need for the session
* Avoid assuming offline reliability if the warning remains

### Quick cache reset

If media should be available but the warning persists:

1. Try a hard refresh first.
   Mac: `Cmd + Shift + R`
   Windows: `Ctrl + Shift + R`
2. If the warning still appears, clear site data for the Escape Director app.
   Chrome or Edge: click the site icon to the left of the address bar, open `Site settings`, then clear or reset stored site data for Escape Director.
   Firefox: click the lock icon in the address bar, then clear cookies and site data for the current site.
   Safari (Mac): open `Safari` > `Settings` > `Privacy` > `Manage Website Data`, search for Escape Director, then remove that site's data.
3. Reopen Escape Director, open the room again, and wait for caching to rebuild.

If your browser gives you a choice, clear data for the Escape Director site only instead of clearing all browsing data.

If the room does not depend heavily on media, you may still be able to run it safely after manual checks.

## The Timer Needs Correction

Use the manual time adjustment controls when:

* A group started late
* You granted bonus time
* The room needed an operational correction

If you change the timer during a real session, add the reason to the session notes when saving statistics.

## Statistics Did Not Save

If the run is missing from `Room Statistics`, check whether:

* The statistics modal was fully completed
* Required fields were filled in
* The session was closed without saving

Required fields are:

* Game master
* Clues used
* Total players

If the data was not saved, it will not appear later in `Room Statistics`.

## When To Escalate

If the issue is not resolved quickly, use [Get Help](../get-help.md) and gather:

* Room name
* What you were trying to do
* Browser and device details
* Screenshot of the problem if possible
