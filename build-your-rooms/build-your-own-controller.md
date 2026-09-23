# Build Your Own Controller

Use the Device SDK to connect your own controller program to Escape Director.
Your code runs the prop; Escape Director can receive its signals, display its
state, and send its named commands through Room Connector.

If you want to configure inputs and outputs without writing code, choose
**Escape Director firmware** instead. If your existing device already speaks
HTTP or MQTT, choose **Existing device** and map its messages.

## Before you begin

You need experience compiling and uploading controller programs, a USB data
cable, and the SDK ZIP supplied with your Escape Director setup.

The supplied Arduino SDK includes an **Arduino GIGA R1 WiFi** adapter. Attach the
GIGA's antenna. Other Arduino boards need their own compatible adapter; managed
UNO R4 support does not mean the SDK includes a custom UNO adapter. Current guided
pairing uses Chrome, USB and Wi-Fi. It does not provide Ethernet-only or Raspberry
Pi setup.

Use a spare controller for your first test. Keep prop loads disconnected while
uploading and use the example's built-in LEDs to check behavior.

## 1. Install and try the example

1. Extract the SDK ZIP and open `GETTING_STARTED.md`.
2. Install the board core, ArduinoJson and ArduinoMqttClient versions listed there.
3. Import both library ZIPs: **EscapeDirectorDevice** and **EscapeDirector**.
4. Open **File → Examples → EscapeDirector → giga_two_props** in Arduino IDE.
5. Select the GIGA's main M7 processor and USB port, then verify and upload.

The example's D2 button counts three presses and latches its blue LED. D3 holds
the red LED on only while pressed. Buttons connect between the input pin and
GND; the sketch enables pull-ups. **Complete prop** is a deliberate override that
keeps the output active until **Reset**.

## 2. Pair and save the props

1. Stop the Room's game and turn off Test mode. Open **Edit → Devices**.
2. Connect Room Connector on this computer. Use version 0.8.2 or later for the
   description guidance and display metadata in this guide.
3. Choose **Add Integrated Device → Your own firmware (SDK)** and name the Device.
4. Choose **Pair controller**, select its USB port and join the Room Station's
   local network. The controller and computer must be able to reach each other.
5. After verification, choose **Save props to Room**.
6. Turn on **Test mode**, try the LED commands and observe the physical outputs.
   Test mode does not run Automations or complete Room Puzzles.

Do not choose **Install firmware** for this program: that installs managed
firmware in place of your custom code.

## 3. Describe your own prop

Start with a copy of the example. Its description supplies the prop names and
capabilities shown in Devices, Device Monitor and Automations:

- A **signal** is something that happens, such as Button pressed or Completed.
- A **command** is an action your code handles, such as Reset or Open latch.
- A **state field** is a current value, such as Door open or Distance.

Use customer-facing names and stable IDs. A rename keeps its ID; a different prop
or action gets a new one. The bundled `protocol.md` lists accepted types and limits.

Optional `description` text gives a capability an information tooltip. Number
fields can include a `unit`, such as `cm`. Enum fields can include readable `labels`
for their stored values:

```json
{
  "id": "door",
  "name": "Door",
  "type": "enum",
  "values": ["door-open", "door-closed"],
  "labels": { "door-open": "Open", "door-closed": "Closed" },
  "description": "Reported by the door contact."
}
```

Labels change presentation, not the wire values or what a command does. A
controller's report is not proof that a physical latch moved; check the mechanism.

## 4. Connect the prop to your Room

For a prop that declares Puzzle completion, choose its **Linked Puzzle**. This
links physical completion to the Puzzle and manual Puzzle completion to the
prop's completion command. Different props can link to different Puzzles.

For other interactions, create an Automation using the Device's named signal as
the trigger, or its command as an action. Names appear as **Device › Prop ›
Capability**. Start a disposable game to verify the actual trigger and effect.

## 5. Update your program

1. Stop the game and turn off Test mode, then upload your changed firmware.
2. If its description changed, open the existing Device's **Controller setup**.
3. Select **Update firmware connection** and choose the same controller over USB.
4. Wait for reconnection, then choose **Save props to Room**.
5. Review changed capabilities, Puzzle links and Automations; test again.

Uploading alone does not approve a new description. This update keeps the Device
and its existing references when their IDs remain unchanged. It is not the flow
for replacing a physical controller with a different one.

## Troubleshooting

**Controller description changed:** use the update steps above. This message is
not a Wi-Fi diagnosis.

**Controller description is invalid:** expand **Developer details**. Fix the listed
fields in your program: check duplicate IDs, identifier formats, size limits,
number ranges and enum label keys. Upload the corrected program and retry setup.

**Offline without a description error:** check controller power, Room Connector
and local network access. If you just changed the description, use **Update
firmware connection**. The Room keeps its saved props while live state is unavailable.

**A Test command works but a Puzzle does not complete:** Test mode intentionally
does not affect gameplay. Check the Puzzle link or Automation during a running game.

## Use another board

Read `BOARD_PORTING.md` in the SDK ZIP before porting. It explains how to provide
Wi-Fi/TLS, USB setup, durable pairing storage and network discovery. You also need
to adapt pins, memory budgets and input/output timing to your board.

Keep the loop responsive and enforce temporary Test-output deadlines even when a
network call blocks. Verify certificate rejection, reset/power recovery, failed
storage writes and reconnect behavior. Compilation alone does not qualify a new
board for an installed room.

## Next

[Configure Room Automations](configure-room-automations.md) to use your prop's
signals and commands in the Room experience.
