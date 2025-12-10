# MedicationAdministration
## Overzicht issues
EHDS Issue 1 https://github.com/Xt-EHR/xt-ehr-common/issues/414    
Model: EHDSMedicationAdministration  
Vraag: Bij een infuus kan de toedieningssnelheid worden gewijzigd. Klopt het dat een instantantiatie van het Xt-EHR logical model EHDSMedicationAdministration een toedieningsperiode representeert waarbinnen de toedieningssnelheid, i.e. EHDSdosage.rate gelijk blijft?  

EHDS Issue 2 ingediend in Imaging consultatie   
Model: EHDSMedicationAdministration  
Vraag: Wat is precies de betekenis van het element 'rateRatio' in de context van EHDSMedicationAdministration.EHDSDosage? Is het A of B of iets anders?  
A: de hoeveelheid infuusvloeistof die inloopt per tijdseenheid
B: de hoeveelheid werkzame stof die inloopt per tijdseenheid

EHDS Issue 3 ingediend in Imaging consultatie    
Model: EHDSMedicationAdministration  
Vraag/verzoek:  
Gegevens voor het element EHDSMedicationAdministration.Reason[x] omvatten nu reasonEHDSCondition, reasonEHDSObservation en reasonCodableConcept. We willen ook graag een verrichting (Procedure) als reden voor de medicatietoediening kunnen opgeven. Zijn jullie bereid om een verwijzing naar Procedure op te nemen of moeten we dan gebruik maken van reasonCodableConcept?"

Zib Issue 1 - https://nictiz.atlassian.net/browse/ZIB-2883  
Samenvatting: Hoe definiëren we Toedieningssnelheid?      
Betreft zib: MedicatieToediening2        
Beschrijving: De zib MedicatieToediening omvat ook infusen. De zib bevat het element Toedieningssnelheid . Dit betekent dat de zib in feite een infuusfase representeert waarin de toedieningssnelheid van het infuus niet verandert. Dit betekent dat elke wijziging van de loopsnelheid een nieuwe instantiatie vergt.    

De vraag is wat de precieze betekenis is van het element Toedieningssnelheid. Er zijn twee mogelijkheden:  
1. De hoeveelheid vloeistof die per tijdseenheid inloopt.  
2. De hoeveelheid werkzame stof die per tijdseenheid inloopt.  

De meest wenselijke betekenis is 2: de hoeveelheid werkzame stof die per tijdseenheid inloopt. Dan kun je nl. in combinatie met de ToegediendeHoeveelheid de duur afleiden dat deze loopsnelheid van toepassing was zonder informatie over de concentratie van de werkzame stof in de toedienvloeistof.  
Als de Toedieningssnelheid de hoeveelheid vloeistof per tijdseenheid representeert, heb je de concentratie werkzame stof in de infuusvloeistof nodig om de periode van inloop af te leiden óf je moet een apart element toevoegen om de inloopperiode weer te geven."  
"Het EHDS model heeft een verwijzing naar EHDSDosage met element 'rate' dat weer bestaat uit de elementen 'rateRatio' en 'rateQuantity'. Het element 'rateRatio' lijkt overeen te komen met het element 'Toedieningssnelheid' in de zib. Op basis hiervan lijkt het Xt_EHR logical model ook uit te gaan van een toedieningsperiode, waarbinnen de toedieningssnelheid gelijk blijft.  
Ook hier geldt dat we precies de betekenis moeten weten van het element rateRatio in de context van EHDSMedicationAdministration.EHDSDosage: gaat het hier om de hoeveelheid vloeistof per tijdseenheid of de hoeveelheid werkzame stof per tijdseenheid? Als we dit weten, moeten we overleggen wat te doen in de zib: de betekenis van Toedieningssnelheid in lijn brengen met EHDS of een andere aanpassing die het aanleveren van de juiste waarde voor het element rateRatio mogelijk maakt.  

Zib Issue 2 - zib-2915  
Samenvatting: Hoe omgaan met toedieningsperiode in EHDSMedicationAdministration in MedicatieToediening2?  
Betreft zib: MedicatieToediening2  
Beschrijving: Als na duidelijkheid over de betekenis van 'rateRatio' in de context van EHDSMedicationAdministration.EHDSDosage het element Toedieningssnelheid de hoeveelheid werkzame stof per tijdseenheid representeert, verdient het aanbeveling om voor aanlevering de periode af te leiden op basis van de combinatie met het element ToegediendeHoeveelheid.
Andersom kunnen we bij ontvangst van de periode en de hoeveelheid werkzame stof per tijdseenheid de ToegediendeHoeveelheid afleiden.
Het toevoegen van een element ToedieningsPeriode met een afleidbare waarde brengt het risico mee van inconsistentie met de waarden van Toedieningssnelheid en ToegediendeHoeveelheid.  

Als Toedieningssnelheid de hoeveelheid vloeistof per tijdseenheid weergeeft, dan hebben we wel een element ToedieningsPeriode met een verwijzing naar TijdsInterval nodig om een waarde voor het element EHDSMedicationAdministration.occurrence[x].occurrencePeriod te kunnen aanleveren.  

Zib Issue 3 - zib-2881  
Samenvatting: Kardinaliteit van RedenVanVoorschrijven van 0..1 naar 0..*?    
Betreft zib: MedicatieAfspraak    
Beschrijving: Het model EHDSMedicationAdministration heeft een element reason [x] met kardinaliteit 0..*.  
RedenVanVoorschrijven in MedicatieAfspraak heeft kardinaliteit 0..1.  Dat is geen probleem bij aanleveren van gegevens, maar bij nadere overweging, lijkt het terecht om de kardinaliteit van RedenVanVoorschrijven te wijzigen naar 0..*. Er kan nl. meer dan één reden zijn om iets voor te schrijven.    

Zib Issue 4 - zib-2917  
Samenvatting: RedenVanVoorschrijven uitbreiden met een verwijzing naar Verrichting?    
Betreft zib: MedicatieAfspraak    
Beschrijving:  
Een verrichting kan een reden van voorschrijven zijn: het gaat dan om medicatie voorafgaand aan of tijdens een verrichting, zoals bijv. antibioticaprofylaxe of pijnstilling. Daarom graag overwegen om de RedenVanVoorschrijven uit te breiden met een verwijzing naar Verrichting.  

Zib Issue 5 - zib-2918    
Samenvatting: waar past reason[x] van EHDSMedicationAdministration in de zibs?    
Betreft zib: MedicatieToediening2      
Beschrijving: Voor het aanleveren van gegevens voor reason[x] in model EHDSMedicationAdministration lijkt er geen probleem. We zouden daarvoor RedenVanVoorschrijven van MedicatieAfspraak kunnen gebruiken onder de aanname dat MedicatieToediening2 een RedenVanToediening met keuzebox krijgt met de mogelijkheid om te verwijzen naar ToedieningsAfspraak óf MedicatieAfspraak (is ook besproken in het architectuurteamoverleg).  
Als er echter via EHDSMedicationAdministration gegevens binnenkomen via element reason[x] hoe passen die dan in de zibs? We hebben dan geen medicatieAfspraak waarin we deze gegevens kunnen opnemen en er is geen element voor in MedicatieToediening2. Als we er in MedicatieToediening2 wel een element voor zouden opnemen dan mag er geen conflict zijn met de RedenVanVoorschrijven in een MedicatieAfspraak.    
Wellicht moeten we overwegen om aan de voorgenomen keuzebox voor RedenVanToediening een element toe te voegen (naam ToedieningsReden?) dat alleen gevuld mag zijn als er geen verwijzing naar ToedieningsAfspraak of MedicatieAfspraak mogelijk is.  


## Bespreking 21-10-2025 met Astrid, Sander, Evelyn, Tim S., Jacob
+ Toediener ontbreekt in EHDS model maar gezien het gebruik van het model is dat logisch. We maken er geen issue van
+ EHDS model: onduidelijk of de toedieningssneldheid de oplossing of de werkzame stof bevat.
    + ==> zib issue, EHDS issue
+ De reden van voorschrijven staat in de zibs in MedicatieAfspraak, maar de kardinaleit is te krap -> zib issue  

21-10-2025 

| zib                                                                          | xtehr                                                    | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-----------------------------------------------------------------------------|:---------------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| MedicationAdministration                                                     | EHDSMedicationAdministration                             |            |                        |             | 0..*          |
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
Onder .occurrence[x] vallen:
+ EHDSMedicationAdministration.occurrence[x].OccurrenceDateTime: match met MedicationAdministration.AdministrationDateTime
+ EHDSMedicationAdministration.occurrence[x].Period : de zib heeft hier geen datatelement voor, terwijl de zib ook infusen dekt. Ws. heeft het element AdministrationDateTime in de zib in dat geval betrekking op het begimoment van de toediening.  
Het lijkt me goed om te overwegen in de zib een element op te nemen met een verwijzing naar TijdsInterval.



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
Onder dosage (verwijzing naar EHDSDosage) vallen:
+ EHDSDosage.dosageDescription
+ EHDSDosage.site - mapt op MedicationAdministration.AdministrationLocation::AnatomicalLocation.Location
    + Het valt op dat in het Xt-EHR logical model wordt verwezen naar alleen een body site als CodableConcept. Laterality wordt dus buiten beschouwing gelaten. Dat is alleen voldoende betrouwbaar als alle toedieningslocaties waarbij lateraliteit nodig is, beschikbaar zijn in geprecoördineerde vorm.
+ EHDSDosage.route - mapt op MedicationAdministration.RouteOfAdministration
+ EHDSDosage.method 
    + In het Xt-EHR logical model is onvoldoende duidelijk wat precies met Method wordt bedoeld.
+ EHDSDosage.dose = mapt op MedicationAdministration.AdministeredAmount
+ EEHDSDosage.rate[x] - mapt op MedicationAdministration.AdministeringSpeed
    + In het Xt-EHR model wordt 'rate' beschreven als 'dose quantity per unit of time). Dat lijkt overeen te komen met de zib.
    + Onder .rate vallen:
        + EHDSDosage.rate[x].rateRatio - Jacob: bijvoorbeeld 5 ml per 24 uur?
        + EHDSDosage.rate[x].rateQuantity - mapt op zib .AdministeringSpeed





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
Zie EHDSMedicationAdministration.dosage



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
Zie EHDSMedicationAdministration.dosage



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
Zie EHDSMedicationAdministration.dosage



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
Is de verwijzing naar de sub-zib AnatomicalLocation. Het gebruikte element daarvan is Location.
Zie EHDSMedicationAdministration.dosage



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
Astrid: Is onderdeel van de 'header' sectie. Patiënt is impliciet het onderwerp waarop de instantiatie van de zib betrekking heeft.  
Jacob: maar dit is Patient in de rol van Toediener. Daar voorziet het EHDS model dus niet in.




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
Hier gaat het niet om de reden voor toediening als zodanig, maar om de reden waarom er een afwijkende toediening heeft plaatsgevonden.

