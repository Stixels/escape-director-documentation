---
description: Review room performance, recorded runs, and full action logs.
---

# 📊 Room Statistics

<figure><img src="../.gitbook/assets/Room Statistics.png" alt=""><figcaption><p>Example Room Statistics Page</p></figcaption></figure>

## Room Statistics

Use this page to review how a room performs over time. Each completed run is recorded as a row you can analyze later.

### View stats for a room

1. Open **Room Statistics**.
2. Select a room from the list.
3. Review the metrics and the **Recorded Games** table.

### Metrics you’ll see

* **Success Rate:** percent of runs marked complete.
* **Average Time:** average completion time (or time remaining).
* **Record Time:** best (fastest) completion.
* **Recorded Games:** every saved run, with key run details.

### Recorded games, logs, and cleanup

Each recorded game includes fields like date, game master, time remaining, clues used, and player counts.

Use the **Options** menu on a recorded game to:

* **View Logs:** open the full action log from the run (same feed concept as the dashboard).
* **View Notes:** read the notes the game master left at the end of the game.
* **Delete:** remove that recorded run from the room’s history.

{% hint style="warning" %}
Deleting a recorded game is permanent. Export first if you might need it later.
{% endhint %}

### Export and import (CSV)

* **Export Statistics:** downloads a CSV for the selected room.
* **Import Statistics:** uploads a CSV and recreates recorded games.

### CSV Format

The first line must contain headers. Each following row represents one recorded game.

{% hint style="warning" %}
If importing your own CSV, make sure the date is in ISO format.
{% endhint %}

Example:

```csv
Date,Game Master,Time Remaining,Clues Used,Total Players,Experienced Players
2023-06-28T01:05:40.557Z,Matthew,58:32.32,2,2,2
2023-06-28T00:40:19.567Z,Matthew,59:53.23,2,5,1
2023-06-28T00:24:57.304Z,Matthew M,59:53.13,2,3,0
2023-06-27T23:57:59.501Z,Matthew,59:59.35,2,3,1
2023-06-22T01:06:36.225Z,Alex M,59:59.07,1,,2
2023-06-22T01:03:27.110Z,Matthew M,00:00.00,2,,3
2023-06-22T01:02:08.487Z,Matthew M,59:59.28,1,,1
2023-06-22T00:57:05.747Z,Matthew,00:00.00,3,,1
```

If you ever have issues getting your statistics in the right format, message us at [support@escapedirector.com](mailto:support@escapedirector.com).

### Filters

Use filters to narrow the **Recorded Games** list before you review stats or open logs. Available filters depend on the current app version and room configuration.

{% hint style="info" %}
Tip: Filter first, then export. This helps you pull a clean dataset for analysis.
{% endhint %}

### Coming soon

{% hint style="info" %}
We’re continuing to expand analytics.

Planned improvements include:

* More filters (date/time, game master, player type, etc.)
* More data visualizations and performance breakdowns
{% endhint %}
