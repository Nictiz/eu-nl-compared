# DataSet

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
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Common elements (including header) for all documents and their independently functioning parts, e.g FHIR resources. |
| definition_zib | Root concept of the RegistrationData process data information model. This root concept contains all data elements of the RegistrationData process data information model. |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet |
| id_zib | NL-CM:22.1.1 |
| name_zib | RegistrationData |
| path_xtehr | EHDSDataSet |
| path_zib | RegistrationData |
| short_xtehr | DataSet model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSDataSet.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header |
| zib | RegistrationData |
| alias_zib | NL: RegistratieGegevens |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Common header for all patient-related data |
| definition_zib | Root concept of the RegistrationData process data information model. This root concept contains all data elements of the RegistrationData process data information model. |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header |
| id_zib | NL-CM:22.1.1 |
| name_zib | RegistrationData |
| path_xtehr | EHDSDataSet.header |
| path_zib | RegistrationData |
| short_xtehr | Common header for all patient-related data |
| stereotype_zib | rootconcept |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSDataSet.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib |  |
| definition_xtehr | Resource authoring details |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.authorship |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.authorship |
| path_zib |  |
| short_xtehr | Authorship |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSDataSet.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship.author[x] |
| zib | RegistrationData.Author::HealthProfessional |
| alias_zib | NL: Auteur::Zorgverlener |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| definition_zib | The author is the one who is responsible for recording information or having information recorded in the medical record.
It concerns not only own observations, but also information received from third parties. The author has decided to include the information in the medical record, and if necessary with source reference. |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.authorship.author[x] |
| id_zib | NL-CM:22.1.2 |
| name_zib | Author::HealthProfessional |
| path_xtehr | EHDSDataSet.header.authorship.author[x] |
| path_zib | RegistrationData.Author::HealthProfessional |
| short_xtehr | Author |
| stereotype_zib | data,reference |
| type_xtehr | EHDSHealthProfessional |
| type_zib |  |

### Comments



## EHDSDataSet.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship.datetime |
| zib | RegistrationData.RegistrationDateTime |
| alias_zib | NL: RegistratieDatumTijd |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| definition_zib | Date and time when the information was recorded in the patient record. |
| definitioncode_zib |  |
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
| binding_xtehr |  |
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
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.language |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.language |
| path_zib |  |
| short_xtehr | Language |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDataSet.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.lastUpdate |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Date and time of the last update to the document/information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.lastUpdate |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.lastUpdate |
| path_zib |  |
| short_xtehr | Date and time of the last update to the resource |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDataSet.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.status |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Status of the resource |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.status |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.status |
| path_zib |  |
| short_xtehr | Status of the resource |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDataSet.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.statusReason[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Reason for the current status of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.statusReason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.statusReason[x] |
| path_zib |  |
| short_xtehr | Reason for the current status of the resource. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDataSet.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.subject |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Patient/subject information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.subject |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.subject |
| path_zib |  |
| short_xtehr | Subject |
| stereotype_zib |  |
| type_xtehr | EHDSPatient |
| type_zib |  |

### Comments



## EHDSDataSet.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.version |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Business version of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.header.version |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.header.version |
| path_zib |  |
| short_xtehr | Version |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDataSet.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.presentedForm |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDataSet.presentedForm |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDataSet.presentedForm |
| path_zib |  |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| stereotype_zib |  |
| type_xtehr | EHDSAttachment |
| type_zib |  |

### Comments



## zib: RegistrationData.AcquisitionDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.AcquisitionDateTime |
| alias_zib | NL: DatumTijdVanVerkrijgen |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Date and when relevant time when the information became available. This may be an earlier time than the date/time when the information was entered in the patient record. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.9 |
| name_zib | AcquisitionDateTime |
| path_xtehr |  |
| path_zib | RegistrationData.AcquisitionDateTime |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | TS |

### Comments



## zib: RegistrationData.AcquisitionMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.AcquisitionMethod |
| alias_zib | NL: WijzeVanVerkrijgen |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | The way in which the information is obtained by the patient record holder. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.8 |
| name_zib | AcquisitionMethod |
| path_xtehr |  |
| path_zib | RegistrationData.AcquisitionMethod |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments



## zib: RegistrationData.CopyIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.CopyIndicator |
| alias_zib | NL: KopieIndicator |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | Indication that the data has been obtained from the EPR of another healthcare professional/healthcare provider. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.11 |
| name_zib | CopyIndicator |
| path_xtehr |  |
| path_zib | RegistrationData.CopyIndicator |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | BL |

### Comments



## zib: RegistrationData.DatTimeOfClosure

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.DatTimeOfClosure |
| alias_zib | NL: AfsluitDatumTijd |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Date and time at which it is recorded in the patient record that the information is no longer relevant, for example because the information is outdated, no longer requires attention, etc. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.5 |
| name_zib | DatTimeOfClosure |
| path_xtehr |  |
| path_zib | RegistrationData.DatTimeOfClosure |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | TS |

### Comments



## zib: RegistrationData.InformationSource

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource |
| alias_zib | NL: Informatiebron |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Container of the InformationSource concept.This container contains all data elements of the InformationSource concept.
If the recorded information has not been assessed by the attending physician, the source of the information can be recorded. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.13 |
| name_zib | InformationSource |
| path_xtehr |  |
| path_zib | RegistrationData.InformationSource |
| short_xtehr |  |
| stereotype_zib | container |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: RegistrationData.InformationSource.ContactPerson

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.ContactPerson |
| alias_zib | NL: Contactpersoon |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | The contact person who is the source of the information. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.15 |
| name_zib | ContactPerson |
| path_xtehr |  |
| path_zib | RegistrationData.InformationSource.ContactPerson |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: RegistrationData.InformationSource.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | The health professional who is the source of the information. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.14 |
| name_zib | HealthProfessional |
| path_xtehr |  |
| path_zib | RegistrationData.InformationSource.HealthProfessional |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: RegistrationData.InformationSource.Patient

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.Patient |
| alias_zib | NL: Patient |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | The patient as information source |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.16 |
| name_zib | Patient |
| path_xtehr |  |
| path_zib | RegistrationData.InformationSource.Patient |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: RegistrationData.ReasonDataAbsent

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.ReasonDataAbsent |
| alias_zib | NL: RedenAfwezigheidGegevens |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Reason why no data is available for the value of a concept. This includes, for example, all 'Unknown' variants, but also 'Indeterminate', 'Specimen unsatisfactory', etc. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.10 |
| name_zib | ReasonDataAbsent |
| path_xtehr |  |
| path_zib | RegistrationData.ReasonDataAbsent |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: RegistrationData.ReasonForClosing

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.ReasonForClosing |
| alias_zib | NL: RedenVanAfsluiten |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Reason why updating the information, or following changes in the the concept in question is no longer considered relevant. For example, in the case of a condition, this does not mean that the disease is no longer present, but merely that the holder of the patients record no longer considers the condition as an aspect to be taken into account during care provision. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.6 |
| name_zib | ReasonForClosing |
| path_xtehr |  |
| path_zib | RegistrationData.ReasonForClosing |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments



## zib: RegistrationData.RegistrationReason

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.RegistrationReason |
| alias_zib | NL: RedenVanVastleggen |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Description of the reason for including the information in the patient record. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:22.1.4 |
| name_zib | RegistrationReason |
| path_xtehr |  |
| path_zib | RegistrationData.RegistrationReason |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments

