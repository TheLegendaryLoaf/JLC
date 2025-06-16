

# Cadia Military Framework - RimWorld Total Conversion

## Overview
This project transforms RimWorld into a comprehensive military civilization inspired by Cadia and the Helldivers universe. The framework aims to create a realistic multi-colony empire featuring psychological conditioning, physical training, structured hierarchies, authentic military logistics, and **intelligent AI-driven military behavior**. The system emphasizes realism, immersion, and player-driven control of recruitment, training, combat operations, and supply chain management with autonomous military decision-making.

## Core Objectives

-   **Multi-Colony Military Network**: Establish specialized facilities (bootcamp, supply depots, manufacturing centers, forward operating bases) across multiple world tiles.
-   **Comprehensive Bootcamp System**: Transform civilian pawns into disciplined soldiers through psychological conditioning, physical training, and military indoctrination.
-   **Authentic Military Hierarchy**: Implement USMC-inspired rank structure with unique names fitting the setting, complete with promotion ceremonies and chain-of-command dynamics.
-   **Intelligent Military AI**: Officers and specialists who think strategically, coordinate tactics, and execute military doctrine autonomously.
-   **Inter-Colony Logistics**: Automated supply runs, equipment transfers, and personnel rotations between facilities using scheduled vehicle convoys.
-   **Specialized Military Roles**: Deep specialization system from basic infantry to advanced technical roles (Rifleman, Medic, Squad Leader, Drone Operator, Heavy Weapons Specialist).
-   **Psychological Realism**: Create "Field Rat" conditioning that makes soldiers enjoy spartan conditions, military discipline, and combat environments that would break civilians.

## Revolutionary Features

### Psychological Conditioning System
-   **Trait Evolution**: Pawns undergo fundamental personality changes during training - removing civilian weaknesses (Greedy, Jealous, Neurotic) and gaining military strengths (Disciplined, Field Hardened, Unit Loyalty).
-   **Field Rat Development**: Soldiers gain preferences for MREs, military cots, outdoor conditions, and high-stress environments.
-   **Mental Resilience**: Graduated soldiers become immune to mood penalties that affect civilians, with bonuses for military structure and unit cohesion.

### Physical Enhancement Framework (Strength, Fitness, Discipline Skills)
-   **Strength Skill**: Influences melee combat effectiveness, construction capabilities, and equipment handling (e.g., carry capacity, mining speed).
-   **Fitness Skill**: Affects movement speed, endurance during extended operations, and recovery (e.g., global work speed, rest need rate).
-   **Discipline Skill**: Controls mental break resistance, order-following behavior, and stress management under fire.

### Advanced Military Hierarchy with Intelligent AI
-   **Rank-Based Progression**: From Recruit through specialized career tracks (Infantry, Medical, Technical, Leadership).
-   **Strategic Command AI**: Officers who make autonomous decisions about base defense, patrol routes, and resource allocation.
-   **Tactical Squad Leaders**: NCOs who coordinate fireteams with real tactical awareness and adaptive combat strategies.
-   **Chain of Command Dynamics**: Higher-ranked pawns influence lower ranks through enhanced job priorities and AI-driven military protocols.
-   **Specialty AI Behaviors**: Role-specific intelligence for medics, engineers, and specialists who prioritize their military functions.

### Military Training and Doctrine System
-   **Drill Sergeant AI**: Bootcamp instructors who autonomously run training programs, bark orders, coordinate drills, and evaluate recruit progress.
-   **Specialized Training Activities**: Includes physical training (PT) exercises with specific designated spots.
-   **Combat Doctrine Implementation**: AI-driven tactical behaviors based on military training and rank structure.
-   **Autonomous Military Operations**: Patrols, guard duties, and tactical responses executed without constant player micromanagement.

### Instinctive "Talents" Perk System (Automatic Acquisition)
-   **Specific Proficiencies**: Pawns automatically gain specialized "talents" (perks) that represent ingrained training and conditioned responses, such as "Rifle Expertise," "Advanced Grenadier," or "Combat Reflexes."
-   **Tree-Based Progression**: Talents are organized in a progression tree, requiring previous talents, specific skill levels (Strength, Fitness, Discipline, Shooting, etc.), and **achievements** (e.g., specific kill counts, raids survived).
-   **Job-Specific Requirements**: Advanced talents will require completion of **specific military training jobs** (e.g., a "Rifle Drill" job, "Tactical Maneuver" job) or accumulated time spent in certain military `WorkTypes`.
-   **Backstory Restrictions**: Elite or unique talents can be gated behind **specific pawn backstories** (e.g., "Spec Ops Veteran," "Ex-Mercenary"), ensuring certain pawns have an inherent aptitude for advanced roles.
-   **No Perk Points**: Talents are automatically acquired the moment all prerequisites are met, simulating true instinctual learning.

## Implementation Strategy & Technical Approach

This project focuses on leveraging and extending existing, robust RimWorld mod frameworks and direct C# modding to achieve complex AI behaviors and systems, without relying on Large/Small Language Models (LLMs/SLMs) for core pawn decision-making. This approach is key to achieving sophisticated military simulation while managing development complexity.

### Phase 1: Foundation Systems
-   **Leverage JecsTools and Community Framework** for advanced trait evolution and psychological conditioning.
-   **Extend Toughness Mod framework** to implement Strength, Fitness, and Discipline skills, and hook them into core pawn stats and existing gameplay.
-   **Custom "PT Spot" & "Perform PT" Job**: Define a new buildable "PT Spot" `ThingDef` (e.g., Exercise Mat) and a custom C# `JobDriver_PerformPT`. This job will have pawns go to the spot, perform exercises (with planned custom animations), and gain XP in Strength and Fitness.
-   **Integrate "Schedule Everything!"**: Define a new "Physical Training" `WorkTypeDef` in XML. This will allow players to easily schedule dedicated PT hours using the "Schedule Everything!" mod for automated pawn assignment.
-   **Initial Military Traits**: Implement basic C# logic to apply initial military traits.
-   **Foundational Military Pawn AI (Individual Soldier)**: Develop custom C# `JobGivers` and `ThinkNodes` for a generic "Soldier" role, focusing on essential behaviors like patrolling, guard duty, basic cover usage, and target engagement.

### Phase 2: Training Pipeline with Intelligent Instructors
-   **Modify Miscellaneous Training and Simple Education** to create structured bootcamp progression.
-   **Implement AI-driven Drill Sergeants**: Via custom C# `ThinkNodes`, these pawns will oversee and manage pawn assignments to "Physical Training" jobs (and other future training jobs), providing bonuses and evaluating recruit progress.
-   **Talents System (Basic Acquisition)**: Implement the core C# `Pawn_TalentTracker` that automatically checks for and applies talents based on initial skill, trait, and basic job completion requirements. Unlocked talents will apply their effects via specific `Hediffs`.
-   **Create trait removal/addition events** triggered by training milestones and instructor assessments.
-   **Develop custom military traits** that override civilian mood penalties and integrate with AI behavior.

### Phase 3: Logistics and Tactical Operations
-   **Utilize Vehicle Framework and Better Pawn Control** for automated supply convoy systems.
-   **Integrate Combat Extended equipment systems** with rank-based loadout assignments and AI tactical preferences.
-   **Develop multi-colony coordination** using faction mechanics, scheduled events, and custom C# strategic AI command decisions.
-   **Implement intelligent patrol systems** with AI-driven route planning and threat assessment.

### Phase 4: Advanced Military Intelligence & Specialization
-   **Advanced Talents Implementation**: Expand the "Talents" system with C# logic to incorporate more complex requirements like kill counts, raid survival, specific job durations, and backstory checks. Implement sophisticated effects via Harmony patching for fine-grained control over pawn behavior (e.g., faster reactions, optimal cover selection for specific situations, weapon-specific handling).
-   **Semi-autonomous Squad Behaviors**: Through integrated custom C# AI and Colony Survival Logic, implement advanced tactical behaviors for fireteams and platoons.
-   **Strategic Command AI**: Via global C# scripts, implement high-level military decision-making for base-level strategy, resource prioritization, and response to external threats.
-   **Advanced equipment systems** using Exosuit Framework for specialized roles with role-specific AI.
-   **Performance optimization** for 100+ total pawns with complex AI behaviors distributed across multiple colonies.

## Technical Architecture

### Core Mod Dependencies
-   **JecsTools** - Foundation for custom abilities and advanced trait systems.
-   **Community Framework** - Complex pawn behavior modification and psychological conditioning.
-   **Dead Man's Switch Suite** - Advanced AI behaviors and military unit mechanics (will be verified for LLM-agnostic implementation).
-   **Combat Extended** - Realistic combat mechanics and equipment systems.
-   **Vehicle Framework** - Inter-colony transport and logistics.
-   **Vanilla Traits Expanded** - Base trait system for military personality development.
-   **Toughness** - Framework for implementing custom Strength, Fitness, and Discipline skills.
-   **[FSF] Simple Education** - For structured skill learning and basic education (for some skills).
-   **Children, school and learning** - If the project includes childhood development impacting military suitability.
-   **Schedule Everything!** - For player-driven scheduling of military duties and training activities.
-   **[1.5-1.4] CAI 5000 - Advanced AI + Fog Of War** - To provide highly challenging and tactical enemy AI, acting as a benchmark and opponent for your advanced military.

### AI Integration Strategy
-   **Custom Behavior Trees (C#)**: Implement military doctrine-based decision trees directly in C# using RimWorld's ThinkTree and JobGiver systems.
-   **Role-Specific Intelligence**: Different AI behaviors for officers, NCOs, specialists, and enlisted personnel defined in C#.
-   **Chain of Command Logic**: Higher ranks can override lower-rank AI decisions through C# defined behavior hierarchies.
-   **Tactical Coordination**: Squad-based AI developed in C# that enables authentic fireteam and platoon-level coordination.
-   **Talent System (Hediff & Harmony-based)**: Talents apply optimized effects via custom `HediffComp`s for stat modification and Harmony patches for direct behavioral overrides, triggered automatically upon meeting prerequisites.

### Performance Considerations
-   **Maximum 50 pawns per map** to maintain stability with complex AI behaviors.
-   **Distributed AI processing** across specialized facility maps.
-   **Automated systems** to reduce micromanagement overhead while maintaining intelligent responses.
-   **Performance optimization mods** integrated for large-scale operations with multiple AI agents.
-   **Event-driven Talent Checks**: Optimize talent acquisition by only checking for unlocks on specific triggers (skill level up, job completion, certain combat events) rather than every tick.

## Long-Term Vision

### Operational Empire with Intelligent Command
-   **Recruitment Centers**: Continuous intake and processing with AI-driven evaluation systems.
-   **Training Facilities**: Specialized bootcamps with autonomous drill instructors and adaptive training programs.
-   **Manufacturing Hubs**: Automated production with AI logistics coordination.
-   **Forward Bases**: Combat-ready outposts with intelligent defensive AI and patrol coordination.
-   **Strategic Command Structure**: AI-assisted coordination between all facilities with autonomous decision-making.

### Realistic Military Culture with Intelligent Actors
-   **Pawns who genuinely prefer military life** over civilian comfort through psychological conditioning.
-   **Natural adaptation to harsh conditions** and high-stress environments with AI-driven resilience.
-   **Unit loyalty and esprit de corps** that affects AI decision-making and combat effectiveness.
-   **Career progression** that creates meaningful specialization, expertise, and corresponding AI behaviors.

### Strategic Gameplay with Autonomous Operations
-   **Resource allocation** between expansion, training, and equipment with AI advisory systems.
-   **Tactical decision-making** for colony placement and specialization with intelligent recommendations.
-   **Long-term planning** for recruitment, training pipelines, and operational readiness with AI-driven forecasting.
-   **Emergent storytelling** through military campaigns, unit histories, and AI-driven character development.

## Development Philosophy
-   **Modification over Creation**: Extend and patch existing robust mods rather than building systems from scratch.
-   **Psychological Realism**: Simulate actual military conditioning and adaptation processes with authentic AI behaviors.
-   **Intelligent Automation**: Use custom C# AI to create autonomous military behaviors that reduce micromanagement.
-   **Modular Design**: Independent systems that can be developed and tested separately.
-   **Performance Conscious**: Scalable architecture that maintains game stability even with complex AI.
-   **Authentic Military Experience**: Draw from real military structure, training, culture, and decision-making processes.

## Notes for Implementation
-   **Focus on XML-based trait definitions** and event systems where possible, with C# for complex AI behaviors.
-   **Utilize existing mod frameworks** (JecsTools, Community Framework) for general utilities and pawn modification.
-   **Maintain compatibility** with Combat Extended and Vehicle Framework ecosystems.
-   **Design for gradual rollout** - each phase should be playable independently.
-   **Prioritize psychological conditioning and AI systems** as the foundation for all other features.
-   **Test AI performance carefully** - custom AI behaviors can be computationally expensive at scale.

## Key AI Enhancements
-   **Drill Sergeants**: Autonomous bootcamp management, recruit evaluation, and training coordination.
-   **Squad Leaders**: Real-time tactical coordination, cover usage, and fireteam command.
-   **Officers**: Strategic base management, resource allocation, and long-term planning.
-   **Specialists**: Role-prioritized behavior for medics, engineers, and technical personnel.
-   **Integrated Command**: Chain of command that actually functions through AI behavior hierarchies.

---

*"The planet broke before the Guard did."*

*And now the Guard thinks for itself.*
