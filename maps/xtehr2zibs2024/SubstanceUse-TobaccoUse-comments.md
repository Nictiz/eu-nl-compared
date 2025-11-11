# SubstanceUse
## Discussion 6 november 2025
Participants: Astrid, Jacob, Sander  
EHDSissues:
+ Change "Alcohol" into "Substance" all over https://github.com/Xt-EHR/xt-ehr-common/issues/369
+ Replace definition of .status in the header by its definition in EHDSDataset https://github.com/Xt-EHR/xt-ehr-common/issues/370
+ Add .status element, definition: Status of the patient’s substance use, type: codeable concept https://github.com/Xt-EHR/xt-ehr-common/issues/370
+ Add .statusDate, definition: Date on which the status was observed, type: dateTime https://github.com/Xt-EHR/xt-ehr-common/issues/371
+ Change cardinality of frequencyAndQuantity to 0..*, as within the period of observation, multiple periods of substance use may have occurred https://github.com/Xt-EHR/xt-ehr-common/issues/372
+ Add .cumulativeUse, definition: Cumulated quantity of substance used up to .statusDate, type: Quantity https://github.com/Xt-EHR/xt-ehr-common/issues/373

Zib issues:
+ DrugUse: Align data type of ObservationOfUse.Amount with EHDS model
+ AlcoholUse, DrugUse, TobaccoUse: add element to match EHDSSubstanceUse.period = Time period for which this observation about substance use is applicabl


## General comments
Both the EHDS model and the zib seem to model an observation of single period (this may be a current period, without end date). In the zib model, metadata about the observation, such as when the observation was made, is absent. In the EHDS model, there is .period, which is defined as "Time period for which this observation about substance use is applicable". It is not clear what this means. 
"Alcohol" in the EHDS model should be replaced by "Substance" throughout the model.

In addition the zib has a 
+ TobaccoUseStatus indicating whether there was any drug use in the past or present (we must assume at the time of the observation). 
+ PackYears which is a summation of TobaccoUse in the past.  

See also https://nictiz.atlassian.net/browse/ZIB-2212.  

The EHDS model has only header.status of which the definition is "Status of the patient’s alcohol use." This is most probably an error, as the header should contain metadata of the _registration_ of the SubstanceUse instance.


| zib                                   | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| TobaccoUse                            | EHDSSubstanceUse                               |            |                        |             | 0..*          |
|                                       | EHDSSubstanceUse.header                        |            | Base                   |             | 1..1          |
|                                       | EHDSSubstanceUse.header.subject                |            | EHDSPatient            |             | 1..1          |
|                                       | EHDSSubstanceUse.header.identifier             |            | Identifier             |             | 0..*          |
|                                       | EHDSSubstanceUse.header.authorship             |            | Base                   |             | 1..*          |
|                                       | EHDSSubstanceUse.header.authorship.author[x]   |            | EHDSHealthProfessional |             | 1..1          |
|                                       | EHDSSubstanceUse.header.authorship.datetime    |            | dateTime               |             | 1..1          |
|                                       | EHDSSubstanceUse.header.lastUpdate             |            | dateTime               |             | 0..1          |
|                                       | EHDSSubstanceUse.header.status                 |            | CodeableConcept        |             | 1..1          |
|                                       | EHDSSubstanceUse.header.statusReason[x]        |            | CodeableConcept        |             | 0..1          |
|                                       | EHDSSubstanceUse.header.language               |            | CodeableConcept        |             | 0..1          |
|                                       | EHDSSubstanceUse.period                        |            | Period                 |             | 0..1          |
|                                       | EHDSSubstanceUse.frequencyAndQuantity          |            | Base                   |             | 0..1          |
| TobaccoUse.ObservationOfUse.Amount    | EHDSSubstanceUse.frequencyAndQuantity.quantity | PQ         | Quantity               | 0..1        | 1..1          |
| TobaccoUse.ObservationOfUse.StartDate; TobaccoUse.ObservationOfUse.StopDate | EHDSSubstanceUse.frequencyAndQuantity.period   | TS         | Period                 | 0..1        | 0..1          |
| TobaccoUse.TypeOfTobaccoUsed          | EHDSSubstanceUse.substanceType                 | CD         | CodeableConcept        | 0..1        | 0..1          |
|                                       | EHDSSubstanceUse.routeOfAdministration         |            | CodeableConcept        |             | 0..*          |
| TobaccoUse.Comment                    | EHDSSubstanceUse.note                          | ST         | string                 | 0..1        | 0..1          |
| TobaccoUse.TobaccoUseStatus           |                                                | CD         |                        | 1           |               |
| TobaccoUse.ObservationOfUse           |                                                |            |                        | 0..1        |               |
| TobaccoUse.ObservationOfUse.PackYears |                                                | INT        |                        | 0..1        |               |



## EHDSSubstanceUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse |
| zib | TobaccoUse |
| alias_zib | NL: TabakGebruik |
| card._xtehr | 0..* |
| definition_xtehr | Statement about using a substance (such as tobacco, alcohol, drugs, etc). |
| definition_zib | Root concept of the TobaccoUse information model. This concept contains all data elements of the TobaccoUse information model. |
| definitioncode_zib | SNOMED CT: 365980008 Finding of tobacco use and exposure |
| id_xtehr | EHDSSubstanceUse |
| id_zib | NL-CM:7.2.1 |
| name_zib | TobaccoUse |
| path_xtehr | EHDSSubstanceUse |
| path_zib | TobaccoUse |
| short_xtehr | Substance use model |
| stereotype_zib | rootconcept |

### Comments



## EHDSSubstanceUse.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSSubstanceUse.header |
| path_xtehr | EHDSSubstanceUse.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSSubstanceUse.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSSubstanceUse.header.subject |
| path_xtehr | EHDSSubstanceUse.header.subject |
| short_xtehr | Patient/subject information |
| type_xtehr | EHDSPatient |

### Comments



## EHDSSubstanceUse.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSSubstanceUse.header.identifier |
| path_xtehr | EHDSSubstanceUse.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSSubstanceUse.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSSubstanceUse.header.authorship |
| path_xtehr | EHDSSubstanceUse.header.authorship |
| short_xtehr | Resource authoring details |
| type_xtehr | Base |

### Comments



## EHDSSubstanceUse.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSSubstanceUse.header.authorship.author[x] |
| path_xtehr | EHDSSubstanceUse.header.authorship.author[x] |
| short_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSSubstanceUse.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of authoring/issuing |
| id_xtehr | EHDSSubstanceUse.header.authorship.datetime |
| path_xtehr | EHDSSubstanceUse.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSSubstanceUse.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| id_xtehr | EHDSSubstanceUse.header.lastUpdate |
| path_xtehr | EHDSSubstanceUse.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| type_xtehr | dateTime |

### Comments



## EHDSSubstanceUse.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.status |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource or document |
| id_xtehr | EHDSSubstanceUse.header.status |
| path_xtehr | EHDSSubstanceUse.header.status |
| short_xtehr | Status of the patient’s alcohol use. |
| type_xtehr | CodeableConcept |

### Comments
Issue: header information is to be used for data about registration. Meaning of "Status of the patient’s alcohol use" is unclear.



## EHDSSubstanceUse.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSSubstanceUse.header.statusReason[x] |
| path_xtehr | EHDSSubstanceUse.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSSubstanceUse.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSSubstanceUse.header.language |
| path_xtehr | EHDSSubstanceUse.header.language |
| short_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSSubstanceUse.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time period for which this observation about substance use is applicable |
| id_xtehr | EHDSSubstanceUse.period |
| path_xtehr | EHDSSubstanceUse.period |
| short_xtehr | Time period for which this observation about substance use is applicable |
| type_xtehr | Period |

### Comments



## EHDSSubstanceUse.frequencyAndQuantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.frequencyAndQuantity |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The extent of the patient’s alcohol use in units of alcohol per time period. |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity |
| short_xtehr | The extent of the patient’s alcohol use in units of alcohol per time period. |
| type_xtehr | Base |

### Comments



## EHDSSubstanceUse.frequencyAndQuantity.quantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| zib | TobaccoUse.ObservationOfUse.Amount |
| alias_zib | NL: Hoeveelheid |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Quantity (volume per time unit). |
| definition_zib | The number of cigarettes, cigars or grams of rolling tobacco consumed per day, week, month or year. |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| id_zib | NL-CM:7.2.6 |
| name_zib | Amount |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| path_zib | TobaccoUse.ObservationOfUse.Amount |
| short_xtehr | Quantity (volume per time unit). |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments



## EHDSSubstanceUse.frequencyAndQuantity.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| zib | TobaccoUse.ObservationOfUse.StartDate |
| alias_zib | NL: StartDatum |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period of alcohol use. |
| definition_zib | The date on which the patient started smoking. |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| id_zib | NL-CM:7.2.4 |
| name_zib | StartDate |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| path_zib | TobaccoUse.ObservationOfUse.StartDate |
| short_xtehr | Time period of alcohol use. |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments



## EHDSSubstanceUse.substanceType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.substanceType |
| zib | TobaccoUse.TypeOfTobaccoUsed |
| alias_zib | NL: SoortTabakGebruik |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Type of substance |
| definition_zib | Type of tobacco the patient uses. |
| definitioncode_zib | SNOMED CT: 53661000146106 Type of tobacco used |
| id_xtehr | EHDSSubstanceUse.substanceType |
| id_zib | NL-CM:7.2.9 |
| name_zib | TypeOfTobaccoUsed |
| path_xtehr | EHDSSubstanceUse.substanceType |
| path_zib | TobaccoUse.TypeOfTobaccoUsed |
| short_xtehr | Type of substance |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSSubstanceUse.routeOfAdministration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.routeOfAdministration |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'EDQM'} |
| card._xtehr | 0..* |
| definition_xtehr | Route(s) of administration |
| id_xtehr | EHDSSubstanceUse.routeOfAdministration |
| path_xtehr | EHDSSubstanceUse.routeOfAdministration |
| short_xtehr | Route(s) of administration |
| type_xtehr | CodeableConcept |

### Comments



## EHDSSubstanceUse.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.note |
| zib | TobaccoUse.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual comment. |
| definition_zib | Relevant comments on the patient’s use of tobacco. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSSubstanceUse.note |
| id_zib | NL-CM:7.2.3 |
| name_zib | Comment |
| path_xtehr | EHDSSubstanceUse.note |
| path_zib | TobaccoUse.Comment |
| short_xtehr | Textual comment. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## zib: TobaccoUse.TobaccoUseStatus

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | TobaccoUse.TobaccoUseStatus |
| alias_zib | NL: TabakGebruikStatus |
| card._zib | 1 |
| definition_zib | The status of the patient’s tobacco use. |
| definitioncode_zib | SNOMED CT: 229819007 Tobacco use and exposure |
| id_zib | NL-CM:7.2.10 |
| name_zib | TobaccoUseStatus |
| path_zib | TobaccoUse.TobaccoUseStatus |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: TobaccoUse.ObservationOfUse

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | TobaccoUse.ObservationOfUse |
| alias_zib | NL: WaarnemingGebruik |
| card._zib | 0..1 |
| definition_zib | This container contains all information on the extent to which the patient is or was exposed to tobacco. |
| id_zib | NL-CM:7.2.2 |
| name_zib | ObservationOfUse |
| path_zib | TobaccoUse.ObservationOfUse |
| stereotype_zib | container |

### Comments



## zib: TobaccoUse.ObservationOfUse.StopDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | TobaccoUse.ObservationOfUse.StopDate |
| alias_zib | NL: StopDatum |
| card._zib | 0..1 |
| definition_zib | The date on which the patient quit smoking |
| id_zib | NL-CM:7.2.5 |
| name_zib | StopDate |
| path_zib | TobaccoUse.ObservationOfUse.StopDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: TobaccoUse.ObservationOfUse.PackYears

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | TobaccoUse.ObservationOfUse.PackYears |
| alias_zib | NL: PackYears |
| card._zib | 0..1 |
| definition_zib | The unit indicating the smoker’s total exposure to tobacco smoke.  For cigarettes, this is calculated using the number of smoked packs of cigarettes per day (one pack = 20 cigarettes) times the number of years of smoking. For other forms of tobacco, this is usually converted to an equivalent cigarette consumption. Often, only the number of pack years is estimated. |
| definitioncode_zib | SNOMED CT: 401201003 Cigarette pack-years |
| id_zib | NL-CM:7.2.7 |
| name_zib | PackYears |
| path_zib | TobaccoUse.ObservationOfUse.PackYears |
| stereotype_zib | data |
| type_zib | INT |

### Comments
Maps on EHDSSubstanceUse.frequencyAndQuantity.period.

