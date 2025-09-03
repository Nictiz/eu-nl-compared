# Comparison between XtEHR and zibs

## Sources

| Comparison Logical model 2020 | Comparison Logical model 2024 | Comparison FHIR profile | XtEHR | zib2020 | zib2024 |
|---|---|---|---|---|---|
|Address|[Address](./maps/xtehr2zibs2024/Address-comments.md) | | [Address](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSAddress.html)| | [AddressInformation-v1.2](https://zibs.nl/wiki/AddressInformation-v1.2(2024EN)) |
|Alert|Alert | | [AlertFlag](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSAlertFlag.html)| | [Alert-v4.1](https://zibs.nl/wiki/Alert-v4.1(2020EN)) |
|AllergyIntolerance|AllergyIntolerance | | [Allergy Intolerance](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSAllergyIntolerance.html)| | [AllergyIntolerance-v3.3](https://zibs.nl/wiki/AllergyIntolerance-v3.3(2020EN))|
|BodyStructure|[BodyStructure](./maps/xtehr2zibs2024/BodyStructure-comments.md) | | [BodyStructure](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSBodyStructure.html)| | [AnatomicalLocation-v1.0.4](https://zibs.nl/wiki/AnatomicalLocation-v1.0.4(2024EN))|
|[Condition](./maps/xtehr2zibs/Condition-comments.md)|[Diagnosis, Condition](./maps/xtehr2zibs2024/Diagnosis-comments.md) | | [Condition](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSCondition.html)| [Problem-v4.4](https://zibs.nl/wiki/Problem-v4.4(2020EN))|
| | [DataSet](./maps/xtehr2zibs2024/DataSet-comments.md) | | [DataSet](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSDataSet.html)| |[RegistrationData-v1.1.2](https://zibs.nl/wiki/RegistrationData-v1.1.2(2024EN))|
|[Device](./maps/xtehr2zibs/Device_And_DeviceUse-comments.md)| [Device](./maps/xtehr2zibs2024/Device-and-DeviceUse-comments.md) | | [Device](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSDevice.html)<br/>[DeviceUse](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSDeviceUse.html)| [MedicalDevice-v3.3.1](https://zibs.nl/wiki/MedicalDevice-v3.3.1(2020EN))|[MedicalDevice-v5.0](https://zibs.nl/wiki/MedicalDevice-v5.0(2024EN))|
|| [Dosaging](./maps/xtehr2zibs2024/Dosaging-comments.md) | | [Dosaging](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSDosaging.html)| |[InstructionsForUse-v3.1](https://zibs.nl/wiki/InstructionsForUse-v3.1(2024EN))|
|Encounter| [Encounter](./maps/xtehr2zibs2024/Encounter-comments.md) | | [Encounter](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSEncounter.html)| [Encounter-v4.0.1](https://zibs.nl/wiki/Encounter-v4.0.1(2020EN))|[Encounter-v7.0](https://zibs.nl/wiki/Encounter-v7.0(2024EN))|
|HealthProfessional|HealthProfessional | |[HealthProfessional](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSHealthProfessional.html)| | [HealthProfessional-v4.0.1](https://zibs.nl/wiki/HealthProfessional-v4.0.1(2024EN))| 
|HumanName|[HumanName](./maps/xtehr2zibs2024/HumanName-comments.md)  | |[HumanName](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSHumanName.html)| | [NameInformation-v1.2](https://zibs.nl/wiki/NameInformation-v1.2(2024EN))| 
|Location-and-Organization|[Location-and-Organization](./maps/xtehr2zibs2024/Location-and-Organization-comments.md) | |[Location-and-Organization](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSLocation-and-Organization.html)| | | 
|Medication overview | | |
|| [Medication](./maps/xtehr2zibs2024/Medication-comments.md) | | [Medication](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSMedication.html)|  | [PharmaceuticalProduct-v2.3](https://zibs.nl/wiki/PharmaceuticalProduct-v2.3(2024EN))
|| [MedicationDispense](./maps/xtehr2zibs2024/MedicationPrescription-comments.md) | | [MedicationDispense](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSMedicationDispense.html)|  | [MedicationDispense-v3.0.1](https://zibs.nl/wiki/MedicationDispense-v3.0.1(2024EN)), [AdministrationAgreement-v3.0](https://zibs.nl/wiki/AdministrationAgreement-v3.0(2024EN))
|| [MedicationPrescription](./maps/xtehr2zibs2024/MedicationPrescription-comments.md) | | [MedicationPrescription](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSMedicationPrescription.html)|  | [DispenseRequest-v4.0](https://zibs.nl/wiki/MedicationDispense-v4.0(2024EN)), [MedicationAgreement-v4.0](https://zibs.nl/wiki/MedicationAgreement-v4.0(2024EN))
|[Patient](./maps/xtehr2zibs/Patient-comments.md)| [Patient](./maps/xtehr2zibs2024/Patient-comments.md) | | [Patient](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSPatient.html)| [Patient-v3.2](https://zibs.nl/wiki/Patient-v3.2(2020EN)) | [Patient-v4.3](https://zibs.nl/wiki/Patient-v4.3(2024EN))
|[Procedure](./maps/xtehr2zibs/Procedure-comments.md)| [Procedure](./maps/xtehr2zibs2024/Procedure-comments.md) | | [Procedure](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSProcedure.html)| [Procedure-v5.2](https://zibs.nl/wiki/Procedure-v5.2(2020EN)) | [Procedure-v6.0](https://zibs.nl/wiki/Procedure-v6.0(2024EN)) |
|Telecom| [Telecom](./maps/xtehr2zibs2024/Telecom-comments.md) | | [Telecom](https://build.fhir.org/ig/Xt-EHR/xt-ehr-common/StructureDefinition-EHDSTelecom.html)|  | [ContactInformation-v1.3.1)](https://zibs.nl/wiki/ContactInformation-v1.3.1(2024EN)) |

## Deliverable

De analyses per bouwsteen zijn te vinden in de Markdown-bestanden `maps/xtehr2zibs/*-comment.md` en `maps/xtehr2zibs/*-comment.md`. Deze bestanden bevatten tabellen waarin per gegevensconcept in zowel de zib als Xt-EHR-model staat aangegeven:

* welke concepten met elkaar relateren
* wat de kardinaliteit is
* wat het datatype is

Daaronder staat een kopje met "Comments" waarin bevindingen geplaatst worden.

## Aanpak
Dit tools in dit repo maken het mogelijk om voor een deels automatisch een vergelijking te maken tussen zibs (2020 en 2024) enerzijds en de Xt-EHR logical models anderzijds. Dit gaat in ieder geval om datatype en kardinaliteit per gegevenselement. Inhoud van terminologie of context rond gebruik zijn bij uitstek dingen die handmatig geanalyseerd moeten worden. De gegenereerde materialen kunnen hierbij helpen.

### Zibs
Als basis dienen de Excels van de zibs. Deze worden gedownload naar:

* voor zib2020: `zibs2020/downloads`: dit zijn de Excels van zibs.nl gedownload
* voor zib2020: `zibs2024/downloads`: deze zijn met Excel (Data->from web) gedownload omdat de Excels nog niet op zibs.nl stonden

Voor elk van deze Excels wordt een "mappable" Excel gemaakt (via zib2020-2-map.py en zib2024-2-map.py), waarmee later de relatie met de Xt-EHR-modellen aangegeven kan worden. De 'mappable' komen respectievelijk in de folders `zibs2020/mappable` en `zibs2024/mappable`. Deze Excels zijn gestandaardiseerd naar een gemeenschappelijk format met voor de zibs kolommen:

* name
* path
* type
* card.
* id
* definition
* definitioncode

### Xt-EHR
Voor Xt-EHR wordt iets soortgelijks gedaan. Als basis dienen de logical models. Deze worden gedownload naar de map `xtehr/downloads`. 

Voor elk van deze logical models wordt eveneens een "mappable" Excel gemaakt (via xtehr2map.py), die in de folder `xtehr/mappable` terechtkomen.

Voor de Xt-EHR logical models bevat de Excel de kolommen:

* id
* path
* short
* definition
* type
* card.
* binding

### Relaties aanleggen tussen zibs en Xt-EHR

Met de "mappable" Excels van de zibs aan de ene kant en Xt-EHR aan de andere kant, kan aangegeven worden hoe de twee modellen zich tot elkaar verhouden. Dit gemeenschappelijk formaat maakt het eenvoudiger de volgende mapping stappen te doen. Belangrijkste is **path** dit is een puntgescheiden path (naam.naam2.naam3) waarmee de mapping tussen zibs en logical models gemaakt wordt.

In `maps` staat de met de hand gemaakte path-op-path mapping.

Deze inputs wordt vervolgens gebruikt voor het genereren van een aantal bestanden:

* Excels voor wie die graag wil zien
* dito CSV, wordt nu niet gebruikt maar vanuit Github worden deze netjes gerenderd als je naar die map gaat
* markdown:
  * {file}.md is de gegenereerde mardown
  * {file}-comments.md is na genereren identiek aan de vorige maar dat is degene die met de hand aangepast kan worden om onder comments kopjes de bevindingen per item te noteren.

Deze bestanden staan in resp. de mappen:

* voor zib2020: `maps/xtehr2zibs`

* voor zib2024: `maps/xtehr2zibs2024`
