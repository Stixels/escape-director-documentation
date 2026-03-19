---
description: How do we solve these problems?
---

# 💡 Solution

Escape Director (ED) solves this by putting your whole room workflow in one place. Design the room, run the session, then review what happened.

### Technical highlights (quick)

ED is built as a modern web app. It’s designed to be fast during live runs and reliable for post-game review.

* **Rich media at scale:** images, audio, and video stored in **AWS S3**.
* **Cross-device UI:** a responsive interface for day-to-day operations.
* **Secure payments:** Pro memberships handled via **Stripe**.

### The core loop

#### 1) Build room content once

Create rooms with structured puzzles and hints. Attach rich media (images, audio, video) to support clue delivery.

#### 2) Run sessions consistently

Game masters use a single dashboard during live runs. The Live View keeps player-facing content controlled and predictable.

#### 3) Improve with real data

Every run produces:

* **Statistics** (success rate, time, clues used, etc.)
* **Full logs** of key actions during the session

Owners can review performance and make data-driven changes.

### Where to go next

Start practical. Then go deeper.

* [Getting Started](../getting-started.md)
* [Managing Escape Rooms](../user-manual/managing-escape-rooms/)
* [Running Escape Rooms](../user-manual/running-escape-rooms.md)
* [Room Statistics](../user-manual/room-statistics.md)

<details>

<summary>Full technical details (stack)</summary>

ED is a web application built with:

* **Front-end:** [React](https://react.dev/) + [Material UI](https://mui.com/)
* **Back-end:** [Node.js](https://nodejs.org/en) + [Express](https://expressjs.com/)
* **Database:** [MongoDB](https://www.mongodb.com/)
* **Media storage:** [AWS S3](https://aws.amazon.com/s3/)
* **Payments:** [Stripe](https://stripe.com/)

</details>
