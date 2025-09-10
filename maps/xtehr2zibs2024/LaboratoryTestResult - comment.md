# LaboratoryTestResult as of 05-9-2025

## Version history

v1: 05-09-2025, initial version

## Actions

## Compared
### Scope

### Other

## Discussions (datum:) LabResult
# Notulen  

## Actiepuntenlijst

| zib                                                      | xtehr                                                                      | type_zib   | type_xtehr                   | card._zib   | card._xtehr   |
|:---------------------------------------------------------|:---------------------------------------------------------------------------|:-----------|:-----------------------------|:------------|:--------------|
| LaboratoryTestResult                                     | EHDSLaboratoryReport                                                       |            |                              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.attachments[x]                                        |            | EHDSAttachment               |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body                                                  |            | Base                         |             | 0..1          |
|                                                          | EHDSLaboratoryReport.body.orderInformation                                 |            | Base                         |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.orderInformation.clinicalQuestion                |            | string                       |             | 0..1          |
|                                                          | EHDSLaboratoryReport.body.orderInformation.orderDateAndTime                |            | dateTime                     |             | 0..1          |
|                                                          | EHDSLaboratoryReport.body.orderInformation.orderId                         |            | Identifier                   |             | 1..*          |
|                                                          | EHDSLaboratoryReport.body.orderInformation.orderPlacer[x]                  |            | EHDSHealthProfessional       |             | 0..1          |
|                                                          | EHDSLaboratoryReport.body.orderInformation.orderReasonText                 |            | string                       |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.orderInformation.orderReason[x]                  |            | CodeableConcept              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation                            |            | Base                         |             | 0..1          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation.condition                  |            | EHDSCondition                |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation.medicationAdministration   |            | EHDSMedicationAdministration |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation.observation                |            | EHDSObservation              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation.otherSupportingInformation |            | Resource                     |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation.sexForClinicalUse          |            | CodeableConcept              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.body.supportingInformation.vaccination                |            | EHDSImmunisation             |             | 0..*          |
|                                                          | EHDSLaboratoryReport.header                                                |            | Base                         |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.attestation                                    |            | Base                         |             | 0..*          |
|                                                          | EHDSLaboratoryReport.header.attestation.attester                           |            | EHDSHealthProfessional       |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.attestation.datetime                           |            | dateTime                     |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.authorSpecialty                                |            | CodeableConcept              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.header.authorship                                     |            | Base                         |             | 1..*          |
|                                                          | EHDSLaboratoryReport.header.authorship.author[x]                           |            | EHDSHealthProfessional       |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.authorship.datetime                            |            | dateTime                     |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.confidentiality                                |            | CodeableConcept              |             | 0..1          |
|                                                          | EHDSLaboratoryReport.header.custodian                                      |            | EHDSOrganisation             |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.documentFormat                                 |            | CodeableConcept              |             | 0..1          |
|                                                          | EHDSLaboratoryReport.header.documentStatus                                 |            | CodeableConcept              |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.documentTitle                                  |            | string                       |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.documentType                                   |            | CodeableConcept              |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.eventType                                      |            | CodeableConcept              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.header.identifier                                     |            | Identifier                   |             | 1..*          |
|                                                          | EHDSLaboratoryReport.header.language                                       |            | CodeableConcept              |             | 0..1          |
|                                                          | EHDSLaboratoryReport.header.lastUpdate                                     |            | dateTime                     |             | 0..1          |
|                                                          | EHDSLaboratoryReport.header.legalAuthentication                            |            | Base                         |             | 0..1          |
|                                                          | EHDSLaboratoryReport.header.legalAuthentication.datetime                   |            | dateTime                     |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.legalAuthentication.legalAuthenticator         |            | EHDSHealthProfessional       |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.period                                         |            | Period                       |             | 0..1          |
| LaboratoryTestResult.ResultStatus                        | EHDSLaboratoryReport.header.status                                         | CD         | CodeableConcept              | 0..1        | 1..1          |
|                                                          | EHDSLaboratoryReport.header.statusReason[x]                                |            | CodeableConcept              |             | 0..1          |
|                                                          | EHDSLaboratoryReport.header.subject                                        |            | EHDSPatient                  |             | 1..1          |
|                                                          | EHDSLaboratoryReport.header.version                                        |            | string                       |             | 0..1          |
|                                                          | EHDSLaboratoryReport.healthInsuranceAndPaymentInformation                  |            | EHDSCoverage                 |             | 0..*          |
|                                                          | EHDSLaboratoryReport.intendedRecipient[x]                                  |            | EHDSPatient                  |             | 0..*          |
|                                                          | EHDSLaboratoryReport.knowledgeResources                                    |            | Base                         |             | 0..0          |
|                                                          | EHDSLaboratoryReport.knowledgeResources.externalReference                  |            | RelatedArtifact              |             | 0..*          |
|                                                          | EHDSLaboratoryReport.knowledgeResources.relatedTo                          |            | Reference                    |             | 0..*          |
|                                                          | EHDSLaboratoryReport.presentedForm                                         |            | EHDSAttachment               |             | 0..*          |
|                                                          | EHDSLaboratoryReport.resultData                                            |            | Base                         |             | 1..1          |
| LaboratoryTestResult.Comment                             | EHDSLaboratoryReport.resultData.commentsInterpretationAndRecommendations   | ST         | Narrative                    | 0..1        | 0..*          |
| LaboratoryTestResult.LaboratoryTest                      | EHDSLaboratoryReport.resultData.laboratoryTestResults                      |            | EHDSLaboratoryObservation    | 0..*        | 0..*          |
|                                                          | EHDSLaboratoryReport.serviceRequest                                        |            | EHDSServiceRequest           |             | 0..*          |
| LaboratoryTestResult.Specimen                            | EHDSLaboratoryReport.specimen                                              |            | EHDSSpecimen                 | 0..1        | 0..*          |
| LaboratoryTestResult.PanelOrBattery                      |                                                                            | CD         |                              | 0..1        |               |
| LaboratoryTestResult.ResultType                          |                                                                            | CD         |                              | 0..1        |               |
| LaboratoryTestResult.RelatedResult::LaboratoryTestResult |                                                                            |            |                              | 0..*        |               |
| LaboratoryTestResult.Performer::HealthcareProvider       |                                                                            |            |                              | 0..1        |               |



## EHDSLaboratoryReport

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport |
| zib | LaboratoryTestResult |
| alias_zib | NL: LaboratoriumUitslag |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Laboratory result report |
| definition_zib | Root concept of the LaboratoryTestResult information model. This root concept contains all data elements of the LaboratoryTestResult information model. |
| id_xtehr | EHDSLaboratoryReport |
| id_zib | NL-CM:13.1.1 |
| name_zib | LaboratoryTestResult |
| path_xtehr | EHDSLaboratoryReport |
| path_zib | LaboratoryTestResult |
| short_xtehr | Laboratory report model |
| stereotype_zib | rootconcept |

### Comments



## EHDSLaboratoryReport.attachments[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.attachments[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Report attachments data elements |
| id_xtehr | EHDSLaboratoryReport.attachments[x] |
| path_xtehr | EHDSLaboratoryReport.attachments[x] |
| short_xtehr | Report attachments data elements |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSLaboratoryReport.body

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Laboratory Report structured body |
| id_xtehr | EHDSLaboratoryReport.body |
| path_xtehr | EHDSLaboratoryReport.body |
| short_xtehr | Laboratory Report structured body |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.body.orderInformation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Order Information (Laboratory Result Report could respond to multiple test orders) |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation |
| short_xtehr | Order Information (Laboratory Result Report could respond to multiple test orders) |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.body.orderInformation.clinicalQuestion

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation.clinicalQuestion |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Specification of clinical question (goal of the investigation) to be answered by the laboratory investigation. |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation.clinicalQuestion |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation.clinicalQuestion |
| short_xtehr | Specification of clinical question (goal of the investigation) to be answered by the laboratory investigation. |
| type_xtehr | string |

### Comments



## EHDSLaboratoryReport.body.orderInformation.orderDateAndTime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation.orderDateAndTime |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the order placement. |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation.orderDateAndTime |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation.orderDateAndTime |
| short_xtehr | Date and time of the order placement. |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryReport.body.orderInformation.orderId

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation.orderId |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | An identifier of the laboratory test order. Laboratory Result Report may respond to multiple orders. |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation.orderId |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation.orderId |
| short_xtehr | An identifier of the laboratory test order. Laboratory Result Report may respond to multiple orders. |
| type_xtehr | Identifier |

### Comments



## EHDSLaboratoryReport.body.orderInformation.orderPlacer[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation.orderPlacer[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The person/organisation "authorised" to place the order. Order placer could be either a health professional, health professional organisation or the patient himself. |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation.orderPlacer[x] |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation.orderPlacer[x] |
| short_xtehr | The person/organisation "authorised" to place the order. Order placer could be either a health professional, health professional organisation or the patient himself. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSLaboratoryReport.body.orderInformation.orderReasonText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation.orderReasonText |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | An explanation or justification for why this service is being requested in textual form. |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation.orderReasonText |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation.orderReasonText |
| short_xtehr | An explanation or justification for why this service is being requested in textual form. |
| type_xtehr | string |

### Comments



## EHDSLaboratoryReport.body.orderInformation.orderReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.orderInformation.orderReason[x] |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..* |
| definition_xtehr | An explanation or justification for why this service is being requested in coded form. |
| id_xtehr | EHDSLaboratoryReport.body.orderInformation.orderReason[x] |
| path_xtehr | EHDSLaboratoryReport.body.orderInformation.orderReason[x] |
| short_xtehr | An explanation or justification for why this service is being requested in coded form.  |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.body.supportingInformation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Additional clinical information about the patient or specimen that may influence the services or their interpretations. This information includes diagnosis, clinical findings and other observations. In laboratory ordering these are typically referred to as 'ask at order entry questions (AOEs).' This includes observations explicitly requested by the producer (filler) to provide context or supporting information needed to complete the order. For example, reporting the amount of inspired oxygen for blood gas measurements. |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation |
| short_xtehr | Additional clinical information about the patient or specimen that may influence the services or their interpretations. This information includes diagnosis, clinical findings and other observations. In laboratory ordering these are typically referred to as 'ask at order entry questions (AOEs).' This includes observations explicitly requested by the producer (filler) to provide context or supporting information needed to complete the order. For example, reporting the amount of inspired oxygen for blood gas measurements. |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.body.supportingInformation.condition

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation.condition |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Condition that may influence the service or result interpretation. |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation.condition |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation.condition |
| short_xtehr | Condition that may influence the service or result interpretation. |
| type_xtehr | EHDSCondition |

### Comments



## EHDSLaboratoryReport.body.supportingInformation.medicationAdministration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation.medicationAdministration |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Medication administered before ordering the service. |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation.medicationAdministration |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation.medicationAdministration |
| short_xtehr | Medication administered before ordering the service. |
| type_xtehr | EHDSMedicationAdministration |

### Comments



## EHDSLaboratoryReport.body.supportingInformation.observation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation.observation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Clinical findings and other observations. |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation.observation |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation.observation |
| short_xtehr | Clinical findings and other observations. |
| type_xtehr | EHDSObservation |

### Comments



## EHDSLaboratoryReport.body.supportingInformation.otherSupportingInformation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation.otherSupportingInformation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Any other type of relevant supporting information |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation.otherSupportingInformation |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation.otherSupportingInformation |
| short_xtehr | Any other type of relevant supporting information |
| type_xtehr | Resource |

### Comments



## EHDSLaboratoryReport.body.supportingInformation.sexForClinicalUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation.sexForClinicalUse |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 sex-parameter-for-clinical-use'} |
| card._xtehr | 0..* |
| definition_xtehr | A Sex Parameter for Clinical Use is a parameter that provides guidance on how a recipient should apply settings or reference ranges that are derived from observable information such as an organ inventory, recent hormone lab tests, genetic testing, menstrual status, obstetric history, etc.. This property is intended for use in clinical decision making, and indicates that treatment or diagnostic tests should consider best practices associated with the relevant reference population |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation.sexForClinicalUse |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation.sexForClinicalUse |
| short_xtehr | A Sex Parameter for Clinical Use is a parameter that provides guidance on how a recipient should apply settings or reference ranges that are derived from observable information such as an organ inventory, recent hormone lab tests, genetic testing, menstrual status, obstetric history, etc.. This property is intended for use in clinical decision making, and indicates that treatment or diagnostic tests should consider best practices associated with the relevant reference population |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.body.supportingInformation.vaccination

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.body.supportingInformation.vaccination |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Vaccination history of the patient. |
| id_xtehr | EHDSLaboratoryReport.body.supportingInformation.vaccination |
| path_xtehr | EHDSLaboratoryReport.body.supportingInformation.vaccination |
| short_xtehr | Vaccination history of the patient.  |
| type_xtehr | EHDSImmunisation |

### Comments



## EHDSLaboratoryReport.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSLaboratoryReport.header |
| path_xtehr | EHDSLaboratoryReport.header |
| short_xtehr | Laboratory Report header |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.header.attestation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.attestation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Document attestation details |
| id_xtehr | EHDSLaboratoryReport.header.attestation |
| path_xtehr | EHDSLaboratoryReport.header.attestation |
| short_xtehr | Attestation |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.header.attestation.attester

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.attestation.attester |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Attester who validated the document. Mulitple attesters could be provided. |
| id_xtehr | EHDSLaboratoryReport.header.attestation.attester |
| path_xtehr | EHDSLaboratoryReport.header.attestation.attester |
| short_xtehr | Attester |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSLaboratoryReport.header.attestation.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.attestation.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the approval of the document by Attester. |
| id_xtehr | EHDSLaboratoryReport.header.attestation.datetime |
| path_xtehr | EHDSLaboratoryReport.header.attestation.datetime |
| short_xtehr | DateTime |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryReport.header.authorSpecialty

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.authorSpecialty |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..* |
| definition_xtehr | Additional details about where the content was created (e.g. clinical specialty) |
| id_xtehr | EHDSLaboratoryReport.header.authorSpecialty |
| path_xtehr | EHDSLaboratoryReport.header.authorSpecialty |
| short_xtehr | Specialty |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSLaboratoryReport.header.authorship |
| path_xtehr | EHDSLaboratoryReport.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSLaboratoryReport.header.authorship.author[x] |
| path_xtehr | EHDSLaboratoryReport.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSLaboratoryReport.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSLaboratoryReport.header.authorship.datetime |
| path_xtehr | EHDSLaboratoryReport.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryReport.header.confidentiality

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.confidentiality |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:Confidentiality'} |
| card._xtehr | 0..1 |
| definition_xtehr | Level of confidentiality of the document. Implicit value is normal. |
| id_xtehr | EHDSLaboratoryReport.header.confidentiality |
| path_xtehr | EHDSLaboratoryReport.header.confidentiality |
| short_xtehr | Confidentiality |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.custodian

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.custodian |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Organisation that is in charge of maintaining the document/report. |
| id_xtehr | EHDSLaboratoryReport.header.custodian |
| path_xtehr | EHDSLaboratoryReport.header.custodian |
| short_xtehr | Document custodian |
| type_xtehr | EHDSOrganisation |

### Comments



## EHDSLaboratoryReport.header.documentFormat

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.documentFormat |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Document Format Codes'} |
| card._xtehr | 0..1 |
| definition_xtehr | An identifier of the document constraints, encoding, structure, and template that the document conforms to beyond the base format indicated in the mimeType. |
| id_xtehr | EHDSLaboratoryReport.header.documentFormat |
| path_xtehr | EHDSLaboratoryReport.header.documentFormat |
| short_xtehr | Document format |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.documentStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.documentStatus |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:CompositionStatus'} |
| card._xtehr | 1..1 |
| definition_xtehr | The status of the Discharge report. E.g., preliminary, final. |
| id_xtehr | EHDSLaboratoryReport.header.documentStatus |
| path_xtehr | EHDSLaboratoryReport.header.documentStatus |
| short_xtehr | Document status |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.documentTitle

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.documentTitle |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Document title, such as Discharge Report, Laboratory Result Report, etc. |
| id_xtehr | EHDSLaboratoryReport.header.documentTitle |
| path_xtehr | EHDSLaboratoryReport.header.documentTitle |
| short_xtehr | Document title |
| type_xtehr | string |

### Comments



## EHDSLaboratoryReport.header.documentType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.documentType |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'LOINC'} |
| card._xtehr | 1..1 |
| definition_xtehr | Identifies the type of document at hand, e.g. Discharge report. |
| id_xtehr | EHDSLaboratoryReport.header.documentType |
| path_xtehr | EHDSLaboratoryReport.header.documentType |
| short_xtehr | Document type |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.eventType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.eventType |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..* |
| definition_xtehr | Categorization of the event covered by the document (e.g. laboratory study types, imaging study types including modality, etc.). Selection of such tags or labels depends on the use case and agreement betwen data sharing parties. This meta-data element serves primarily for searching and filtering purpuses. |
| id_xtehr | EHDSLaboratoryReport.header.eventType |
| path_xtehr | EHDSLaboratoryReport.header.eventType |
| short_xtehr | Event type |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.identifier |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Unique identifier of the document |
| id_xtehr | EHDSLaboratoryReport.header.identifier |
| path_xtehr | EHDSLaboratoryReport.header.identifier |
| short_xtehr | Document ID |
| type_xtehr | Identifier |

### Comments



## EHDSLaboratoryReport.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSLaboratoryReport.header.language |
| path_xtehr | EHDSLaboratoryReport.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSLaboratoryReport.header.lastUpdate |
| path_xtehr | EHDSLaboratoryReport.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryReport.header.legalAuthentication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.legalAuthentication |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Document legal authentication |
| id_xtehr | EHDSLaboratoryReport.header.legalAuthentication |
| path_xtehr | EHDSLaboratoryReport.header.legalAuthentication |
| short_xtehr | Legal authentication |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.header.legalAuthentication.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.legalAuthentication.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time when the document was authorized. |
| id_xtehr | EHDSLaboratoryReport.header.legalAuthentication.datetime |
| path_xtehr | EHDSLaboratoryReport.header.legalAuthentication.datetime |
| short_xtehr | DateTime |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryReport.header.legalAuthentication.legalAuthenticator

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.legalAuthentication.legalAuthenticator |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | The person taking responsibility for the medical content of the document |
| id_xtehr | EHDSLaboratoryReport.header.legalAuthentication.legalAuthenticator |
| path_xtehr | EHDSLaboratoryReport.header.legalAuthentication.legalAuthenticator |
| short_xtehr | Legal authenticator |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSLaboratoryReport.header.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time of service that is being documented |
| id_xtehr | EHDSLaboratoryReport.header.period |
| path_xtehr | EHDSLaboratoryReport.header.period |
| short_xtehr | Period |
| type_xtehr | Period |

### Comments



## EHDSLaboratoryReport.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.status |
| zib | LaboratoryTestResult.ResultStatus |
| alias_zib | NL: ResultaatStatus |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Status of the resource |
| definition_zib | The status of the laboratory test result. If the laboratory test is a panel/cluster,  this status reflects the status of the whole panel/cluster. If the status item per subtest is used too, this status must be in accordance with these status values. |
| definitioncode_zib | LOINC: 92235-1 Lab order result status |
| id_xtehr | EHDSLaboratoryReport.header.status |
| id_zib | NL-CM:13.1.6 |
| name_zib | ResultStatus |
| path_xtehr | EHDSLaboratoryReport.header.status |
| path_zib | LaboratoryTestResult.ResultStatus |
| short_xtehr | Status of the resource |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSLaboratoryReport.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSLaboratoryReport.header.statusReason[x] |
| path_xtehr | EHDSLaboratoryReport.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryReport.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSLaboratoryReport.header.subject |
| path_xtehr | EHDSLaboratoryReport.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSLaboratoryReport.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSLaboratoryReport.header.version |
| path_xtehr | EHDSLaboratoryReport.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSLaboratoryReport.healthInsuranceAndPaymentInformation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.healthInsuranceAndPaymentInformation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Health insurance and payment information |
| id_xtehr | EHDSLaboratoryReport.healthInsuranceAndPaymentInformation |
| path_xtehr | EHDSLaboratoryReport.healthInsuranceAndPaymentInformation |
| short_xtehr | Health insurance and payment information |
| type_xtehr | EHDSCoverage |

### Comments



## EHDSLaboratoryReport.intendedRecipient[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.intendedRecipient[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Information recipient (intended recipient or recipients of the report, additional recipients might be identified by the ordering party, e.g. GP, other specialist), if applicable |
| id_xtehr | EHDSLaboratoryReport.intendedRecipient[x] |
| path_xtehr | EHDSLaboratoryReport.intendedRecipient[x] |
| short_xtehr | Intended recipient |
| type_xtehr | EHDSPatient |

### Comments



## EHDSLaboratoryReport.knowledgeResources

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.knowledgeResources |
| zib |  |
| card._xtehr | 0..0 |
| definition_xtehr | Related documents and information sources |
| id_xtehr | EHDSLaboratoryReport.knowledgeResources |
| path_xtehr | EHDSLaboratoryReport.knowledgeResources |
| short_xtehr | Related documents and information sources |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.knowledgeResources.externalReference

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.knowledgeResources.externalReference |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | ... |
| id_xtehr | EHDSLaboratoryReport.knowledgeResources.externalReference |
| path_xtehr | EHDSLaboratoryReport.knowledgeResources.externalReference |
| short_xtehr | ... |
| type_xtehr | RelatedArtifact |

### Comments



## EHDSLaboratoryReport.knowledgeResources.relatedTo

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.knowledgeResources.relatedTo |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | ... |
| id_xtehr | EHDSLaboratoryReport.knowledgeResources.relatedTo |
| path_xtehr | EHDSLaboratoryReport.knowledgeResources.relatedTo |
| short_xtehr | ... |
| type_xtehr | Reference |

### Comments



## EHDSLaboratoryReport.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSLaboratoryReport.presentedForm |
| path_xtehr | EHDSLaboratoryReport.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSLaboratoryReport.resultData

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.resultData |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Laboratory report result data |
| id_xtehr | EHDSLaboratoryReport.resultData |
| path_xtehr | EHDSLaboratoryReport.resultData |
| short_xtehr | Laboratory report result data |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryReport.resultData.commentsInterpretationAndRecommendations

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.resultData.commentsInterpretationAndRecommendations |
| zib | LaboratoryTestResult.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Narrative Comments, such as a textual interpretation or advice accompanying the result report, for example. |
| definition_zib | Comments, such as a textual interpretation or advice accompanying the result, for example. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSLaboratoryReport.resultData.commentsInterpretationAndRecommendations |
| id_zib | NL-CM:13.1.5 |
| name_zib | Comment |
| path_xtehr | EHDSLaboratoryReport.resultData.commentsInterpretationAndRecommendations |
| path_zib | LaboratoryTestResult.Comment |
| short_xtehr | Narrative Comments, such as a textual interpretation or advice accompanying the result report, for example. |
| stereotype_zib | data |
| type_xtehr | Narrative |
| type_zib | ST |

### Comments



## EHDSLaboratoryReport.resultData.laboratoryTestResults

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.resultData.laboratoryTestResults |
| zib | LaboratoryTestResult.LaboratoryTest |
| alias_zib | NL: LaboratoriumTest |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Observation details (report could consist of�multiple observations) |
| definition_zib | Container of the LaboratoryTest concept. This container contains all data elements of the LaboratoryTest concept. |
| id_xtehr | EHDSLaboratoryReport.resultData.laboratoryTestResults |
| id_zib | NL-CM:13.1.3 |
| name_zib | LaboratoryTest |
| path_xtehr | EHDSLaboratoryReport.resultData.laboratoryTestResults |
| path_zib | LaboratoryTestResult.LaboratoryTest |
| short_xtehr | Observation details (report could consist of�multiple observations) |
| stereotype_zib | container |
| type_xtehr | EHDSLaboratoryObservation |

### Comments



## EHDSLaboratoryReport.serviceRequest

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.serviceRequest |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Specification of requested service or services |
| id_xtehr | EHDSLaboratoryReport.serviceRequest |
| path_xtehr | EHDSLaboratoryReport.serviceRequest |
| short_xtehr | Specification of requested service or services |
| type_xtehr | EHDSServiceRequest |

### Comments



## EHDSLaboratoryReport.specimen

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryReport.specimen |
| zib | LaboratoryTestResult.Specimen |
| alias_zib | NL: Monster |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Specimen information |
| definition_zib | Container of the concept Specimen. This container contains all data elements of the concept Specimen. A completed container is related to a sample from the Snomed Hierarchy. <br> <br>If the TestCode implicitly also describes a specimen (often the case if coded in LOINC), elements within the concept specimen may not conflict with it. However, if desired, these data can provide a more detailed description.This is in line with the agreements made in the IHE/Nictiz e-Lab programme. |
| definitioncode_zib | SNOMED CT: 123038009 Specimen |
| id_xtehr | EHDSLaboratoryReport.specimen |
| id_zib | NL-CM:13.1.2 |
| name_zib | Specimen |
| path_xtehr | EHDSLaboratoryReport.specimen |
| path_zib | LaboratoryTestResult.Specimen |
| short_xtehr | Specimen information |
| stereotype_zib | container |
| type_xtehr | EHDSSpecimen |

### Comments



## zib: LaboratoryTestResult.PanelOrBattery

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.PanelOrBattery |
| alias_zib | NL: Onderzoek |
| card._zib | 0..1 |
| definition_zib | For laboratory tests comprising multiple subtests and often requested together as a whole, this concept contains the name of the compound request (often indicated as a �panel�, �battery� or �cluster�). Examples include: blood gases and EBV serology. |
| id_zib | NL-CM:13.1.4 |
| name_zib | PanelOrBattery |
| path_zib | LaboratoryTestResult.PanelOrBattery |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: LaboratoryTestResult.ResultType

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.ResultType |
| alias_zib | NL: ResultaatType |
| card._zib | 0..1 |
| definition_zib | The type of result defines the laboratory specialty under which the test is categorized. |
| id_zib | NL-CM:13.1.7 |
| name_zib | ResultType |
| path_zib | LaboratoryTestResult.ResultType |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: LaboratoryTestResult.RelatedResult::LaboratoryTestResult

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.RelatedResult::LaboratoryTestResult |
| alias_zib | NL: GerelateerdeUitslag::LaboratoriumUitslag |
| card._zib | 0..* |
| definition_zib | Reference to related tests, e.g. paired tests or sequential tests like gram staining and microbiological cultures. It concerns previous results that collectively lead to the current interpretation. |
| id_zib | NL-CM:13.1.33 |
| name_zib | RelatedResult::LaboratoryTestResult |
| path_zib | LaboratoryTestResult.RelatedResult::LaboratoryTestResult |
| stereotype_zib | data,reference |

### Comments



## zib: LaboratoryTestResult.Performer::HealthcareProvider

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.Performer::HealthcareProvider |
| alias_zib | NL: Uitvoerder::Zorgaanbieder |
| card._zib | 0..1 |
| definition_zib | The healthcare provider who is responsible for the excecution of the laboratory examination and delivering the Laboratory result. |
| id_zib | NL-CM:13.1.35 |
| name_zib | Performer::HealthcareProvider |
| path_zib | LaboratoryTestResult.Performer::HealthcareProvider |
| stereotype_zib | context,reference |

### Comments

