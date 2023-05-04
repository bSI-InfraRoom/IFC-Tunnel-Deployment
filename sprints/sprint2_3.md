# Sprint 2.3

This sprint implements and tests project structure specific usages.


## Prerequisities

This sprint assumes you completed the following sprints:

- [Sprint 1.1](./sprint1_1.md),
- [Sprint 1.2](./sprint1_2.md),
- [Sprint 1.3](./sprint1_3.md),
- [Sprint 2.1](./sprint2_1.md), and
- [Sprint 2.2](./sprint2_2.md).


## Duration

| Kick-off    | Submission  | Closure     |
|-------------|-------------|-------------|
| 2023.05.11. | 2023.05.29. | 2023.06.08. |


## Usages

This sprint encompasses the following usages:

- Linear Composition
    - in progress: https://github.com/bSI-InfraRoom/IFC-Specification/issues/523
- [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm)
    - All `IfcElement` instances which are linearly placed, shall be placed according to the [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm) concept template, i.e. `IfcReferent.ObjectPlacement.PlacementRelTo` shall point to `IfcReferent.PositionedRelativeTo.RelatingPositioningElement.ObjectPlacement`.
- [Body Tesselation Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-tessellation-geometry.htm)
    - on the example of `IfcGeoScienceModel` (other `IfcProduct` allowed)
- [Body Brep Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-brep-geometry.htm)
    - on the example of `IfcGeoScienceModel` (other `IfcProduct` allowed)
- Voxel Geometry
    - on the example of `IfcGeoScienceModel` (other `IfcProduct` allowed)
- [Library Association](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/library-association.htm) (optional)
