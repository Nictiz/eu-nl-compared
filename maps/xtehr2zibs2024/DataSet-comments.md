# DataSet

## Actions
- Vraag EHDS: Verduidelijking van auteur. Is dat de informatiebron of de vastlegger?
*Should author be interpreted as the original creator of the information content (the source of truth), or as the person/system who entered or issued the resource in a particular EHR? When data is transferred or reused across    systems, the distinction between the original author (the creator of the content) and the recorder (the one who entered or reissued the information) becomes important. Does author represent the original information source or the responsible recorder within the receiving system?*
- Zib issue: Term auteur past wellicht niet goed bij de omschrijving (verantwoorelijke). Hoewel de term bij EHDS hetzelfde is, zou het wat anders kunnen betekenen.
- Vraag EHDS: Verduidelijking datetime. Date and time of the issuing the document/resource by its author, is dat het moment van vastleggen (eenmalig) of registratie in een bepaald systeem? *Does datetime refer to the time of    original issuance or to the time of recording/import in the receiving system?*
- Vraag EHDS: Wat voor business identifier is dit? *Should the business identifier be understood as identifying a specific instantiation of the resource, or the underlying business concept that the resource represents?*
  *Should the business identifier be understood as identifying the business object itself (the conceptual entity) or a particular instantiation or occurrence of that object within the system?*
- Zib issue: Language misschien toevoegen
- Zib issue: Last update misschien toevoegen
- Vraag EHDS: Verduidelijking status

## Discussion

- de patient is impliciet in de zibs?
- de zib heeft veel meer velden
  - de zib RegistrationData is nog niet in de praktijk getoetst, moeten we dan die extra velden inbrengen in XtEHR?
  - of misschien een of een paar velden wel?
- absentReason zit in de zib, in XtEHR zit dit ofwel in valueSets ofwel pas in FHIR (meestal het eerste)
- identificatie is 0..1 in de zib en 0..* in XtEHR
- XtEHR heeft 'language' - dus van de resource zelf, is dit een nuttige toevoeging?

| zib                                                   | xtehr                                   | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:------------------------------------------------------|:----------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| RegistrationData                                      | EHDSDataSet                             |            |                        |             | 0..*          |
| RegistrationData                                      | EHDSDataSet.header                      |            | Base                   |             | 1..1          |
|                                                       | EHDSDataSet.header.authorship           |            | Base                   |             | 1..*          |
| RegistrationData.Author::HealthProfessional           | EHDSDataSet.header.authorship.author[x] |            | EHDSHealthProfessional | 1           | 1..1          |
| RegistrationData.RegistrationDateTime                 | EHDSDataSet.header.authorship.datetime  | TS         | dateTime               | 1           | 1..1          |
| RegistrationData.IdentificationNumber                 | EHDSDataSet.header.identifier           | II         | Identifier             | 0..1        | 0..*          |
|                                                       | EHDSDataSet.header.language             |            | CodeableConcept        |             | 0..1          |
|                                                       | EHDSDataSet.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                                       | EHDSDataSet.header.status               |            | CodeableConcept        |             | 1..1          |
|                                                       | EHDSDataSet.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                                       | EHDSDataSet.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                                       | EHDSDataSet.header.version              |            | string                 |             | 0..1          |
|                                                       | EHDSDataSet.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| RegistrationData.AcquisitionDateTime                  |                                         | TS         |                        | 0..1        |               |
| RegistrationData.AcquisitionMethod                    |                                         | ST         |                        | 1           |               |
| RegistrationData.CopyIndicator                        |                                         | BL         |                        | 1           |               |
| RegistrationData.DatTimeOfClosure                     |                                         | TS         |                        | 0..1        |               |
| RegistrationData.InformationSource                    |                                         |            |                        | 0..1        |               |
| RegistrationData.InformationSource.ContactPerson      |                                         |            |                        | (0..1)      |               |
| RegistrationData.InformationSource.HealthProfessional |                                         |            |                        | (0..1)      |               |
| RegistrationData.InformationSource.Patient            |                                         |            |                        | (0..1)      |               |
| RegistrationData.ReasonDataAbsent                     |                                         | CD         |                        | 0..1        |               |
| RegistrationData.ReasonForClosing                     |                                         | ST         |                        | 0..1        |               |
| RegistrationData.RegistrationReason                   |                                         | ST         |                        | 0..1        |               |



## EHDSDataSet

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet |
| zib | RegistrationData |
| alias_zib | NL: RegistratieGegevens |
| card._xtehr | 0..* |
| definition_xtehr | Common elements (including header) for all documents and their independently functioning parts, e.g FHIR resources. |
| definition_zib | Root concept of the RegistrationData process data information model. This root concept contains all data elements of the RegistrationData process data information model. |
| id_xtehr | EHDSDataSet |
| id_zib | NL-CM:22.1.1 |
| name_zib | RegistrationData |
| path_xtehr | EHDSDataSet |
| path_zib | RegistrationData |
| short_xtehr | DataSet model |
| stereotype_zib | rootconcept |

### Comments



## EHDSDataSet.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header |
| zib | RegistrationData |
| alias_zib | NL: RegistratieGegevens |
| card._xtehr | 1..1 |
| definition_xtehr | Common header for all patient-related data |
| definition_zib | Root concept of the RegistrationData process data information model. This root concept contains all data elements of the RegistrationData process data information model. |
| id_xtehr | EHDSDataSet.header |
| id_zib | NL-CM:22.1.1 |
| name_zib | RegistrationData |
| path_xtehr | EHDSDataSet.header |
| path_zib | RegistrationData |
| short_xtehr | Common header for all patient-related data |
| stereotype_zib | rootconcept |
| type_xtehr | Base |

### Comments
Is de header bedoeld voor de informatiebron of de registratie?


## EHDSDataSet.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship |
| zib |  |
| card._xtehr | 1..* |
| definition_xtehr | Resource authoring details |
| id_xtehr | EHDSDataSet.header.authorship |
| path_xtehr | EHDSDataSet.header.authorship |
| short_xtehr | Authorship |
| type_xtehr | Base |

### Comments
Meerdere auteurs lijkte me problematisch. Wie is er verantwoordelijk voor een registratie als er > 1 auteur is?
Is de auteur degene die de gegevens vastgeled/geregistereerd heeft, of ben je (ook) auteur als je de gegevens overgenomen hebt?
Verdere verduidelijking gewenst: Wanneer ben je een auteur en wanneer niet? Gaat het om de informatiebron of de vastlegger? Belangrijk om de verschillen met de zib te identificeren.
In de zib gaat het alleen om registratiegegevens en niet om composities. In de zib zou verantwoordelijke wellicht beter passen i.p.v. auteur, o.b.v. huidig gebruik. Het gaat namelijk niet per se over wie het geschreven heeft.
FHIR Provernance biedt meerdere opties.
Hoe kan een organisatie een auteur zijn?
Waarom is de auteur verplicht en waarom is het mogelijk om meerdere auteurs te hebben?

## EHDSDataSet.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship.author[x] |
| zib | RegistrationData.Author::HealthProfessional |
| alias_zib | NL: Auteur::Zorgverlener |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| definition_zib | The author is the one who is responsible for recording information or having information recorded in the medical record.
It concerns not only own observations, but also information received from third parties. The author has decided to include the information in the medical record, and if necessary with source reference. |
| id_xtehr | EHDSDataSet.header.authorship.author[x] |
| id_zib | NL-CM:22.1.2 |
| name_zib | Author::HealthProfessional |
| path_xtehr | EHDSDataSet.header.authorship.author[x] |
| path_zib | RegistrationData.Author::HealthProfessional |
| short_xtehr | Author |
| stereotype_zib | data,reference |
| type_xtehr | EHDSHealthProfessional |

### Comments
De zib Zorgverlener dekt geen Device. (De zib registratiegegevens dekt geen device)

EHDSDataSet.header.authorship.author[x] .authorEHDSHealthProfessional					Zib Zorgverlener representeert HealthProfessional, maar de match tussen Zorgverlener en EHDSHealthProfessional valt onder een aparte verschillenanalyse.
EHDSDataSet.header.authorship.author[x] .authorEHDSOrganisation					Zib Zorgverlener omvat verwijzing naar Zorgaanbieder, maar de match tussen ZorgAanbieder en EHDSOrganisation valt onder een andere verschillenanalyse.
EHDSDataSet.header.authorship.author[x] .authorEHDSDevice

## EHDSDataSet.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.authorship.datetime |
| zib | RegistrationData.RegistrationDateTime |
| alias_zib | NL: RegistratieDatumTijd |
| card._xtehr | 1..1 |
| card._zib | 1 |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| definition_zib | Date and time when the information was recorded in the patient record. |
| id_xtehr | EHDSDataSet.header.authorship.datetime |
| id_zib | NL-CM:22.1.3 |
| name_zib | RegistrationDateTime |
| path_xtehr | EHDSDataSet.header.authorship.datetime |
| path_zib | RegistrationData.RegistrationDateTime |
| short_xtehr | Date and time of authoring/issuing |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Of dit overeenkomt met de zib is afhankelijk van de definitie van author. Is dit het moment dat het vastgelegd is in een systeem (nieuwe of overgenomen informatie)? Daar lijkt het op vanwege het woord issuing, en dan zou het overeenkomen met de zib.
Uit de definitie van author lijkt het eerder het moment van schrijven, zodat deze datum en de auteur niet meer veranderen als de informatie in een ander systeem overgenomen wordt.


## EHDSDataSet.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.identifier |
| zib | RegistrationData.IdentificationNumber |
| alias_zib | NL: Identificatienummer |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Business identifier for the object |
| definition_zib | Globally unique number that identifies the instantiation of the information model. The number is composed of an identification of the issuer organization and a unique number assigned by this organization. |
| definitioncode_zib | SNOMED CT: 396278008 Identification number |
| id_xtehr | EHDSDataSet.header.identifier |
| id_zib | NL-CM:22.1.12 |
| name_zib | IdentificationNumber |
| path_xtehr | EHDSDataSet.header.identifier |
| path_zib | RegistrationData.IdentificationNumber |
| short_xtehr | Business identifier for the object |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | II |

### Comments
We moeten overleggen of het wenselijk is om meerdere identifiers te hebben, bijv. een identifier van een verzender als alias. Hierover staat een issue open. Er lijkt een informatiebehoefte te zijn voor het vastleggen van meerdere identifiers. De vraag is eigenlijk: wat is erop tegen om er meerdere vast te leggen?
Wat voor identifier is dit? Gaat het alleen om de instantiatie of over het onderliggende concept?

## EHDSDataSet.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.language |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| id_xtehr | EHDSDataSet.header.language |
| path_xtehr | EHDSDataSet.header.language |
| short_xtehr | Language |
| type_xtehr | CodeableConcept |

### Comments
Zou toegevoegd kunnen worden in de zib, maar de relevantie zou beter uitgezocht moeten worden. Is registratiegegevens de goede plek daarvoor? Hoe gaat dat veranderen als met zibs 2.0 ook de uitwisseling gedekt moet zijn?


## EHDSDataSet.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.lastUpdate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time of the last update to the document/information |
| id_xtehr | EHDSDataSet.header.lastUpdate |
| path_xtehr | EHDSDataSet.header.lastUpdate |
| short_xtehr | Date and time of the last update to the resource |
| type_xtehr | dateTime |

### Comments
Als een gegeven veranderd, is het dan een nieuwe registratie of een aangepaste registratie? Veranderd daarmee ook de datumtijd of alleen dit veld?
In de zib wordt er geen onderscheid gemaakt voor datumtijd (nieuw of aangepast), misschien zal de zib de oude datumtijd overschrijven bij een aanpassing. 


## EHDSDataSet.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.status |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Status of the resource |
| id_xtehr | EHDSDataSet.header.status |
| path_xtehr | EHDSDataSet.header.status |
| short_xtehr | Status of the resource |
| type_xtehr | CodeableConcept |

### Comments
"Als het zib element DatTimeOfClosure (m.i. typefout in naam) gevuld is, impliceert dit een statuswaarde: nl. dat vanaf dat moment de instantiatie niet meer van toepassing is.
We moeten ons afvragen of het wenselijk is  dat RegistratieGegevens een wat algemener element krijgt voor de status van de instantiatie."
Verdere verduidelijking gewenst: Wat is status?

## EHDSDataSet.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.statusReason[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Reason for the current status of the resource. |
| id_xtehr | EHDSDataSet.header.statusReason[x] |
| path_xtehr | EHDSDataSet.header.statusReason[x] |
| short_xtehr | Reason for the current status of the resource. |
| type_xtehr | CodeableConcept |

### Comments
Zeer beperkte match: betreft alleen de reden voor een instantiatie met een afgesloten status. Als we kiezen voor een algemenr element Status in de zib RegistratieGegevens dan moet de reden voor die status ook algemener zijn.


## EHDSDataSet.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient/subject information |
| id_xtehr | EHDSDataSet.header.subject |
| path_xtehr | EHDSDataSet.header.subject |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments
De verwijzing naar Patient is impliciet in de zib.


## EHDSDataSet.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.header.version |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Business version of the resource. |
| id_xtehr | EHDSDataSet.header.version |
| path_xtehr | EHDSDataSet.header.version |
| short_xtehr | Version |
| type_xtehr | string |

### Comments
Dit gegevenselement zie ik niet terug in het XT-EHR logical model.


## EHDSDataSet.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDataSet.presentedForm |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| id_xtehr | EHDSDataSet.presentedForm |
| path_xtehr | EHDSDataSet.presentedForm |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| type_xtehr | EHDSAttachment |

### Comments
Dit gegevenselement zie ik niet terug in het XT-EHR logical model.


## zib: RegistrationData.AcquisitionDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.AcquisitionDateTime |
| alias_zib | NL: DatumTijdVanVerkrijgen |
| card._zib | 0..1 |
| definition_zib | Date and when relevant time when the information became available. This may be an earlier time than the date/time when the information was entered in the patient record. |
| id_zib | NL-CM:22.1.9 |
| name_zib | AcquisitionDateTime |
| path_zib | RegistrationData.AcquisitionDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: RegistrationData.AcquisitionMethod

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.AcquisitionMethod |
| alias_zib | NL: WijzeVanVerkrijgen |
| card._zib | 1 |
| definition_zib | The way in which the information is obtained by the patient record holder. |
| id_zib | NL-CM:22.1.8 |
| name_zib | AcquisitionMethod |
| path_zib | RegistrationData.AcquisitionMethod |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: RegistrationData.CopyIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.CopyIndicator |
| alias_zib | NL: KopieIndicator |
| card._zib | 1 |
| definition_zib | Indication that the data has been obtained from the EPR of another healthcare professional/healthcare provider. |
| id_zib | NL-CM:22.1.11 |
| name_zib | CopyIndicator |
| path_zib | RegistrationData.CopyIndicator |
| stereotype_zib | data |
| type_zib | BL |

### Comments



## zib: RegistrationData.DatTimeOfClosure

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.DatTimeOfClosure |
| alias_zib | NL: AfsluitDatumTijd |
| card._zib | 0..1 |
| definition_zib | Date and time at which it is recorded in the patient record that the information is no longer relevant, for example because the information is outdated, no longer requires attention, etc. |
| id_zib | NL-CM:22.1.5 |
| name_zib | DatTimeOfClosure |
| path_zib | RegistrationData.DatTimeOfClosure |
| stereotype_zib | data |
| type_zib | TS |

### Comments
Het lijkt me dat EHDS een StatusDateTime zou moeten hebben, zodat duidelijk is vanaf wanneer de statuswaarde van toepassing is.


## zib: RegistrationData.InformationSource

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource |
| alias_zib | NL: Informatiebron |
| card._zib | 0..1 |
| definition_zib | Container of the InformationSource concept.This container contains all data elements of the InformationSource concept.
If the recorded information has not been assessed by the attending physician, the source of the information can be recorded. |
| id_zib | NL-CM:22.1.13 |
| name_zib | InformationSource |
| path_zib | RegistrationData.InformationSource |
| stereotype_zib | container |

### Comments
Ik kan me voorstellen dat het wenselijk is om de bron van een gegeven te weten. Bespreken of we dit willen inbrengen bij EHDS.


## zib: RegistrationData.InformationSource.ContactPerson

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.ContactPerson |
| alias_zib | NL: Contactpersoon |
| card._zib | (0..1) |
| definition_zib | The contact person who is the source of the information. |
| id_zib | NL-CM:22.1.15 |
| name_zib | ContactPerson |
| path_zib | RegistrationData.InformationSource.ContactPerson |
| stereotype_zib | data,reference |

### Comments



## zib: RegistrationData.InformationSource.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| card._zib | (0..1) |
| definition_zib | The health professional who is the source of the information. |
| id_zib | NL-CM:22.1.14 |
| name_zib | HealthProfessional |
| path_zib | RegistrationData.InformationSource.HealthProfessional |
| stereotype_zib | data,reference |

### Comments



## zib: RegistrationData.InformationSource.Patient

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.InformationSource.Patient |
| alias_zib | NL: Patient |
| card._zib | (0..1) |
| definition_zib | The patient as information source |
| id_zib | NL-CM:22.1.16 |
| name_zib | Patient |
| path_zib | RegistrationData.InformationSource.Patient |
| stereotype_zib | data,reference |

### Comments



## zib: RegistrationData.ReasonDataAbsent

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.ReasonDataAbsent |
| alias_zib | NL: RedenAfwezigheidGegevens |
| card._zib | 0..1 |
| definition_zib | Reason why no data is available for the value of a concept. This includes, for example, all 'Unknown' variants, but also 'Indeterminate', 'Specimen unsatisfactory', etc. |
| id_zib | NL-CM:22.1.10 |
| name_zib | ReasonDataAbsent |
| path_zib | RegistrationData.ReasonDataAbsent |
| stereotype_zib | data |
| type_zib | CD |

### Comments



## zib: RegistrationData.ReasonForClosing

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.ReasonForClosing |
| alias_zib | NL: RedenVanAfsluiten |
| card._zib | 0..1 |
| definition_zib | Reason why updating the information, or following changes in the the concept in question is no longer considered relevant. For example, in the case of a condition, this does not mean that the disease is no longer present, but merely that the holder of the patients record no longer considers the condition as an aspect to be taken into account during care provision. |
| id_zib | NL-CM:22.1.6 |
| name_zib | ReasonForClosing |
| path_zib | RegistrationData.ReasonForClosing |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: RegistrationData.RegistrationReason

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | RegistrationData.RegistrationReason |
| alias_zib | NL: RedenVanVastleggen |
| card._zib | 0..1 |
| definition_zib | Description of the reason for including the information in the patient record. |
| id_zib | NL-CM:22.1.4 |
| name_zib | RegistrationReason |
| path_zib | RegistrationData.RegistrationReason |
| stereotype_zib | data |
| type_zib | ST |

### Comments

