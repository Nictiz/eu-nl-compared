# CurrentPregnancy

| zib                                                            | xtehr                                            | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:---------------------------------------------------------------|:-------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Pregnancy                                                      | EHDSCurrentPregnancy                             |            |                        |             | 0..*          |
|                                                                | EHDSCurrentPregnancy.currentPregnancyStatus      |            | CodeableConcept        |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.dateOfStatus                |            | dateTime               |             | 0..1          |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery | EHDSCurrentPregnancy.expectedDateOfDelivery      | TS         | date                   | 0..1        | 0..1          |
| Pregnancy.PregnancyDuration                                    | EHDSCurrentPregnancy.gestationalAge              | PQ         | Quantity               | 0..1        | 0..1          |
|                                                                | EHDSCurrentPregnancy.header                      |            | Base                   |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.header.authorship           |            | Base                   |             | 1..*          |
|                                                                | EHDSCurrentPregnancy.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.header.identifier           |            | Identifier             |             | 0..*          |
|                                                                | EHDSCurrentPregnancy.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                                | EHDSCurrentPregnancy.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                                | EHDSCurrentPregnancy.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                                | EHDSCurrentPregnancy.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.header.version              |            | string                 |             | 0..1          |
| Pregnancy.Comment                                              | EHDSCurrentPregnancy.narrative                   | ST         | string                 | 0..1        | 0..1          |
|                                                                | EHDSCurrentPregnancy.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| Pregnancy.EstimatedDateOfDeliveryItems                         |                                                  |            |                        | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation    |                                                  | TS         |                        | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation        |                                                  | TS         |                        | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod        |                                                  | CD         |                        | 0..1        |               |
| Pregnancy.Gravidity                                            |                                                  | INT        |                        | 0..1        |               |
| Pregnancy.Parity                                               |                                                  | INT        |                        | 0..1        |               |



## EHDSCurrentPregnancy

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy |
| zib | Pregnancy |
| alias_zib | NL: Zwangerschap |
| card._xtehr | 0..* |
| definition_xtehr | Current pregnancy status |
| definition_zib | Root concept of the Pregnancy information model. This root concept contains all data elements of the Pregnancy information model. |
| definitioncode_zib | SNOMED CT: 118185001 Finding related to pregnancy |
| id_xtehr | EHDSCurrentPregnancy |
| id_zib | NL-CM:7.14.1 |
| name_zib | Pregnancy |
| path_xtehr | EHDSCurrentPregnancy |
| path_zib | Pregnancy |
| short_xtehr | Current pregnancy status model |
| stereotype_zib | rootconcept |

### Comments



## EHDSCurrentPregnancy.currentPregnancyStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.currentPregnancyStatus |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 1..1 |
| definition_xtehr | Current state of the pregnancy at the date the observation was made, e.g. pregnant, not pregnant, unknown. |
| id_xtehr | EHDSCurrentPregnancy.currentPregnancyStatus |
| path_xtehr | EHDSCurrentPregnancy.currentPregnancyStatus |
| short_xtehr | Current pregnancy status |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCurrentPregnancy.dateOfStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.dateOfStatus |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Effective date of the current pregnancy status. |
| id_xtehr | EHDSCurrentPregnancy.dateOfStatus |
| path_xtehr | EHDSCurrentPregnancy.dateOfStatus |
| short_xtehr | Effective date of the current pregnancy status. |
| type_xtehr | dateTime |

### Comments



## EHDSCurrentPregnancy.expectedDateOfDelivery

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.expectedDateOfDelivery |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| alias_zib | NL: ATermeDatum |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date in which the woman is due to give birth. Year, day and month are required. |
| definition_zib | The date on which the pregnancy is expected to be 40w 0d (280 days). Different due dates are used at various points in the pregnancy. |
| definitioncode_zib | SNOMED CT: 161714006 Estimated date of delivery |
| id_xtehr | EHDSCurrentPregnancy.expectedDateOfDelivery |
| id_zib | NL-CM:7.14.3 |
| name_zib | EstimatedDateOfDelivery |
| path_xtehr | EHDSCurrentPregnancy.expectedDateOfDelivery |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| short_xtehr | Date in which the woman is due to give birth. Year, day and month are required. |
| stereotype_zib | data |
| type_xtehr | date |
| type_zib | TS |

### Comments



## EHDSCurrentPregnancy.gestationalAge

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.gestationalAge |
| zib | Pregnancy.PregnancyDuration |
| alias_zib | NL: Zwangerschapsduur |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Gestational age - duration of the pregnancy on the day on which the patient was asked or at the delivery. The duration can be given in weeks and/or days. |
| definition_zib | Duration of the pregnancy on the day on which the patient was asked. The duration can be given in days (d) or weeks (wk). |
| definitioncode_zib | SNOMED CT: 57036006 Fetal gestational age |
| id_xtehr | EHDSCurrentPregnancy.gestationalAge |
| id_zib | NL-CM:7.14.4 |
| name_zib | PregnancyDuration |
| path_xtehr | EHDSCurrentPregnancy.gestationalAge |
| path_zib | Pregnancy.PregnancyDuration |
| short_xtehr | Duration of the pregnancy at this day |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments



## EHDSCurrentPregnancy.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSCurrentPregnancy.header |
| path_xtehr | EHDSCurrentPregnancy.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSCurrentPregnancy.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSCurrentPregnancy.header.authorship |
| path_xtehr | EHDSCurrentPregnancy.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSCurrentPregnancy.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSCurrentPregnancy.header.authorship.author[x] |
| path_xtehr | EHDSCurrentPregnancy.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSCurrentPregnancy.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSCurrentPregnancy.header.authorship.datetime |
| path_xtehr | EHDSCurrentPregnancy.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSCurrentPregnancy.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSCurrentPregnancy.header.identifier |
| path_xtehr | EHDSCurrentPregnancy.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSCurrentPregnancy.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSCurrentPregnancy.header.language |
| path_xtehr | EHDSCurrentPregnancy.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCurrentPregnancy.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSCurrentPregnancy.header.lastUpdate |
| path_xtehr | EHDSCurrentPregnancy.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSCurrentPregnancy.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSCurrentPregnancy.header.status |
| path_xtehr | EHDSCurrentPregnancy.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCurrentPregnancy.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSCurrentPregnancy.header.statusReason[x] |
| path_xtehr | EHDSCurrentPregnancy.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCurrentPregnancy.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSCurrentPregnancy.header.subject |
| path_xtehr | EHDSCurrentPregnancy.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSCurrentPregnancy.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSCurrentPregnancy.header.version |
| path_xtehr | EHDSCurrentPregnancy.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSCurrentPregnancy.narrative

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.narrative |
| zib | Pregnancy.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Narrative description describing the status of the current pregnancy. |
| definition_zib | Comment on the pregnancy. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSCurrentPregnancy.narrative |
| id_zib | NL-CM:7.14.7 |
| name_zib | Comment |
| path_xtehr | EHDSCurrentPregnancy.narrative |
| path_zib | Pregnancy.Comment |
| short_xtehr | Textual description of current pregnancy status |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSCurrentPregnancy.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSCurrentPregnancy.presentedForm |
| path_xtehr | EHDSCurrentPregnancy.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems |
| alias_zib | NL: ATermeDatumItems |
| card._zib | 0..1 |
| definition_zib | Container of the EstimatedDateOfDeliveryItems concept.This container contains all data elements of the EstimatedDateOfDeliveryItems concept. |
| id_zib | NL-CM:7.14.9 |
| name_zib | EstimatedDateOfDeliveryItems |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems |
| stereotype_zib | container |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation |
| alias_zib | NL: DatumLaatsteMenstruatie |
| card._zib | 0..1 |
| definition_zib | The date on which the last menstruation started. |
| definitioncode_zib | SNOMED CT: 21840007 Date of last menstrual period |
| id_zib | NL-CM:7.14.8 |
| name_zib | DateLastMenstruation |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation |
| alias_zib | NL: DatumBepaling |
| card._zib | 0..1 |
| definition_zib | Date on which the delivery date is estimated. |
| id_zib | NL-CM:7.14.11 |
| name_zib | DateOfEstimation |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod |
| alias_zib | NL: BepalingsMethode |
| card._zib | 0..1 |
| definition_zib | Method by which the delivery date is estimated. |
| id_zib | NL-CM:7.14.10 |
| name_zib | EstimatingMethod |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Pregnancy.Gravidity

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.Gravidity |
| alias_zib | NL: Graviditeit |
| card._zib | 0..1 |
| definition_zib | The number of times the woman has gotten pregnant (including this one). |
| definitioncode_zib | SNOMED CT: 161732006 Gravida |
| id_zib | NL-CM:7.14.5 |
| name_zib | Gravidity |
| path_zib | Pregnancy.Gravidity |
| stereotype_zib | data |
| type_zib | INT |

### Comments



## zib: Pregnancy.Parity

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.Parity |
| alias_zib | NL: Pariteit |
| card._zib | 0..1 |
| definition_zib | Number of previous pregnancies ending in partum (>= 16w 0d / 112 days). |
| definitioncode_zib | SNOMED CT: 364325004 Parity |
| id_zib | NL-CM:7.14.6 |
| name_zib | Parity |
| path_zib | Pregnancy.Parity |
| stereotype_zib | data |
| type_zib | INT |

### Comments

