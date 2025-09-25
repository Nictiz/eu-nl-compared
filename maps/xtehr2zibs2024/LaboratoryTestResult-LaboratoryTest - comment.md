# LaboratoryTestResult.LaboratoryTest as of 10-9-2025

## Version history

v1: 10-09-2025, initial version

## Compared
### Scope
Scope is similar. Main difference is the possibility to have components in a test and hasMemeber relationships. 

### Other
- For observation.code terminology additional binding in xtEHR to NPU and in the zib to NHG.
- Interpertation  xtEHR proposes CD datatype with terminology binding SNOMED and  HL7 ObservationInterpretation. Where the zib is free text. 
- Reference range Datatype Base is wrong in the logical model as it does not define what reference range is.  
 
Mapping for Order to Aanvraaggegvens is a sperate mapping
Header is not mapped other than for status. 

### Zib elements not present in xtEHR model:
- LaboratoryTestResult.LaboratoryTest.ResultFlags

### EHDS elements not present in the zib model:

- EHDSLaboratoryObservation.accreditationStatus
- EHDSLaboratoryObservation.anatomicLocation  
- EHDSLaboratoryObservation.calibrator
- EHDSLaboratoryObservation.component
- EHDSLaboratoryObservation.component.code
- EHDSLaboratoryObservation.component.dataAbsentReason
- EHDSLaboratoryObservation.component.interpretation
- EHDSLaboratoryObservation.component.referenceRange
- EHDSLaboratoryObservation.component.result
- EHDSLaboratoryObservation.component.result.uncertainty
- EHDSLaboratoryObservation.component.result.value[x]
- EHDSLaboratoryObservation.dataAbsentReason
- EHDSLaboratoryObservation.derivedFrom[x]
- EHDSLaboratoryObservation.hasMember[x]
- EHDSLaboratoryObservation.order
- EHDSLaboratoryObservation.originalName
- EHDSLaboratoryObservation.performer[x]
- EHDSLaboratoryObservation.pointOfCareTest
- EHDSLaboratoryObservation.previousResults
- EHDSLaboratoryObservation.result
- EHDSLaboratoryObservation.result.uncertainty
- EHDSLaboratoryObservation.resultDescription
- EHDSLaboratoryObservation.testKit
- EHDSLaboratoryObservation.triggeredBy[x]

## Discussions (datum:) LabResult
# Notulen  

### 1. hasMember & Components
- **Vraagstuk**: Hoe om te gaan met `hasMember` in EHDS?  
  - Zit nu in *LaboratoryTest*.  
  - Twee mogelijkheden:
    1. Panels onder `hasMember` verwerken (en `components` laten vervallen).  
    2. Definitie verduidelijken (nu onduidelijk).  
- **Actie Xt-EHR**: Guidance geven op dit vlak – vraag aan EHDS.

> ✅ **Misschien checken bij Dave?** Waarschijnlijk is dit al afgesproken (ook internationaal, binnen EU en bij andere observations).

---

### 2. Observation Code (NPU)
- **Opmerking**: Observation code mogelijk via *NPU*.  
- **Belangrijk**: NPU mag er niet uit (voorstel Feijke).  
- **Acties**:
  - **ZC**: Hoe aangeven wat de ontvangende kant moet ontvangen?  
  - Beschrijven hoe om te gaan met codes uit andere codesystemen (mogelijk in zibs-tekst).  
  - Eventueel *components* volledig weglaten.  
  - **Audits**: Moet gecodeerde uitwisseling altijd in het Engels?

---

### 3. Interpretation
- **Huidig verschil**:  
  - EU → *code data type*.  
  - ZC → *string veld*.  
  - Mogelijk verschil door verkeerde mapping met *ResultFlags*.  
- **Acties**:  
  - Mapping nalopen.  
  - **Roxanne**: nagaan welk element beter mapt.  
  - Beter navolgen hoe interpretations geïnterpreteerd moeten worden.

---

### 4. Reference Range
- **Probleem**: In EHDS LLM datatype = *base* → inhoudsloos.  
- **Actie**: Wijzigen naar hetzelfde datatype als de normale *reference range* in de standaard Observation.

---

### 5. AccreditationStatus
- **Acties**:  
  - **Diag**: Definitie verduidelijken – wat betekent geaccrediteerd lab precies?  
  - **ZC**: Onderzoeken of dit dataelement meerwaarde heeft.

---

### 6. AnatomicLocation
- **Opmerking**: Komt zowel bij *Specimen* als *LabObservation* voor.  
- **Probleem**: Meerwaarde onduidelijk.  
- **Actie ZC**: Beschrijven in scope (Excel) waarom dit in PS als *Observation* is gedefinieerd i.p.v. *LaboratoryObservation*.

---

### 7. Calibrator
- **Actie ZC**: Zib-issue maken voor toevoegen van dit dataelement.

---

### 8. dataAbsentReason
- **Huidig**:  
  - Values zijn hetzelfde in NL Core en FHIR.  
- **Acties**:  
  - **Michal**: check profiling guidelines.  
  - **ZC**: onderzoeken of dit een zib-issue is of opgelost kan worden in FHIR.

---

### 9. DerivedFrom
- **Verschil**:  
  - EHDS → meerdere soorten relaties met andere labresultaten.  
  - Zib → alleen *GerelateerdeUitslag*.  
- **Actie ZC**: Uitzoeken of specificatie van relaties nodig is.  
  - Als NL geen behoefte heeft: hoe zorgen we toch voor duidelijke relaties?

---

### 10. Header.Status
- **Vraag**: Bedoelen we de *status van de observatie*?  
- **Opmerking**: EHDS → status van de resource (technisch), niet inhoudelijk.

---

### 11. originalName
- **Huidig**: Valt onder *ObservationCode*.  
- **Probleem**: Onduidelijk verschil met bestaande string veld in *Codeable Context*.  
- **Actie**: Feedback → veld weghalen óf duidelijke definitie/meerwaarde geven.

---

### 12. PreviousResults
- **Huidig**: Niet in zib.  
- **Mogelijk**: Wel in IS → afstemmen met EG.  
- **Vraagstuk**: Gaat dit om panels of voorgaande labresultaten in de tijd?  
- **Actie EHDS**: verduidelijken betekenis en toepassing.

---

### 13. Uncertainty
- **Actie ZC**: Analyseren of dit in de zib moet worden opgenomen.

---

### 14. TestKit
- **Actie ZC**: Analyseren of dit in de zib moet worden opgenomen.


## Actiepuntenlijst

| zib                                                               | xtehr                                                  | type_zib   | type_xtehr                | card._zib   | card._xtehr   |
|:------------------------------------------------------------------|:-------------------------------------------------------|:-----------|:--------------------------|:------------|:--------------|
| LaboratoryTestResult.LaboratoryTest                               | EHDSLaboratoryObservation                              |            |                           | 0..*        | 0..*          |
|                                                                   | EHDSLaboratoryObservation.accreditationStatus          |            | boolean                   |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.anatomicLocation             |            | EHDSBodyStructure         |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.calibrator                   |            | Identifier                |             | 0..1          |
| LaboratoryTestResult.LaboratoryTest.TestCode                      | EHDSLaboratoryObservation.code                         | CD         | CodeableConcept           | 1           | 1..1          |
|                                                                   | EHDSLaboratoryObservation.component                    |            | Base                      |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.component.code               |            | CodeableConcept           |             | 1..1          |
|                                                                   | EHDSLaboratoryObservation.component.dataAbsentReason   |            | CodeableConcept           |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.component.interpretation     |            | CodeableConcept           |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.component.referenceRange     |            | Base                      |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.component.result             |            | Base                      |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.component.result.uncertainty |            | Base                      |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.component.result.value[x]    |            | string                    |             | 1..1          |
|                                                                   | EHDSLaboratoryObservation.dataAbsentReason             |            | CodeableConcept           |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.derivedFrom[x]               |            | EHDSObservation           |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.hasMember[x]                 |            | EHDSLaboratoryObservation |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.header                       |            | Base                      |             | 1..1          |
|                                                                   | EHDSLaboratoryObservation.header.authorship            |            | Base                      |             | 1..*          |
|                                                                   | EHDSLaboratoryObservation.header.authorship.author[x]  |            | EHDSHealthProfessional    |             | 1..1          |
|                                                                   | EHDSLaboratoryObservation.header.authorship.datetime   |            | dateTime                  |             | 1..1          |
|                                                                   | EHDSLaboratoryObservation.header.directSubject[x]      |            | EHDSPatient               |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.header.identifier            |            | Identifier                |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.header.language              |            | CodeableConcept           |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.header.lastUpdate            |            | dateTime                  |             | 0..1          |
| LaboratoryTestResult.LaboratoryTest.TestResultStatus              | EHDSLaboratoryObservation.header.status                | CD         | CodeableConcept           | 0..1        | 1..1          |
|                                                                   | EHDSLaboratoryObservation.header.statusReason[x]       |            | CodeableConcept           |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.header.subject               |            | EHDSPatient               |             | 1..1          |
|                                                                   | EHDSLaboratoryObservation.header.version               |            | string                    |             | 0..1          |
| LaboratoryTestResult.LaboratoryTest.ResultInterpretation          | EHDSLaboratoryObservation.interpretation               | ST         | CodeableConcept           | 0..1        | 0..*          |
| LaboratoryTestResult.LaboratoryTest.TestMethod                    | EHDSLaboratoryObservation.method                       | CD         | CodeableConcept           | 0..1        | 0..1          |
| LaboratoryTestResult.LaboratoryTest.TestDateTime                  | EHDSLaboratoryObservation.observationDate[x]           | TS         | dateTime                  | 0..1        | 1..1          |
|                                                                   | EHDSLaboratoryObservation.order                        |            | EHDSServiceRequest        |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.originalName                 |            | string                    |             | 0..1          |
| LaboratoryTestResult.LaboratoryTest.Performer::HealthcareProvider | EHDSLaboratoryObservation.performer[x]                 |            | EHDSHealthProfessional    |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.pointOfCareTest              |            | boolean                   |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.presentedForm                |            | EHDSAttachment            |             | 0..*          |
|                                                                   | EHDSLaboratoryObservation.previousResults              |            | EHDSLaboratoryObservation |             | 0..*          |
| LaboratoryTestResult.LaboratoryTest.ReferenceRangeUpperLimit      | EHDSLaboratoryObservation.referenceRange               | ANY        | Base                      | 0..1        | 0..*          |
|                                                                   | EHDSLaboratoryObservation.result                       |            | Base                      |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.result.uncertainty           |            | Base                      |             | 0..1          |
| LaboratoryTestResult.LaboratoryTest.TestResult                    | EHDSLaboratoryObservation.result.value[x]              | ANY        | string                    | 0..1        | 1..1          |
|                                                                   | EHDSLaboratoryObservation.resultDescription            |            | string                    |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.testKit                      |            | EHDSDevice                |             | 0..1          |
|                                                                   | EHDSLaboratoryObservation.triggeredBy[x]               |            | EHDSLaboratoryObservation |             | 0..*          |
| LaboratoryTestResult.LaboratoryTest.ReferenceRangeLowerLimit      |                                                        | ANY        |                           | 0..1        |               |
| LaboratoryTestResult.LaboratoryTest.ResultFlags                   |                                                        | CD         |                           | 0..1        |               |



## EHDSLaboratoryObservation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation |
| zib | LaboratoryTestResult.LaboratoryTest |
| alias_zib | NL: LaboratoriumTest |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | EHDS refined base model for Observation performed by laboratory |
| definition_zib | Container of the LaboratoryTest concept. This container contains all data elements of the LaboratoryTest concept. |
| id_xtehr | EHDSLaboratoryObservation |
| id_zib | NL-CM:13.1.3 |
| name_zib | LaboratoryTest |
| path_xtehr | EHDSLaboratoryObservation |
| path_zib | LaboratoryTestResult.LaboratoryTest |
| short_xtehr | Laboratory observation model |
| stereotype_zib | container |

### Comments



## EHDSLaboratoryObservation.accreditationStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.accreditationStatus |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Accreditation status of the laboratory for the observation. |
| id_xtehr | EHDSLaboratoryObservation.accreditationStatus |
| path_xtehr | EHDSLaboratoryObservation.accreditationStatus |
| short_xtehr | Accreditation status of the laboratory for the observation. |
| type_xtehr | boolean |

### Comments



## EHDSLaboratoryObservation.anatomicLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.anatomicLocation |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Anatomic location and laterality where the observation was performed. |
| id_xtehr | EHDSLaboratoryObservation.anatomicLocation |
| path_xtehr | EHDSLaboratoryObservation.anatomicLocation |
| short_xtehr | Anatomic location and laterality where the observation was performed. |
| type_xtehr | EHDSBodyStructure |

### Comments



## EHDSLaboratoryObservation.calibrator

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.calibrator |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Information about which end-user calibrator the laboratory used for the measurement to indicate the metrological traceability chain.� |
| id_xtehr | EHDSLaboratoryObservation.calibrator |
| path_xtehr | EHDSLaboratoryObservation.calibrator |
| short_xtehr | Information about which end-user calibrator the laboratory used for the measurement to indicate the metrological traceability chain.� |
| type_xtehr | Identifier |

### Comments



## EHDSLaboratoryObservation.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.code |
| zib | LaboratoryTestResult.LaboratoryTest.TestCode |
| alias_zib | NL: TestCode |
| binding_xtehr | {'strength': 'preferred', 'description': 'LOINC, NPU'} |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Code representing the observation using the agreed code systems. |
| definition_zib | The name and code of the executed test. |
| id_xtehr | EHDSLaboratoryObservation.code |
| id_zib | NL-CM:13.1.8 |
| name_zib | TestCode |
| path_xtehr | EHDSLaboratoryObservation.code |
| path_zib | LaboratoryTestResult.LaboratoryTest.TestCode |
| short_xtehr | Observation code |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
- Scope and cardinality match, terminology additional binding to NPU and in the zib to NHG.



## EHDSLaboratoryObservation.component

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Component in case the observation consists of multiple sub-observations (e.g. blood pressure). |
| id_xtehr | EHDSLaboratoryObservation.component |
| path_xtehr | EHDSLaboratoryObservation.component |
| short_xtehr | Component in case the observation consists of multiple sub-observations (e.g. blood pressure). |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.component.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.code |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'LOINC, NPU, SNOMED CT'} |
| card._xtehr | 1..1 |
| definition_xtehr | Code representing the observation using the agreed code systems. |
| id_xtehr | EHDSLaboratoryObservation.component.code |
| path_xtehr | EHDSLaboratoryObservation.component.code |
| short_xtehr | Code representing the observation using the agreed code systems. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryObservation.component.dataAbsentReason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.dataAbsentReason |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Data absent reason'} |
| card._xtehr | 0..1 |
| definition_xtehr | Provides a reason why the expected value in the element Observation.value[x] is missing. |
| id_xtehr | EHDSLaboratoryObservation.component.dataAbsentReason |
| path_xtehr | EHDSLaboratoryObservation.component.dataAbsentReason |
| short_xtehr | Provides a reason why the expected value in the element Observation.value[x] is missing. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryObservation.component.interpretation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.interpretation |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, HL7 ObservationInterpretation'} |
| card._xtehr | 0..* |
| definition_xtehr | Information about reference intervals and result interpretation. |
| id_xtehr | EHDSLaboratoryObservation.component.interpretation |
| path_xtehr | EHDSLaboratoryObservation.component.interpretation |
| short_xtehr | Information about reference intervals and result interpretation. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryObservation.component.referenceRange

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.referenceRange |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reference range, multiple reference ranges of different types culd by provided. Provides guide for interpretation of result. |
| id_xtehr | EHDSLaboratoryObservation.component.referenceRange |
| path_xtehr | EHDSLaboratoryObservation.component.referenceRange |
| short_xtehr | Reference range, multiple reference ranges of different types culd by provided. Provides guide for interpretation of result. |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.component.result

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.result |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Result of the observation including text, numeric and coded results of the measurement and measurement uncertainty. Content of the observation result will vary according to the type of the observation. |
| id_xtehr | EHDSLaboratoryObservation.component.result |
| path_xtehr | EHDSLaboratoryObservation.component.result |
| short_xtehr | Result of the observation including text, numeric and coded results of the measurement and measurement uncertainty. Content of the observation result will vary according to the type of the observation. |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.component.result.uncertainty

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.result.uncertainty |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Measurement uncertainty type and interval if needed. |
| id_xtehr | EHDSLaboratoryObservation.component.result.uncertainty |
| path_xtehr | EHDSLaboratoryObservation.component.result.uncertainty |
| short_xtehr | Measurement uncertainty type and interval if needed. |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.component.result.value[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.component.result.value[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Observation result value according to the type of observation |
| id_xtehr | EHDSLaboratoryObservation.component.result.value[x] |
| path_xtehr | EHDSLaboratoryObservation.component.result.value[x] |
| short_xtehr | Observation result value according to the type of observation |
| type_xtehr | string |

### Comments



## EHDSLaboratoryObservation.dataAbsentReason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.dataAbsentReason |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Data absent reason'} |
| card._xtehr | 0..1 |
| definition_xtehr | Provides a reason why the expected value in the element Observation.value[x] is missing. |
| id_xtehr | EHDSLaboratoryObservation.dataAbsentReason |
| path_xtehr | EHDSLaboratoryObservation.dataAbsentReason |
| short_xtehr | Provides a reason why the expected value in the element Observation.value[x] is missing. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryObservation.derivedFrom[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.derivedFrom[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reference to the related resource from which the observation has been made. For example, a calculated anion gap or a fetal measurement based on an ultrasound image. |
| id_xtehr | EHDSLaboratoryObservation.derivedFrom[x] |
| path_xtehr | EHDSLaboratoryObservation.derivedFrom[x] |
| short_xtehr | Reference to the related resource from which the observation has been made. For example, a calculated anion gap or a fetal measurement based on an ultrasound image. |
| type_xtehr | EHDSObservation |

### Comments



## EHDSLaboratoryObservation.hasMember[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.hasMember[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | This observation is a group observation (e.g. a battery, a panel of tests, a set of vital sign measurements) that includes the target as a member of the group. |
| id_xtehr | EHDSLaboratoryObservation.hasMember[x] |
| path_xtehr | EHDSLaboratoryObservation.hasMember[x] |
| short_xtehr | This observation is a group observation (e.g. a battery, a panel of tests, a set of vital sign measurements) that includes the target as a member of the group. |
| type_xtehr | EHDSLaboratoryObservation |

### Comments



## EHDSLaboratoryObservation.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSLaboratoryObservation.header |
| path_xtehr | EHDSLaboratoryObservation.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSLaboratoryObservation.header.authorship |
| path_xtehr | EHDSLaboratoryObservation.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSLaboratoryObservation.header.authorship.author[x] |
| path_xtehr | EHDSLaboratoryObservation.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSLaboratoryObservation.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSLaboratoryObservation.header.authorship.datetime |
| path_xtehr | EHDSLaboratoryObservation.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryObservation.header.directSubject[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.directSubject[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The direct subject of the observation if different from the patient (subject of care), e.g. an observation of an implanted device |
| id_xtehr | EHDSLaboratoryObservation.header.directSubject[x] |
| path_xtehr | EHDSLaboratoryObservation.header.directSubject[x] |
| short_xtehr | The direct subject of the observation if different from the patient (subject of care), e.g. an observation of an implanted device |
| type_xtehr | EHDSPatient |

### Comments



## EHDSLaboratoryObservation.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSLaboratoryObservation.header.identifier |
| path_xtehr | EHDSLaboratoryObservation.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSLaboratoryObservation.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSLaboratoryObservation.header.language |
| path_xtehr | EHDSLaboratoryObservation.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryObservation.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSLaboratoryObservation.header.lastUpdate |
| path_xtehr | EHDSLaboratoryObservation.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSLaboratoryObservation.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.status |
| zib | LaboratoryTestResult.LaboratoryTest.TestResultStatus |
| alias_zib | NL: TestUitslagStatus |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Observation status'} |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Status of the resource |
| definition_zib | The status of the test result of this test. If the laboratory test is a panel/cluster, the overall status is given in the status of the panel/cluster. |
| definitioncode_zib | LOINC: 92236-9 Lab observation result status |
| id_xtehr | EHDSLaboratoryObservation.header.status |
| id_zib | NL-CM:13.1.31 |
| name_zib | TestResultStatus |
| path_xtehr | EHDSLaboratoryObservation.header.status |
| path_zib | LaboratoryTestResult.LaboratoryTest.TestResultStatus |
| short_xtehr | Status of the resource |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
This seems to match based on the terminology binding? 


## EHDSLaboratoryObservation.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSLaboratoryObservation.header.statusReason[x] |
| path_xtehr | EHDSLaboratoryObservation.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSLaboratoryObservation.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSLaboratoryObservation.header.subject |
| path_xtehr | EHDSLaboratoryObservation.header.subject |
| short_xtehr | Patient who is receiving health care. This patient might be different from the direct subject of the observation. |
| type_xtehr | EHDSPatient |

### Comments



## EHDSLaboratoryObservation.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSLaboratoryObservation.header.version |
| path_xtehr | EHDSLaboratoryObservation.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSLaboratoryObservation.interpretation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.interpretation |
| zib | LaboratoryTestResult.LaboratoryTest.ResultInterpretation |
| alias_zib | NL: UitslagInterpretatie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, HL7 ObservationInterpretation'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Information about reference intervals and result interpretation. |
| definition_zib | Comment of the laboratory specialist regarding the interpretation of the results |
| definitioncode_zib | SNOMED CT: 441742003 Evaluation finding |
| id_xtehr | EHDSLaboratoryObservation.interpretation |
| id_zib | NL-CM:13.1.32 |
| name_zib | ResultInterpretation |
| path_xtehr | EHDSLaboratoryObservation.interpretation |
| path_zib | LaboratoryTestResult.LaboratoryTest.ResultInterpretation |
| short_xtehr | Information about reference intervals and result interpretation. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | ST |

### Comments
Scope match, Cardinality and datatype mismatch. xtEHR proposes CD with terminology binding SNOMED and  HL7 ObservationInterpretation. 


## EHDSLaboratoryObservation.method

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.method |
| zib | LaboratoryTestResult.LaboratoryTest.TestMethod |
| alias_zib | NL: Testmethode |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Observation method (measurement principle) to obtain the result. |
| definition_zib | The test method used to obtain the result. |
| definitioncode_zib | SNOMED CT: 246501002 Technique |
| id_xtehr | EHDSLaboratoryObservation.method |
| id_zib | NL-CM:13.1.9 |
| name_zib | TestMethod |
| path_xtehr | EHDSLaboratoryObservation.method |
| path_zib | LaboratoryTestResult.LaboratoryTest.TestMethod |
| short_xtehr | Observation method |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Match. 


## EHDSLaboratoryObservation.observationDate[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.observationDate[x] |
| zib | LaboratoryTestResult.LaboratoryTest.TestDateTime |
| alias_zib | NL: TestDatumTijd |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Clinically relevant time or time period for the observation |
| definition_zib | The date and if possible the time at which the test was carried out. |
| id_xtehr | EHDSLaboratoryObservation.observationDate[x] |
| id_zib | NL-CM:13.1.13 |
| name_zib | TestDateTime |
| path_xtehr | EHDSLaboratoryObservation.observationDate[x] |
| path_zib | LaboratoryTestResult.LaboratoryTest.TestDateTime |
| short_xtehr | Clinically relevant time or time period for the observation |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Scope definition is not exactly the same but intend seems equal. Cardinality and datatype match. 


## EHDSLaboratoryObservation.order

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.order |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Identifies order and order placer this observation belongs to |
| id_xtehr | EHDSLaboratoryObservation.order |
| path_xtehr | EHDSLaboratoryObservation.order |
| short_xtehr | Identifies order and order placer this observation belongs to |
| type_xtehr | EHDSServiceRequest |

### Comments
Could be matched to Zib Aanvraaggegevens. 


## EHDSLaboratoryObservation.originalName

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.originalName |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Original (conventional) name of the observation |
| id_xtehr | EHDSLaboratoryObservation.originalName |
| path_xtehr | EHDSLaboratoryObservation.originalName |
| short_xtehr | Original (conventional) name of the observation |
| type_xtehr | string |

### Comments



## EHDSLaboratoryObservation.performer[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.performer[x] |
| zib | LaboratoryTestResult.LaboratoryTest.Performer::HealthcareProvider |
| card._xtehr | 0..1 |
| definition_xtehr | Performer of the observation. Some test could be performed by the patient himself or by a care giver. Those are in the scope of this deliverable under specified conditions. |
| id_xtehr | EHDSLaboratoryObservation.performer[x] |
| path_xtehr | EHDSLaboratoryObservation.performer[x] |
| short_xtehr | Performer of the observation. Some test could be performed by the patient himself or by a care giver. Those are in the scope of this deliverable under specified conditions. |
| type_xtehr | EHDSHealthProfessional |

### Comments
Match.


## EHDSLaboratoryObservation.pointOfCareTest

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.pointOfCareTest |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Indicates if the observation is a point-of-care test (POCT), i.e. an examination performed near or at the site of a patient. |
| id_xtehr | EHDSLaboratoryObservation.pointOfCareTest |
| path_xtehr | EHDSLaboratoryObservation.pointOfCareTest |
| short_xtehr | Examination performed near or at the site of a patient. |
| type_xtehr | boolean |

### Comments



## EHDSLaboratoryObservation.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSLaboratoryObservation.presentedForm |
| path_xtehr | EHDSLaboratoryObservation.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSLaboratoryObservation.previousResults

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.previousResults |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Previous results of the same observation |
| id_xtehr | EHDSLaboratoryObservation.previousResults |
| path_xtehr | EHDSLaboratoryObservation.previousResults |
| short_xtehr | Previous results of the same observation |
| type_xtehr | EHDSLaboratoryObservation |

### Comments



## EHDSLaboratoryObservation.referenceRange

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.referenceRange |
| zib | LaboratoryTestResult.LaboratoryTest.ReferenceRangeUpperLimit |
| alias_zib | NL: ReferentieBovengrens |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Reference range, multiple reference ranges of different types culd by provided. Provides guide for interpretation of result. |
| definition_zib | The upper reference limit for the patient of the value measured in the test. |
| id_xtehr | EHDSLaboratoryObservation.referenceRange |
| id_zib | NL-CM:13.1.11 |
| name_zib | ReferenceRangeUpperLimit |
| path_xtehr | EHDSLaboratoryObservation.referenceRange |
| path_zib | LaboratoryTestResult.LaboratoryTest.ReferenceRangeUpperLimit |
| short_xtehr | Reference range, multiple reference ranges of different types culd by provided. Provides guide for interpretation of result. |
| stereotype_zib | data |
| type_xtehr | Base |
| type_zib | ANY |

### Comments
Match, but zib has 2 seperate values for Upper and Lower limit. Datatype Base is wrong in the logical model as it does not define what referencerange is.  


## EHDSLaboratoryObservation.result

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.result |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Result of the observation including text, numeric and coded results of the measurement and measurement uncertainty. Content of the observation result will vary according to the type of the observation. |
| id_xtehr | EHDSLaboratoryObservation.result |
| path_xtehr | EHDSLaboratoryObservation.result |
| short_xtehr | Result of the observation including text, numeric and coded results of the measurement and measurement uncertainty. Content of the observation result will vary according to the type of the observation. |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.result.uncertainty

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.result.uncertainty |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Measurement uncertainty type and interval if needed. |
| id_xtehr | EHDSLaboratoryObservation.result.uncertainty |
| path_xtehr | EHDSLaboratoryObservation.result.uncertainty |
| short_xtehr | Measurement uncertainty type and interval if needed. |
| type_xtehr | Base |

### Comments



## EHDSLaboratoryObservation.result.value[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.result.value[x] |
| zib | LaboratoryTestResult.LaboratoryTest.TestResult |
| alias_zib | NL: TestUitslag |
| binding_xtehr | {'strength': 'preferred', 'description': 'UCUM for units, SNOMED CT for coded results'} |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Observation result value according to the type of observation |
| definition_zib | The test result. Depending on the type of test, the result will consist of a value with a unit or a coded value (ordinal or nominal). |
| id_xtehr | EHDSLaboratoryObservation.result.value[x] |
| id_zib | NL-CM:13.1.10 |
| name_zib | TestResult |
| path_xtehr | EHDSLaboratoryObservation.result.value[x] |
| path_zib | LaboratoryTestResult.LaboratoryTest.TestResult |
| short_xtehr | Observation result value according to the type of observation |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ANY |

### Comments
Cardinality mismatch but the result.value is in a result cluster and this is 0..1 so result.value can also be omitted. The zib only defines quantities and codeable concepts as possible datatypes, xtEHR adds Range and String (free text). 


## EHDSLaboratoryObservation.resultDescription

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.resultDescription |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Comments and narrative representation of the observation result and findings. |
| id_xtehr | EHDSLaboratoryObservation.resultDescription |
| path_xtehr | EHDSLaboratoryObservation.resultDescription |
| short_xtehr | Comments and narrative representation of the observation result and findings. |
| type_xtehr | string |

### Comments



## EHDSLaboratoryObservation.testKit

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.testKit |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Laboratory test kit used during measurement. |
| id_xtehr | EHDSLaboratoryObservation.testKit |
| path_xtehr | EHDSLaboratoryObservation.testKit |
| short_xtehr | Laboratory test kit used during measurement. |
| type_xtehr | EHDSDevice |

### Comments



## EHDSLaboratoryObservation.triggeredBy[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLaboratoryObservation.triggeredBy[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | References to the observation(s) that triggered the performance of this observation. |
| id_xtehr | EHDSLaboratoryObservation.triggeredBy[x] |
| path_xtehr | EHDSLaboratoryObservation.triggeredBy[x] |
| short_xtehr | References to the observation(s) that triggered the performance of this observation. |
| type_xtehr | EHDSLaboratoryObservation |

### Comments



## zib: LaboratoryTestResult.LaboratoryTest.ReferenceRangeLowerLimit

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.LaboratoryTest.ReferenceRangeLowerLimit |
| alias_zib | NL: ReferentieOndergrens |
| card._zib | 0..1 |
| definition_zib | The lower reference limit for the patient of the value measured with the test. |
| id_zib | NL-CM:13.1.12 |
| name_zib | ReferenceRangeLowerLimit |
| path_zib | LaboratoryTestResult.LaboratoryTest.ReferenceRangeLowerLimit |
| stereotype_zib | data |
| type_zib | ANY |

### Comments



## zib: LaboratoryTestResult.LaboratoryTest.ResultFlags

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.LaboratoryTest.ResultFlags |
| alias_zib | NL: InterpretatieVlaggen |
| card._zib | 0..1 |
| definition_zib | Attention codes indicating whether the result of a quantitative test is above or below certain reference values or interpreting the result otherwise.(Resistent). The values Resistant, Intermediate en Susceptible are used with microbiological test results. |
| definitioncode_zib | SNOMED CT: 363713009 Has interpretation |
| id_zib | NL-CM:13.1.14 |
| name_zib | ResultFlags |
| path_zib | LaboratoryTestResult.LaboratoryTest.ResultFlags |
| stereotype_zib | data |
| type_zib | CD |

### Comments

