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
1. [Element Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-decomposition.htm)
1. [Element Composition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-composition.htm)
1. [Product Assignment](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-assignment.htm)
1. [Dataset Association](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/dataset-association.htm)
1. [Product Span Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-span-positioning.htm)
1. [Assignment to Product](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/assignment-to-product.htm)


## Usages

This sprint encompasses the following usages.

The participants are encouraged to submit three separate files, each with a different book included.
To enable easier review process, please denote the file names with `Book_A`, `Book_B` or `Book_C` corresponding to the options below.


### Book A

1. `IfcBorehole`
    1. [contained](#new-concepts) in `IfcSite`
    1. Geometry: See IfcBorehole [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_SpatialGeoObsBorehole`

1. `IfcGeoScienceObservation/BOREHOLELOG`
    1. [assigned](#new-concepts) to `IfcBorehole` above
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. [properties](./sprint2_3.md) with `Pset_GeoObsBoreholeGeoLogInterval`

1. `IfcDatasetInformation`
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. [associated](#new-concepts) to `IfcGeoScienceObservation/BOREHOLELOG`

1. `IfcSpatialZone/MAPPEDZONE`
    1. [aggregated](#new-concepts) in `IfcSite`
    1. Geometry: See IfcSpatialZone/MAPPEDZONE [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_SpatialGeoObsMappedZoneCommon`

1. `IfcGeoScienceObservation/MAPPEDFEATURE`
    1. [assigned](#new-concepts) to `IfcSpatialZone/MAPPEDZONE` above
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. Geometry: See IfcGeoScienceObservation/MAPPEDFEATURE [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_GeoObsMappedUnit`

1. `IfcGeoScienceObservation/LOCALINFORMATION`
    1. [assigned](#new-concepts) to `IfcSpatialZone/MAPPEDZONE` above
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. Geometry: See IfcGeoScienceObservation/LOCALINFORMATION [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_GeoObsPtObservationCommon`

1. `IfcGeoScienceObservation/INSITUTESTRESULT`
    1. [assigned](#new-concepts) to `IfcSpatialZone/MAPPEDZONE` above
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. Geometry: See IfcGeoScienceObservation/INSITUTESTRESULT [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_InSituTestCommon`

1. `IfcGeoScienceObservation/LABTESTRESULT`
    1. [assigned](#new-concepts) to `IfcSpatialZone/MAPPEDZONE` above
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. Geometry: See IfcGeoScienceObservation/LABTESTRESULT [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_LabTestCommon`

1. `IfcGeoScienceObservation/GEOPHYSICALSURVEYRESULT`
    1. [assigned](#new-concepts) to `IfcSpatialZone/MAPPEDZONE` above
    1. [declared](./sprint1_1.md) in `IfcProject`
    1. Geometry: See IfcGeoScienceObservation/GEOPHYSICALSURVEYRESULT [here](./IFC-Tunnel-Geotechnics_Geometry.xlsx).
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_GeophysicalSurveyCommon`



### Book B

1. `IfcGeoScienceModel` 
    1. `PredefinedType` is depending on decomposition (valid pairs: WIP) 
    1. [contained](#new-concepts) in `IfcSite`
    1. [decomposed by](#new-concepts) `IfcGeoScienceFeature/*` below
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_GeoScienceModelCommon`

1. `IfcGeoScienceFeature`
    1. [part of](#new-concepts) `IfcGeoScienceModel` above
    1. `PredefinedType` - at least one of:

    1. `PHYSICALPROPERTYDISTRIBUTION`
        1. body geometry
            1. if geometry is [`IfcVoxelGrid`](./sprint2_3.md) an [associated instance of `IfcVoxelData`](#new-concepts) is required
            1. otherwise any other *body* geometry from [Sprint 2.3](./sprint2_3.md) is required
        1. [local placement](./sprint2_2.md)
        1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureCommon`
    1. `GEOLOGICALUNIT`
        1. body geometry
            1. if geometry is [`IfcVoxelGrid`](./sprint2_3.md) an [associated instance of `IfcVoxelData`](#new-concepts) is required
            1. otherwise any other *body* geometry from [Sprint 2.3](./sprint2_3.md) is required
        1. [local placement](./sprint2_2.md)
        1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeGeologicalUnit`
    1. `FAULT`
        1. body geometry
            1. if geometry is [`IfcVoxelGrid`](./sprint2_3.md) an [associated instance of `IfcVoxelData`](#new-concepts) is required
            1. otherwise any other *body* geometry from [Sprint 2.3](./sprint2_3.md) is required
        1. [local placement](./sprint2_2.md)
        1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeFault`
    1. `CONTACT`
        1. [surface geometry](./sprint2_3.md)
        1. [local placement](./sprint2_2.md)
        1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeContact`
    1. `GEOTECHNICALUNIT`
        1. body geometry
            1. if geometry is [`IfcVoxelGrid`](./sprint2_3.md) an [associated instance of `IfcVoxelData`](#new-concepts) is required
            1. otherwise any other *body* geometry from [Sprint 2.3](./sprint2_3.md) is required
        1. [local placement](./sprint2_2.md)
        1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureCommon`
    1. `HAZARDAREA`
        1. body geometry
            1. if geometry is [`IfcVoxelGrid`](./sprint2_3.md) an [associated instance of `IfcVoxelData`](#new-concepts) is required
            1. otherwise any other *body* geometry from [Sprint 2.3](./sprint2_3.md) is required
        1. [local placement](./sprint2_2.md)
        1. [properties](./sprint2_3.md) with `Pset_GeoScienceFeatureTypeGeoHazard`


### Book C

1. `IfcTunnelTypicalSection/GEOTECH`
	1. [contained](#new-concepts) in `IfcTunnel`
	1. [positioned between two](#new-concepts) `IfcReferent`
	1. [properties](./sprint2_3.md) with `Pset_GeoAspects`


### Other example

You don't have some of these specific geotechnic support capabilities within your suite (regardless of Book option)?
If you have a different idea that is more easily supported with your software suite,
 please come forward at the support meetings or contact us per email.
We will try to come up with (tunnel specific) instructions for your example.

### Geometric representations

The geometry representations specified above are suggestions from the IFC Tunnel technical team. For general requirements on geometric representations, please consult the [geometry requirements as specified by the IFC Tunnel geoscience domain experts](./IFC-Tunnel_Geotechnics_Geometry.xlsx).

