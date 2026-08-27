# Meta Quest asset budgets

These are initial engineering budgets for the InterVerseSG standalone Quest build. They are guardrails, not absolute platform limits.

## Geometry

- Small prop: target <= 10k triangles at LOD0.
- Medium furniture/interactive prop: target <= 20k triangles at LOD0.
- Large architectural module: target <= 30k triangles at LOD0.
- Every repeated asset should provide at least LOD0, LOD1, and LOD2 or use a proven equivalent reduction strategy.
- Use simple collision primitives whenever possible.

## Materials and textures

- Prefer one material slot per small/medium asset.
- Prefer texture atlases for repeated furniture and architectural kits.
- Default texture ceiling: 1024 px for common props; 2048 px only where visual importance justifies it.
- Avoid expensive translucent materials unless required.
- Avoid per-object dynamic material complexity on large repeated sets.

## Runtime

- Prefer instanced static meshes for repeated chairs, trees, desks, and architectural modules.
- Prefer baked/static lighting where the design permits it.
- Avoid spawning large quantities in one frame; batch or stagger non-critical creation.
- Keep interactive collision and ticking disabled until needed.
- Profile on the standalone headset, not only PC VR.

## Asset acceptance

An asset is `quest_ready` only after:

1. scale and pivot are correct,
2. collision is verified,
3. material count is acceptable,
4. LOD strategy exists,
5. the asset has a local symbolic Blueprint mapping,
6. it has been tested in the target Quest scene.
