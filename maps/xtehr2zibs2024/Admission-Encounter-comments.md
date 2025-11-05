# Encounter

## Discussie 30 oktober 2025  
Aanwezig:
+ Astrid
+ Yasmin
+ Wouter
+ Marty
+ Sander
+ Jacob

.priority: FHIRr6: niet meer bij admission - Astrid:deze hoort gezien de huidige waardenlijst niet in dit model maar in een procesmodel zoals Aanvraaggegevens. Achteraf noteren van prioriteit kan een kwaliteit/performance doel dienen. Daarvoor volstaat een meer beperkte waardenlijst bv spoed/regulier.    
In de zib aanvraaggegevens moet priority ==> zib issue    
===> zib-issue: deelopnames  
===> zib-issue: admission type nodig (deelopname en volledige opname)  

hoe zijn de location parts bedoeld?  
zib: opname is op vestigingsniveau?
alleen volledige opname binnen vestiging bedoeld?  

.note: naar EHDS opmerken: dit is een narrative (tekstuele samenvattiing) en hoort niet in het model  
(zie voorstel Astrid over narrative, note, comment in AllergyIntolerance). We communiceren dit naar EHDS, maar niet als een issue op EHDSEncounter.    

.baseOn: Er is nu geen relatie in de zibs tussen opname en encounter naar zorgepisode => zib issue

.partOf
wat is de definitie van .partOf?  wordt het bepaald door de locatie? kan je binnen een part meerdere locations hebben?
Een definitie van encounter zou kunnen zijn:
+ aaneengesloten
+ in 1 vestiging
Astrid pleit voor : location 1-op-1 met part maken, dan moet location kardinaliteit 1 krijgen ==> EHDS issue 

  

## Overall discussion
The Xt-EHR Encounter model apparently has a broader scope, including the scope of both Admission and Contact zibs. 
The Xt-EHR model and the zib can both be used for both past admissions and planned admissions. However, only the Xt-EHR models actual and planned start and end dates separately.
The Xt-EHR model is layered: an encounter can be part of an encounter. 


| zib                                                               | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:------------------------------------------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Admission                                                         | EHDSEncounter                                  |            |                        |             | 0..*          |
|                                                                   | EHDSEncounter.presentedForm                    |            | EHDSAttachment         |             | 0..*          |
|                                                                   | EHDSEncounter.priority                         |            | CodeableConcept        |             | 0..1          |
|                                                                   | EHDSEncounter.type                             |            | CodeableConcept        |             | 1..1          |
|                                                                   | EHDSEncounter.note                             |            | string                 |             | 0..1          |
|                                                                   | EHDSEncounter.episodeOfCare                    |            | EHDSEpisodeOfCare      |             | 0..*          |
|                                                                   | EHDSEncounter.basedOn[x]                       |            | EHDSCarePlan           |             | 0..*          |
|                                                                   | EHDSEncounter.partOf                           |            | EHDSEncounter          |             | 0..1          |
|                                                                   | EHDSEncounter.serviceProvider                  |            | EHDSOrganisation       |             | 0..1          |
| Admission.StartDateTime                                           | EHDSEncounter.actualPeriod                     | TS         | Period                 | 1           | 0..1          |
| Admission.StartDateTime                                           | EHDSEncounter.plannedStartDate                 | TS         | dateTime               | 1           | 0..1          |
| Admission.EndDateTime                                             | EHDSEncounter.plannedEndDate                   | TS         | dateTime               | 0..1        | 0..1          |
|                                                                   | EHDSEncounter.admission                        |            | Base                   |             | 0..1          |
|                                                                   | EHDSEncounter.admission.admitter               |            | EHDSHealthProfessional |             | 0..1          |
|                                                                   | EHDSEncounter.admission.admitSource            |            | CodeableConcept        |             | 0..1          |
|                                                                   | EHDSEncounter.admission.referringProfessional  |            | EHDSHealthProfessional |             | 0..1          |
| Admission.ReasonAdmission.Problem                                 | EHDSEncounter.admission.reason[x]              |            | CodeableConcept        | 1           | 0..*          |
| Admission.ReasonAdmission.TiggerForAdmission                      | EHDSEncounter.admission.reason[x]              | CD         | CodeableConcept        | 1           | 0..*          |
| Admission.ReasonAdmission.Problem.Diagnosis                       | EHDSEncounter.admission.reason[x]              |            | CodeableConcept        | (0..1)      | 0..*          |
| Admission.ReasonAdmission.Problem.Reaction                        | EHDSEncounter.admission.reason[x]              |            | CodeableConcept        | (0..1)      | 0..*          |
| Admission.ReasonAdmission.Problem.Symptom                         | EHDSEncounter.admission.reason[x]              |            | CodeableConcept        | (0..1)      | 0..*          |
| Admission.CareFacility::HealthcareProvider.CommentAdmissionReason | EHDSEncounter.admission.reasonComment          | ST         | string                 | 0..1        | 0..1          |
|                                                                   | EHDSEncounter.admission.legalStatus            |            | CodeableConcept        |             | 0..1          |
|                                                                   | EHDSEncounter.discharge                        |            | Base                   |             | 0..1          |
| Admission.Destination                                             | EHDSEncounter.discharge.destinationType        | CD         | CodeableConcept        | 0..1        | 0..1          |
|                                                                   | EHDSEncounter.discharge.destinationLocation[x] |            | EHDSOrganisation       |             | 0..1          |
|                                                                   | EHDSEncounter.location                         |            | Base                   |             | 0..*          |
|                                                                   | EHDSEncounter.location.period                  |            | Period                 |             | 0..1          |
| Admission.CareFacility::HealthcareProvider                        | EHDSEncounter.location.organisationPart[x]     |            | EHDSOrganisation       | 1           | 1..1          |
| Admission.CareType                                                |                                                | CD         |                        | 1           |               |
| Admission.Origin                                                  |                                                | CD         |                        | 1           |               |
| Admission.AdmissionScope                                          |                                                | CD         |                        | 1           |               |
| Admission.ReasonAdmission                                         |                                                |            |                        | 1           |               |
| Admission.ResponsibleHealthProfessional::HealthProfessional       |                                                |            |                        | 1           |               |






## EHDSEncounter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter |
| zib | Admission |
| alias_zib | NL: Opname |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Encounter |
| definition_zib | Root concept of the Admission information model.This root concept contains all data elements of the Admission information model. |
| id_xtehr | EHDSEncounter |
| id_zib | NL-CM:15.4.1 |
| name_zib | Admission |
| path_xtehr | EHDSEncounter |
| path_zib | Admission |
| short_xtehr | Encounter model |
| stereotype_zib | rootconcept |

### Comments



## EHDSEncounter.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSEncounter.presentedForm |
| path_xtehr | EHDSEncounter.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments
Not present in the zib as per design principles.



## EHDSEncounter.priority

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.priority |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:v3-xEncounterAdmissionUrgency'} |
| card._xtehr | 0..1 |
| definition_xtehr | Indicates the urgency of the encounter. |
| id_xtehr | EHDSEncounter.priority |
| path_xtehr | EHDSEncounter.priority |
| short_xtehr | Priority |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.type |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7v3:ActEncounterCode'} |
| card._xtehr | 1..1 |
| definition_xtehr | The type of the encounter whether inpatient or short stay encounter. |
| id_xtehr | EHDSEncounter.type |
| path_xtehr | EHDSEncounter.type |
| short_xtehr | Encounter type |
| type_xtehr | CodeableConcept |

### Comments
This concept is absent in the zib as the scope of the zib is only Admission.



## EHDSEncounter.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.note |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | A narrative description of the encounter course. |
| id_xtehr | EHDSEncounter.note |
| path_xtehr | EHDSEncounter.note |
| short_xtehr | A narrative description of the encounter course. |
| type_xtehr | string |

### Comments



## EHDSEncounter.episodeOfCare

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.episodeOfCare |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reference to the episode(s) of care that this encounter should be recorded against |
| id_xtehr | EHDSEncounter.episodeOfCare |
| path_xtehr | EHDSEncounter.episodeOfCare |
| short_xtehr | Reference to the episode(s) of care that this encounter should be recorded against |
| type_xtehr | EHDSEpisodeOfCare |

### Comments



## EHDSEncounter.basedOn[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.basedOn[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Reference to the request that initiated this encounter |
| id_xtehr | EHDSEncounter.basedOn[x] |
| path_xtehr | EHDSEncounter.basedOn[x] |
| short_xtehr | Reference to the request that initiated this encounter |
| type_xtehr | EHDSCarePlan |

### Comments



## EHDSEncounter.partOf

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.partOf |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reference to another encounter this encounter is part of |
| id_xtehr | EHDSEncounter.partOf |
| path_xtehr | EHDSEncounter.partOf |
| short_xtehr | Reference to another encounter this encounter is part of |
| type_xtehr | EHDSEncounter |

### Comments



## EHDSEncounter.serviceProvider

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.serviceProvider |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The organisation (facility) responsible for this encounter |
| id_xtehr | EHDSEncounter.serviceProvider |
| path_xtehr | EHDSEncounter.serviceProvider |
| short_xtehr | The organisation (facility) responsible for this encounter |
| type_xtehr | EHDSOrganisation |

### Comments
The zib has only HealthcareProvider in the role of *location*. 



## EHDSEncounter.actualPeriod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.actualPeriod |
| zib | Admission.StartDateTime |
| alias_zib | NL: BeginDatumTijd |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The actual start and end time of the encounter |
| definition_zib | Date and time when the (partial) admission will start or was started. |
| id_xtehr | EHDSEncounter.actualPeriod |
| id_zib | NL-CM:15.4.3 |
| name_zib | StartDateTime |
| path_xtehr | EHDSEncounter.actualPeriod |
| path_zib | Admission.StartDateTime |
| short_xtehr | The actual start and end time of the encounter |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments
Data type mismatch. The zib has StartDateTime and EndDateTime. The zib does not include actual and planned dates separately. 




## EHDSEncounter.plannedStartDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.plannedStartDate |
| zib | Admission.StartDateTime |
| alias_zib | NL: BeginDatumTijd |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The planned start date/time (or admission date) of the encounter |
| definition_zib | Date and time when the (partial) admission will start or was started. |
| id_xtehr | EHDSEncounter.plannedStartDate |
| id_zib | NL-CM:15.4.3 |
| name_zib | StartDateTime |
| path_xtehr | EHDSEncounter.plannedStartDate |
| path_zib | Admission.StartDateTime |
| short_xtehr | The planned start date/time (or admission date) of the encounter |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
The zib does not include actual and planned dates separately. 


## EHDSEncounter.plannedEndDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.plannedEndDate |
| zib | Admission.EndDateTime |
| alias_zib | NL: EindDatumTijd |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | The planned end date/time (or discharge date) of the encounter |
| definition_zib | Date and time on which the (partial) admission ended. For a future or ongoing admission, the end date can be empty. |
| id_xtehr | EHDSEncounter.plannedEndDate |
| id_zib | NL-CM:15.4.4 |
| name_zib | EndDateTime |
| path_xtehr | EHDSEncounter.plannedEndDate |
| path_zib | Admission.EndDateTime |
| short_xtehr | The planned end date/time (or discharge date) of the encounter |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
The zib does not include actual and planned dates separately. 


## EHDSEncounter.admission

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Details about the admission to a healthcare service |
| id_xtehr | EHDSEncounter.admission |
| path_xtehr | EHDSEncounter.admission |
| short_xtehr | Details about the admission to a healthcare service |
| type_xtehr | Base |

### Comments



## EHDSEncounter.admission.admitter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.admitter |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Admitting healthcare professional |
| id_xtehr | EHDSEncounter.admission.admitter |
| path_xtehr | EHDSEncounter.admission.admitter |
| short_xtehr | Admitting healthcare professional |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSEncounter.admission.admitSource

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.admitSource |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:admit-source'} |
| card._xtehr | 0..1 |
| definition_xtehr | From where the patient was admitted (e.g. physician referral, transfer). |
| id_xtehr | EHDSEncounter.admission.admitSource |
| path_xtehr | EHDSEncounter.admission.admitSource |
| short_xtehr | From where the patient was admitted (e.g. physician referral, transfer). |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.admission.referringProfessional

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.referringProfessional |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Referring Healthcare Professional |
| id_xtehr | EHDSEncounter.admission.referringProfessional |
| path_xtehr | EHDSEncounter.admission.referringProfessional |
| short_xtehr | Referring Healthcare Professional |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSEncounter.admission.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reason[x] |
| zib | Admission.ReasonAdmission.Problem |
| alias_zib | NL: Probleem |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| definition_zib | Container of the Problem concept.This container contains all data elements of the Problem concept. |
| id_xtehr | EHDSEncounter.admission.reason[x] |
| id_zib | NL-CM:15.4.14 |
| name_zib | Problem |
| path_xtehr | EHDSEncounter.admission.reason[x] |
| path_zib | Admission.ReasonAdmission.Problem |
| short_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| stereotype_zib | container |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.admission.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reason[x] |
| zib | Admission.ReasonAdmission.TiggerForAdmission |
| alias_zib | NL: AanleidingOpname |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| definition_zib | The specific reason for the admission in relation to the diagnosis and/or treatment of the problem. |
| definitioncode_zib | SNOMED CT: 59021000146108 Reason for admission |
| id_xtehr | EHDSEncounter.admission.reason[x] |
| id_zib | NL-CM:15.4.7 |
| name_zib | TiggerForAdmission |
| path_xtehr | EHDSEncounter.admission.reason[x] |
| path_zib | Admission.ReasonAdmission.TiggerForAdmission |
| short_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSEncounter.admission.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reason[x] |
| zib | Admission.ReasonAdmission.Problem.Diagnosis |
| alias_zib | NL: Diagnose |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| definition_zib | The diagnosis as the reason for the admission. |
| id_xtehr | EHDSEncounter.admission.reason[x] |
| id_zib | NL-CM:15.4.15 |
| name_zib | Diagnosis |
| path_xtehr | EHDSEncounter.admission.reason[x] |
| path_zib | Admission.ReasonAdmission.Problem.Diagnosis |
| short_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.admission.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reason[x] |
| zib | Admission.ReasonAdmission.Problem.Reaction |
| alias_zib | NL: Reactie |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| definition_zib | The adverse reaction to a substance or radiation as the reason for admission. |
| id_xtehr | EHDSEncounter.admission.reason[x] |
| id_zib | NL-CM:15.4.16 |
| name_zib | Reaction |
| path_xtehr | EHDSEncounter.admission.reason[x] |
| path_zib | Admission.ReasonAdmission.Problem.Reaction |
| short_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.admission.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reason[x] |
| zib | Admission.ReasonAdmission.Problem.Symptom |
| alias_zib | NL: Symptoom |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| definition_zib | The symptom as the reason for the admission. |
| id_xtehr | EHDSEncounter.admission.reason[x] |
| id_zib | NL-CM:15.4.17 |
| name_zib | Symptom |
| path_xtehr | EHDSEncounter.admission.reason[x] |
| path_zib | Admission.ReasonAdmission.Problem.Symptom |
| short_xtehr | Reason(s) for admission, e.g. problem, procedure or finding. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEncounter.admission.reasonComment

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.reasonComment |
| zib | Admission.CareFacility::HealthcareProvider.CommentAdmissionReason |
| alias_zib | NL: ToelichtingRedenOpname |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Explanation of the reason for the encounter. |
| definition_zib | Comment on the reason for the (partial) admission, insofar as this cannot be sufficiently expressed in the other elements. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSEncounter.admission.reasonComment |
| id_zib | NL-CM:15.4.8 |
| name_zib | CommentAdmissionReason |
| path_xtehr | EHDSEncounter.admission.reasonComment |
| path_zib | Admission.CareFacility::HealthcareProvider.CommentAdmissionReason |
| short_xtehr | Explanation of the reason for the encounter. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSEncounter.admission.legalStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.admission.legalStatus |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Legal status can be either voluntary or involuntary, however the legal status is always determined by a court. A patient can also receive healthcare based on a forensic status. (voluntary, involuntary, admission by legal authority). |
| id_xtehr | EHDSEncounter.admission.legalStatus |
| path_xtehr | EHDSEncounter.admission.legalStatus |
| short_xtehr | Legal status/situation at admission (indicates the basis on which the patient is staying in a healthcare organisation). |
| type_xtehr | CodeableConcept |

### Comments
The legal status is modelled in a separate zib, but the Admission zib does not have a reference to it.  



## EHDSEncounter.discharge

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.discharge |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Discharge details |
| id_xtehr | EHDSEncounter.discharge |
| path_xtehr | EHDSEncounter.discharge |
| short_xtehr | Discharge details |
| type_xtehr | Base |

### Comments



## EHDSEncounter.discharge.destinationType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.discharge.destinationType |
| zib | Admission.Destination |
| alias_zib | NL: Bestemming |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7.discharge-disposition'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Type of location to which the patient will go after the encounter. E.g. home, hospital, nursing home, left against medical advice etc. |
| definition_zib | Location where the patient will go after the (partial) admission. This will mainly be used at the end of hospitalization. |
| id_xtehr | EHDSEncounter.discharge.destinationType |
| id_zib | NL-CM:15.4.10 |
| name_zib | Destination |
| path_xtehr | EHDSEncounter.discharge.destinationType |
| path_zib | Admission.Destination |
| short_xtehr | Type of location to which the patient will go after the encounter. E.g. home, hospital, nursing home, left against medical advice etc. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
The concepts match exactly. The Xt-EHR concept is bound to HL7-discharge-disposition code system, whereas the zib concept is bound to a set of SNOMED values. Note that the values in this set that do not fit in the Destination concept are deprecated in the zib, but are still present in the HL7 code system. 


## EHDSEncounter.discharge.destinationLocation[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.discharge.destinationLocation[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The location/organisation to which the patient will go after the encounter. Name, address and telecommunication contact. |
| id_xtehr | EHDSEncounter.discharge.destinationLocation[x] |
| path_xtehr | EHDSEncounter.discharge.destinationLocation[x] |
| short_xtehr | The location/organisation to which the patient will go after the encounter. Name, address and telecommunication contact. |
| type_xtehr | EHDSOrganisation |

### Comments

## EHDSEncounter.location

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.location |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | List of locations where the patient has been. |
| id_xtehr | EHDSEncounter.location |
| path_xtehr | EHDSEncounter.location |
| short_xtehr | List of locations where the patient has been. |
| type_xtehr | Base |

### Comments





## EHDSEncounter.location.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.location.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time period during which the patient was present at the location |
| id_xtehr | EHDSEncounter.location.period |
| path_xtehr | EHDSEncounter.location.period |
| short_xtehr | Time period during which the patient was present at the location |
| type_xtehr | Period |

### Comments

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEncounter.location.organisationPart[x] |
| zib | Admission.CareFacility::HealthcareProvider |
| alias_zib | NL: ZorgInstelling::Zorgaanbieder |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Organisation or organisation part (department) where the patient was present. |
| definition_zib | The physical location of the healthcare provider where the (partial) admission has taken place or will take place. |
| id_xtehr | EHDSEncounter.location.organisationPart[x] |
| id_zib | NL-CM:15.4.13 |
| name_zib | CareFacility::HealthcareProvider |
| path_xtehr | EHDSEncounter.location.organisationPart[x] |
| path_zib | Admission.CareFacility::HealthcareProvider |
| short_xtehr | Organisation or organisation part (department) where the patient was present. |
| stereotype_zib | context,reference |
| type_xtehr | EHDSOrganisation |

### Comments
Partial data type mismatch. In the zib, the location is a reference to zib Healthcare provicer (hence, an organization). In the Xt-EHR model, the location is either a EHDSOrganisation or a EHDSLocation.  
Cardinality mismatch. In the Xt-EHR model, container .location has cardinality 0..*. In the zib, .CareFacility has cardinality 1..1.




## zib: Admission.CareType

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Admission.CareType |
| alias_zib | NL: ZorgType |
| card._zib | 1 |
| definition_zib | The type of care that has been or will be provided to the patient during the (partial) admission. This is related, among other things, to the severity category of the care. |
| id_zib | NL-CM:15.4.2 |
| name_zib | CareType |
| path_zib | Admission.CareType |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Admission.Origin

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Admission.Origin |
| alias_zib | NL: Herkomst |
| card._zib | 1 |
| definition_zib | Location where the patient comes from prior to the (partial) admission. This will mainly be used at the start of hospitalisation. |
| id_zib | NL-CM:15.4.9 |
| name_zib | Origin |
| path_zib | Admission.Origin |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Admission.AdmissionScope

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Admission.AdmissionScope |
| alias_zib | NL: OpnameScope |
| card._zib | 1 |
| definition_zib | AdmissionScope indicates whether it is a overall admission or a partial admission. |
| id_zib | NL-CM:15.4.11 |
| name_zib | AdmissionScope |
| path_zib | Admission.AdmissionScope |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Admission.ReasonAdmission

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Admission.ReasonAdmission |
| alias_zib | NL: RedenOpname |
| card._zib | 1 |
| definition_zib | Container of the ReasonAdmission concept.This container contains all data elements of the ReasonAdmission concept. |
| id_zib | NL-CM:15.4.5 |
| name_zib | ReasonAdmission |
| path_zib | Admission.ReasonAdmission |
| stereotype_zib | container |

### Comments



## zib: Admission.ResponsibleHealthProfessional::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Admission.ResponsibleHealthProfessional::HealthProfessional |
| alias_zib | NL: VerantwoordelijkBehandelaar::Zorgverlener |
| card._zib | 1 |
| definition_zib | The health professional who is responsible during the (partial) admission. The information about the health professional can also include the specialism and role of the health professional. |
| id_zib | NL-CM:15.4.12 |
| name_zib | ResponsibleHealthProfessional::HealthProfessional |
| path_zib | Admission.ResponsibleHealthProfessional::HealthProfessional |
| stereotype_zib | context,reference |

### Comments

