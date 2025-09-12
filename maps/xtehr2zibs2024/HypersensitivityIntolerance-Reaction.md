# AllergyIntolerance

| zib                                                          | xtehr                                              | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-------------------------------------------------------------|:---------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
|                                                              | EHDSAllergyIntolerance                             |            |                        |             | 0..*          |
|                                                              | EHDSAllergyIntolerance.header                      |            | Base                   |             | 1..1          |
|                                                              | EHDSAllergyIntolerance.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                              | EHDSAllergyIntolerance.header.identifier           |            | Identifier             |             | 0..*          |
|                                                              | EHDSAllergyIntolerance.header.authorship           |            | Base                   |             | 1..*          |
|                                                              | EHDSAllergyIntolerance.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                              | EHDSAllergyIntolerance.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                              | EHDSAllergyIntolerance.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                              | EHDSAllergyIntolerance.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.header.version              |            | string                 |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.presentedForm               |            | EHDSAttachment         |             | 0..*          |
|                                                              | EHDSAllergyIntolerance.agentOrAllergen             |            | CodeableConcept        |             | 1..1          |
|                                                              | EHDSAllergyIntolerance.typeOfPropensity            |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.description                 |            | string                 |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.criticality                 |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.certainty                   |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.status                      |            | CodeableConcept        |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.onsetDate                   |            | dateTime               |             | 0..1          |
|                                                              | EHDSAllergyIntolerance.endDate                     |            | dateTime               |             | 0..1          |
| Reaction                                                     | EHDSAllergyIntolerance.reaction                    |            | Base                   |             | 0..*          |
| Reaction.Condition                                           | EHDSAllergyIntolerance.reaction.manifestation      |            | CodeableConcept        | 0..1        | 0..*          |
|                                                              | EHDSAllergyIntolerance.reaction.date               |            | dateTime               |             | 0..1          |
| Reaction.Severity                                            | EHDSAllergyIntolerance.reaction.severity           | CD         | CodeableConcept        |             | 0..1          |
| Reaction.DiagnosisDate                                       | EHDSAllergyIntolerance.reaction.onsetDate          | TS         | dateTime               | 1           | 0..1          |
| Reaction.Diagnostician::HealthProfessional                   |                                                    |            |                        | 1           |               |
| Reaction.DiagnosisStatus                                     |                                                    | CD         |                        | 1           |               |
| Reaction.WayOfDetermination                                  |                                                    | CD         |                        | 1           |               |
| Reaction.DiagnosisNameData                                   |                                                    |            |                        | 1           |               |
| Reaction.DiagnosisNameData.DiagnosisName                     |                                                    | CD         |                        | 1           |               |
| Reaction.DiagnosisNameData.FurtherSpecificationDiagnosisName |                                                    | ST         |                        | 0..1        |               |
| Reaction.CausativeAagent                                     |                                                    |            |                        | 1           |               |
| Reaction.CausativeAagent.CausativeSubstance                  |                                                    | CD         |                        | (0..1)      |               |
| Reaction.CausativeAagent.Radiation                           |                                                    | CD         |                        | (0..1)      |               |
| Reaction.RouteOfExposure                                     |                                                    | CD         |                        | 1           |               |
| Reaction.LatencyTime::Range                                  |                                                    |            |                        | 1           |               |
| Reaction.Cause::Procedure                                    |                                                    |            |                        | 0..1        |               |
| Reaction.Comment                                             |                                                    | ST         |                        | 0..1        |               |
| Reaction.HypersensitivityIntolerance                         |                                                    |            |                        | 0..1        |               |



## EHDSAllergyIntolerance

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for allergy/intolerance |
| id_xtehr | EHDSAllergyIntolerance |
| path_xtehr | EHDSAllergyIntolerance |
| short_xtehr | Allergy intolerance model |

### Comments



## EHDSAllergyIntolerance.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSAllergyIntolerance.header |
| path_xtehr | EHDSAllergyIntolerance.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSAllergyIntolerance.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSAllergyIntolerance.header.subject |
| path_xtehr | EHDSAllergyIntolerance.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSAllergyIntolerance.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSAllergyIntolerance.header.identifier |
| path_xtehr | EHDSAllergyIntolerance.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSAllergyIntolerance.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSAllergyIntolerance.header.authorship |
| path_xtehr | EHDSAllergyIntolerance.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSAllergyIntolerance.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSAllergyIntolerance.header.authorship.author[x] |
| path_xtehr | EHDSAllergyIntolerance.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSAllergyIntolerance.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSAllergyIntolerance.header.authorship.datetime |
| path_xtehr | EHDSAllergyIntolerance.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSAllergyIntolerance.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSAllergyIntolerance.header.lastUpdate |
| path_xtehr | EHDSAllergyIntolerance.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSAllergyIntolerance.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSAllergyIntolerance.header.status |
| path_xtehr | EHDSAllergyIntolerance.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSAllergyIntolerance.header.statusReason[x] |
| path_xtehr | EHDSAllergyIntolerance.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSAllergyIntolerance.header.language |
| path_xtehr | EHDSAllergyIntolerance.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSAllergyIntolerance.header.version |
| path_xtehr | EHDSAllergyIntolerance.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSAllergyIntolerance.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSAllergyIntolerance.presentedForm |
| path_xtehr | EHDSAllergyIntolerance.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSAllergyIntolerance.agentOrAllergen

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.agentOrAllergen |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.24 **eHDSIActiveIngredient** (ATC, used in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.61 eHDSISubstance (EMA SMS, used in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.19 eHDSIAllergenNoDrug (SCT, used in MH@EU); ICD-11 Allergens'} |
| card._xtehr | 1..1 |
| definition_xtehr | A specific allergen or other agent/substance (drug, food, chemical agent, etc.) to which the patient has an adverse reaction propensity. |
| id_xtehr | EHDSAllergyIntolerance.agentOrAllergen |
| path_xtehr | EHDSAllergyIntolerance.agentOrAllergen |
| short_xtehr | A specific allergen or other agent/substance (drug, food, chemical agent, etc.) to which the patient has an adverse reaction propensity. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.typeOfPropensity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.typeOfPropensity |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.18 eHDSIAdverseEventType (SCT, used in MH@EU); http://hl7.org/fhir/ValueSet/allergy-intolerance-type (HL7, required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| definition_xtehr | This element describes whether this condition refers to an allergy, non-allergy intolerance, or unknown class of intolerance (not known to be allergy or intolerance) |
| id_xtehr | EHDSAllergyIntolerance.typeOfPropensity |
| path_xtehr | EHDSAllergyIntolerance.typeOfPropensity |
| short_xtehr | This element describes whether this condition refers to an allergy, non-allergy intolerance, or unknown class of intolerance (not known to be allergy or intolerance) |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.description |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Textual description of the allergy or intolerance |
| id_xtehr | EHDSAllergyIntolerance.description |
| path_xtehr | EHDSAllergyIntolerance.description |
| short_xtehr | Textual description of the allergy or intolerance |
| type_xtehr | string |

### Comments



## EHDSAllergyIntolerance.criticality

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.criticality |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.57 eHDSICriticality (HL7, used in MH@EU); http://hl7.org/fhir/ValueSet/allergy-intolerance-criticality (HL7, required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| definition_xtehr | Estimate of the potential clinical harm, or seriousness, of a reaction to an identified substance. |
| id_xtehr | EHDSAllergyIntolerance.criticality |
| path_xtehr | EHDSAllergyIntolerance.criticality |
| short_xtehr | Estimate of the potential clinical harm, or seriousness, of a reaction to an identified substance. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.certainty

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.certainty |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.58 eHDSIAllergyCertainty (HL7, used in MH@EU) ; http://hl7.org/fhir/ValueSet/allergyintolerance-verification (HL7, required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| definition_xtehr | Assertion about the certainty associated with a propensity, or potential risk, of a reaction to the identified substance. Diagnostic and /or clinical evidence of condition |
| id_xtehr | EHDSAllergyIntolerance.certainty |
| path_xtehr | EHDSAllergyIntolerance.certainty |
| short_xtehr | Assertion about the certainty associated with a propensity, or potential risk, of a reaction to the identified substance. Diagnostic and /or clinical evidence of condition |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.status |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.59 eHDSIAllergyStatus (HL7, used in MH@EU); http://hl7.org/fhir/ValueSet/allergyintolerance-clinical (HL7, required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| definition_xtehr | Current status of the allergy or intolerance, for example, whether it is active, in remission, resolved, etc. |
| id_xtehr | EHDSAllergyIntolerance.status |
| path_xtehr | EHDSAllergyIntolerance.status |
| short_xtehr | Current status of the allergy or intolerance, for example, whether it is active, in remission, resolved, etc. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.onsetDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.onsetDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | When allergy or intolerance was identified |
| id_xtehr | EHDSAllergyIntolerance.onsetDate |
| path_xtehr | EHDSAllergyIntolerance.onsetDate |
| short_xtehr | When allergy or intolerance was identified |
| type_xtehr | dateTime |

### Comments



## EHDSAllergyIntolerance.endDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.endDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date of resolution of the allergy (e.g. when the clinician deemed there is no longer any need to track the underlying condition) |
| id_xtehr | EHDSAllergyIntolerance.endDate |
| path_xtehr | EHDSAllergyIntolerance.endDate |
| short_xtehr | Date of resolution of the allergy (e.g. when the clinician deemed there is no longer any need to track the underlying condition) |
| type_xtehr | dateTime |

### Comments



## EHDSAllergyIntolerance.reaction

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction |
| zib | Reaction |
| alias_zib | NL: Reactie |
| card._xtehr | 0..* |
| definition_xtehr | Adverse Reaction Events linked to exposure to substance. |
| definition_zib | This is a reference to the rootconcept of information model Reaction. |
| definitioncode_zib | SNOMED CT: 281647001 Adverse reaction |
| id_xtehr | EHDSAllergyIntolerance.reaction |
| id_zib | NL-CM:5.3.1 |
| name_zib | Reaction |
| path_xtehr | EHDSAllergyIntolerance.reaction |
| path_zib | Reaction |
| short_xtehr | Adverse Reaction Events linked to exposure to substance. |
| stereotype_zib | rootconcept |
| type_xtehr | Base |

### Comments



## EHDSAllergyIntolerance.reaction.manifestation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.manifestation |
| zib | Reaction.Condition |
| alias_zib | NL: AandoeningOfGesteldheid |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.5 eHDSIIllnessandDisorder (ICD-10, alternative in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.11 eHDSIReactionAllergy (SCT, alternative in MH@EU); ICD-11 MMS'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Description of the clinical manifestation of the allergic reaction. Example: anaphylactic shock, angioedema. (the clinical manifestation also gives information about the severity of the observed reaction). |
| definition_zib | The condition that the healthcare provider has identified as a reaction. |
| id_xtehr | EHDSAllergyIntolerance.reaction.manifestation |
| id_zib | NL-CM:5.3.2 |
| name_zib | Condition |
| path_xtehr | EHDSAllergyIntolerance.reaction.manifestation |
| path_zib | Reaction.Condition |
| short_xtehr | Description of the clinical manifestation of the allergic reaction. Example: anaphylactic shock, angioedema. (the clinical manifestation also gives information about the severity of the observed reaction). |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAllergyIntolerance.reaction.date

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.date |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of allergy manifestation |
| id_xtehr | EHDSAllergyIntolerance.reaction.date |
| path_xtehr | EHDSAllergyIntolerance.reaction.date |
| short_xtehr | Date and time of allergy manifestation |
| type_xtehr | dateTime |

### Comments



## EHDSAllergyIntolerance.reaction.severity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.severity |
| zib | Reaction.Severity |
| alias_zib | NL: Ernst |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.13 eHDSISeverity (SCT, used in MH@EU); http://hl7.org/fhir/ValueSet/reaction-event-severity (HL7, Required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| definition_xtehr | Severity of the clinical manifestation of the allergic reaction. |
| definition_zib | The degree of severity of the reaction. |
| id_xtehr | EHDSAllergyIntolerance.reaction.severity |
| id_zib | NL-CM:5.4.6 |
| name_zib | Severity |
| path_xtehr | EHDSAllergyIntolerance.reaction.severity |
| path_zib | Reaction.Severity |
| short_xtehr | Severity of the clinical manifestation of the allergic reaction. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSAllergyIntolerance.reaction.onsetDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.onsetDate |
| zib | Reaction.DiagnosisDate |
| alias_zib | NL: DiagnoseDatum |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Date of the observation of the reaction |
| definition_zib | Date (and time) at which the care professional came to the diagnosis. |
| definitioncode_zib | SNOMED CT: 432213005 Date of diagnosis |
| id_xtehr | EHDSAllergyIntolerance.reaction.onsetDate |
| id_zib | NL-CM:5.3.6 |
| name_zib | DiagnosisDate |
| path_xtehr | EHDSAllergyIntolerance.reaction.onsetDate |
| path_zib | Reaction.DiagnosisDate |
| short_xtehr | Date of the observation of the reaction |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## zib: Reaction.Diagnostician::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.Diagnostician::HealthProfessional |
| alias_zib | NL: DiagnoseSteller::Zorgverlener |
| card._zib | 1 |
| definition_zib | The health professional that acquired the diagnostic insight of the reaction. This can be a different individual than the person who recorded the diagnostic insight. |
| definitioncode_zib | PRF performer |
| id_zib | NL-CM:5.3.5 |
| name_zib | Diagnostician::HealthProfessional |
| path_zib | Reaction.Diagnostician::HealthProfessional |
| stereotype_zib | context,reference |

### Comments



## zib: Reaction.DiagnosisStatus

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.DiagnosisStatus |
| alias_zib | NL: DiagnoseStatus |
| card._zib | 1 |
| definition_zib | Indicates the status of the diagnostic process. |
| id_zib | NL-CM:5.3.7 |
| name_zib | DiagnosisStatus |
| path_zib | Reaction.DiagnosisStatus |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Reaction.WayOfDetermination

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.WayOfDetermination |
| alias_zib | NL: WijzeVanVastellen |
| card._zib | 1 |
| definition_zib | The way in which the reaction is determined. |
| definitioncode_zib | SNOMED CT: 418775008 Finding method |
| id_zib | NL-CM:5.3.8 |
| name_zib | WayOfDetermination |
| path_zib | Reaction.WayOfDetermination |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Reaction.DiagnosisNameData

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.DiagnosisNameData |
| alias_zib | NL: DiagnoseNaamGegevens |
| card._zib | 1 |
| definition_zib | Container of the DiagnosisNameData concept involving a reaction.This container contains all data elements of the DiagnosisNameData concept.<br>Represents a reaction as interpretation of the condition. |
| id_zib | NL-CM:5.3.9 |
| name_zib | DiagnosisNameData |
| path_zib | Reaction.DiagnosisNameData |
| stereotype_zib | container |

### Comments



## zib: Reaction.DiagnosisNameData.DiagnosisName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.DiagnosisNameData.DiagnosisName |
| alias_zib | NL: DiagnoseNaam |
| card._zib | 1 |
| definition_zib | The term with associated code that the care professional selects from the used code list. |
| definitioncode_zib | SNOMED CT: 439401001 Diagnosis |
| id_zib | NL-CM:5.3.10 |
| name_zib | DiagnosisName |
| path_zib | Reaction.DiagnosisNameData.DiagnosisName |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Reaction.DiagnosisNameData.FurtherSpecificationDiagnosisName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.DiagnosisNameData.FurtherSpecificationDiagnosisName |
| alias_zib | NL: NadereSpecificatieDiagnoseNaam |
| card._zib | 0..1 |
| definition_zib | A more detailed description of the name of the reaction in free text, when this detail is not available in the used code list. |
| id_zib | NL-CM:5.3.11 |
| name_zib | FurtherSpecificationDiagnosisName |
| path_zib | Reaction.DiagnosisNameData.FurtherSpecificationDiagnosisName |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Reaction.CausativeAagent

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.CausativeAagent |
| alias_zib | NL: Veroorzaker |
| card._zib | 1 |
| definition_zib | Container of the CausativeAagent concept.This container contains all data elements of the CausativeAagent concept.<br>It is the agent that triggered the reaction. |
| definitioncode_zib | SNOMED CT: 246075003 Causative agent |
| id_zib | NL-CM:5.3.12 |
| name_zib | CausativeAagent |
| path_zib | Reaction.CausativeAagent |
| stereotype_zib | container |

### Comments



## zib: Reaction.CausativeAagent.CausativeSubstance

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.CausativeAagent.CausativeSubstance |
| alias_zib | NL: VeroorzakendeStof |
| card._zib | (0..1) |
| definition_zib | The substance that (presumably) caused the adverse reaction. |
| definitioncode_zib | SNOMED CT: 105590001 Substance |
| id_zib | NL-CM:5.3.13 |
| name_zib | CausativeSubstance |
| path_zib | Reaction.CausativeAagent.CausativeSubstance |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Reaction.CausativeAagent.Radiation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.CausativeAagent.Radiation |
| alias_zib | NL: Straling |
| card._zib | (0..1) |
| definition_zib | The radiation that (presumably) caused the reaction. |
| definitioncode_zib | SNOMED CT: 82107009 Radiation |
| id_zib | NL-CM:5.3.14 |
| name_zib | Radiation |
| path_zib | Reaction.CausativeAagent.Radiation |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Reaction.RouteOfExposure

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.RouteOfExposure |
| alias_zib | NL: WijzeVanBlootstelling |
| card._zib | 1 |
| definition_zib | Way in which the patient came into contact with the causative agent or the way in which the agent was administered. |
| definitioncode_zib | SNOMED CT: 410675002 Route of administration |
| id_zib | NL-CM:5.3.15 |
| name_zib | RouteOfExposure |
| path_zib | Reaction.RouteOfExposure |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Reaction.LatencyTime::Range

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.LatencyTime::Range |
| alias_zib | NL: LatentieTijd::Bereik |
| card._zib | 1 |
| definition_zib | The period of time between the moment of exposure to the substance or radiation and the onset of the undesirable reaction. |
| definitioncode_zib | SNOMED CT: 350371000146103 Time interval between date of exposure and date of onset of symptoms |
| id_zib | NL-CM:5.3.16 |
| name_zib | LatencyTime::Range |
| path_zib | Reaction.LatencyTime::Range |
| stereotype_zib | data,reference |

### Comments



## zib: Reaction.Cause::Procedure

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.Cause::Procedure |
| alias_zib | NL: Aanleiding::Verrichting |
| card._zib | 0..1 |
| definition_zib | The procedure that caused the reaction. |
| definitioncode_zib | SNOMED CT: 71388002 Procedure |
| id_zib | NL-CM:5.3.3 |
| name_zib | Cause::Procedure |
| path_zib | Reaction.Cause::Procedure |
| stereotype_zib | data,reference |

### Comments



## zib: Reaction.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Textual explanation of the reaction which cannot be expressed in any of the other fields. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:5.3.18 |
| name_zib | Comment |
| path_zib | Reaction.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Reaction.HypersensitivityIntolerance

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Reaction.HypersensitivityIntolerance |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| card._zib | 0..1 |
| definition_zib | Hypersensitivity or intolerance underlying the reaction. |
| definitioncode_zib | SNOMED CT: 420134006 Propensity to adverse reaction |
| id_zib | NL-CM:5.3.4 |
| name_zib | HypersensitivityIntolerance |
| path_zib | Reaction.HypersensitivityIntolerance |
| stereotype_zib | data,reference |

### Comments

