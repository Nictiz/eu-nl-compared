# Condition

| zib                                                           | xtehr                                     | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------------------------------|:------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Condition                                                     | EHDSCondition                             |            |                        |             | 0..*          |
| Diagnosis                                                     | EHDSCondition                             |            |                        |             | 0..*          |
| Diagnosis.AnatomicalLocation                                  | EHDSCondition.anatomicLocation            |            | EHDSBodyStructure      | 0..*        | 0..*          |
| Diagnosis.DiagnosisDate                                       | EHDSCondition.assertedDate                | TS         | dateTime               | 1           | 0..1          |
| Diagnosis.Diagnostician::HealthProfessional                   | EHDSCondition.asserter                    |            | EHDSHealthProfessional | 1           | 0..1          |
|                                                               | EHDSCondition.category                    |            | CodeableConcept        |             | 0..*          |
| Diagnosis.DiagnosisStatus                                     | EHDSCondition.diagnosisAssertionStatus    | CD         | CodeableConcept        | 1           | 0..1          |
| Condition.PeriodPresent::TimeInterval                         | EHDSCondition.endDate                     |            | dateTime               | 1           | 0..1          |
|                                                               | EHDSCondition.externalResource            |            | uri                    |             | 0..*          |
|                                                               | EHDSCondition.header                      |            | Base                   |             | 1..1          |
|                                                               | EHDSCondition.header.authorship           |            | Base                   |             | 1..*          |
|                                                               | EHDSCondition.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                               | EHDSCondition.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                               | EHDSCondition.header.identifier           |            | Identifier             |             | 0..*          |
|                                                               | EHDSCondition.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                               | EHDSCondition.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                               | EHDSCondition.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                               | EHDSCondition.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                               | EHDSCondition.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                               | EHDSCondition.header.version              |            | string                 |             | 0..1          |
| Condition.PeriodPresent::TimeInterval                         | EHDSCondition.onsetDate                   |            | dateTime               | 1           | 0..1          |
|                                                               | EHDSCondition.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| Diagnosis.DiagnosisNameData.DiagnosisName                     | EHDSCondition.problem                     | CD         | CodeableConcept        | 1           | 1..1          |
| Condition.Course                                              | EHDSCondition.problemStatus               | CD         | CodeableConcept        | 0..1        | 0..1          |
|                                                               | EHDSCondition.resolutionCircumstances     |            | string                 |             | 0..*          |
| Condition.Severity                                            | EHDSCondition.severity                    | CD         | CodeableConcept        | 1           | 0..1          |
|                                                               | EHDSCondition.specialistContact           |            | EHDSHealthProfessional |             | 0..*          |
|                                                               | EHDSCondition.stage                       |            | CodeableConcept        |             | 0..*          |
| Condition.Comment                                             |                                           | ST         |                        | 0..1        |               |
| Condition.StatusDate                                          |                                           | TS         |                        | 1           |               |
| Diagnosis.Comment                                             |                                           | ST         |                        | 0..1        |               |
| Diagnosis.Condition                                           |                                           |            |                        | 0..1        |               |
| Diagnosis.DiagnosisNameData                                   |                                           |            |                        | 1..*        |               |
| Diagnosis.DiagnosisNameData.FurtherSpecificationDiagnosisName |                                           | ST         |                        | 0..1        |               |
| Diagnosis.IsComplication                                      |                                           | BL         |                        | 0..1        |               |
| Diagnosis.MethodOfConfirmation                                |                                           | CD         |                        | 1           |               |
| Diagnosis.Reason                                              |                                           |            |                        | 0..*        |               |
| Diagnosis.Reason.Diagnosis                                    |                                           |            |                        | (0..1)      |               |
| Diagnosis.Reason.Incident                                     |                                           | CD         |                        | (0..1)      |               |
| Diagnosis.Reason.Procedure                                    |                                           |            |                        | (0..1)      |               |



## EHDSCondition

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition |
| zib | Condition |
| alias_zib | NL: AandoeningOfGesteldheid |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for a clinical condition, problem, diagnosis, or other event, situation, issue, or clinical concept that has risen to a level of concern. |
| definition_zib | This is a reference to the root concept of information model Condition. This root concept contains all data elements of the information model Condition. |
| definitioncode_zib | SNOMED CT: 64572001 Disease |
| id_xtehr | EHDSCondition |
| id_zib | NL-CM:5.4.1 |
| name_zib | Condition |
| path_xtehr | EHDSCondition |
| path_zib | Condition |
| short_xtehr | Condition model |
| stereotype_zib | rootconcept |

### Comments



## EHDSCondition

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition |
| zib | Diagnosis |
| alias_zib | NL: Diagnose |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for a clinical condition, problem, diagnosis, or other event, situation, issue, or clinical concept that has risen to a level of concern. |
| definition_zib | Root concept of the Diagnosis information model. This root concept contains all data elements of the Diagnosis information model. |
| definitioncode_zib | SNOMED CT: 404684003 Clinical finding |
| id_xtehr | EHDSCondition |
| id_zib | NL-CM:5.6.1 |
| name_zib | Diagnosis |
| path_xtehr | EHDSCondition |
| path_zib | Diagnosis |
| short_xtehr | Condition model |
| stereotype_zib | rootconcept |

### Comments



## EHDSCondition.anatomicLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.anatomicLocation |
| zib | Diagnosis.AnatomicalLocation |
| alias_zib | NL: AnatomischeLocatie |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | The anatomical location including laterality where this condition manifests itself. |
| definition_zib | The location(s) on and/or in the body that is/are affected by the condition, conform the diagnostics. |
| definitioncode_zib | SNOMED CT: 123037004 Body structure |
| id_xtehr | EHDSCondition.anatomicLocation |
| id_zib | NL-CM:5.6.9 |
| name_zib | AnatomicalLocation |
| path_xtehr | EHDSCondition.anatomicLocation |
| path_zib | Diagnosis.AnatomicalLocation |
| short_xtehr | The anatomical location including laterality where this condition manifests itself. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSBodyStructure |

### Comments



## EHDSCondition.assertedDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.assertedDate |
| zib | Diagnosis.DiagnosisDate |
| alias_zib | NL: DiagnoseDatum |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Date and time of the diagnosis assertion |
| definition_zib | Date (and time) at which the care professional came to the diagnosis. |
| definitioncode_zib | SNOMED CT: 432213005 Date of diagnosis |
| id_xtehr | EHDSCondition.assertedDate |
| id_zib | NL-CM:5.6.3 |
| name_zib | DiagnosisDate |
| path_xtehr | EHDSCondition.assertedDate |
| path_zib | Diagnosis.DiagnosisDate |
| short_xtehr | Date and time of the diagnosis assertion |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSCondition.asserter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.asserter |
| zib | Diagnosis.Diagnostician::HealthProfessional |
| alias_zib | NL: DiagnoseSteller::Zorgverlener |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The asserter of the condition |
| definition_zib | The care professional who made the diagnosis. This can be a different individual than the person who recorded the diagnosis. |
| definitioncode_zib | PRF performer |
| id_xtehr | EHDSCondition.asserter |
| id_zib | NL-CM:5.6.2 |
| name_zib | Diagnostician::HealthProfessional |
| path_xtehr | EHDSCondition.asserter |
| path_zib | Diagnosis.Diagnostician::HealthProfessional |
| short_xtehr | The asserter of the condition |
| stereotype_zib | context,reference |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSCondition.category

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.category |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Category or categories of the problem (e.g. POA - present on admission, HAC - hospital aquired condition, and other categorisations). |
| id_xtehr | EHDSCondition.category |
| path_xtehr | EHDSCondition.category |
| short_xtehr | Category or categories of the problem (e.g. POA - present on admission, HAC - hospital aquired condition, and other categorisations). |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCondition.diagnosisAssertionStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.diagnosisAssertionStatus |
| zib | Diagnosis.DiagnosisStatus |
| alias_zib | NL: DiagnoseStatus |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Condition Verification Status'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Assertion about the certainty associated with a diagnosis. Diagnostic and/or clinical evidence of condition. |
| definition_zib | Indicates the status of the diagnostic process. |
| id_xtehr | EHDSCondition.diagnosisAssertionStatus |
| id_zib | NL-CM:5.6.4 |
| name_zib | DiagnosisStatus |
| path_xtehr | EHDSCondition.diagnosisAssertionStatus |
| path_zib | Diagnosis.DiagnosisStatus |
| short_xtehr | Assertion about the certainty associated with a diagnosis. Diagnostic and/or clinical evidence of condition. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSCondition.endDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.endDate |
| zib | Condition.PeriodPresent::TimeInterval |
| alias_zib | NL: PeriodeAanwezig::TijdsInterval |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The date or estimated date that the condition resolved or went into remission |
| definition_zib | The period in which the condition is (was) present. |
| id_xtehr | EHDSCondition.endDate |
| id_zib | NL-CM:5.4.8 |
| name_zib | PeriodPresent::TimeInterval |
| path_xtehr | EHDSCondition.endDate |
| path_zib | Condition.PeriodPresent::TimeInterval |
| short_xtehr | The date or estimated date that the condition resolved or went into remission |
| stereotype_zib | data,reference |
| type_xtehr | dateTime |

### Comments



## EHDSCondition.externalResource

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.externalResource |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | External Resource which may be specifically related to the problem, for example a link between a rare disease problem and the corresponding guidelines. |
| id_xtehr | EHDSCondition.externalResource |
| path_xtehr | EHDSCondition.externalResource |
| short_xtehr | External Resource which may be specifically related to the problem, for example a link between a rare disease problem and the corresponding guidelines. |
| type_xtehr | uri |

### Comments



## EHDSCondition.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSCondition.header |
| path_xtehr | EHDSCondition.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSCondition.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSCondition.header.authorship |
| path_xtehr | EHDSCondition.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSCondition.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSCondition.header.authorship.author[x] |
| path_xtehr | EHDSCondition.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSCondition.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSCondition.header.authorship.datetime |
| path_xtehr | EHDSCondition.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSCondition.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSCondition.header.identifier |
| path_xtehr | EHDSCondition.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSCondition.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSCondition.header.language |
| path_xtehr | EHDSCondition.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCondition.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSCondition.header.lastUpdate |
| path_xtehr | EHDSCondition.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSCondition.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSCondition.header.status |
| path_xtehr | EHDSCondition.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCondition.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSCondition.header.statusReason[x] |
| path_xtehr | EHDSCondition.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSCondition.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSCondition.header.subject |
| path_xtehr | EHDSCondition.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSCondition.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSCondition.header.version |
| path_xtehr | EHDSCondition.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSCondition.onsetDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.onsetDate |
| zib | Condition.PeriodPresent::TimeInterval |
| alias_zib | NL: PeriodeAanwezig::TijdsInterval |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Onset date of a problem/condition |
| definition_zib | The period in which the condition is (was) present. |
| id_xtehr | EHDSCondition.onsetDate |
| id_zib | NL-CM:5.4.8 |
| name_zib | PeriodPresent::TimeInterval |
| path_xtehr | EHDSCondition.onsetDate |
| path_zib | Condition.PeriodPresent::TimeInterval |
| short_xtehr | Onset date of a problem/condition |
| stereotype_zib | data,reference |
| type_xtehr | dateTime |

### Comments



## EHDSCondition.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSCondition.presentedForm |
| path_xtehr | EHDSCondition.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSCondition.problem

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.problem |
| zib | Diagnosis.DiagnosisNameData.DiagnosisName |
| alias_zib | NL: DiagnoseNaam |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT, ICD-O, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Code identifying the condition, problem or diagnosis |
| definition_zib | The term with associated code that the care professional selects from the used code system with conditions. |
| definitioncode_zib | SNOMED CT: 439401001 Diagnosis |
| id_xtehr | EHDSCondition.problem |
| id_zib | NL-CM:5.6.7 |
| name_zib | DiagnosisName |
| path_xtehr | EHDSCondition.problem |
| path_zib | Diagnosis.DiagnosisNameData.DiagnosisName |
| short_xtehr | Code identifying the condition, problem or diagnosis |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSCondition.problemStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.problemStatus |
| zib | Condition.Course |
| alias_zib | NL: Beloop |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Condition Clinical Status Codes'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Status of the condition/problem (active, resolved, inactive, ...) |
| definition_zib | The course of the condition. This is independent of the diagnostic insight for the condition. The course indicates how the condition is developing: such as stable, progression, remission, etc.. |
| id_xtehr | EHDSCondition.problemStatus |
| id_zib | NL-CM:5.4.5 |
| name_zib | Course |
| path_xtehr | EHDSCondition.problemStatus |
| path_zib | Condition.Course |
| short_xtehr | Status of the condition/problem (active, resolved, inactive, ...) |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSCondition.resolutionCircumstances

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.resolutionCircumstances |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | This field includes free text if the resolution circumstances are not already included in other fields such as surgical procedure, medical device, etc., e.g. hepatic cystectomy (this will be the resolution circumstances for the problem "hepatic cyst" and will be included in surgical procedures). |
| id_xtehr | EHDSCondition.resolutionCircumstances |
| path_xtehr | EHDSCondition.resolutionCircumstances |
| short_xtehr | Describes the reason for which the status of the problem changed from current to inactive (e.g. surgical procedure, medical treatment, etc.). |
| type_xtehr | string |

### Comments



## EHDSCondition.severity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.severity |
| zib | Condition.Severity |
| alias_zib | NL: Ernst |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Condition/Diagnosis Severity; SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | A subjective assessment of the severity of the condition as evaluated by the clinician. |
| definition_zib | Indication of the severity of the condition. A condition may cause few or mild symptoms and yet be serious, but the reverse is also possible. |
| definitioncode_zib | SNOMED CT: 246112005 Severity |
| id_xtehr | EHDSCondition.severity |
| id_zib | NL-CM:5.4.6 |
| name_zib | Severity |
| path_xtehr | EHDSCondition.severity |
| path_zib | Condition.Severity |
| short_xtehr | A subjective assessment of the severity of the condition as evaluated by the clinician. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSCondition.specialistContact

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.specialistContact |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Health Professional who may be specifically related to the problem, as a preferred contact. |
| id_xtehr | EHDSCondition.specialistContact |
| path_xtehr | EHDSCondition.specialistContact |
| short_xtehr | Health Professional who may be specifically related to the problem, as a preferred contact. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSCondition.stage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCondition.stage |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'e.g. TNM, ICD-O-3, Bi-Rads, Li-Rads, …'} |
| card._xtehr | 0..* |
| definition_xtehr | Stage/grade usually assessed formally using a specific staging/grading system. Multiple assessment systems could be used. |
| id_xtehr | EHDSCondition.stage |
| path_xtehr | EHDSCondition.stage |
| short_xtehr | Stage/grade usually assessed formally using a specific staging/grading system. Multiple assessment systems could be used. |
| type_xtehr | CodeableConcept |

### Comments



## zib: Condition.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Condition.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | A comment in free text with respect to the condition, that is not represented by the other data elements in the information model. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:5.4.7 |
| name_zib | Comment |
| path_zib | Condition.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Condition.StatusDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Condition.StatusDate |
| alias_zib | NL: StatusDatum |
| card._zib | 1 |
| definition_zib | The moment from when the data regarding the condition apply. It may be a vague moment. |
| definitioncode_zib | SNOMED CT: 350351000146106 Date health condition changed |
| id_zib | NL-CM:5.4.3 |
| name_zib | StatusDate |
| path_zib | Condition.StatusDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Diagnosis.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | A comment in free text with respect to the diagnosis, that is not represented by the other data elements in the information model. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:5.6.11 |
| name_zib | Comment |
| path_zib | Diagnosis.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Diagnosis.Condition

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.Condition |
| alias_zib | NL: AandoeningOfGesteldheid |
| card._zib | 0..1 |
| definition_zib | The Condition to which the Diagnosis applies. |
| id_zib | NL-CM:5.6.10 |
| name_zib | Condition |
| path_zib | Diagnosis.Condition |
| stereotype_zib | data,reference |

### Comments



## zib: Diagnosis.DiagnosisNameData

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.DiagnosisNameData |
| alias_zib | NL: DiagnoseNaamGegevens |
| card._zib | 1..* |
| definition_zib | Container of the DiagnosisNameData concept. This container contains all data elements of the DiagnosisNameData concept.
Represents a disease or physiological condition as part of the diagnosis. |
| id_zib | NL-CM:5.6.6 |
| name_zib | DiagnosisNameData |
| path_zib | Diagnosis.DiagnosisNameData |
| stereotype_zib | container |

### Comments



## zib: Diagnosis.DiagnosisNameData.FurtherSpecificationDiagnosisName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.DiagnosisNameData.FurtherSpecificationDiagnosisName |
| alias_zib | NL: NadereSpecificatieDiagnoseNaam |
| card._zib | 0..1 |
| definition_zib | A more detailed description of the DiagnosisName in free text, when this detail is not available in the used code list. |
| id_zib | NL-CM:5.6.8 |
| name_zib | FurtherSpecificationDiagnosisName |
| path_zib | Diagnosis.DiagnosisNameData.FurtherSpecificationDiagnosisName |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Diagnosis.IsComplication

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.IsComplication |
| alias_zib | NL: IsComplicatie |
| card._zib | 0..1 |
| definition_zib | Indicates whether or not the diagnosis involves a complication. |
| id_zib | NL-CM:5.6.12 |
| name_zib | IsComplication |
| path_zib | Diagnosis.IsComplication |
| stereotype_zib | data |
| type_zib | BL |

### Comments



## zib: Diagnosis.MethodOfConfirmation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.MethodOfConfirmation |
| alias_zib | NL: WijzeVanVaststellen |
| card._zib | 1 |
| definition_zib | The method that the care professional used to diagnose the condition, such as history taking only, history taking and physical examination or additional diagnostic examination. |
| definitioncode_zib | SNOMED CT: 418775008 Finding method |
| id_zib | NL-CM:5.6.5 |
| name_zib | MethodOfConfirmation |
| path_zib | Diagnosis.MethodOfConfirmation |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Diagnosis.Reason

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.Reason |
| alias_zib | NL: Aanleiding |
| card._zib | 0..* |
| definition_zib | Container of the Reason concept.This container contains all data elements of the Reason concept. |
| id_zib | NL-CM:5.6.13 |
| name_zib | Reason |
| path_zib | Diagnosis.Reason |
| stereotype_zib | container |

### Comments



## zib: Diagnosis.Reason.Diagnosis

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.Reason.Diagnosis |
| alias_zib | NL: Diagnose |
| card._zib | (0..1) |
| definition_zib | The diagnosis with regard to another condition that is seen as a reason for the condition with the current diagnosis. |
| id_zib | NL-CM:5.6.16 |
| name_zib | Diagnosis |
| path_zib | Diagnosis.Reason.Diagnosis |
| stereotype_zib | data,reference |

### Comments



## zib: Diagnosis.Reason.Incident

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.Reason.Incident |
| alias_zib | NL: Incident |
| card._zib | (0..1) |
| definition_zib | The unintended event during the care process that has led, could have led or could (still) lead to harm to the patient. |
| definitioncode_zib | SNOMED CT: 418019003 Accidental event |
| id_zib | NL-CM:5.6.14 |
| name_zib | Incident |
| path_zib | Diagnosis.Reason.Incident |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Diagnosis.Reason.Procedure

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Diagnosis.Reason.Procedure |
| alias_zib | NL: Verrichting |
| card._zib | (0..1) |
| definition_zib | The procedure that gave rise to the condition to which the diagnosis relates. |
| definitioncode_zib | SNOMED CT: 71388002 Procedure |
| id_zib | NL-CM:5.6.15 |
| name_zib | Procedure |
| path_zib | Diagnosis.Reason.Procedure |
| stereotype_zib | data,reference |

### Comments

