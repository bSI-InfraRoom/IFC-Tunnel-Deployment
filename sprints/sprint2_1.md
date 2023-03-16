# Sprint 2.1

This sprint implements and tests project structure specific usages.


## Prerequisities

This sprint assumes you completed the following sprints:

- [Sprint 1.1](./sprint1_1.md),
- [Sprint 1.2](./sprint1_2.md), and
- [Sprint 1.3](./sprint1_3.md).


## Duration

| Kick-off    | Submission  | Closure     |
|-------------|-------------|-------------|
| 2023.03.16. | 2023.04.03. | 2023.04.13. |


## Usages

This sprint encompasses the following usages:

- [Spatial Composition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-composition.htm)
    - All `IfcTunnelPart` shall be aggregated in an `IfcTunnel` or `IfcTunnelPart`.
    - All `IfcTunnel` shall be aggregated in either an `IfcTunnel`, `IfcSite` or `IfcProject`.
    - All `IfcSite` shall be aggregated in `IfcProject`.
- [Spatial Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-decomposition.htm)
    - Each `IfcTunnel` may only be decomposed by `IfcTunnel` or `IfcTunnelPart`.
    - There shall be at least one `IfcTunnel` in the file with non-empty `Name`.
- Linear Composition
    - in progress: https://github.com/bSI-InfraRoom/IFC-Specification/issues/523
    - There shall be one `IfcAlignment` in the file with non-empty `Name`.
- [Alignment Layout](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/alignment-layout.htm)
    - There shall be at least one `LINE`, at least one `CIRCULARARC` and at least one `CLOTHOID` segments nested in the horizontal layout (see `IfcAlignmentHorizontalSegment.PredefinedType`).
    - There shall be at least one `CONSTANTGRADIENT` and either at least one `CIRCULARARC` or at least one `PARABOLICARC` segments nested in the vertical layout (see `IfcAlignmentVerticalSegment.PredefinedType`).
- [Object Nesting](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/object-nesting.htm)
    - There shall be at least one `IfcReferent` on `IfcAlignment` with non-empty `Name`.
    - All `IfcReferent` shall be nested in any `IfcAlignment`.
- [Group Assignment](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/group-assignment.htm)
    - There shall be at least one `IfcGroup` (or any of the subtypes) in the file with at least one element grouped.
