---
layout: ../../layouts/CaseStudy.astro
title: Emergent behavior in a city evacuation
category: Simulation engineering · UCLA Artificial Life
summary: A Unity simulation in which civilians evacuate, defenders coordinate, and predators pursue—combining shared navigation with local agent behavior.
role: Primary simulation developer
period: 2026
team: Four-person course project
tools: [Unity, C#, Dijkstra flow fields, Spatial hashing, Steering behaviors, Finite state machines]
evidence:
  - label: Source code
    url: https://github.com/jehfoori/275-project
  - label: Project report · PDF
    url: /reports/evacuation.pdf
  - label: Existing video recordings
    url: https://github.com/jehfoori/275-project/tree/main/docs/video
note: "Team: Jeffrey Huang, Hongyi Jin, Krish Patel, and Aaron Zhao. I led the simulation implementation; teammates contributed to the report, presentation, and HTML write-up."
---

## Building the simulation

For our artificial life project, I built the Unity simulation, including its scripts, scene setup, and work with 3D assets. My teammates helped develop the report, presentation, and HTML write-up.

The simulation places civilians, soldiers, and large predators in a bounded city. Civilians move through the streets and flee toward exits. Soldiers respond to threats and can rally before engaging. Predators wander, pursue, and attack nearby prey.

<figure><img src="/images/navigation-graph.png" alt="The simulation city with its waypoint graph and obstacle boundaries visible" loading="lazy" /><figcaption>The city navigation graph connects walkable locations while accounting for buildings and walls.</figcaption></figure>

## Shared routes, individual decisions

Evacuation routes use a precomputed Dijkstra flow field over the waypoint network. Each node records its cost to an exit and the next node along that route, so agents can share navigation information rather than independently solving the same route problem.

Local behavior can override that route. A civilian near a predator prioritizes fleeing, then resumes evacuation routing after escaping the immediate threat. Steering combines path following with separation, alignment, cohesion, wandering, and obstacle avoidance.

<figure><img src="/images/evacuation-flow-field.png" alt="Arrows showing evacuation routes through the city toward exit gates" loading="lazy" /><figcaption>A visualization of the shared evacuation flow field.</figcaption></figure>

## Coordinating agents and spatial queries

Agent state machines govern civilian evacuation, soldier patrol and rally behavior, and predator pursuit. Stress and fatigue modify movement and behavior, while panic can spread through nearby civilians.

A spatial hash grid narrows neighborhood searches for flocking, threat detection, and panic propagation. This avoids checking every agent against every other agent in typical dispersed scenes; performance still depends on population density and query ranges.

## Exploring the resulting behavior

The report compares no defense, naive defense, and rally-based defense using three runs per configuration. In those runs, civilian survival was 75.6% with naive defense and 79.7% with rally defense. Soldier survival was unchanged at 17.6%.

These are exploratory results from a small set of runs. They illustrate how local rules, spawn placement, and navigation interact; they do not establish a general improvement in evacuation safety or combat effectiveness.

The project’s main contribution is the implemented system: a shared environment where navigation, agent state, and local interactions produce observable group behavior. Existing recordings, screenshots, and the report document it alongside the source code.
