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

1. [Spatial Composition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-composition.htm)
    1. All `IfcTunnelPart` shall be aggregated in an `IfcTunnel` or `IfcTunnelPart`.
    1. All `IfcTunnel` shall be aggregated in either an `IfcTunnel`, `IfcSite` or `IfcProject`.
    1. All `IfcSite` shall be aggregated in `IfcProject`.
1. [Spatial Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-decomposition.htm)
    1. Each `IfcTunnel` may only be decomposed by `IfcTunnel` or `IfcTunnelPart`.
    1. There shall be at least one `IfcTunnel` in the file with non-empty `Name`.
1. Linear Composition
    1. There shall be one `IfcAlignment` in the file with non-empty `Name`.
1. [Alignment Layout](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/alignment-layout.htm)
    1. There shall be at least one `LINE`, at least one `CIRCULARARC` and at least one `CLOTHOID` segments nested in the horizontal layout (see `IfcAlignmentHorizontalSegment.PredefinedType`).
    1. There shall be at least one `CONSTANTGRADIENT` and either at least one `CIRCULARARC` or at least one `PARABOLICARC` segments nested in the vertical layout (see `IfcAlignmentVerticalSegment.PredefinedType`).
1. [Object Nesting](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/object-nesting.htm)
    1. There shall be at least one `IfcReferent` on `IfcAlignment` with non-empty `Name`.
    1. All `IfcReferent` shall be nested in any `IfcAlignment`. The `IfcRelNests` relationship nesting instances of `IfcReferent` shall only nest instances of `IfcReferent` (see https://github.com/bSI-InfraRoom/IFC-Tunnel-Deployment/issues/112).
1. [Group Assignment](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/group-assignment.htm)
    1. There shall be at least one `IfcGroup` (or any of the subtypes) declared in `IfcProject` with at least one element grouped.
