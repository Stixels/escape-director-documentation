---
description: Connect a controller, configure its props, and test them with your Room.
---

# Connect Room devices

Use **Escape Director firmware** to set up supported puzzle behavior in the app.
You do not need Arduino IDE or the SDK for this path. Choose **My own sketch
(SDK)** only when you or your developer will write the controller's program.

## Before you start

Use Chrome on the computer that will operate the Room. Have your controller,
a USB data cable and Wi-Fi password ready. For a GIGA R1 WiFi, attach its external
antenna. Start on the same non-guest network as the Room Station; the devices
must be allowed to communicate with one another.

The current managed setup supports Arduino GIGA R1 WiFi and UNO R4 WiFi. Custom
SDK setup currently has a GIGA adapter. Keep the controller's prop outputs
disconnected while installing firmware and setting up wiring.

## 1. Connect Room Connector

1. Open your Room, choose **Edit**, then **Devices**.
2. Connect **Room Connector**. On a Mac, download it when prompted, move the app
   to **Applications**, and open it.
3. When Chrome asks to open Room Connector, allow it. Choose **Connect** in
   Room Connector's window.
4. Return to the Devices tab and confirm Room Connector says **Connected**.

Keep Room Connector running on this computer while operating the Room. You do
not need to reinstall it when you refresh the page.

## 2. Add and pair your controller

1. Choose **Add Integrated Device**, then **Escape Director firmware**.
2. Give the Device a recognizable name and choose **Add Device**.
3. Connect the controller by USB and choose **Pair controller**.
4. If the board needs firmware, choose **Install firmware** and select your board.
   Installation replaces its current program. When it finishes, choose
   **Continue to Wi-Fi** and select the controller in Chrome.
5. Follow the setup steps to choose a Wi-Fi network and enter its password.
   Use **Scan again** if needed, or **Enter name manually** for a hidden network.
6. Wait for setup to confirm that the controller reached the Room Station.

USB is needed for initial setup and firmware installation. After successful setup,
normal communication uses Wi-Fi. The controller still needs a suitable power source.

## 3. Configure the props

1. Add the props this controller will operate.
2. Choose each prop's behavior and assign the input and output channels to match
   the wiring. Several props can share one board using different channels.
3. For an ordered sequence, arrange the input rows in the order players must
   activate them.
4. Choose **Apply to device** and wait for confirmation.

If the app reports a problem, correct it before testing. Saving a configuration
in the app and applying it to the physical controller are separate steps.

## 4. Test before running a game

1. Turn on **Test mode**.
2. Operate each physical input and check the reported progress and actual output.
3. Reset the prop and try the inputs in a different order. Confirm each prop
   controls only its intended output.
4. Leave the inputs in their starting positions, reset the props, and turn off
   Test mode before changing configuration or starting a game.

Test mode does not run Automations or change Room Puzzle completion. Device
activity and diagnostics are separate from the Session Log. Use the board's
wiring instructions to connect and verify the intended loads before admitting guests.

## 5. Link props to Room Puzzles

1. In a prop's **Linked Puzzle** selector, choose the Puzzle it represents.
   Different props can link to different Puzzles.
2. Start a bench game from the Room Dashboard. Complete the Puzzle from the
   Dashboard and check that the linked prop completes.
3. Finish the game, then choose **Reset Room**. Start another bench game and
   solve the physical prop. Check that its Puzzle completes once.
4. Finish and reset again. Check controller power-cycle recovery before using
   the Room with guests.

A linked Puzzle handles both directions without reciprocal Automations. Use
Automations when completion should also trigger other actions, such as audio.

During a running game, the same controller can show **Reconnecting…** while
recovering, then resume control automatically. Commands missed during the gap
are not repeated. If **Device control paused** remains, check the controller
and any reported problem before choosing **Resume device control**.

## Updating Room Connector

If the app asks for an update, quit Room Connector, replace the existing app in
Applications with the new download, then open it again. Restarting the old app
does not update it. Keep your existing setup; you should not need to pair again.

## Existing HTTP and MQTT devices

Choose **Existing device** to keep a device’s current firmware and map its
messages to Escape Director. Follow [Connect existing devices](connect-existing-devices.md).

## Using your own sketch

Follow the getting-started guide included in the SDK download to install its
libraries and upload your sketch first. Then choose **My own sketch (SDK)** when
adding the Device, pair it, and choose **Save props to Room**. Your sketch defines
its props and wiring; those settings are edited in the sketch.

After uploading a changed sketch, use **Controller setup → Update sketch** and
save its reported props again. Do not use **Install firmware** for a custom
sketch: that replaces it with Escape Director's managed program.

## Next

Try [Three ways to connect a prop to your Room](device-workflows.md) for complete
managed-controller, MQTT and HTTP examples.
