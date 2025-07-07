---
title: "Dev Log #3 – AI Overhaul, Dungeons, and Persistent Resources"
date: 2025-07-07
categories: [devlog]
tags: [roguelike, game systems, godot, AI, GOAP, C++, ECS, procedural generation, quest system]
author: bartholomule
---

This has been one of the most transformative weeks of development yet. I've ripped out and replaced several core systems, migrated performance-critical code to C++, and introduced major new gameplay features like dungeons and a complete questing system. The game is faster, deeper, and more robust.

---

## Complete AI Rework: GOAP & C++ Migration

The old AI system has been fully replaced with a much more powerful and flexible Goal-Oriented Action Planning (GOAP) architecture. To ensure the game runs smoothly, the most performance-intensive parts of the AI have been ported from GDScript to C++.

-GOAP Planner: All villager behavior is now driven by a GOAP planner, allowing for complex, multi-step goals like hunting, crafting, and building.

-C++ Performance: The core GOAP planner, spatial queries (find_nearest_entity), and visibility calculations were migrated to C++ for a massive performance uplift.

-Critical Bug Fixes: Resolved core issues in the AI that caused villagers to stall or get stuck in loops, particularly for building and mining tasks.

-Intelligent Hunting: The hunting system was rewritten to use the new planner, enabling a full resource loop: hunt animal -> retrieve meat -> drop off at firepit.

---

## Procedural Dungeon System

You can now delve beneath the overworld into procedurally generated dungeons. This system was built to be completely seamless, allowing for instant transitions between the two views.

-Procedural Generation: Dungeons are generated on the fly, creating unique layouts for every playthrough.

-Seamless View Switching: A new DungeonManager handles instantaneous transitions between the overworld and dungeon views, re-parenting sprites and switching camera logic as needed.

-Dungeon-Specific Mechanics: The system supports separate collision detection, camera controls, and movement rules tailored for dungeon exploration.

---

## Persistent & Strategic Resource Gathering

Resources are no longer simple, one-time consumables. Trees, ore deposits, and berry bushes are now persistent nodes that must be depleted over time, adding a new layer of strategy to resource management.

-Depletable Nodes: Trees now require multiple chops, and tin deposits must be mined repeatedly, making them feel like substantial resources.

-Multi-Stage Gathering: Villager AI has been updated to support gathering from a single source multiple times until their inventory is full or the node is depleted.

-Smarter Resource Logic: The gathering system now yields multiple resource types (e.g., wood and kindling from trees) and correctly handles node destruction only when fully exhausted.

---

## Atlas-Based Rendering Overhaul

The entire rendering pipeline was redesigned to use Godot's TileSet atlases instead of loading individual textures. This is a breaking change that provides significant benefits.

-Improved Performance & Memory: Using a single texture atlas reduces texture swaps and lowers memory usage.

-Streamlined Workflow: All entity visuals can now be managed visually within the Godot TileSet editor, making it easier to add and modify sprites.

-Centralized Asset Management: The RenderableComponent was redesigned to reference atlas coordinates, creating a more consistent and scalable rendering system.
---

## New Gameplay Systems & Features

Alongside the major overhauls, several new systems were integrated to deepen the gameplay loop.

-Villager Lifecycle: Villagers now have a finite lifespan. An AgingSystem was added to manage their age, and the HousingSystem now spawns new villagers over time to grow the village.

-Quest System: A foundational quest system has been integrated. The first quest, 'Light the Firepit', is now triggered on world creation to guide the player's initial actions.

-UI and World Gen: The UI now includes a coordinate display for easier navigation, and world generation has been improved to create more natural landscapes.

---