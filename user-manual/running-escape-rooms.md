---
description: Learn how to run the rooms
---

# 🖥️ Running Escape Rooms

<figure><img src="../.gitbook/assets/Dashboard.png" alt=""><figcaption><p>Example of a Room Dashboard</p></figcaption></figure>

## Room Dashboard

Use the Room Dashboard during live games. It’s built for fast hint delivery, rich media clues, and consistent runs.

### Typical run (quick flow)

{% stepper %}
{% step %}
### Reset and prep

Use **Reset** to clear the dashboard and Live View before a new group.
{% endstep %}

{% step %}
### Open Live View

Click **Open Live View** to launch the player-facing screen.
{% endstep %}

{% step %}
### Start the game

Either:

* click **Show Video Brief** (auto-starts the timer at the end), or
* use **Start/Stop** to start manually.
{% endstep %}

{% step %}
### Run the session

Send hints, share media, and track puzzle progress. Use the Action Feed to confirm what was sent and when.
{% endstep %}

{% step %}
### End the game (and record stats)

Use **Complete Room** for a win. Or let the timer expire for a fail.

Both paths trigger a **game-ending event** that records the run for stats and logs.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
The room dashboard is subject to change and there may be more functionality added.
{% endhint %}

### Header

* **Back**: Takes you back to the previous page.
* **Edit Room**: Navigates to the Edit Room page for the current room, allowing you to make further adjustments.
* **Audio Mixer**: Lets you adjust the volume, play/pause, and reset any audio added to the room.
* **Open Live View**: Opens the Live View, which provides players with important information during the game, such as time remaining, clues, and in-game messages.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Example of a LiveView</p></figcaption></figure>

### Room Controls

* **Reset**: Resets everything within the dashboard and Live View, ensuring the room is ready to run again.
* **Show Video Brief**: Displays the introduction video for the room and automatically starts the timer once it finishes.
* **Complete Room**: Marks the room as successfully completed, showing a congratulatory message to the players along with their remaining time.
* **Game-Ending Event**: Prompts you for run details (game master, clues used, players, etc.). This is used for [Room Statistics](room-statistics.md) and logs.

{% hint style="info" %}
**Fail View:** When the time runs out, the Live View displays a fail screen and asks game masters for the same information. It is also a game-ending event.
{% endhint %}

### Time Controls

* **Time Remaining**: Displays the remaining time for the room.
* **Start/Stop**: Starts or stops the timer accordingly.
* **Speed Control**: Allows you to adjust the time to run at 0.5x, 1x, or 1.5x speed.
* **Adjust Time**: An input box where you can manually adjust the time by a specified number of minutes using the +/- buttons.

### Clue Controls

* **Hints Remaining**: Shows the number of hints available to the players.
* **Using Hints**: Clicking on the 🔒 icons unlocks a hint 🔓, indicating that it has been used by the players.

### Puzzles and Hints

* **Puzzles Display**: Lists the puzzles in the order they were saved.
* **Puzzle Details**: Clicking on a puzzle displays its information to the right.
* **Mark as Complete**: This allows you to mark a puzzle as complete.
* **Hint Messaging**: Within the message box, you can send hints to the players. Sent hints appear darker and italicized to indicate they have been used.

### Communication Controls

* **Manual Messaging**: Enables game masters to type personal messages and send them by pressing the Send button.
* **Alert**: Triggers an alert sound within the room to attract the players' attention.
* **Transmit**: Allows game masters to communicate directly with players using their microphones.
* **Media Sharing**: Buttons to send images, videos, or play audio in the Live View.

### Action Feed

Displays important game master actions throughout the game.

* **Live View Display**: The bottom-most message in the action feed is displayed within the Live View.
* **Clear Live View**: Clears the Live View, removing all displayed messages.

### Next: review the run

After a session, head to [Room Statistics](room-statistics.md) to review stats and open the full logs.
