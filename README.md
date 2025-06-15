# RimWorld: Cadia-Style Military Simulation Framework

## Overview

This project aims to transform RimWorld into a multi-map, militarized civilization similar to the world of Cadia. It includes systems for bootcamp training, logistics networks, map-to-map supply chains, advanced pawn role simulation, and modular infrastructure scaling. The design focuses on realism, immersion, and player-driven control of combat, manufacturing, and recruitment.

## Core Objectives

- Build a network of colonies fulfilling military roles (bootcamp, supply depots, factories, FOBs)
- Implement a structured bootcamp pipeline: mental conditioning, skills training, rank progression
- Simulate logistics between maps (e.g., MRE supply runs, weapons transfers)
- Develop pawn roles (e.g., Rifleman, Medic, Squad Leader) with distinct traits, gear, and behavior
- Distribute population across maps to manage performance while scaling up total pawns

## Implementation Goals

- Use and patch existing mods (e.g., Dead Man’s Switch, CSL, CE) to avoid full rewrites
- Create XML trait definitions and promotion systems linked to training or skill thresholds
- Script events (e.g., graduation, promotion) and assign loadouts dynamically
- Design scheduling and zone logic to simulate doctrine, discipline, and operational hierarchy
- Maintain compatibility with RimWorld v1.6 and Combat Extended

## Long-Term Vision

- Semi-autonomous units (e.g., fireteams) managed through trait-based logic and job priorities
- AI-like "commander" pawns that issue orders or influence behavior through zone or job triggers
- Modular faction development across multiple world tiles with limited overlap
- Endgame goal: operational empire with scalable manpower, real logistics, and war-readiness

## Notes for AI Agents

- Focus on XML logic, mod integration, trait definition, faction mechanics, and RimWorld modding standards
- Avoid suggesting full rewrites; work within the RimWorld mod architecture unless absolutely necessary
- Modular development preferred: traits, events, jobs, gear logic, faction setups should be isolated
