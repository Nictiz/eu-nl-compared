# Medication Dispense as of 2025-08-21

## Version history

v1: 21-08-2025, initial version

## Actions

## Compared
### Scope
Scope largely corresponds namely dispensing a medication with accompanying instructions. There is no medication agreement or administration agreement in xtEHR which means that when mapping InstructionsForUse one or the other (depending on what is more actual information) should be mapped.

Substitute drugs are modelled in the xtEHR model within the group elements Substitution.  This models the decision to give a substitute drug by the pharmacist with reasons. Within the zibs, there is an administration arrangement separate from the medication arrangement in which the pharmaceutical product may differ from medication arrangement which allows it to be inferred that a substitute drug was given, but does not clarify why this was done.

### Summary of partly matching elements
- EHDSMedicationDispense.dispenseLocation string in the zib, location model in EHDS
- EHDSMedicationDispense.dispensedQuantity additional bindings that are not mentioned in xtEHR and zib
- EHDSMedicationDispense.relatedRequest cardinality mismatch


### Zib elements not present in xtEHR model:

- MedicationDispense.DistributionForm
- MedicationDispense.DurationOfUse
- MedicationDispense.MedicationDispenseAdditionalInformation can possibly be matched one way to EHDSMedicationDispense.substitution.reason
- MedicationDispense.RequestDate
- MedicationDispense.Supplier::HealthcareProvider

### EHDS elements not present in the zib model:

- EHDSMedicationDispense.dosageInstructions can likely be modelled based on InstructionForUse via MedicationAgreement or AdministrationAgreement, but there are no reference(s) in the zib.
- EHDSMedicationDispense.receiver[x]
- EHDSMedicationDispense.substitution
- EHDSMedicationDispense.substitution.reason
- EHDSMedicationDispense.substitution.substitutionOccurred
- EHDSMedicationDispense.substitution.type


### Other

The .header elements and .presentForm are skipped in this comparison (as they should map on more generic zib(s) like registration data).

## Discussions (datum:)

| zib                                                         | xtehr                                                    | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:------------------------------------------------------------|:---------------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| MedicationDispense                                          | EHDSMedicationDispense                                   |            |                        |             | 0..*          |
| MedicationDispense.Comment                                  | EHDSMedicationDispense.comment                           | ST         | string                 | 0..1        | 0..*          |
| MedicationDispense.DispenseLocation                         | EHDSMedicationDispense.dispenseLocation                  | ST         | EHDSLocation           | 0..1        | 0..1          |
| MedicationDispense.DispensedAmount                          | EHDSMedicationDispense.dispensedQuantity                 | PQ         | Quantity               | 0..1        | 1..1          |
|                                                             | EHDSMedicationDispense.dosageInstructions                |            | EHDSDosaging           |             | 0..*          |
|                                                             | EHDSMedicationDispense.header                            |            | Base                   |             | 1..1          |
|                                                             | EHDSMedicationDispense.header.authorship                 |            | Base                   |             | 1..*          |
|                                                             | EHDSMedicationDispense.header.authorship.author[x]       |            | EHDSHealthProfessional |             | 1..1          |
|                                                             | EHDSMedicationDispense.header.authorship.datetime        |            | dateTime               |             | 1..1          |
|                                                             | EHDSMedicationDispense.header.identifier                 |            | Identifier             |             | 0..*          |
|                                                             | EHDSMedicationDispense.header.language                   |            | CodeableConcept        |             | 0..1          |
|                                                             | EHDSMedicationDispense.header.lastUpdate                 |            | dateTime               |             | 0..1          |
|                                                             | EHDSMedicationDispense.header.status                     |            | CodeableConcept        |             | 1..1          |
|                                                             | EHDSMedicationDispense.header.statusReason[x]            |            | CodeableConcept        |             | 0..1          |
|                                                             | EHDSMedicationDispense.header.subject                    |            | EHDSPatient            |             | 1..1          |
|                                                             | EHDSMedicationDispense.header.version                    |            | string                 |             | 0..1          |
| MedicationDispense.DispensedMedicine::PharmaceuticalProduct | EHDSMedicationDispense.medication                        |            | EHDSMedication         | 1           | 1..1          |
|                                                             | EHDSMedicationDispense.presentedForm                     |            | EHDSAttachment         |             | 0..*          |
|                                                             | EHDSMedicationDispense.receiver[x]                       |            | EHDSPatient            |             | 0..1          |
| MedicationDispense.DispenseRequest                          | EHDSMedicationDispense.relatedRequest                    |            | Identifier             | 0..1        | 0..*          |
|                                                             | EHDSMedicationDispense.substitution                      |            | Base                   |             | 0..1          |
|                                                             | EHDSMedicationDispense.substitution.reason               |            | CodeableConcept        |             | 0..*          |
|                                                             | EHDSMedicationDispense.substitution.substitutionOccurred |            | boolean                |             | 1..1          |
|                                                             | EHDSMedicationDispense.substitution.type                 |            | CodeableConcept        |             | 0..1          |
| MedicationDispense.MedicationDispenseDateTime               | EHDSMedicationDispense.timeOfDispensation                | TS         | dateTime               | 0..1        | 1..1          |
| MedicationDispense.DistributionForm                         |                                                          | CD         |                        | 0..1        |               |
| MedicationDispense.DurationOfUse                            |                                                          | PQ         |                        | 0..1        |               |
| MedicationDispense.MedicationDispenseAdditionalInformation  |                                                          | CD         |                        | 0..*        |               |
| MedicationDispense.RequestDate                              |                                                          | TS         |                        | 0..1        |               |
| MedicationDispense.Supplier::HealthcareProvider             |                                                          |            |                        | 0..1        |               |



## EHDSMedicationDispense

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense |
| zib | MedicationDispense |
| alias_zib | NL: Medicatieverstrekking |
| card._xtehr | 0..* |
| definition_xtehr | Logical model for medication dispensation (based on request or independently) |
| definition_zib | Root concept of the MedicationDispense information model. This root concept contains all data elements of the MedicationDispense information model. |
| definitioncode_zib | SNOMED CT: 373784005 Dispensing medication |
| id_xtehr | EHDSMedicationDispense |
| id_zib | NL-CM:9.9.20270 |
| name_zib | MedicationDispense |
| path_xtehr | EHDSMedicationDispense |
| path_zib | MedicationDispense |
| short_xtehr | Medication dispense model |
| stereotype_zib | rootconcept |

### Comments
Why is cardinality of xtEHR rootconcept 0..*


## EHDSMedicationDispense.comment

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.comment |
| zib | MedicationDispense.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Additional information or comments |
| definition_zib | Comments on the dispense. |
| id_xtehr | EHDSMedicationDispense.comment |
| id_zib | NL-CM:9.9.22276 |
| name_zib | Comment |
| path_xtehr | EHDSMedicationDispense.comment |
| path_zib | MedicationDispense.Comment |
| short_xtehr | Additional information or comments |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Complete match


## EHDSMedicationDispense.dispenseLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.dispenseLocation |
| zib | MedicationDispense.DispenseLocation |
| alias_zib | NL: Afleverlocatie |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Location of dispense |
| definition_zib | Dispense location |
| id_xtehr | EHDSMedicationDispense.dispenseLocation |
| id_zib | NL-CM:9.9.20925 |
| name_zib | DispenseLocation |
| path_xtehr | EHDSMedicationDispense.dispenseLocation |
| path_zib | MedicationDispense.DispenseLocation |
| short_xtehr | Location of dispense |
| stereotype_zib | data |
| type_xtehr | EHDSLocation |
| type_zib | ST |

### Comments
Scope match, cardinality match, datatype mismatch string in zib complete location model in xtEHR.


## EHDSMedicationDispense.dispensedQuantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.dispensedQuantity |
| zib | MedicationDispense.DispensedAmount |
| alias_zib | NL: VerstrekteHoeveelheid |
| binding_xtehr | {'strength': 'preferred', 'description': 'UCUM, EDQM Standard Terms'} |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Number of dispensed packages if the pack size is known, or number of smaller items/units |
| definition_zib | Number of units of the product (measured based on the relevant product code) supplied. Optionally a translation to NHG table Gebruiksvoorschriften(Table 25) is also allowed. |
| id_xtehr | EHDSMedicationDispense.dispensedQuantity |
| id_zib | NL-CM:9.9.20923 |
| name_zib | DispensedAmount |
| path_xtehr | EHDSMedicationDispense.dispensedQuantity |
| path_zib | MedicationDispense.DispensedAmount |
| short_xtehr | Number of dispensed packages if the pack size is known, or number of smaller items/units |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments
match scope, cardinality and datatype. Partial match on binding for UCUM. Additional binding possible in zib for NHG table 25. Additional preferred binding for xtEHR on EDQM.


## EHDSMedicationDispense.dosageInstructions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.dosageInstructions |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Dosaging and administration instructions |
| id_xtehr | EHDSMedicationDispense.dosageInstructions |
| path_xtehr | EHDSMedicationDispense.dosageInstructions |
| short_xtehr | Dosaging and administration instructions |
| type_xtehr | EHDSDosaging |

### Comments
Can be mapped via the zib InstructionsForUse. (reference is missing in the zib to DispenseAgreement -> InstructionsForUse)


## EHDSMedicationDispense.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSMedicationDispense.header |
| path_xtehr | EHDSMedicationDispense.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSMedicationDispense.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSMedicationDispense.header.authorship |
| path_xtehr | EHDSMedicationDispense.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSMedicationDispense.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSMedicationDispense.header.authorship.author[x] |
| path_xtehr | EHDSMedicationDispense.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSMedicationDispense.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSMedicationDispense.header.authorship.datetime |
| path_xtehr | EHDSMedicationDispense.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationDispense.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSMedicationDispense.header.identifier |
| path_xtehr | EHDSMedicationDispense.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSMedicationDispense.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSMedicationDispense.header.language |
| path_xtehr | EHDSMedicationDispense.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationDispense.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSMedicationDispense.header.lastUpdate |
| path_xtehr | EHDSMedicationDispense.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationDispense.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSMedicationDispense.header.status |
| path_xtehr | EHDSMedicationDispense.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationDispense.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSMedicationDispense.header.statusReason[x] |
| path_xtehr | EHDSMedicationDispense.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationDispense.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSMedicationDispense.header.subject |
| path_xtehr | EHDSMedicationDispense.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSMedicationDispense.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSMedicationDispense.header.version |
| path_xtehr | EHDSMedicationDispense.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSMedicationDispense.medication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.medication |
| zib | MedicationDispense.DispensedMedicine::PharmaceuticalProduct |
| alias_zib | NL: VerstrektGeneesmiddel::FarmaceutischProduct |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Exact dispensed product |
| definition_zib | The dispensed medicine. |
| id_xtehr | EHDSMedicationDispense.medication |
| id_zib | NL-CM:9.9.22259 |
| name_zib | DispensedMedicine::PharmaceuticalProduct |
| path_xtehr | EHDSMedicationDispense.medication |
| path_zib | MedicationDispense.DispensedMedicine::PharmaceuticalProduct |
| short_xtehr | Exact dispensed product |
| stereotype_zib | data,reference |
| type_xtehr | EHDSMedication |

### Comments



## EHDSMedicationDispense.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSMedicationDispense.presentedForm |
| path_xtehr | EHDSMedicationDispense.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSMedicationDispense.receiver[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.receiver[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Identification of the person who received the dispensed medication, especially when it was not the patient |
| id_xtehr | EHDSMedicationDispense.receiver[x] |
| path_xtehr | EHDSMedicationDispense.receiver[x] |
| short_xtehr | Identification of the person who received the dispensed medication, especially when it was not the patient |
| type_xtehr | EHDSPatient |

### Comments



## EHDSMedicationDispense.relatedRequest

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.relatedRequest |
| zib | MedicationDispense.DispenseRequest |
| alias_zib | NL: Verstrekkingsverzoek |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Identifier of the prescription or prescription item the dispense is related to |
| definition_zib | Relationship to the dispense request this medication dispense was based on. |
| id_xtehr | EHDSMedicationDispense.relatedRequest |
| id_zib | NL-CM:9.9.22396 |
| name_zib | DispenseRequest |
| path_xtehr | EHDSMedicationDispense.relatedRequest |
| path_zib | MedicationDispense.DispenseRequest |
| short_xtehr | Identifier of the prescription or prescription item the dispense is related to |
| stereotype_zib | context,reference |
| type_xtehr | Identifier |

### Comments
Scope match, cardinality mismatch zib 0..1 xtehr 0..*, datatype almost match, xtehr is an identifier zib a reference. But it is allowed to use identifiers to create a context reference. 


## EHDSMedicationDispense.substitution

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.substitution |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Indicated whether substitution was made by the dispenser |
| id_xtehr | EHDSMedicationDispense.substitution |
| path_xtehr | EHDSMedicationDispense.substitution |
| short_xtehr | Indicated whether substitution was made by the dispenser |
| type_xtehr | Base |

### Comments



## EHDSMedicationDispense.substitution.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.substitution.reason |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reason why the substitution was made or why the expected substitution was not made. |
| id_xtehr | EHDSMedicationDispense.substitution.reason |
| path_xtehr | EHDSMedicationDispense.substitution.reason |
| short_xtehr | Reason why the substitution was made or why the expected substitution was not made. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationDispense.substitution.substitutionOccurred

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.substitution.substitutionOccurred |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Indicated whether substitution was made by the dispenser |
| id_xtehr | EHDSMedicationDispense.substitution.substitutionOccurred |
| path_xtehr | EHDSMedicationDispense.substitution.substitutionOccurred |
| short_xtehr | Indicated whether substitution was made by the dispenser |
| type_xtehr | boolean |

### Comments



## EHDSMedicationDispense.substitution.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.substitution.type |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | What kind of substitution was made by the dispenser |
| id_xtehr | EHDSMedicationDispense.substitution.type |
| path_xtehr | EHDSMedicationDispense.substitution.type |
| short_xtehr | What kind of substitution was made by the dispenser |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationDispense.timeOfDispensation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationDispense.timeOfDispensation |
| zib | MedicationDispense.MedicationDispenseDateTime |
| alias_zib | NL: MedicatieverstrekkingsDatumTijd |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of dispensation |
| definition_zib | The time at which the medicine was supplied. The date and time at which the medicine is delivered.  <br>Note: this is the time at which the medicine was delivered to the patient (or their administrator/representative) and not the request date. |
| id_xtehr | EHDSMedicationDispense.timeOfDispensation |
| id_zib | NL-CM:9.9.20272 |
| name_zib | MedicationDispenseDateTime |
| path_xtehr | EHDSMedicationDispense.timeOfDispensation |
| path_zib | MedicationDispense.MedicationDispenseDateTime |
| short_xtehr | Date and time of dispensation |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Complete match


## zib: MedicationDispense.DistributionForm

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationDispense.DistributionForm |
| alias_zib | NL: Distributievorm |
| card._zib | 0..1 |
| definition_zib | Distribution form |
| id_zib | NL-CM:9.9.20927 |
| name_zib | DistributionForm |
| path_zib | MedicationDispense.DistributionForm |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: MedicationDispense.DurationOfUse

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationDispense.DurationOfUse |
| alias_zib | NL: Verbruiksduur |
| card._zib | 0..1 |
| definition_zib | The period in which the medication is expected to be used. The value depends on the dose and the dispensed amount. |
| id_zib | NL-CM:9.9.20924 |
| name_zib | DurationOfUse |
| path_zib | MedicationDispense.DurationOfUse |
| stereotype_zib | data |
| type_zib | PQ |

### Comments



## zib: MedicationDispense.MedicationDispenseAdditionalInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationDispense.MedicationDispenseAdditionalInformation |
| alias_zib | NL: MedicatieverstrekkingAanvullendeInformatie |
| card._zib | 0..* |
| definition_zib | Additional information includes details on the structure of the medical dispense. This can be e.g. a reason for deviating from the dispense request. <br>For now, this list is used. This list will be replaced by a thesaurus in the G standard at a later stage. |
| id_zib | NL-CM:9.9.23285 |
| name_zib | MedicationDispenseAdditionalInformation |
| path_zib | MedicationDispense.MedicationDispenseAdditionalInformation |
| stereotype_zib | data |
| type_zib | CD |

### Comments
Might match partially with EHDSMedicationDispense.substitution.reason (one way mapping possible xtEHR to zib)


## zib: MedicationDispense.RequestDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationDispense.RequestDate |
| alias_zib | NL: AanschrijfDatum |
| card._zib | 0..1 |
| definition_zib | The request date is the time at which a pharmacist records an intended dispense. |
| id_zib | NL-CM:9.9.22500 |
| name_zib | RequestDate |
| path_zib | MedicationDispense.RequestDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: MedicationDispense.Supplier::HealthcareProvider

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationDispense.Supplier::HealthcareProvider |
| alias_zib | NL: Verstrekker::Zorgaanbieder |
| card._zib | 0..1 |
| definition_zib | In almost all cases, the supplier will be a pharmacy (healthcare provider). It could also be supplied by a webshop (in case of an online order), a drug store or a foreign pharmacist. |
| id_zib | NL-CM:9.9.20858 |
| name_zib | Supplier::HealthcareProvider |
| path_zib | MedicationDispense.Supplier::HealthcareProvider |
| stereotype_zib | context,reference |

### Comments

