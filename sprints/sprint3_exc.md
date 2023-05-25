# Sprint 3.exc

This sprint implements and tests specific usages for *excavation, lining and support*.


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

### Excavation

1. `IfcGeoScienceModel` 
	1. mock a simple aggregated `IfcGeoScienceFeature/GEOTECHNICALUNIT`
1. `IfcFeatureElementSubtraction`
	1. `IfcRelVoidsElements` of `IfcGeoScienceModel` above

1. `IfcUndergroundExcavation`
	1. Pset_ExcavationCommon
	1. geometry: SectionedSolid together with GuideCurves?
		1. body representation
		1. curve set representation
1. `IfcEarthworksCut`
	1. Pset_EarthworksCutCommon

### Waterproofing

1. `IfcBuiltSystem/WATERPROOFING`
	1. Pset_BuiltSystemTypeWaterproofing
	1. declared by `IfcProject`
	1. groups the covering and zone below
1. `IfcCovering/MEMBRANE`
	1. Pset_CoveringTypeMembrane
	1. body or surface geometry
	1. contained in tunnel
	1. material layer set
1. `IfcDiscreteAccessory/WATER_BARRIER`
	1. Pset_DiscreteAccessoryTypeWaterBarrier
	1. aggregated in covering?
1. `IfcSpatialZone/COMPARTMENT`
	1. Pset_SpatialYoneTypeCompartment
	1. body geometry
	1. aggregated in tunnel

### Presupport

1. 

### Support

### Lining

1. `IfcTunnelTypicalSection/EXCAVATIONSUPPORT`

