# AlertFlag

| zib                                     | xtehr                    | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:----------------------------------------|:-------------------------|:-----------|:----------------|:------------|:--------------|
| Alert                                   | EHDSAlertFlag            |            |                 |             | 0..*          |
| Alert.DecisionMaker::HealthProfessional | EHDSAlertFlag.author     |            | Reference       | 1           | 0..1          |
| Alert.AlertName                         | EHDSAlertFlag.code       | CD         | CodeableConcept | (0..1)      | 1..1          |
|                                         | EHDSAlertFlag.encounter  |            | Reference       |             | 0..1          |
|                                         | EHDSAlertFlag.identifier |            | Identifier      |             | 0..*          |
|                                         | EHDSAlertFlag.patient    |            | Reference       |             | 1..1          |
| Alert.EndDateTime                       | EHDSAlertFlag.period     | TS         | Period          | 0..1        | 0..1          |
| Alert.StartDateTime                     | EHDSAlertFlag.period     | TS         | Period          | 0..1        | 0..1          |
|                                         | EHDSAlertFlag.priority   |            | CodeableConcept |             | 0..*          |
|                                         | EHDSAlertFlag.status     |            | CodeableConcept |             | 0..1          |
|                                         | EHDSAlertFlag.text       |            | string          |             | 0..1          |
| Alert.AlertType                         |                          | CD         |                 | 0..1        |               |
| Alert.Comment                           |                          | ST         |                 | 0..1        |               |
| Alert.Diagnosis                         |                          |            |                 | (0..1)      |               |
| Alert.HypersensitivityIntolerance       |                          |            |                 | (0..1)      |               |



## EHDSAlertFlag

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag |
| zib | Alert |
| alias_zib | NL: Alert |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.22 - EHDS refined base model for Alert flag |
| definition_zib | Root concept of the Alert information model. This root concept contains all data elements of the Alert information model. |
| definitioncode_zib | SNOMED CT: 37341000000109 Alert note |
| id_xtehr | EHDSAlertFlag |
| id_zib | NL-CM:8.3.1 |
| name_zib | Alert |
| path_xtehr | EHDSAlertFlag |
| path_zib | Alert |
| short_xtehr | Alert flag model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSAlertFlag.author

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.author |
| zib | Alert.DecisionMaker::HealthProfessional |
| alias_zib | NL: Vaststeller::Zorgverlener |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The person, organization or device that created the flag. |
| definition_zib | The health professional who is responsible for setting the alert. |
| definitioncode_zib | PRF performer |
| id_xtehr | EHDSAlertFlag.author |
| id_zib | NL-CM:8.3.9 |
| name_zib | DecisionMaker::HealthProfessional |
| path_xtehr | EHDSAlertFlag.author |
| path_zib | Alert.DecisionMaker::HealthProfessional |
| short_xtehr | C.22.9 - Author |
| stereotype_zib | context,reference |
| type_xtehr | Reference |
| type_zib |  |

### Comments



## EHDSAlertFlag.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.code |
| zib | Alert.AlertName |
| alias_zib | NL: AlertNaam |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 1..1 |
| card._zib | (0..1) |
| definition_xtehr | A coded or textual representation of the flag. |
| definition_zib | A warning, other than a condition or problem. For example, a patient can be given an ‘Aggressive patient' alert. 
The warning can be entered in code (there are codes for frequently used alerts), but seeing the dynamic nature of the warnings cf. SARS and Ebola, these alerts will often be entered as free text. |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.code |
| id_zib | NL-CM:8.3.4 |
| name_zib | AlertName |
| path_xtehr | EHDSAlertFlag.code |
| path_zib | Alert.AlertName |
| short_xtehr | C.22.5 - Code |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSAlertFlag.encounter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.encounter |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | This alert is only relevant during the encounter. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.encounter |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAlertFlag.encounter |
| path_zib |  |
| short_xtehr | C.22.8 - Encounter |
| stereotype_zib |  |
| type_xtehr | Reference |
| type_zib |  |

### Comments



## EHDSAlertFlag.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.identifier |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Flag identifier (Business identifiers assigned to this flag). |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAlertFlag.identifier |
| path_zib |  |
| short_xtehr | C.22.1 - Identifier |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSAlertFlag.patient

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.patient |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Who/What this flag is a record of |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.patient |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAlertFlag.patient |
| path_zib |  |
| short_xtehr | C.22.6 - Subject |
| stereotype_zib |  |
| type_xtehr | Reference |
| type_zib |  |

### Comments



## EHDSAlertFlag.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.period |
| zib | Alert.EndDateTime |
| alias_zib | NL: EindDatumTijd |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period when flag is active. The period of time from the activation of the flag to inactivation of the flag. If the flag is active, the end of the period should be unspecified. |
| definition_zib | The date and time at which the described condition was retracted as a warning.  
This can be an exact date and time, or a rough indication of the date (such as only the year, or the month and the year). |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.period |
| id_zib | NL-CM:8.3.8 |
| name_zib | EndDateTime |
| path_xtehr | EHDSAlertFlag.period |
| path_zib | Alert.EndDateTime |
| short_xtehr | C.22.7 - Period |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments



## EHDSAlertFlag.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.period |
| zib | Alert.StartDateTime |
| alias_zib | NL: BeginDatumTijd |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period when flag is active. The period of time from the activation of the flag to inactivation of the flag. If the flag is active, the end of the period should be unspecified. |
| definition_zib | The date and time at which the described condition was entered as a warning.  
This can be an exact date and time, or a rough indication of the date (such as only the year, or the month and the year). |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.period |
| id_zib | NL-CM:8.3.5 |
| name_zib | StartDateTime |
| path_xtehr | EHDSAlertFlag.period |
| path_zib | Alert.StartDateTime |
| short_xtehr | C.22.7 - Period |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments



## EHDSAlertFlag.priority

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.priority |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:Flag-priority-code'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | A code that identifies the priority of the alert. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.priority |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAlertFlag.priority |
| path_zib |  |
| short_xtehr | C.22.3 - Priority |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSAlertFlag.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.status |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:Flag-status'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Current status of the flag, Indicates whether this flag is active and needs to be displayed to a user, or whether it is no longer needed or was entered in error. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.status |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAlertFlag.status |
| path_zib |  |
| short_xtehr | C.22.4 - Status |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSAlertFlag.text

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlertFlag.text |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | A human-readable narrative that contains a summary of the flag and can be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it \"clinically safe\" for a human to just read the narrative.
Example 1: intolerance to aspirin due to gastrointestinal bleeding.
Example 2: intolerance to captopril because of cough (the patient is not allergic but can't tolerate it because of persistent cough)
Example 3: the patient has a rare disease that requires special treatment
Example 4: Airway Alert / Difficult Intubation
Example 5: Diagnoses such as malignant hyperthermia, porphyria, and bleeding disorders; special treatments like anticoagulants or immunosuppressants; implanted devices.
Example 6: transplanted organs illustrate other information that has to be taken into account in a healthcare contact.
Example 7: participation in a clinical trial that has to be taken into account in a healthcare contact. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAlertFlag.text |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAlertFlag.text |
| path_zib |  |
| short_xtehr | C.22.2 - Text |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## zib: Alert.AlertType

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.AlertType |
| alias_zib | NL: AlertType |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Indicates the type of alert, meaning a rough description of the cause or origin of the warning. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:8.3.6 |
| name_zib | AlertType |
| path_xtehr |  |
| path_zib | Alert.AlertType |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: Alert.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.Comment |
| alias_zib | NL: Toelichting |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Explanatory comments to the alert that can not be expressed in any of the other elements. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr |  |
| id_zib | NL-CM:8.3.7 |
| name_zib | Comment |
| path_xtehr |  |
| path_zib | Alert.Comment |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments



## zib: Alert.Diagnosis

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.Diagnosis |
| alias_zib | NL: Diagnose |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | A warning about a particular diagnosis, because it may pose a risk to the patient with certain treatments. For example, 'Pacemaker' can be included as an alert. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:8.3.10 |
| name_zib | Diagnosis |
| path_xtehr |  |
| path_zib | Alert.Diagnosis |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: Alert.HypersensitivityIntolerance

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.HypersensitivityIntolerance |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | (0..1) |
| definition_xtehr |  |
| definition_zib | A warning for a specific hypersensitivity or intolerance, because this can pose a risk to the patient with certain treatments. For example, an alert can be given such as 'Hypersensitivity to UV light'. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:8.3.11 |
| name_zib | HypersensitivityIntolerance |
| path_xtehr |  |
| path_zib | Alert.HypersensitivityIntolerance |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments

