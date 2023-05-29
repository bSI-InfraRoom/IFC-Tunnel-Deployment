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
2. [Product Assignment](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-assignment.htm)
3. Dataset Association (new CT needed!)
   1. IfcObjectDefinition=>IfcRelAssociatesDataset=>IfcDatasetReference

4. [Element Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-decomposition.htm)
5. [Element Composition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-composition.htm)
6. [Product Span Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-span-positioning.htm)


## Usages

This sprint encompasses the following usages:


### Book A

1. `IfcBorehole`
   1. [contained](#new-concepts) in `IfcSite`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_SpatialGeoObsBorehole`

1. `IfcGeoScienceObservation/BOREHOLELOG`
   1. [assigned](#new-concepts) `IfcBorehole` above
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. [properties](./sprint2_3.md) with `Pset_GeoObsBoreholeGeoLogInterval`
1. `IfcDatasetInformation`
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. [associated](#new-concepts) to `IfcGeoScienceObservation/BOREHOLELOG`

1. `IfcSpatialZone/MAPPEDZONE`
   1. [aggregated](#new-concepts) in `IfcSite`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_SpatialGeoObsMappedZoneCommon`

1. `IfcGeoScienceObservation/MAPPEDFEATURE`
   1. [assigned](#new-concepts) `IfcSpatialZone/MAPPEDZONE` above
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_GeoObsMappedUnit`

1. `IfcGeoScienceObservation/LOCALINFORMATION`
   1. [assigned](#new-concepts) `IfcSpatialZone/MAPPEDZONE` above
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_GeoObsPtObservationCommon`

1. `IfcGeoScienceObservation/INSITUTESTRESULT`
   1. [assigned](#new-concepts) `IfcSpatialZone/MAPPEDZONE` above
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_InSituTestCommon`

1. `IfcGeoScienceObservation/LABTESTRESULT`
   1. [assigned](#new-concepts) `IfcSpatialZone/MAPPEDZONE` above
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_LabTestCommon`

1. `IfcGeoScienceObservation/GEOPHYSICALSURVEYRESULT`
   1. [assigned](#new-concepts) `IfcSpatialZone/MAPPEDZONE` above
   1. [declared](./sprint1_1.md) in `IfcProject`
   1. Geometry?
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_GeophysicalSurveyCommon`



### Book B

1. `IfcGeoScienceModel/GEOTECHMODEL` (PredefinedType depending on decomposition!)
   1. [contained](#new-concepts) in `IfcSite`
   1. [decomposed by](#new-concepts) `IfcGeoScienceFeature/*` below
   1. [local placement](./sprint2_2.md)
   1. [properties](./sprint2_3.md) with `Pset_GeoScienceModelCommon`

1. `IfcGeoScienceFeature`
   1. [part of](#new-concepts) `IfcGeoScienceModel/GEOTECHMODEL`
   1. PredefinedType - at least one of:

   1. `PHYSICALPROPERTYDISTRIBUTION`
        	  1. [body geometry](./sprint2_3.md) 
                	     1. If geometry = IfcVoxelGrid an associated instance of IfcVoxelData (new CT!) is required
        	  2. [local placement](./sprint2_2.md)
        	  3. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypePropertyDistribution`
   1. `GEOLOGICALUNIT`
        	  1. [body geometry](./sprint2_3.md) 
                	     1. If geometry = IfcVoxelGrid an associated instance of IfcVoxelData (new CT!) is required
        	  2. [local placement](./sprint2_2.md)
        	  3. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeGeologicalUnit`
   1. `FAULT`
      1. [body geometry](./sprint2_3.md) 
         1. If geometry = IfcVoxelGrid an associated instance of IfcVoxelData (new CT!) is required

      1. [local placement](./sprint2_2.md)
      1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeFault`

   1. `CONTACT`
      1. [surface geometry](./sprint2_3.md) 
      2. [local placement](./sprint2_2.md)
      3. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeContact`
   1. `GEOTECHNICALUNIT`
      1. [body geometry](./sprint2_3.md) 
         1. If geometry = IfcVoxelGrid an associated instance of IfcVoxelData (new CT!) is required

      1. [local placement](./sprint2_2.md)
      1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeGroundTypeDistribution`

   1. `HAZARDAREA`
      1. [body geometry](./sprint2_3.md) 
         1. If geometry = IfcVoxelGrid an associated instance of IfcVoxelData (new CT!) is required

      1. [local placement](./sprint2_2.md)
      1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeGeoHazard`


### Book C

1. `IfcTunnelTypicalSection/GEOTECH`
	1. [contained](#new-concepts) in `IfcTunnel`
	2. [positioned between two](#new-concepts) `IfcReferent`
	3. [properties](./sprint2_3.md) with `TBD`
