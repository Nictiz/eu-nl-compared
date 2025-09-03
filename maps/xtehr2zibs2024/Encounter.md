# Encounter

| zib                                                           | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Encounter                                                     | EHDSEncounter                                  |            |                        |             | 0..*          |
|                                                               | EHDSEncounter.header                           |            | Base                   |             | 1..1          |
|                                                               | EHDSEncounter.priority                         |            | CodeableConcept        |             | 0..1          |
| Encounter.EncounterType                                       | EHDSEncounter.type                             | CD         | CodeableConcept        | 1           | 1..1          |
|                                                               | EHDSEncounter.note                             |            | string                 |             | 0..1          |
|                                                               | EHDSEncounter.episodeOfCare                    |            | EHDSEpisodeOfCare      |             | 0..*          |
|                                                               | EHDSEncounter.basedOn[x]                       |            | EHDSCarePlan           |             | 0..*          |
|                                                               | EHDSEncounter.partOf                           |            | EHDSEncounter          |             | 0..1          |
| Encounter.HealthProfessional                                  |                                                |            |                        | 1..*        |               |
| Encounter.Location::HealthcareProvider                        | EHDSEncounter.serviceProvider                  |            | EHDSOrganisation       | 1           | 0..1          |
| Encounter.DateTime                                            | EHDSEncounter.actualPeriod                     | TS         | Period                 | 1           | 0..1          |
| Encounter.DateTime                                            | EHDSEncounter.plannedStartDate                 | TS         | dateTime               | 1           | 0..1          |
|                                                               | EHDSEncounter.plannedEndDate                   |            | dateTime               |             | 0..1          |
|                                                               | EHDSEncounter.admission                        |            | Base                   |             | 0..1          |
|                                                               | EHDSEncounter.admission.admitter               |            | EHDSHealthProfessional |             | 0..1          |
|                                                               | EHDSEncounter.admission.admitSource            |            | CodeableConcept        |             | 0..1          |
|                                                               | EHDSEncounter.admission.referringProfessional  |            | EHDSHealthProfessional |             | 0..1          |
| Encounter.EncounterReason                                     |                                                |            |                        | 1           |               |
| Encounter.EncounterReason.Reason                              | EHDSEncounter.admission.reason[x]              | CD         | CodeableConcept        | 1           | 0..*          |
| Encounter.EncounterReason.Problem                             |                                                |            |                        | 1           |               |
| Encounter.EncounterReason.Problem.Diagnosis                   |                                                |            |                        | (0..1)      |               |
| Encounter.EncounterReason.Problem.HypersensitivityIntolerance |                                                |            |                        | (0..1)      |               |
| Encounter.EncounterReason.Problem.Reaction                    |                                                |            |                        | (0..1)      |               |
| Encounter.EncounterReason.Problem.Symptom                     |                                                |            |                        | (0..1)      |               |
| Encounter.EncounterReason.Problem.NursingDiagnosis            |                                                |            |                        | (0..1)      |               |
| Encounter.ResponsableHealthProfessional::HealthProfessional   |                                                |            |                        | 1           |               |
| Encounter.HealthProfessional.CommentEncounterReason           | EHDSEncounter.admission.reasonComment          | ST         | string                 | 0..1        | 0..1          |
|                                                               | EHDSEncounter.admission.legalStatus            |            | CodeableConcept        |             | 0..1          |
|                                                               | EHDSEncounter.discharge                        |            | Base                   |             | 0..1          |
|                                                               | EHDSEncounter.discharge.destinationType        |            | CodeableConcept        |             | 0..1          |
|                                                               | EHDSEncounter.discharge.destinationLocation[x] |            | EHDSOrganisation       |             | 0..1          |
|                                                               | EHDSEncounter.location                         |            | Base                   |             | 0..*          |
|                                                               | EHDSEncounter.location.period                  |            | Period                 |             | 0..1          |
|                                                               | EHDSEncounter.location.organisationPart[x]     |            | EHDSOrganisation       |             | 1..1          |
| Encounter.EncounterSetting                                    |                                                | CD         |                        | 1           |               |



## EHDSEncounter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter |
| zib | Encounter |
| alias_zib | NL: Contact |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Encounter |
| definition_zib | Root concept of the Encounter information model. This concept contains all data elements of the Encounter information model. |
| definitioncode_zib | SNOMED CT: 308335008 Patient encounter procedure |
| id_xtehr | EHDSEncounter |
| id_zib | NL-CM:15.1.1 |
| name_zib | Encounter |
| path_xtehr | EHDSEncounter |
| path_zib | Encounter |
| short_xtehr | Encounter model |
| stereotype_zib | rootconcept |

### Comments



## EHDSEncounter.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSEncounter.header |
| path_xtehr | EHDSEncounter.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSEncounter.priority

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.priority |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:v3-xEncounterAdmissionUrgency'} |
| card._xtehr | 0..1 |
| definition_xtehr | Indicates the urgency of the encounter. |
| id_xtehr | EHDSEncounter.priority |
| path_xtehr | EHDSEncounter.priority |
| short_xtehr | Priority |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.type |
| zib | Encounter.EncounterType |
| alias_zib | NL: ContactType |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7v3:ActEncounterCode'} |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | The type of the encounter whether inpatient or short stay encounter. |
| definition_zib | The type of encounter is based on the setting of the encounter and the participants present. |
| id_xtehr | EHDSEncounter.type |
| id_zib | NL-CM:15.1.2 |
| name_zib | EncounterType |
| path_xtehr | EHDSEncounter.type |
| path_zib | Encounter.EncounterType |
| short_xtehr | Encounter type |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSEncounter.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.note |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | A narrative description of the encounter course. |
| id_xtehr | EHDSEncounter.note |
| path_xtehr | EHDSEncounter.note |
| short_xtehr | A narrative description of the encounter course. |
| type_xtehr | string |

### Comments



## EHDSEncounter.episodeOfCare

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.episodeOfCare |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reference to the episode(s) of care that this encounter should be recorded against |
| id_xtehr | EHDSEncounter.episodeOfCare |
| path_xtehr | EHDSEncounter.episodeOfCare |
| short_xtehr | Reference to the episode(s) of care that this encounter should be recorded against |
| type_xtehr | EHDSEpisodeOfCare |

### Comments



## EHDSEncounter.basedOn[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.basedOn[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reference to the request that initiated this encounter |
| id_xtehr | EHDSEncounter.basedOn[x] |
| path_xtehr | EHDSEncounter.basedOn[x] |
| short_xtehr | Reference to the request that initiated this encounter |
| type_xtehr | EHDSCarePlan |

### Comments



## EHDSEncounter.partOf

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.partOf |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reference to another encounter this encounter is part of |
| id_xtehr | EHDSEncounter.partOf |
| path_xtehr | EHDSEncounter.partOf |
| short_xtehr | Reference to another encounter this encounter is part of |
| type_xtehr | EHDSEncounter |

### Comments



## zib: Encounter.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| card._zib | 1..* |
| definition_zib | The health professional with whom the encounter took or will take place. The specialty and role of the health professional can be entered in the HealthProfessional information model. |
| id_zib | NL-CM:15.1.7 |
| name_zib | HealthProfessional |
| path_zib | Encounter.HealthProfessional |
| stereotype_zib | context,reference |

### Comments



## EHDSEncounter.serviceProvider

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.serviceProvider |
| zib | Encounter.Location::HealthcareProvider |
| alias_zib | NL: Locatie::Zorgaanbieder |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The organisation (facility) responsible for this encounter |
| definition_zib | The physical location at which the encountert ook or will take place. |
| id_xtehr | EHDSEncounter.serviceProvider |
| id_zib | NL-CM:15.1.8 |
| name_zib | Location::HealthcareProvider |
| path_xtehr | EHDSEncounter.serviceProvider |
| path_zib | Encounter.Location::HealthcareProvider |
| short_xtehr | The organisation (facility) responsible for this encounter |
| stereotype_zib | context,reference |
| type_xtehr | EHDSOrganisation |

### Comments



## EHDSEncounter.actualPeriod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.actualPeriod |
| zib | Encounter.DateTime |
| alias_zib | NL: DatumTijd |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The actual start and end time of the encounter |
| definition_zib | The date and time at which the encounter took or will take place. |
| id_xtehr | EHDSEncounter.actualPeriod |
| id_zib | NL-CM:15.1.3 |
| name_zib | DateTime |
| path_xtehr | EHDSEncounter.actualPeriod |
| path_zib | Encounter.DateTime |
| short_xtehr | The actual start and end time of the encounter |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments



## EHDSEncounter.plannedStartDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.plannedStartDate |
| zib | Encounter.DateTime |
| alias_zib | NL: DatumTijd |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The planned start date/time (or admission date) of the encounter |
| definition_zib | The date and time at which the encounter took or will take place. |
| id_xtehr | EHDSEncounter.plannedStartDate |
| id_zib | NL-CM:15.1.3 |
| name_zib | DateTime |
| path_xtehr | EHDSEncounter.plannedStartDate |
| path_zib | Encounter.DateTime |
| short_xtehr | The planned start date/time (or admission date) of the encounter |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSEncounter.plannedEndDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.plannedEndDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The planned end date/time (or discharge date) of the encounter |
| id_xtehr | EHDSEncounter.plannedEndDate |
| path_xtehr | EHDSEncounter.plannedEndDate |
| short_xtehr | The planned end date/time (or discharge date) of the encounter |
| type_xtehr | dateTime |

### Comments



## EHDSEncounter.admission

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Details about the admission to a healthcare service |
| id_xtehr | EHDSEncounter.admission |
| path_xtehr | EHDSEncounter.admission |
| short_xtehr | Details about the admission to a healthcare service |
| type_xtehr | Base |

### Comments



## EHDSEncounter.admission.admitter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.admitter |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Admitting healthcare professional |
| id_xtehr | EHDSEncounter.admission.admitter |
| path_xtehr | EHDSEncounter.admission.admitter |
| short_xtehr | Admitting healthcare professional |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSEncounter.admission.admitSource

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.admitSource |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:admit-source'} |
| card._xtehr | 0..1 |
| definition_xtehr | From where the patient was admitted (e.g. physician referral, transfer). |
| id_xtehr | EHDSEncounter.admission.admitSource |
| path_xtehr | EHDSEncounter.admission.admitSource |
| short_xtehr | From where the patient was admitted (e.g. physician referral, transfer). |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.admission.referringProfessional

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.referringProfessional |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Referring Healthcare Professional |
| id_xtehr | EHDSEncounter.admission.referringProfessional |
| path_xtehr | EHDSEncounter.admission.referringProfessional |
| short_xtehr | Referring Healthcare Professional |
| type_xtehr | EHDSHealthProfessional |

### Comments



## zib: Encounter.EncounterReason

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason |
| alias_zib | NL: RedenContact |
| card._zib | 1 |
| definition_zib | Container of the EncounterReason concept.This container contains all data elements of the EncounterReason concept. |
| id_zib | NL-CM:15.1.13 |
| name_zib | EncounterReason |
| path_zib | Encounter.EncounterReason |
| stereotype_zib | container |

### Comments



## EHDSEncounter.admission.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reason[x] |
| zib | Encounter.EncounterReason.Reason |
| alias_zib | NL: AanleidingContact |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| definition_zib | Main reason for the encounter within the context of the health problem. |
| id_xtehr | EHDSEncounter.admission.reason[x] |
| id_zib | NL-CM:15.1.20 |
| name_zib | Reason |
| path_xtehr | EHDSEncounter.admission.reason[x] |
| path_zib | Encounter.EncounterReason.Reason |
| short_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## zib: Encounter.EncounterReason.Problem

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason.Problem |
| alias_zib | NL: Probleem |
| card._zib | 1 |
| definition_zib | Container of the Problem concept.This container contains all data elements of the Problem concept. |
| id_zib | NL-CM:15.1.21 |
| name_zib | Problem |
| path_zib | Encounter.EncounterReason.Problem |
| stereotype_zib | container |

### Comments



## zib: Encounter.EncounterReason.Problem.Diagnosis

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason.Problem.Diagnosis |
| alias_zib | NL: Diagnose |
| card._zib | (0..1) |
| definition_zib | The diagnosis as the reason for the encounter. |
| id_zib | NL-CM:15.1.22 |
| name_zib | Diagnosis |
| path_zib | Encounter.EncounterReason.Problem.Diagnosis |
| stereotype_zib | data,reference |

### Comments



## zib: Encounter.EncounterReason.Problem.HypersensitivityIntolerance

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason.Problem.HypersensitivityIntolerance |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| card._zib | (0..1) |
| definition_zib | The hypersensitivity or intolerance as the reason for the encounter. |
| id_zib | NL-CM:15.1.23 |
| name_zib | HypersensitivityIntolerance |
| path_zib | Encounter.EncounterReason.Problem.HypersensitivityIntolerance |
| stereotype_zib | data,reference |

### Comments



## zib: Encounter.EncounterReason.Problem.Reaction

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason.Problem.Reaction |
| alias_zib | NL: Reactie |
| card._zib | (0..1) |
| definition_zib | The adverse reaction to a substance or radiation as the reason for the encounter. |
| id_zib | NL-CM:15.1.24 |
| name_zib | Reaction |
| path_zib | Encounter.EncounterReason.Problem.Reaction |
| stereotype_zib | data,reference |

### Comments



## zib: Encounter.EncounterReason.Problem.Symptom

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason.Problem.Symptom |
| alias_zib | NL: Symptoom |
| card._zib | (0..1) |
| definition_zib | The symptom as the reason for the encounter. |
| id_zib | NL-CM:15.1.25 |
| name_zib | Symptom |
| path_zib | Encounter.EncounterReason.Problem.Symptom |
| stereotype_zib | data,reference |

### Comments



## zib: Encounter.EncounterReason.Problem.NursingDiagnosis

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterReason.Problem.NursingDiagnosis |
| alias_zib | NL: VerpleegkundigeDiagnose |
| card._zib | (0..1) |
| definition_zib | The nursing diagnosis as the reason for the encounter. |
| id_zib | NL-CM:15.1.26 |
| name_zib | NursingDiagnosis |
| path_zib | Encounter.EncounterReason.Problem.NursingDiagnosis |
| stereotype_zib | data,reference |

### Comments



## zib: Encounter.ResponsableHealthProfessional::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.ResponsableHealthProfessional::HealthProfessional |
| alias_zib | NL: VerantwoordelijkBehandelaar::Zorgverlener |
| card._zib | 1 |
| definition_zib | The health professional who is responsible at the time of the encounter for the treatment of the patient's stated health problem. |
| id_zib | NL-CM:15.1.18 |
| name_zib | ResponsableHealthProfessional::HealthProfessional |
| path_zib | Encounter.ResponsableHealthProfessional::HealthProfessional |
| stereotype_zib | context,reference |

### Comments



## EHDSEncounter.admission.reasonComment

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reasonComment |
| zib | Encounter.HealthProfessional.CommentEncounterReason |
| alias_zib | NL: ToelichtingRedenContact |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Explanation of the reason for the encounter. |
| definition_zib | Comment on the reason for the encounter, insofar as this cannot be sufficiently expressed in the other elements. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSEncounter.admission.reasonComment |
| id_zib | NL-CM:15.1.17 |
| name_zib | CommentEncounterReason |
| path_xtehr | EHDSEncounter.admission.reasonComment |
| path_zib | Encounter.HealthProfessional.CommentEncounterReason |
| short_xtehr | Explanation of the reason for the encounter. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSEncounter.admission.legalStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.legalStatus |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Legal status can be either voluntary or involuntary, however the legal status is always determined by a court. A patient can also receive healthcare based on a forensic status. (voluntary, involuntary, admission by legal authority). |
| id_xtehr | EHDSEncounter.admission.legalStatus |
| path_xtehr | EHDSEncounter.admission.legalStatus |
| short_xtehr | Legal status/situation at admission (indicates the basis on which the patient is staying in a healthcare organisation). |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.discharge

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.discharge |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Discharge details |
| id_xtehr | EHDSEncounter.discharge |
| path_xtehr | EHDSEncounter.discharge |
| short_xtehr | Discharge details |
| type_xtehr | Base |

### Comments



## EHDSEncounter.discharge.destinationType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.discharge.destinationType |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7.discharge-disposition'} |
| card._xtehr | 0..1 |
| definition_xtehr | Type of location to which the patient will go after the encounter. E.g. home, hospital, nursing home, left against medical advice etc. |
| id_xtehr | EHDSEncounter.discharge.destinationType |
| path_xtehr | EHDSEncounter.discharge.destinationType |
| short_xtehr | Type of location to which the patient will go after the encounter. E.g. home, hospital, nursing home, left against medical advice etc. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.discharge.destinationLocation[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.discharge.destinationLocation[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The location/organisation to which the patient will go after the encounter. Name, address and telecommunication contact. |
| id_xtehr | EHDSEncounter.discharge.destinationLocation[x] |
| path_xtehr | EHDSEncounter.discharge.destinationLocation[x] |
| short_xtehr | The location/organisation to which the patient will go after the encounter. Name, address and telecommunication contact. |
| type_xtehr | EHDSOrganisation |

### Comments



## EHDSEncounter.location

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.location |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | List of locations where the patient has been. |
| id_xtehr | EHDSEncounter.location |
| path_xtehr | EHDSEncounter.location |
| short_xtehr | List of locations where the patient has been. |
| type_xtehr | Base |

### Comments



## EHDSEncounter.location.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.location.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time period during which the patient was present at the location |
| id_xtehr | EHDSEncounter.location.period |
| path_xtehr | EHDSEncounter.location.period |
| short_xtehr | Time period during which the patient was present at the location |
| type_xtehr | Period |

### Comments



## EHDSEncounter.location.organisationPart[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.location.organisationPart[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Organisation or organisation part (department) where the patient was present. |
| id_xtehr | EHDSEncounter.location.organisationPart[x] |
| path_xtehr | EHDSEncounter.location.organisationPart[x] |
| short_xtehr | Organisation or organisation part (department) where the patient was present. |
| type_xtehr | EHDSOrganisation |

### Comments



## zib: Encounter.EncounterSetting

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Encounter.EncounterSetting |
| alias_zib | NL: ContactVorm |
| card._zib | 1 |
| definition_zib | EncounterSetting describes the manner and setting in which the contact takes place |
| id_zib | NL-CM:15.1.19 |
| name_zib | EncounterSetting |
| path_zib | Encounter.EncounterSetting |
| stereotype_zib | data |
| type_zib | CD |

### Comments

