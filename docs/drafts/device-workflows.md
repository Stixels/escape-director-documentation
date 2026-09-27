---
description: Walk through a held-button prop, an MQTT puzzle, and an HTTP input using named signals, commands and state.
---

# Three ways to connect a prop to your Room

Use these walkthroughs to choose how a physical input should affect a prop and
Escape Director. Start in a bench Room with no guests or connected mechanisms.

- **Managed controller:** Escape Director firmware reads wired inputs and runs
  the configured local behavior.
- **Existing MQTT or HTTP device:** keep its firmware. Map the messages it already
  sends and the commands it already understands.

A **signal** starts an Automation. A **command** asks a device to do something.
**State** displays what a device reports; displaying state alone does not create
an Automation. Give all three names a Game Master can recognize.

## Hold a button to keep an output on

**As a Room owner, I want the output active only while players hold a button,
and I want the prop to complete its linked Puzzle during a game.**

This bench uses an Arduino UNO R4 WiFi and its built-in LED. It does not drive a
relay or lock. The UNO R4 WiFi has a built-in antenna.

1. In **Edit Room → Devices**, connect Room Connector. Choose **Add Integrated
   Device → Escape Director firmware**, name it **Hold-button controller**, and
   save the Device if prompted.
2. Connect USB and choose **Pair controller**, then select the UNO in the setup
   dialog. Install managed firmware if asked; setup continues to Wi-Fi by
   itself. Enter the Wi-Fi details and wait for the Room Station verification
   to succeed. The computer and board
   must be able to reach one another on the local network.
3. Disconnect USB before wiring. Connect a normally-open button between **D2**
   and **GND**. With a four-leg tactile button, use two terminals that become
   connected only when pressed; two legs on the same side may already be joined.
   Reconnect USB after checking the wiring.
4. Configure one prop named **Hold button**. Use one input on **D2**, active-low
   with the pull-up configuration, and **All inputs active**. Disable the override
   for this bench.
5. Choose **Built-in LED** as the output, **While inputs are active**, and startup
   off. Choose **Save and apply**, confirm, and wait for the controller to
   confirm the change.
6. Turn on **Test mode**. Press the button: the input and LED should become active.
   Release it: both should become inactive. Repeat several times. Test mode must
   not complete a Room Puzzle or run an Automation.
7. Turn off Test mode. Select the Room Puzzle under **Linked Puzzle**. Start a
   bench game and press the button. The LED should turn on and the Puzzle should
   complete. Releasing the button turns off the LED but leaves completion recorded.
8. Release the button, mark the Puzzle undone, then press again. It should complete
   again. Finish/reset the bench game, then check that a controller reset or power
   cycle reconnects and returns to the expected starting state.

**You're ready when:** the input, LED and Puzzle respond as described, and the
board reconnects without being paired again. Test the real output hardware
separately before using it with guests.

**Why use Linked Puzzle?** It handles both directions without reciprocal
Automations. Completing the Puzzle manually completes the prop too. A manual
completion or override holds the output until Reset; it is different from simply
releasing a physical input.

## An MQTT puzzle reports that it is solved

**As a Room owner, I want to keep my existing puzzle controller and complete a
Room Puzzle when it reports solved. Repeated status reports should not repeatedly
run the Automation.**

Example messages below are illustrative. Substitute the topics and payloads your
device actually supports; Escape Director does not add these commands to it.

1. Add an **Existing device → MQTT**, enter its broker address and credentials,
   then save it. Add a prop named **Wall safe**.
2. Choose **Add from a message**, keep **A moment**, name it **Solved**, enter a Listen filter such as
   `room/wall-safe/#`, and choose **Listen**. Operate the device until it publishes
   a status message such as `{"solved":true}` on `room/wall-safe/state`.
3. Select that message and click its `true` value, so JSON field `solved` matches
   boolean `true`, not text `"true"`. Set the verb to **changes to**.
4. Under **Complete a puzzle**, choose **Wall safe**, then **Save signal**. This creates an editable Automation. Open **Automations** and check that it is enabled.
5. Choose **Add from a message** again, select **A reading**, and name it
   **Solved**, using the same topic and JSON field with value type **true / false**. This gives Device Monitor a readout in addition to the signal.
6. In Test mode, make the device report `{"solved":false}`, then
   `{"solved":true}`, then `{"solved":true}` again. The change-to-match signal
   should occur once. False rearms it; another true can trigger it again.
7. Turn off Test mode and start a bench game. Repeat false → true. Check the
   Puzzle and Session Log. A first report only establishes the starting state;
   a retained report does not run an Automation.

**You're ready when:** a fresh unsolved-to-solved transition completes the right
Puzzle, repeated solved reports do not create repeated runs, and the readout
shows reported state.

For a device that sends discrete **button pressed** events instead of periodic
state, set the verb to **is**. Repeats then count as events. Listening
cannot decide which meaning your device intended.

## An HTTP input completes a Puzzle and sends a command

**As a Room owner, I want an existing sensor to notify Escape Director, then use
that input to complete a Puzzle and ask another device to open a latch.**

1. Add an **Existing device → HTTP**. If it only sends messages, leave
   **Device address** blank.
2. Copy its generated **POST endpoint** and **X-ED-Token header** into the sensor's
   request settings. Send JSON such as `{"pressed":true}` in the request body.
   Keep the token private and use an address reachable from the sensor.
3. Add a prop, then **Add from a message** for a signal named **Pressed**. Listen
   for the request, then click the `true` value of `pressed`. For distinct press
   events, keep the verb **is**. Choose a Puzzle under **Complete a puzzle** if wanted.
4. Add the output device using its supported HTTP or MQTT connection. It can be
   the same Device if it has a **Device address**, or a separate Device.
5. Under the output prop, choose **Add command** and name it **Open latch**. Enter
   the device's documented command: for example, HTTP `POST /open` with body
   `open`, or MQTT topic `room/latch/command` with payload `open`.
6. If the device reports its position, add a state mapping first, then select the
   expected state and value in the command. For example, **Door = open** within
   three seconds. Only a new report received after the send counts.
7. Use **Test mode → Send test**. Confirm the physical result. HTTP acceptance or
   an MQTT broker receipt alone does not prove the latch moved. No fresh report
   leaves the state unconfirmed, even if the command worked.
8. In **Automations**, choose either **Pressed** or the associated **Puzzle
   completed** event as the trigger. Add **Open latch** as the device-command
   action, save, and enable the Automation. Use one route for this action so it is not sent twice.
9. Leave Test mode and run a bench game. Send one input; verify the intended
   Puzzle completion, Automation, command and reported state together.

**You're ready when:** the incoming request reaches the correct prop, the intended
Automation runs once, and the output acts and reports as expected.

An incoming-only device's last-request time is not an online-health guarantee.
**Reset Room** does not invent a reset command for existing hardware; restore its
starting state using its own reset procedure or an explicitly configured command.

## Explore messages without affecting a game

In Test mode, **Map…** turns an unmapped capture into a draft. Review its name,
value type and verb. **Turn off Test mode and save** ends testing before
saving the mapping. The draft itself must not change the applied configuration.

Test mode can send real commands, but it does not run Automations or write device
activity into the Session Log. Use its message list and device trace for setup;
use a bench game to verify the complete gameplay path.

## Next

- [Connect Room devices](connect-room-devices.md)
- [Connect existing HTTP and MQTT devices](connect-existing-devices.md)
- [Configure Room Automations](../../build-your-rooms/configure-room-automations.md)
