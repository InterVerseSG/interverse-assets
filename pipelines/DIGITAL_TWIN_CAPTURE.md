# Digital twin capture pipeline

## Goal

Convert a real campus area into an optimized, navigable InterVerseSG environment for Meta Quest.

## 1. Capture planning

Start with one small pilot area, not the whole campus. Recommended first target: entrance + reception + one hallway + one classroom.

Capture requirements:

- stable, slow movement,
- strong image overlap,
- consistent exposure and lighting,
- avoid crowds and moving vehicles when possible,
- capture walls, corners, ceilings, doors, floors, signs, and transition areas from multiple viewpoints,
- take supplemental still photographs for surfaces that video does not capture cleanly.

A phone capable of high-quality 4K capture is sufficient for the pilot. A LiDAR-capable device or dedicated scanner can improve geometry but is not required to begin.

## 2. Processing options

Approved experiment tracks:

### Photogrammetry
Produces a textured mesh. Best when the environment must become conventional Unreal geometry and collision.

### Gaussian Splatting
Produces highly realistic view-dependent reconstruction. Excellent for visual fidelity, but standalone Quest integration requires careful performance testing and may need conversion, streaming, or a simplified proxy environment for interaction/collision.

For the first Quest MVP, prefer an optimized photogrammetry mesh or a hybrid: splat for visual reference plus simplified Unreal geometry for navigation and collision.

## 3. Cleanup

Before registration:

- remove floating geometry and capture artifacts,
- close important holes,
- simplify inaccessible geometry,
- separate major architectural zones,
- create clean collision proxies,
- correct scale to centimeters for Unreal,
- orient world axes consistently,
- reduce polygon count,
- bake high-detail appearance into optimized textures when practical,
- generate LODs.

## 4. Segment the environment

Do not import an entire campus as one object. Recommended segmentation:

- exterior_ground,
- exterior_building_shell,
- entrance,
- reception,
- hallway_north,
- classroom_101,
- furniture_static,
- signage,
- vegetation.

This supports occlusion, selective loading, optimization, and future updates.

## 5. Register approved assets

Every final segment receives metadata:

- asset id,
- human-readable name,
- campus zone,
- source/capture date,
- processing method,
- scale verified,
- collision status,
- triangle count,
- material slots,
- texture resolution,
- LOD status,
- Quest test status.

Only assets marked `quest_ready=true` enter the production registry.

## 6. Unreal integration

The final environment is imported into `interverse-unreal`, then local Blueprint/Data Asset references are registered. Network commands never point directly to arbitrary asset paths.

## First milestone

A Quest user should be able to:

1. enter the captured area,
2. walk or teleport through it,
3. reach `NAV_Classroom101`,
4. interact with one door,
5. interact with one screen,
6. maintain acceptable standalone Quest performance.
