# ServiceRequest

| zib                                     | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:----------------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| OrderData                               | EHDSServiceRequest                             |            |                        |             | 0..*          |
|                                         | EHDSServiceRequest.header                      |            | Base                   |             | 1..1          |
|                                         | EHDSServiceRequest.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                         | EHDSServiceRequest.header.identifier           |            | Identifier             |             | 0..*          |
|                                         | EHDSServiceRequest.header.authorship           |            | Base                   |             | 1..*          |
|                                         | EHDSServiceRequest.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                         | EHDSServiceRequest.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                         | EHDSServiceRequest.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                         | EHDSServiceRequest.header.status               |            | CodeableConcept        |             | 1..1          |
|                                         | EHDSServiceRequest.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                         | EHDSServiceRequest.header.language             |            | CodeableConcept        |             | 0..1          |
| OrderData.ClinicalQuestion              | EHDSServiceRequest.serviceText                 | ST         | string                 | 0..1        | 0..1          |
|                                         | EHDSServiceRequest.serviceCode                 |            | CodeableConcept        |             | 0..1          |
| OrderData.OrderReason                   | EHDSServiceRequest.reasonCode                  | ST         | CodeableConcept        | 0..1        | 0..*          |
|                                         | EHDSServiceRequest.quantity                    |            | Quantity               |             | 0..1          |
|                                         | EHDSServiceRequest.anatomicLocation            |            | EHDSBodyStructure      |             | 0..*          |
|                                         | EHDSServiceRequest.reasonReference[x]          |            | EHDSObservation        |             | 0..*          |
|                                         | EHDSServiceRequest.priority                    |            | CodeableConcept        |             | 0..1          |
| OrderData.Comment                       | EHDSServiceRequest.supportingInformation[x]    | ST         | EHDSObservation        | 0..1        | 0..*          |
|                                         | EHDSServiceRequest.specimen                    |            | EHDSSpecimen           |             | 0..*          |
|                                         | EHDSServiceRequest.encounter                   |            | EHDSEncounter          |             | 0..1          |
|                                         | EHDSServiceRequest.occurrence[x]               |            | dateTime               |             | 0..1          |
|                                         | EHDSServiceRequest.patientInstructions         |            | string                 |             | 0..1          |
|                                         | EHDSServiceRequest.coverage                    |            | EHDSCoverage           |             | 0..*          |
| OrderData.Requester::HealthProfessional |                                                |            |                        | 1           |               |
| OrderData.OrderDateTime                 |                                                | TS         |                        | 1           |               |
| OrderData.OrderId                       |                                                | II         |                        | 1           |               |
| OrderData.Status                        |                                                | CD         |                        | 1           |               |



## EHDSServiceRequest

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest |
| zib | OrderData |
| alias_zib | NL: AanvraagGegevens |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Specification of requested service or services |
| definition_zib | Root concept of the OrderData process data information model.This root concept contains all data elements of the OrderData process data information model. |
| id_xtehr | EHDSServiceRequest |
| id_zib | NL-CM:22.2.1 |
| name_zib | OrderData |
| path_xtehr | EHDSServiceRequest |
| path_zib | OrderData |
| short_xtehr | Service request model |
| stereotype_zib | rootconcept |

### Comments



## EHDSServiceRequest.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSServiceRequest.header |
| path_xtehr | EHDSServiceRequest.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSServiceRequest.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSServiceRequest.header.subject |
| path_xtehr | EHDSServiceRequest.header.subject |
| short_xtehr | Patient/subject information |
| type_xtehr | EHDSPatient |

### Comments



## EHDSServiceRequest.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSServiceRequest.header.identifier |
| path_xtehr | EHDSServiceRequest.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSServiceRequest.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSServiceRequest.header.authorship |
| path_xtehr | EHDSServiceRequest.header.authorship |
| short_xtehr | Resource authoring details |
| type_xtehr | Base |

### Comments



## EHDSServiceRequest.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSServiceRequest.header.authorship.author[x] |
| path_xtehr | EHDSServiceRequest.header.authorship.author[x] |
| short_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSServiceRequest.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of authoring/issuing |
| id_xtehr | EHDSServiceRequest.header.authorship.datetime |
| path_xtehr | EHDSServiceRequest.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSServiceRequest.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| id_xtehr | EHDSServiceRequest.header.lastUpdate |
| path_xtehr | EHDSServiceRequest.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| type_xtehr | dateTime |

### Comments



## EHDSServiceRequest.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource or document |
| id_xtehr | EHDSServiceRequest.header.status |
| path_xtehr | EHDSServiceRequest.header.status |
| short_xtehr | Status of the resource or document |
| type_xtehr | CodeableConcept |

### Comments



## EHDSServiceRequest.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSServiceRequest.header.statusReason[x] |
| path_xtehr | EHDSServiceRequest.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSServiceRequest.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSServiceRequest.header.language |
| path_xtehr | EHDSServiceRequest.header.language |
| short_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSServiceRequest.serviceText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.serviceText |
| zib | OrderData.ClinicalQuestion |
| alias_zib | NL: Vraagstelling |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual description of the requested service |
| definition_zib | Description of the question to which the requester hopes to receive an answer. This is especially important for actions whose outcome requires interpretation from the performer. |
| id_xtehr | EHDSServiceRequest.serviceText |
| id_zib | NL-CM:22.2.6 |
| name_zib | ClinicalQuestion |
| path_xtehr | EHDSServiceRequest.serviceText |
| path_zib | OrderData.ClinicalQuestion |
| short_xtehr | Service text |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSServiceRequest.serviceCode

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.serviceCode |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'LOINC, NPU, SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | A code that identifies a particular service (i.e., procedure, diagnostic investigation, or panel of investigations) that have been requested. |
| id_xtehr | EHDSServiceRequest.serviceCode |
| path_xtehr | EHDSServiceRequest.serviceCode |
| short_xtehr | Service code |
| type_xtehr | CodeableConcept |

### Comments



## EHDSServiceRequest.reasonCode

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.reasonCode |
| zib | OrderData.OrderReason |
| alias_zib | NL: RedenAanvraag |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10 (ICD-11 when available), SNOMED CT, Orphacode'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Health conditions affecting the health of the patient and are important to be known for a health professional during a health encounter. Clinical conditions of the subject relevant for the results interpretation. |
| definition_zib | Context of the order, which is relevant for the execution. |
| id_xtehr | EHDSServiceRequest.reasonCode |
| id_zib | NL-CM:22.2.5 |
| name_zib | OrderReason |
| path_xtehr | EHDSServiceRequest.reasonCode |
| path_zib | OrderData.OrderReason |
| short_xtehr | Reason code |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | ST |

### Comments



## EHDSServiceRequest.quantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.quantity |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Amount of requested services of the same type |
| id_xtehr | EHDSServiceRequest.quantity |
| path_xtehr | EHDSServiceRequest.quantity |
| short_xtehr | Quantity |
| type_xtehr | Quantity |

### Comments



## EHDSServiceRequest.anatomicLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.anatomicLocation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Anatomic location and laterality where the procedure should be performed. This is the target site. |
| id_xtehr | EHDSServiceRequest.anatomicLocation |
| path_xtehr | EHDSServiceRequest.anatomicLocation |
| short_xtehr | Anatomic location |
| type_xtehr | EHDSBodyStructure |

### Comments



## EHDSServiceRequest.reasonReference[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.reasonReference[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Indicates another resource that provides a justification for why this service is being requested. |
| id_xtehr | EHDSServiceRequest.reasonReference[x] |
| path_xtehr | EHDSServiceRequest.reasonReference[x] |
| short_xtehr | Reason reference |
| type_xtehr | EHDSObservation |

### Comments



## EHDSServiceRequest.priority

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.priority |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Request priority'} |
| card._xtehr | 0..1 |
| definition_xtehr | Indicates how quickly the ServiceRequest should be addressed with respect to other requests. |
| id_xtehr | EHDSServiceRequest.priority |
| path_xtehr | EHDSServiceRequest.priority |
| short_xtehr | Priority |
| type_xtehr | CodeableConcept |

### Comments



## EHDSServiceRequest.supportingInformation[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.supportingInformation[x] |
| zib | OrderData.Comment |
| alias_zib | NL: Opmerking |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Health conditions relevant for the results interpretation, e.g. fasting status, sex for clinical use, etc. |
| definition_zib | Additional information that is important for the execution of the order and which cannot be described in any of the other elements. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSServiceRequest.supportingInformation[x] |
| id_zib | NL-CM:22.2.8 |
| name_zib | Comment |
| path_xtehr | EHDSServiceRequest.supportingInformation[x] |
| path_zib | OrderData.Comment |
| short_xtehr | Supporting information |
| stereotype_zib | data |
| type_xtehr | EHDSObservation |
| type_zib | ST |

### Comments



## EHDSServiceRequest.specimen

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.specimen |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Specimens to be used by the laboratory procedure |
| id_xtehr | EHDSServiceRequest.specimen |
| path_xtehr | EHDSServiceRequest.specimen |
| short_xtehr | Specimen |
| type_xtehr | EHDSSpecimen |

### Comments



## EHDSServiceRequest.encounter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.encounter |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | An encounter that provides additional information about the healthcare context in which this request is made. |
| id_xtehr | EHDSServiceRequest.encounter |
| path_xtehr | EHDSServiceRequest.encounter |
| short_xtehr | Encounter |
| type_xtehr | EHDSEncounter |

### Comments



## EHDSServiceRequest.occurrence[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.occurrence[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | When service should occur |
| id_xtehr | EHDSServiceRequest.occurrence[x] |
| path_xtehr | EHDSServiceRequest.occurrence[x] |
| short_xtehr | Occurrence |
| type_xtehr | dateTime |

### Comments



## EHDSServiceRequest.patientInstructions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.patientInstructions |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Patient or consumer-oriented instructions |
| id_xtehr | EHDSServiceRequest.patientInstructions |
| path_xtehr | EHDSServiceRequest.patientInstructions |
| short_xtehr | Patient instructions |
| type_xtehr | string |

### Comments



## EHDSServiceRequest.coverage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.coverage |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Insurance or medical plan or a payment agreement. |
| id_xtehr | EHDSServiceRequest.coverage |
| path_xtehr | EHDSServiceRequest.coverage |
| short_xtehr | Coverage |
| type_xtehr | EHDSCoverage |

### Comments



## zib: OrderData.Requester::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.Requester::HealthProfessional |
| alias_zib | NL: Aanvrager::Zorgverlener |
| card._zib | 1 |
| definition_zib | The person who ordered the action (procedure, test, etc.). |
| id_zib | NL-CM:22.2.4 |
| name_zib | Requester::HealthProfessional |
| path_zib | OrderData.Requester::HealthProfessional |
| stereotype_zib | data,reference |

### Comments



## zib: OrderData.OrderDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.OrderDateTime |
| alias_zib | NL: AanvraagDatumTijd |
| card._zib | 1 |
| definition_zib | Date and if relevant time when the order is made. |
| id_zib | NL-CM:22.2.2 |
| name_zib | OrderDateTime |
| path_zib | OrderData.OrderDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: OrderData.OrderId

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.OrderId |
| alias_zib | NL: Aanvraagnummer |
| card._zib | 1 |
| definition_zib | Order identification number. |
| id_zib | NL-CM:22.2.3 |
| name_zib | OrderId |
| path_zib | OrderData.OrderId |
| stereotype_zib | data |
| type_zib | II |

### Comments



## zib: OrderData.Status

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.Status |
| alias_zib | NL: Status |
| card._zib | 1 |
| definition_zib | Status of the order in the ordering process, such as e.g. 'requested', 'planned', 'completed' |
| id_zib | NL-CM:22.2.7 |
| name_zib | Status |
| path_zib | OrderData.Status |
| stereotype_zib | data |
| type_zib | CD |

### Comments

