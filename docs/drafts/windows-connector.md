# Set up Room Connector on Windows

Release draft — verify these steps with the Windows installer before publication.

Use Chrome on a Windows 11 PC with a 64-bit Intel or AMD processor. Connect the
PC and controller to the same private network. Have a USB data cable ready.

1. Open your Room, choose **Edit**, then **Devices**.
2. Choose **Set up Room Connector**, then **Download for Windows 11**.
3. Run the installer and open **Room Connector**. Its icon appears in the
   Windows tray. You do not need to install developer tools.
4. Return to Escape Director and choose **Open Room Connector**. Allow Chrome
   to open the app, then choose **Connect** in Room Connector's window.
5. If Windows asks about network access, allow the Connector on your private
   network so it can communicate with the controller. Keep the firewall enabled.
6. Confirm Room Connector says **Connected**, then continue with
   [Add and pair your controller](connect-room-devices.md#2-add-and-pair-your-controller).

Keep Room Connector running while using the Room. From its tray menu, enable
**Start at login** if this PC operates the Room each day.

## Update it

Finish any running game. Quit Room Connector from its tray menu, download the
update in Escape Director, and run the installer. Open Room Connector again.
Your pairing and settings stay saved; there is no need to add the same Devices
again. The update notice clears once the new version connects.

## Before publishing this page

Record the actual unsigned installer warning, firewall wording and any USB
driver steps from the Windows check. Replace this section with verified help
beside the affected steps. Do not claim Windows is supported until that check
passes; do not recommend disabling security protection to install the app.
