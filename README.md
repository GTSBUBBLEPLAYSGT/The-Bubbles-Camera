# The Bubbles Camera

A camera mod for **Gorilla Tag** (PC VR) built for making clips. It renders a separate, smoothed camera to your monitor so your footage isn't a shaky copy of the headset view, and it's built around making YouTube and TikTok content.

Built as a [BepInEx](https://github.com/BepInEx/BepInEx) plugin in C#.

## Features

- **Six camera modes:** smooth first person, third person, front facing, freecam, spectate, and handheld
- **Spectate:** jump between other players in the lobby
- **Handheld camera:** attach the camera to your right hand and aim it like a camcorder
- **Vertical output:** 16:9, **9:16 (TikTok / YouTube Shorts)**, and 1:1
- **In-game menu:** sliders for FOV, distance, height, and smoothing
- **Presets:** save and load your favorite camera setups (stored as JSON)
- **Instant replay:** a rolling 30-second buffer you can save with one key press

## Controls

| Key | Action |
|---|---|
| `F1` | Cycle camera mode |
| `F4` | Show / hide the menu |
| `F5` / `F6` | Next / previous player (spectate) |
| `F9` | Save the last 30 seconds of replay |

**Freecam:** `W A S D` to move, `Q` / `E` for down / up, `Shift` to go faster, hold right mouse button to look.

The menu and camera view appear on your **desktop window**, not in the headset. Capture the game window in OBS to record or stream it.

## Requirements

- Gorilla Tag (PC, Steam)
- [BepInEx 5](https://github.com/BepInEx/BepInEx/releases) (x64, Mono) installed in the game folder. Run the game once after installing it so it creates its folders.

## Installation

1. Download the latest `.dll` from the [Releases](../../releases) page.
2. Copy it into `Gorilla Tag/BepInEx/plugins`.
3. Launch the game and join a private or modded lobby.

The camera starts a few seconds after you load into a lobby.

## Saving replays

Press `F9` to save the buffered footage as a numbered sequence of JPG images in:

```
Gorilla Tag/BepInEx/ClipCam/Replays/<date_time>/
```

Turn them into a video with [ffmpeg](https://ffmpeg.org/):

```
ffmpeg -framerate 30 -i frame_%05d.jpg -c:v libx264 -pix_fmt yuv420p clip.mp4
```

Presets are saved to `Gorilla Tag/BepInEx/ClipCam/presets.json`.
