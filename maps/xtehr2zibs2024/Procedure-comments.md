# Procedure as of 27-05-2025

| zib                                                       | xtehr                          | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:----------------------------------------------------------|:-------------------------------|:-----------|:----------------|:------------|:--------------|
| Procedure                                                 | EHDSProcedure                  |            |                 |             | 0..*          |
| Procedure.ProcedureAnatomicalLocation::AnatomicalLocation | EHDSProcedure.anatomicLocation |            | CodeableConcept | 0..1        | 0..*          |
| Procedure.ProcedureType                                   | EHDSProcedure.code             |            | CodeableConcept |             | 0..1          |
|                                                           | EHDSProcedure.complication     |            | CodeableConcept |             | 0..*          |
| Procedure.ProcedureEndDate                                | EHDSProcedure.date[x]          | TS         | dateTime        | 0..1        | 0..1          |
| Procedure.ProcedureStartDate                              | EHDSProcedure.date[x]          | TS         | dateTime        | 0..1        | 0..1          |
|                                                           | EHDSProcedure.description      |            | string          |             | 0..1          |
|                                                           | EHDSProcedure.deviceUsed       |            | EHDSDevice      |             | 0..*          |
| Procedure.MedicalDevice                                   | EHDSProcedure.focalDevice      |            | Reference       |             | 0..*          |
|                                                           | EHDSProcedure.identifier       |            | Identifier      |             | 0..*          |
| Procedure.Location::HealthcareProvider                    | EHDSProcedure.location         |            | EHDSLocation    | 0..1        | 0..*          |
|                                                           | EHDSProcedure.note             |            | string          |             | 0..1          |
|                                                           | EHDSProcedure.outcome          |            | CodeableConcept |             | 0..1          |
| Procedure.Performer::HealthProfessional                   | EHDSProcedure.performer        |            | Reference       | 0..*        | 0..*          |
| Procedure.Indication                                      | EHDSProcedure.reason           |            | Reference       | 0..*        | 0..*          |
| Procedure.Indication.Diagnosis                            | EHDSProcedure.reason           |            | Reference       | (0..1)      | 0..*          |
| Procedure.Indication.Reaction                             | EHDSProcedure.reason           |            | Reference       | (0..1)      | 0..*          |
| Procedure.Indication.Symptom                              | EHDSProcedure.reason           |            | Reference       | (0..1)      | 0..*          |
| Procedure.Indication::Problem                             | EHDSProcedure.reason           |            | Reference       |             | 0..*          |
|                                                           | EHDSProcedure.subject          |            | Reference       |             | 1..1          |
|                                                           |                                |            |                 | 0..*        |               |
| Procedure.ProcedureMethod                                 |                                |            |                 |             |               |
|                                                           |                                | CD         |                 | 0..*        |               |
|                                                           |                                | CD         |                 | 1           |               |
| Procedure.Requester::HealthProfessional                   |                                |            |                 |             |               |



## EHDSProcedure

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure |
| zib | Procedure |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.16 - EHDS refined base model for An action that is or was performed on or for a patient |
| definition_zib | Root concept of the Procedure information model. This root concept contains all data elements of the Procedure information model. |
| definitioncode_zib | 71388002 Procedure |
| id_xtehr | EHDSProcedure |
| id_zib | NL-CM:14.1.1 |
| name_zib | Procedure |
| path_xtehr | EHDSProcedure |
| path_zib | Procedure |
| short_xtehr | Procedure model |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSProcedure.anatomicLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.anatomicLocation |
| zib | Procedure.ProcedureAnatomicalLocation::AnatomicalLocation |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-O-3'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Anatomic location and laterality where the procedure was performed. This is the target site. |
| definition_zib | Anatomical location that is the focus of the procedure. |
| definitioncode_zib | 405813007 Procedure site - Direct |
| id_xtehr | EHDSProcedure.anatomicLocation |
| id_zib | NL-CM:14.1.13 |
| name_zib | ProcedureAnatomicalLocation::AnatomicalLocation |
| path_xtehr | EHDSProcedure.anatomicLocation |
| path_zib | Procedure.ProcedureAnatomicalLocation::AnatomicalLocation |
| short_xtehr | C.16.6 - Anatomic location |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.code |
| zib | Procedure.ProcedureType |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Code identifying the procedure |
| definition_zib | The name of the procedure |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.code |
| id_zib | NL-CM:14.1.4 |
| name_zib |  |
| path_xtehr | EHDSProcedure.code |
| path_zib |  |
| short_xtehr | C.16.3 - Code |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
Zib Procedure.Proceduretype defines the following value sets, in which the choices are as follows: the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG). Of all these valuesets the ProcedureMethodCodelist (SNOMED < 129264002), the ProcedureTypeGGZcodelist (SNOMED Ref set ^140741000146104)  and the ProcedureTypeMaternityCareCodelist (SNOMED CT ^146481000146103) is in SNOMED CT. The zib 2024 describes EHDSprocedure.code as a type, which conveys the name of the procedure. The zib furthermore has a cardinality of 1, which means the element is required to be filled. 


## EHDSProcedure.complication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.complication |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10*, SNOMED CT, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Any complications that occurred during the procedure, or in the immediate post-performance period. These are generally tracked separately from the procedure description, which will typically describe the procedure itself rather than any 'post procedure' issues. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.complication |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.complication |
| path_zib |  |
| short_xtehr | C.16.9 - Complication |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

The Zib Diagnosis contains amongst others information element IsComplication. It Indicates whether or not the diagnosis involves a complication. This is however not related to specific complications occured during the procedure. Hence, there is no zib which accurately describes a complication which occurs during a specific intervention/procedure. 


## EHDSProcedure.date[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.date[x] |
| zib | Procedure.ProcedureEndDate |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the procedure or interval of its performance |
| definition_zib | The end date (and if possible end time) of the procedure. A ‘vague’ date, such as only the year, is permitted.
The element offers the option to indicate the end of the period of a series of related procedures. The end date element is only used for a procedures that takes some time and is then always applied. If the procedure still continues, the value is left empty. For instantaneous or very short lasting procedures the element is omitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.date[x] |
| id_zib | NL-CM:14.1.3 |
| name_zib | ProcedureEndDate |
| path_xtehr | EHDSProcedure.date[x] |
| path_zib | Procedure.ProcedureEndDate |
| short_xtehr | C.16.4 - Date |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Xt EHR and Zib seem to match. According to FHIR datatypes, date consists of two components: datetime and period. Datetime entails a date, date-time or partial date (e.g. just year or year + month) as used in human communication. The format is YYYY, YYYY-MM, YYYY-MM-DD or YYYY-MM-DDThh:mm:ss+zz:zz, e.g. 2018, 1973-06, 1905-08-23, 2015-02-07T13:28:17-05:00 or 2017-01-01T00:00:00.000Z. Period according to FHIR entails a time range defined by start and end date/time
+ Rule: If present, start SHALL have a lower or equal value than end

## EHDSProcedure.date[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.date[x] |
| zib | Procedure.ProcedureStartDate |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of the procedure or interval of its performance |
| definition_zib | The (desired) start date (and if possible start time) of the procedure. A ‘vague’ date, such as only the year, is permitted.
The element offers the option to indicate the start of the period of a series of related procedures. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.date[x] |
| id_zib | NL-CM:14.1.2 |
| name_zib | ProcedureStartDate |
| path_xtehr | EHDSProcedure.date[x] |
| path_zib | Procedure.ProcedureStartDate |
| short_xtehr | C.16.4 - Date |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Xt EHR and Zib seem to match. According to FHIR, date consists of two components: datetime and period. Datetime entails a date, date-time or partial date (e.g. just year or year + month) as used in human communication. The format is YYYY, YYYY-MM, YYYY-MM-DD or YYYY-MM-DDThh:mm:ss+zz:zz, e.g. 2018, 1973-06, 1905-08-23, 2015-02-07T13:28:17-05:00 or 2017-01-01T00:00:00.000Z. Period according to FHIR entails a time range defined by start and end date/time
+ Rule: If present, start SHALL have a lower or equal value than end

## EHDSProcedure.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.description |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Procedure specification in string form |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.description |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.description |
| path_zib |  |
| short_xtehr | C.16.2 - Description |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSProcedure.deviceUsed

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.deviceUsed |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Device used to perform the procedure |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.deviceUsed |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.deviceUsed |
| path_zib |  |
| short_xtehr | C.16.10 - Device used |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments

In the information model Zib Procedure, a reference is made to zib MedicalDevice. The product, the placing of which in or on the body is the purpose of the procedure, for example placing an implant. The cardinality of MedicalDevice is 0..*. 

## EHDSProcedure.focalDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.focalDevice |
| zib | Procedure.MedicalDevice |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Device or devices that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| definition_zib | The medical device (internally or externally). |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.focalDevice |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.focalDevice |
| path_zib |  |
| short_xtehr | C.16.11 - Focal device |
| type_xtehr | Reference |
| type_zib |  |

### Comments

There is a distinct difference between the zib and xt ehr definition in its meaning. The MedicalDevice-v5.0 information model from the Dutch "Zorginformatiebouwstenen" (ZIB) defines medical devices more broadly. It encompasses any internally implanted or external devices and aids used by the patient, either currently or in the past, to:
1. Reduce the effects of functional limitations in organ systems
2. Facilitate the treatment of a disease
This includes devices like wheelchairs, hearing aids, or prosthetic limbs, regardless of whether they are the focus of a current medical procedure.

The xt ehr definition of focal device defines medical devices as devices that are the primary focus of a medical procedure. 


## EHDSProcedure.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.identifier |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Procedure identifier |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.identifier |
| path_zib |  |
| short_xtehr | C.16.1 - Identifier |
| type_xtehr | Identifier |
| type_zib |  |

### Comments

Zib doesn't contain element Procedure.Identifier. Instead, the Zib identifies Procedure.Type. That defines the specific name of the procedure: 	The name of the procedure.
That is not the same as an identifier. Hence there is a small difference. The Zib Procedure.Type defines it as: The name of the procedure.
Choices are the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG).


## EHDSProcedure.location

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.location |
| zib | Procedure.Location::HealthcareProvider |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Location where the procedure had been performed |
| definition_zib | The healthcare provider where the procedure was, is or will be carried out. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.location |
| id_zib | NL-CM:14.1.5 |
| name_zib | Location::HealthcareProvider |
| path_xtehr | EHDSProcedure.location |
| path_zib | Procedure.Location::HealthcareProvider |
| short_xtehr | C.16.12 - Location |
| type_xtehr | EHDSLocation |
| type_zib |  |

### Comments

See reference zib HealthCare.Provider. Under this you can see data element OrganizationLocation, which is divided in two other data elements: LocationName and LocationNumber. LocationName refers to the 
Name of the location, in case a healthcare organization has more than one location.
Locationnumber refers to the Number of the location Number, if a numerical location identification is used next to or instead of a location name.

## EHDSProcedure.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.note |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Additional information about the procedure |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.note |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.note |
| path_zib |  |
| short_xtehr | C.16.13 - Note |
| type_xtehr | string |
| type_zib |  |

### Comments

Normally any additional information is being added in the 'toelichting' field, which most zibs have. 

## EHDSProcedure.outcome

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.outcome |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The outcome of the procedure - did it resolve the reasons for the procedure being performed? |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.outcome |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.outcome |
| path_zib |  |
| short_xtehr | C.16.8 - Outcome |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

There is no data element under procedure, which specifically refers to the outcome of the procedure performed. There is a Zib 2024 which specifically focuses on the OutcomeOfCare in general: Zib OutcomeOfCare, hence not related to a specific intervention/procedure. Under Zib OutcomeofCare there are two sub data elements: HealthcareResult and HealthCondition The sub data element HealthcareResul defines the concept as follows: The textual account of the healthcare result. If HealthcareResult cannot be entered as a functional/mental status, it can be described as free text in the healthcare result.


## EHDSProcedure.performer

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.performer |
| zib | Procedure.Performer::HealthProfessional |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | An actor who or what performed the procedure |
| definition_zib | The healthcare professional who carried out or will carry out the procedure. In most cases, only the medical specialty is entered, and not the name of the healthcare professional. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.performer |
| id_zib | NL-CM:14.1.6 |
| name_zib | Performer::HealthProfessional |
| path_xtehr | EHDSProcedure.performer |
| path_zib | Procedure.Performer::HealthProfessional |
| short_xtehr | C.16.5 - Performer |
| type_xtehr | Reference |
| type_zib |  |

### Comments

Seems like a match. Good to note that zib Procedure.Performer:: Healthprofessional is a reference zib. It refers to the zib Healthprofessional. Which distinguishes between Healthprofessional:Specialty, HealthProfessional:Gender, HealthprofessionalRole, HealthprofessionalIdentificationnumber. 
Related to sub data element Healthprofessional: Specality, it uses two codelists: https://www.zibs.nl/wiki/HealthProfessional-v4.0.1(2024EN)#SpecialtyAGBCodelist and https://www.zibs.nl/wiki/HealthProfessional-v4.0.1(2024EN)#SpecialtyUZICodelist. Under a HealthcareProfessionals speciality is intended: the Health professional’s medical specialty. This refers to the recognized medical specialties as stated in the BIG Act. For example general practitioner or cardiologist.

Hence two mainly Dutch codelists, not based on SNOMED: 
COD016-VEKT (Vektis AGB-medische specialismen)
RoleCodeNL (Zorgverlenertype (personen))

## EHDSProcedure.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason |
| zib | Procedure.Indication |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | The reason why the procedure was performed. |
| definition_zib | Container of the Indication concept.This container contains all data elements of the Indication concept. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason |
| id_zib | NL-CM:14.1.14 |
| name_zib | Indication |
| path_xtehr | EHDSProcedure.reason |
| path_zib | Procedure.Indication |
| short_xtehr | C.16.7 - Reason |
| type_xtehr | Reference |
| type_zib |  |

### Comments

The definition between xtehr and zib is a bit different. Xtehr refers specifically to the reason why a procedure has been performed. the zib indication is divided in three sub elements: diagnosis, reaction, symptom. 
The diagnosis could be interpreted as the reason why a procedure should be performed to a patient, or a specific symptom could also be the direct consequence for undergoing treatment. 

## EHDSProcedure.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason |
| zib | Procedure.Indication.Diagnosis |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. |
| definition_zib | A diagnosis that serves as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason |
| id_zib | NL-CM:14.1.15 |
| name_zib | Diagnosis |
| path_xtehr | EHDSProcedure.reason |
| path_zib | Procedure.Indication.Diagnosis |
| short_xtehr | C.16.7 - Reason |
| type_xtehr | Reference |
| type_zib |  |

### Comments

Hence the difference with the xtehr is that the zib makes the reason behind the intervention/procedure more specific: wether it is the direct result of a symptom, or a new diagnosis or a specific reaction the patient has.
xtehr keeps it with its formulation very general: the reason, which is free to be filled in with a textual description. 
## EHDSProcedure.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason |
| zib | Procedure.Indication.Reaction |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. |
| definition_zib | An undesired reaction to a substance or radiation that served as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason |
| id_zib | NL-CM:14.1.16 |
| name_zib | Reaction |
| path_xtehr | EHDSProcedure.reason |
| path_zib | Procedure.Indication.Reaction |
| short_xtehr | C.16.7 - Reason |
| type_xtehr | Reference |
| type_zib |  |

### Comments

Hence the difference with the xtehr is that the zib makes the reason behind the intervention/procedure more specific: wether it is the direct result of a symptom, or a new diagnosis or a specific reaction the patient has.
xtehr keeps it with its formulation very general: the reason, which is free to be filled in with a textual description. 

## EHDSProcedure.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason |
| zib | Procedure.Indication.Symptom |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. |
| definition_zib | A symptom that serves as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason |
| id_zib | NL-CM:14.1.17 |
| name_zib | Symptom |
| path_xtehr | EHDSProcedure.reason |
| path_zib | Procedure.Indication.Symptom |
| short_xtehr | C.16.7 - Reason |
| type_xtehr | Reference |
| type_zib |  |

### Comments

Hence the difference with the xtehr is that the zib makes the reason behind the intervention/procedure more specific: wether it is the direct result of a symptom, or a new diagnosis or a specific reaction the patient has.
xtehr keeps it with its formulation very general: the reason, which is free to be filled in with a textual description. 

## EHDSProcedure.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason |
| zib | Procedure.Indication::Problem |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The reason why the procedure was performed. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.reason |
| path_zib |  |
| short_xtehr | C.16.7 - Reason |
| type_xtehr | Reference |
| type_zib |  |

### Comments

The sub element procedure.Indication: problem has become invalid and has been replaced by the zib indication: symptom, reaction, diagnosis. Please dubbelcheck the statement and whether the zib problem has become definitely invalid. 

## EHDSProcedure.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.subject |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | On whom or on what the procedure was performed. This is usually an individual human, but can also be performed on animals, groups of humans or animals, organizations or practitioners (for licensing), locations or devices (for safety inspections or regulatory authorizations). If the actual focus of the procedure is different from the subject, the focus element specifies the actual focus of the procedure. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.subject |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.subject |
| path_zib |  |
| short_xtehr | C.16.14 - Patient |
| type_xtehr | Reference |
| type_zib |  |

### Comments

This data sub element of procedure can be filled up with the zib Subject. Hence the direct patient on which the procedure has been performed. Under the zib Procedure, there is no data sub element referring to the patient. For this the zib he

## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..* |
| definition_xtehr |  |
| definition_zib | The product, the placing of which in or on the body is the purpose of the procedure, for example placing an implant. |
| definitioncode_zib | 405815000 Procedure device |
| id_xtehr |  |
| id_zib | NL-CM:14.1.7 |
| name_zib | MedicalDevice |
| path_xtehr |  |
| path_zib | Procedure.MedicalDevice.MedicalDevice |
| short_xtehr |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: Procedure.ProcedureMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Procedure.ProcedureMethod |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib |  |
| definition_xtehr |  |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib |  |
| name_zib |  |
| path_xtehr |  |
| path_zib |  |
| short_xtehr |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..* |
| definition_xtehr |  |
| definition_zib | The method or technique that is going to be or was used to perform the procedure, e.g. approach, lavage, pressuring, etc. |
| definitioncode_zib | 260686004 Method |
| id_xtehr |  |
| id_zib | NL-CM:14.1.12 |
| name_zib | ProcedureMethod |
| path_xtehr |  |
| path_zib | Procedure.ProcedureMethod.ProcedureMethod |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | The name of the procedure.Choices are the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG). |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.1.4 |
| name_zib | ProcedureType |
| path_xtehr |  |
| path_zib | Procedure.ProcedureType.ProcedureType |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: Procedure.Requester::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Procedure.Requester::HealthProfessional |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib |  |
| definition_xtehr |  |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib |  |
| name_zib |  |
| path_xtehr |  |
| path_zib |  |
| short_xtehr |  |
| type_xtehr |  |
| type_zib |  |

### Comments

