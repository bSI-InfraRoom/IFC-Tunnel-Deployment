# Sprint 1.3

This sprint implements and tests `IfcProject` specific usages.


## Prerequisities

This sprint assumes you completed the following sprints:

- [Sprint 1.1](./sprint1_1.md) and
- [Sprint 1.2](./sprint1_2.md).


## Duration

| Kick-off    | Submission  | Closure     |
| ----------- | ----------- | ----------- |
| 2023.02.23. | 2023.03.13. | 2023.03.16. |


## Usages

This sprint encompasses the following usages:

1. [Project Document Information](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-document-information.htm)
    1. The `IfcProject` shall associate `IfcDocumentInformation` with;
        1. non-empty `Identification`, `Name` and `Location` attributes (content of the attributes is irrelevant to the check at this stage); as well as
        1. `ElectronicFormat` shall be `application/pdf` to denote the format of the "virtually" attached file; (you are not required to attach any such file for the test) and
        1. `Editor` of the file being yourself or any other actor - do not forget to declare it using [Project Declaration usage from Sprint 1.1](./sprint1_1.md). 
1. [Project Dataset Information](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-dataset-information.htm)
    1. The `IfcProject` shall associate `IfcDatasetInformation` with:
        1. non-empty `Identification`, `Name` and `Location` attributes (content of the attributes is irrelevant to the check at this stage); as well as
        1. `ElectronicFormat` shall be `text/xml` to denote the format of the "virtually" attached file; (You are not required to attach any such file for the test) and
        1. `SchemaReference` being equal to `http://geosciml.org/geosciml/2.0/xsd/geosciml.xsd`.
1. [Project Library Information](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-library-information.htm)
    1. The `IfcProject` shall associate `IfcLibraryInformation` with:
        1. non-empty `Location`, `Version`, `VersionDate` and `Publisher` attributes (content of the attributes is irrelevant to the check at this stage).
1. [Project Type Definitions](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-type-definitions.htm)
    1. The `IfcProject` shall declare an `IfcArchElementType`.
1. [Project Template Definitions](https://bsi-infraroom.github.io/IFC-Documentation-Tunnel/4_4_0_0/general/HTML/link/project-template-definitions.htm)
    1. The `IfcProject` shall declare an `IfcPropertySetTemplate` with the following structure:
        - `Name` : 'Pset_GeoObsBoreholeConstruction'
        - `TemplateType` : .PSET_TYPEDRIVENOVERRIDE.
        - `ApplicableEntity` : 'IfcBorehole'
        - `HasPropertyTemplates` :
          - `IfcSimplePropertyTemplate` :
            - `Name` : 'DrillingDiameter'
            - `TemplateType` : .P_SINGLEVALUE.
            - `PrimaryMeasureType` : 'IfcPositiveLengthMeasure'
