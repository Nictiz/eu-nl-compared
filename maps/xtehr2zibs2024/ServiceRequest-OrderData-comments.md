# ServiceRequest

## Overall discussion
Er zijn slechts 3 equivalente concepten.
De zib heeft meer procesinformatie (indiener van het verzoek, status van het verzoek). Wel opmerkelijk dat een belangrijk procesgegeven, namelijk "when service should occur" ontbreekt in de zib en wel aanwezig is in het LM.
Het EHDS LM heeft meer gestructureerde informatie over datgene dat wordt verzocht, de reden van het verzoek, en de ondersteunende informatie. De zib heeft hier vrije tekst velden voor.
Opmerkelijk dat de indiener en het tijdstip van indienen in het EHDS model ontbreken. De informatie in de header geldt, zou je zeggen, alleen voor de _registratie_ van het verzoek.



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
Matige match: een vraag waarop een antwoord wordt verwacht (Zib) is niet hetzelfde als de omschrijving van de gevraagde dienst (EHDS). 


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
EHDS heeft hier een gecodeerd concept, zib heeft vrije tekst. NB definitie en naam van het zib concept passen niet bij elkaar. De reden van het verzoek hoeft niet relevant te zijn voor de uitvoering.


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
Afwezig in de zib: zib heeft OrderReason maar dat context die relevant is voor de uitvoering.



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
Slechte match: de zib heeft alleen een ongestructureerd veld voor alle additionele informatie, die niet in de overige velden van de zib past, waaronder ook informatie die het EHDS model _wel_ gemodelleerd heeft.



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

