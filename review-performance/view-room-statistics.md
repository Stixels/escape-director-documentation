---
description: Review room metrics, recorded runs, notes, logs, and CSV data.
---

# View Room Statistics

<figure><img src="../.gitbook/assets/Room Statistics.png" alt=""><figcaption><p>Example Room Statistics Page</p></figcaption></figure>

Room Statistics is where you review how a room performs over time. Each saved session appears as a recorded run.

## Before You Begin

Make sure:

* At least one room session has been saved
* You have selected the correct room

{% hint style="info" %}
Room Statistics depends on completed session data. If sessions are not being saved at the end of each game, the reporting view will stay incomplete.
{% endhint %}

## Open Room Statistics

1. Open the `Room Statistics` page.
2. Select the room you want to review.
3. Wait for the metrics and recorded sessions to load.

## Understand The Summary Metrics

| Metric | What it shows |
| --- | --- |
| Success Rate | Percentage of runs marked successful |
| Average Time | Average recorded time outcome |
| Record Time | Best recorded result |

Use these metrics to spot room difficulty, operational consistency, and whether changes are improving results.

## Review Recorded Games

Each recorded game may include:

* Date
* Game master
* Time remaining
* Clues used
* Total players
* Experienced players

Use the table to compare runs, identify outliers, and review changes over time.

## Open Notes And Action Logs

Use the row options menu to:

* View session notes
* View the action log

Notes help explain unusual circumstances. The action log helps you review what happened step by step during the run.

## Delete A Recorded Run

Deletion makes sense when:

* The run was saved by mistake
* The data is invalid
* The session was a test and should not affect production reporting

{% hint style="warning" %}
Delete runs carefully. Export statistics first if you may need the data later.
{% endhint %}

## Export Statistics To CSV

1. Open `Room Statistics`.
2. Select the room.
3. Use the export option to download the CSV.

Expected columns:

| Column | Description |
| --- | --- |
| Date | Session date in ISO format |
| Game Master | Name entered when the session was saved |
| Time Remaining | Recorded time result |
| Clues Used | Number of clues used |
| Total Players | Total player count |
| Experienced Players | Number of experienced players |

## Import Statistics From CSV

The CSV must use the expected headers exactly:

```csv
Date,Game Master,Time Remaining,Clues Used,Total Players,Experienced Players
```

Imported rows should follow these rules:

* `Date` must be a valid date
* `Time Remaining` must use the expected time format
* Player and clue counts must be numeric
* Header names must match exactly

{% hint style="warning" %}
If the headers or field formats are wrong, the import will fail.
{% endhint %}

## Best Practices

* Save every real session.
* Use notes for context when something unusual happens.
* Open logs when a metric changes unexpectedly.
* Export before major cleanup.

## Troubleshooting

### I selected a room, but no statistics appear

This usually means no saved sessions exist for that room yet.

### The import failed

Check:

* The header row matches exactly
* Dates are valid
* Time values use the expected format
* Numeric fields contain numbers only

If the problem continues, contact [support@escapedirector.com](mailto:support@escapedirector.com).

### Should I delete test sessions?

Yes, if you do not want them affecting production reporting. Export first if you may need the data later.
