# Build Your Own Controller

Use this guide to connect a controller running your own firmware to your Room.
Your firmware runs the prop. Escape Director shows its state, sends its commands
and uses its signals in Automations and linked Puzzles.

If you want to set up inputs and outputs without writing code, choose
**Escape Director firmware** instead. If a device already sends HTTP or MQTT
messages, choose **Existing device** and map its messages.

## Before you begin

- **Supported boards:** Arduino UNO R4 WiFi or GIGA R1 WiFi, paired over USB
  and Wi-Fi. Other boards need an adapter; see `BOARD_PORTING.md` in the SDK
  download.
- **Room Connector** 0.8.2 or later, running on the Room Station computer.
- **Chrome**, a USB data cable and the SDK download.
- Experience uploading Arduino sketches.

Use a spare controller for your first test, with prop loads disconnected.

## 1. Upload the example

Follow `GETTING_STARTED.md` in the SDK download. It installs the libraries and
uploads an example with two props, **Three taps** and **Hold button**, each
with an LED.

## 2. Pair the controller

1. Open the Room and choose **Edit → Devices**. Stop any game first.
2. Choose **Add Integrated Device → Your own firmware (SDK)** and name the Device.
3. Choose **Pair controller**, select the controller's USB port and join the
   Room Station's network.
4. When the controller connects, choose **Save props to Room**.

Do not choose **Install firmware**: it replaces your firmware with Escape
Director's.

## 3. Test the props

Turn on **Test mode** and try each prop's commands. Watch the physical outputs
as well as the reported state: a confirmed command means the controller accepted
it, not that a mechanism moved.

Test mode does not run Automations or complete Puzzles.

## 4. Use the props in your Room

- **Linked Puzzle:** for a prop that supports Puzzle completion, choose the
  Puzzle it completes. Completing either one completes the other.
- **Automations:** use the prop's signals as triggers and its commands as
  actions. They appear as **Device › Prop › Capability**.

Start a practice game to check the trigger and the effect.

## 5. Update your firmware

1. Stop any game, turn off Test mode, then upload the new firmware.
2. If you changed the props, open the Device's **Controller setup** and choose
   **Update firmware connection**.
3. When the controller reconnects, choose **Save props to Room**.
4. Check Linked Puzzles and Automations, then test again.

Links and Automations are kept for props and capabilities whose IDs didn't
change.

## Build your prop with a coding agent

The SDK download includes `AGENTS.md`, instructions that coding agents such as
Claude Code read automatically. It gives the agent the SDK's rules, the
description schema and the commands to check its work.

1. Open the extracted SDK folder in your coding agent.
2. Describe your prop: its inputs and outputs, what solves it, and which
   commands you want. For example: _"Copy the two_props example to
   vault_keypad. Make one prop that completes when 4-7-1-9 is entered on a
   keypad, with Reset and Open latch commands. Compile it for the UNO R4 WiFi."_
3. Review the changes, then upload the firmware and follow
   [Pair the controller](#2-pair-the-controller) or
   [Update your firmware](#5-update-your-firmware).
4. Test every command yourself. The agent can compile the firmware but can't
   check the wiring or the prop.

## You're ready when...

- The Device shows **Connected** and **Props saved**.
- Each prop reports its state and responds in Test mode.
- A practice game completes the linked Puzzle or runs the Automation once.

## Troubleshooting

**Controller description changed:** you uploaded firmware with different props.
Follow [Update your firmware](#5-update-your-firmware).

**Controller description is invalid:** expand **Developer details**, fix the
listed fields in your firmware and upload it again.

**The controller ran out of memory during setup:** restart it and try again.
If it continues, reduce the memory your firmware uses, such as large buffers or
text.

**Offline:** check the controller's power and Wi-Fi, and that Room Connector is
running.

**A Test command works but the Puzzle doesn't complete:** Test mode never
completes Puzzles. Check the Linked Puzzle during a practice game.

## Next

[Configure Room Automations](configure-room-automations.md) to use your props'
signals and commands.
