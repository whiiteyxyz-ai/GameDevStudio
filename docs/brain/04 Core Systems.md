---
tags: [design, systems]
---
# Core Systems (first draft, to be refined into GDDs)

## 1. Portals
- Two portals per player: left (Q), right (E). Both must exist to travel.
- Placed on **portalable surfaces** only (map-authored); non-portalable surfaces give feedback.
- Entering one exits the other; velocity and look direction are rotated to match the exit normal (momentum preserved).
- Bullets and projectiles pass through portals; players can see through them.
- Tuning knobs: max distance, placement cooldown, portal size, lifetime, enemy dispel rule.

## 2. Movement
- Quake-style: air control, strafe jumping or bunny-hop-lite, slide, optional double jump (decide in prototype).
- Portals are a movement tool: fling through floor/ceiling pairs to gain speed.

## 3. Weapons (own set, placeholders)
Spawn at fixed locations on timers; no loadouts.
- Starter sidearm (infinite ammo)
- Shotgun, rail/sniper, rocket launcher, rapid-fire SMG, grenade launcher (bounce), melee or shock weapon.
- Rule: each weapon should have a clear portal interaction (rockets curve through, rail line pierces both ends).

## 4. Match rules
- Free-for-all and team deathmatch first.
- Ends on frag limit or time limit; highest score wins; fast respawn at safe spawn points.
- Items: health, armor, weapon pickups, maybe one power-up (quad-style).

## 5. Maps
- Compact, readable, three+ vertical layers, portalable surfaces placed on purpose.
- Start with one test map, then 3 to 4 production maps.

## 6. Netcode
- Server-authoritative, client prediction for movement, lag compensation for hitscan, portal transform-aware prediction. Details in [[05 Tech - Unity]].

Related: [[01 Vision]], [[07 Roadmap]]
