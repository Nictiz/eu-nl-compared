# PregnancyHistory

| zib                                                            | xtehr                                 | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:---------------------------------------------------------------|:--------------------------------------|:-----------|:----------------|:------------|:--------------|
| Pregnancy                                                      | EHDSPregnancyHistory                  |            |                 |             | 0..*          |
|                                                                | EHDSPregnancyHistory.narrative        |            | string          |             | 0..1          |
|                                                                | EHDSPregnancyHistory.numberOfChildren |            | integer         |             | 0..1          |
|                                                                | EHDSPregnancyHistory.outcome          |            | CodeableConcept |             | 0..1          |
|                                                                | EHDSPregnancyHistory.outcomeDate      |            | dateTime        |             | 0..1          |
|                                                                | EHDSPregnancyHistory.presentedForm    |            | EHDSAttachment  |             | 0..*          |
| Pregnancy.Comment                                              |                                       | ST         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems                         |                                       |            |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation    |                                       | TS         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation        |                                       | TS         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |                                       | TS         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod        |                                       | CD         |                 | 0..1        |               |
| Pregnancy.Gravidity                                            |                                       | INT        |                 | 0..1        |               |
| Pregnancy.Parity                                               |                                       | INT        |                 | 0..1        |               |
| Pregnancy.PregnancyDuration                                    |                                       | PQ         |                 | 0..1        |               |



## EHDSPregnancyHistory

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory |
| zib | Pregnancy |
| alias_zib | NL: Zwangerschap |
| card._xtehr | 0..* |
| definition_xtehr | Pregnancy history for one pregnancy |
| definition_zib | Root concept of the Pregnancy information model. This root concept contains all data elements of the Pregnancy information model. |
| definitioncode_zib | SNOMED CT: 118185001 Finding related to pregnancy |
| id_xtehr | EHDSPregnancyHistory |
| id_zib | NL-CM:7.14.1 |
| name_zib | Pregnancy |
| path_xtehr | EHDSPregnancyHistory |
| path_zib | Pregnancy |
| short_xtehr | Pregnancy history model |
| stereotype_zib | rootconcept |

### Comments



## EHDSPregnancyHistory.narrative

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.narrative |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Narrative description describing the outcome of any previous pregnancies. |
| id_xtehr | EHDSPregnancyHistory.narrative |
| path_xtehr | EHDSPregnancyHistory.narrative |
| short_xtehr | Narrative, potentially formatted, content of the section |
| type_xtehr | string |

### Comments



## EHDSPregnancyHistory.numberOfChildren

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.numberOfChildren |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Number of children/fetuses in this specific pregnancy |
| id_xtehr | EHDSPregnancyHistory.numberOfChildren |
| path_xtehr | EHDSPregnancyHistory.numberOfChildren |
| short_xtehr | Number of children/fetuses in this specific pregnancy |
| type_xtehr | integer |

### Comments



## EHDSPregnancyHistory.outcome

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.outcome |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.62 eHDSIOutcomeOfPregnancy (SNOMED CT, used in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.63 eHDSIRareDisease (OrphaCodes, used in MH@EU); ICD-11; SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Outcome of the previous pregnancy. |
| id_xtehr | EHDSPregnancyHistory.outcome |
| path_xtehr | EHDSPregnancyHistory.outcome |
| short_xtehr | Outcome |
| type_xtehr | CodeableConcept |

### Comments



## EHDSPregnancyHistory.outcomeDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.outcomeDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date referred to the previous pregnancies outcome. |
| id_xtehr | EHDSPregnancyHistory.outcomeDate |
| path_xtehr | EHDSPregnancyHistory.outcomeDate |
| short_xtehr | Outcome date |
| type_xtehr | dateTime |

### Comments



## EHDSPregnancyHistory.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSPregnancyHistory.presentedForm |
| path_xtehr | EHDSPregnancyHistory.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## zib: Pregnancy.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comment on the pregnancy. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:7.14.7 |
| name_zib | Comment |
| path_zib | Pregnancy.Comment |
| stereotype_zib | data |
| type_zib | ST |

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



## zib: Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| alias_zib | NL: ATermeDatum |
| card._zib | 0..1 |
| definition_zib | The date on which the pregnancy is expected to be 40w 0d (280 days). Different due dates are used at various points in the pregnancy. |
| definitioncode_zib | SNOMED CT: 161714006 Estimated date of delivery |
| id_zib | NL-CM:7.14.3 |
| name_zib | EstimatedDateOfDelivery |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
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



## zib: Pregnancy.PregnancyDuration

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.PregnancyDuration |
| alias_zib | NL: Zwangerschapsduur |
| card._zib | 0..1 |
| definition_zib | Duration of the pregnancy on the day on which the patient was asked. The duration can be given in days (d) or weeks (wk). |
| definitioncode_zib | SNOMED CT: 57036006 Fetal gestational age |
| id_zib | NL-CM:7.14.4 |
| name_zib | PregnancyDuration |
| path_zib | Pregnancy.PregnancyDuration |
| stereotype_zib | data |
| type_zib | PQ |

### Comments

