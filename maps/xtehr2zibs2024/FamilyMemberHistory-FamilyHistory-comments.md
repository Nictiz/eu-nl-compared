# FamilyMemberHistory

## Toegevoegd door Jacob na de bespreking op 10 november
+ geen EHDS issue: de constructie in de zib waarbij één van de AandoeningFamilielid met een indicator als doodsoorzaak wordt aangewezen voorkomt redundantie. Maar het EHDS model is altijd te mappen op de zib en andersom => geen issue.
+ zib issue(?): de zib heeft een overlijdensindicator, het EHDS model niet. Een familielid met alleen een overlijdensindicator kan niet worden gemapt op het EHDS model zonder informatieverlies. Mogelijk nuttig als de overlijdensdatum/leeftijd bij overlijden niet bekend is? Maar wat is dan de toegevoegde waarde van de kennis dat het familielid overleden is? Voorstel: overlijdensindicator uit zib verwijderen.
+ EHDS issue: Het EHDS model heeft een geboortedatum, de zib niet. Een familielid met alleen een geboortedatum kan niet worden gemapt op de zib zonder informatieverlies. Maar het lijkt er op dat de geboortedatum alleen is toegevoegd om het mogelijk te maken om de overlijdensdatum in plaats van de leetfijd bij overlijden. Dit maakt het EHDS model nodeloos complex. Voorstel: EHDS model vereenvoudigen door ageOrDateOfDeathDate te verwijderen: dan is dateOfBirth niet nodig. Als EHDS dit verzoek niet inwilligt dan moet de zib het EHDS model volgen.
+ zib issue: de zib bevat een verwijzing naar Diagnose en OvergevoelighedIntolerantie, het EHDS heeft alleen een codeable concept. In dit geval lijkt een codeable concept voldoende en zou de optie om alleen een codeable concept te gebruiken moeten worden toegevoegd aan de zib.
+ zib issue: in de zib kunnen alleen diagnoses en overgevoeligheidintoleranties als doodsoorzaken worden geregistreerd. Dat komt neer op SNOMED codes uit de bevindingen-tak. Een verkeersongeluk en zelfmoord (gebeurtenis) passen hier niet in (zou dan letsel door verkeersongeluk resp zelfmoord moeten worden). In het EHDS model speelt dit probleem niet. Is op te lossen door ook codeable conept toe te staan.

## Bespreking 10 november 2025
Aanwezig: Jacob Shenaida Chevy
+ EHDS issue: toelichting (comment) op familielid ontbreekt
+ EHDS issue: het EHDS model verwijst naar hl7:v3-RoleCode.  In deze lijst komen ook items voor die geen bloedverwantsschap betreffen en de zib beperkt zich tot bloedverwanten. In het kader van de familieanamnese is dat ook terecht. Het EHDS model zou zich ook tot bloedverwanten moeten beperken.  (FHIR (R5) perkt deze lijst in naar concept is-a FAMMEMB)
+ EHDS issue: kardinaliteit van FamilyMemberHistory binnen Discharge Report is 0..ster. Dat klopt niet met de naam van het model en heeft als effect dat iedere familielid-entry een header krijgt. Dat lijkt niet handig. Voorstel: breng de elementen in het model onder in FamilyMember container met kardinaliteit 1..ster. (als dit verzoek niet wordt ingewilligd moet de zib het EHDS model volgen; de registratiegegevens kunnen immers per familielid anders zijn).
+ EHDS issue: de datum waarop de anamnese is afgenomen ontbreekt. Wij gaan er van uit dat de datum in de header (Date and time of authoring/issuing) een andere betekenis heeft.


| zib                                                                | xtehr                                               | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-------------------------------------------------------------------|:----------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| FamilyHistory                                                      | EHDSFamilyMemberHistory                             |            |                        |             | 0..*          |
|                                                                    | EHDSFamilyMemberHistory.header                      |            | Base                   |             | 1..1          |
|                                                                    | EHDSFamilyMemberHistory.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                                    | EHDSFamilyMemberHistory.header.identifier           |            | Identifier             |             | 0..*          |
|                                                                    | EHDSFamilyMemberHistory.header.authorship           |            | Base                   |             | 1..*          |
|                                                                    | EHDSFamilyMemberHistory.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
| FamilyHistory.Date                                                 | EHDSFamilyMemberHistory.header.authorship.datetime  | TS         | dateTime               | 0..1        | 1..1          |
|                                                                    | EHDSFamilyMemberHistory.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                                    | EHDSFamilyMemberHistory.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                                    | EHDSFamilyMemberHistory.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                                    | EHDSFamilyMemberHistory.header.language             |            | CodeableConcept        |             | 0..1          |
| FamilyHistory.FamilyMember.BiologicalRelationship                  | EHDSFamilyMemberHistory.patientRelationship         | CD         | CodeableConcept        | 1           | 0..1          |
|                                                                    | EHDSFamilyMemberHistory.dateOfBirth                 |            | date                   |             | 0..1          |
| FamilyHistory.FamilyMember.AgeAtDeath                              | EHDSFamilyMemberHistory.ageOrDateOfDeath[x]         | INT        | date                   | 0..1        | 0..1          |
| FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember.Diagnosis | EHDSFamilyMemberHistory.condition                   |            | CodeableConcept        |             | 0..*          |
|                                                                    | EHDSFamilyMemberHistory.causeOfDeath                |            | CodeableConcept        |             | 0..1          |
| FamilyHistory.FamilyMember                                         |                                                     |            |                        | 1..*        |               |
| FamilyHistory.FamilyMember.Comment                                 |                                                     | ST         |                        | 0..1        |               |
| FamilyHistory.FamilyMember.Disorder                                |                                                     |            |                        | 1..*        |               |
| FamilyHistory.FamilyMember.Disorder.IsCauseOfDeath                 |                                                     | BL         |                        | 0..1        |               |
| FamilyHistory.FamilyMember.DeathIndicator                          |                                                     | BL         |                        | 0..1        |               |
| FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember           |                                                     |            |                        | (0..1)      |               |



## EHDSFamilyMemberHistory

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory |
| zib | FamilyHistory |
| alias_zib | NL: Familieanamnese |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for family member history |
| definition_zib | Root concept of the FamilyHistory information model. This root concept contains all data elements of the FamilyHistory information model. |
| id_xtehr | EHDSFamilyMemberHistory |
| id_zib | NL-CM:6.1.1 |
| name_zib | FamilyHistory |
| path_xtehr | EHDSFamilyMemberHistory |
| path_zib | FamilyHistory |
| short_xtehr | Family member history model |
| stereotype_zib | rootconcept |

### Comments



## EHDSFamilyMemberHistory.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| id_xtehr | EHDSFamilyMemberHistory.header |
| path_xtehr | EHDSFamilyMemberHistory.header |
| short_xtehr | Common header for all patient-related data |
| type_xtehr | Base |

### Comments



## EHDSFamilyMemberHistory.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSFamilyMemberHistory.header.subject |
| path_xtehr | EHDSFamilyMemberHistory.header.subject |
| short_xtehr | The person whose family member's medical history is described. |
| type_xtehr | EHDSPatient |

### Comments



## EHDSFamilyMemberHistory.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business identifier for the object |
| id_xtehr | EHDSFamilyMemberHistory.header.identifier |
| path_xtehr | EHDSFamilyMemberHistory.header.identifier |
| short_xtehr | Business identifier for the object |
| type_xtehr | Identifier |

### Comments



## EHDSFamilyMemberHistory.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSFamilyMemberHistory.header.authorship |
| path_xtehr | EHDSFamilyMemberHistory.header.authorship |
| short_xtehr | Resource authoring details |
| type_xtehr | Base |

### Comments



## EHDSFamilyMemberHistory.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.authorship.author[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| id_xtehr | EHDSFamilyMemberHistory.header.authorship.author[x] |
| path_xtehr | EHDSFamilyMemberHistory.header.authorship.author[x] |
| short_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| type_xtehr | EHDSHealthProfessional |

### Comments



## EHDSFamilyMemberHistory.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.authorship.datetime |
| zib | FamilyHistory.Date |
| alias_zib | NL: Datum |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Date and time of authoring/issuing |
| definition_zib | Date on which the family history was entered. A ‘vague’ date is permitted. |
| id_xtehr | EHDSFamilyMemberHistory.header.authorship.datetime |
| id_zib | NL-CM:6.1.2 |
| name_zib | Date |
| path_xtehr | EHDSFamilyMemberHistory.header.authorship.datetime |
| path_zib | FamilyHistory.Date |
| short_xtehr | Date and time of authoring/issuing |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSFamilyMemberHistory.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| id_xtehr | EHDSFamilyMemberHistory.header.lastUpdate |
| path_xtehr | EHDSFamilyMemberHistory.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource (may be used for technical corrections). |
| type_xtehr | dateTime |

### Comments



## EHDSFamilyMemberHistory.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource or document |
| id_xtehr | EHDSFamilyMemberHistory.header.status |
| path_xtehr | EHDSFamilyMemberHistory.header.status |
| short_xtehr | Status of the resource or document |
| type_xtehr | CodeableConcept |

### Comments



## EHDSFamilyMemberHistory.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSFamilyMemberHistory.header.statusReason[x] |
| path_xtehr | EHDSFamilyMemberHistory.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSFamilyMemberHistory.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSFamilyMemberHistory.header.language |
| path_xtehr | EHDSFamilyMemberHistory.header.language |
| short_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSFamilyMemberHistory.patientRelationship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.patientRelationship |
| zib | FamilyHistory.FamilyMember.BiologicalRelationship |
| alias_zib | NL: BiologischeRelatie |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:v3-RoleCode'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The family relation between the related person and the patient. |
| definition_zib | Indicates the biological relationship of the family member to the patient. |
| id_xtehr | EHDSFamilyMemberHistory.patientRelationship |
| id_zib | NL-CM:6.1.4 |
| name_zib | BiologicalRelationship |
| path_xtehr | EHDSFamilyMemberHistory.patientRelationship |
| path_zib | FamilyHistory.FamilyMember.BiologicalRelationship |
| short_xtehr | Patient relationship |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Slechte match: het EHDS model verwijst naar hl7:v3-RoleCode. FHIR (R5) perkt deze lijst in naar cocnept is-a FAMMEMB.  
In deze lijst komen ook items voor die geen bloedverwantsschap betreffen en de zib beperkt zich tot bloedverwanten. In het kader van de familieanamnese is dat ook terecht. Het EHDS model zou zich ook tot bloedverwanten moeten beperken.  




## EHDSFamilyMemberHistory.dateOfBirth

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.dateOfBirth |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date of birth of the family member. |
| id_xtehr | EHDSFamilyMemberHistory.dateOfBirth |
| path_xtehr | EHDSFamilyMemberHistory.dateOfBirth |
| short_xtehr | Date of birth of the family member. |
| type_xtehr | date |

### Comments



## EHDSFamilyMemberHistory.ageOrDateOfDeath[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.ageOrDateOfDeath[x] |
| zib | FamilyHistory.FamilyMember.AgeAtDeath |
| alias_zib | NL: LeeftijdBijOverlijden |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Age or date of the death of the family member. |
| definition_zib | The age at which the family member died. |
| id_xtehr | EHDSFamilyMemberHistory.ageOrDateOfDeath[x] |
| id_zib | NL-CM:6.1.12 |
| name_zib | AgeAtDeath |
| path_xtehr | EHDSFamilyMemberHistory.ageOrDateOfDeath[x] |
| path_zib | FamilyHistory.FamilyMember.AgeAtDeath |
| short_xtehr | Age or date of the death of the family member. |
| stereotype_zib | data |
| type_xtehr | date |
| type_zib | INT |

### Comments



## EHDSFamilyMemberHistory.condition

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.condition |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember.Diagnosis |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..* |
| definition_xtehr | Medical problems this person suffers or suffered. |
| id_xtehr | EHDSFamilyMemberHistory.condition |
| path_xtehr | EHDSFamilyMemberHistory.condition |
| short_xtehr | Medical problems this person suffers or suffered. |
| type_xtehr | CodeableConcept |

### Comments
Modellering in EHDS is niet echt mooi, want laat ruimte voor redundantie. De ziekte die als doodsoorzaak wordt gezien, kun je vastleggen bij alleen .causeOfDeath, maar ook bij zowel .causeOfDeath als bij .condition.




## EHDSFamilyMemberHistory.causeOfDeath

### Table

| attribute | value |
|---|---|
| xtehr | EHDSFamilyMemberHistory.causeOfDeath |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10, SNOMED CT, Orphacode if rare disease is diagnosed'} |
| card._xtehr | 0..1 |
| definition_xtehr | Information about disease or condition that was the main cause of death. |
| id_xtehr | EHDSFamilyMemberHistory.causeOfDeath |
| path_xtehr | EHDSFamilyMemberHistory.causeOfDeath |
| short_xtehr | Information about disease or condition that was the main cause of death. |
| type_xtehr | CodeableConcept |

### Comments
In de zib is dit de combinatie van AandoeningFamilielid én IsDoodsoorzaak = 1.




## zib: FamilyHistory.FamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember |
| alias_zib | NL: Familielid |
| card._zib | 1..* |
| definition_zib | Container of the FamilyMember concept. This container contains all data elements of the FamilyMember concept. |
| id_zib | NL-CM:6.1.3 |
| name_zib | FamilyMember |
| path_zib | FamilyHistory.FamilyMember |
| stereotype_zib | container |

### Comments



## zib: FamilyHistory.FamilyMember.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comment with information on the family member which might be relevant to the family history. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:6.1.5 |
| name_zib | Comment |
| path_zib | FamilyHistory.FamilyMember.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder |
| alias_zib | NL: Aandoening |
| card._zib | 1..* |
| definition_zib | Container of the Disorder concept. This container contains all data elements of the Disorder concept. |
| id_zib | NL-CM:6.1.6 |
| name_zib | Disorder |
| path_zib | FamilyHistory.FamilyMember.Disorder |
| stereotype_zib | container |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder.IsCauseOfDeath

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.IsCauseOfDeath |
| alias_zib | NL: IsDoodsoorzaak |
| card._zib | 0..1 |
| definition_zib | Indication stating whether the described health problem was the cause of death of the family member. |
| id_zib | NL-CM:6.1.9 |
| name_zib | IsCauseOfDeath |
| path_zib | FamilyHistory.FamilyMember.Disorder.IsCauseOfDeath |
| stereotype_zib | data |
| type_zib | BL |

### Comments
Dit is in de zib een boolean. Per aandoening die het familielid heeft, kun je aangeven of deze ook als doodsoorzaak geldt.



## zib: FamilyHistory.FamilyMember.DeathIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.DeathIndicator |
| alias_zib | NL: OverlijdensIndicator |
| card._zib | 0..1 |
| definition_zib | An indication stating whether the family member has died. |
| id_zib | NL-CM:6.1.10 |
| name_zib | DeathIndicator |
| path_zib | FamilyHistory.FamilyMember.DeathIndicator |
| stereotype_zib | data |
| type_zib | BL |

### Comments
In het EHDS model kun je nu niet aangeven dat een familielid is overleden als je niet de leeftijd van overlijden weet en ook niet welke ziekte leidde tot de dood. Stel je weet dat oma van moeders zijde hartpatiënt was en darmkanker had, maar je weet niet waar ze aan overleed en op welke leeftijd. Met de DeathIndicator in de zib kun je wel kwijt dat deze oma niet meer leeft.



## zib: FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| alias_zib | NL: AandoeningFamilielid |
| card._zib | 1 |
| definition_zib | Container of the DisorderFamilyMember concept.This container contains all data elements of the DisorderFamilyMember concept. |
| id_zib | NL-CM:6.1.13 |
| name_zib | DisorderFamilyMember |
| path_zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| stereotype_zib | container |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| alias_zib | NL: Diagnose |
| card._zib | (0..1) |
| definition_zib | Diagnosis of a condition in a blood relative of the patient. |
| id_zib | NL-CM:6.1.14 |
| name_zib | DisorderFamilyMember |
| path_zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| stereotype_zib | data,reference |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| card._zib | (0..1) |
| definition_zib | Hypersensitivity or intolerance in a blood relative of the patient. |
| id_zib | NL-CM:6.1.15 |
| name_zib | DisorderFamilyMember |
| path_zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| stereotype_zib | data,reference |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| alias_zib | NL: AandoeningFamilielid |
| card._zib | 1 |
| definition_zib | Container of the DisorderFamilyMember concept.This container contains all data elements of the DisorderFamilyMember concept. |
| id_zib | NL-CM:6.1.13 |
| name_zib | DisorderFamilyMember |
| path_zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| stereotype_zib | container |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| alias_zib | NL: Diagnose |
| card._zib | (0..1) |
| definition_zib | Diagnosis of a condition in a blood relative of the patient. |
| id_zib | NL-CM:6.1.14 |
| name_zib | DisorderFamilyMember |
| path_zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| stereotype_zib | data,reference |

### Comments



## zib: FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| alias_zib | NL: OvergevoeligheidIntolerantie |
| card._zib | (0..1) |
| definition_zib | Hypersensitivity or intolerance in a blood relative of the patient. |
| id_zib | NL-CM:6.1.15 |
| name_zib | DisorderFamilyMember |
| path_zib | FamilyHistory.FamilyMember.Disorder.DisorderFamilyMember |
| stereotype_zib | data,reference |

### Comments



## zib: FamilyHistory.FamilyMember.AgeAtDeath

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.AgeAtDeath |
| alias_zib | NL: LeeftijdBijOverlijden |
| card._zib | 0..1 |
| definition_zib | The age at which the family member died. |
| id_zib | NL-CM:6.1.12 |
| name_zib | AgeAtDeath |
| path_zib | FamilyHistory.FamilyMember.AgeAtDeath |
| stereotype_zib | data |
| type_zib | INT |

### Comments



## zib: FamilyHistory.FamilyMember.DeathIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | FamilyHistory.FamilyMember.DeathIndicator |
| alias_zib | NL: OverlijdensIndicator |
| card._zib | 0..1 |
| definition_zib | An indication stating whether the family member has died. |
| id_zib | NL-CM:6.1.10 |
| name_zib | DeathIndicator |
| path_zib | FamilyHistory.FamilyMember.DeathIndicator |
| stereotype_zib | data |
| type_zib | BL |

### Comments

