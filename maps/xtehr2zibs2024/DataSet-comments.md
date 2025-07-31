# DataSet

## Voorlopige conclusies

- de patient is impliciet in de zibs?
- de zib heeft veel meer velden
  - de zib RegistrationData is nog niet in de praktijk getoetst, moeten we dan die extra velden inbrengen in XtEHR?
  - of misschien een of een paar velden wel?
- absentReason zit in de zib, in XtEHR zit dit ofwel in valueSets ofwel pas in FHIR (meestal het eerste)
- identificatie is 0..1 in de zib en 0..* in XtEHR
- XtEHR heeft 'language' - dus van de resource zelf, is dit een nuttige toevoeging?

| zib                                                   | xtehr                                   | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:------------------------------------------------------|:----------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| RegistrationData                                      | EHDSDataSet                             |            |                        |             | 0..*          |
| RegistrationData                                      | EHDSDataSet.header                      |            | Base                   |             | 1..1          |
|                                                       | EHDSDataSet.header.authorship           |            | Base                   |             | 1..*          |
| RegistrationData.Author::HealthProfessional           | EHDSDataSet.header.authorship.author[x] |            | EHDSHealthProfessional | 1           | 1..1          |
| RegistrationData.RegistrationDateTime                 | EHDSDataSet.header.authorship.datetime  | TS         | dateTime               | 1           | 1..1          |
| RegistrationData.IdentificationNumber                 | EHDSDataSet.header.identifier           | II         | Identifier             | 0..1        | 0..*          |
|                                                       | EHDSDataSet.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                       | EHDSDataSet.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                       | EHDSDataSet.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                       | EHDSDataSet.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                       | EHDSDataSet.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                       | EHDSDataSet.header.version              |            | string                 |             | 0..1          |
|                                                       | EHDSDataSet.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| RegistrationData.AcquisitionDateTime                  |                                         | TS         |                        | 0..1        |               |
| RegistrationData.AcquisitionMethod                    |                                         | ST         |                        | 1           |               |
| RegistrationData.CopyIndicator                        |                                         | BL         |                        | 1           |               |
| RegistrationData.DatTimeOfClosure                     |                                         | TS         |                        | 0..1        |               |
| RegistrationData.InformationSource                    |                                         |            |                        | 0..1        |               |
| RegistrationData.InformationSource.ContactPerson      |                                         |            |                        | (0..1)      |               |
| RegistrationData.InformationSource.HealthProfessional |                                         |            |                        | (0..1)      |               |
| RegistrationData.InformationSource.Patient            |                                         |            |                        | (0..1)      |               |
| RegistrationData.ReasonDataAbsent                     |                                         | CD         |                        | 0..1        |               |
| RegistrationData.ReasonForClosing                     |                                         | ST         |                        | 0..1        |               |
| RegistrationData.RegistrationReason                   |                                         | ST         |                        | 0..1        |               |



## EHDSDataSet

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet |
| zib | RegistrationData |
| alias_zib | NL: RegistratieGegevens |
| card._xtehr | 0..* |
| definition_xtehr | Common elements (including header) for all documents and their independently functioning parts, e.g FHIR resources. |
| definition_zib | Root concept of the RegistrationData process data information model. This root concept contains all data elements of the RegistrationData process data information model. |
| id_xtehr | EHDSDataSet |
| id_zib | NL-CM:22.1.1 |
| name_zib | RegistrationData |
| path_xtehr | EHDSDataSet |
| path_zib | RegistrationData |
| short_xtehr | DataSet model |
| stereotype_zib | rootconcept |

### Comments



## EHDSDataSet.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header |
| zib | RegistrationData |
| alias_zib | NL: RegistratieGegevens |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| definition_zib | Root concept of the RegistrationData process data information model. This root concept contains all data elements of the RegistrationData process data information model. |
| id_xtehr | EHDSDataSet.header |
| id_zib | NL-CM:22.1.1 |
| name_zib | RegistrationData |
| path_xtehr | EHDSDataSet.header |
| path_zib | RegistrationData |
| short_xtehr | Common header for all patient-related data |
| stereotype_zib | rootconcept |
| type_xtehr | Base |

### Comments



## EHDSDataSet.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSDataSet.header.authorship |
| path_xtehr | EHDSDataSet.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSDataSet.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship.author[x] |
| zib | RegistrationData.Author::HealthProfessional |
| alias_zib | NL: Auteur::Zorgverlener |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| definition_zib | The author is the one who is responsible for recording information or having information recorded in the medical record.
It concerns not only own observations, but also information received from third parties. The author has decided to include the information in the medical record, and if necessary with source reference. |
| id_xtehr | EHDSDataSet.header.authorship.author[x] |
| id_zib | NL-CM:22.1.2 |
| name_zib | Author::HealthProfessional |
| path_xtehr | EHDSDataSet.header.authorship.author[x] |
| path_zib | RegistrationData.Author::HealthProfessional |
| short_xtehr | Author |
| stereotype_zib | data,reference |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSDataSet.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship.datetime |
| zib | RegistrationData.RegistrationDateTime |
| alias_zib | NL: RegistratieDatumTijd |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| definition_zib | Date and time when the information was recorded in the patient record. |
| id_xtehr | EHDSDataSet.header.authorship.datetime |
| id_zib | NL-CM:22.1.3 |
| name_zib | RegistrationDateTime |
| path_xtehr | EHDSDataSet.header.authorship.datetime |
| path_zib | RegistrationData.RegistrationDateTime |
| short_xtehr | Date and time of authoring/issuing |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSDataSet.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.identifier |
| zib | RegistrationData.IdentificationNumber |
| alias_zib | NL: Identificatienummer |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Business identifier for the object |
| definition_zib | Globally unique number that identifies the instantiation of the information model. The number is composed of an identification of the issuer organization and a unique number assigned by this organization. |
| definitioncode_zib | SNOMED CT: 396278008 Identification number |
| id_xtehr | EHDSDataSet.header.identifier |
| id_zib | NL-CM:22.1.12 |
| name_zib | IdentificationNumber |
| path_xtehr | EHDSDataSet.header.identifier |
| path_zib | RegistrationData.IdentificationNumber |
| short_xtehr | Business identifier for the object |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | II |

### Comments



## EHDSDataSet.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSDataSet.header.language |
| path_xtehr | EHDSDataSet.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSDataSet.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSDataSet.header.lastUpdate |
| path_xtehr | EHDSDataSet.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSDataSet.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSDataSet.header.status |
| path_xtehr | EHDSDataSet.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSDataSet.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSDataSet.header.statusReason[x] |
| path_xtehr | EHDSDataSet.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSDataSet.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSDataSet.header.subject |
| path_xtehr | EHDSDataSet.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSDataSet.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSDataSet.header.version |
| path_xtehr | EHDSDataSet.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSDataSet.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSDataSet.presentedForm |
| path_xtehr | EHDSDataSet.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## zib: RegistrationData.AcquisitionDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.AcquisitionDateTime |
| alias_zib | NL: DatumTijdVanVerkrijgen |
| card._zib | 0..1 |
| definition_zib | Date and when relevant time when the information became available. This may be an earlier time than the date/time when the information was entered in the patient record. |
| id_zib | NL-CM:22.1.9 |
| name_zib | AcquisitionDateTime |
| path_zib | RegistrationData.AcquisitionDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: RegistrationData.AcquisitionMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.AcquisitionMethod |
| alias_zib | NL: WijzeVanVerkrijgen |
| card._zib | 1 |
| definition_zib | The way in which the information is obtained by the patient record holder. |
| id_zib | NL-CM:22.1.8 |
| name_zib | AcquisitionMethod |
| path_zib | RegistrationData.AcquisitionMethod |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: RegistrationData.CopyIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.CopyIndicator |
| alias_zib | NL: KopieIndicator |
| card._zib | 1 |
| definition_zib | Indication that the data has been obtained from the EPR of another healthcare professional/healthcare provider. |
| id_zib | NL-CM:22.1.11 |
| name_zib | CopyIndicator |
| path_zib | RegistrationData.CopyIndicator |
| stereotype_zib | data |
| type_zib | BL |

### Comments



## zib: RegistrationData.DatTimeOfClosure

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.DatTimeOfClosure |
| alias_zib | NL: AfsluitDatumTijd |
| card._zib | 0..1 |
| definition_zib | Date and time at which it is recorded in the patient record that the information is no longer relevant, for example because the information is outdated, no longer requires attention, etc. |
| id_zib | NL-CM:22.1.5 |
| name_zib | DatTimeOfClosure |
| path_zib | RegistrationData.DatTimeOfClosure |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: RegistrationData.InformationSource

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource |
| alias_zib | NL: Informatiebron |
| card._zib | 0..1 |
| definition_zib | Container of the InformationSource concept.This container contains all data elements of the InformationSource concept.
If the recorded information has not been assessed by the attending physician, the source of the information can be recorded. |
| id_zib | NL-CM:22.1.13 |
| name_zib | InformationSource |
| path_zib | RegistrationData.InformationSource |
| stereotype_zib | container |

### Comments



## zib: RegistrationData.InformationSource.ContactPerson

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.ContactPerson |
| alias_zib | NL: Contactpersoon |
| card._zib | (0..1) |
| definition_zib | The contact person who is the source of the information. |
| id_zib | NL-CM:22.1.15 |
| name_zib | ContactPerson |
| path_zib | RegistrationData.InformationSource.ContactPerson |
| stereotype_zib | data,reference |

### Comments



## zib: RegistrationData.InformationSource.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| card._zib | (0..1) |
| definition_zib | The health professional who is the source of the information. |
| id_zib | NL-CM:22.1.14 |
| name_zib | HealthProfessional |
| path_zib | RegistrationData.InformationSource.HealthProfessional |
| stereotype_zib | data,reference |

### Comments



## zib: RegistrationData.InformationSource.Patient

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.Patient |
| alias_zib | NL: Patient |
| card._zib | (0..1) |
| definition_zib | The patient as information source |
| id_zib | NL-CM:22.1.16 |
| name_zib | Patient |
| path_zib | RegistrationData.InformationSource.Patient |
| stereotype_zib | data,reference |

### Comments



## zib: RegistrationData.ReasonDataAbsent

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.ReasonDataAbsent |
| alias_zib | NL: RedenAfwezigheidGegevens |
| card._zib | 0..1 |
| definition_zib | Reason why no data is available for the value of a concept. This includes, for example, all 'Unknown' variants, but also 'Indeterminate', 'Specimen unsatisfactory', etc. |
| id_zib | NL-CM:22.1.10 |
| name_zib | ReasonDataAbsent |
| path_zib | RegistrationData.ReasonDataAbsent |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: RegistrationData.ReasonForClosing

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.ReasonForClosing |
| alias_zib | NL: RedenVanAfsluiten |
| card._zib | 0..1 |
| definition_zib | Reason why updating the information, or following changes in the the concept in question is no longer considered relevant. For example, in the case of a condition, this does not mean that the disease is no longer present, but merely that the holder of the patients record no longer considers the condition as an aspect to be taken into account during care provision. |
| id_zib | NL-CM:22.1.6 |
| name_zib | ReasonForClosing |
| path_zib | RegistrationData.ReasonForClosing |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: RegistrationData.RegistrationReason

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.RegistrationReason |
| alias_zib | NL: RedenVanVastleggen |
| card._zib | 0..1 |
| definition_zib | Description of the reason for including the information in the patient record. |
| id_zib | NL-CM:22.1.4 |
| name_zib | RegistrationReason |
| path_zib | RegistrationData.RegistrationReason |
| stereotype_zib | data |
| type_zib | ST |

### Comments

