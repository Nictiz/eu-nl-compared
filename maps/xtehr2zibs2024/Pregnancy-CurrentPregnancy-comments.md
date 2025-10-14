# CurrentPregnancy
## Bespreking 14-10
+ EHDSCurrentPregnancy.gestationalAge en Zwangerschapsduur in de zib: dit concept hoort niet in het model. Gestational age kan worden afgeleid (40 wk minus het aantal weken tussen ATermeDatum en Statusdatum). Hier maken we een consultatie-issue van en een zib-issue. 
+ EHDSCurrentPregnancy.dateOfStatus: dit concept ontbreekt in de zib, maar is wel essentieel, omdat ook de zib het karakter van een _observatie_ heeft. StatusDatum moet aan het rootconcept worden toegevoegd. DatumBepaling (van de a-terme datum) lijkt niet nodig in de zib (is metadata). Hier maken we een zib-issue van.

+ In zowel de zib als EHDSCurrentPregnancy ontbreekt het aantal foetussen. We maken er een zib issue en een consultatie-issue van.
+ In EHDSCurrentPregnancy ontbreken graviditeit en pariteit. Die kunnen in principe worden afgeleid uit de aanwezige instanties van EHDSPregnancyHistory, maar het afleiden van de pariteit is niet eenvoudig. We maken er geen consultatie-issue van en voor de zib moeten we overwegen om ze ergens anders onder te brengen: het zijn immers geen eigenschappen van de zwangerschap.

## Overall discussion
The zib has all (logical) concepts of the Xt-EHR model except for .currentPregnancyStatus, with which it is possible to express, for example, that the subject is not pregnant. The zib has Gravidity, Parity, and several concepts to express the data on which the EstimatedDateOfDelivery is based which the Xt-EHR model has not. 
Note that the Xt-EHR model models an *observation* regarding pregnance at .dateOfStatus. In its current form, it is not clear whether the zib models an observation or a condition.  
  
Commentaar Astrid:  
Wel vreemd dat zowel in het Xt-EHR logical model als in de zib geen element is opgenomen, waarin wordt aangegeven of het om 1 of meerdere foetussen gaat.  


| zib                                                            | xtehr                                            | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:---------------------------------------------------------------|:-------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| Pregnancy                                                      | EHDSCurrentPregnancy                             |            |                        |             | 0..*          |
|                                                                | EHDSCurrentPregnancy.currentPregnancyStatus      |            | CodeableConcept        |             | 1..1          |
|                                                                | EHDSCurrentPregnancy.dateOfStatus                |            | dateTime               |             | 0..1          |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery | EHDSCurrentPregnancy.expectedDateOfDelivery      | TS         | date                   | 0..1        | 0..1          |
| Pregnancy.PregnancyDuration                                    | EHDSCurrentPregnancy.gestationalAge              | PQ         | Quantity               | 0..1        | 0..1          |
| Pregnancy.Comment                                              | EHDSCurrentPregnancy.narrative                   | ST         | string                 | 0..1        | 0..1          |
|                                                                | EHDSCurrentPregnancy.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| Pregnancy.EstimatedDateOfDeliveryItems                         |                                                  |            |                        | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateLastMenstruation    |                                                  | TS         |                        | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.DateOfEstimation        |                                                  | TS         |                        | 0..1        |               |
| Pregnancy.EstimatedDateOfDeliveryItems.EstimatingMethod        |                                                  | CD         |                        | 0..1        |               |
| Pregnancy.Gravidity                                            |                                                  | INT        |                        | 0..1        |               |
| Pregnancy.Parity                                               |                                                  | INT        |                        | 0..1        |               |



## EHDSCurrentPregnancy

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy |
| zib | Pregnancy |
| alias_zib | NL: Zwangerschap |
| card._xtehr | 0..* |
| definition_xtehr | Current pregnancy status |
| definition_zib | Root concept of the Pregnancy information model. This root concept contains all data elements of the Pregnancy information model. |
| definitioncode_zib | SNOMED CT: 118185001 Finding related to pregnancy |
| id_xtehr | EHDSCurrentPregnancy |
| id_zib | NL-CM:7.14.1 |
| name_zib | Pregnancy |
| path_xtehr | EHDSCurrentPregnancy |
| path_zib | Pregnancy |
| short_xtehr | Current pregnancy status model |
| stereotype_zib | rootconcept |

### Comments



## EHDSCurrentPregnancy.currentPregnancyStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.currentPregnancyStatus |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 1..1 |
| definition_xtehr | Current state of the pregnancy at the date the observation was made, e.g. pregnant, not pregnant, unknown. |
| id_xtehr | EHDSCurrentPregnancy.currentPregnancyStatus |
| path_xtehr | EHDSCurrentPregnancy.currentPregnancyStatus |
| short_xtehr | Current pregnancy status |
| type_xtehr | CodeableConcept |

### Comments
Absent in the zib. In general, absence of conditions are not modelled in the zibs itself.
Note: the presence of this concept indicates that the model is to be interpreted as an *observation*.


## EHDSCurrentPregnancy.dateOfStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.dateOfStatus |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Effective date of the current pregnancy status. |
| id_xtehr | EHDSCurrentPregnancy.dateOfStatus |
| path_xtehr | EHDSCurrentPregnancy.dateOfStatus |
| short_xtehr | Effective date of the current pregnancy status. |
| type_xtehr | dateTime |

### Comments
Absent in the zib. See .currentPregnancyStatus.
Note: the presence of this concept indicates that the model is to be interpreted as an *observation*.


## EHDSCurrentPregnancy.expectedDateOfDelivery

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.expectedDateOfDelivery |
| zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| alias_zib | NL: ATerme |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date in which the woman is due to give birth. Year, day and month are required. |
| definition_zib | The date on which the pregnancy is expected to be 40w 0d (280 days). Different due dates are used at various points in the pregnancy. |
| definitioncode_zib | SNOMED CT: 161714006 Estimated date of delivery |
| id_xtehr | EHDSCurrentPregnancy.expectedDateOfDelivery |
| id_zib | NL-CM:7.14.3 |
| name_zib | EstimatedDateOfDelivery |
| path_xtehr | EHDSCurrentPregnancy.expectedDateOfDelivery |
| path_zib | Pregnancy.EstimatedDateOfDeliveryItems.EstimatedDateOfDelivery |
| short_xtehr | Date in which the woman is due to give birth. Year, day and month are required. |
| stereotype_zib | data |
| type_xtehr | date |
| type_zib | TS |

### Comments
Match but the zib definition is more specific. 


## EHDSCurrentPregnancy.gestationalAge

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.gestationalAge |
| zib | Pregnancy.PregnancyDuration |
| alias_zib | NL: Zwangerschapsduur |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Gestational age - duration of the pregnancy on the day on which the patient was asked or at the delivery. The duration can be given in weeks and/or days. |
| definition_zib | Duration of the pregnancy on the day on which the patient was asked. The duration can be given in days (d) or weeks (wk). |
| definitioncode_zib | SNOMED CT: 57036006 Fetal gestational age |
| id_xtehr | EHDSCurrentPregnancy.gestationalAge |
| id_zib | NL-CM:7.14.4 |
| name_zib | PregnancyDuration |
| path_xtehr | EHDSCurrentPregnancy.gestationalAge |
| path_zib | Pregnancy.PregnancyDuration |
| short_xtehr | Duration of the pregnancy at this day |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments
Match. This concept is not present in the EHDS WP 6.1 stakeholder consultation branch.  
Commentaar Astrid:  
Dit zou de mapping m.i. moeten zijn, maar dat blijkt onvoldoende uit de definitie van het element in de zib en het voorbeeld. In het Xt-EHR logical model lijkt het dat de zwangerschapsduur betrekking heeft op de dateOfStatus. Zo niet, dan zegt gestationalAge weinig.  
In de zib hebben we helemaal geen Status, alleen een datum waarop de à terme datum is bepaald. Daardoor is de zwangerschapsduur een vaag gegeven, want de datum waarop die is gevraagd is onbekend en hoe betrouwbaar is het om deze duur te 'vragen', zeker als de patiënt het antwoord moet geven. Je zou verwachten dat de zwangerschapsduur afgeleid kan worden op basis van 40 wk minus het aantal weken tussen ATermeDatum en Statusdatum. Het lijkt me betrouwbaarder om een StatusDatum te hebben en op basis van functionaliteit de zwangerschapsduur te bepalen dan een zwangerschapduur te 'vragen' zonder StatusDatum.  
Het voorbeeld bij de zib is niet eenvoudig te intrpreteren: als de zwangerschapsduur 24 wk is, dan moet de StatusDatum dus liggen op ATermeDatum - (40 wk - 24 wk) = 18-09-2014.
Neem in overweging om een StatusDatum op te nemen, waarbij Zwangerschapsduur dan een afgeleid gegeven is.  




## EHDSCurrentPregnancy.narrative

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.narrative |
| zib | Pregnancy.Comment |
| alias_zib | NL: Toelichting |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Narrative description describing the status of the current pregnancy. |
| definition_zib | Comment on the pregnancy. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSCurrentPregnancy.narrative |
| id_zib | NL-CM:7.14.7 |
| name_zib | Comment |
| path_xtehr | EHDSCurrentPregnancy.narrative |
| path_zib | Pregnancy.Comment |
| short_xtehr | Textual description of current pregnancy status |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Commentaat Astrid:  
Geen goede match: het element 'narrative' is een tekstuele weergave van de huidige zwangerschap als geheel. Het element 'comment' van de zib is bedoeld voor gegevens die niet te representeren zijn met de gestructureerde elementen van de zib.


## EHDSCurrentPregnancy.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCurrentPregnancy.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSCurrentPregnancy.presentedForm |
| path_xtehr | EHDSCurrentPregnancy.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments
This concept is absent in the zib as per design principles. This concept is not present in the EHDS WP6.1 stakeholder consultation branch.  




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
Commentaar Astrid:  
Zie mijn opmerking bij PregnancyDuration. Laten we overleggen of DateOfEstimation zou moeten gelden als StatusDatum en aan het rootconcept zou moeten hangen. In ieder geval moeten de ATermeDatum en de Zwangerschapsduur consistent zijn met elkaar.  


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

