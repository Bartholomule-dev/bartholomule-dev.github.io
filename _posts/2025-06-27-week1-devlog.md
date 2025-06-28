---
title: "Dev Log #2 – Possession, Inventory, and Dynamic Lighting"
date: 2025-06-27
categories: [devlog]
tags: [oguelike, game systems, godot, AI, possession mechanics]
author: bartholomule
---

It's been a wild and productive week in development, with several major systems coming online that dramatically deepen the gameplay. Here’s a breakdown of the big milestones:

---

## Spirit Possession Mechanics

Players can now take control of villagers using a new possession system! This feature introduces:

-A miracle-based targeting UI to select villagers to possess.

-Visual cues like golden outlines to identify possessed characters.

-A dispossession ability and a dynamic UI indicator.

This system also swaps control logic and ensures your inventory and state move with you—everything is tightly integrated into the game’s ECS architecture.

---

## Detailed Stats & Inventory System

I reworked the character stat system and added flexible equipment mechanics:

-Villagers now have strength, speed, and skill proficiencies.

-A slot-based gear system lets them equip weapons, armor, and tools.

-Consumables like healing items are supported with one-time use logic.

Combat is now influenced by strength and equipped bonuses, opening up deep mechanical potential.

---

## Day/Night Cycle and Fog of War

The game now features a smooth, immersive day/night cycle:

-Visibility changes with time—see further during the day, less at night.

-CanvasModulate gives the world a realistic color tint based on time.

-Fog of war is handled by a performant shader that fades and blends beautifully in real-time.

These visuals not only look great, they impact strategy.

---

## Dynamic Lighting System

Lights are now fully dynamic:

-Firepits glow with warmth.

-Players emit their own ambient light.

-Lights interact with fog and day/night to build atmosphere.

Using PointLight2D nodes managed via ECS systems ensures that lights react appropriately to game logic.

---

## Performance & Stability Boosts

Several behind-the-scenes improvements were made:

-Faster initial world loading.

-Smarter AI batching and goal selection.

-Vast improvements to tree generation and pathfinding.

These changes make the game more stable, efficient, and ready for the next stage of development.

---