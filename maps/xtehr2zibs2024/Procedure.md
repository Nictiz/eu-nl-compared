# Procedure

| zib                                                       | xtehr                                     | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:----------------------------------------------------------|:------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Procedure                                                 | EHDSProcedure                             |            |                        |             | 0..*          |
| Procedure.ProcedureAnatomicalLocation::AnatomicalLocation | EHDSProcedure.bodySite                    |            | EHDSBodyStructure      | 0..1        | 0..*          |
| Procedure.ProcedureType                                   | EHDSProcedure.code                        | CD         | CodeableConcept        | 1           | 0..1          |
|                                                           | EHDSProcedure.complication                |            | CodeableConcept        |             | 0..*          |
| Procedure.ProcedureEndDate                                | EHDSProcedure.date[x]                     | TS         | dateTime               | 0..1        | 0..1          |
| Procedure.ProcedureStartDate                              | EHDSProcedure.date[x]                     | TS         | dateTime               | 0..1        | 0..1          |
|                                                           | EHDSProcedure.deviceUsed                  |            | EHDSDevice             |             | 0..*          |
| Procedure.MedicalDevice                                   | EHDSProcedure.focalDevice                 |            | EHDSDevice             | 0..*        | 0..*          |
| Registratiegegevens, zie DataSet mapping                  | EHDSProcedure.header                      |            | Base                   |             | 1..1          |
|                                                           | EHDSProcedure.header.authorship           |            | Base                   |             | 1..*          |
|                                                           | EHDSProcedure.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                           | EHDSProcedure.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                           | EHDSProcedure.header.identifier           |            | Identifier             |             | 0..*          |
|                                                           | EHDSProcedure.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                           | EHDSProcedure.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                           | EHDSProcedure.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                           | EHDSProcedure.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                           | EHDSProcedure.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                           | EHDSProcedure.header.version              |            | string                 |             | 0..1          |
| Procedure.Location::HealthcareProvider                    | EHDSProcedure.location                    |            |                        | 0..1        |               |
|                                                           | EHDSProcedure.note                        |            | string                 |             | 0..1          |
|                                                           | EHDSProcedure.outcome                     |            | CodeableConcept        |             | 0..1          |
| Procedure.Performer::HealthProfessional                   | EHDSProcedure.performer                   |            | EHDSHealthProfessional | 0..*        | 0..*          |
|                                                           | EHDSProcedure.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| Procedure.Indication                                      | EHDSProcedure.reason[x]                   |            | CodeableConcept        | 0..*        | 0..*          |
| Procedure.Indication.Diagnosis                            | EHDSProcedure.reason[x]                   |            | CodeableConcept        | (0..1)      | 0..*          |
| Procedure.Indication.Reaction                             | EHDSProcedure.reason[x]                   |            | CodeableConcept        | (0..1)      | 0..*          |
| Procedure.Indication.Symptom                              | EHDSProcedure.reason[x]                   |            | CodeableConcept        | (0..1)      | 0..*          |
| Procedure.Indication::Problem                             | EHDSProcedure.reason[x]                   |            | CodeableConcept        |             | 0..*          |
| Procedure.ProcedureMethod                                 |                                           | CD         |                        | 0..*        |               |
| Procedure.Requester::HealthProfessional                   |                                           |            |                        |             |               |



## EHDSProcedure

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure |
| zib | Procedure |
| alias_zib | NL: Verrichting |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for an action that is or was performed on or for a patient |
| definition_zib | Root concept of the Procedure information model. This root concept contains all data elements of the Procedure information model. |
| definitioncode_zib | SNOMED CT: 71388002 Procedure |
| id_xtehr | EHDSProcedure |
| id_zib | NL-CM:14.1.1 |
| name_zib | Procedure |
| path_xtehr | EHDSProcedure |
| path_zib | Procedure |
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
| zib | Procedure.ProcedureAnatomicalLocation::AnatomicalLocation |
| alias_zib | NL: VerrichtingAnatomischeLocatie::AnatomischeLocatie |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Procedure target body site. Details of where the procedure was performed. Laterality may be included as qualifier of the body site. |
| definition_zib | Anatomical location that is the focus of the procedure. |
| definitioncode_zib | SNOMED CT: 405813007 Procedure site - Direct |
| id_xtehr | EHDSProcedure.bodySite |
| id_zib | NL-CM:14.1.13 |
| name_zib | ProcedureAnatomicalLocation::AnatomicalLocation |
| path_xtehr | EHDSProcedure.bodySite |
| path_zib | Procedure.ProcedureAnatomicalLocation::AnatomicalLocation |
| short_xtehr | Procedure target body site. Details of where the procedure was performed. Laterality may be included as qualifier of the body site. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSBodyStructure |
| type_zib |  |

### Comments



## EHDSProcedure.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.code |
| zib | Procedure.ProcedureType |
| alias_zib | NL: VerrichtingType |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Code identifying the procedure |
| definition_zib | The name of the procedure.<br />Choices are the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG). |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.code |
| id_zib | NL-CM:14.1.4 |
| name_zib | ProcedureType |
| path_xtehr | EHDSProcedure.code |
| path_zib | Procedure.ProcedureType |
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
| zib | Procedure.ProcedureEndDate |
| alias_zib | NL: VerrichtingEindDatum |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the procedure or interval of its performance |
| definition_zib | The end date (and if possible end time) of the procedure. A ‘vague’ date, such as only the year, is permitted. 
The element offers the option to indicate the end of the period of a series of related procedures. The end date element is only used for a procedures that takes some time and is then always applied. If the procedure still continues, the value is left empty. For instantaneous or very short lasting procedures the element is omitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.date[x] |
| id_zib | NL-CM:14.1.3 |
| name_zib | ProcedureEndDate |
| path_xtehr | EHDSProcedure.date[x] |
| path_zib | Procedure.ProcedureEndDate |
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
| zib | Procedure.ProcedureStartDate |
| alias_zib | NL: VerrichtingStartDatum |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the procedure or interval of its performance |
| definition_zib | The (desired) start date (and if possible start time) of the procedure. A ‘vague’ date, such as only the year, is permitted. 
The element offers the option to indicate the start of the period of a series of related procedures. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.date[x] |
| id_zib | NL-CM:14.1.2 |
| name_zib | ProcedureStartDate |
| path_xtehr | EHDSProcedure.date[x] |
| path_zib | Procedure.ProcedureStartDate |
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
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Device used to perform the procedure |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.deviceUsed |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.deviceUsed |
| path_zib |  |
| short_xtehr | Device used to perform the procedure |
| stereotype_zib |  |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments



## EHDSProcedure.focalDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.focalDevice |
| zib | Procedure.MedicalDevice |
| alias_zib | NL: MedischHulpmiddel |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| definition_zib | The product, the placing of which in or on the body is the purpose of the procedure, for example placing an implant. |
| definitioncode_zib | SNOMED CT: 405815000 Procedure device |
| id_xtehr | EHDSProcedure.focalDevice |
| id_zib | NL-CM:14.1.7 |
| name_zib | MedicalDevice |
| path_xtehr | EHDSProcedure.focalDevice |
| path_zib | Procedure.MedicalDevice |
| short_xtehr | Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments



## EHDSProcedure.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header |
| zib | Registratiegegevens, zie DataSet mapping |
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



## EHDSProcedure.location

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.location |
| zib | Procedure.Location::HealthcareProvider |
| alias_zib | NL: Locatie::Zorgaanbieder |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The healthcare provider where the procedure was, is or will be carried out. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.1.5 |
| name_zib | Location::HealthcareProvider |
| path_xtehr |  |
| path_zib | Procedure.Location::HealthcareProvider |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSProcedure.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.note |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Additional information about the procedure |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.note |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.note |
| path_zib |  |
| short_xtehr | Additional information about the procedure |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

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
| zib | Procedure.Performer::HealthProfessional |
| alias_zib | NL: Uitvoerder::Zorgverlener |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | An actor who performed the procedure |
| definition_zib | The healthcare professional who carried out or will carry out the procedure. In most cases, only the medical specialty is entered, and not the name of the healthcare professional. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.performer |
| id_zib | NL-CM:14.1.6 |
| name_zib | Performer::HealthProfessional |
| path_xtehr | EHDSProcedure.performer |
| path_zib | Procedure.Performer::HealthProfessional |
| short_xtehr | An actor who performed the procedure |
| stereotype_zib | context,reference |
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
| zib | Procedure.Indication |
| alias_zib | NL: Indicatie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | Container of the Indication concept.This container contains all data elements of the Indication concept. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.14 |
| name_zib | Indication |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib | container |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | Procedure.Indication.Diagnosis |
| alias_zib | NL: Diagnose |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | A diagnosis that serves as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.15 |
| name_zib | Diagnosis |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication.Diagnosis |
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
| zib | Procedure.Indication.Reaction |
| alias_zib | NL: Reactie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | An undesired reaction to a substance or radiation that served as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.16 |
| name_zib | Reaction |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication.Reaction |
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
| zib | Procedure.Indication.Symptom |
| alias_zib | NL: Symptoom |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | A symptom that serves as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.17 |
| name_zib | Symptom |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication.Symptom |
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
| zib | Procedure.Indication::Problem |
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



## zib: Procedure.ProcedureMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Procedure.ProcedureMethod |
| alias_zib | NL: VerrichtingMethode |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..* |
| definition_xtehr |  |
| definition_zib | The method or technique that is going to be or was used to perform the procedure, e.g. approach, lavage, pressuring, etc. |
| definitioncode_zib | SNOMED CT: 260686004 Method |
| id_xtehr |  |
| id_zib | NL-CM:14.1.12 |
| name_zib | ProcedureMethod |
| path_xtehr |  |
| path_zib | Procedure.ProcedureMethod |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: Procedure.Requester::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Procedure.Requester::HealthProfessional |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib |  |
| definition_xtehr |  |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib |  |
| name_zib |  |
| path_xtehr |  |
| path_zib |  |
| short_xtehr |  |
| stereotype_zib |  |
| type_xtehr |  |
| type_zib |  |

### Comments

