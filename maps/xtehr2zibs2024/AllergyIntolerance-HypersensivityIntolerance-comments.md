# AllergyIntolerance

## Overall discussion

EHDSAllergyIntolerance maps to the following zibs, that are connected by references:
+ HypersensitivityIntolerance
+ Reaction
+ Condition 
+ Symptom 

In this comparison, the mapping to HypersensitivityIntolerance is used as a basis, but references to the zib models Reaction, Symptom and Condition are made in the discussion of the concepts in the Xt-EHR model that map to concepts in these zibs.

Since the Xt-EHR model does not make the distinction, it lacks the functionality of the zibs to relate the AllergyIntolerance and is reactions as diagnoses to conditions and their symptoms.

Hypersensitity to radiation cannot be expressed using the Xt-EHR model.   

Issues on the Xt-EHR model:  
+ We need a clearer definition of EHDSAllergyIntolerance.onsetDate for a correct mapping to one of the zibs. Is the diagnosis date or the onset of the condition?
+ The name of the reaction seems to be missing.
+ The reaction.date and reaction.severity seem to apply to the manifestation by definition, but are modelled as attributes of .reaction
General remark:
+ During the qualification of e-Overdracht and BgZ it appeared that no vendor was able to register symptoms grouped by reaction. In general they register HypersensitivityIntolerance with a list of symptoms (or a mox of symptoms and reactions).

  



| zib                                                                             | xtehr                                              | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------------------------------------------------|:---------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| HypersensitivityIntolerance                                                     | EHDSAllergyIntolerance                             |            |                        |             | 0..*          |
|                                                                                 | EHDSAllergyIntolerance.header                      |            | Base                   |             | 1..1          |
|                                                                                 | EHDSAllergyIntolerance.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                                                 | EHDSAllergyIntolerance.header.identifier           |            | Identifier             |             | 0..*          |
|                                                                                 | EHDSAllergyIntolerance.header.authorship           |            | Base                   |             | 1..*          |
|                                                                                 | EHDSAllergyIntolerance.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                                                 | EHDSAllergyIntolerance.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                                                 | EHDSAllergyIntolerance.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                                                 | EHDSAllergyIntolerance.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.header.language             |            | CodeableConcept        |             | 0..1          |
| HypersensitivityIntolerance.Agent.Substance                                     | EHDSAllergyIntolerance.agentOrAllergen             | CD         | CodeableConcept        | (0..1)      | 1..1          |
|                                                                                 | EHDSAllergyIntolerance.typeOfPropensity            |            | CodeableConcept        |             | 0..1          |
| HypersensitivityIntolerance.Comment                                             | EHDSAllergyIntolerance.description                 | ST         | string                 | 0..1        | 0..1          |
| HypersensitivityIntolerance.ExpectedRiskUponExposure                            | EHDSAllergyIntolerance.criticality                 | CD         | CodeableConcept        | 0..1        | 0..1          |
| HypersensitivityIntolerance.DiagnosisStatus                                     | EHDSAllergyIntolerance.certainty                   | CD         | CodeableConcept        | 1           | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.status                      |            | CodeableConcept        |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.onsetDate                   |            | dateTime               |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.endDate                     |            | dateTime               |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.reaction                    |            | Base                   |             | 0..*          |
|                                                                                 | EHDSAllergyIntolerance.reaction.manifestation      |            | CodeableConcept        |             | 0..*          |
|                                                                                 | EHDSAllergyIntolerance.reaction.date               |            | dateTime               |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.reaction.severity           |            | CodeableConcept        |             | 0..1          |
|                                                                                 | EHDSAllergyIntolerance.reaction.onsetDate          |            | dateTime               |             | 0..1          |
| HypersensitivityIntolerance.Condition                                           |                                                    |            |                        | 0..1        |               |
| HypersensitivityIntolerance.WayOfDetermination                                  |                                                    | CD         |                        | 1           |               |
| HypersensitivityIntolerance.Category                                            |                                                    | CD         |                        | 1..*        |               |
| HypersensitivityIntolerance.DiagnosisNameData                                   |                                                    |            |                        | 1           |               |
| HypersensitivityIntolerance.DiagnosisNameData.DiagnosisName                     |                                                    | CD         |                        | 1           |               |
| HypersensitivityIntolerance.DiagnosisNameData.FurtherSpecificationDiagnosisName |                                                    | ST         |                        | 0..1        |               |
| HypersensitivityIntolerance.DiagnoisDate                                        |                                                    | TS         |                        | 1           |               |
| HypersensitivityIntolerance.Diagnostician::HealthProfessional                   |                                                    |            |                        | 1           |               |
| HypersensitivityIntolerance.Agent                                               |                                                    |            |                        | 1           |               |
| HypersensitivityIntolerance.Agent.Radiation                                     |                                                    | CD         |                        | (0..1)      |               |



## EHDSAllergyIntolerance

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance |
| zib | HypersensitivityIntolerance |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for allergy/intolerance |
| definition_zib | This is a reference to the rootconcept of information model HypersensitivityIntolerance. |
| definitioncode_zib | SNOMED CT: 420134006 Propensity to adverse reaction |
| id_xtehr | EHDSAllergyIntolerance |
| id_zib | NL-CM:8.6.1 |
| name_zib | HypersensitivityIntolerance |
| path_xtehr | EHDSAllergyIntolerance |
| path_zib | HypersensitivityIntolerance |
| short_xtehr | Allergy intolerance model |
| stereotype_zib | rootconcept |

### Comments





## EHDSAllergyIntolerance.agentOrAllergen

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.agentOrAllergen |
| zib | HypersensitivityIntolerance.Agent.Substance |
| alias_zib | NL: Stof |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.24 **eHDSIActiveIngredient** (ATC, used in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.61 eHDSISubstance (EMA SMS, used in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.19 eHDSIAllergenNoDrug (SCT, used in MH@EU); ICD-11 Allergens'} |
| card._xtehr | 1..1 |
| card._zib | (0..1) |
| definition_xtehr | A specific allergen or other agent/substance (drug, food, chemical agent, etc.) to which the patient has an adverse reaction propensity. |
| definition_zib | The substance or group of substances that trigger a reaction in the patient upon exposure. |
| definitioncode_zib | SNOMED CT: 105590001 Substance |
| id_xtehr | EHDSAllergyIntolerance.agentOrAllergen |
| id_zib | NL-CM:8.6.15 |
| name_zib | Substance |
| path_xtehr | EHDSAllergyIntolerance.agentOrAllergen |
| path_zib | HypersensitivityIntolerance.Agent.Substance |
| short_xtehr | A specific allergen or other agent/substance (drug, food, chemical agent, etc.) to which the patient has an adverse reaction propensity. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Binding valuesets mismatch. The binding in the zib is required.
Cardinality mismatch because in the zib, either Radiation or Substance must be chosen.

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
No match in the zib. The type intolerance may be pre-coordinated in the .DiagnosisName.



## EHDSAllergyIntolerance.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.description |
| zib | HypersensitivityIntolerance.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual description of the allergy or intolerance |
| definition_zib | Textual explanation of the hypersensitivity or intolerance which cannot be entered in any of the other fields. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSAllergyIntolerance.description |
| id_zib | NL-CM:8.6.12 |
| name_zib | Comment |
| path_xtehr | EHDSAllergyIntolerance.description |
| path_zib | HypersensitivityIntolerance.Comment |
| short_xtehr | Textual description of the allergy or intolerance |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Not an exact match. The zib has a more restricted use of the concept by definition.


## EHDSAllergyIntolerance.criticality

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.criticality |
| zib | HypersensitivityIntolerance.ExpectedRiskUponExposure |
| alias_zib | NL: VerwachtRisicoBijBlootstelling |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.57 eHDSICriticality (HL7, used in MH@EU); http://hl7.org/fhir/ValueSet/allergy-intolerance-criticality (HL7, required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Estimate of the potential clinical harm, or seriousness, of a reaction to an identified substance. |
| definition_zib | The healthcare professional's assessment of the expected severity of the reaction upon future exposure to the substance, group of substances or environmental factor to which the patient is hypersensitive or intolerant. |
| definitioncode_zib | SNOMED CT: 340271000146105 Expected severity of reaction |
| id_xtehr | EHDSAllergyIntolerance.criticality |
| id_zib | NL-CM:8.6.11 |
| name_zib | ExpectedRiskUponExposure |
| path_xtehr | EHDSAllergyIntolerance.criticality |
| path_zib | HypersensitivityIntolerance.ExpectedRiskUponExposure |
| short_xtehr | Estimate of the potential clinical harm, or seriousness, of a reaction to an identified substance. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Match. The valueset in the Xt-EHRT model has "unable to assess" which the zib has not as per design principles. 



## EHDSAllergyIntolerance.certainty

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.certainty |
| zib | HypersensitivityIntolerance.DiagnosisStatus |
| alias_zib | NL: DiagnoseStatus |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.58 eHDSIAllergyCertainty (HL7, used in MH@EU) ; http://hl7.org/fhir/ValueSet/allergyintolerance-verification (HL7, required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Assertion about the certainty associated with a propensity, or potential risk, of a reaction to the identified substance. Diagnostic and /or clinical evidence of condition |
| definition_zib | Indicates the status of the diagnostic process. |
| id_xtehr | EHDSAllergyIntolerance.certainty |
| id_zib | NL-CM:8.6.3 |
| name_zib | DiagnosisStatus |
| path_xtehr | EHDSAllergyIntolerance.certainty |
| path_zib | HypersensitivityIntolerance.DiagnosisStatus |
| short_xtehr | Assertion about the certainty associated with a propensity, or potential risk, of a reaction to the identified substance. Diagnostic and /or clinical evidence of condition |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Cardinality mismatch, as the zib has conceptual cardinality.
https://hl7.org/fhir/valueset-allergyintolerance-verification.html has a distinction between "unconfirmed" and its child "presumed" which the zib has not. It has a value "refuted" which is not in the zib value set because there is a separate zib "Exclusion". It has a value "entered in error" which is not in the zib value set as per design principles.  





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
This concept has a poor match to .Course in the zib Condition, to which the zib HypersensitivityIntolerance has a reference. In https://hl7.org/fhir/valueset-allergyintolerance-clinical.html we have "active", "inactive" and its child "resolved". Only "resolved" has an equivalent "No longer present" in the zib. The same incompatibility issues apply to the EHDSCondition.problemStatus element. 



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
There's a definition / name mismatch in the Xt-EHR model here.
If the onset date is meant, this concept matches Condition.PeriodPresent.TimeInterval.StartEvent.
If the date of the diagnosis is meant, this concept matches HypersensitityIntolerance.DianoisDate (typo in zib!).


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
This concept matches Condition.PeriodPresent.TimeInterval.EndEvent. 



## EHDSAllergyIntolerance.reaction

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Adverse Reaction Events linked to exposure to substance. |
| id_xtehr | EHDSAllergyIntolerance.reaction |
| path_xtehr | EHDSAllergyIntolerance.reaction |
| short_xtehr | Adverse Reaction Events linked to exposure to substance. |
| type_xtehr | Base |

### Comments
This concept matches the root concept of the zib Reaction.



## EHDSAllergyIntolerance.reaction.manifestation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.manifestation |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.5 eHDSIIllnessandDisorder (ICD-10, alternative in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.11 eHDSIReactionAllergy (SCT, alternative in MH@EU); ICD-11 MMS'} |
| card._xtehr | 0..* |
| definition_xtehr | Description of the clinical manifestation of the allergic reaction. Example: anaphylactic shock, angioedema. (the clinical manifestation also gives information about the severity of the observed reaction). |
| id_xtehr | EHDSAllergyIntolerance.reaction.manifestation |
| path_xtehr | EHDSAllergyIntolerance.reaction.manifestation |
| short_xtehr | Description of the clinical manifestation of the allergic reaction. Example: anaphylactic shock, angioedema. (the clinical manifestation also gives information about the severity of the observed reaction). |
| type_xtehr | CodeableConcept |

### Comments
As the cardinality of this concept is 0..*, this concept can only be mapped to Symptom.SymptomName. The binding in the zib to SNOMED findings is required.
However,the examples given in the definition are more applicable to the name of the reaction itself, which would map to Reaction.DiagnosisNameData.DiagnosisName. It appears that the name of the reaction itself (cardinality 0..1) is missing. 


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
This concept matches Symptom.SymptomPeriod::TimeInterval.StartEvent.



## EHDSAllergyIntolerance.reaction.severity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.severity |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.13 eHDSISeverity (SCT, used in MH@EU); http://hl7.org/fhir/ValueSet/reaction-event-severity (HL7, Required in HL7 FHIR)'} |
| card._xtehr | 0..1 |
| definition_xtehr | Severity of the clinical manifestation of the allergic reaction. |
| id_xtehr | EHDSAllergyIntolerance.reaction.severity |
| path_xtehr | EHDSAllergyIntolerance.reaction.severity |
| short_xtehr | Severity of the clinical manifestation of the allergic reaction. |
| type_xtehr | CodeableConcept |

### Comments
This concept matches Condition.Severity (not Symptom.SymptomSeverity, as that would be the severity of the _manifestation_ of the reaction). The preferred binding is a 3 point HL7 scale. The zib has a 3 point SNOMED scale with a required binding. The scales match exactly.    



## EHDSAllergyIntolerance.reaction.onsetDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAllergyIntolerance.reaction.onsetDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date of the observation of the reaction |
| id_xtehr | EHDSAllergyIntolerance.reaction.onsetDate |
| path_xtehr | EHDSAllergyIntolerance.reaction.onsetDate |
| short_xtehr | Date of the observation of the reaction |
| type_xtehr | dateTime |

### Comments
This concept matches Condition.PeriodPresent::TimeInterval.StartEvent.StartDateTime.



## zib: HypersensitivityIntolerance.Condition

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.Condition |
| alias_zib | NL: AandoeningOfGesteldheid |
| card._zib | 0..1 |
| definition_zib | The condition of which the hypersensitivity or intolerance is the interpretation. |
| id_zib | NL-CM:8.6.2 |
| name_zib | Condition |
| path_zib | HypersensitivityIntolerance.Condition |
| stereotype_zib | data,reference |

### Comments



## zib: HypersensitivityIntolerance.WayOfDetermination

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.WayOfDetermination |
| alias_zib | NL: WijzeVanVastellen |
| card._zib | 1 |
| definition_zib | The way in which the hypersensitivity or intlerance is determined. |
| definitioncode_zib | SNOMED CT: 418775008 Finding method |
| id_zib | NL-CM:8.6.4 |
| name_zib | WayOfDetermination |
| path_zib | HypersensitivityIntolerance.WayOfDetermination |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: HypersensitivityIntolerance.Category

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.Category |
| alias_zib | NL: Categorie |
| card._zib | 1..* |
| definition_zib | Identifies the category of the agent to which the hypersensitivity or intolerance relates, such as medicines and nutritional substances. |
| id_zib | NL-CM:8.6.5 |
| name_zib | Category |
| path_zib | HypersensitivityIntolerance.Category |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: HypersensitivityIntolerance.DiagnosisNameData

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.DiagnosisNameData |
| alias_zib | NL: DiagnoseNaamGegevens |
| card._zib | 1 |
| definition_zib | Container of the DiagnosisNameData concept. This container contains all data elements of the DiagnosisNameData concept.<br>Represents the hypersensitivity as interpretation of the condition. |
| id_zib | NL-CM:8.6.6 |
| name_zib | DiagnosisNameData |
| path_zib | HypersensitivityIntolerance.DiagnosisNameData |
| stereotype_zib | container |

### Comments



## zib: HypersensitivityIntolerance.DiagnosisNameData.DiagnosisName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.DiagnosisNameData.DiagnosisName |
| alias_zib | NL: DiagnoseNaam |
| card._zib | 1 |
| definition_zib | The term with associated code that the care professional selects from the used code list to specify the diagnosis. |
| definitioncode_zib | SNOMED CT: 439401001 Diagnosis |
| id_zib | NL-CM:8.6.7 |
| name_zib | DiagnosisName |
| path_zib | HypersensitivityIntolerance.DiagnosisNameData.DiagnosisName |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: HypersensitivityIntolerance.DiagnosisNameData.FurtherSpecificationDiagnosisName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.DiagnosisNameData.FurtherSpecificationDiagnosisName |
| alias_zib | NL: NadereSpecificatieDiagnoseNaam |
| card._zib | 0..1 |
| definition_zib | A more detailed description of the name of the hypersensitivity or intolerance in free text, when this detail is not available in the used code list. |
| id_zib | NL-CM:8.6.8 |
| name_zib | FurtherSpecificationDiagnosisName |
| path_zib | HypersensitivityIntolerance.DiagnosisNameData.FurtherSpecificationDiagnosisName |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: HypersensitivityIntolerance.DiagnoisDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.DiagnoisDate |
| alias_zib | NL: DiagnoseDatum |
| card._zib | 1 |
| definition_zib | Date (and time) at which the care professional came to the diagnosis. |
| definitioncode_zib | SNOMED CT: 432213005 Date of diagnosis |
| id_zib | NL-CM:8.6.9 |
| name_zib | DiagnoisDate |
| path_zib | HypersensitivityIntolerance.DiagnoisDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: HypersensitivityIntolerance.Diagnostician::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.Diagnostician::HealthProfessional |
| alias_zib | NL: DiagnoseSteller::Zorgverlener |
| card._zib | 1 |
| definition_zib | The care professional that acquired the diagnostic insight regarding the hypersensitivity or intolerance. This can be a different individual than the person who recorded the diagnostic insight. |
| definitioncode_zib | PRF performer |
| id_zib | NL-CM:8.6.10 |
| name_zib | Diagnostician::HealthProfessional |
| path_zib | HypersensitivityIntolerance.Diagnostician::HealthProfessional |
| stereotype_zib | context,reference |

### Comments



## zib: HypersensitivityIntolerance.Agent

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.Agent |
| alias_zib | NL: Agens |
| card._zib | 1 |
| definition_zib | Container of the Agent concept. This container contains all data elements of the Agent concept. |
| definitioncode_zib | SNOMED CT: 246075003 Causative agent |
| id_zib | NL-CM:8.6.13 |
| name_zib | Agent |
| path_zib | HypersensitivityIntolerance.Agent |
| stereotype_zib | container |

### Comments



## zib: HypersensitivityIntolerance.Agent.Radiation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HypersensitivityIntolerance.Agent.Radiation |
| alias_zib | NL: Straling |
| card._zib | (0..1) |
| definition_zib | Radiation as trigger for an adverse reaction. |
| definitioncode_zib | SNOMED CT: 82107009 Radiation |
| id_zib | NL-CM:8.6.14 |
| name_zib | Radiation |
| path_zib | HypersensitivityIntolerance.Agent.Radiation |
| stereotype_zib | data |
| type_zib | CD |

### Comments

