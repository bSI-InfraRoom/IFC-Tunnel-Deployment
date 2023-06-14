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
1. [Element Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-decomposition.htm)
1. [Element Composition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/element-composition.htm)
1. [Material single](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/material-single.htm)
1. [Material Layer Set Usage](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/material-layer-set-usage.htm)
1. [Assigning properties to material](https://github.com/bSI-InfraRoom/IFC-Specification/issues/649)
1. [Earthworks Cuttings](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/earthworks-cuttings.htm)
1. [Excavation Cuttings](https://github.com/bSI-InfraRoom/IFC-Specification/pull/653)
1. [Body Sectioned SolidHorizontal](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/body-sectionedsolidhorizontal.htm)
1. [Guide Curves](https://github.com/bSI-InfraRoom/IFC-Specification/pull/655)
1. [Product Span Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/product-span-positioning.htm)


## Usages

This sprint encompasses the following usages:

### Excavation

1. `IfcUndergroundExcavation` or `IfcEarthworksCut`
    1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) (does this need to be contained?)
    1. body geometry
        1. [Body Sectioned SolidHorizontal](#new-concepts) and [Guide Curves](#new-concepts) or
        1. any other [body geometry](./sprint2_3.md)
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_ExcavationCommon`
    1. [excavation cuttings](#new-concepts)
        1. The excavation shall void (`IfcRelVoidsElements`) the `IfcGeoScienceModel` below

1. `IfcGeoScienceModel/GEOTECHMODEL` 
    1. see [geotechnics, book B](./sprint3_geo.md#book-b)

1. `IfcGeoSciencefeature/GEOTECHNICALUNIT`
    1. see [geotechnics, book B](./sprint3_geo.md#book-b)


### Waterproofing

1. `IfcCovering/MEMBRANE`
    1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
    1. [body geometry or surface tesselation geometry](./sprint2_3.md) 
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_CoveringTypeMembrane`
    1. [material layer set](#new-concepts) (see also https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/ifccovering.htm - Table 157) with at least 2 layers:
        1. Layer
            1. `LayerThickness` being `2 mm`
            1. `Name` being `'Front'`
            1. `Material.Name` = `'Synthetic'`
        1. Layer
            1. `LayerThickness` being `0.5 mm`
            1. `Name` being `'Fill'`
            1. `Material.Name` = `'GeoTextile'`

1. `IfcDiscreteAccessory/WATER_BARRIER`
    1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
    1. Geometry: WIP
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_DiscreteAccessoryTypeWaterBarrier`

1. `IfcSpatialZone/COMPARTMENT`
    1. [aggregated](./sprint2_1.md) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
    1. [body geometry](./sprint2_3.md)
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_SpatialZoneTypeCompartment`

1. `IfcBuiltSystem/WATERPROOFING`
    1. [declared](./sprint2_1.md) by `IfcProject`
    1. [groups](./sprint2_1.md) elements `IfcCovering/MEMBRANE`, `IfcDiscreteAccessory/WATER_BARRIER` and `IfcSpatialZone/COMPARTMENT`
    1. [properties](./sprint2_3.md) with `Pset_BuiltSystemTypeWaterproofing`

### Support

1. `IfcElementAssembly/ARCH`
    1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
    1. [decomposed by](#new-concepts) `IfcArchElement/SEGMENT`
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `WIP`

1. `IfcArchElement/SEGMENT`
    1. [part of](#new-concepts) `IfcElementAssembly/ARCH`
    1. [body geometry](./sprint2_3.md) 
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_ArchElementCommon`
    1. [single material](#new-concepts)
        1. [properties](#new-concepts) with `Pset_MaterialConcrete`

1. `IfcTunnelTypicalSection/EXCAVATIONSUPPORT`
    1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
    1. [positioned between two](#new-concepts) `IfcReferent`
    1. [properties](./sprint2_3.md) with `WIP`

1. `IfcBuiltSystem/TUNNEL_SUPPORT`
    1. [declared](./sprint2_1.md) by `IfcProject`
    1. [groups](./sprint2_1.md) elements `IfcElementAssembly/ARCH` and `IfcTunnelTypicalSection/EXCAVATIONSUPPORT`
    1. [properties](./sprint2_3.md) with `WIP`

### Lining

1. `IfcArchElement/LINING`
    1. [contained](#new-concepts) in [`IfcTunnel`](./sprint2_1.md) or [`IfcTunnelPart`](./sprint2_1.md) 
    1. [body geometry](./sprint2_3.md) 
    1. [local placement](./sprint2_2.md)
    1. [properties](./sprint2_3.md) with `Pset_ArchElementCommon`
    1. [single material](#new-concepts)
        1. [properties](#new-concepts) with `Pset_MaterialConcrete`

1. `IfcBuiltSystem/TUNNEL_LINING`
    1. [declared](./sprint2_1.md) by `IfcProject`
    1. [groups](./sprint2_1.md) elements `IfcArchElement/LINING`
    1. [properties](./sprint2_3.md) with `WIP`

