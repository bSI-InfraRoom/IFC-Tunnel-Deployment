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

1. [Product Relative Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-relative-positioning.htm) and [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm)
    1. The `IfcSite`  (defined in [Sprint 2.1](./sprint2_1.md)) should be placed using the above concepts:
        1. either along the `IfcAlignment` (defined in [Sprint 2.1](./sprint2_1.md)) 
        1. or relative to an `IfcReferent` (defined in [Sprint 2.1](./sprint2_1.md), which is nested according to [Sprint 2.2](./sprint2_2.md)). 
    - In other words: `IfcSite.ObjectPlacement.PlacementRelTo` shall point to `IfcSite.PositionedRelativeTo.RelatingPositioningElement.ObjectPlacement`.
1. [Product Geometric Representation](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-geometric-representation.htm)
    1. We encourage to provide examples for `IfcGeoScienceModel` (other `IfcElement` are allowed).
    1. Provide at least one of the listed alternatives for the [volumetric](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-geometry.htm) or [surfaic](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/surface-geometry.htm) representation:
        1. [Body Tesselation Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-tessellation-geometry.htm) or
        1. [Body Brep Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-brep-geometry.htm) or
        1. [Body SweptSolid Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-sweptsolid-geometry.htm) or
        1. [Body Surface Model Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-surfacemodel-geometry.htm) or
        1. Voxel Geometry - [in progress](https://github.com/bSI-InfraRoom/IFC-Specification/issues/524) or
        1. [Surface Tessellation Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/surface-tessellation-geometry.htm) with [`IfcTriangulatedIrregularNetwork`](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifctriangulatedirregularnetwork.htm).
1. [Property Sets with Override](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/property-sets-with-override.htm)
    1. The `IfcSite` shall have the property set [Pset_LandRegistration](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/pset_landregistration.htm) assigned with:
        1. the property `LandID` provided with non-empty value (the exact value is arbitrary),
        1. the property `IsPermanentID` provided with value `.T.` (i.e. `true`) and 
        1. the property `LandTitleID` provided with non-empty value (the exact value is arbitrary).
1. [Classification Association](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/classification-association.htm)
    1. At least one instance of `IfcProduct` shall be associated with an `IfcClassificationReference` where:
        1. `Identification` and `Name` shall exist, and
        1. `ReferencedSource` shall reference the `IfcClassification` occurrence associated with the `IfcProject` in [Sprint 1.2](./sprint1_2.md).

Optional usage in this sprint:

1. [Library Association](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/library-association.htm) (optional)
    1. The `Pset_LandRegistration` from above shall associate an `IfcLibraryReference` where:
        1. `Location` shall be a URI value pointing to the computer interpretable listing for the IFC 4.4 draft specification (you need to find it yourself in the specification),
        1. `Identification` being `"#3540"`, and
        1. `Name` being `"Pset_LandRegistration"`.

