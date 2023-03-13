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
- [Product Linear Placement](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-linear-placement.htm)
- [Element Nesting](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-nesting.htm)
    - only for `IfcReferent`
