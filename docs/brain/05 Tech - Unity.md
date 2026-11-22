---
tags: [tech, unity]
---
# Tech: Unity

- **Engine**: Unity 6.3, C#. Code root is `Assets/` (project config rule).
- **Render pipeline**: URP (good for web/mobile reach and portal cameras).
- **Input**: Unity Input System package (Q/E actions, remappable).
- **Character**: custom kinematic controller (not the default CharacterController) so teleport and velocity rotation are exact.
- **Portal rendering**: a camera per portal renders to a RenderTexture, positioned by mirroring the player camera through the portal pair; oblique near-plane clipping to avoid seeing geometry behind the exit. Recursion depth capped at 1-2.
- **Teleport**: when a player or projectile crosses the portal plane, apply the transform `exit * rotate180 * inverse(entry)` to position, rotation and velocity.
- **Netcode**: Netcode for GameObjects (simpler start) with Unity Gaming Services (Relay/Lobby) for matchmaking; server-authoritative. Revisit if prediction needs push toward Netcode for Entities.
- **Tests**: `Assets/Tests/EditMode` for portal math and match rules, `PlayMode` for integration.
- **Open risk**: portal plus client-side prediction is the hardest part; prototype single-player portals first.

See [[08 Decisions]].
