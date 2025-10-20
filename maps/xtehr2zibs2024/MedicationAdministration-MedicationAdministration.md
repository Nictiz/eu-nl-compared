# MedicationAdministration

| zib                                                                          | xtehr                                                    | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-----------------------------------------------------------------------------|:---------------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| MedicationAdministration                                                     | EHDSMedicationAdministration                             |            |                        |             | 0..*          |
|                                                                              | EHDSMedicationAdministration.header                      |            | Base                   |             | 1..1          |
|                                                                              | EHDSMedicationAdministration.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                                              | EHDSMedicationAdministration.header.identifier           |            | Identifier             |             | 0..*          |
|                                                                              | EHDSMedicationAdministration.header.authorship           |            | Base                   |             | 1..*          |
|                                                                              | EHDSMedicationAdministration.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                                              | EHDSMedicationAdministration.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                                              | EHDSMedicationAdministration.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                                              | EHDSMedicationAdministration.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                                              | EHDSMedicationAdministration.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                                              | EHDSMedicationAdministration.header.language             |            | CodeableConcept        |             | 0..1          |
| MedicationAdministration.AdministrationProduct::PharmaceuticalProduct        | EHDSMedicationAdministration.medication                  |            | EHDSMedication         | 1           | 1..1          |
| MedicationAdministration.AdministrationDateTime                              | EHDSMedicationAdministration.occurrence[x]               | TS         | dateTime               | 1           | 1..1          |
|                                                                              | EHDSMedicationAdministration.reason[x]                   |            | CodeableConcept        |             | 0..*          |
| MedicationAdministration.Comment                                             | EHDSMedicationAdministration.note                        | ST         | string                 | 0..1        | 0..1          |
|                                                                              | EHDSMedicationAdministration.dosage                      |            | EHDSDosage             |             | 0..1          |
| MedicationAdministration.AdministeringSpeed                                  |                                                          | PQ         |                        | 0..1        |               |
| MedicationAdministration.AdministeredAmount                                  |                                                          | PQ         |                        | 0..1        |               |
| MedicationAdministration.RouteOfAdministration                               |                                                          | CD         |                        | 1           |               |
| MedicationAdministration.AdministrationLocation::AnatomicalLocation          |                                                          |            |                        | 0..1        |               |
| MedicationAdministration.AdministrationLocation::AnatomicalLocation.Location |                                                          | CD         |                        |             |               |
| MedicationAdministration.Administrator                                       |                                                          |            |                        | 0..1        |               |
| MedicationAdministration.Administrator.Patient                               |                                                          |            |                        | (0..1)      |               |
| MedicationAdministration.Administrator.HealthProfessional                    |                                                          |            |                        | (0..1)      |               |
| MedicationAdministration.Administrator.Caregiver::Contact                    |                                                          |            |                        | (0..1)      |               |
| MedicationAdministration.MedicationAdministrationReasonForDeviation          |                                                          | CD         |                        | 0..1        |               |



## EHDSMedicationAdministration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration |
| zib | MedicationAdministration |
| alias_zib | NL: Medicatietoediening |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for a single medication administration |
| definition_zib | Root concept of the MedicationAdministration information model. This root concept contains all data elements of the MedicationAdministration information model. |
| definitioncode_zib | SNOMED CT: 18629005 Administration of medication |
| id_xtehr | EHDSMedicationAdministration |
| id_zib | NL-CM:9.13.20928 |
| name_zib | MedicationAdministration |
| path_xtehr | EHDSMedicationAdministration |
| path_zib | MedicationAdministration |
| short_xtehr | Medication administration model |
| stereotype_zib | rootconcept |

### Comments



## EHDSMedicationAdministration.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSMedicationAdministration.header |
| path_xtehr | EHDSMedicationAdministration.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSMedicationAdministration.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSMedicationAdministration.header.subject |
| path_xtehr | EHDSMedicationAdministration.header.subject |
| short_xtehr | Patient/subject information |
| type_xtehr | EHDSPatient |

### Comments



## EHDSMedicationAdministration.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSMedicationAdministration.header.identifier |
| path_xtehr | EHDSMedicationAdministration.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSMedicationAdministration.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSMedicationAdministration.header.authorship |
| path_xtehr | EHDSMedicationAdministration.header.authorship |
| short_xtehr | Resource authoring details |
| type_xtehr | Base |

### Comments



## EHDSMedicationAdministration.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSMedicationAdministration.header.authorship.author[x] |
| path_xtehr | EHDSMedicationAdministration.header.authorship.author[x] |
| short_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSMedicationAdministration.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of authoring/issuing |
| id_xtehr | EHDSMedicationAdministration.header.authorship.datetime |
| path_xtehr | EHDSMedicationAdministration.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationAdministration.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| id_xtehr | EHDSMedicationAdministration.header.lastUpdate |
| path_xtehr | EHDSMedicationAdministration.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| type_xtehr | dateTime |

### Comments



## EHDSMedicationAdministration.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.status |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 MedicationAdimnistrationStatusCodes'} |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource or document |
| id_xtehr | EHDSMedicationAdministration.header.status |
| path_xtehr | EHDSMedicationAdministration.header.status |
| short_xtehr | Status of the administration (e.g. completed, not-done, on-hold, in-progress, unknown) |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationAdministration.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.statusReason[x] |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSMedicationAdministration.header.statusReason[x] |
| path_xtehr | EHDSMedicationAdministration.header.statusReason[x] |
| short_xtehr | Reason administration was not performed |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationAdministration.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSMedicationAdministration.header.language |
| path_xtehr | EHDSMedicationAdministration.header.language |
| short_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationAdministration.medication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.medication |
| zib | MedicationAdministration.AdministrationProduct::PharmaceuticalProduct |
| alias_zib | NL: ToedieningsProduct::FarmaceutischProduct |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Administered medication |
| definition_zib | The product taken or administered. This is usually medication. Food, blood products, aids and bandages do not strictly fall under the category of medication, but can be reported as well.  <br><br>In principle, this will be the prescribed product, but the administrator may substitute it by replacing the product with an equivalent product. For example: two 50mg tablets can be administered instead of one 100mg tablet. |
| id_xtehr | EHDSMedicationAdministration.medication |
| id_zib | NL-CM:9.13.20929 |
| name_zib | AdministrationProduct::PharmaceuticalProduct |
| path_xtehr | EHDSMedicationAdministration.medication |
| path_zib | MedicationAdministration.AdministrationProduct::PharmaceuticalProduct |
| short_xtehr | Administered medication |
| stereotype_zib | data,reference |
| type_xtehr | EHDSMedication |

### Comments



## EHDSMedicationAdministration.occurrence[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.occurrence[x] |
| zib | MedicationAdministration.AdministrationDateTime |
| alias_zib | NL: ToedieningsDatumTijd |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Specific date/time or interval of time during which the administration took place (or did not take place) |
| definition_zib | The date and time at which the medication was administered. |
| id_xtehr | EHDSMedicationAdministration.occurrence[x] |
| id_zib | NL-CM:9.13.21193 |
| name_zib | AdministrationDateTime |
| path_xtehr | EHDSMedicationAdministration.occurrence[x] |
| path_zib | MedicationAdministration.AdministrationDateTime |
| short_xtehr | Specific date/time or interval of time during which the administration took place (or did not take place) |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSMedicationAdministration.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.reason[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Condition or observation that supports why the medication was administered |
| id_xtehr | EHDSMedicationAdministration.reason[x] |
| path_xtehr | EHDSMedicationAdministration.reason[x] |
| short_xtehr | Condition or observation that supports why the medication was administered |
| type_xtehr | CodeableConcept |

### Comments



## EHDSMedicationAdministration.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.note |
| zib | MedicationAdministration.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual information about the administration |
| definition_zib | Comments on administering the medication. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSMedicationAdministration.note |
| id_zib | NL-CM:9.13.21337 |
| name_zib | Comment |
| path_xtehr | EHDSMedicationAdministration.note |
| path_zib | MedicationAdministration.Comment |
| short_xtehr | Textual information about the administration |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSMedicationAdministration.dosage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationAdministration.dosage |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Details of how medication was taken |
| id_xtehr | EHDSMedicationAdministration.dosage |
| path_xtehr | EHDSMedicationAdministration.dosage |
| short_xtehr | Details of how medication was taken |
| type_xtehr | EHDSDosage |

### Comments



## zib: MedicationAdministration.AdministeringSpeed

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.AdministeringSpeed |
| alias_zib | NL: Toedieningssnelheid |
| card._zib | 0..1 |
| definition_zib | The administering speed is used in slow administration of liquid. In practice, the measuring unit is almost always ml/hour. <br>Entering an interval (such as 0-10 ml/hour) is also a commonly used option. <br><br>For example, with an administering speed of 10ml/hour: <br>-  amount = 10,<br>-  dose unit = ml<br>-  time unit = hour<br>Optionally a translation to NHG table Gebruiksvoorschriften(Table 25) is also allowed. |
| id_zib | NL-CM:9.13.23159 |
| name_zib | AdministeringSpeed |
| path_zib | MedicationAdministration.AdministeringSpeed |
| stereotype_zib | data |
| type_zib | PQ |

### Comments



## zib: MedicationAdministration.AdministeredAmount

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.AdministeredAmount |
| alias_zib | NL: ToegediendeHoeveelheid |
| card._zib | 0..1 |
| definition_zib | Amount of the administered product. |
| id_zib | NL-CM:9.13.21194 |
| name_zib | AdministeredAmount |
| path_zib | MedicationAdministration.AdministeredAmount |
| stereotype_zib | data |
| type_zib | PQ |

### Comments



## zib: MedicationAdministration.RouteOfAdministration

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.RouteOfAdministration |
| alias_zib | NL: Toedieningsweg |
| card._zib | 1 |
| definition_zib | The route through which the medication is administered (oral, nasal, intravenous,...). |
| definitioncode_zib | SNOMED CT: 410675002 Route of administration |
| id_zib | NL-CM:9.13.21195 |
| name_zib | RouteOfAdministration |
| path_zib | MedicationAdministration.RouteOfAdministration |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: MedicationAdministration.AdministrationLocation::AnatomicalLocation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.AdministrationLocation::AnatomicalLocation |
| alias_zib | NL: Toedienlocatie::AnatomischeLocatie |
| card._zib | 0..1 |
| definition_zib | Location on or in the body where the medication was administered. Usually used to indicate the location at which a patient was administered an injection or patch was applied. The value list PrikPlakLocationCodelijst list can serve as a starting point for coding these concepts. If both the anatomical location and administration route are filled, they should be aligned. |
| id_zib | NL-CM:9.13.23381 |
| name_zib | AdministrationLocation::AnatomicalLocation |
| path_zib | MedicationAdministration.AdministrationLocation::AnatomicalLocation |
| stereotype_zib | data,reference |

### Comments



## zib: MedicationAdministration.AdministrationLocation::AnatomicalLocation.Location

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.AdministrationLocation::AnatomicalLocation.Location |
| alias_zib | NL: Locatie |
| definition_zib | Location from AnatomicalLocation. |
| id_zib | NL-CM:20.7.4 |
| name_zib | Location |
| path_zib | MedicationAdministration.AdministrationLocation::AnatomicalLocation.Location |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: MedicationAdministration.Administrator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.Administrator |
| alias_zib | NL: Toediener |
| card._zib | 0..1 |
| definition_zib | Container of the Administrator concept. This container contains all data elements of the Administrator concept. The concept describes the person who administered the product. This is a professional authorised administrator, the patient themselves or the caregiver, for example. |
| id_zib | NL-CM:9.13.21196 |
| name_zib | Administrator |
| path_zib | MedicationAdministration.Administrator |
| stereotype_zib | container |

### Comments



## zib: MedicationAdministration.Administrator.Patient

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.Administrator.Patient |
| alias_zib | NL: Patiënt |
| card._zib | (0..1) |
| definition_zib | If the patient administered the medication themselves, indicate that here. If the medication is administered by a health professional or caregiver/family member/etc., the health professional is entered in the 'HealthProfessional' element or the caregiver/family member/etc. is entered in the 'Contact' element respectively. |
| id_zib | NL-CM:9.13.23380 |
| name_zib | Patient |
| path_zib | MedicationAdministration.Administrator.Patient |
| stereotype_zib | context,reference |

### Comments



## zib: MedicationAdministration.Administrator.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.Administrator.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| card._zib | (0..1) |
| definition_zib | The concept describes the person who administered the product. This is a professional authorised administrator. |
| id_zib | NL-CM:9.13.23172 |
| name_zib | HealthProfessional |
| path_zib | MedicationAdministration.Administrator.HealthProfessional |
| stereotype_zib | context,reference |

### Comments



## zib: MedicationAdministration.Administrator.Caregiver::Contact

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.Administrator.Caregiver::Contact |
| alias_zib | NL: Mantelzorger::Contactpersoon |
| card._zib | (0..1) |
| definition_zib | Information on the patient’s personal relative or contact that administered the medication. |
| id_zib | NL-CM:9.13.23355 |
| name_zib | Caregiver::Contact |
| path_zib | MedicationAdministration.Administrator.Caregiver::Contact |
| stereotype_zib | context,reference |

### Comments



## zib: MedicationAdministration.MedicationAdministrationReasonForDeviation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationAdministration.MedicationAdministrationReasonForDeviation |
| alias_zib | NL: MedicatietoedieningRedenVanAfwijken |
| card._zib | 0..1 |
| definition_zib | Reason why the medication was not taken or administered or was taken or administered differently. Here, you can choose to enter text or one of the codes. |
| definitioncode_zib | SNOMED CT: 153631000146105 Reason for deviation in administration of drug or medicament |
| id_zib | NL-CM:9.13.23166 |
| name_zib | MedicationAdministrationReasonForDeviation |
| path_zib | MedicationAdministration.MedicationAdministrationReasonForDeviation |
| stereotype_zib | data |
| type_zib | CD |

### Comments

