# SubstanceUse

| zib                                | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-----------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| DrugUse                            | EHDSSubstanceUse                               |            |                        |             | 0..*          |
|                                    | EHDSSubstanceUse.header                        |            | Base                   |             | 1..1          |
|                                    | EHDSSubstanceUse.header.subject                |            | EHDSPatient            |             | 1..1          |
|                                    | EHDSSubstanceUse.header.identifier             |            | Identifier             |             | 0..*          |
|                                    | EHDSSubstanceUse.header.authorship             |            | Base                   |             | 1..*          |
|                                    | EHDSSubstanceUse.header.authorship.author[x]   |            | EHDSHealthProfessional |             | 1..1          |
|                                    | EHDSSubstanceUse.header.authorship.datetime    |            | dateTime               |             | 1..1          |
|                                    | EHDSSubstanceUse.header.lastUpdate             |            | dateTime               |             | 0..1          |
|                                    | EHDSSubstanceUse.header.status                 |            | CodeableConcept        |             | 1..1          |
|                                    | EHDSSubstanceUse.header.statusReason[x]        |            | CodeableConcept        |             | 0..1          |
|                                    | EHDSSubstanceUse.header.language               |            | CodeableConcept        |             | 0..1          |
|                                    | EHDSSubstanceUse.period                        |            | Period                 |             | 0..1          |
|                                    | EHDSSubstanceUse.frequencyAndQuantity          |            | Base                   |             | 0..1          |
| DrugUse.ObservationOfUse.Amount    | EHDSSubstanceUse.frequencyAndQuantity.quantity | ST         | Quantity               | 0..1        | 1..1          |
| DrugUse.ObservationOfUse.StartDate | EHDSSubstanceUse.frequencyAndQuantity.period   | TS         | Period                 | 0..1        | 0..1          |
| DrugUse.DrugOrMedicationType       | EHDSSubstanceUse.substanceType                 | CD         | CodeableConcept        | 0..1        | 0..1          |
| DrugUse.RouteOfAdministration      | EHDSSubstanceUse.routeOfAdministration         | CD         | CodeableConcept        | 0..*        | 0..*          |
| DrugUse.Comment                    | EHDSSubstanceUse.note                          | ST         | string                 | 0..1        | 0..1          |
| DrugUse.DrugUseStatus              |                                                | CD         |                        | 1           |               |
| DrugUse.ObservationOfUse           |                                                |            |                        | 0..1        |               |
| DrugUse.ObservationOfUse.StopDate  |                                                | TS         |                        | 0..1        |               |



## EHDSSubstanceUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse |
| zib | DrugUse |
| alias_zib | NL: DrugsGebruik |
| card._xtehr | 0..* |
| definition_xtehr | Statement about using a substance (such as tobacco, alcohol, drugs, etc). |
| definition_zib | Root concept of the DrugUse information model. This concept contains all data elements of the DrugUse information model. |
| definitioncode_zib | SNOMED CT: 228366006 Finding relating to drug misuse behavior |
| id_xtehr | EHDSSubstanceUse |
| id_zib | NL-CM:7.4.1 |
| name_zib | DrugUse |
| path_xtehr | EHDSSubstanceUse |
| path_zib | DrugUse |
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
| zib | DrugUse.ObservationOfUse.Amount |
| alias_zib | NL: Hoeveelheid |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Quantity (volume per time unit). |
| definition_zib | The number of units (pills, joints, shots etc.) per day, week, month, or year; or the frequency of use. |
| definitioncode_zib | SNOMED CT: 228390007 Frequency of drug misuse |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| id_zib | NL-CM:7.4.8 |
| name_zib | Amount |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity.quantity |
| path_zib | DrugUse.ObservationOfUse.Amount |
| short_xtehr | Quantity (volume per time unit). |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | ST |

### Comments



## EHDSSubstanceUse.frequencyAndQuantity.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| zib | DrugUse.ObservationOfUse.StartDate |
| alias_zib | NL: StartDatum |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period of alcohol use. |
| definition_zib | The date on which the patient started using. |
| id_xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| id_zib | NL-CM:7.4.6 |
| name_zib | StartDate |
| path_xtehr | EHDSSubstanceUse.frequencyAndQuantity.period |
| path_zib | DrugUse.ObservationOfUse.StartDate |
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
| zib | DrugUse.DrugOrMedicationType |
| alias_zib | NL: DrugsOfGeneesmiddelSoort |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Type of substance |
| definition_zib | Type of drug used by the patient. |
| definitioncode_zib | SNOMED CT: 410942007 Drug or medicament |
| id_xtehr | EHDSSubstanceUse.substanceType |
| id_zib | NL-CM:7.4.2 |
| name_zib | DrugOrMedicationType |
| path_xtehr | EHDSSubstanceUse.substanceType |
| path_zib | DrugUse.DrugOrMedicationType |
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
| zib | DrugUse.RouteOfAdministration |
| alias_zib | NL: Toedieningsweg |
| binding_xtehr | {'strength': 'preferred', 'description': 'EDQM'} |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Route(s) of administration |
| definition_zib | The way the drugs are used. |
| definitioncode_zib | SNOMED CT: 410675002 Route of administration |
| id_xtehr | EHDSSubstanceUse.routeOfAdministration |
| id_zib | NL-CM:7.4.4 |
| name_zib | RouteOfAdministration |
| path_xtehr | EHDSSubstanceUse.routeOfAdministration |
| path_zib | DrugUse.RouteOfAdministration |
| short_xtehr | Route(s) of administration |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSSubstanceUse.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSubstanceUse.note |
| zib | DrugUse.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual comment. |
| definition_zib | Relevant comments on the drug use. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSSubstanceUse.note |
| id_zib | NL-CM:7.4.9 |
| name_zib | Comment |
| path_xtehr | EHDSSubstanceUse.note |
| path_zib | DrugUse.Comment |
| short_xtehr | Textual comment. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## zib: DrugUse.DrugUseStatus

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | DrugUse.DrugUseStatus |
| alias_zib | NL: DrugsGebruikStatus |
| card._zib | 1 |
| definition_zib | Indication stating whether there was any drug use in the past or present. |
| definitioncode_zib | SNOMED CT: 228366006 Finding relating to drug misuse behavior |
| id_zib | NL-CM:7.4.3 |
| name_zib | DrugUseStatus |
| path_zib | DrugUse.DrugUseStatus |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: DrugUse.ObservationOfUse

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | DrugUse.ObservationOfUse |
| alias_zib | NL: WaarnemingGebruik |
| card._zib | 0..1 |
| definition_zib | Container for ObservationOfUse. This container contains all data elements of the ObservationOfUse container. |
| id_zib | NL-CM:7.4.5 |
| name_zib | ObservationOfUse |
| path_zib | DrugUse.ObservationOfUse |
| stereotype_zib | container |

### Comments



## zib: DrugUse.ObservationOfUse.StopDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | DrugUse.ObservationOfUse.StopDate |
| alias_zib | NL: StopDatum |
| card._zib | 0..1 |
| definition_zib | The date on which the patient quit using. |
| id_zib | NL-CM:7.4.7 |
| name_zib | StopDate |
| path_zib | DrugUse.ObservationOfUse.StopDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments

