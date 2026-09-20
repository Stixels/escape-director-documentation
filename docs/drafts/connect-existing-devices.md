---
description: Connect existing HTTP or MQTT props to Room Automations without replacing their firmware.
---

# Connect existing devices

Use this guide to receive messages from existing props and send their supported
commands from Escape Director. Your device must already support HTTP or MQTT;
you do not need to install Escape Director firmware on it.

## Before you begin

Have the device's connection instructions, message format and supported commands
ready. For MQTT, you also need its broker address and any login details. Run Room
Connector on the Room Station, on a network that allows it to reach the devices
or broker. Guest networks may block that communication.

## 1. Add the connection

1. Open your Room, choose **Edit**, then **Devices**.
2. Connect or update **Room Connector** if prompted.
3. Choose **Add Integrated Device**, then **Existing device**. Give it a name.
4. Choose **MQTT** or **HTTP** and fill in its connection details.
5. For HTTP, choose whether the device sends to Escape Director, receives
   commands, or does both. A device that only sends messages needs no address.
6. Choose **Add Device**, then expand its row.

For incoming HTTP, copy the **POST endpoint** and **X-ED-Token header** into the
device's outgoing request settings. Send its text or JSON as the request body.
Keep the token private. The endpoint points to this Room Station; update the
device if that computer's network address changes.

For outgoing HTTP, **Check reachability** checks whether the address answers.
It does not test a command or prove that the physical prop works.

Connection passwords and tokens stay on this computer. Setting up another Room
Station requires entering those details again.

## 2. Map a signal

1. Choose **Add prop** and name the puzzle or mechanism.
2. Under that prop, choose **Add signal** and give the signal a useful name,
   such as **Button pressed**.
3. Choose **Listen**, then operate the device. For MQTT, enter its topic filter.
   Select the message you want to use. You can also enter its mapping manually.
4. Choose an exact text value, a JSON field and value, or any message. For JSON,
   check the value type: the boolean `true` differs from the text `"true"`.
5. Choose when the signal should trigger:
   - **Every matching message** runs for each arrival, repeats included. Use it
     for events such as a button press.
   - **When it changes to match** waits for a nonmatching value followed by a
     match. The first report establishes the starting state. Use it for state
     transitions, such as a prop changing from unsolved to solved.
6. If the signal should complete a Room Puzzle, select **Also complete a puzzle
   when this arrives** and choose the Puzzle. This creates a regular Automation.
7. Choose **Save signal**.

Listening cannot determine whether repeated messages are separate events or
periodic state reports. Choose the trigger based on how your device works.
MQTT messages marked **Retained** show previous state and do not run Automations.

## 3. Map state and commands

Use **Add state** to name a reported text, number or true/false value for Device
Monitor. This does not create an Automation trigger by itself.

Use **Add command** to define a supported MQTT topic and payload, or an HTTP
GET/POST path. Choose a name such as **Open latch** that a Game Master can identify.
If the device reports its result, select that state under expected state and
choose the value and wait time.

Test sends a real command. Keep people clear of moving props and verify the
physical result before using the command during a game. The result distinguishes:

- **Sent**: Room Connector sent the request.
- **Accepted**: the broker or HTTP endpoint accepted it. This does not prove that
  the prop acted. MQTT delivery without acknowledgement may show only Sent.
- **Expected state reported**: a matching report arrived after this command.
  No new report means unconfirmed; the command may still have worked.

MQTT commands are never retained. With delivery level 1, a broker can deliver a
command more than once, so use commands the device can safely repeat. The device's
own broker session may also queue messages while it is offline; check its settings.

## 4. Use it in an Automation

Open **Automations**, choose a device signal as a trigger or a device command as
an action, and select the named prop mapping. You can also choose **New device
signal…** or **New device command…** there, create the mapping, then choose
**Save and use**. Save the Automation afterward.

The **Used in** control beside a mapping opens its referring Automations.
Removing a mapping disables Automations that depend on it until you repair them.

## 5. Check the complete game

1. In Devices, turn on **Test mode**. Send inputs, inspect messages, and test each
   command. Test mode does not run Automations or write to the Session Log.
2. To map a captured message, choose **Map…**. Your mapping stays a draft until
   you choose **Turn off Test mode and save**.
3. Turn off Test mode and run a bench game from the Room Dashboard. Operate the
   prop and check the Puzzle, Automation action and physical output together.
4. Finish the game and check the device's own reset procedure. **Reset Room**
   does not invent a reset command for existing hardware.

You're ready when the input triggers the intended Automation, the command acts
on the correct prop, and the starting state can be restored for the next group.
Device Monitor shows reported state. An incoming-only HTTP device shows its last
request time rather than Online: a quiet device may simply have nothing to report.

Commands missed during a disconnection are not replayed when Room Connector
reconnects. Verify the prop's current state before manually sending another command.

## Next

[Configure Room Automations](../../build-your-rooms/configure-room-automations.md)
to combine device signals and commands with your Room's other actions.
