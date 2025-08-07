# Procedure as of 8-7-2025

## Version history

v1: 27-05-2025, initial version

v2: 8-7-2025

- EHDSProcedure now uses "EHDSDataset" with metadata (common to more EHDS models)
- some texts have changed (numbers deleted and other minor changes)
- anatomicLocation (CodeableConcept) is replaced with submodel bodySite
- description is gone, presentedForm is part of EHDSDataSet

## Discussion

What is missing in the Xtehr and present in zib 2024? 

* zib: Procedure.ProcedureMethod
* zib: Procedure.ProcedureType

What is missing in the zib 2024 and is present in the Xtehr dataset: 

* EHDSProcedure.complication
* EHDSProcedure.description
* EHDSProcedure.identifier
* EHDSProcedure.note
* EHDSProcedure.outcome
* EHDSProcedure.subject.

Regarding the latter. Some text seem to be missing. The subject is not defined in this dataset.

It can be noted that the zib procedure has a scope of a "therapeutic or diagnostic procedure undergone by the patient or which the patient will undergo", so past en future use (and presumably present use as well). The scope of the Xt-EHR is "An action that is or was performed on or for a patient", so only past and present use. So the zib has future use in scope while Xt-EHR has not.
In addition, Xt-EHR doesn't have the restriction on therapeutic or diagnostic procedures, so it _might_ have a broader scope - e.g. an action could also be an freedom restricting intervention, which is not a Procedure according to the zib. I'm not sure about this though

Regarding EHDSProcedure.reason: there seems to be quite a mismatch on terminology and interpretation: The definition between xtehr and zib is a bit different. Xtehr refers specifically to the reason why a procedure has been performed. the zib indication is divided in three sub elements: diagnosis, reaction, symptom. The diagnosis could be interpreted as the reason why a procedure should be performed on a patient, or a specific symptom could also be the direct consequence for undergoing treatment. At the moment it is hard to tell since the zib condition is quite complex. The xt ehr seems to be much more simplistic: textually defining the reason behind intervention. 

Regarding EHDSProcedure.performer an additional analysis should be made between EHDSHealthProfessional and zib HealthProfessional. An extra subtask has been created. 

Regarding EHDSProcedure.outcome. ZibOutcomeOfCare is not relevant for the procedure zib, but it is relevant for the NursingIntervention zib, which should also be compared to EHDSProcedure. An additional subtask needs to be added for this specific  mapping. 

Regarding EHDSProcedure.location. An analysis should be made between EHDSLocation and Zib HealthcareProvider. The conceptual match is on HealthcareProvider.  

Regarding EHDSProcedure.identifier. this doesn’t align with Procedure.Type; the identifier is about identifying this specific procedure, while type is about the kind of procedure. There is probably a match with zib RegistrationData.Identifier, but that has a more restricted cardinality.


Regarding EHDSProcedure.focalDevice: the zib and the Xt-EHR model do match up nicely here. Both are about the device that was the “focal device” of the procedure: “Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure” according to Xt-EHR, or “The product, the placing of which in or on the body is the purpose of the procedure, for example placing an implant” according to the zib.It is true that there are mismatches in the MedicalDevice model itself between the zib and Xt-EHR, but for this specific context, they mean the same.

Regarding EHDSProcedure.deviceUsed: this element has no equivalent in the zib (although it has one in zib NursingIntervention); this is about devices used in order to perform the procedure, and not about the device that was implanted or manipulated during the procedure … think bandages and such

Regarding EHDSProcedure.description: this element is gone in the current build.

Regarding date[x]: It’s not quite true that date consists of the components: datetime and period; “date[x]” means it can be either a dateTime or a Period.
The mapping between zib and Xt-EHR is not straightforward and touches both ProcedureStartDate and ProcedureEndDate.
The meaning of the Xt-EHR model is that date can be:
- an “instantaneous” procedure in the past (because of the scope)
- a procedure that took time, in the past
- an ongoing procedure that has started but not yet ended

The meaning of the zib is that the procedure can be:
- an “instantaneous” procedure in the past (only ProcedureStartDate present and in the past)
-an “instantaneous” procedure in the future (only ProcedureStartDate present and in the future)
- a procedure that took time, in the past (ProcedureStartDate and ProcedureEndDate present and in the past)
- an ongoing procedure that has started but not yet ended (ProcedureStartDate in the past, ProcedureEndDate present but “left empty”)
- a procedure that will take time, in the future (ProcedureStartDate in the future, ProcedureEndDate present but “left empty”)
- a series of procedures that has completed (ProcedureStartDate and ProcedureEndDate in the past, presumably a ProcedureType that indicates that this is a series)
- a series of procedures that is ongoing (ProcedureStartDate in the past, ProcedureEndDate present but “left empty”, and presumably a ProcedureType that indicates that this is a series)
- a series of procedures that is will start in the future (ProcedureStartDate in the future, ProcedureEndDate present but “left empty”, and presumably a ProcedureType that indicates that this is a series)

So the zib relies on different heuristics to alter the meaning of the concepts ProcedureStartDate and ProcedureEndDate and has a mismatch in data types. There is no one-to-one mapping between the Xt-EHR model and the zib, although the meaning of the two models seem to align.


Regarding EHDSProcedure.complication: I do think zib Diagnosis matches this element, as zib Diagnosis has a Reason element which can be a reference to zib Procedure. However, the mapping is problematic as zib Diagnosis requires a lot of information that is not present in the simple list of “complications that arose during the procedure” of Xt-EHR. Terminology wise, the Xt-EHR model has only a preferred binding. It hints as Orphacode as allowed code system, which is not present in the zib, (next to SNOMED and ICD-10, which are valid in the zib).


Regarding EHDSProcedure.code/Procedure.ProcedureType: the zib is more restrictive than XtEHR as it has required bindings to a range of different ValueSets, some of them SNOMED. The use of other code systems besides SNOMED doesn’t seem to be problematic as the XtEHR binding is only preferred.

As the zib is more restrictive, an instance for the will will alwaiys be valid for this element against the XtEHR model. An XtEHR instance however is not guaranteed to be valid against the zib, as the .code may be absent, use a terminology not valid in the zib, or define an action that is not a therapeutic or diagnostic procedure.

There is a  zib for patient, and there is also a reference zib for outcome, but it is not specifically connected to the Procedure zib. 
This zib exists:  UitkomstVanZorg-v3.3.1(2024NL) which could be used to describe a certain outcome of an intervention. 


| zib                                                       | xtehr                                     | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:----------------------------------------------------------|:------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Procedure                                                 | EHDSProcedure                             |            |                        |             | 0..*          |
| Procedure.ProcedureAnatomicalLocation::AnatomicalLocation | EHDSProcedure.bodySite                    |            | EHDSBodyStructure      | 0..1        | 0..*          |
| Procedure.ProcedureType                                   | EHDSProcedure.code                        | CD         | CodeableConcept        | 1           | 0..1          |
|                                                           | EHDSProcedure.complication                |            | CodeableConcept        |             | 0..*          |
| Procedure.ProcedureEndDate                                | EHDSProcedure.date[x]                     | TS         | dateTime               | 0..1        | 0..1          |
| Procedure.ProcedureStartDate                              | EHDSProcedure.date[x]                     | TS         | dateTime               | 0..1        | 0..1          |
|                                                           | EHDSProcedure.deviceUsed                  |            | EHDSDevice             |             | 0..*          |
| Procedure.MedicalDevice                                   | EHDSProcedure.focalDevice                 |            | EHDSDevice             | 0..*        | 0..*          |
| Registratiegegevens, zie DataSet mapping                  | EHDSProcedure.header                      |            | Base                   |             | 1..1          |
|                                                           | EHDSProcedure.header.authorship           |            | Base                   |             | 1..*          |
|                                                           | EHDSProcedure.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                           | EHDSProcedure.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                           | EHDSProcedure.header.identifier           |            | Identifier             |             | 0..*          |
|                                                           | EHDSProcedure.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                           | EHDSProcedure.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                           | EHDSProcedure.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                           | EHDSProcedure.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                           | EHDSProcedure.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                           | EHDSProcedure.header.version              |            | string                 |             | 0..1          |
| Procedure.Location::HealthcareProvider                    | EHDSProcedure.location                    |            |                        | 0..1        |               |
|                                                           | EHDSProcedure.note                        |            | string                 |             | 0..1          |
|                                                           | EHDSProcedure.outcome                     |            | CodeableConcept        |             | 0..1          |
| Procedure.Performer::HealthProfessional                   | EHDSProcedure.performer                   |            | EHDSHealthProfessional | 0..*        | 0..*          |
|                                                           | EHDSProcedure.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| Procedure.Indication                                      | EHDSProcedure.reason[x]                   |            | CodeableConcept        | 0..*        | 0..*          |
| Procedure.Indication.Diagnosis                            | EHDSProcedure.reason[x]                   |            | CodeableConcept        | (0..1)      | 0..*          |
| Procedure.Indication.Reaction                             | EHDSProcedure.reason[x]                   |            | CodeableConcept        | (0..1)      | 0..*          |
| Procedure.Indication.Symptom                              | EHDSProcedure.reason[x]                   |            | CodeableConcept        | (0..1)      | 0..*          |
| Procedure.Indication::Problem                             | EHDSProcedure.reason[x]                   |            | CodeableConcept        |             | 0..*          |
| Procedure.ProcedureMethod                                 |                                           | CD         |                        | 0..*        |               |
| Procedure.Requester::HealthProfessional                   |                                           |            |                        |             |               |



## EHDSProcedure

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure |
| zib | Procedure |
| alias_zib | NL: Verrichting |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for an action that is or was performed on or for a patient |
| definition_zib | Root concept of the Procedure information model. This root concept contains all data elements of the Procedure information model. |
| definitioncode_zib | SNOMED CT: 71388002 Procedure |
| id_xtehr | EHDSProcedure |
| id_zib | NL-CM:14.1.1 |
| name_zib | Procedure |
| path_xtehr | EHDSProcedure |
| path_zib | Procedure |
| short_xtehr | Procedure model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSProcedure.bodySite

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.bodySite |
| zib | Procedure.ProcedureAnatomicalLocation::AnatomicalLocation |
| alias_zib | NL: VerrichtingAnatomischeLocatie::AnatomischeLocatie |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Procedure target body site. Details of where the procedure was performed. Laterality may be included as qualifier of the body site. |
| definition_zib | Anatomical location that is the focus of the procedure. |
| definitioncode_zib | SNOMED CT: 405813007 Procedure site - Direct |
| id_xtehr | EHDSProcedure.bodySite |
| id_zib | NL-CM:14.1.13 |
| name_zib | ProcedureAnatomicalLocation::AnatomicalLocation |
| path_xtehr | EHDSProcedure.bodySite |
| path_zib | Procedure.ProcedureAnatomicalLocation::AnatomicalLocation |
| short_xtehr | Procedure target body site. Details of where the procedure was performed. Laterality may be included as qualifier of the body site. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSBodyStructure |
| type_zib |  |

### Comments

Previous comment re. anatomicLocation: Seems to match, although a different cardinality is being used. The zib uses specific SNOMED codelists. See for example: 2.16.840.1.113883.6.96 : https://www.zibs.nl/wiki/AnatomicalLocation-v1.0.4(2024EN)#LateralityCodelist. SNOMED CT based. 
And https://www.zibs.nl/wiki/AnatomicalLocation-v1.0.4(2024EN)#LocationCodelist. SNOMED CT based. 

anatomicLocation is now replaced with bodySite, we should compare the submodel.

## EHDSProcedure.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.code |
| zib | Procedure.ProcedureType |
| alias_zib | NL: VerrichtingType |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Code identifying the procedure |
| definition_zib | The name of the procedure.<br />Choices are the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG). |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.code |
| id_zib | NL-CM:14.1.4 |
| name_zib | ProcedureType |
| path_xtehr | EHDSProcedure.code |
| path_zib | Procedure.ProcedureType |
| short_xtehr | Code identifying the procedure |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments

Zib Procedure.Proceduretype defines the following value sets, in which the choices are as follows: the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG). Of all these valuesets the ProcedureMethodCodelist (SNOMED < 129264002), the ProcedureTypeGGZcodelist (SNOMED Ref set ^140741000146104)  and the ProcedureTypeMaternityCareCodelist (SNOMED CT ^146481000146103) is in SNOMED CT. The zib 2024 describes EHDSprocedure.code as a type, which conveys the name of the procedure. The zib furthermore has a cardinality of 1, which means the element is required to be filled. 

## EHDSProcedure.complication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.complication |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT, Orphacode if rare disease is diagnosed'} |
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
| short_xtehr | Any complications that occurred during the procedure, or in the immediate post-performance period. These are generally tracked separately from the procedure description, which will typically describe the procedure itself rather than any 'post procedure' issues. |
| stereotype_zib |  |
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
| alias_zib | NL: VerrichtingEindDatum |
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
| short_xtehr | Date and time of the procedure or interval of its performance |
| stereotype_zib | data |
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
| alias_zib | NL: VerrichtingStartDatum |
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
| short_xtehr | Date and time of the procedure or interval of its performance |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments

Xt EHR and Zib seem to match. According to FHIR, date consists of two components: datetime and period. Datetime entails a date, date-time or partial date (e.g. just year or year + month) as used in human communication. The format is YYYY, YYYY-MM, YYYY-MM-DD or YYYY-MM-DDThh:mm:ss+zz:zz, e.g. 2018, 1973-06, 1905-08-23, 2015-02-07T13:28:17-05:00 or 2017-01-01T00:00:00.000Z. Period according to FHIR entails a time range defined by start and end date/time
+ Rule: If present, start SHALL have a lower or equal value than end

## EHDSProcedure.deviceUsed

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.deviceUsed |
| zib |  |
| alias_zib |  |
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
| short_xtehr | Device used to perform the procedure |
| stereotype_zib |  |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments

In the information model Zib Procedure, a reference is made to zib MedicalDevice. The product, the placing of which in or on the body is the purpose of the procedure, for example placing an implant. The cardinality of MedicalDevice is 0..*. 
See tab medicaldevice comments for further explanation and comparison. 

## EHDSProcedure.focalDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.focalDevice |
| zib | Procedure.MedicalDevice |
| alias_zib | NL: MedischHulpmiddel |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| definition_zib | The product, the placing of which in or on the body is the purpose of the procedure, for example placing an implant. |
| definitioncode_zib | SNOMED CT: 405815000 Procedure device |
| id_xtehr | EHDSProcedure.focalDevice |
| id_zib | NL-CM:14.1.7 |
| name_zib | MedicalDevice |
| path_xtehr | EHDSProcedure.focalDevice |
| path_zib | Procedure.MedicalDevice |
| short_xtehr | Device(s) that is/are implanted, removed, or otherwise manipulated (calibration, battery replacement, fitting a prosthesis, attaching a wound-vac, etc.) as a focal portion of the Procedure. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments

There is a distinct difference between the zib and xt ehr definition in its meaning. The MedicalDevice-v5.0 information model from the Dutch "Zorginformatiebouwstenen" (ZIB) defines medical devices more broadly. It encompasses any internally implanted or external devices and aids used by the patient, either currently or in the past, to:
1. Reduce the effects of functional limitations in organ systems
2. Facilitate the treatment of a disease
This includes devices like wheelchairs, hearing aids, or prosthetic limbs, regardless of whether they are the focus of a current medical procedure.

The xt ehr definition of focal device defines medical devices as devices that are the primary focus of a medical procedure. 

## EHDSProcedure.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header |
| zib | Registratiegegevens, zie DataSet mapping |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Common header for all patient-related data |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header |
| path_zib |  |
| short_xtehr | Common header for all patient-related data |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSProcedure.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.authorship |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib |  |
| definition_xtehr | Resource authoring details |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.authorship |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.authorship |
| path_zib |  |
| short_xtehr | Authorship |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSProcedure.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.authorship.author[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.authorship.author[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.authorship.author[x] |
| path_zib |  |
| short_xtehr | Author |
| stereotype_zib |  |
| type_xtehr | EHDSHealthProfessional |
| type_zib |  |

### Comments



## EHDSProcedure.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.authorship.datetime |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.authorship.datetime |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.authorship.datetime |
| path_zib |  |
| short_xtehr | Date and time of authoring/issuing |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSProcedure.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.identifier |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Business identifier for the object |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.identifier |
| path_zib |  |
| short_xtehr | Business identifier for the object |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments

Zib doesn't contain element Procedure.Identifier. Instead, the Zib identifies Procedure.Type. That defines the specific name of the procedure: 	The name of the procedure.
That is not the same as an identifier. Hence there is a small difference. The Zib Procedure.Type defines it as: The name of the procedure.
Choices are the DHD procedure thesaurus,  the procedures file (CBV), the Care activities file (NZa), the Dutch Mental Health and Addiction Care procedures list (GGZ) and the procedures list of the Dutch College of General Practitioners (NHG).

## EHDSProcedure.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.language |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.language |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.language |
| path_zib |  |
| short_xtehr | Language |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.lastUpdate |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Date and time of the last update to the document/information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.lastUpdate |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.lastUpdate |
| path_zib |  |
| short_xtehr | Date and time of the last update to the resource |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSProcedure.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.status |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Status of the resource |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.status |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.status |
| path_zib |  |
| short_xtehr | Status of the resource |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.statusReason[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Reason for the current status of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.statusReason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.statusReason[x] |
| path_zib |  |
| short_xtehr | Reason for the current status of the resource. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSProcedure.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.subject |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Patient/subject information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.subject |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.subject |
| path_zib |  |
| short_xtehr | Subject |
| stereotype_zib |  |
| type_xtehr | EHDSPatient |
| type_zib |  |

### Comments



## EHDSProcedure.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.header.version |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Business version of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.header.version |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.header.version |
| path_zib |  |
| short_xtehr | Version |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSProcedure.location

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.location |
| zib | Procedure.Location::HealthcareProvider |
| alias_zib | NL: Locatie::Zorgaanbieder |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The healthcare provider where the procedure was, is or will be carried out. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:14.1.5 |
| name_zib | Location::HealthcareProvider |
| path_xtehr |  |
| path_zib | Procedure.Location::HealthcareProvider |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
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
| alias_zib |  |
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
| short_xtehr | Additional information about the procedure |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments

Normally any additional information is being added in the 'toelichting' field, which most zibs have. Unclear whether zib procedure has this possibility

## EHDSProcedure.outcome

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.outcome |
| zib |  |
| alias_zib |  |
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
| short_xtehr | The outcome of the procedure - did it resolve the reasons for the procedure being performed? |
| stereotype_zib |  |
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
| alias_zib | NL: Uitvoerder::Zorgverlener |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | An actor who performed the procedure |
| definition_zib | The healthcare professional who carried out or will carry out the procedure. In most cases, only the medical specialty is entered, and not the name of the healthcare professional. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.performer |
| id_zib | NL-CM:14.1.6 |
| name_zib | Performer::HealthProfessional |
| path_xtehr | EHDSProcedure.performer |
| path_zib | Procedure.Performer::HealthProfessional |
| short_xtehr | An actor who performed the procedure |
| stereotype_zib | context,reference |
| type_xtehr | EHDSHealthProfessional |
| type_zib |  |

### Comments

Seems like a match. Good to note that zib Procedure.Performer:: Healthprofessional is a reference zib. It refers to the zib Healthprofessional. Which distinguishes between Healthprofessional:Specialty, HealthProfessional:Gender, HealthprofessionalRole, HealthprofessionalIdentificationnumber. 
Related to sub data element Healthprofessional: Specality, it uses two codelists: https://www.zibs.nl/wiki/HealthProfessional-v4.0.1(2024EN)#SpecialtyAGBCodelist and https://www.zibs.nl/wiki/HealthProfessional-v4.0.1(2024EN)#SpecialtyUZICodelist. Under a HealthcareProfessionals speciality is intended: the Health professional’s medical specialty. This refers to the recognized medical specialties as stated in the BIG Act. For example general practitioner or cardiologist.

Hence two mainly Dutch codelists, not based on SNOMED: 
COD016-VEKT (Vektis AGB-medische specialismen)
RoleCodeNL (Zorgverlenertype (personen))

## EHDSProcedure.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.presentedForm |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.presentedForm |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.presentedForm |
| path_zib |  |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| stereotype_zib |  |
| type_xtehr | EHDSAttachment |
| type_zib |  |

### Comments

This is a narrative for the entire Procedure which is missing in the zib (though may be present in FHIR)

## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | Procedure.Indication |
| alias_zib | NL: Indicatie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | Container of the Indication concept.This container contains all data elements of the Indication concept. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.14 |
| name_zib | Indication |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib | container |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

The definition between xtehr and zib is a bit different. Xtehr refers specifically to the reason why a procedure has been performed. the zib indication is divided in three sub elements: diagnosis, reaction, symptom. 
The diagnosis could be interpreted as the reason why a procedure should be performed to a patient, or a specific symptom could also be the direct consequence for undergoing treatment. 

## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | Procedure.Indication.Diagnosis |
| alias_zib | NL: Diagnose |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | A diagnosis that serves as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.15 |
| name_zib | Diagnosis |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication.Diagnosis |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

Hence the difference with the xtehr is that the zib makes the reason behind the intervention/procedure more specific: wether it is the direct result of a symptom, or a new diagnosis or a specific reaction the patient has.
xtehr keeps it with its formulation very general: the reason, which is free to be filled in with a textual description. 

## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | Procedure.Indication.Reaction |
| alias_zib | NL: Reactie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | An undesired reaction to a substance or radiation that served as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.16 |
| name_zib | Reaction |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication.Reaction |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

See above

## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | Procedure.Indication.Symptom |
| alias_zib | NL: Symptoom |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib | (0..1) |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib | A symptom that serves as an indication for the procedure. |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib | NL-CM:14.1.17 |
| name_zib | Symptom |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib | Procedure.Indication.Symptom |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

See above

## EHDSProcedure.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSProcedure.reason[x] |
| zib | Procedure.Indication::Problem |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ICD-10, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSProcedure.reason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSProcedure.reason[x] |
| path_zib |  |
| short_xtehr | The reason why the procedure was performed. This may be a concept from a terminology or a reference to a specific instance that describes the reason. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

The sub element procedure.Indication: problem has become invalid and has been replaced by the zib indication: symptom, reaction, diagnosis. Please dubbelcheck the statement and whether the zib problem has become definitely invalid. 

## zib: Procedure.ProcedureMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Procedure.ProcedureMethod |
| alias_zib | NL: VerrichtingMethode |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..* |
| definition_xtehr |  |
| definition_zib | The method or technique that is going to be or was used to perform the procedure, e.g. approach, lavage, pressuring, etc. |
| definitioncode_zib | SNOMED CT: 260686004 Method |
| id_xtehr |  |
| id_zib | NL-CM:14.1.12 |
| name_zib | ProcedureMethod |
| path_xtehr |  |
| path_zib | Procedure.ProcedureMethod |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments

From xt ehr there is no such construct as procedure method.

## zib: Procedure.Requester::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Procedure.Requester::HealthProfessional |
| alias_zib |  |
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
| stereotype_zib |  |
| type_xtehr |  |
| type_zib |  |

### Comments

There is no such thing as procedure requester in the EHDS logical model: Procedure model. This element could be part of the header information. This should be analyzed in further steps. 
