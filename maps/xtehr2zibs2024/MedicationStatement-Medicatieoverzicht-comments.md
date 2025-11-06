# MedicationStatement
## issues (mail Astrid 31-10-2025)
EHDS Issue 1  
Model: Local

eu-nl-compared/maps/xtehr2zibs2024/EpisodeOfCare-EpisodeOfCare-comments.md at main · Nictiz/eu-nl-compared
https://github.com/Nictiz/eu-nl-compared/blob/main/maps/xtehr2zibs2024/EpisodeOfCare-EpisodeOfCare-comments.md

EHDSMedicationStatement  
"Verzoek: de waarden van medicationTreatmentStatus in lijn brengen met de definitie.
Het element medicationTreatmentStatus heeft als definitie 'The current status of the taking of medicine' en als type CodeableConcept. Als het om de current use gaat, dan kan de waarde alleen 'ja' of 'nee' zijn. Het verzoek is om de toegestane waarden van medicationTreatmentStatus daarmee in lijn te brengen."

EHDS Issue 2  https://github.com/Xt-EHR/xt-ehr-common/issues/361  
Model: EHDSMedicationStatement  
Verzoek: Toevoegen van twee elementen aan EHDSMedicationStatement met resp. een reference naar EHDSMedicationDispense en EHDSMedicationPrescription.  
In EHDSServiceRequest is het niet eenvoudig om het element dosageInstructions goed te interpreteren. Zoals het nu is gedefinieerd betreft dit feitelijk gebruik (is/was taken) of voorgeschreven gebruik (should be taken). Feitelijk gebruik kan afwijken van voorgeschreven gebruik. De patiënt kan minder gebruiken, meer gebruiken, eerder stoppen of het helemaal niet gebruiken. Hetzelfde geldt voor het element periodOfUse. Ook hier kan de periode van feitelijk gebruik afwijken van de voorgeschreven periode van gebruik.  
Er is behoefte aan duidelijkheid m.b.t. het voorgeschreven gebruik en het feitelijk gebruik.  
Die duidelijkheid kan worden verkregen door het volgende:
  1. Voor het voorgeschreven gebruik twee extra elementen opnemen:
Het ene element met een reference naar EHDSMedicationDispense voor de doseerinstructies zoals afgegeven door de apotheek en het andere element met een reference naar EHDSMedicationPrescription voor het oorspronkelijke voorschrift. In dit voorschrift zitten de doseerinstructies en de bedoelde periode van gebruik, zoals gespecificeerd door de voorschrijver.
  2. De elementen dosageInstructions en periodOfUse reserveren voor feitelijk gebruik in verleden of heden (separaat issue)

Op deze manier is de betekenis van de elementen eenduidig en heeft de gebruiker altijd inzicht in het feitelijk gebruik met een mogelijkheid om dit te vergelijken met het bedoelde (voorgeschreven) gebruik."

EHDS Issue 3 https://github.com/Xt-EHR/xt-ehr-common/issues/362
Model: EHDSMedicationStatement
Verzoek: naam en definitie wijzigen van 'dosageInstructions' naar 'actualDosage' met definitie 'Details of how medication is/was used.'

Het element 'dosageInstructions' is nu niet goed interpreteerbaar, omdat niet duidelijk is of het feitelijk gebruik betreft (is/was taken) of gebruik zoals voorgeschreven (should be taken). Het is wenselijk om dit element alleen te gebruiken voor feitelijk gebruik.
Het bedoelde gebruik van het geneesmiddel is beschikbaar als het verzoek wordt ingewilligd om twee elementen toe te voegen (separaat issue):
Het ene element met een reference naar EHDSMedicationDispense voor de doseerinstructies zoals afgegeven door de apotheek en het andere element met een reference naar EHDSMedicationPrescription voor de doseerinstructies van het oorspronkelijke voorschrift.
Zo kun je aangeven dat een patiënt een voorgeschreven middel anders gebruikt dan voorgeschreven of zelfs helemaal niet gebruikt. In het laatste geval is er een verwijzing naar het voorgeschreven geneesmiddel via EHDSMedicationPrescription, heeft medicationTreatmentStatus de waarde 'nee' en blijft het element dosageInstructions leeg."

EHDS Issue 4  
Model: EHDSMedicationStatement  
Verzoek: naam en definitie wijzigen van 'periodOfUse' naar 'actualPeriodOfUse' met definitie 'Period when patient took/is taking the medication.
Het element 'periodOfUse' is nu niet goed interpreteerbaar, omdat niet duidelijk is of het de feitelijke periode betreft (took, is taking) of de periode zoals voorgeschreven (is excpected to take). Het is wenselijk om dit element alleen te gebruiken voor de feitelijke periode van gebruik.  
De bedoelde periode van gebruik is beschikbaar als het verzoek wordt ingewilligd om een element met een reference naar EHDSMedicationPrescription toe te voegen (separaat issue) waarin de bedoelde periodOfUse is gespecificeerd.  
Zo is duidelijk of een patiënt een voorgeschreven middel in de voorgeschreven periode gebruikt of daarvan afwijkt (later of eerder is begonnen met gebruik).  
Als de patiënt het voorgeschreven geneesmiddel (nog) niet gebruikt, is er een verwijzing naar het voorgeschreven geneesmiddel via EHDSMedicationPrescription, heeft medicationTreatmentStatus de waarde 'nee' en blijft het element periodOfUse leeg."

EHDS Issue 5  
Model: EHDSMedicationStatement  
Verzoek: element 'intendeUseType' laten vervallen.  
Dit element is in feite een gegeven bij het medicatievoorschrift. Het element 'intendedUseType' is niet meer nodig als het verzoek wordt ingewilligd om een element in het model op te nemen (separaat issue) met een reference naar EHDSMedicationPrescription waarin intendedUseType wordt gespecificeerd."

EHDS Issue 6  
Model: EHDSMedicationStatement  
Verzoek: element 'medicationReason' laten vervallen.  
Dit element is in feite een gegeven bij het medicatievoorschrift. Het element 'medicationReason' is niet meer nodig als het verzoek (separaat issue) wordt ingewilligd om een element in het model op te nemen met een reference naar EHDSMedicationPrescription waarin de indicatie voor het voorgeschreven geneesmiddel wordt gespecificeerd."

Zib Issue 1  
Zib: MedicatieAfspraak  
Beschrijving:  
Het model EHDSMedicationStatement heeft een element intendedUseType, waarin kan worden aangegeven wat de intentie is voor het toepassen van het geneesmiddel, zoals profylactisch, curatief, palliatief, diagnostisch, etc.
Wellicht moeten wij on overleg met het veld nagaan of een dergelijk element ook wenselijk is in de zib MedicatieAfspraak."

Zib Issue 2
Zib: MedicatieGebruik
Beschrijving:  
De zib MedicatieGebruik is net als bij EHDSMedicationStatement bedoeld voor verleden, heden en toekomst. Het element GebruikIndicator is een boolean en kan geen onderscheid maken tussen verleden en toekomst. Om dit onderscheid wel te kunnen maken is een waardenlijst nodig.
De vraag is wat de betekenis is van MedicatieGebruik in de toekomst? Hoe verhoudt zich dit tot een ToedieningsAfspraak en/of een MedicatieAfspraak.






## Overleg 23-10
Aanwezig: Astrid, Sander, Evelyn, Tim S. en Yasmin
Medicationreason zou toegevoegd kunnen worden in de zib, maar vanwege de gevolgen voor de informatiestandaard is het ter overweging, anderzijds kan het beter zijn om alle veranderingen in 1 keer door te voeren (voor leveranciers) - issue aanmaken ter overweging
_Wordt vervolgd_

## discussie 21-10-2025 met Astrid, Jacob, Sander, Evelyn, Tim S.
+ zib TreatmentStatus en EHDS .UseIndicator zijn redundant met PeriodOfUse. Ieder afzonderlijk zijn ze goed te gebruiken. Issue EHDS: er is geen binding bij medicationTreatmentStatus. Waarschijnlijk meer dan alleen ja of nee, dan ook zib issue om dit aan te passen.

_Wordt vervolgd_

## Algemeen
Algemeen:
In deze mapping worden elementen uit > 1 zib gecombineerd. Bedenk dat je niet zonder meer de relatie tussen instantiaties van verschillende zibs kunt leggen op basis van het farmaceutisch product, want een patiënt kan meerdere keren in zijn leven, evt. met lange tussenpozen, hetzelfde farmaceutisch product gebruiken. Daarom is een expliciete relatie tussen instantiaties van verschillende zibs belangrijk!
De gewenste relaties zijn ook aan bod gekomen bij het architectuurteamoverleg.  

hHt is niet eenvoudig om het elementen dosageInstructions en periodOfUse goed te interpreteren. Zoals het nu is gedefinieerd betreft dit feitelijk gebruik (is/was taken) of voorgeschreven gebruik (should be taken). Feitelijk gebruik kan afwijken van voorgeschreven gebruik. De patiënt kan minder gebruiken, meer gebruiken, eerder stoppen of het helemaal niet gebruiken. Hetzelfde geldt voor het element periodOfUse. Ook hier kan de periode van feitelijk gebruik afwijken van de voorgeschreven periode van gebruik.
Er is behoefte aan duidelijkheid m.b.t. wat de patiënt volgens instructies zou moeten gebruiken en wat hij feitelijk gebruikt.
Die duidelijkheid kan worden verkregen door het volgende:  
  1. De elementen dosageInstructions en periodOfUse te reserveren voor feitelijk gebruik in verleden of heden.
  2. Voor het voorgeschreven gebruik twee extra elementen op te nemen: Het ene element met een reference naar EHDSMedicationDispense voor de doseerinstructies zoals afgegeven door de apotheek en het andere element met een reference naar EHDSMedicationPrescription voor het oorspronkelijke voorschrift. In dit voorschrift zitten de doseerinstructies en de bedoelde periode van gebruik, maar ook de indicatie (reden van voorschrijven)en het gebruiksdoel (intendedUseType), zoals gespecificeerd door de voorschrijver.

Op deze manier is de betekenis van de elementen eenduidig en heeft de gebruiker altijd inzicht in het feitelijk gebruik met een mogelijkheid om dit te vergelijken met het bedoelde (voorgeschreven) gebruik.
De elementen intendedUseType en medicationReason zijn dan niet meer nodig, omdat die inEHDSMedicationPrescription zitten.
Het element MedicationReasonText kan worden gebruikt om de reden van zelfmedicatie te representeren.



| zib                                                    | xtehr                                               | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-------------------------------------------------------|:----------------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| MedicationUse                                          | EHDSMedicationStatement                             |            |                        |             | 0..*          |
|                                                        | EHDSMedicationStatement.header                      |            | Base                   |             | 1..1          |
|                                                        | EHDSMedicationStatement.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                        | EHDSMedicationStatement.header.identifier           |            | Identifier             |             | 0..*          |
|                                                        | EHDSMedicationStatement.header.authorship           |            | Base                   |             | 1..*          |
|                                                        | EHDSMedicationStatement.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                                        | EHDSMedicationStatement.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                                        | EHDSMedicationStatement.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                        | EHDSMedicationStatement.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                        | EHDSMedicationStatement.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                        | EHDSMedicationStatement.header.language             |            | CodeableConcept        |             | 0..1          |
| MedicationUse.UseIndicator                             | EHDSMedicationStatement.medicationTreatmentStatus   | BL         | CodeableConcept        | 1           | 0..1          |
| MedicationUse.ProductUsed::PharmaceuticalProduct       | EHDSMedicationStatement.medication                  |            | EHDSMedication         | 1           | 1..1          |
| MedicationAgreement.PrescriptionReason.Diagnosis; MedicationAgreement.PrescriptionReason HypersensitivityIntolerance; MedicationAgreement.PrescriptionReason.Reaction; MedicationAgreement.PrescriptionReason.Symptom                                                       | EHDSMedicationStatement.medicationReason            |            | CodeableConcept        |             | 0..*          |
| MedicationUse.ReasonForUse                             | EHDSMedicationStatement.medicationReasonText        | ST         | string                 | 0..1        | 0..1          |
|                                                        | EHDSMedicationStatement.intendedUseType             |            | CodeableConcept        |             | 0..1          |
| MedicationUse.InstructionsForUse; AdministrationAgreement.InstructionsForUse; MedicationAgreement.InstructionsForUse                       | EHDSMedicationStatement.dosageInstructions          |            | EHDSDosaging           | 0..1        | 1..*          |
| MedicationUse.PeriodOfUse::TimeInterval                | EHDSMedicationStatement.periodOfUse                 |            | Period                 | 1           | 0..1          |
| MedicationUse.Prescriber::HealthProfessional           |                                                     |            |                        | 0..1        |               |
| MedicationUse.MedicationUseDateTime                    |                                                     | TS         |                        | 1           |               |
| MedicationUse.AsAgreedIndicator                        |                                                     | BL         |                        | 0..1        |               |
| MedicationUse.MedicationUseStopType                    |                                                     | CD         |                        | 0..1        |               |
| MedicationUse.ReasonModificationOrDiscontinuationOfUse |                                                     | CD         |                        | 0..*        |               |
| MedicationUse.Comment                                  |                                                     | ST         |                        | 0..1        |               |



## EHDSMedicationStatement

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement |
| zib | MedicationUse |
| alias_zib | NL: Medicatiegebruik |
| card._xtehr | 0..* |
| definition_xtehr | Statement about a single medication as part of a medication summary. |
| definition_zib | Root concept of the MedicationUse information model. This root concept contains all data elements of the MedicationUse information model. |
| definitioncode_zib | SNOMED CT: 422979000 Medication regimen behavior finding |
| id_xtehr | EHDSMedicationStatement |
| id_zib | NL-CM:9.11.21338 |
| name_zib | MedicationUse |
| path_xtehr | EHDSMedicationStatement |
| path_zib | MedicationUse |
| short_xtehr | Medication statement model |
| stereotype_zib | rootconcept |

### Comments





## EHDSMedicationStatement.medicationTreatmentStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.medicationTreatmentStatus |
| zib | MedicationUse.UseIndicator |
| alias_zib | NL: GebruikIndicator |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The current status of the taking of medicine |
| definition_zib | Is this medicine used or not? |
| id_xtehr | EHDSMedicationStatement.medicationTreatmentStatus |
| id_zib | NL-CM:9.11.22399 |
| name_zib | UseIndicator |
| path_xtehr | EHDSMedicationStatement.medicationTreatmentStatus |
| path_zib | MedicationUse.UseIndicator |
| short_xtehr | The current status of the taking of medicine |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | BL |

### Comments
Het zib element is een boolean. Men kan alleen aangeven of het medicament wordt gebruikt of niet. Het is niet duidelijk welke waarden gelden voor het EHDS element medicationTreatmentStatus. De definitie van medicationTreatmentStatus is 'The current status of the taking of medicine'. Dan kan de waarde alleen maar 'ja' of nee' zijn.   
Het verzoek aan EHDS is om de toegestane waarden van medicationTreatmentStatus daarmee in lijn te brengen.

## EHDSMedicationStatement.medication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.medication |
| zib | MedicationUse.ProductUsed::PharmaceuticalProduct |
| alias_zib | NL: Gebruiksproduct::FarmaceutischProduct |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Describes the medicinal product. |
| definition_zib | The product used. This is usually medication. Food, blood products, aids and bandages do not strictly fall under the category of medication, but can be recorded as well. <br><br>In principle, this will be the prescribed product, but the product used may differ from the prescribed product. |
| id_xtehr | EHDSMedicationStatement.medication |
| id_zib | NL-CM:9.11.21339 |
| name_zib | ProductUsed::PharmaceuticalProduct |
| path_xtehr | EHDSMedicationStatement.medication |
| path_zib | MedicationUse.ProductUsed::PharmaceuticalProduct |
| short_xtehr | Describes the medicinal product. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSMedication |

### Comments



## EHDSMedicationStatement.medicationReason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.medicationReason |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Coded reason for the use of the medication (typically diagnosis, or a procedure) |
| id_xtehr | EHDSMedicationStatement.medicationReason |
| path_xtehr | EHDSMedicationStatement.medicationReason |
| short_xtehr | Coded reason for the use of the medication (typically diagnosis, or a procedure) |
| type_xtehr | CodeableConcept |

### Comments
Mapt op: 
+ MedicationAgreement.PrescriptionReason.Diagnosis
+ MedicationAgreement.PrescriptionReason.HypersensitivityIntolerance
+ MedicationAgreement.PrescriptionReason.Reaction
+ MedicationAgreement.PrescriptionReason.Symptom  

Naast de genoemde Dagnosis, Hypersensitivity, Reaction en Symptom, kan ook een (voorgenomen) Procedure reden zijn voor medicatiegebruik.
De hier opgegeven verwijzingen naar zibs komen voor in de zib MedicatieAfspraak. Dat is een andere zib dan MedicatieGebruik. Het is belangrijk dat duidelijk is dat de instantiaties van deze twee zibs expliciet aan elkaar zijn gerelateerd! Zie ook de algemene opmerking bovenaan.  
Wat betreft EHDS kan dit element vervallen als het verzoek wordt ingewilligd om een element op te nemen met een reference naar EHDSMedicationPrescrition. Dit model bevat nl. de indicatie voor het voorgeschreven geneesmiddel.

## EHDSMedicationStatement.medicationReasonText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.medicationReasonText |
| zib | MedicationUse.ReasonForUse |
| alias_zib | NL: RedenGebruik |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Reason for the use of the medication (typically diagnosis, or a procedure) in free text. |
| definition_zib | The reason for using the medication, particularly in self-care medicine purchased by the patient themselves. |
| definitioncode_zib | SNOMED CT: 11611000146100 Reason for taking medication |
| id_xtehr | EHDSMedicationStatement.medicationReasonText |
| id_zib | NL-CM:9.11.22491 |
| name_zib | ReasonForUse |
| path_xtehr | EHDSMedicationStatement.medicationReasonText |
| path_zib | MedicationUse.ReasonForUse |
| short_xtehr | Reason for the use of the medication (typically diagnosis, or a procedure) in free text. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Dit kun je gebruiken als de patiënt op eigen initiatief medicatie gebruikt.



## EHDSMedicationStatement.intendedUseType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.intendedUseType |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The type of intended use of the medication, e.g. prophylactic, therapeutic, diagnostic, anesthesia, etc. |
| id_xtehr | EHDSMedicationStatement.intendedUseType |
| path_xtehr | EHDSMedicationStatement.intendedUseType |
| short_xtehr | The type of intended use of the medication, e.g. prophylactic, therapeutic, diagnostic, anesthesia, etc. |
| type_xtehr | CodeableConcept |

### Comments
Dit heb ik niet kunnen terugvinden in de zib(s). Dit moet mogelijk een plaats krijgen in de zib MedicatieAfspraak. Er is dan ook een relatie nodig tussen de zibs MedicatieGebruik em MedicatieAfspraak.
Dit element kan uit het EHDS model worden verwijderd  als het verzoek wordt ingewilligd om een element met een reference naar EHDSMedicationPrescription toe te voegen (separaat issue) waarin intendedUseType wordt gespecificeerd.




## EHDSMedicationStatement.dosageInstructions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.dosageInstructions |
| zib | MedicationUse.InstructionsForUse |
| alias_zib | NL: Gebruiksinstructie::GebruiksInstructie |
| card._xtehr | 1..* |
| card._zib | 0..1 |
| definition_xtehr | Details of how medication is/was taken or should be taken. This includes the number of units per intake and frequency of intake over a specified duration of time. Example: 1 tablet every 24h, for 10 days . |
| definition_zib | Instructions for the use of the medication, e.g. dose and route of administration. In the event of medication use, this is the pattern of use established by the patient or that the patient followed. |
| id_xtehr | EHDSMedicationStatement.dosageInstructions |
| id_zib | NL-CM:9.11.22504 |
| name_zib | InstructionsForUse |
| path_xtehr | EHDSMedicationStatement.dosageInstructions |
| path_zib | MedicationUse.InstructionsForUse |
| short_xtehr | Details of how medication is/was taken or should be taken |
| stereotype_zib | data,reference |
| type_xtehr | EHDSDosaging |

### Comments
Mapt op:
+ MedicationUse.InstructionsForUse
+ AdministrationAgreement.InstructionsForUse
+ MedicationAgreement.InstructionsForUse

Het element 'dosageInstructions' is nu niet goed interpreteerbaar, omdat niet duidelijk is of het feitelijk gebruik betreft (is/was taken) of gebruik zoals voorgeschreven (should be taken). Het is wenselijk om dit element alleen te gebruiken voor feitelijk gebruik.
Het bedoelde gebruik is beschikbaar als het verzoek wordt ingewilligd om twee elementen toe te voegen (separaat issue):
Het ene element met een reference naar EHDSMedicationDispense voor de doseerinstructies zoals afgegeven door de apotheek en het andere element met een reference naar EHDSMedicationPrescription voor de doseerinstructies van het oorspronkelijke voorschrift.  
Zo kun je ook aangeven dat een patiënt een voorgeschreven middel anders gebruikt als voorgeschreven of zelfs helemaal niet gebruikt. In het laatste geval is er wel een verwijzing naar het voorgeschreven geneesmiddel via EHDSMedicationPrescription, heeft medicationTreatmentStatus de waarde 'nee' en blijft het element dosageInstructions leeg.  
Verzoek aan EHDS is om de naam te wijzigen in 'actualDosage' met definitie 'Details of how medication is/was used.'



## EHDSMedicationStatement.periodOfUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedicationStatement.periodOfUse |
| zib | MedicationUse.PeriodOfUse::TimeInterval |
| alias_zib | NL: Gebruiksperiode::TijdsInterval |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Period when patient took, is taking or is expected to take the medication. This information may be expressed using start and end date times OR indicating the duration. The first is used to indicate a specified interval (e.g., from March 15th, 2017); the latter for indicating a 'floating' period (e.g., 2 weeks). In case of unbounded period (continuous therapy), the end element will be valued with an exceptional value. |
| definition_zib | Medication use can be recorded for a certain moment or over a certain period. Thus, medication use can be recorded multiple times during the use of medication. The usage period is the period or moment over which the data is recorded.<br>Start date: This is the time at which the agreement was to take effect (or took effect or will take effect). <br>Duration: The intended duration of use. E.g. 5 days or 8 weeks. It is not allowed to indicate the duration in months, because different months have a variable duration in days. <br>End date: The time at which the period of use ends (or ended or will end). To avoid confusion between 'to' and 'up until and including', the submission of time is always mandatory for the end date. |
| id_xtehr | EHDSMedicationStatement.periodOfUse |
| id_zib | NL-CM:9.11.22663 |
| name_zib | PeriodOfUse::TimeInterval |
| path_xtehr | EHDSMedicationStatement.periodOfUse |
| path_zib | MedicationUse.PeriodOfUse::TimeInterval |
| short_xtehr | Period when patient took, is taking or is expected to take the medication |
| stereotype_zib | data,reference |
| type_xtehr | Period |

### Comments
'periodOfUse' is nu niet goed interpreteerbaar, omdat niet duidelijk is of het de feitelijke periode betreft (took, is taking) of de periode zoals voorgeschreven (is excpected to take). Het is wenselijk om dit element alleen te gebruiken voor de feitelijke periode van gebruik.
De bedoelde periode van gebruik is beschikbaar als het verzoek wordt ingewilligd om een element met een reference naar EHDSMedicationPrescription toe te voegen (separaat issue) waarin de bedoelde periodOfUse is gespecificeerd.
Zo is ook duidelijk of een patiënt een voorgeschreven middel in de voorgeschreven periode gebruikt of daarvan afwijkt (later of eerder is begonnen met gebruik).
Als de patiënt het voorgeschreven geneesmiddel (nog) niet gebruikt, is er een verwijzing naar het voorgeschreven geneesmiddel via EHDSMedicationPrescription, heeft medicationTreatmentStatus de waarde 'nee' en blijft het element periodOfUse leeg.
Verzoek aan EHDS is om de naam te wijzigen in 'actualPeriodOfUse' met definitie 'Period when patient took/is taking the medication.'


## zib: MedicationUse.Prescriber::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationUse.Prescriber::HealthProfessional |
| alias_zib | NL: Voorschrijver::Zorgverlener |
| card._zib | 0..1 |
| definition_zib | The health professional that entered the medication agreement with the patient. |
| id_zib | NL-CM:9.11.23290 |
| name_zib | Prescriber::HealthProfessional |
| path_zib | MedicationUse.Prescriber::HealthProfessional |
| stereotype_zib | context,reference |

### Comments



## zib: MedicationUse.MedicationUseDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationUse.MedicationUseDateTime |
| alias_zib | NL: MedicatiegebruikDatumTijd |
| card._zib | 1 |
| definition_zib | Date on which this use is entered. |
| id_zib | NL-CM:9.11.22398 |
| name_zib | MedicationUseDateTime |
| path_zib | MedicationUse.MedicationUseDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: MedicationUse.AsAgreedIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationUse.AsAgreedIndicator |
| alias_zib | NL: VolgensAfspraakIndicator |
| card._zib | 0..1 |
| definition_zib | Is the medicine used as outlined in the medication agreement? |
| definitioncode_zib | SNOMED CT: 112221000146107 Patient takes medication as prescribed |
| id_zib | NL-CM:9.11.22492 |
| name_zib | AsAgreedIndicator |
| path_zib | MedicationUse.AsAgreedIndicator |
| stereotype_zib | data |
| type_zib | BL |

### Comments



## zib: MedicationUse.MedicationUseStopType

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationUse.MedicationUseStopType |
| alias_zib | NL: MedicatiegebruikStopType |
| card._zib | 0..1 |
| definition_zib | Stop type, the manner in which this medication is discontinued (temporary or definitive). |
| id_zib | NL-CM:9.11.23132 |
| name_zib | MedicationUseStopType |
| path_zib | MedicationUse.MedicationUseStopType |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: MedicationUse.ReasonModificationOrDiscontinuationOfUse

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationUse.ReasonModificationOrDiscontinuationOfUse |
| alias_zib | NL: RedenWijzigenOfStoppenGebruik |
| card._zib | 0..* |
| definition_zib | Reason for changing or discontinuing use of medication. |
| definitioncode_zib | SNOMED CT: 153861000146102 Reason for change of medication usage |
| id_zib | NL-CM:9.11.22493 |
| name_zib | ReasonModificationOrDiscontinuationOfUse |
| path_zib | MedicationUse.ReasonModificationOrDiscontinuationOfUse |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: MedicationUse.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicationUse.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comments on the medication use. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:9.11.21624 |
| name_zib | Comment |
| path_zib | MedicationUse.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments

