# Sprint 3.sys

This sprint implements and tests specific usages for *systems*.


## Prerequisities

This sprint assumes you completed the following sprints:

- [Sprint 1.1](./sprint1_1.md),
- [Sprint 1.2](./sprint1_2.md),
- [Sprint 1.3](./sprint1_3.md),
- [Sprint 2.1](./sprint2_1.md),
- [Sprint 2.2](./sprint2_2.md), and
- [Sprint 2.3](./sprint2_3.md).


## Duration

| Kick-off    | Submission  | Closure     |
|-------------|-------------|-------------|
| 2023.06.15. | 2023.08.15. | 2023.08.31. |


## Concepts

### New concepts

1. [Spatial containment](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-containment.htm)
1. [Port connectivity](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/port-connectivity.htm)
1. [Port nesting](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/port-nesting.htm)
1. [Port to Distribution system](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/port-to-distribution-system.htm)
1. [Control flow](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/control-flow.htm)

### Additional geometries

1. [Body SweptSolid Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-sweptsolid-geometry.htm)
1. [Body AdvancedSwept DiskSolid Polycurve Geometry](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-advancedswept-disksolid-polycurve-geometry.htm)


## Usages

This sprint encompasses the following usages:

### Example on fire protection

1. `IfcPipeSegment`
	1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md)
	1. [body geometry](./sprint2_3.md), e.g. see geometry concepts listed [here](#additional-geometries), or any volumetric representation from [sprint 2.3](./sprint2_3.md)
	1. [local placement](./sprint2_2.md)
	1. [nesting ports](#new-concepts): see also Table 599 [here](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifcpipesegment.htm)
	1. [properties](./sprint2_3.md) with `Pset_PipeSegmentTypeCommon`
1. `IfcPipeFitting`
	1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md)
	1. [body geometry](./sprint2_3.md)
	1. [local placement](./sprint2_2.md)
	1. [properties](./sprint2_3.md) with `Pset_PipeFittingTypeCommon`
	1. [nesting ports](#new-concepts): see also Table 594 [here](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifcpipefitting.htm)
1. `IfcFireSuppressionTerminal/SPRINKLER`
	1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md)
	1. [body geometry](./sprint2_3.md)
	1. [local placement](./sprint2_2.md)
	1. [nesting ports](#new-concepts): see also Table 640 [here](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifcfiresuppressionterminal.htm)
1. `IfcSensor`
	1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md)
	1. [body geometry](./sprint2_3.md)
	1. [local placement](./sprint2_2.md)
	1. [nesting ports](#new-concepts): see also Table 318 [here](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifcsensor.htm)
	1. [flow control](#new-concepts) to the `IfcFireSuppressionTerminal/SPRINKLER` above: see also Table 319 [here](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifcsensor.htm)
1. `IfcDistributionPort`
	1. [connected](#new-concepts) to other `IfcDistributionPort`
		1. one side shall be `SOURCE` and the other a `SINK` as [per documentation](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifcdistributionport.htm)
	1. [nested](#new-concepts) to all elements listed above
	1. no [geometry](./sprint2_3.md)
	1. no [containment](#new-concepts)
	1. [properties](./sprint2_3.md) with `Pset_DistributionPortTypePipe`
1. `IfcDistributionSystem/FIREPROTECTION`
	1. [declared](./sprint1_1.md) in `IfcProject`
	1. [groups](./sprint2_1.md) all elements listed above

### Other example

You don't have fire protection support capabilities within your suite?
If you have a different `IfcSystem` that is more easily supported with your software suite,
 please come forward at the support meetings or contact us per email.
We will try to come up with (tunnel specific) instructions for your example.
