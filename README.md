# InterVerse Assets

Versioned 3D asset catalog for InterVerseSG.

This repository defines the approved asset vocabulary used by `interverse-builder` and `interverse-unreal`. Large binary source files should use Git LFS or external object storage; this repository keeps manifests, metadata, optimization rules, previews, and import guidance.

## Initial asset classes

- wall -> BP_WallBasic
- floor -> BP_FloorBasic
- door -> BP_DoorInteractive
- window -> BP_WindowBasic
- chair -> BP_FurnitureChair
- desk -> BP_FurnitureDesk
- screen -> BP_InteractiveScreen
- sign -> BP_SignInteractive
- tree -> BP_TreeOptimized
- light -> BP_LightOptimized
- navigation_point -> BP_NavigationPoint

## Meta Quest baseline

Assets are designed for standalone Meta Quest first. Prefer baked lighting, compact materials, LODs, texture atlases, simple collision, instancing, and aggressive draw-call control.

## Digital twin pipeline

Real-world captures will be processed separately, optimized, segmented, and only then registered here as approved campus assets. Raw video and photogrammetry captures should not be committed directly to GitHub.
