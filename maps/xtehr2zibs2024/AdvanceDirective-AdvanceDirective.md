# AdvanceDirective

| zib                                            | xtehr                                            | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-----------------------------------------------|:-------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| AdvanceDirective                               | EHDSAdvanceDirective                             |            |                        |             | 0..*          |
|                                                | EHDSAdvanceDirective.header                      |            | Base                   |             | 1..1          |
|                                                | EHDSAdvanceDirective.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                | EHDSAdvanceDirective.header.identifier           |            | Identifier             |             | 0..*          |
|                                                | EHDSAdvanceDirective.header.authorship           |            | Base                   |             | 1..*          |
|                                                | EHDSAdvanceDirective.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                | EHDSAdvanceDirective.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                | EHDSAdvanceDirective.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                | EHDSAdvanceDirective.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                | EHDSAdvanceDirective.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                | EHDSAdvanceDirective.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                | EHDSAdvanceDirective.header.version              |            | string                 |             | 0..1          |
|                                                | EHDSAdvanceDirective.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| AdvanceDirective.LivingWillType                | EHDSAdvanceDirective.category                    | CD         | CodeableConcept        | 1           | 0..*          |
|                                                | EHDSAdvanceDirective.narrative                   |            | string                 |             | 0..1          |
| AdvanceDirective.LivingWillDate                | EHDSAdvanceDirective.effectivePeriod             | TS         | Period                 | 1           | 0..1          |
|                                                | EHDSAdvanceDirective.authorisingEntity[x]        |            | EHDSPatient            |             | 0..1          |
| AdvanceDirective.Diagnosis                     | EHDSAdvanceDirective.relatedConditions[x]        |            | CodeableConcept        | 0..*        | 0..*          |
| AdvanceDirective.LivingWillDocument            | EHDSAdvanceDirective.advanceDirectiveDocument    | ED         | EHDSAttachment         | 0..1        | 0..1          |
| AdvanceDirective.Representative::ContactPerson |                                                  |            |                        | 0..*        |               |
| AdvanceDirective.Comment                       |                                                  | ST         |                        | 0..1        |               |



## EHDSAdvanceDirective

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective |
| zib | AdvanceDirective |
| alias_zib | NL: Wilsverklaring |
| card._xtehr | 0..* |
| definition_xtehr | Healthcare directives concerning life or after life wishes of the patient |
| definition_zib | Root concept of the AdvanceDirective information model. This concept contains all data elements of the AdvanceDirective information model. |
| id_xtehr | EHDSAdvanceDirective |
| id_zib | NL-CM:7.15.1 |
| name_zib | AdvanceDirective |
| path_xtehr | EHDSAdvanceDirective |
| path_zib | AdvanceDirective |
| short_xtehr | Advance directive model |
| stereotype_zib | rootconcept |

### Comments



## EHDSAdvanceDirective.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSAdvanceDirective.header |
| path_xtehr | EHDSAdvanceDirective.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSAdvanceDirective.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSAdvanceDirective.header.subject |
| path_xtehr | EHDSAdvanceDirective.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments



## EHDSAdvanceDirective.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSAdvanceDirective.header.identifier |
| path_xtehr | EHDSAdvanceDirective.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSAdvanceDirective.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSAdvanceDirective.header.authorship |
| path_xtehr | EHDSAdvanceDirective.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments



## EHDSAdvanceDirective.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSAdvanceDirective.header.authorship.author[x] |
| path_xtehr | EHDSAdvanceDirective.header.authorship.author[x] |
| short_xtehr | Author |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSAdvanceDirective.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.authorship.datetime |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| id_xtehr | EHDSAdvanceDirective.header.authorship.datetime |
| path_xtehr | EHDSAdvanceDirective.header.authorship.datetime |
| short_xtehr | Date and time of authoring/issuing |
| type_xtehr | dateTime |

### Comments



## EHDSAdvanceDirective.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSAdvanceDirective.header.lastUpdate |
| path_xtehr | EHDSAdvanceDirective.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments



## EHDSAdvanceDirective.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSAdvanceDirective.header.status |
| path_xtehr | EHDSAdvanceDirective.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAdvanceDirective.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSAdvanceDirective.header.statusReason[x] |
| path_xtehr | EHDSAdvanceDirective.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAdvanceDirective.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSAdvanceDirective.header.language |
| path_xtehr | EHDSAdvanceDirective.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAdvanceDirective.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSAdvanceDirective.header.version |
| path_xtehr | EHDSAdvanceDirective.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments



## EHDSAdvanceDirective.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSAdvanceDirective.presentedForm |
| path_xtehr | EHDSAdvanceDirective.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSAdvanceDirective.category

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.category |
| zib | AdvanceDirective.LivingWillType |
| alias_zib | NL: WilsverklaringType |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Categories of Directives related to decisions prior and after death |
| definition_zib | The type of living will. |
| id_xtehr | EHDSAdvanceDirective.category |
| id_zib | NL-CM:7.15.2 |
| name_zib | LivingWillType |
| path_xtehr | EHDSAdvanceDirective.category |
| path_zib | AdvanceDirective.LivingWillType |
| short_xtehr | Categories of Directives related to decisions prior and after death |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSAdvanceDirective.narrative

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.narrative |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Textual description of the directive |
| id_xtehr | EHDSAdvanceDirective.narrative |
| path_xtehr | EHDSAdvanceDirective.narrative |
| short_xtehr | Textual description of the directive |
| type_xtehr | string |

### Comments



## EHDSAdvanceDirective.effectivePeriod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.effectivePeriod |
| zib | AdvanceDirective.LivingWillDate |
| alias_zib | NL: WilsverklaringDatum |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Time period during which the directive is effective |
| definition_zib | The date on which the living will was recorded. |
| id_xtehr | EHDSAdvanceDirective.effectivePeriod |
| id_zib | NL-CM:7.15.7 |
| name_zib | LivingWillDate |
| path_xtehr | EHDSAdvanceDirective.effectivePeriod |
| path_zib | AdvanceDirective.LivingWillDate |
| short_xtehr | Time period during which the directive is effective |
| stereotype_zib | data |
| type_xtehr | Period |
| type_zib | TS |

### Comments



## EHDSAdvanceDirective.authorisingEntity[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.authorisingEntity[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Person or organisation that authorizes the directive |
| id_xtehr | EHDSAdvanceDirective.authorisingEntity[x] |
| path_xtehr | EHDSAdvanceDirective.authorisingEntity[x] |
| short_xtehr | Person or organisation that authorizes the directive |
| type_xtehr | EHDSPatient |

### Comments



## EHDSAdvanceDirective.relatedConditions[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.relatedConditions[x] |
| zib | AdvanceDirective.Diagnosis |
| alias_zib | NL: Diagnose |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT, Orphacode'} |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | The problem or disorder to which the living will applies. Multiple fields could be provided. |
| definition_zib | The diagnosis of the condition to which the advance directive relates. |
| id_xtehr | EHDSAdvanceDirective.relatedConditions[x] |
| id_zib | NL-CM:7.15.8 |
| name_zib | Diagnosis |
| path_xtehr | EHDSAdvanceDirective.relatedConditions[x] |
| path_zib | AdvanceDirective.Diagnosis |
| short_xtehr | The problem or disorder to which the living will applies. Multiple fields could be provided. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments



## EHDSAdvanceDirective.advanceDirectiveDocument

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAdvanceDirective.advanceDirectiveDocument |
| zib | AdvanceDirective.LivingWillDocument |
| alias_zib | NL: WilsverklaringDocument |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Scanned source document with the living will and the patient's signature, such as a PDF. |
| definition_zib | Scanned source document with the living will and the patient's signature, such as a PDF. |
| id_xtehr | EHDSAdvanceDirective.advanceDirectiveDocument |
| id_zib | NL-CM:7.15.5 |
| name_zib | LivingWillDocument |
| path_xtehr | EHDSAdvanceDirective.advanceDirectiveDocument |
| path_zib | AdvanceDirective.LivingWillDocument |
| short_xtehr | Scanned source document with the living will and the patient's signature, such as a PDF. |
| stereotype_zib | data |
| type_xtehr | EHDSAttachment |
| type_zib | ED |

### Comments



## zib: AdvanceDirective.Representative::ContactPerson

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AdvanceDirective.Representative::ContactPerson |
| alias_zib | NL: Vertegenwoordiger::Contactpersoon |
| card._zib | 0..* |
| definition_zib | The person who is the legal representative or is appointed as the authorized representative in the signed authorization. |
| id_zib | NL-CM:7.15.3 |
| name_zib | Representative::ContactPerson |
| path_zib | AdvanceDirective.Representative::ContactPerson |
| stereotype_zib | data,reference |

### Comments



## zib: AdvanceDirective.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AdvanceDirective.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comment on the living will: the form, such as a medallion, tattoo, etc., or where the living will can be found. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:7.15.6 |
| name_zib | Comment |
| path_zib | AdvanceDirective.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments

