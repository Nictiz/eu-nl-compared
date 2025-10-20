# SubstanceUse

## General comments
Both the EHDS model and the zib seem to model an observation of a period (this may be a current period, without end date), but metadata about the observation, like a date on which the observation was made, is missing in both models.  
The zib has a AlcoholUseStatus which is a mix of the status at the time of the observation and the history.  
The EHDS model has only header.status of which the definition is "Status of the patient’s alcohol use." This is probably an error, as the header should contain metadata of the _registration_ of the SubstanceUse instance.   
There may be an issue with units of the amount of substance consumed. The zib has "unis per time unit", the EHDS model has "volume per time unit".  
The zib lacks routeOfAdministration. 



| zib                                   | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| AlcoholUse                            | EHDSSubstanceUse                               |            |                        |             | 0..*          |
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
| AlcoholUse.ObservationOfUse.StartDate; AlcoholUse.ObservationOfUse.StopDate| EHDSSubstanceUse.period                        | TS         | Period                 | 0..1        | 0..1          |
|                                       | EHDSSubstanceUse.frequencyAndQuantity          |            | Base                   |             | 0..1          |
| AlcoholUse.ObservationOfUse.Amount    | EHDSSubstanceUse.frequencyAndQuantity.quantity | PQ         | Quantity               | 0..1        | 1..1          |
|                                       | EHDSSubstanceUse.frequencyAndQuantity.period   |            | Period                 |             | 0..1          |
|                                       | EHDSSubstanceUse.substanceType                 |            | CodeableConcept        |             | 0..1          |
|                                       | EHDSSubstanceUse.routeOfAdministration         |            | CodeableConcept        |             | 0..*          |
| AlcoholUse.Comment                    | EHDSSubstanceUse.note                          | ST         | string                 | 0..1        | 0..1          |
| AlcoholUse.AlcoholUseStatus           |                                                | CD         |                        | 1           |               |
| AlcoholUse.ObservationOfUse           |                                                |            |                        | 0..1        |               |




## EHDSSubstanceUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse |
| zib | AlcoholUse |
| alias_zib | NL: AlcoholGebruik |
| card._xtehr | 0..* |
| definition_xtehr | Statement about using a substance (such as tobacco, alcohol, drugs, etc). |
| definition_zib | Root concept of the AlcoholUse information model. This concept contains all data elements of the AlcoholUse information model. |
| id_xtehr | EHDSSubstanceUse |
| id_zib | NL-CM:7.3.1 |
| name_zib | AlcoholUse |
| path_xtehr | EHDSSubstanceUse |
| path_zib | AlcoholUse |
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
The definition of this concept is probably a error. The header contains metadata about the registration of the instance of SubstanceUse.



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
| zib | AlcoholUse.ObservationOfUse.StartDate |
| alias_zib | NL: StartDatum |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period for which this observation about substance use is applicable |
| definition_zib | The date on which the patient started using alcohol. |
| id_xtehr | EHDSSubstanceUse.period |
| id_zib | NL-CM:7.3.4 |
| name_zib | StartDate |
| path_xtehr | EHDSSubstanceUse.period |
| path_zib | AlcoholUse.ObservationOfUse.StartDate; AlcoholUse.ObservationOfUse.StopDate |
| short_xtehr | Time period for which this observation about substance use is applicable |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

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
| zib | AlcoholUse.ObservationOfUse.Amount |
| alias_zib | NL: Hoeveelheid |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Quantity (volume per time unit). |
| definition_zib | The extent of the patient’s alcohol use in units of alcohol per time period. |
| definitioncode_zib | SNOMED CT: 897148007 Alcoholic beverage intake |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| id_zib | NL-CM:7.3.6 |
| name_zib | Amount |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| path_zib | AlcoholUse.ObservationOfUse.Amount |
| short_xtehr | Quantity (volume per time unit). |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments
The zib had units "units per timeperiod". The EHDS model has units "volume per time unit". 



## EHDSSubstanceUse.frequencyAndQuantity.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time period of alcohol use. |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| short_xtehr | Time period of alcohol use. |
| type_xtehr | Period |

### Comments



## EHDSSubstanceUse.substanceType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.substanceType |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Type of substance |
| id_xtehr | EHDSSubstanceUse.substanceType |
| path_xtehr | EHDSSubstanceUse.substanceType |
| short_xtehr | Type of substance |
| type_xtehr | CodeableConcept |

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
| zib | AlcoholUse.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual comment. |
| definition_zib | Relevant comments on the alcohol consumption. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSSubstanceUse.note |
| id_zib | NL-CM:7.3.7 |
| name_zib | Comment |
| path_xtehr | EHDSSubstanceUse.note |
| path_zib | AlcoholUse.Comment |
| short_xtehr | Textual comment. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## zib: AlcoholUse.AlcoholUseStatus

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AlcoholUse.AlcoholUseStatus |
| alias_zib | NL: AlcoholGebruikStatus |
| card._zib | 1 |
| definition_zib | The status of the patient’s alcohol use. |
| definitioncode_zib | SNOMED CT: 228273003 Finding relating to alcohol drinking behavior |
| id_zib | NL-CM:7.3.2 |
| name_zib | AlcoholUseStatus |
| path_zib | AlcoholUse.AlcoholUseStatus |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: AlcoholUse.ObservationOfUse

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AlcoholUse.ObservationOfUse |
| alias_zib | NL: WaarnemingGebruik |
| card._zib | 0..1 |
| definition_zib | Container of the ObservationOfUse concept. This container contains all data elements of the observation of alcohol use. |
| id_zib | NL-CM:7.3.3 |
| name_zib | ObservationOfUse |
| path_zib | AlcoholUse.ObservationOfUse |
| stereotype_zib | container |

### Comments



## zib: AlcoholUse.ObservationOfUse.StopDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AlcoholUse.ObservationOfUse.StopDate |
| alias_zib | NL: StopDatum |
| card._zib | 0..1 |
| definition_zib | The date on which the patient stopped consuming alcohol. |
| id_zib | NL-CM:7.3.5 |
| name_zib | StopDate |
| path_zib | AlcoholUse.ObservationOfUse.StopDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments

