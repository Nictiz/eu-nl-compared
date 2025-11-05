# PregnancyHistory  
## Bespreking 5-11
Aanwezig: Astrid, Jacob  
De waardenlijst EHDSOutcomeOfPregnancy bevat waarden voor drie concepten: 
+ Reason for termination of pregnancy
  + Ectopic pregnancy
  + Hydatidiform mole, benign
  + Fetal death
  + Foetale nood
+ Result of pregnancy
  + Livebirth
  + Miscarriage
  + Stillbirth
+ Termination of pregnancy
  + cesarian section
  + abortus provocatus
  + through medication
  + non-sectio surgical procedure  

EHDS issue: splits outcome in deze drie concepten.   
Als concept niet geplitst kan worden dan moet de kardinaliteit naar 0..*.
## Bespreking 14-10
Aanwezig: Lilian, Micha, Astrid, Jacob  
+ Er is geen zib voor pregnancy history, maar EHDSPregnancyHistory kan worden gevuld vanuit instantiaties van zib Zwangerschap die beëindigd zijn 
+ De items voor de codelijst van EHDS Outcome sluiten elkaar niet uit en de kardinaliteit is nu 0..1.
Verzoek voor EHDS:
  1. De lijst is niet mutually exclusive, omdat sommige items enerzijds een diagnose zijn waarbij de vrucht het lichaam nog niet heeft verlaten en anderzijds de manier aangeven waarop de zwangerschap eindigde. Als dat zo blijft, verhoog dan de kardinaliteit naar 0..*.
  2. Als de kardinaliteit 0..1 moet blijven, zorg dan dat de items in de lijst elkaar uitsluiten. 
+ EHDS element outcomeDate: Dit is een moeilijk element, omdat er in de lijst voor 'outcome' een mengeling van waarden staat: enerzijds waarden die betrekking hebben op een diagnose, terwijl de vrucht nog in de moeder is (zwangeschap loopt nog) en anderzijds waarden (behalve newborn death) die echt een einde van de zwangerschap zijn.  
In het eerste geval hebben we het over een diagnosedatum en in het andere geval over de einddatum van de zwangerschap.  
Verzoek voor EHDS:  
Wijzig 'outcomeDate' in 'EndDate', die dan betrekking heeft op het moment waarop de zwangerschap is beëindigd, d.w.z. de vrucht het lichaam verliet. Zo is er geen onduidelijkheid of de datum betrekking heeft op een diagnose, zoals 'fetal death', dan wel op het moment waarop de zwangerschap eindigde, nl. het moment van de 'stillbirth' of de 'termination of pregnancy'.
+ De zib mist een einddatum. Zib issue: EindDatum toevoegen aan rootconcept.
  + Deze zal kunnen worden gemapped op outcomeDate, maar alleen als de outcome het einde van de zwangerschap is en niet een diagnose! Zie het verzoek hierboven m.b.t. het EHDS element 'outcomeDate'.
+ In de zib ontbreekt een equivalent voor de outcome van een zwangerschap.
  + zib issue: voeg TypeZwangerschapseinde toe aan het rootconcept
    + Codelijst voor TypeZwangerschapsEinde:
      + Livebirth
      + Miscarriage
      + Stillbirth
      + Termination of pregnancy (bedoelen ze hier abortus provocatus? Wat evt. nog meer?) 	
  + zib issue: voeg verwijzing naar Diagnose toe aan rootconcept
    + let op: Diagnose en Zwangerschapseinde zitten ws niet in dezelfde 'versie' (instantiatie) van dezelfde zwangerschap.
    + Diagnose bij de moeder kan belangrijke context zijn voor de zwangerschap! Verwijzing naar diagnose bij moeder? Of gewoon in de toelichting?
    + Codelijst voor Diagnose:
      + Ectopic pregnancy
      + Hydatidiform mole, benign
      + Fetal death
      + Foetale nood
    + Uitgangspunt is dat er nog sprake is van zwangerschap zolang de vrucht het lichaam nog niet heeft verlaten.  
Verwijzing naar diagnose lijkt niet nodig (voor EHDS).
+ Waardenlijst bij EHDSPregnancyHistory.outcome
  + Newborn death: Dit betreft het kindje, dat binnen 28 dagen na de geboorte overlijdt. Het is dus geen einde van de zwangerschap, want het kindje kwam levend ter wereld. Men vindt het blijkbaar relevant om te weten of een zwangerschap al dan niet tot een geboorte van een kindje heeft geleid dat minstens 28 in leven is gebleven.
    + Verzoek voor EHDS verwijderen uit de lijst om de volgende redenen:
      + Het is geen einde van de zwangerschap: dat is nl. een live birth.
      + Newborn death wordt pas ná de zwangerschap bekend.
      + Het betreft een levend geboren kindje, dus een andere patiënt.


## Overall discussion
There are no matching concepts in the zib versus the Xt-EHR logical model.  
Commentaar Astrid:  
Blijkbaar gaat het hier om een instantiatie per zwangerschap in het verleden. Daarvoor kunnen we de zib niet gebruiken: er is geen 'outcome', omdat de zwangerschap nog gaande is.  
Er is geen overeenkomst in dataelementen.  




| zib                                                            | xtehr                                 | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:---------------------------------------------------------------|:--------------------------------------|:-----------|:----------------|:------------|:--------------|
| Pregnancy                                                      | EHDSPregnancyHistory                  |            |                 |             | 0..*          |
|                                                                | EHDSPregnancyHistory.presentedForm    |            | EHDSAttachment  |             | 0..*          |
|                                                                | EHDSPregnancyHistory.narrative        |            | string          |             | 0..1          |
|                                                                | EHDSPregnancyHistory.outcomeDate      |            | dateTime        |             | 0..1          |
|                                                                | EHDSPregnancyHistory.outcome          |            | CodeableConcept |             | 0..1          |
|                                                                | EHDSPregnancyHistory.numberOfChildren |            | integer         |             | 0..1          |
| Pregnancy.PregnancyDuration                                    |                                       | PQ         |                 | 0..1        |               |
| Pregnancy.Parity                                               |                                       | INT        |                 | 0..1        |               |
| Pregnancy.Gravidity                                            |                                       | INT        |                 | 0..1        |               |
| Pregnancy.Comment                                              |                                       | ST         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems                         |                                       |            |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |                                       | TS         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod        |                                       | CD         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation        |                                       | TS         |                 | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation    |                                       | TS         |                 | 0..1        |               |



## EHDSPregnancyHistory

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory |
| zib | Pregnancy |
| alias_zib | NL: Zwangerschap |
| card._xtehr | 0..* |
| definition_xtehr | Pregnancy history for one pregnancy |
| definition_zib | Root concept of the Pregnancy information model. This root concept contains all data elements of the Pregnancy information model. |
| definitioncode_zib | SNOMED CT: 118185001 Finding related to pregnancy |
| id_xtehr | EHDSPregnancyHistory |
| id_zib | NL-CM:7.14.1 |
| name_zib | Pregnancy |
| path_xtehr | EHDSPregnancyHistory |
| path_zib | Pregnancy |
| short_xtehr | Pregnancy history model |
| stereotype_zib | rootconcept |

### Comments



## EHDSPregnancyHistory.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSPregnancyHistory.presentedForm |
| path_xtehr | EHDSPregnancyHistory.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments



## EHDSPregnancyHistory.narrative

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.narrative |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Narrative description describing the outcome of any previous pregnancies. |
| id_xtehr | EHDSPregnancyHistory.narrative |
| path_xtehr | EHDSPregnancyHistory.narrative |
| short_xtehr | Narrative, potentially formatted, content of the section |
| type_xtehr | string |

### Comments



## EHDSPregnancyHistory.outcomeDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.outcomeDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date referred to the previous pregnancies outcome. |
| id_xtehr | EHDSPregnancyHistory.outcomeDate |
| path_xtehr | EHDSPregnancyHistory.outcomeDate |
| short_xtehr | Outcome date |
| type_xtehr | dateTime |

### Comments



## EHDSPregnancyHistory.outcome

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.outcome |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': '1.3.6.1.4.1.12559.11.10.1.3.1.42.62 eHDSIOutcomeOfPregnancy (SNOMED CT, used in MH@EU); 1.3.6.1.4.1.12559.11.10.1.3.1.42.63 eHDSIRareDisease (OrphaCodes, used in MH@EU); ICD-11; SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Outcome of the previous pregnancy. |
| id_xtehr | EHDSPregnancyHistory.outcome |
| path_xtehr | EHDSPregnancyHistory.outcome |
| short_xtehr | Outcome |
| type_xtehr | CodeableConcept |

### Comments



## EHDSPregnancyHistory.numberOfChildren

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPregnancyHistory.numberOfChildren |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Number of children/fetuses in this specific pregnancy |
| id_xtehr | EHDSPregnancyHistory.numberOfChildren |
| path_xtehr | EHDSPregnancyHistory.numberOfChildren |
| short_xtehr | Number of children/fetuses in this specific pregnancy |
| type_xtehr | integer |

### Comments



## zib: Pregnancy.PregnancyDuration

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.PregnancyDuration |
| alias_zib | NL: Zwangerschapsduur |
| card._zib | 0..1 |
| definition_zib | Duration of the pregnancy on the day on which the patient was asked. The duration can be given in days (d) or weeks (wk). |
| definitioncode_zib | SNOMED CT: 57036006 Fetal gestational age |
| id_zib | NL-CM:7.14.4 |
| name_zib | PregnancyDuration |
| path_zib | Pregnancy.PregnancyDuration |
| stereotype_zib | data |
| type_zib | PQ |

### Comments



## zib: Pregnancy.Parity

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.Parity |
| alias_zib | NL: Pariteit |
| card._zib | 0..1 |
| definition_zib | Number of previous pregnancies ending in partum (>= 16w 0d / 112 days). |
| definitioncode_zib | SNOMED CT: 364325004 Parity |
| id_zib | NL-CM:7.14.6 |
| name_zib | Parity |
| path_zib | Pregnancy.Parity |
| stereotype_zib | data |
| type_zib | INT |

### Comments



## zib: Pregnancy.Gravidity

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.Gravidity |
| alias_zib | NL: Graviditeit |
| card._zib | 0..1 |
| definition_zib | The number of times the woman has gotten pregnant (including this one). |
| definitioncode_zib | SNOMED CT: 161732006 Gravida |
| id_zib | NL-CM:7.14.5 |
| name_zib | Gravidity |
| path_zib | Pregnancy.Gravidity |
| stereotype_zib | data |
| type_zib | INT |

### Comments



## zib: Pregnancy.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comment on the pregnancy. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:7.14.7 |
| name_zib | Comment |
| path_zib | Pregnancy.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems |
| alias_zib | NL: ATermeDatumItems |
| card._zib | 0..1 |
| definition_zib | Container of the EstimatedDateOfDeliveryItems concept.This container contains all data elements of the EstimatedDateOfDeliveryItems concept. |
| id_zib | NL-CM:7.14.9 |
| name_zib | EstimatedDateOfDeliveryItems |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems |
| stereotype_zib | container |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| alias_zib | NL: ATermeDatum |
| card._zib | 0..1 |
| definition_zib | The date on which the pregnancy is expected to be 40w 0d (280 days). Different due dates are used at various points in the pregnancy. |
| definitioncode_zib | SNOMED CT: 161714006 Estimated date of delivery |
| id_zib | NL-CM:7.14.3 |
| name_zib | EstimatedDateOfDelivery |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod |
| alias_zib | NL: BepalingsMethode |
| card._zib | 0..1 |
| definition_zib | Method by which the delivery date is estimated. |
| id_zib | NL-CM:7.14.10 |
| name_zib | EstimatingMethod |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation |
| alias_zib | NL: DatumBepaling |
| card._zib | 0..1 |
| definition_zib | Date on which the delivery date is estimated. |
| id_zib | NL-CM:7.14.11 |
| name_zib | DateOfEstimation |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation |
| alias_zib | NL: DatumLaatsteMenstruatie |
| card._zib | 0..1 |
| definition_zib | The date on which the last menstruation started. |
| definitioncode_zib | SNOMED CT: 21840007 Date of last menstrual period |
| id_zib | NL-CM:7.14.8 |
| name_zib | DateLastMenstruation |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation |
| stereotype_zib | data |
| type_zib | TS |

### Comments

