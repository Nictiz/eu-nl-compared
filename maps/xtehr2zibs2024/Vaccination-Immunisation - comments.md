# Immunisation as of 2025-09-12

## Version history

v1: 12-09-2025, initial version

## Actions

## Compared
### Scope
Scope matches they are both about vaccination (the process of getting immunized). Name of the EHDS concept is bit misleading.

The EHDS misses information about dosaging, a link to dossaging model is not present. The zib does present elements of dossaging. 

EHDS presents the nextVaccinationDate which is not present in the zib.

### Summary of partly matching elements

### Other

- The .header elements and .presentForm are skipped in this comparison (as they should map on more generic zib(s) like registration data).
- EHDS can have multiple target Agent or diseases (where the zib only has the primary pathogen).
- Binding Terminology in the zib only on SNOMED CT (5 concepts extensible, xtEHR also allows ICD-10).
- EHDS vaccine is missing in the zib, this could be represented in the Pharmaceutical product code. Multiple codes are allowed. 

## Discussions (16-09-2025:)# Vaccination
Consultatie: Sharper definition needed is this about vaccination or immunisation (Does it include passive and active immunisation)
Consultatie: Dossaging add as a non mandatory item (there is some discussion in NL). 
Consultatie: NextVaccinationDate under specified (should this be a different model, vaccinationScheme?). Possible model in fhir "ImmunizationRecommenation / Request". 
ZIBissue: Mogelijk 1..* maken van pathogen (en kijken naar hoe dit past binnen rijksvaccinatie programma). 
Consultatie: Please add examples and a better description for what vaccine is. And what is the value of this field?
Consultatie: Add a comment field to the model, for instance to describe deviating regimes.
Zib issue: Motive opnieuw beoordelen en/of bij scheiding vaccinatie / toediening.  


A workgroup EUvac is starting up (Nictiz is not participating yet), may impact future versions. 



| zib                                           | xtehr                                        | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:----------------------------------------------|:---------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Vaccination                                   | EHDSImmunisation                             |            |                        |             | 0..*          |
|                                               | EHDSImmunisation.header                      |            | Base                   |             | 1..1          |
|                                               | EHDSImmunisation.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                               | EHDSImmunisation.header.identifier           |            | Identifier             |             | 0..*          |
|                                               | EHDSImmunisation.header.authorship           |            | Base                   |             | 1..*          |
|                                               | EHDSImmunisation.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                               | EHDSImmunisation.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                               | EHDSImmunisation.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                               | EHDSImmunisation.header.status               |            | CodeableConcept        |             | 1..1          |
|                                               | EHDSImmunisation.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                               | EHDSImmunisation.header.language             |            | CodeableConcept        |             | 0..1          |
|                                               | EHDSImmunisation.header.version              |            | string                 |             | 0..1          |
|                                               | EHDSImmunisation.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| Vaccination.VaccinationPathogen               | EHDSImmunisation.diseaseOrAgentTargeted      | CD         | CodeableConcept        | 1           | 0..*          |
|                                               | EHDSImmunisation.vaccine                     |            | CodeableConcept        |             | 1..1          |
| Vaccination.PharmaceuticalProduct             | EHDSImmunisation.administeredProduct         |            | EHDSMedication         | 1           | 0..1          |
|                                               | EHDSImmunisation.doseNumber                  |            | integer                |             | 0..1          |
| Vaccination.VaccinationDateTime               | EHDSImmunisation.dateOfVaccination           | TS         | date                   | 1           | 1..1          |
| Vaccination.Location::HealthcareProvider      | EHDSImmunisation.administeringCentre         |            | EHDSOrganisation       | 1           | 0..*          |
| Vaccination.Administrator::Healthprofessional | EHDSImmunisation.vaccineAdministrator        |            | EHDSHealthProfessional | 1           | 0..*          |
|                                               | EHDSImmunisation.nextVaccinationDate         |            | date                   |             | 0..1          |
| Vaccination.AnatomicalLocation                |                                              |            |                        | 0..1        |               |
| Vaccination.Dose                              |                                              | PQ         |                        | 0..1        |               |
| Vaccination.Comment                           |                                              | ST         |                        | 0..1        |               |
| Vaccination.RouteOfAdministration             |                                              | CD         |                        | 1           |               |
| Vaccination.VaccinationMotive                 |                                              | CD         |                        | 1..*        |               |



## EHDSImmunisation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation |
| zib | Vaccination |
| alias_zib | NL: Vaccinatie |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Immunisation |
| definition_zib | Root concept of the Vaccination information model. This root concept contains all data elements of the Vaccination information model. |
| id_xtehr | EHDSImmunisation |
| id_zib | NL-CM:11.1.1 |
| name_zib | Vaccination |
| path_xtehr | EHDSImmunisation |
| path_zib | Vaccination |
| short_xtehr | Immunisation model |
| stereotype_zib | rootconcept |

### Comments
Matches


## EHDSImmunisation.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSImmunisation.header |
| path_xtehr | EHDSImmunisation.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSImmunisation.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSImmunisation.header.subject |
| path_xtehr | EHDSImmunisation.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSImmunisation.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSImmunisation.header.identifier |
| path_xtehr | EHDSImmunisation.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSImmunisation.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSImmunisation.header.authorship |
| path_xtehr | EHDSImmunisation.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSImmunisation.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSImmunisation.header.authorship.author[x] |
| path_xtehr | EHDSImmunisation.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSImmunisation.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSImmunisation.header.authorship.datetime |
| path_xtehr | EHDSImmunisation.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSImmunisation.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSImmunisation.header.lastUpdate |
| path_xtehr | EHDSImmunisation.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSImmunisation.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Indicates the current status of the immunisation event (completed, not-done). |
| id_xtehr | EHDSImmunisation.header.status |
| path_xtehr | EHDSImmunisation.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSImmunisation.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSImmunisation.header.statusReason[x] |
| path_xtehr | EHDSImmunisation.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSImmunisation.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSImmunisation.header.language |
| path_xtehr | EHDSImmunisation.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSImmunisation.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSImmunisation.header.version |
| path_xtehr | EHDSImmunisation.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSImmunisation.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSImmunisation.presentedForm |
| path_xtehr | EHDSImmunisation.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSImmunisation.diseaseOrAgentTargeted

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.diseaseOrAgentTargeted |
| zib | Vaccination.VaccinationPathogen |
| alias_zib | NL: VaccinatieZiekteverwekker |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT'} |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Disease or agent that the vaccination provides protection against. |
| definition_zib | The disease or pathogeen against what the vaccination is primarily given. |
| id_xtehr | EHDSImmunisation.diseaseOrAgentTargeted |
| id_zib | NL-CM:11.1.11 |
| name_zib | VaccinationPathogen |
| path_xtehr | EHDSImmunisation.diseaseOrAgentTargeted |
| path_zib | Vaccination.VaccinationPathogen |
| short_xtehr | Disease or agent targeted |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Scope matches, however EHDS can have multiple target Agent or diseases (where the zib only has the primary pathogen).  Binding Terminology in the zib only on SNOMED CT (5 concepts extensible, xtEHR also allows ICD-10). 


## EHDSImmunisation.vaccine

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.vaccine |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, ATC'} |
| card._xtehr | 1..1 |
| definition_xtehr | Generic description of the vaccine/prophylaxis or its component(s). |
| id_xtehr | EHDSImmunisation.vaccine |
| path_xtehr | EHDSImmunisation.vaccine |
| short_xtehr | Type of vaccine |
| type_xtehr | CodeableConcept |

### Comments
This could be represented in the Parmaceutical product code. Multiple codes are allowed. 


## EHDSImmunisation.administeredProduct

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.administeredProduct |
| zib | Vaccination.PharmaceuticalProduct |
| alias_zib | NL: FarmaceutischProduct |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Administered medicinal product |
| definition_zib | The pharmaceutical product of the administered vaccination |
| id_xtehr | EHDSImmunisation.administeredProduct |
| id_zib | NL-CM:11.1.9 |
| name_zib | PharmaceuticalProduct |
| path_xtehr | EHDSImmunisation.administeredProduct |
| path_zib | Vaccination.PharmaceuticalProduct |
| short_xtehr | Administered medicinal product |
| stereotype_zib | data,reference |
| type_xtehr | EHDSMedication |

### Comments
Matches scope, datatype. Mismatch cardinality for EHDS 0..1 while zib 1..1, however zib misses vaccine which means the Pharmaceutical product is always needed.  


## EHDSImmunisation.doseNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.doseNumber |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Order in the vaccination course. |
| id_xtehr | EHDSImmunisation.doseNumber |
| path_xtehr | EHDSImmunisation.doseNumber |
| short_xtehr | Number in a series of vaccinations / doses |
| type_xtehr | integer |

### Comments



## EHDSImmunisation.dateOfVaccination

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.dateOfVaccination |
| zib | Vaccination.VaccinationDateTime |
| alias_zib | NL: VaccinatieDatumTijd |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | The date and time when the vaccination was administered |
| definition_zib | Date (and if possible time) that the vaccine is administered. In the case of a historical vaccination, a vague date (month, year) is allowed. |
| id_xtehr | EHDSImmunisation.dateOfVaccination |
| id_zib | NL-CM:11.1.3 |
| name_zib | VaccinationDateTime |
| path_xtehr | EHDSImmunisation.dateOfVaccination |
| path_zib | Vaccination.VaccinationDateTime |
| short_xtehr | Date of vaccination |
| stereotype_zib | data |
| type_xtehr | date |
| type_zib | TS |

### Comments
Matches


## EHDSImmunisation.administeringCentre

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.administeringCentre |
| zib | Vaccination.Location::HealthcareProvider |
| alias_zib | NL: Locatie::Zorgaanbieder |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Name/code of administering centre or a health authority responsible for the vaccination event |
| definition_zib | The healthcare provider where the vaccination is or will be carried out. |
| id_xtehr | EHDSImmunisation.administeringCentre |
| id_zib | NL-CM:11.1.8 |
| name_zib | Location::HealthcareProvider |
| path_xtehr | EHDSImmunisation.administeringCentre |
| path_zib | Vaccination.Location::HealthcareProvider |
| short_xtehr | Administering centre |
| stereotype_zib | context,reference |
| type_xtehr | EHDSOrganisation |

### Comments
Matches scope almost (same intend zib could be clearer). Cardinality mismatch 0..* vs 1..1 in the zib. It seems odd that a single vaccination can take place at multiple administering centres and by multiple administrators. 


## EHDSImmunisation.vaccineAdministrator

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.vaccineAdministrator |
| zib | Vaccination.Administrator::Healthprofessional |
| alias_zib | NL: Toediener::Zorgverlener |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Health professional responsible for administering the vaccine or prophylaxis |
| definition_zib | The healthcare provider by whom the vaccination was done or will be done. |
| id_xtehr | EHDSImmunisation.vaccineAdministrator |
| id_zib | NL-CM:11.1.6 |
| name_zib | Administrator::Healthprofessional |
| path_xtehr | EHDSImmunisation.vaccineAdministrator |
| path_zib | Vaccination.Administrator::Healthprofessional |
| short_xtehr | Administrator of vaccine |
| stereotype_zib | context,reference |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSImmunisation.nextVaccinationDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSImmunisation.nextVaccinationDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The date when the vaccination is planned to be given/repeated (e.g. next dose) |
| id_xtehr | EHDSImmunisation.nextVaccinationDate |
| path_xtehr | EHDSImmunisation.nextVaccinationDate |
| short_xtehr | Next vaccination date |
| type_xtehr | date |

### Comments



## zib: Vaccination.AnatomicalLocation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Vaccination.AnatomicalLocation |
| alias_zib | NL: AnatomischeLocatie |
| card._zib | 0..1 |
| definition_zib | The location on the body where the vaccination was administered. |
| id_zib | NL-CM:11.1.13 |
| name_zib | AnatomicalLocation |
| path_zib | Vaccination.AnatomicalLocation |
| stereotype_zib | context,reference |

### Comments



## zib: Vaccination.Dose

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Vaccination.Dose |
| alias_zib | NL: Dosis |
| card._zib | 0..1 |
| definition_zib | The amount of product administered. In most cases, the entire product is administered; in some cases, a described part of the product is administered. |
| id_zib | NL-CM:11.1.4 |
| name_zib | Dose |
| path_zib | Vaccination.Dose |
| stereotype_zib | data |
| type_zib | PQ |

### Comments



## zib: Vaccination.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Vaccination.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comment on the vaccination |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:11.1.7 |
| name_zib | Comment |
| path_zib | Vaccination.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Vaccination.RouteOfAdministration

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Vaccination.RouteOfAdministration |
| alias_zib | NL: Toedieningsweg |
| card._zib | 1 |
| definition_zib | The route by which the vaccine is came into the body. |
| definitioncode_zib | SNOMED CT: 410675002 Route of administration |
| id_zib | NL-CM:11.1.12 |
| name_zib | RouteOfAdministration |
| path_zib | Vaccination.RouteOfAdministration |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Vaccination.VaccinationMotive

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Vaccination.VaccinationMotive |
| alias_zib | NL: VaccinatieAanleiding |
| card._zib | 1..* |
| definition_zib | Displays the trigger based on what the vaccine was administered. |
| definitioncode_zib | SNOMED CT: 159941000146109 Reason for vaccination |
| id_zib | NL-CM:11.1.10 |
| name_zib | VaccinationMotive |
| path_zib | Vaccination.VaccinationMotive |
| stereotype_zib | data |
| type_zib | CD |

### Comments

