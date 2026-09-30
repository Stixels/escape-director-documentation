# Unpublished device setup guide

[Connect Room devices](../../build-your-rooms/connect-room-devices.md) is a release draft for the device
integration work. It is intentionally absent from the published SUMMARY until
this workflow is released. Add it under Build Your Rooms, link it from that
section's README, and verify its labels and installation steps against the
release candidate before publication.

Release qualification still needs the unsigned macOS installation path, Windows
availability, managed physical checks and final download locations. Add only
platform instructions backed by a tested installer. This draft does not promise
Windows or ChromeOS availability. The [Windows setup draft](../../build-your-rooms/windows-connector.md)
is ready for comparison with the Windows candidate; its native install, firewall
and USB checks remain pending. The SDK's developer quickstart
(`GETTING_STARTED.md`) is maintained in the
[Device SDK repository](https://github.com/Stixels/escape-director-device-sdk),
not here.

## Release coordination

The companion branch is `ed-70-add-supported-hardware-and-prop-integration`,
reviewed through a draft PR targeting `dev`. Link it from the frontend/backend
promotion PRs. Every device guide stays in `docs/drafts/`, outside `SUMMARY.md`,
so merging or promoting this branch publishes nothing. Keep the guides
unpublished until the feature release.

The frontend's `docs/ed70-implementation-status.md` owns the documentation release
gate. Production readiness requires both the owner setup guide and a public
technical SDK guide, checked against the staging candidate and the SDK release.
The [technical SDK guide](../../build-your-rooms/build-your-own-controller.md) covers the app side;
the SDK's `GETTING_STARTED.md` covers Arduino installation and the example, and
links back to it. It links to the SDK repository, which must be public before
this guide is published. Record the reviewed documentation commit and prepare
final links before main promotion.

## Publish with the feature release

In one change, with the approved feature release:

1. Move `connect-room-devices.md`, `connect-existing-devices.md`,
   `device-workflows.md` and `build-your-own-controller.md` into
   `build-your-rooms/` (and `windows-connector.md` only if Windows is
   qualified), then fix their relative links.
2. Add them to `SUMMARY.md` under Build Your Rooms and link them from
   `build-your-rooms/README.md`.
3. Confirm the SDK repository link is public and every download link works.

## Existing HTTP and MQTT devices

[Connect existing devices](../../build-your-rooms/connect-existing-devices.md) covers the Room Connector
0.8.5 candidate's setup, shared mapping editor, Test boundary and command
evidence. Keep it unpublished with the owner guide until the feature release.
Its local HTTP walkthrough was exercised in the app; qualify representative
customer devices and broker settings against the release candidate.
