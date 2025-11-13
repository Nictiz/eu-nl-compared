# Alert
## Duiding door Jacob en Astrid 13 november 2025
+ EHDSIssue: add .alertSetter, definition: the health professional who is responsible for setting the alert, type: EHDSHealthProfessional. This is not the same rol as .header.author: the .author is the person responsible for registration in the health record, while the setter of the alert can be a professional in another organisation.
+ EHDSIssue: remove .status. It seems to overlap with .header.status and it is redundant because EHDSAlert.period indicates when the alert is active.
+ zib issue: add equivalent of EHDSAlert.priority

## General discussion
Missing in the EHDS model: 
+ Alert.DecisionMaker = asserter of the Alert (we assume that EHDSAlert.header.author is another role)
+ Alert.HypersensitivityIntolerance and Alert.Diagnosis (references) - only their names can be mapped to EHDSAlert.code
+ Alert.AlertType (valueset: Condition, Potential contraindication for medication, Alert). The zib has binding MedicationContraIndicationNameCodelist (for contra indications), and AlertNameCodelist (gereral codelist, mostly useful for hospital admissions). It is not clear in which EHDS model contraindications are represented.

Missing in the zib:
+ priority (value set: no alarm, low, medium, high)
+ status (valueset: active, inactive, entered in error): what is the difference with .header.status?




| zib                                     | xtehr                                 | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:----------------------------------------|:--------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Alert                                   | EHDSAlert                             |            |                        |             | 0..*          |
|                                         | EHDSAlert.header                      |            | Base                   |             | 1..1          |
|                                         | EHDSAlert.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                         | EHDSAlert.header.identifier           |            | Identifier             |             | 0..*          |
|                                         | EHDSAlert.header.authorship           |            | Base                   |             | 1..*          |
|                                         | EHDSAlert.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                         | EHDSAlert.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                         | EHDSAlert.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                         | EHDSAlert.header.status               |            | CodeableConcept        |             | 1..1          |
|                                         | EHDSAlert.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                         | EHDSAlert.header.language             |            | CodeableConcept        |             | 0..1          |
| Alert.Comment                           | EHDSAlert.text                        | ST         | string                 | 0..1        | 0..1          |
|                                         | EHDSAlert.priority                    |            | CodeableConcept        |             | 0..*          |
|                                         | EHDSAlert.status                      |            | CodeableConcept        |             | 0..1          |
| Alert.AlertName                         | EHDSAlert.code                        | CD         | CodeableConcept        | (0..1)      | 1..1          |
| Alert.StartDateTime; Alert.EndDateTime  | EHDSAlert.period                      | TS         | Period                 | 0..1        | 0..1          |
| Alert.AlertType                         |                                       | CD         |                        | 0..1        |               |
| Alert.HypersensitivityIntolerance       |                                       |            |                        | (0..1)      |               |
| Alert.Diagnosis                         |                                       |            |                        | (0..1)      |               |
| Alert.DecisionMaker::HealthProfessional |                                       |            |                        | 1           |               |



## EHDSAlert

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert |
| zib | Alert |
| alias_zib | NL: Alert |
| card._xtehr | 0..* |
| definition_xtehr | Alert flag |
| definition_zib | Root concept of the Alert information model. This root concept contains all data elements of the Alert information model. |
| definitioncode_zib | SNOMED CT: 37341000000109 Alert note |
| id_xtehr | EHDSAlert |
| id_zib | NL-CM:8.3.1 |
| name_zib | Alert |
| path_xtehr | EHDSAlert |
| path_zib | Alert |
| short_xtehr | Alert model |
| stereotype_zib | rootconcept |

### Comments



## EHDSAlert.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSAlert.header |
| path_xtehr | EHDSAlert.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSAlert.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSAlert.header.subject |
| path_xtehr | EHDSAlert.header.subject |
| short_xtehr | Patient/subject information |
| type_xtehr | EHDSPatient |

### Comments



## EHDSAlert.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSAlert.header.identifier |
| path_xtehr | EHDSAlert.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSAlert.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSAlert.header.authorship |
| path_xtehr | EHDSAlert.header.authorship |
| short_xtehr | Resource authoring details |
| type_xtehr | Base |

### Comments



## EHDSAlert.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSAlert.header.authorship.author[x] |
| path_xtehr | EHDSAlert.header.authorship.author[x] |
| short_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSAlert.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of authoring/issuing |
| id_xtehr | EHDSAlert.header.authorship.datetime |
| path_xtehr | EHDSAlert.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSAlert.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| id_xtehr | EHDSAlert.header.lastUpdate |
| path_xtehr | EHDSAlert.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| type_xtehr | dateTime |

### Comments



## EHDSAlert.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource or document |
| id_xtehr | EHDSAlert.header.status |
| path_xtehr | EHDSAlert.header.status |
| short_xtehr | Status of the resource or document |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAlert.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSAlert.header.statusReason[x] |
| path_xtehr | EHDSAlert.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAlert.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSAlert.header.language |
| path_xtehr | EHDSAlert.header.language |
| short_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAlert.text

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.text |
| zib | Alert.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | A human-readable narrative that contains a summary of the flag and can be used to represent the content of the resource to a human. The narrative need not encode all the structured data, but is required to contain sufficient detail to make it \"clinically safe\" for a human to just read the narrative.<br>Example 1: intolerance to aspirin due to gastrointestinal bleeding.<br>Example 2: intolerance to captopril because of cough (the patient is not allergic but can't tolerate it because of persistent cough)<br>Example 3: the patient has a rare disease that requires special treatment<br>Example 4: Airway Alert / Difficult Intubation<br>Example 5: Diagnoses such as malignant hyperthermia, porphyria, and bleeding disorders; special treatments like anticoagulants or immunosuppressants; implanted devices.<br>Example 6: transplanted organs illustrate other information that has to be taken into account in a healthcare contact.<br>Example 7: participation in a clinical trial that has to be taken into account in a healthcare contact. |
| definition_zib | Explanatory comments to the alert that can not be expressed in any of the other elements. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSAlert.text |
| id_zib | NL-CM:8.3.7 |
| name_zib | Comment |
| path_xtehr | EHDSAlert.text |
| path_zib | Alert.Comment |
| short_xtehr | Text |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Astrid 13-11: Beperkte mapping, want in de zib vult text de gestructureerde gegevens aan, terwijl EHDSAlert.text zelfstandig interpreteerbaar moet zijn.



## EHDSAlert.priority

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.priority |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:Flag-priority-code'} |
| card._xtehr | 0..* |
| definition_xtehr | A code that identifies the priority of the alert. |
| id_xtehr | EHDSAlert.priority |
| path_xtehr | EHDSAlert.priority |
| short_xtehr | Priority |
| type_xtehr | CodeableConcept |

### Comments
Astrid 13-11: Alert van het type 'Waarschuwing' zou je kunnen mappen op 'High priority', aangenomen dat deze valueset wordt gebruikt: https://build.fhir.org/ig/HL7/fhir-extensions/CodeSystem-flag-priority-code.html
Het lijkt mij dat dit wel voor EHDS compatibiliteit nodig is en dus een zib-issue moet zijn. De gebruiker moet de priority ws zelf aangeven.


## EHDSAlert.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.status |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:Flag-status'} |
| card._xtehr | 0..1 |
| definition_xtehr | Current status of the flag, Indicates whether this flag is active and needs to be displayed to a user, or whether it is no longer needed or was entered in error. |
| id_xtehr | EHDSAlert.status |
| path_xtehr | EHDSAlert.status |
| short_xtehr | Status |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAlert.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.code |
| zib | Alert.AlertName |
| alias_zib | NL: AlertNaam |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 1..1 |
| card._zib | (0..1) |
| definition_xtehr | A coded or textual representation of the flag. |
| definition_zib | A warning, other than a condition or problem. For example, a patient can be given an �Aggressive patient' alert. <br>The warning can be entered in code (there are codes for frequently used alerts), but seeing the dynamic nature of the warnings cf. SARS and Ebola, these alerts will often be entered as free text. |
| id_xtehr | EHDSAlert.code |
| id_zib | NL-CM:8.3.4 |
| name_zib | AlertName |
| path_xtehr | EHDSAlert.code |
| path_zib | Alert.AlertName |
| short_xtehr | Code |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSAlert.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAlert.period |
| zib | Alert.StartDateTime |
| alias_zib | NL: BeginDatumTijd |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period when flag is active. The period of time from the activation of the flag to inactivation of the flag. If the flag is active, the end of the period should be unspecified. |
| definition_zib | The date and time at which the described condition was entered as a warning.  <br>This can be an exact date and time, or a rough indication of the date (such as only the year, or the month and the year). |
| id_xtehr | EHDSAlert.period |
| id_zib | NL-CM:8.3.5 |
| name_zib | StartDateTime |
| path_xtehr | EHDSAlert.period |
| path_zib | Alert.StartDateTime |
| short_xtehr | Period |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments



## zib: Alert.EndDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.EndDateTime |
| alias_zib | NL: EindDatumTijd |
| card._zib | 0..1 |
| definition_zib | The date and time at which the described condition was retracted as a warning.  <br>This can be an exact date and time, or a rough indication of the date (such as only the year, or the month and the year). |
| id_zib | NL-CM:8.3.8 |
| name_zib | EndDateTime |
| path_zib | Alert.EndDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Alert.AlertType

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.AlertType |
| alias_zib | NL: AlertType |
| card._zib | 0..1 |
| definition_zib | Indicates the type of alert, meaning a rough description of the cause or origin of the warning. |
| id_zib | NL-CM:8.3.6 |
| name_zib | AlertType |
| path_zib | Alert.AlertType |
| stereotype_zib | data |
| type_zib | CD |

### Comments
Astrid 13-11: De vraag is of het 'erg' is als je geen AlertType kunt uitwisselen buiten Nederland. Het is vooral van belang voor MedicatieBewakingsoftware, die in Nederland G-standaard codes gebruikt.



## zib: Alert.HypersensitivityIntolerance

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.HypersensitivityIntolerance |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| card._zib | (0..1) |
| definition_zib | A warning for a specific hypersensitivity or intolerance, because this can pose a risk to the patient with certain treatments. For example, an alert can be given such as 'Hypersensitivity to UV light'. |
| id_zib | NL-CM:8.3.11 |
| name_zib | HypersensitivityIntolerance |
| path_zib | Alert.HypersensitivityIntolerance |
| stereotype_zib | data,reference |

### Comments



## zib: Alert.Diagnosis

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.Diagnosis |
| alias_zib | NL: Diagnose |
| card._zib | (0..1) |
| definition_zib | A warning about a particular diagnosis, because it may pose a risk to the patient with certain treatments. For example, 'Pacemaker' can be included as an alert. |
| id_zib | NL-CM:8.3.10 |
| name_zib | Diagnosis |
| path_zib | Alert.Diagnosis |
| stereotype_zib | data,reference |

### Comments



## zib: Alert.DecisionMaker::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Alert.DecisionMaker::HealthProfessional |
| alias_zib | NL: Vaststeller::Zorgverlener |
| card._zib | 1 |
| definition_zib | The health professional who is responsible for setting the alert. |
| definitioncode_zib | PRF performer |
| id_zib | NL-CM:8.3.9 |
| name_zib | DecisionMaker::HealthProfessional |
| path_zib | Alert.DecisionMaker::HealthProfessional |
| stereotype_zib | context,reference |

### Comments
Astrid 13-11: EHDS issue: dit element aanvragen. Als je twijfelt aan de (prioriteit van) een Alert dan is het nuttig om te weten wie het Alert heeft ingesteld. Je kunt dan beoordelen of je het wilt overnemen of zelf wilt evalueren/aanpassen.

