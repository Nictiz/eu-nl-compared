# MedicationStatement

## Algemeen
Algemeen:
In deze mapping worden elementen uit > 1 zib gecombineerd. Bedenk dat je niet zonder meer de relatie tussen instantiaties van verschillende zibs kunt leggen op basis van het farmaceutisch product, want een patiënt kan meerdere keren in zijn leven, evt. met lange tussenpozen, hetzelfde farmaceutisch product gebruiken. Daarom is een expliciete relatie tussen instantiaties van verschillende zibs belangrijk!
De gewenste relaties zijn ook aan bod gekomen bij het architectuurteamoverleg.


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
Het zib element is een boolean. Men kan alleen aangeven of het medicament wordt gebruitk of niet. Het is niet duidelijk welke waarden gelden voor het EHDS element medicationTreatmentStatus. Er zal wel overlap zijn van betekenis, maar ws niet volledig. Als je kijkt naar de definitie van PeriodOfUse in de zib MedicationUse dan is deze zib voor verleden, heden en toekomst bedoeld. In geval van verleden en toekomst kan een boolean geen onderscheid maken: de waarde is dan 0. Ik kan me voorstellen dat het EHDS model dit onderscheid wel maakt.
Afgezien van de waarden in het EHDS model is dit onderscheid wenselijk, want in het geval van 'verleden' en 'heden' moeten de InstructionForUse weegeven wat het feitelijk gebruik was/is en in het geval van 'toekomst' (planned) moeten de InstructionsForUse gebaseerd zijn op de MedicationAgreement/AdministrationAgreement.



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

Naast de genoemde Diagnosis, Hypersensitivity, Reaction en Symptom, kan ook een (voorgenomen) Procedure reden zijn voor medicatiegebruik.  
De hier opgegeven verwijzingen naar zibs komen voor in de zib MedicatieAfspraak. Dat is een andere zib dan MedicatieGebruik. Het is belangrijk dat duidelijk is dat de instantiaties van deze twee zibs expliciet aan elkaar zijn gerelateerd!  
Zie ook de algemene opmerking bovenaan.



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
Dit heb ik niet kunnen terugvinden in de zib(s).




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

Alle drie de zibs (MedicatieAfspraak, ToedieningsAfspraak en MedicatieGebruik) hebben een verwijzing naar GebruiksInstructie. Als er een MedicatieAfspraak/ToedieningsAfspraak is, zou de patiënt zich daaraan moeten houden, maar de patiënt kan ook zelf het initiatief nemen tot medicatiegebruik.  
Het lijkt hier in het EHDS logical model te gaan om het feitelijk medicatiegebruik, tenzij het in de toekomst ligt.  
Als de medicatie in gebruik is, lijkt het element MedicationUse.InstructionsForUse de beste match.  
Als het geneesmiddel in de toekomst moet worden gebruikt, dan lijken de instructies op basis van een MedicatieAfspraak/ToedieninsgAfspraak van toepassing.  Het is dan wenselijk dat deze relatie expliciet is, zodat je uit instantiaties van verschillende zibs de juiste combineert om de gegevens voor dit EHDS model aan te leveren.
Zie ook de algemene opmerking bovenaan.




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
In de zib wordt in de definitie van dit element gesproken over de 'intended duration of use', maar in het EHDS model lijkt het (ook) te gaan over de feitelijke periode van gebruik. Mogelijk moet dit in de definitie in de zib worden aangepast.


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

