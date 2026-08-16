# Global Football Journey

An original cross-platform Unity football vertical slice for Android, Windows, and Linux. It is inspired by
the broadcast presentation and accessible controls of modern football games, but contains no EA FC, FIFA,
UEFA, club-logo, player-likeness, kit, trophy, or stadium assets.

## What is playable now

- Fully procedural 3D pitch, goals, stadium tiers, floodlights, 22 players, and match ball.
- Broadcast-style camera that follows the ball and currently controlled player.
- Keyboard, gamepad, and touch controls through Unity Input System 1.20.
- Passing, shooting, sprinting, player switching, dribbling, scoring, match clock, extra time, and a simulated
  shootout decision if a knockout match is still tied.
- A menu, settings screen, team browser, persistent save data, and tournament hub.
- 211 selectable national associations and 36 original club teams.
- International Cup group standings and knockout progression, plus a simulated 36-club common table with
  top-eight direct qualification, positions 9-24 play-off entry, quick match, and a sixteen-stage Journey mode.
- Mobile, balanced, and ultra graphics presets.
- One-click editor menu builds for APK, Windows 64-bit, and Linux 64-bit.

This is a complete **prototype/vertical slice**, not a production replacement for a AAA football game. A
production FC-scale title needs licensed data and art, motion capture, commentary, online services, extensive
match AI, hundreds of artists/engineers, and years of development.

## Open and run

1. Install **Unity 6000.5.8f1** in Unity Hub (URP 17.5 is resolved by the project).
2. Add the **Android Build Support**, Android SDK/NDK/OpenJDK, **Windows Build Support**, and optionally
   **Linux Build Support** modules.
3. In Unity Hub choose **Add > Add project from disk** and select this folder.
4. Wait for packages to resolve. The project creates `Assets/Scenes/Boot.unity` automatically.
5. Open `Assets/Scenes/Boot.unity` and press Play.

If auto-setup did not run, use `Global Football > Setup > Repair Project Setup` once.

## Controls

| Action | Keyboard | Gamepad | Mobile |
|---|---|---|---|
| Move | WASD or arrow keys | Left stick | Virtual stick |
| Sprint | Shift | Right shoulder | SPRINT |
| Pass | J or Space | South face button | PASS |
| Shoot | K | West face button | SHOOT |
| Switch player | Q or L | Left shoulder | SWITCH |
| Pause | Escape | Start | Pause icon |

## Build

Use the custom Unity menu:

- `Global Football > Build > Android APK`
- `Global Football > Build > Windows 64-bit`
- `Global Football > Build > Linux 64-bit`

Outputs are written to `Builds/`. Android requires the Android modules installed through Unity Hub. A release
APK/AAB also needs your own signing keystore before store distribution.

## Art replacement workflow

The runtime primitives deliberately keep the repository small and legally clean. To move toward production:

1. Model a modular stadium and footballer base mesh in Blender. Keep the pitch at 105 x 68 metres.
2. UV unwrap, create LOD0/LOD1/LOD2, and export FBX with metres and applied transforms.
3. Paint original kit and surface textures in Krita or Quixel Mixer. Only use assets acquired under a licence
   that explicitly permits Unity and redistribution inside a built game.
4. Rig the character to a humanoid skeleton. Upload the original mesh to Mixamo or create animations in
   Blender, then export FBX without embedding copyrighted characters.
5. Import animations as Humanoid clips and create an Animator Controller with idle, jog, sprint, pass, shoot,
   tackle, celebrate, and goalkeeper states.
6. Replace `Footballer.BuildVisual()` with a prefab reference. Keep `Footballer`, `BallController`, and
   `MatchController` as the gameplay layer.

## Project layout

```text
Assets/GlobalFootball/Scripts/Core   bootstrap, save data, session state
Assets/GlobalFootball/Scripts/Data   national and club catalog
Assets/GlobalFootball/Scripts/Input  unified keyboard/gamepad/touch input
Assets/GlobalFootball/Scripts/Match  stadium, players, ball, AI, camera, match rules
Assets/GlobalFootball/Scripts/UI     runtime menus, HUD, touch controls
Assets/GlobalFootball/Editor         setup, validation, and build commands
Docs                                 production notes and 16-stage roadmap
```

## Important scope and legal notes

- Team association names are used as descriptive data only. No official crests, flags, kits, sponsors, player
  names, faces, official fixtures, or competition marks are bundled.
- The club catalog is intentionally fictional. Replace it only with data and art you have licensed.
- “International Cup” and “Champions Cup” are original in-game brands; the official FIFA/UEFA competition
  names, logos, anthem, graphics package, and trophy models are not included.
- The application has no online multiplayer, account system, store, licensed commentary, or live data.

See `Docs/PRODUCTION_GUIDE.md`, `Docs/ROADMAP_16_STAGES.md`, and `Docs/QA_REPORT.md` for the researched
production path and the exact validation boundary.
Persian setup instructions are available in `README_FA.md`.
