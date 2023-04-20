# Sprint 2.2

This sprint implements and tests project structure specific usages.


## Prerequisities

This sprint assumes you completed the following sprints:

- [Sprint 1.1](./sprint1_1.md),
- [Sprint 1.2](./sprint1_2.md),
- [Sprint 1.3](./sprint1_3.md), and
- [Sprint 2.1](./sprint2_1.md).


## Duration

| Kick-off    | Submission  | Closure     |
|-------------|-------------|-------------|
| 2023.04.13. | 2023.05.02. | 2023.05.11. |


## Usages

This sprint encompasses the following usages:

- [Product Local Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-local-placement.htm)
    - The `IfcTunnelPart.ObjectPlacement.PlacementRelTo` shall point to the `IfcTunnelPart.Decomposes.RelatingObject.ObjectPlacement` (i.e., the `IfcTunnel` or `IfcTunnelPart` it is part of).
    - If `IfcTunnel` is aggregated in `IfcSite` or `IfcTunnel`, then the `IfcTunnel.ObjectPlacement.PlacementRelTo` shall point to the `IfcTunnel.Decomposes.RelatingObject.ObjectPlacement` (i.e., the `IfcSite` or `IfcTunnel` it is part of).
- [Alignment Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/alignment-geometry.htm)
    - Any `IfcAlignment` nested by only an `IfcAligmentHorizontal` and an `IfcAlignmentVertical` shall be represented according to concept template [Alignment Geometry Gradient](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/alignment-geometry-gradient.htm):
        - `RepresentationIdentifier = 'Axis'`
        - `RepresentationType = 'Curve3D'`
        - representation is `IfcGradientCurve`
    - Any `IfcAlignment` nested by an `IfcAligmentHorizontal` and an `IfcAlignmentVertical` and an `IfcAlignmentCant` shall be represented according to concept template [Alignment Geometry Cant](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/alignment-geometry-cant.htm):
        - `RepresentationIdentifier = 'Axis'`
        - `RepresentationType = 'Curve3D'`
        - representation is `IfcSegmentedReferenceCurve`
    - All `IfcAlignment` instances shall have an additional 2D representation (documentation):
        - `RepresentationIdentifier = 'Axis'`
        - `RepresentationType = 'Curve2D'`
        - representation is `IfcCompositeCurve` (the same instance used as `IfcGradientCurve.BaseCurve` or `IfcSegmentedReferenceCurve.BaseCurve.BaseCurve` above),
- [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm)
    - All `IfcReferent` instances shall be linearly placed according to the [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm) concept template (i.e. `IfcReferent.ObjectPlacement.PlacementRelTo` shall point to `IfcReferent.PositionedRelativeTo.RelatingPositioningElement.ObjectPlacement`).
- [Element Nesting](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-nesting.htm)
    - All `IfcReferent` instances shall be linearly placed according to the [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm) concept template:
        - `IfcReferent.ObjectPlacement` shall be `IfcLinearPlacement`.
        - `IfcReferent.ObjectPlacement.PlacementRelTo` shall point to `IfcReferent.Nests.RelatingObject.ObjectPlacement`.
- [Linear Composition](https://github.com/bSI-InfraRoom/IFC-Specification/pull/557)
    - All `IfcAlignment` instances shall be aggregated in `IfcProject`. It shall use its own `IfcRelAggregates` instance and not share it with the [Spatial Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-decomposition.htm) usage from Sprint 1.2.

