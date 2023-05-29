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


## Concepts

### New concepts

1. [Spatial containment](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-containment.htm)
2. [Element Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-decomposition.htm)
3. [Element Composition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-composition.htm)
4. [Material single](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/material-single.htm)
5. [Material Layer Set](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/material-layer-set.htm)
6. [Earthworks Cuttings](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/earthworks-cuttings.htm)
7. Excavation Cuttings (does not exist - generalize Earthworks Cuttings?)
8. [Body Sectioned SolidHorizontal](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-sectionedsolidhorizontal.htm)
9. Geometric Curve Set!
10. [Product Span Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-span-positioning.htm)


## Usages

This sprint encompasses the following usages:

### Excavation

1. `IfcUndergroundExcavation`
  1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) (does this need to be contained?)
  1. body geometry (New - IfcSectionedSolidHorizontal with guide curves!)
     1. [Body representation](#new-concepts) 
     1. curve set representation (New!)
  1. [local placement](./sprint2_2.md)
  1. [properties](./sprint2_3.md) with `Pset_ExcavationCommon`
  1. [excavation cuttings](#new-concepts)
     1. The excavation shall void (`IfcRelVoidsElements`) the `IfcGeoScienceModel` below
1. `IfcEarthworksCut`
   1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) (does this need to be contained?)
   2. [body geometry](./sprint2_3.md)
   3. [local placement](./sprint2_2.md)
   4. [properties](./sprint2_3.md) with `Pset_EarthworksCutCommon`
   5. [earthworks cuttings](#new-concepts)
      1. The cut shall void (`IfcRelVoidsElements`) the `IfcGeoScienceModel` below
1. `IfcGeoScienceModel/GEOTECHMODEL` 
  1. [contained](#new-concepts) in [`IfcSite`](./sprint2_1.md) 
  1. [local placement](./sprint2_2.md)
  1. [decomposed by](#new-concepts) `IfcGeoSciencefeature/GEOTECHNICALUNIT`

1. `IfcGeoSciencefeature/GEOTECHNICALUNIT`
   1. [part of](#new-concepts) `IfcGeoScienceModel/GEOTECHMODEL` 
   1. [body geometry or surface tesselation geometry](./sprint2_3.md) 
   1. [local placement](./sprint2_2.md)


### Waterproofing

1. `IfcCovering/MEMBRANE`
  1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
  1. [body geometry or surface tesselation geometry](./sprint2_3.md) 
  1. [local placement](./sprint2_2.md)
  1. [properties](./sprint2_3.md) with `Pset_CoveringTypeMembrane`
  1. [material layer set](#new-concepts) (see also https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/material-layer-set.htm - Table 157)
     1. IfcMaterialLayer-1
        1. LayerThickness = 2 mm
        1. Name = 'Front'
        1. Material.Name = "Synthetic"
     1. IfcMaterialLayer-2
        1. LayerThickness = 0.5 mm
        1. Name = "Fill"
        1. Material.Name = 'GeoTextile'
1. `IfcDiscreteAccessory/WATER_BARRIER`
  1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
  1. Geometry?
  1. [local placement](./sprint2_2.md)
  1. [properties](./sprint2_3.md) with `Pset_DiscreteAccessoryTypeWaterBarrier`
1. `IfcSpatialZone/COMPARTMENT`
  1. [aggregated](./sprint2_1.md) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
  1. [body geometry](./sprint2_3.md)
  1. [local placement](./sprint2_2.md)
  1. [properties](./sprint2_3.md) with `Pset_SpatialZoneTypeCompartment`
1. `IfcBuiltSystem/WATERPROOFING`
   1. [declared](./sprint2_1.md) by `IfcProject`
   1. [groups](./sprint2_1.md) elements IfcCovering/MEMBRANE, IfcDiscreteAccessory/WATER_BARRIER and IfcSpatialZone/COMPARTMENT
   1. [properties](./sprint2_3.md) with `Pset_BuiltSystemTypeWaterproofing`

### Support

1. `IfcElementAssembly/ARCH`
   1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
   2. [decomposed by](#new-concepts) `IfcArchElement/SEGMENT`
   3. [local placement](./sprint2_2.md)
   4. [properties](./sprint2_3.md) with `TBD`

2. `IfcArchElement/SEGMENT`
   1. [part of](#new-concepts) `IfcElementAssembly/ARCH`
   2. [body geometry](./sprint2_3.md) 
   3. [local placement](./sprint2_2.md)
   4. [properties](./sprint2_3.md) with `Pset_ArchElementCommon`
   5. [single material](#new-concepts)
      1. Including properties with `Pset_MaterialConcrete`

3. `IfcTunnelTypicalSection/EXCAVATIONSUPPORT`
   1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
   2. [positioned between two](#new-concepts) `IfcReferent`
   3. [properties](./sprint2_3.md) with `TBD`

4. `IfcBuiltSystem/TUNNEL_SUPPORT`
   1. [declared](./sprint2_1.md) by `IfcProject`
   2. [groups](./sprint2_1.md) elements `IfcElementAssembly/ARCH` and `IfcTunnelTypicalSection/EXCAVATIONSUPPORT`
   3. [properties](./sprint2_3.md) with `TBD`

### Lining

1. `IfcArchElement/LINING`
   1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
   2. [body geometry](./sprint2_3.md) 
   3. [local placement](./sprint2_2.md)
   4. [properties](./sprint2_3.md) with `Pset_ArchElementCommon`
   5. [single material](#new-concepts)
      1. Including properties with `Pset_MaterialConcrete`
2. `IfcBuiltSystem/TUNNEL_LINING`
   1. [declared](./sprint2_1.md) by `IfcProject`
   2. [groups](./sprint2_1.md) elements `IfcArchElement/LINING`
   3. [properties](./sprint2_3.md) with `TBD`

