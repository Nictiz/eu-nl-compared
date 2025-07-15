# Procedure

| zib                                                    | xtehr                                     | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-------------------------------------------------------|:------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| NursingIntervention                                    | EHDSProcedure                             |            |                        |             | 0..*          |
|                                                        | EHDSProcedure.bodySite                    |            | EHDSBodyStructure      |             | 0..*          |
| NursingIntervention.Intervention                       | EHDSProcedure.code                        | CD         | CodeableConcept        | 1           | 0..1          |
|                                                        | EHDSProcedure.complication                |            | CodeableConcept        |             | 0..*          |
| NursingIntervention.ProcedureEndDateTime               | EHDSProcedure.date[x]                     | TS         | dateTime               | 0..1        | 0..1          |
| NursingIntervention.ProcedureStartDateTime             | EHDSProcedure.date[x]                     | TS         | dateTime               | 0..1        | 0..1          |
| NursingIntervention.MedicalDevice                      | EHDSProcedure.deviceUsed                  |            | EHDSDevice             | 0..*        | 0..*          |
|                                                        | EHDSProcedure.focalDevice                 |            | EHDSDevice             |             | 0..*          |
|                                                        | EHDSProcedure.header                      |            | Base                   |             | 1..1          |
|                                                        | EHDSProcedure.header.authorship           |            | Base                   |             | 1..*          |
|                                                        | EHDSProcedure.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                        | EHDSProcedure.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                        | EHDSProcedure.header.identifier           |            | Identifier             |             | 0..*          |
|                                                        | EHDSProcedure.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                        | EHDSProcedure.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                        | EHDSProcedure.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                        | EHDSProcedure.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                        | EHDSProcedure.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                        | EHDSProcedure.header.version              |            | string                 |             | 0..1          |
| NursingIntervention.Comment                            | EHDSProcedure.note                        | ST         | string                 | 0..1        | 0..1          |
|                                                        | EHDSProcedure.outcome                     |            | CodeableConcept        |             | 0..1          |
| NursingIntervention.Performer                          | EHDSProcedure.performer                   |            | EHDSHealthProfessional | 0..1        | 0..*          |
|                                                        | EHDSProcedure.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| NursingIntervention.Indication::NursingDiagnosis       | EHDSProcedure.reason[x]                   |            | CodeableConcept        | 0..1        | 0..*          |
| NursingIntervention.Indication::Problem                | EHDSProcedure.reason[x]                   |            | CodeableConcept        |             | 0..*          |
| NursingIntervention.Frequency                          |                                           | PQ         |                        | 0..1        |               |
| NursingIntervention.Instruction                        |                                           | ST         |                        | 0..1        |               |
| NursingIntervention.Interval                           |                                           | PQ         |                        | 0..1        |               |
| NursingIntervention.Performer.Caregiver::ContactPerson |                                           |            |                        | (0..1)      |               |
| NursingIntervention.Performer.HealthProfessional       |                                           |            |                        | (0..1)      |               |
| NursingIntervention.Performer.Patient                  |                                           |            |                        | (0..1)      |               |
| NursingIntervention.Requester::HealthProfessional      |                                           |            |                        | 0..*        |               |
| NursingIntervention.TreatmentObjective                 |                                           |            |                        | 0..1        |               |



## EHDSProcedure

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure |
| zib | NursingIntervention |
| alias_zib | NL: VerpleegkundigeInterventie |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for an action that is or was performed on or for a patient |
| definition_zib | Root concept of the NursingIntervention information model. This root concept contains all data elements of the NursingIntervention information model. |
| definitioncode_zib | SNOMED CT: 9632001 Nursing procedure |
| id_xtehr | EHDSProcedure |
| id_zib | NL-CM:14.2.1 |
| name_zib | NursingIntervention |
| path_xtehr | EHDSProcedure |
| path_zib | NursingIntervention |
| short_xtehr | Procedure model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSProcedure.bodySite

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.bodySite |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Procedure target body site. Details of where the procedure was performed. Laterality may be included as qualifier of the body site. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.bodySite |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.bodySite |
| path_zib |  |
| short_xtehr | Procedure target body site. Details of where the procedure was performed. Laterality may be included as qualifier of the body site. |
| stereotype_zib |  |
| type_xtehr | EHDSBodyStructure |
| type_zib |  |

### Comments



## EHDSProcedure.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.code |
| zib | NursingIntervention.Intervention |
| alias_zib | NL: Interventie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Code identifying the procedure |
| definition_zib | A nursing intervention is a treatment carried out by a nurse based on an expert opinion and clinical knowledge for the benefit of the person requesting healthcare. The intervention is targeted towards a certain problem (diagnosis) and has a predetermined healthcare result. It is possible to build a hierarchy of nursing interventions (where one intervention is part of another). |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.code |
| id_zib | NL-CM:14.2.2 |
| name_zib | Intervention |
| path_xtehr | EHDSProcedure.code |
| path_zib | NursingIntervention.Intervention |
| short_xtehr | Code identifying the procedure |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSProcedure.complication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.complication |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Any complications that occurred during the procedure, or in the immediate post-performance period. These are generally tracked separately from the procedure description, which will typically describe the procedure itself rather than any 'post procedure' issues. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.complication |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.complication |
| path_zib |  |
| short_xtehr | Any complications that occurred during the procedure, or in the immediate post-performance period. These are generally tracked separately from the procedure description, which will typically describe the procedure itself rather than any 'post procedure' issues. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.date[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.date[x] |
| zib | NursingIntervention.ProcedureEndDateTime |
| alias_zib | NL: ActieEindDatumTijd |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the procedure or interval of its performance |
| definition_zib | The end date (and if possible end time) of the procedure. The concept offers the option to indicate the end of the period of a series of repeating procedures. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.date[x] |
| id_zib | NL-CM:14.2.12 |
| name_zib | ProcedureEndDateTime |
| path_xtehr | EHDSProcedure.date[x] |
| path_zib | NursingIntervention.ProcedureEndDateTime |
| short_xtehr | Date and time of the procedure or interval of its performance |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSProcedure.date[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.date[x] |
| zib | NursingIntervention.ProcedureStartDateTime |
| alias_zib | NL: ActieStartDatumTijd |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the procedure or interval of its performance |
| definition_zib | The start date (and if possible start time) of the procedure. The concept offers the option to indicate the start of the period of a series of repeating procedures. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.date[x] |
| id_zib | NL-CM:14.2.11 |
| name_zib | ProcedureStartDateTime |
| path_xtehr | EHDSProcedure.date[x] |
| path_zib | NursingIntervention.ProcedureStartDateTime |
| short_xtehr | Date and time of the procedure or interval of its performance |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSProcedure.deviceUsed

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.deviceUsed |
| zib | NursingIntervention.MedicalDevice |
| alias_zib | NL: MedischHulpmiddel |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Device used to perform the procedure |
| definition_zib | Description of the materials used for the nursing procedure, such as bandages. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.deviceUsed |
| id_zib | NL-CM:14.2.13 |
| name_zib | MedicalDevice |
| path_xtehr | EHDSProcedure.deviceUsed |
| path_zib | NursingIntervention.MedicalDevice |
| short_xtehr | Device used to perform the procedure |
| stereotype_zib | data,reference |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments



## EHDSProcedure.focalDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.focalDevice |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.focalDevice |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.focalDevice |
| path_zib |  |
| short_xtehr | Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| stereotype_zib |  |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments



## EHDSProcedure.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Common header for all patient-related data |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header |
| path_zib |  |
| short_xtehr | Common header for all patient-related data |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSProcedure.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.authorship |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib |  |
| definition_xtehr | Resource authoring details |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.authorship |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.authorship |
| path_zib |  |
| short_xtehr | Authorship |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSProcedure.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.authorship.author[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.authorship.author[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.authorship.author[x] |
| path_zib |  |
| short_xtehr | Author |
| stereotype_zib |  |
| type_xtehr | EHDSHealthProfessional |
| type_zib |  |

### Comments



## EHDSProcedure.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.authorship.datetime |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.authorship.datetime |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.authorship.datetime |
| path_zib |  |
| short_xtehr | Date and time of authoring/issuing |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSProcedure.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.identifier |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Business identifier for the object |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.identifier |
| path_zib |  |
| short_xtehr | Business identifier for the object |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSProcedure.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.language |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.language |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.language |
| path_zib |  |
| short_xtehr | Language |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.lastUpdate |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Date and time of the last update to the document/information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.lastUpdate |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.lastUpdate |
| path_zib |  |
| short_xtehr | Date and time of the last update to the resource |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSProcedure.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.status |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Status of the resource |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.status |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.status |
| path_zib |  |
| short_xtehr | Status of the resource |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.statusReason[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Reason for the current status of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.statusReason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.statusReason[x] |
| path_zib |  |
| short_xtehr | Reason for the current status of the resource. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.subject |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Patient/subject information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.subject |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.subject |
| path_zib |  |
| short_xtehr | Subject |
| stereotype_zib |  |
| type_xtehr | EHDSPatient |
| type_zib |  |

### Comments



## EHDSProcedure.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.version |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Business version of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.version |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.version |
| path_zib |  |
| short_xtehr | Version |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSProcedure.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.note |
| zib | NursingIntervention.Comment |
| alias_zib | NL: Toelichting |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Additional information about the procedure |
| definition_zib | Comment on the nursing intervention. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSProcedure.note |
| id_zib | NL-CM:14.2.5 |
| name_zib | Comment |
| path_xtehr | EHDSProcedure.note |
| path_zib | NursingIntervention.Comment |
| short_xtehr | Additional information about the procedure |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSProcedure.outcome

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.outcome |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The outcome of the procedure - did it resolve the reasons for the procedure being performed? |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.outcome |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.outcome |
| path_zib |  |
| short_xtehr | The outcome of the procedure - did it resolve the reasons for the procedure being performed? |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.performer

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.performer |
| zib | NursingIntervention.Performer |
| alias_zib | NL: Uitvoerder |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | An actor who performed the procedure |
| definition_zib | The person carrying out the nursing procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.performer |
| id_zib | NL-CM:14.2.15 |
| name_zib | Performer |
| path_xtehr | EHDSProcedure.performer |
| path_zib | NursingIntervention.Performer |
| short_xtehr | An actor who performed the procedure |
| stereotype_zib | container |
| type_xtehr | EHDSHealthProfessional |
| type_zib |  |

### Comments



## EHDSProcedure.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.presentedForm |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.presentedForm |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.presentedForm |
| path_zib |  |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| stereotype_zib |  |
| type_xtehr | EHDSAttachment |
| type_zib |  |

### Comments



## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | NursingIntervention.Indication::NursingDiagnosis |
| alias_zib | NL: Indicatie::VerpleegkundigeDiagnose |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | The nursing diagnosis that serves as the indication for the nursing intervention. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.2.19 |
| name_zib | Indication::NursingDiagnosis |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | NursingIntervention.Indication::NursingDiagnosis |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | NursingIntervention.Indication::Problem |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib |  |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## zib: NursingIntervention.Frequency

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Frequency |
| alias_zib | NL: Frequentie |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The frequency describes how often and in which period certain procedures are carried out, e.g. 3x a day. |
| definitioncode_zib | SNOMED CT: 153681000146109 Procedure frequency |
| id_xtehr |  |
| id_zib | NL-CM:14.2.4 |
| name_zib | Frequency |
| path_xtehr |  |
| path_zib | NursingIntervention.Frequency |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | PQ |

### Comments



## zib: NursingIntervention.Instruction

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Instruction |
| alias_zib | NL: Instructie |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Instructions for performing the nursing action. This is particularly at issue when the action is performed by the patient himself or by a caregiver. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.2.18 |
| name_zib | Instruction |
| path_xtehr |  |
| path_zib | NursingIntervention.Instruction |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments



## zib: NursingIntervention.Interval

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Interval |
| alias_zib | NL: Interval |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Interval indicates the time between planned procedures.  
When entering an interval, the focus is on the time between the consecutive procedures, such as in the treatment of a wound, for example. The exact times are of lesser importance. |
| definitioncode_zib | SNOMED CT: 153691000146106 Interval between procedures |
| id_xtehr |  |
| id_zib | NL-CM:14.2.3 |
| name_zib | Interval |
| path_xtehr |  |
| path_zib | NursingIntervention.Interval |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | PQ |

### Comments



## zib: NursingIntervention.Performer.Caregiver::ContactPerson

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Performer.Caregiver::ContactPerson |
| alias_zib | NL: Verzorger::ContactPersoon |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | The caregiver carrying out the nursing procedure. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.2.16 |
| name_zib | Caregiver::ContactPerson |
| path_xtehr |  |
| path_zib | NursingIntervention.Performer.Caregiver::ContactPerson |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: NursingIntervention.Performer.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Performer.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | The health professional carrying out the nursing procedure. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.2.7 |
| name_zib | HealthProfessional |
| path_xtehr |  |
| path_zib | NursingIntervention.Performer.HealthProfessional |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: NursingIntervention.Performer.Patient

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Performer.Patient |
| alias_zib | NL: Patient |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | The patient carrying out the nursing procedure. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.2.17 |
| name_zib | Patient |
| path_xtehr |  |
| path_zib | NursingIntervention.Performer.Patient |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: NursingIntervention.Requester::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.Requester::HealthProfessional |
| alias_zib | NL: Aanvrager::Zorgverlener |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..* |
| definition_xtehr |  |
| definition_zib | The health professional who requested the nursing intervention. If desired, only the requester’s specialty can be entered. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.2.8 |
| name_zib | Requester::HealthProfessional |
| path_xtehr |  |
| path_zib | NursingIntervention.Requester::HealthProfessional |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: NursingIntervention.TreatmentObjective

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NursingIntervention.TreatmentObjective |
| alias_zib | NL: Behandeldoel |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The description of the treatment goal that the intervention decision is based on. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.2.14 |
| name_zib | TreatmentObjective |
| path_xtehr |  |
| path_zib | NursingIntervention.TreatmentObjective |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments

