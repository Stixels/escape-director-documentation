# Unpublished device setup guide

[Connect Room devices](connect-room-devices.md) is a release draft for the device
integration work. It is intentionally absent from the published SUMMARY until
this workflow is released. Add it under Build Your Rooms, link it from that
section's README, and verify its labels and installation steps against the
release candidate before publication.

Release qualification still needs the unsigned macOS installation path, Windows
availability, managed physical checks and final download locations. Add only
platform instructions backed by a tested installer. This draft does not promise
Windows or ChromeOS availability. The [Windows setup draft](windows-connector.md)
is ready for comparison with the Windows candidate; its native install, firewall
and USB checks remain pending. The SDK's developer quickstart ships with the
SDK; it is maintained beside that code in the backend repository.

## Release coordination

The companion branch is `ed-70-add-supported-hardware-and-prop-integration`.
Open its documentation PR when the application feature is prepared for staging,
and link it from the frontend/backend promotion PRs. Keep the guides unpublished
until the feature release.

The frontend's `docs/ed70-implementation-status.md` owns the documentation release
gate. Production readiness requires both the owner setup guide and a public
technical SDK guide, checked against the staging candidate and its SDK download.
The [technical SDK guide](../../build-your-rooms/build-your-own-controller.md)
and its navigation entry are prepared alongside the app links. It covers the app
side; the SDK download's `GETTING_STARTED.md` covers Arduino installation and the
example, and links back to it. Record the reviewed documentation commit and
prepare final links before main promotion. Publish with the approved feature
release.

## Existing HTTP and MQTT devices

[Connect existing devices](connect-existing-devices.md) covers the implemented
Room Connector 0.8.0 setup, shared mapping editor, Test boundary and command
evidence. Keep it unpublished with the owner guide until the feature release.
Its local HTTP walkthrough was exercised in the app; qualify representative
customer devices and broker settings against the release candidate.
