---
description: Configure the player-facing Live View before test runs and live sessions.
---

# Configure Live View

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption><p>Example Live View</p></figcaption></figure>

Live View is the player-facing screen your guests see during the game. This is where you control the room's visual presentation, timer display, live messaging, and clue counter.

## Before You Begin

Make sure you have:

* Created and configured the room
* Opened the room in the editor
* Navigated to the Live View settings area

{% hint style="info" %}
Live View controls what players see. It is separate from the game master dashboard used during live operations.
{% endhint %}

## What You Can Configure

| Section | What it controls | Typical use |
| --- | --- | --- |
| Background and media | Background color, image, intro video, background video, soundtrack, alert tone | Sets the room's visual and audio atmosphere |
| Timer | Visibility, color, size, and position | Shows the countdown to players |
| Live messages | Visibility, colors, size, width, and position | Displays messages or hints sent during the game |
| Clue counter | Visibility, size, and position | Shows players how many clues remain |
| Success and failure screens | End-screen text, timer visibility, colors, and end-state media | Controls what players see when the game ends |

## Open The Live View Settings

1. Go to `All Rooms`.
2. Open the room you want to edit.
3. Click `Edit`.
4. Open the Live View configuration area.

## Configure Background And Media

### Set the background color

Use a background color when you want a minimal display or a fallback behind image or video content.

### Add background media

You can upload:

* Background image
* Intro video brief
* Background video
* Background soundtrack
* Alert tone

### Use the background video as the timer

If a background video is uploaded, you can enable the option to use the video duration as the room timer.

This is useful when the room experience is designed around a timed video or when the timer should be represented indirectly.

When this setting is enabled:

* The background video's duration controls the countdown
* The room should be tested on the real player display before live use
* Standard timer layout choices still matter if the timer remains visible elsewhere in the design

{% hint style="warning" %}
Use background motion and audio carefully. If the screen becomes too busy, players may miss the timer or important messages.
{% endhint %}

## Configure The Timer

You can control:

* Visibility
* Color
* Font size
* Horizontal position
* Vertical position

The timer should be easy to scan quickly and should not overlap the message area.

## Configure Live Messages

Use live messages for text sent to players during the game.

You can configure:

* Text color
* Background color
* Font size
* Width
* Position

Use a background color if the message area needs stronger readability over a complex image or video.

## Configure The Clue Counter

If your room shows remaining clues to players, configure the clue counter so it stays visible without competing with the timer or message area.

You can control:

* Visibility
* Size
* Position

## Configure Success And Failure Screens

Live View setup also includes the end screens shown when the room is completed or failed.

For both the success and failure screens, you can configure:

* Background color and media behavior
* Main text visibility and styling
* Timer visibility and styling
* Top and bottom message text

Use this section to make sure the end-of-game state matches the room tone and still stays readable on the display.

### What to decide for end screens

Confirm:

* Whether the remaining time should stay visible
* What headline and supporting message players should see
* Whether the success and failure screens should feel distinct from normal gameplay

{% hint style="info" %}
End screens are part of room setup in the editor. Do not wait until the live dashboard to decide how they should look.
{% endhint %}

## Test Before Live Use

Before using the room with players, confirm:

* The timer is readable from the room
* Messages are visible over the background
* The clue counter is shown only if intended
* Audio and alert behavior match the room design
* Success and failure screens are readable and use the correct text

{% hint style="info" %}
If the real display resolution does not match the editor preview, adjust sizes and positions after testing on the actual screen.
{% endhint %}

## Best Practices

* Prioritize readability over decoration.
* Keep the timer and message area visually separate.
* Use motion and audio only when they support the room experience.
* Test on the real display, not only in the editor preview.

## Troubleshooting

### The timer is hard to read

Increase contrast, adjust placement, or simplify the background behind it.

### Messages overlap other Live View elements

Reposition the message area or reduce its width until it clears the timer and clue counter.

### The display looks different on the room screen

Check the actual display resolution and revise font sizes or positioning from the editor.
