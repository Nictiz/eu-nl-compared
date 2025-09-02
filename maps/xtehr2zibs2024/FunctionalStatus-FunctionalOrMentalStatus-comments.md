# FunctionalStatus 

## Overall comments
The main differences are:
+ EHDSFunctionalStatus.relatedConditions is present in the Xt-EHR model, not in the zib. Note that this concept is present in the main branch of the Xt-EHR logical models, but not in the 6.2 stakeholder consultation branch. Why isn't a reference to EHDSCondition used?
+ A reference to a medical device is present in the zib but not in the logical model.  
+ The zib scope definitions mentions functional and mental status explicitly (without making clear what the diference is). The Xt-EHR model does not.   


| zib                                                   | xtehr                                                                           | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:------------------------------------------------------|:--------------------------------------------------------------------------------|:-----------|:----------------|:------------|:--------------|
| FunctionalOrMentalStatus                              | EHDSFunctionalStatus                                                            |            |                 |             | 0..*          |
| FunctionalOrMentalStatus.Comment                      | EHDSFunctionalStatus.description                                                | ST         | string          | 0..1        | 0..1          |
|                                                       | EHDSFunctionalStatus.functionalStatusAssessment                                 |            | Base            |             | 0..*          |
| FunctionalOrMentalStatus.StatusName                   | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentCode        | CD         | CodeableConcept | 1           | 0..1          |
| FunctionalOrMentalStatus.StatusDate                   | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDateTime    | TS         | dateTime        | 0..1        | 0..1          |
|                                                       | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDescription |            | string          |             | 0..1          |
| FunctionalOrMentalStatus.StatusValue                  | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentResult[x]   | CO         | string          | 0..1        | 0..1          |
|                                                       | EHDSFunctionalStatus.presentedForm                                              |            | EHDSAttachment  |             | 0..*          |
|                                                       | EHDSFunctionalStatus.relatedConditions                                          |            | Base            |             | 0..*          |
|                                                       | EHDSFunctionalStatus.relatedConditions.condition                                |            | CodeableConcept |             | 0..1          |
|                                                       | EHDSFunctionalStatus.relatedConditions.conditionText                            |            | string          |             | 0..1          |
|                                                       | EHDSFunctionalStatus.relatedConditions.onsetDate                                |            | dateTime        |             | 0..1          |
|                                                       |                                                                                 |            |                 | 0..*        |               |
| FunctionalOrMentalStatus.MedicalDevice::MedicalDevice |                                                                                 |            |                 |             |               |



## EHDSFunctionalStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus |
| zib | FunctionalOrMentalStatus |
| alias_zib | NL: FunctioneleOfMentaleStatus |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Functional status |
| definition_zib | Root concept of FunctionalOrMentalStatus. This concept contains all data elements of the FunctionalOrMentalStatus information model. |
| id_xtehr | EHDSFunctionalStatus |
| id_zib | NL-CM:4.26.1 |
| name_zib | FunctionalOrMentalStatus |
| path_xtehr | EHDSFunctionalStatus |
| path_zib | FunctionalOrMentalStatus |
| short_xtehr | Functional status |
| stereotype_zib | rootconcept |

### Comments



## EHDSFunctionalStatus.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.description |
| zib | FunctionalOrMentalStatus.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Narrative description of the need for the patient to be continuously assessed by third parties; functional status may influence decisions about how to plan and administer treatments. |
| definition_zib | Explanatory comments as a description of the functional or mental status. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSFunctionalStatus.description |
| id_zib | NL-CM:4.26.4 |
| name_zib | Comment |
| path_xtehr | EHDSFunctionalStatus.description |
| path_zib | FunctionalOrMentalStatus.Comment |
| short_xtehr | Narrative description of the functional status |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
There is no equivalent in the zib as per zib design principles.



## EHDSFunctionalStatus.functionalStatusAssessment

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.functionalStatusAssessment |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Functional status assessment of the patient according to a specific assessment scheme. |
| id_xtehr | EHDSFunctionalStatus.functionalStatusAssessment |
| path_xtehr | EHDSFunctionalStatus.functionalStatusAssessment |
| short_xtehr | Functional assessment of the patient |
| type_xtehr | Base |

### Comments
This container is absent in the zib.


## EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentCode

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentCode |
| zib | FunctionalOrMentalStatus.StatusName |
| alias_zib | NL: StatusNaam |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICF, SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Standardized code corresponding to the Functional assessment |
| definition_zib | Coded description of the functional or mental status or limitation. <br>Code systems used include: <br>-  SNOMED CT<br>-  ICF (International Classification of Functioning, Disability and Health)  |
| id_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentCode |
| id_zib | NL-CM:4.26.2 |
| name_zib | StatusName |
| path_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentCode |
| path_zib | FunctionalOrMentalStatus.StatusName |
| short_xtehr | Standardized code corresponding to the Functional assessment |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Exact match including preferred bindings. 



## EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDateTime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDateTime |
| zib | FunctionalOrMentalStatus.StatusDate |
| alias_zib | NL: StatusDatum |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the functional assessment |
| definition_zib | Date on which the status is or was determined. A �vague� date, such as only the year, is permitted. |
| id_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDateTime |
| id_zib | NL-CM:4.26.6 |
| name_zib | StatusDate |
| path_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDateTime |
| path_zib | FunctionalOrMentalStatus.StatusDate |
| short_xtehr | Date and time of the functional assessment |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Exact match.



## EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDescription

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDescription |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Description of the functional assessment |
| id_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDescription |
| path_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentDescription |
| short_xtehr | Description of the functional assessment |
| type_xtehr | string |

### Comments
In the zib there is no concept for the textual description of the coded assessment, as per zib design principles.

## EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentResult[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentResult[x] |
| zib | FunctionalOrMentalStatus.StatusValue |
| alias_zib | NL: StatusWaarde |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICF, SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Functional assessment result value |
| definition_zib | The extent to which the patient is limited by the functional or mental condition. <br>If both the status name and the status value are recorded in code, then both values must come from the same code system.  <br>If the patient uses a medical device, the evaluation of the extent of the limitation will take place without this aid.<br>The answer codes must be selected from the subselection of the code system corresponding with the request in accordance with the rules applicable to that system. |
| id_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentResult[x] |
| id_zib | NL-CM:4.26.3 |
| name_zib | StatusValue |
| path_xtehr | EHDSFunctionalStatus.functionalStatusAssessment.functionalAssessmentResult[x] |
| path_zib | FunctionalOrMentalStatus.StatusValue |
| short_xtehr | Functional assessment result value |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | CO |

### Comments
These concepts match, except for the datatype. The datatype in the zib is restricted to codeable concept with bindings SNOMED CT and ICF. The data types in the Xt-EHR model can be string, Quantity or CodeableConcept with bindings SNOMED CT and ICF.



## EHDSFunctionalStatus.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSFunctionalStatus.presentedForm |
| path_xtehr | EHDSFunctionalStatus.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments
This concept is absent in the zib as per zib design principles.



## EHDSFunctionalStatus.relatedConditions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.relatedConditions |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Conditions related to the functional status |
| id_xtehr | EHDSFunctionalStatus.relatedConditions |
| path_xtehr | EHDSFunctionalStatus.relatedConditions |
| short_xtehr | Conditions related to the functional status |
| type_xtehr | Base |

### Comments



## EHDSFunctionalStatus.relatedConditions.condition

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.relatedConditions.condition |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Condition related to the functional status |
| id_xtehr | EHDSFunctionalStatus.relatedConditions.condition |
| path_xtehr | EHDSFunctionalStatus.relatedConditions.condition |
| short_xtehr | Condition related to the functional status |
| type_xtehr | CodeableConcept |

### Comments



## EHDSFunctionalStatus.relatedConditions.conditionText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.relatedConditions.conditionText |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Textual description of the condition |
| id_xtehr | EHDSFunctionalStatus.relatedConditions.conditionText |
| path_xtehr | EHDSFunctionalStatus.relatedConditions.conditionText |
| short_xtehr | Textual description of the condition |
| type_xtehr | string |

### Comments



## EHDSFunctionalStatus.relatedConditions.onsetDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFunctionalStatus.relatedConditions.onsetDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Onset date of a condition |
| id_xtehr | EHDSFunctionalStatus.relatedConditions.onsetDate |
| path_xtehr | EHDSFunctionalStatus.relatedConditions.onsetDate |
| short_xtehr | Onset date of a condition |
| type_xtehr | dateTime |

### Comments



## zib: FunctionalOrMentalStatus.MedicalDevice::MedicalDevice

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FunctionalOrMentalStatus.MedicalDevice::MedicalDevice |
| alias_zib | NL: Hulpmiddel::MedischHulpmiddel |
| card._zib | 0..* |
| definition_zib | Medical aid the patient has or will receive to reduce the impact of the disability or disorder. |
| id_zib | NL-CM:4.26.5 |
| name_zib | MedicalDevice:MedicalDevice::MedicalDevice::MedicalDevice::MedicalDevice::MedicalDevice |
| path_zib | FunctionalOrMentalStatus.MedicalDevice:::MedicalDevice |
| stereotype_zib | data,reference |

### Comments


