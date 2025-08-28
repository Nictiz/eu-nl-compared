# MedicationPrescription

| zib                                                          | xtehr                                                               | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-------------------------------------------------------------|:--------------------------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| DispenseRequest                                              | EHDSMedicationPrescription                                          |            |                        |             | 0..*          |
|                                                              | EHDSMedicationPrescription.comment                                  |            | string                 |             | 0..*          |
|                                                              | EHDSMedicationPrescription.header                                   |            | Base                   |             | 1..1          |
|                                                              | EHDSMedicationPrescription.header.authorship                        |            | Base                   |             | 1..*          |
|                                                              | EHDSMedicationPrescription.header.authorship.author[x]              |            | EHDSHealthProfessional |             | 1..1          |
|                                                              | EHDSMedicationPrescription.header.authorship.datetime               |            | dateTime               |             | 1..1          |
|                                                              | EHDSMedicationPrescription.header.identifier                        |            | Identifier             |             | 0..*          |
|                                                              | EHDSMedicationPrescription.header.language                          |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.lastUpdate                        |            | dateTime               |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.recorder                          |            | EHDSHealthProfessional |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.recordingDate                     |            | dateTime               |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.status                            |            | CodeableConcept        |             | 1..1          |
|                                                              | EHDSMedicationPrescription.header.statusReason[x]                   |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.subject                           |            | EHDSPatient            |             | 1..1          |
|                                                              | EHDSMedicationPrescription.header.validFrom                         |            | dateTime               |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.validUntil                        |            | dateTime               |             | 0..1          |
|                                                              | EHDSMedicationPrescription.header.version                           |            | string                 |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem                         |            | Base                   |             | 1..*          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.category                |            | CodeableConcept        |             | 0..*          |
| DispenseRequest.Comment                                      | EHDSMedicationPrescription.prescriptionItem.comment                 | ST         | string                 | 0..1        | 0..*          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.dosageInstructions      |            | EHDSDosaging           |             | 0..*          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.identifier              |            | Identifier             |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.indicationText          |            | string                 |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.indication[x]           |            | CodeableConcept        |             | 0..*          |
| DispenseRequest.MedicineToBeDispensed::PharmaceuticalProduct | EHDSMedicationPrescription.prescriptionItem.medication              |            | EHDSMedication         | 1           | 1..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.minimumDispenseInterval |            | Quantity               |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.offLabel                |            | Base                   |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.offLabel.isOffLabelUse  |            | boolean                |             | 1..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.offLabel.reason[x]      |            | CodeableConcept        |             | 0..*          |
| DispenseRequest.AdditionalWishes                             | EHDSMedicationPrescription.prescriptionItem.preparationInstructions | CD         | string                 | 0..*        | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.prescriptionIntent      |            | CodeableConcept        |             | 0..1          |
| DispenseRequest.Amount                                       | EHDSMedicationPrescription.prescriptionItem.quantityPrescribed      | PQ         | Quantity               | 0..1        | 0..1          |
| DispenseRequest.NumberOfRefills                              | EHDSMedicationPrescription.prescriptionItem.repeatsAllowed          | INT        | integer                | 0..1        | 0..1          |
| DispenseRequest.DispenseRequestStatus                        | EHDSMedicationPrescription.prescriptionItem.status                  | CD         | CodeableConcept        | 1           | 1..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.statusReason[x]         |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.substitution            |            | Base                   |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.substitution.allowed[x] |            | boolean                |             | 0..1          |
|                                                              | EHDSMedicationPrescription.prescriptionItem.substitution.reason[x]  |            | CodeableConcept        |             | 0..1          |
| DispenseRequest.SupplyPeriod::TimeInterval                   | EHDSMedicationPrescription.prescriptionItem.treatmentPeriod         |            | Period                 | 0..1        | 0..1          |
|                                                              | EHDSMedicationPrescription.presentedForm                            |            | EHDSAttachment         |             | 0..*          |
| DispenseRequest.DispenseLocation                             |                                                                     | ST         |                        | 0..1        |               |
| DispenseRequest.DispenseRequestDate                          |                                                                     | TS         |                        | 0..1        |               |
| DispenseRequest.IntendedSupplier::HealthcareProvider         |                                                                     |            |                        | 0..1        |               |



## EHDSMedicationPrescription

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription |
| zib | DispenseRequest |
| alias_zib | NL: Verstrekkingsverzoek |
| card._xtehr | 0..* |
| definition_xtehr | Logical model for medication prescription. A prescription contains one or more prescription items. |
| definition_zib | Root concept of the DispenseRequest information model.This root concept contains all data elements of the DispenseRequest information model. |
| definitioncode_zib | SNOMED CT: 52711000146108 Request to dispense medication to patient |
| id_xtehr | EHDSMedicationPrescription |
| id_zib | NL-CM:9.10.19963 |
| name_zib | DispenseRequest |
| path_xtehr | EHDSMedicationPrescription |
| path_zib | DispenseRequest |
| short_xtehr | Medication prescription model |
| stereotype_zib | rootconcept |

### Comments



## EHDSMedicationPrescription.comment

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.comment |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Additional information or comments |
| id_xtehr | EHDSMedicationPrescription.comment |
| path_xtehr | EHDSMedicationPrescription.comment |
| short_xtehr | Additional information or comments |
| type_xtehr | string |

### Comments



## EHDSMedicationPrescription.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Prescription header data elements |
| id_xtehr | EHDSMedicationPrescription.header |
| path_xtehr | EHDSMedicationPrescription.header |
| short_xtehr | Prescription header |
| type_xtehr | Base |

### Comments



## EHDSMedicationPrescription.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSMedicationPrescription.header.authorship |
| path_xtehr | EHDSMedicationPrescription.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSMedicationPrescription.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSMedicationPrescription.header.authorship.author[x] |
| path_xtehr | EHDSMedicationPrescription.header.authorship.author[x] |
| short_xtehr | The prescriber, the person who made the prescription, and who takes the responsibility of the treatment. [Used for searching] |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSMedicationPrescription.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSMedicationPrescription.header.authorship.datetime |
| path_xtehr | EHDSMedicationPrescription.header.authorship.datetime |
| short_xtehr | Time of issuing (signing) the prescription by health care professional. [Used for searching] |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationPrescription.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSMedicationPrescription.header.identifier |
| path_xtehr | EHDSMedicationPrescription.header.identifier |
| short_xtehr | Business identifier(s) for the prescription. [Used for searching] |
| type_xtehr | Identifier |

### Comments



## EHDSMedicationPrescription.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSMedicationPrescription.header.language |
| path_xtehr | EHDSMedicationPrescription.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSMedicationPrescription.header.lastUpdate |
| path_xtehr | EHDSMedicationPrescription.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationPrescription.header.recorder

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.recorder |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The recorder of the prescription/draft in the information system |
| id_xtehr | EHDSMedicationPrescription.header.recorder |
| path_xtehr | EHDSMedicationPrescription.header.recorder |
| short_xtehr | The recorder of the prescription/draft in the information system |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSMedicationPrescription.header.recordingDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.recordingDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time of authoring the prescription/draft in the information system |
| id_xtehr | EHDSMedicationPrescription.header.recordingDate |
| path_xtehr | EHDSMedicationPrescription.header.recordingDate |
| short_xtehr | Time of authoring the prescription/draft in the information system |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationPrescription.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSMedicationPrescription.header.status |
| path_xtehr | EHDSMedicationPrescription.header.status |
| short_xtehr | Status of the prescription, this should not be status of treatment. For multi-item prescription, the status of prescription is often related to statuses of single lines. In case of single-item prescriptions, the status for line is usually the status of prescription. [Used for searching] |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSMedicationPrescription.header.statusReason[x] |
| path_xtehr | EHDSMedicationPrescription.header.statusReason[x] |
| short_xtehr | Reason for the current status of prescription, for example the reason why the prescription was made invalid or why the prescription was changed from previous |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSMedicationPrescription.header.subject |
| path_xtehr | EHDSMedicationPrescription.header.subject |
| short_xtehr | The person for whom the medication is prescribed/ordered. [Used for searching] |
| type_xtehr | EHDSPatient |

### Comments



## EHDSMedicationPrescription.header.validFrom

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.validFrom |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Effective date of the prescription. The prescription is not dispensable before this date. In most cases this information repeats issueDate. [Used for searching] |
| id_xtehr | EHDSMedicationPrescription.header.validFrom |
| path_xtehr | EHDSMedicationPrescription.header.validFrom |
| short_xtehr | Effective date of the prescription. The prescription is not dispensable before this date. In most cases this information repeats issueDate. [Used for searching] |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationPrescription.header.validUntil

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.validUntil |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The validity period end date. The prescription is not dispensable after this date. [Used for searching] |
| id_xtehr | EHDSMedicationPrescription.header.validUntil |
| path_xtehr | EHDSMedicationPrescription.header.validUntil |
| short_xtehr | The validity period end date. The prescription is not dispensable after this date. [Used for searching] |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationPrescription.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSMedicationPrescription.header.version |
| path_xtehr | EHDSMedicationPrescription.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSMedicationPrescription.prescriptionItem

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Prescription line for one medication. In many countries, only one item is allowed. In case multiple medications are allowed, all lines need to be authored together. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem |
| short_xtehr | Prescription line for one medication. In many countries, only one item is allowed. In case multiple medications are allowed, all lines need to be authored together. |
| type_xtehr | Base |

### Comments



## EHDSMedicationPrescription.prescriptionItem.category

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.category |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Category or categories of prescription. For example type of reimbursement, or type of prescription (e.g. hospital, private, etc). |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.category |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.category |
| short_xtehr | Category or categories of prescription. For example type of reimbursement, or type of prescription (e.g. hospital, private, etc). |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.prescriptionItem.comment

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.comment |
| zib | DispenseRequest.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Additional information or comments |
| definition_zib | Explanation for the dispense request. <br> <br>This explanation can contain e.g. information on why a prescriber submits a dispense request that deviates from the norm, e.g. an extra dispense request needed because the patient has lost the medication. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.comment |
| id_zib | NL-CM:9.10.22274 |
| name_zib | Comment |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.comment |
| path_zib | DispenseRequest.Comment |
| short_xtehr | Additional information or comments |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSMedicationPrescription.prescriptionItem.dosageInstructions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.dosageInstructions |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Dosaging and administration instructions |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.dosageInstructions |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.dosageInstructions |
| short_xtehr | Dosaging and administration instructions |
| type_xtehr | EHDSDosaging |

### Comments



## EHDSMedicationPrescription.prescriptionItem.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.identifier |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Identifier for a single item on prescription, if exists. In case of single-item prescription, this identifier is typically the same as prescription identifier. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.identifier |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.identifier |
| short_xtehr | Identifier for a single item on prescription, if exists. In case of single-item prescription, this identifier is typically the same as prescription identifier. |
| type_xtehr | Identifier |

### Comments



## EHDSMedicationPrescription.prescriptionItem.indicationText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.indicationText |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the prescription in textual form. This might not be allowed by some implementations. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.indicationText |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.indicationText |
| short_xtehr | Reason for the prescription in textual form. This might not be allowed by some implementations. |
| type_xtehr | string |

### Comments



## EHDSMedicationPrescription.prescriptionItem.indication[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.indication[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reason for the prescription (typically diagnosis, or a procedure) |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.indication[x] |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.indication[x] |
| short_xtehr | Reason for the prescription (typically diagnosis, or a procedure) |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.prescriptionItem.medication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.medication |
| zib | DispenseRequest.MedicineToBeDispensed::PharmaceuticalProduct |
| alias_zib | NL: TeVerstrekkenGeneesmiddel::FarmaceutischProduct |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Prescribed product, branded, generic, virtual, extemporal, etc |
| definition_zib | The medicine to be dispensed. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.medication |
| id_zib | NL-CM:9.10.22249 |
| name_zib | MedicineToBeDispensed::PharmaceuticalProduct |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.medication |
| path_zib | DispenseRequest.MedicineToBeDispensed::PharmaceuticalProduct |
| short_xtehr | Prescribed product, branded, generic, virtual, extemporal, etc |
| stereotype_zib | data,reference |
| type_xtehr | EHDSMedication |

### Comments



## EHDSMedicationPrescription.prescriptionItem.minimumDispenseInterval

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.minimumDispenseInterval |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | If a prescription allows for repeated dispensations, the interval between dispensations shall be stated here. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.minimumDispenseInterval |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.minimumDispenseInterval |
| short_xtehr | Minimum Dispense Interval |
| type_xtehr | Quantity |

### Comments



## EHDSMedicationPrescription.prescriptionItem.offLabel

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Indicates that the prescriber has knowingly prescribed the medication for an indication, age group, dosage, or route of administration that is not approved by the regulatory agencies and is not mentioned in the prescribing information for the drug |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel |
| short_xtehr | Indicates that the prescriber has knowingly prescribed the medication for an indication, age group, dosage, or route of administration that is not approved by the regulatory agencies and is not mentioned in the prescribing information for the drug |
| type_xtehr | Base |

### Comments



## EHDSMedicationPrescription.prescriptionItem.offLabel.isOffLabelUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel.isOffLabelUse |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Indicates off-label use. Must be 'true' when .reason is provided. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel.isOffLabelUse |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel.isOffLabelUse |
| short_xtehr | Indicates off-label use. Must be 'true' when .reason is provided. |
| type_xtehr | boolean |

### Comments



## EHDSMedicationPrescription.prescriptionItem.offLabel.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel.reason[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reason or related clarification for off-label use |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel.reason[x] |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.offLabel.reason[x] |
| short_xtehr | Reason or related clarification for off-label use |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.prescriptionItem.preparationInstructions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.preparationInstructions |
| zib | DispenseRequest.AdditionalWishes |
| alias_zib | NL: AanvullendeWensen |
| card._xtehr | 0..1 |
| card._zib | 0..* |
| definition_xtehr | Additional instructions about preparation or dispense |
| definition_zib | Logistics and other instructions such as: do not enter in GDS, urgent, purposeful deviation, etc. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.preparationInstructions |
| id_zib | NL-CM:9.10.22759 |
| name_zib | AdditionalWishes |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.preparationInstructions |
| path_zib | DispenseRequest.AdditionalWishes |
| short_xtehr | Additional instructions about preparation or dispense |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | CD |

### Comments



## EHDSMedicationPrescription.prescriptionItem.prescriptionIntent

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.prescriptionIntent |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Intent of the prescription - prophylaxis, treatment, anesthesia, etc |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.prescriptionIntent |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.prescriptionIntent |
| short_xtehr | Intent of the prescription - prophylaxis, treatment, anesthesia, etc |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.prescriptionItem.quantityPrescribed

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.quantityPrescribed |
| zib | DispenseRequest.Amount |
| alias_zib | NL: TeVerstrekkenHoeveelheid |
| binding_xtehr | {'strength': 'preferred', 'description': 'UCUM, EDQM Standard Terms'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Overall quantity of prescribed product (e.g number of packages or number of tablets). |
| definition_zib | This is the number of units of the ordered product per dispense. The number of refills indicates how often this amount is allowed to be dispensed. Optionally a translation to NHG table Gebruiksvoorschriften (Table 25) is also allowed. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.quantityPrescribed |
| id_zib | NL-CM:9.10.19964 |
| name_zib | Amount |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.quantityPrescribed |
| path_zib | DispenseRequest.Amount |
| short_xtehr | Overall quantity of prescribed product (e.g number of packages or number of tablets). |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments



## EHDSMedicationPrescription.prescriptionItem.repeatsAllowed

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.repeatsAllowed |
| zib | DispenseRequest.NumberOfRefills |
| alias_zib | NL: AantalHerhalingen |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | How many times the prescription item can be dispensed in addition to the original dispense. |
| definition_zib | The number of additional times the medication may be dispensed after the first time. <br>In the case of Amount: The total amount that may be dispensed is: (Number of refills + 1) x amount to be dispensed.<br>In the case of Period of Use:The total period of use is: (Number of refills + 1) x period of use |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.repeatsAllowed |
| id_zib | NL-CM:9.10.22120 |
| name_zib | NumberOfRefills |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.repeatsAllowed |
| path_zib | DispenseRequest.NumberOfRefills |
| short_xtehr | Number of refills authorized |
| stereotype_zib | data |
| type_xtehr | integer |
| type_zib | INT |

### Comments



## EHDSMedicationPrescription.prescriptionItem.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.status |
| zib | DispenseRequest.DispenseRequestStatus |
| alias_zib | NL: VerstrekkingsverzoekStatus |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Status of a single item of a multi-item prescription. In case of single-item prescriptions, the status of prescription has the same meaning as the status of the item. |
| definition_zib | Status of the order in the ordering process, such as e.g. 'cancelled', 'ordered' |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.status |
| id_zib | NL-CM:9.10.22760 |
| name_zib | DispenseRequestStatus |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.status |
| path_zib | DispenseRequest.DispenseRequestStatus |
| short_xtehr | Status of a single item of a multi-item prescription. In case of single-item prescriptions, the status of prescription has the same meaning as the status of the item. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSMedicationPrescription.prescriptionItem.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of prescription, for example the reason why the prescription was made invalid or why the prescription was changed from previous |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.statusReason[x] |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.statusReason[x] |
| short_xtehr | Reason for the current status of prescription, for example the reason why the prescription was made invalid or why the prescription was changed from previous |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.prescriptionItem.substitution

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.substitution |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Whether and which type of substitution is allowed for this medication treatment item |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.substitution |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.substitution |
| short_xtehr | Whether and which type of substitution is allowed for this medication treatment item |
| type_xtehr | Base |

### Comments



## EHDSMedicationPrescription.prescriptionItem.substitution.allowed[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.substitution.allowed[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Whether and to what extent substitution is allowed. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.substitution.allowed[x] |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.substitution.allowed[x] |
| short_xtehr | Whether and to what extent substitution is allowed. |
| type_xtehr | boolean |

### Comments



## EHDSMedicationPrescription.prescriptionItem.substitution.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.substitution.reason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the substitution requirement (e.g. Biological product, Patient allergic to an excipient in alternative products, etc) |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.substitution.reason[x] |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.substitution.reason[x] |
| short_xtehr | Reason for the substitution requirement (e.g. Biological product, Patient allergic to an excipient in alternative products, etc) |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationPrescription.prescriptionItem.treatmentPeriod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.prescriptionItem.treatmentPeriod |
| zib | DispenseRequest.SupplyPeriod::TimeInterval |
| alias_zib | NL: Verbruiksperiode::TijdsInterval |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Period over which the medication is to be taken (in case of multiple dosaging schemes, this would be the overall period of all dosages.) |
| definition_zib | During the approved period of use, the pharmacist has permission to dispense medicine so that the patient has a sufficient amount of medication.<br><br>In many cases, the approved supply period can be described by only an end date: the approved end date of use. <br><br>Toegestane eenheden voor de duur zijn:  uur, dag, week, jaar. |
| id_xtehr | EHDSMedicationPrescription.prescriptionItem.treatmentPeriod |
| id_zib | NL-CM:9.10.20062 |
| name_zib | SupplyPeriod::TimeInterval |
| path_xtehr | EHDSMedicationPrescription.prescriptionItem.treatmentPeriod |
| path_zib | DispenseRequest.SupplyPeriod::TimeInterval |
| short_xtehr | Period over which the medication is to be taken (in case of multiple dosaging schemes, this would be the overall period of all dosages.) |
| stereotype_zib | data,reference |
| type_xtehr | Period |

### Comments



## EHDSMedicationPrescription.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationPrescription.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSMedicationPrescription.presentedForm |
| path_xtehr | EHDSMedicationPrescription.presentedForm |
| short_xtehr | Entire prescription as issued. Various formats could be provided, PDF format is recommended. |
| type_xtehr | EHDSAttachment |

### Comments



## zib: DispenseRequest.DispenseLocation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | DispenseRequest.DispenseLocation |
| alias_zib | NL: Afleverlocatie |
| card._zib | 0..1 |
| definition_zib | Dispense location. |
| id_zib | NL-CM:9.10.20068 |
| name_zib | DispenseLocation |
| path_zib | DispenseRequest.DispenseLocation |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: DispenseRequest.DispenseRequestDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | DispenseRequest.DispenseRequestDate |
| alias_zib | NL: VerstrekkingsverzoekDatum |
| card._zib | 0..1 |
| definition_zib | Time at which the dispense request is entered. |
| id_zib | NL-CM:9.10.20060 |
| name_zib | DispenseRequestDate |
| path_zib | DispenseRequest.DispenseRequestDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: DispenseRequest.IntendedSupplier::HealthcareProvider

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | DispenseRequest.IntendedSupplier::HealthcareProvider |
| alias_zib | NL: BeoogdVerstrekker::Zorgaanbieder |
| card._zib | 0..1 |
| definition_zib | The intended supplier is a pharmacist. |
| id_zib | NL-CM:9.10.19966 |
| name_zib | IntendedSupplier::HealthcareProvider |
| path_zib | DispenseRequest.IntendedSupplier::HealthcareProvider |
| stereotype_zib | context,reference |

### Comments

