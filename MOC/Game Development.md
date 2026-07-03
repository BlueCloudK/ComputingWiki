# Game Development

Aliases: game dev, game programming, phát triển game

Type: MOC

## Context / Ngữ cảnh

Game Development mở rộng game loop, rendering, physics, input, gameplay systems, asset pipeline và engine architecture.

## Boundary / Ranh giới

### Nó là gì

Đây là MOC điều hướng cho các node thuộc Game Development.

### Nó không phải là gì

Nó không phải tutorial dài hoặc danh sách tool rời rạc.

## Core Mechanism / Cơ chế lõi

Cơ chế lõi là gom node theo workflow, artifact, runtime behavior và failure mode.

## Project Role / Vai trò trong dự án

MOC này giúp mở rộng ComputingWiki có kiểm soát và tìm đúng vùng khi làm project.

## Output / Artifact nên có

- Pack map
- Navigation links
- Source trace cấp vùng

## Decision Checklist / Câu hỏi kiểm tra

- Node có thuộc pack này thật không?
- Link có giúp navigation không?
- Node có nên là tool riêng hay chỉ là keyword?

## Failure Modes / Cách nó gây lỗi

- Nhồi tool quá nhiều mà thiếu cơ chế
- Link rộng làm graph nhiễu
- Node thiếu source trace

## Khi nào chưa cần hoặc dễ over-engineer

- Chưa cần chia sâu nếu pack chưa được dùng trong path
- Dễ over-engineer nếu biến MOC thành tutorial

## Gồm những gì

- [[Game Loop]]
- [[Update Loop]]
- [[Fixed Timestep]]
- [[Delta Time]]
- [[Frame Rate]]
- [[Render Loop]]
- [[Game Engine]]
- [[Scene Graph]]
- [[Entity Component System]]
- [[Game Object]]
- [[Component System]]
- [[Transform]]
- [[Camera System]]
- [[Input System]]
- [[Input Mapping]]
- [[Physics Engine]]
- [[Collision Detection]]
- [[Collision Response]]
- [[Rigid Body]]
- [[Collider]]
- [[Trigger Collider]]
- [[Raycast]]
- [[Animation System]]
- [[State Machine Animation]]
- [[Sprite]]
- [[Texture Atlas]]
- [[Material]]
- [[Shader]]
- [[Vertex Shader]]
- [[Fragment Shader]]
- [[Lighting]]
- [[Particle System]]
- [[Audio Engine]]
- [[Spatial Audio]]
- [[Asset Pipeline]]
- [[Asset Importer]]
- [[Asset Bundle]]
- [[Level Design]]
- [[Tilemap]]
- [[NavMesh]]
- [[Pathfinding]]
- [[AI Behavior Tree]]
- [[Finite State AI]]
- [[Gameplay System]]
- [[Game State]]
- [[Save System]]
- [[Checkpoint]]
- [[Inventory System]]
- [[Quest System]]
- [[Dialogue System]]
- [[UI Canvas]]
- [[HUD]]
- [[Game Menu]]
- [[Pause System]]
- [[Multiplayer]]
- [[Client Prediction]]
- [[Lag Compensation]]
- [[Authoritative Server]]
- [[Matchmaking]]
- [[Lobby]]
- [[Replication]]
- [[Network Tick]]
- [[Game Telemetry]]
- [[Game Analytics]]
- [[Playtest]]
- [[Balancing]]
- [[Difficulty Curve]]
- [[Procedural Generation]]
- [[Random Seed]]
- [[Object Pooling]]
- [[Frame Budget]]
- [[Draw Call]]
- [[Culling]]
- [[Level of Detail]]
- [[Occlusion Culling]]
- [[Memory Budget]]
- [[Platform Porting]]
- [[Game Build]]
- [[Game Patch]]
- [[Mod Support]]

## Nối mạnh

- Chưa có nối mạnh ngoài các node con trực tiếp

## Liên quan rộng

- Programming Languages
- Performance
- Software Architecture

## Keywords / Từ khóa tìm kiếm

- Game Development
- game dev
- game programming
- phát triển game

## Source trace

- Game Programming Patterns
- Unity documentation
- Unreal Engine documentation
- Godot documentation
