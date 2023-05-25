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


## Usages

This sprint encompasses the following usages:

1. Ports connectivity
1. Ports nesting
1. Port to Distribution system

Example on fire protection:

1. `IfcPipeSegment`
	1. contained in Tunnel
	1. body geometry, e.g. swept profile solid
1. `IfcPipeFitting`
	1. contained in Tunnel
	1. body geometry
1. `IfcSensor`
	1. contained in Tunnel
	1. body geometry
	1. `IfcRelFlowControlElements` to the sprinkler below
1. `IfcFireSuppressionTerminal/SPRINKLER`
	1. contained in Tunnel
	1. body geometry
1. `IfcDistributionPort`
	1. connected to other ports
	1. nested to elements above
1. `IfcDistributionSystem/FIREPROTECTION`
	1. declare in `IfcProject`
	1. group all elements above
