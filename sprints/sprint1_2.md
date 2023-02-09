# Sprint 1.2

This sprint implements and tests `IfcProject` specific usages.


## Prerequisities

This sprint assumes you completed the following sprints:

- none.


## Duration

| Kick-off    | Submission  | Closure     |
|-------------|-------------|-------------|
| 2023.02.09. | 2023.02.20. | 2023.02.23. |


## Usages

This sprint encompasses the following usages:

- [Project Classification Information](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-classification-information.htm)
	1. The `IfcProject` shall associate `IfcClassification` with non-empty `Source` and `Name` attributes (content of the attributes is irrelevant to the check at this stage)
- [Spatial Decomposition](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/spatial-decomposition.htm)
	1. There shall be either an `IfcSite` or an `IfcFacility` (with subtypes irrelevant to the check) aggregated in the `IfcProject`. Observe the *NOTE* in the documentation.

Georeferencing can be achieved in three different ways with three different usages as presented in the figure below.
The participants are encouraged to submit three separate files, each with a different scenario.
To enable easier review process, please denote the file names with `Georef_A`, `Georef_B` or `Georef_C` corresponding to the lines below.
There shall be only one of these in the `ifc` dataset for the check to pass:
- [Project Global Positioning](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-global-positioning.htm) - scenario `Georef_A`
	1. `IfcMapConversion` or `IfcMapConversionScaled` is used (attributes' values are irrelevant).
	2. one of these shall be true:
		- `IfcProjectedCRS.Name` shall begin with `EPSG:` and be followed by 4 or 5 digits (actual numbers are irrelevant to the checker).
		- `IfcProjectedCRS.HasWellKnownTextRepresentation.WellKnownText` shall be non-empty.
- [Project Global Positioning Geographic](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-global-positioning-geodetic.htm) - scenario `Georef_B`
	1. `IfcRigidOperation` is used (attributes' values are irrelevant).
	2. one of these shall be true:
		- `IfcGeographicCRS.Name` shall begin with `EPSG:` and be followed by 4 or 5 digits (actual numbers are irrelevant to the checker).
		- `IfcGeographicCRS.HasWellKnownTextRepresentation.WellKnownText` shall be non-empty.
- [Project Global Positioning Mapped](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-global-positioning.htm) - scenario `Georef_C`
	1. `IfcRigidOperation` is used (attributes' values are irrelevant).
	2. one of these shall be true:
		- `IfcProjectedCRS.Name` shall begin with `EPSG:` and be followed by 4 or 5 digits (actual numbers are irrelevant to the checker).
		- `IfcProjectedCRS.HasWellKnownTextRepresentation.WellKnownText` shall be non-empty.

![grafik](https://user-images.githubusercontent.com/59165496/217642943-edfbf726-dbe4-4428-a596-7ce6357bc8bb.png)

Top path corresponds to `Georef_C`, diagonal path to `Georef_A` and bottom path to `Georef_B`. Sketch courtesy of Stefan Jaud.
