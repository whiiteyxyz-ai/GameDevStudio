# Technical Preferences

<!-- project.yaml at the repo root is the machine-readable source of truth for
     engine, specialists, naming, performance, platform, and testing.framework.
     This file is the human-readable LEGACY FALLBACK: agents and skills resolve
     each key from project.yaml first and fall back here only when the
     project.yaml key is absent. /setup-engine dual-writes both.
     Forbidden patterns and allowed libraries are NOT migrated — they live only
     in this file. Populated by /setup-engine; updated as decisions are made. -->

## Engine & Language

- **Engine**: Unity 6.3 LTS (6000.3.26f1)
- **Language**: C#
- **Rendering**: URP
- **Physics**: PhysX

## Input & Platform

<!-- Written by /setup-engine. Read by /ux-design, /ux-review, /test-setup, /team-ui, and /dev-story -->
<!-- to scope interaction specs, test helpers, and implementation to the correct input methods. -->

- **Target Platforms**: PC (Windows)
- **Input Methods**: Keyboard/Mouse, Gamepad
- **Primary Input**: Keyboard/Mouse
- **Gamepad Support**: Partial
- **Touch Support**: None
- **Platform Notes**: Q = left portal, E = right portal (remappable via the Unity Input System). Low input latency is a requirement.

## Naming Conventions

- **Classes**: PascalCase (`PlayerController`)
- **Variables**: public PascalCase (`MoveSpeed`), private _camelCase (`_moveSpeed`)
- **Signals/Events**: PascalCase `On<Event>`
- **Files**: PascalCase matching the class (`PlayerController.cs`)
- **Scenes/Prefabs**: PascalCase
- **Constants**: PascalCase or UPPER_SNAKE_CASE (UNVERIFIED, see project.yaml)

## Performance Budgets

- **Target Framerate**: 144 fps (stretch 180 Hz, floor 120 Hz), low input latency
- **Frame Budget**: 6.9 ms at 144 fps (5.5 ms at 180 Hz, 8.3 ms at 120 Hz); includes portal cameras
- **Draw Calls**: [TO BE CONFIGURED once a portal prototype is profiled]
- **Memory Ceiling**: [TO BE CONFIGURED once target hardware is known]

## Testing

- **Framework**: NUnit (Unity Test Framework): `Assets/Tests/EditMode`, `Assets/Tests/PlayMode`
- **Minimum Coverage**: [TO BE CONFIGURED]
- **Required Tests**: Balance formulas, gameplay systems, networking (if applicable)

## Forbidden Patterns

<!-- Add patterns that should never appear in this project's codebase -->
- [None configured yet — add as architectural decisions are made]

## Allowed Libraries / Addons

<!-- Add approved third-party dependencies here -->
- [None configured yet — add as dependencies are approved]

## Architecture Decisions Log

<!-- Quick reference linking to full ADRs in docs/architecture/ -->
- [No ADRs yet — use /architecture-decision to create one]

## Engine Specialists

<!-- Written by /setup-engine when engine is configured. -->
<!-- Read by /code-review, /architecture-decision, /architecture-review, and team skills -->
<!-- to know which specialist to spawn for engine-specific validation. -->

- **Primary**: unity-specialist
- **Language/Code Specialist**: unity-specialist (C# review)
- **Shader Specialist**: unity-shader-specialist (Shader Graph, HLSL, URP materials)
- **UI Specialist**: unity-ui-specialist (UI Toolkit, UGUI)
- **Additional Specialists**: unity-dots-specialist (ECS/Jobs/Burst), unity-addressables-specialist (asset loading)
- **Routing Notes**: Primary for architecture and C# review; shader specialist for portal rendering and VFX; UI specialist for HUD and menus; network-programmer for netcode.

### File Extension Routing

<!-- Skills use this table to select the right specialist per file type. -->
<!-- If a row says [TO BE CONFIGURED], fall back to Primary for that file type. -->

| File Extension / Type | Specialist to Spawn |
|-----------------------|---------------------|
| Game code (.cs) | unity-specialist |
| Shader / material files (.shader, .shadergraph, .mat) | unity-shader-specialist |
| UI / screen files (.uxml, .uss, Canvas prefabs) | unity-ui-specialist |
| Scene / prefab / level files (.unity, .prefab) | unity-specialist |
| Native extension / plugin files (.dll) | unity-specialist |
| General architecture review | Primary |
