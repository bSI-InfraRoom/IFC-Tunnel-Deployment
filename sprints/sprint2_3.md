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

- [Product Relative Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-relative-positioning.htm) and [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm)
    - The `IfcSite`  (defined in [Sprint 2.1](./sprint2_1.md)) should be placed using the above concepts:
        - either along the `IfcAlignment` (defined in [Sprint 2.1](./sprint2_1.md)) 
        - or relative to an `IfcReferent` (defined in [Sprint 2.1](./sprint2_1.md), which is nested according to [Sprint 2.2](./sprint2_2.md)). 
    - In other words: `IfcElement.ObjectPlacement.PlacementRelTo` shall point to `IfcElement.PositionedRelativeTo.RelatingPositioningElement.ObjectPlacement`.
- [Product Geometric Representation](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-geometric-representation.htm)
    - We encourage to provide examples for `IfcGeoScienceModel` (other `IfcElement` are allowed).
    - Provide at least one of the listed alternatives for the [volumetric](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-geometry.htm) or [surfaic](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/surface-geometry.htm) representation:
        - [Body Tesselation Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-tessellation-geometry.htm) or
        - [Body Brep Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-brep-geometry.htm) or
        - [Body Surface Model Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-surfacemodel-geometry.htm) or
        - Voxel Geometry - [in progress](https://github.com/bSI-InfraRoom/IFC-Specification/issues/524) or
        - [Surface Tessellation Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/surface-tessellation-geometry.htm) with [`IfcTriangulatedIrregularNetwork`](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifctriangulatedirregularnetwork.htm).
- [Property Sets with Override](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/property-sets-with-override.htm)
    - The `IfcSite` shall have the property set [Pset_LandRegistration](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/pset_landregistration.htm) assigned with:
        - the property `LandId` provided (the value is arbitrary),
        - the property `IsPermanentId` provided with value `.T.` (i.e. `true`) and 
        - the property `LandTitleId`.
- [Library Association](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/library-association.htm) (optional)
    - The `Pset_LandRegistration` from above shall associate an `IfcLibraryReference` where:
        - `Location` shall be a URI value pointing to the computer interpretable listing for the IFC 4.4 draft specification (you need to find it yourself in the specification),
        - `Identification` being `"#3540"`, and
        - `Name` being `"Pset_LandRegistration"`.
- [Classification Association](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/classification-association.htm)
    - At least one instance of `IfcProdcut` shall be associated with an `IfcClassificationReference` where:
      - `Identification` and `Name` shall exist, and
      - `ReferencedSource` shall reference the `IfcClassification` occurrence associated with the `IfcProject` in [Sprint 1.2](./sprint1_2.md).

