# EpisodeOfCare
## Bespreking 10 november
Aanwezig: Chevy, Shenaida, Jacob, Marty  

+ EHDS issue: er lijkt overlap te zitten in .reason (kan verwijzing naar condition zijn) en .diagnosis.condition. Dat is onduidelijk
  + opmerking Jacob na de meeting: .reason gaat over een geplande episode, .diagnosis is voor de verslaglegging van een voorbije episode. Maar dan hebben we de volgende issues:
    + EHDS issue: blijkbaar kan EpisodeOfCare gebruikt worden voor zowel een geplande episode als een voorbije episode, maar dan ontbreken elementen voor een status en een statusdatum, voeg deze toe
    + EHDS issue: waarom kan een EHDSProcedure een reden zijn voor een EpisodeOfCare? We denken dat hier niet de geplande procedures moeten zijn, daarvoor is immers het CarePlan.  
+ EHDS issue: begin- en einddatum ontbreken (als dit model voor zowel planning als verslaglegging kan worden gebruikt, dan zijn zowel geplande als actuele begin en einddatum nodig)
+ EHDS issue: tekstvelden voor naam en toelichting van de episode ontbreken
+ EHDS issue: van .type ontbreekt binding informatie
+ zib issue: kardinaliteit van .FocusEpisodeOfCare::Condition moet 0..* zijn ipv 0..1
+ zib issue: we hebben een equivalent voor EHDSEpisodeOfCare.type nodig
+ zib issue: we hebben een equivalent voor EHDSEpisodeOfCare.reason nodig. 


## Overall discussion
There is only one concept in the EHDS model that more or less matches a concept in the zib: EHDSEpisodeOfCare.diagnosis.condition[x].  


| zib                                         | xtehr                                         | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:--------------------------------------------|:----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| EpisodeOfCare                               | EHDSEpisodeOfCare                             |            |                        |             | 0..*          |
|                                             | EHDSEpisodeOfCare.type                        |            | CodeableConcept        |             | 0..*          |
|                                             | EHDSEpisodeOfCare.reasonText                  |            | string                 |             | 0..1          |
|                                             | EHDSEpisodeOfCare.reason[x]                   |            | CodeableConcept        |             | 0..*          |
|                                             | EHDSEpisodeOfCare.diagnosis                   |            | Base                   |             | 0..*          |
|                                             | EHDSEpisodeOfCare.diagnosis.description       |            | string                 |             | 1..1          |
| EpisodeOfCare.FocusEpisodeOfCare::Condition | EHDSEpisodeOfCare.diagnosis.condition[x]      |            | CodeableConcept        | 0..1        | 0..1          |
| EpisodeOfCare.StartDate                     |                                               | TS         |                        | 0..1        |               |
| EpisodeOfCare.EndDate                       |                                               | TS         |                        | 0..1        |               |
| EpisodeOfCare.EpisodeOfCareName             |                                               | ST         |                        | 0..1        |               |
| EpisodeOfCare.Comment                       |                                               | ST         |                        | 0..1        |               |



## EHDSEpisodeOfCare

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare |
| zib | EpisodeOfCare |
| alias_zib | NL: ZorgEpisode |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Episode of care |
| definition_zib | Root concept of the EpisodeOfCare information model.This root concept contains all data elements of the EpisodeOfCare information model. |
| id_xtehr | EHDSEpisodeOfCare |
| id_zib | NL-CM:16.6.1 |
| name_zib | EpisodeOfCare |
| path_xtehr | EHDSEpisodeOfCare |
| path_zib | EpisodeOfCare |
| short_xtehr | Episode of care model |
| stereotype_zib | rootconcept |

### Comments




## EHDSEpisodeOfCare.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.type |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A classification of the type of episode of care; e.g. specialist referral, disease management. |
| id_xtehr | EHDSEpisodeOfCare.type |
| path_xtehr | EHDSEpisodeOfCare.type |
| short_xtehr | A classification of the type of episode of care; e.g. specialist referral, disease management. |
| type_xtehr | CodeableConcept |

### Comments



## EHDSEpisodeOfCare.reasonText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.reasonText |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Textual descriptions of the medical reasons that are expected to be addressed during the episode of care. |
| id_xtehr | EHDSEpisodeOfCare.reasonText |
| path_xtehr | EHDSEpisodeOfCare.reasonText |
| short_xtehr | Textual descriptions of the medical reasons that are expected to be addressed during the episode of care. |
| type_xtehr | string |

### Comments
No match. The zib has no medical reasons.



## EHDSEpisodeOfCare.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.reason[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Coded list of medical reasons that are expected to be addressed during the episode of care. |
| id_xtehr | EHDSEpisodeOfCare.reason[x] |
| path_xtehr | EHDSEpisodeOfCare.reason[x] |
| short_xtehr | Coded list of medical reasons that are expected to be addressed during the episode of care. |
| type_xtehr | CodeableConcept |

### Comments
This concept is absent in the zib. It is a list of coded concepts, and references to EHDSObservation, EHDSProcedure, and EHDSCondition. 



## EHDSEpisodeOfCare.diagnosis

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.diagnosis |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | List of medical conditions that were addressed during the episode of care |
| id_xtehr | EHDSEpisodeOfCare.diagnosis |
| path_xtehr | EHDSEpisodeOfCare.diagnosis |
| short_xtehr | List of medical conditions that were addressed during the episode of care |
| type_xtehr | Base |

### Comments
To describe the focus of the episode, the EHDS model has a list of diagnoses, consisting of a textual description of the diagnosis and either a code or a referenze to EHDSCondition. The zib has only one reference to the Condition zib.


## EHDSEpisodeOfCare.diagnosis.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.diagnosis.description |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Textual description of the medical condition that was addressed during the episode of care |
| id_xtehr | EHDSEpisodeOfCare.diagnosis.description |
| path_xtehr | EHDSEpisodeOfCare.diagnosis.description |
| short_xtehr | Textual description of the medical condition that was addressed during the episode of care |
| type_xtehr | string |

### Comments



## EHDSEpisodeOfCare.diagnosis.condition[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSEpisodeOfCare.diagnosis.condition[x] |
| zib | EpisodeOfCare.FocusEpisodeOfCare::Condition |
| alias_zib | NL: FocusZorgEpisode::AandoeningOfGesteldheid |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | The medical condition that was addressed during the episode of care |
| definition_zib | The condition on which the episode of care focuses. |
| id_xtehr | EHDSEpisodeOfCare.diagnosis.condition[x] |
| id_zib | NL-CM:16.6.7 |
| name_zib | FocusEpisodeOfCare::Condition |
| path_xtehr | EHDSEpisodeOfCare.diagnosis.condition[x] |
| path_zib | EpisodeOfCare.FocusEpisodeOfCare::Condition |
| short_xtehr | The medical condition that was addressed during the episode of care |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |

### Comments
There is a match with the reference to the zib Condition, but note that the EHDSEpisodeOfCare.condition[X] can either a codeable concept or a reference to EHDSCondition. 


## zib: EpisodeOfCare.StartDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.StartDate |
| alias_zib | NL: BeginDatum |
| card._zib | 0..1 |
| definition_zib | The date that marks the beginning of the episode of care. Usually this is the date of the first contact of the patient with the care provider in the context of the health problem. |
| definitioncode_zib | SNOMED CT: 413946009 Date treatment started |
| id_zib | NL-CM:16.6.2 |
| name_zib | StartDate |
| path_zib | EpisodeOfCare.StartDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: EpisodeOfCare.EndDate

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.EndDate |
| alias_zib | NL: EindDatum |
| card._zib | 0..1 |
| definition_zib | The date that marks the end of the episode of care. This can be the date of the last contact of the patient with the care provider in the context of the health problem, but also thereafter on the basis of hindsight. |
| definitioncode_zib | SNOMED CT: 413947000 Date treatment stopped |
| id_zib | NL-CM:16.6.3 |
| name_zib | EndDate |
| path_zib | EpisodeOfCare.EndDate |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: EpisodeOfCare.EpisodeOfCareName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.EpisodeOfCareName |
| alias_zib | NL: ZorgEpisodeNaam |
| card._zib | 0..1 |
| definition_zib | A name that characterizes the episode of care for the care provider. |
| id_zib | NL-CM:16.6.5 |
| name_zib | EpisodeOfCareName |
| path_zib | EpisodeOfCare.EpisodeOfCareName |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: EpisodeOfCare.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | EpisodeOfCare.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Additional information about the episode of care that the care provider wishes to see at first glance. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:16.6.6 |
| name_zib | Comment |
| path_zib | EpisodeOfCare.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments

