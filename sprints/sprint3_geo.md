# Sprint 3.geo

This sprint implements and tests specific usages for *geotechnics*.


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


## Usages

This sprint encompasses the following usages:


### Book A

1. `IfcBorehole`
	1. Pset_SpatialGeoObsBorehole
	1. geometry?
	1. contained in `IfcSite`
1. `IfcGeoScienceObservation/BOREHOLELOG`
	1. AssignsToProduct to Borehole above
	1. Pset_GeoObsBoreholeCommon
	1. Pset_GeoObsBoreholeGeoLogInterval?
1. `IfcDatasetInformation`
	1. relate to `IfcGeoScienceObservation/BOREHOLELOG` above with `IfcRelAssociatesDataset`
	1. has to be declared by `IfcProject`

1. `IfcSpatialZone/MAPPEDZONE`
	1. Pset_SpatialGeoObsMappedZoneCommon
	1. geometry?
	1. aggregated in `IfcSite`
1. `IfcGeoScienceObservation/MAPPEDFEATURE`
	1. AssignsToProduct to SpatialZone above
	1. Pset_GeoObsMappedUnit
	1. declared to project?
1. `IfcGeoScienceObservation/LOCALINFORMATION`
	1. AssignsToProduct to SpatialZone above
	1. Pset_GeoObsPtObservationCommon
1. `IfcGeoScienceObservation/INSITUTESTRESULT`
	1. AssignsToProduct to SpatialZone above
	1. Pset_InSituTestCommon
1. `IfcGeoScienceObservation/LABTESTRESULT`
	1. AssignsToProduct to SpatialZone above
	1. Pset_LabTestCommon

1. `IfcGeoScienceObservation/GEOPHYSICALSURVEYRESULT`
	1. AssignsToProduct to ?? above
	1. Pset_GeophysicalSurveyCommon

### Book B

1. `IfcGeoScienceModel`
	1. Pset_GeoScienceModelCommon
	1. contained in `IfcSite`

1. `IfcGeoScienceFeature`
	1. aggregated in `IfcGeoScienceModel`
	1. at least one of:
		1. `PSYSICALPROPERTYDISTRIBUTION`
			1. Body geometry, e.g. Voxel geometry (with Voxel data)
			1. Pset_GeoScienceFeatureTypePropertyDistribution
		1. `GEOLOGICALUNIT`
			1. Body geometry, e.g. brep or voxel geometry
			1. Pset_GeoScienceFeatureTypeGeologicalUnit
		1. `FAULT`
			1. Body geometry, e.g. brep or voxel geometry
			1. Pset_GeoScienceFeatureTypeFault
		1. `CONTACT`
			1. Surface geometry
			1. Pset_GeoScienceFeatureTypeContact
		1. `GEOTECHNICALUNIT`
			1. Body geometry, e.g. brep or voxel geometry
			1. Pset_GeoScienceFeatureTypeGroundTypeDistribution
		1. `HAZARDAREA`
			1. Body geometry, e.g. brep or voxel geometry
			1. Pset_GeoScienceFeatureTypeGeoHazard

### Book C

1. `IfcTunnelTypicalSection/GEOTECH`
	1. Pset still in the makings
	1. contained in Tunnel
	1. [Product Span Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-span-positioning.htm)
