# EpisodeOfCare

| zib                                         | xtehr                                         | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------------|:----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| EpisodeOfCare                               | EHDSEpisodeOfCare                             |            |                        |             | 0..*          |
|                                             | EHDSEpisodeOfCare.header                      |            | Base                   |             | 1..1          |
|                                             | EHDSEpisodeOfCare.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                             | EHDSEpisodeOfCare.header.identifier           |            | Identifier             |             | 0..*          |
|                                             | EHDSEpisodeOfCare.header.authorship           |            | Base                   |             | 1..*          |
|                                             | EHDSEpisodeOfCare.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                             | EHDSEpisodeOfCare.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                             | EHDSEpisodeOfCare.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                             | EHDSEpisodeOfCare.header.status               |            | CodeableConcept        |             | 1..1          |
|                                             | EHDSEpisodeOfCare.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                             | EHDSEpisodeOfCare.header.language             |            | CodeableConcept        |             | 0..1          |
|                                             | EHDSEpisodeOfCare.type                        |            | CodeableConcept        |             | 0..*          |
|                                             | EHDSEpisodeOfCare.reasonText                  |            | string                 |             | 0..1          |
|                                             | EHDSEpisodeOfCare.reason[x]                   |            | CodeableConcept        |             | 0..*          |
|                                             | EHDSEpisodeOfCare.diagnosis                   |            | Base                   |             | 0..*          |
|                                             | EHDSEpisodeOfCare.diagnosis.description       |            | string                 |             | 1..1          |
| EpisodeOfCare.FocusEpisodeOfCare::Condition | EHDSEpisodeOfCare.diagnosis.condition[x]      |            | CodeableConcept        | 0..1        | 0..1          |
| EpisodeOfCare.StartDate                     |                                               | TS         |                        | 0..1        |               |
| EpisodeOfCare.EndDate                       |                                               | TS         |                        | 0..1        |               |
| EpisodeOfCare.EpisodeOfCareName             |                                               | ST         |                        | 0..1        |               |
| EpisodeOfCare.Comment                       |                                               | ST         |                        | 0..1        |               |



## EHDSEpisodeOfCare

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare |
| zib | EpisodeOfCare |
| alias_zib | NL: ZorgEpisode |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Episode of care |
| definition_zib | Root concept of the EpisodeOfCare information model.This root concept contains all data elements of the EpisodeOfCare information model. |
| id_xtehr | EHDSEpisodeOfCare |
| id_zib | NL-CM:16.6.1 |
| name_zib | EpisodeOfCare |
| path_xtehr | EHDSEpisodeOfCare |
| path_zib | EpisodeOfCare |
| short_xtehr | Episode of care model |
| stereotype_zib | rootconcept |

### Comments



## EHDSEpisodeOfCare.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSEpisodeOfCare.header |
| path_xtehr | EHDSEpisodeOfCare.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSEpisodeOfCare.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSEpisodeOfCare.header.subject |
| path_xtehr | EHDSEpisodeOfCare.header.subject |
| short_xtehr | Patient/subject information |
| type_xtehr | EHDSPatient |

### Comments



## EHDSEpisodeOfCare.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSEpisodeOfCare.header.identifier |
| path_xtehr | EHDSEpisodeOfCare.header.identifier |
| short_xtehr | Business identifiers assigned to this episode of care. |
| type_xtehr | Identifier |

### Comments



## EHDSEpisodeOfCare.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSEpisodeOfCare.header.authorship |
| path_xtehr | EHDSEpisodeOfCare.header.authorship |
| short_xtehr | Resource authoring details |
| type_xtehr | Base |

### Comments



## EHDSEpisodeOfCare.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSEpisodeOfCare.header.authorship.author[x] |
| path_xtehr | EHDSEpisodeOfCare.header.authorship.author[x] |
| short_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSEpisodeOfCare.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of authoring/issuing |
| id_xtehr | EHDSEpisodeOfCare.header.authorship.datetime |
| path_xtehr | EHDSEpisodeOfCare.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSEpisodeOfCare.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| id_xtehr | EHDSEpisodeOfCare.header.lastUpdate |
| path_xtehr | EHDSEpisodeOfCare.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| type_xtehr | dateTime |

### Comments



## EHDSEpisodeOfCare.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource or document |
| id_xtehr | EHDSEpisodeOfCare.header.status |
| path_xtehr | EHDSEpisodeOfCare.header.status |
| short_xtehr | Status of the resource or document |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEpisodeOfCare.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSEpisodeOfCare.header.statusReason[x] |
| path_xtehr | EHDSEpisodeOfCare.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEpisodeOfCare.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSEpisodeOfCare.header.language |
| path_xtehr | EHDSEpisodeOfCare.header.language |
| short_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEpisodeOfCare.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.type |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A classification of the type of episode of care; e.g. specialist referral, disease management. |
| id_xtehr | EHDSEpisodeOfCare.type |
| path_xtehr | EHDSEpisodeOfCare.type |
| short_xtehr | A classification of the type of episode of care; e.g. specialist referral, disease management. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEpisodeOfCare.reasonText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.reasonText |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Textual descriptions of the medical reasons that are expected to be addressed during the episode of care. |
| id_xtehr | EHDSEpisodeOfCare.reasonText |
| path_xtehr | EHDSEpisodeOfCare.reasonText |
| short_xtehr | Textual descriptions of the medical reasons that are expected to be addressed during the episode of care. |
| type_xtehr | string |

### Comments



## EHDSEpisodeOfCare.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.reason[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Coded list of medical reasons that are expected to be addressed during the episode of care. |
| id_xtehr | EHDSEpisodeOfCare.reason[x] |
| path_xtehr | EHDSEpisodeOfCare.reason[x] |
| short_xtehr | Coded list of medical reasons that are expected to be addressed during the episode of care. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEpisodeOfCare.diagnosis

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.diagnosis |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | List of medical conditions that were addressed during the episode of care |
| id_xtehr | EHDSEpisodeOfCare.diagnosis |
| path_xtehr | EHDSEpisodeOfCare.diagnosis |
| short_xtehr | List of medical conditions that were addressed during the episode of care |
| type_xtehr | Base |

### Comments



## EHDSEpisodeOfCare.diagnosis.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.diagnosis.description |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Textual description of the medical condition that was addressed during the episode of care |
| id_xtehr | EHDSEpisodeOfCare.diagnosis.description |
| path_xtehr | EHDSEpisodeOfCare.diagnosis.description |
| short_xtehr | Textual description of the medical condition that was addressed during the episode of care |
| type_xtehr | string |

### Comments



## EHDSEpisodeOfCare.diagnosis.condition[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.diagnosis.condition[x] |
| zib | EpisodeOfCare.FocusEpisodeOfCare::Condition |
| alias_zib | NL: FocusZorgEpisode::AandoeningOfGesteldheid |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | The medical condition that was addressed during the episode of care |
| definition_zib | The condition on which the episode of care focuses. |
| id_xtehr | EHDSEpisodeOfCare.diagnosis.condition[x] |
| id_zib | NL-CM:16.6.7 |
| name_zib | FocusEpisodeOfCare::Condition |
| path_xtehr | EHDSEpisodeOfCare.diagnosis.condition[x] |
| path_zib | EpisodeOfCare.FocusEpisodeOfCare::Condition |
| short_xtehr | The medical condition that was addressed during the episode of care |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments



## zib: EpisodeOfCare.StartDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.StartDate |
| alias_zib | NL: BeginDatum |
| card._zib | 0..1 |
| definition_zib | The date that marks the beginning of the episode of care. Usually this is the date of the first contact of the patient with the care provider in the context of the health problem. |
| definitioncode_zib | SNOMED CT: 413946009 Date treatment started |
| id_zib | NL-CM:16.6.2 |
| name_zib | StartDate |
| path_zib | EpisodeOfCare.StartDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: EpisodeOfCare.EndDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.EndDate |
| alias_zib | NL: EindDatum |
| card._zib | 0..1 |
| definition_zib | The date that marks the end of the episode of care. This can be the date of the last contact of the patient with the care provider in the context of the health problem, but also thereafter on the basis of hindsight. |
| definitioncode_zib | SNOMED CT: 413947000 Date treatment stopped |
| id_zib | NL-CM:16.6.3 |
| name_zib | EndDate |
| path_zib | EpisodeOfCare.EndDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: EpisodeOfCare.EpisodeOfCareName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.EpisodeOfCareName |
| alias_zib | NL: ZorgEpisodeNaam |
| card._zib | 0..1 |
| definition_zib | A name that characterizes the episode of care for the care provider. |
| id_zib | NL-CM:16.6.5 |
| name_zib | EpisodeOfCareName |
| path_zib | EpisodeOfCare.EpisodeOfCareName |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: EpisodeOfCare.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Additional information about the episode of care that the care provider wishes to see at first glance. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:16.6.6 |
| name_zib | Comment |
| path_zib | EpisodeOfCare.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments

