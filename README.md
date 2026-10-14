# ds-vr — Dead Space (2008) in VR · alpha for Linux

A VR mod for the original **Dead Space** (2008, Steam app 17470), played through
**SteamVR on Linux** (Steam + Proton). You play in first person: you look around
with your head, aim the gun with your hand, and see Isaac's own hands follow
your controllers. The game's holograms stay holograms.

> **Alpha.** It has been played through the start of the game on one PC
> (AMD GPU, Proton, SteamVR, Valve Index controllers). Expect bugs. It's not
> affiliated with EA or Motive.

## Download

Get `ds-vr-0.1.0-alpha-linux.tar.gz` from the
[Releases](https://github.com/Mortygotvr/deadspace-vr/releases) page, extract
it, and follow the steps below from the extracted folder.

## What you need

- Dead Space (2008) on Steam, running under Proton.
- SteamVR, with a headset and two tracked controllers.
- Windows is **not supported yet** (the mod relies on Proton's DXVK).

## Install

1. Close the game.
2. Run `./install.sh` from this folder. It finds the game in your Steam
   libraries; otherwise give its folder: `./install.sh "/path/to/Dead Space"`.
3. In Steam, right click Dead Space › Properties › Launch options:

   ```
   WINEDLLOVERRIDES="d3d9=n,b" %command%
   ```

4. In the game's own options, play **windowed** with **VSync off** (the mod
   paces frames to your headset).
5. Valve Index controllers: with SteamVR closed, run `./steamvr-binding.sh`
   once (A/B as buttons, trackpads off, grip at 30%). Other controllers use
   SteamVR's defaults.

Optional, if the view stutters: give SteamVR's compositor the priority it asks
for (one time, needs your password):

```
sudo setcap CAP_SYS_NICE=eip ~/.local/share/Steam/steamapps/common/SteamVR/bin/linux64/vrcompositor-launcher
```

To remove the mod: `./uninstall.sh`, and clear the launch option.

## Playing

Start SteamVR, then the game. Menus, loading screens and videos show on a
floating screen; in a level you're in Isaac's head. When a level has loaded,
the view centers on you: face the way you want to play.

### Controls

| Control | Not aiming | Aiming (hold right grip) |
|---|---|---|
| Right trigger | Melee | Fire |
| Right A | Interact / accept | Reload |
| Right B | Stomp | Alternate fire |
| Left grip | — | Stasis |
| Left A | Locator | Kinesis |
| Left stick | Walk | Walk |
| Left stick click | Run | Run |
| Right stick left / right | Turn (smooth or snap) | Turn |
| Left trigger + right stick | Pick a weapon | Pick a weapon |
| Right stick down | X | X |
| Left B (short / long) | Inventory / pause | Inventory / pause |
| Swing your right hand | Melee | — |
| Right stick up, held 3 s | Recenter the view | |
| Right stick click, held 1 s | **Settings menu** | |

Your health and stasis show on a hologram on your left wrist.

### Settings menu

Hold the right stick click for a second. Right stick up/down picks a line,
left/right changes it, right B closes.

- **Resolution**: sizes in your headset's own shape (VR 75–150% of what
  SteamVR recommends), or 2560 × 1920. Pick one, then press **right A** to
  apply it. (Applying is new in this alpha; if it misbehaves, the choice is
  also used the next time the game starts.)
- **Turning**: smooth or snap, turn speed, snap angle.
- **Walk smoothing** and **head bob filter**: how much the view softens
  Isaac's steps.

Settings are kept in `ds-vr.cfg` in the game folder.

### Tuning console (optional)

`./ds-vr-console` is a desktop window with every setting as a slider; changes
apply live while the game runs. Note that clicking it takes focus from the
game, which then pauses.

## Known issues

- **One image for both eyes** (no stereo depth yet).
- **Weapons**: the plasma cutter is the one tested; others may sit or aim
  oddly in your hand.
- **Saving** only at the game's save stations.
- The image can feel a bit heavy when the GPU is near its limit (SteamVR
  then drops to a lower frame rate).
- If the GPU ever crashes while loading at some resolution, go back to
  2560 × 1920 (edit `game_width` / `game_height` in `ds-vr.cfg`).

## When something goes wrong

The log is `deadspace_vr.log` in the game folder (earlier runs in `logs/`).
Clicking the right stick writes a marker in it, handy to point at a moment.
Please share the log with your bug report.

## Credits

- **ReverseEngineeringGamer**, whose first-person Cheat Engine table and notes
  showed where the game keeps its camera, holograms and more.
- Valve's OpenVR (`openvr_api.dll`, BSD license, see `LICENSE-openvr`).
- DXVK, through Proton.
