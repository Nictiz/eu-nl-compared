# ServiceRequest
## Actions
EHDS Issue 1
Model: algemeen
"Verzoek: apart element buiten de header voor de verantwoordelijk/uitvoerend zorgverlener naast header.authorship.author[x].
In een deel van de EHDS modellen is de auteur in de header gescheiden van een health professional met een specifieke rol: zo heeft Condition de auteur in de header, maar ook daarnaast expliciet de 'asserter' (diagnosesteller).
Andere EHDS modellen hebben alleen het element auteur in de header met een verwijzing naar zorgverlener. Het lijkt niet wenselijk om een gegeven in de header een dubbelrol te geven, waarbij het twee betekenissen moet representeren. Het is wenselijk om naast het element in de header voor de administratieve verantwoordelijkheid als auteur (die voor elk model geldt) een apart element te hebben voor de zorgverlener die verantwoordelijk is voor een interpretatie, een besluit of het uitvoeren van een activiteit."

*Request: Add a separate element outside the header for the responsible/executing healthcare professional, in addition to header.authorship.author[x]. 
In some EHDS models, the author in the header is distinguished from a healthcare professional with a specific role — for example, the Condition model has the author in the header but also explicitly defines the asserter (the clinician who made the diagnosis).
Other EHDS models only have the author element in the header, referring to a healthcare professional.
It seems undesirable for a single element in the header to serve a dual purpose, representing both administrative authorship and clinical responsibility. It would be preferable to have, alongside the header element that expresses administrative authorship (applicable to all models), a separate element for the healthcare professional responsible for interpretation, decision-making, or execution of an activity.*

EHDS Issue 2
Model: EHDSServiceRequest
"verzoek: toevoegen van een een apart element 'Aanvrager'.
Het is wenselijk om naast het element in de header voor de administratieve verantwoordelijkheid als auteur (die voor elk model geldt) een apart element te hebben voor de zorgverlener die verantwoordelijk is voor een interpretatie, een besluit of het uitvoeren van een activiteit.
In het kader van EHDSServiceRequest is er behoefte aan een apart element 'Aanvrager'."

*In addition to the header element expressing administrative authorship (which applies to all models), it is desirable to include a separate element for the healthcare professional responsible for interpretation, decision-making, or the performance of an activity.
In the context of the EHDSServiceRequest, there is a specific need for an element representing the requester.*

EHDS Issue 3
Model: EHDSServiceRequest
Vraag: Wat is de betekenis van reasonReferenceEHDSMedication? Gaat het hier om het toedienen vanmedicatie, waarbij die toediening de aangevraagde service (verrichting) vergt? Zo nee, hoe kan medicatie dan een reden zijn voor het aanvragen van de service?

*Question: What is the meaning of reasonReferenceEHDSMedication?
Does it refer to the administration of medication, where that administration requires the requested service (procedure)?
If not, how can medication be a reason for requesting the service?*

EHDS Issue 4
Model: EHDSServiceRequest
"Verzoek: toevoegen van een element voor de status van de voortgang van de aanvraag. Dit gegeven is belangrijk voor het bepalen van de volgende stap in het afhandelen van de aanvraag.
In de header zit een veld 'status', maar dat element komt in elk Xt-EHR logical model voor.
Er zijn modellen waar naast header.status ook een apart element is voor de conceptspecifieke status, zoals het element diagnosisAssertionStatus in EHDSCondition.
Het is belangrijk dat EHDS in haar logical models de administratieve status in de headersectie apart modelleert van een conceptspecifieke status die vaak ook een specifieke waardenlijst heeft.
De valueset EventStatus (FHIR) geeft weer aan wat voor status er behoefte is. "

*Request: Add an element representing the status of the progress of the request.
This information is important for determining the next step in processing the request.
There is a status field in the header, but that element appears in every Xt-EHR logical model.
Some models, however, include a separate concept-specific status in addition to header.status, such as the element diagnosisAssertionStatus in EHDSCondition.
It is important that EHDS logical models distinguish between: an administrative status (in the header section), and a concept-specific status, which often uses its own specific value set.
The FHIR EventStatus value set illustrates the type of status that would be needed here.*

EHDS Issue 5
Model: EHDSServiceRequest
"Probleem: Er lijkt op basis van de 'mouse-over' informatie overlap in betekenis tussen de elementen reasonCode en supportingInformation. Bij een 'reden' denk je al gauw aan de indicatie voor de aangevraagde service. Voor die indicatie is er al het element reasonReference.
Het verzoek is om één van de volgende opties te overwegen:
1. reasonCode verwijderen als de betekenis wordt gedekt door de combinatie van reasonReference[x] en supportingInformation
2. Als reasonCode bestaanrecht heeft, een duidelijk onderscheid maken tussen de betekenis van de elementen reasonCode, reasonReference[x]en supportingInformation. Daarbij is dan ook het verzoek om de naam van   reasonCode aan te passen, zodat het niet de indicatie voor de aangevraagde service suggereert."

*Problem: Based on the “mouse-over” descriptions, there appears to be an overlap in meaning between the elements reasonCode and supportingInformation.
When reading reason, one naturally thinks of the indication for the requested service — but that is already represented by the element reasonReference.
Request: Consider one of the following options:
Remove reasonCode if its meaning is already covered by the combination of reasonReference[x] and supportingInformation.
If reasonCode remains justified, clearly distinguish between the meanings of reasonCode, reasonReference[x], and supportingInformation. In that case, it is also requested to rename reasonCode to avoid suggesting that it represents the indication for the requested service.*

EHDS Issue 6
Model: EHDSServiceRequest
"Verzoek: toevoegen van element AanvraagIngediendDatumTijd.
Het moment van indienen van een aanvraag hoeft niet per se gelijk te zijn aan het moment waarop de aanvraag wordt aangemaakt. Het lijkt wenselijk om in EHDSServiceRequest een expliciet element te hebben met het moment waarop de aanvraag is ingediend naast de registratiedatum/tijd van de aanvraag (authorship.dateTime)."

*The moment when a request is submitted is not necessarily the same as the moment when it is created.
It seems desirable for EHDSServiceRequest to include an explicit element representing the time of submission of the request, in addition to the registration date/time (authorship.dateTime).*

Zib Issue 1
Zib: AanvraagGegevens
"Beschrijving:
Het is vreemd dat de zib Aanvrager geen gegevens heeft m.b.t. het tijdinterval waarin de aangevraagde activiteit moet worden uitgevoerd. Dit is een essentieel onderdeel van een aanvraag om te zorgen voor een goede planning."

Zib Issue 2
Zib: AanvraagGegevens
"Supporting information betreft medisch inhoudelijke informatie die belangrijk is voor het uitvoeren van een verrichting en/of het interpreteren van de resulteten daarvan (nuchter zijn, houdingsbeperkingen, Malampati score, diabetes, etc.). Deze informatie wordt in de praktijk inderdaad bij een aanvraag meegegeven. Vanuit het perspectief van de use-case 'Aanvraag' zijn deze gegevens relevant, maar horen deze gegevens dan conceptueel bij de aanvraag (het proces) of bij de verrichting?
Het is niet duidelijk of RedenAanvraag deze informatie dekt. Als dat zo is, is de naam van het element niet echt intuïtief, want je denkt al gauw aan de indicatie voor de aangevraagde activiteit."
## Overall discussion
Er zijn slechts 3 equivalente concepten.
De zib heeft meer procesinformatie (indiener van het verzoek, status van het verzoek). Wel opmerkelijk dat een belangrijk procesgegeven, namelijk "when service should occur" ontbreekt in de zib en wel aanwezig is in het LM.
Het EHDS LM heeft meer gestructureerde informatie over datgene dat wordt verzocht, de reden van het verzoek, en de ondersteunende informatie. De zib heeft hier vrije tekst velden voor.
Opmerkelijk dat de indiener en het tijdstip van indienen in het EHDS model ontbreken. De informatie in de header geldt, zou je zeggen, alleen voor de _registratie_ van het verzoek.


"Algemeen:
Je ziet hier dat het Xt_EHR logical model een combinatie is van gegevens m.b.t. wát er wordt gevraagd en gegevens van het aanvraagproces.
In de zibs is dit gescheiden: de zib verrichting is bedoeld voor verleden en toekomst en de gegevens m.b.t. het aanvraagproces zijn gemodelleerd in het procespatroon AanvraagGegevens.
De mapping tussen EHDSServiceRequest en de zibs omvat daarom zowel het procespatroon AanvraagGegevens als de zib Verrichting."


| zib                                     | xtehr                                          | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:----------------------------------------|:-----------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| OrderData                               | EHDSServiceRequest                             |            |                        |             | 0..*          |
|                                         | EHDSServiceRequest.header                      |            | Base                   |             | 1..1          |
|                                         | EHDSServiceRequest.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                         | EHDSServiceRequest.header.identifier           |            | Identifier             |             | 0..*          |
|                                         | EHDSServiceRequest.header.authorship           |            | Base                   |             | 1..*          |
|                                         | EHDSServiceRequest.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                         | EHDSServiceRequest.header.authorship.datetime  |            | dateTime               |             | 1..1          |
|                                         | EHDSServiceRequest.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                         | EHDSServiceRequest.header.status               |            | CodeableConcept        |             | 1..1          |
|                                         | EHDSServiceRequest.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                         | EHDSServiceRequest.header.language             |            | CodeableConcept        |             | 0..1          |
| OrderData.ClinicalQuestion              | EHDSServiceRequest.serviceText                 | ST         | string                 | 0..1        | 0..1          |
|                                         | EHDSServiceRequest.serviceCode                 |            | CodeableConcept        |             | 0..1          |
| OrderData.OrderReason                   | EHDSServiceRequest.reasonCode                  | ST         | CodeableConcept        | 0..1        | 0..*          |
|                                         | EHDSServiceRequest.quantity                    |            | Quantity               |             | 0..1          |
|                                         | EHDSServiceRequest.anatomicLocation            |            | EHDSBodyStructure      |             | 0..*          |
|                                         | EHDSServiceRequest.reasonReference[x]          |            | EHDSObservation        |             | 0..*          |
|                                         | EHDSServiceRequest.priority                    |            | CodeableConcept        |             | 0..1          |
| OrderData.Comment                       | EHDSServiceRequest.supportingInformation[x]    | ST         | EHDSObservation        | 0..1        | 0..*          |
|                                         | EHDSServiceRequest.specimen                    |            | EHDSSpecimen           |             | 0..*          |
|                                         | EHDSServiceRequest.encounter                   |            | EHDSEncounter          |             | 0..1          |
|                                         | EHDSServiceRequest.occurrence[x]               |            | dateTime               |             | 0..1          |
|                                         | EHDSServiceRequest.patientInstructions         |            | string                 |             | 0..1          |
|                                         | EHDSServiceRequest.coverage                    |            | EHDSCoverage           |             | 0..*          |
| OrderData.Requester::HealthProfessional |                                                |            |                        | 1           |               |
| OrderData.OrderDateTime                 |                                                | TS         |                        | 1           |               |
| OrderData.OrderId                       |                                                | II         |                        | 1           |               |
| OrderData.Status                        |                                                | CD         |                        | 1           |               |



## EHDSServiceRequest

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest |
| zib | OrderData |
| alias_zib | NL: AanvraagGegevens |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Specification of requested service or services |
| definition_zib | Root concept of the OrderData process data information model.This root concept contains all data elements of the OrderData process data information model. |
| id_xtehr | EHDSServiceRequest |
| id_zib | NL-CM:22.2.1 |
| name_zib | OrderData |
| path_xtehr | EHDSServiceRequest |
| path_zib | OrderData |
| short_xtehr | Service request model |
| stereotype_zib | rootconcept |

### Comments






## EHDSServiceRequest.serviceText

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.serviceText |
| zib | OrderData.ClinicalQuestion |
| alias_zib | NL: Vraagstelling |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Textual description of the requested service |
| definition_zib | Description of the question to which the requester hopes to receive an answer. This is especially important for actions whose outcome requires interpretation from the performer. |
| id_xtehr | EHDSServiceRequest.serviceText |
| id_zib | NL-CM:22.2.6 |
| name_zib | ClinicalQuestion |
| path_xtehr | EHDSServiceRequest.serviceText |
| path_zib | OrderData.ClinicalQuestion |
| short_xtehr | Service text |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Matige match: een vraag waarop een antwoord wordt verwacht (Zib) is niet hetzelfde als de omschrijving van de gevraagde dienst (EHDS). 


## EHDSServiceRequest.serviceCode

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.serviceCode |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'LOINC, NPU, SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | A code that identifies a particular service (i.e., procedure, diagnostic investigation, or panel of investigations) that have been requested. |
| id_xtehr | EHDSServiceRequest.serviceCode |
| path_xtehr | EHDSServiceRequest.serviceCode |
| short_xtehr | Service code |
| type_xtehr | CodeableConcept |

### Comments
Dit lijkt goed mapbaar op Verrichting.VerrichtingType


## EHDSServiceRequest.reasonCode

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.reasonCode |
| zib | OrderData.OrderReason |
| alias_zib | NL: RedenAanvraag |
| binding_xtehr | {'strength': 'preferred', 'description': 'ICD-10 (ICD-11 when available), SNOMED CT, Orphacode'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Health conditions affecting the health of the patient and are important to be known for a health professional during a health encounter. Clinical conditions of the subject relevant for the results interpretation. |
| definition_zib | Context of the order, which is relevant for the execution. |
| id_xtehr | EHDSServiceRequest.reasonCode |
| id_zib | NL-CM:22.2.5 |
| name_zib | OrderReason |
| path_xtehr | EHDSServiceRequest.reasonCode |
| path_zib | OrderData.OrderReason |
| short_xtehr | Reason code |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | ST |

### Comments
EHDS heeft hier een gecodeerd concept, zib heeft vrije tekst. NB definitie en naam van het zib concept passen niet bij elkaar. De reden van het verzoek hoeft niet relevant te zijn voor de uitvoering.

"OrderData.OrderReason is geen goede match door het verschil in datatype. 

De naam van het element RedenAanvraag in de zib AanvraagGegevens is ongelukkig gekozen, gegeven de bijbehorende definitie. Bij een reden van een Aanvraag denkt men intuïtief aan de indicatie voor hetgeen is aangevraagd. Deze indicatie is nu gemodelleerd bij de zib Verrichting zelf. We moeten ons afvragen of er een naam te vinden is die de lading beter dekt."

## EHDSServiceRequest.quantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.quantity |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Amount of requested services of the same type |
| id_xtehr | EHDSServiceRequest.quantity |
| path_xtehr | EHDSServiceRequest.quantity |
| short_xtehr | Quantity |
| type_xtehr | Quantity |

### Comments



## EHDSServiceRequest.anatomicLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.anatomicLocation |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Anatomic location and laterality where the procedure should be performed. This is the target site. |
| id_xtehr | EHDSServiceRequest.anatomicLocation |
| path_xtehr | EHDSServiceRequest.anatomicLocation |
| short_xtehr | Anatomic location |
| type_xtehr | EHDSBodyStructure |

### Comments
"M.i. kan hier Verrichting.VerrichtingAnatomischeLocatie:AnatomischeLocatie als match dienen.
"


## EHDSServiceRequest.reasonReference[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.reasonReference[x] |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Indicates another resource that provides a justification for why this service is being requested. |
| id_xtehr | EHDSServiceRequest.reasonReference[x] |
| path_xtehr | EHDSServiceRequest.reasonReference[x] |
| short_xtehr | Reason reference |
| type_xtehr | EHDSObservation |

### Comments
Afwezig in de zib: zib heeft OrderReason maar dat context die relevant is voor de uitvoering.

reasonReferenceEHDSObservation "M.i. is de juiste match de Indicatie van de aangevraagde Verrichting. Bij een Symptoom betreft dat:
Verrichting.Indicatie.Symptoom.SymptoomNaam

reasonReferenceEHDSCondition "M.i. is de juiste match de Indicatie van de aangevraagde Verrichting. Bij een Diagnose of een Reactie betreft dat:
Verrichting.Indicatie.Diagnose.DiagnoseNaamGegevens.DiagnoseNaam
of
Verrichting.Indicatie.Reactie.DiagnoseNaamGegevens.DiagnoseNaam

reasonReferenceEHDSMedication Niet duidelijk wat hier wordt bedoeld. Het betreft 'prescribed/dispensed' medication'. Is dit een reden voor de aanvraag? We moeten aan EHDS vragen wat hier precies wordt bedoeld. Als het gaat om het toedienen van medicatie, waarbij die toediening een verrichting vergt, dan is het begrijpelijk, maar dit blijkt niet uit de 'mouse-over'.



## EHDSServiceRequest.priority

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.priority |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Request priority'} |
| card._xtehr | 0..1 |
| definition_xtehr | Indicates how quickly the ServiceRequest should be addressed with respect to other requests. |
| id_xtehr | EHDSServiceRequest.priority |
| path_xtehr | EHDSServiceRequest.priority |
| short_xtehr | Priority |
| type_xtehr | CodeableConcept |

### Comments



## EHDSServiceRequest.supportingInformation[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.supportingInformation[x] |
| zib | OrderData.Comment |
| alias_zib | NL: Opmerking |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Health conditions relevant for the results interpretation, e.g. fasting status, sex for clinical use, etc. |
| definition_zib | Additional information that is important for the execution of the order and which cannot be described in any of the other elements. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSServiceRequest.supportingInformation[x] |
| id_zib | NL-CM:22.2.8 |
| name_zib | Comment |
| path_xtehr | EHDSServiceRequest.supportingInformation[x] |
| path_zib | OrderData.Comment |
| short_xtehr | Supporting information |
| stereotype_zib | data |
| type_xtehr | EHDSObservation |
| type_zib | ST |

### Comments
Slechte match: de zib heeft alleen een ongestructureerd veld voor alle additionele informatie, die niet in de overige velden van de zib past, waaronder ook informatie die het EHDS model _wel_ gemodelleerd heeft.

"Puntje van aandacht: supporting information wordt in de praktijk inderdaad bij een aanvraag meegegeven. Vanuit het perspectief van de use-case 'Aanvraag' zijn deze gegevens relevant, maar zijn het procesgegevens? De gegevens zijn van belang voor de interpretatie van de resultaten, maar kunnen ook van belang zijn voor de uitvoering. Hoort het dan conceptueel bij de aanvraag of bij de verrichting?
Er is overlap in betekenis tussen reasonCode en supportingInformation. reasonCode moet vervallen óf een duidelijk andere betekenis hebben dan supportingInformation en in dat geval moet de naam zodanig zijn dat niet de indruk wordt gewekt dat het om de indicatie gaat voor aangevraagde activiteit."

"Geen goede match met supportingInformation om twee redenen:
1. AanvraagGegevens.Opmerking is breder dan alleen gegevens die van belang zijn voor de interpretatie van de resultaten.
2. Mismatch in datatype en kardinaliteit. Bij een opmerking in vrije tekst heeft een kardinaliteit > 1 uiteraard geen zin."


## EHDSServiceRequest.specimen

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.specimen |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Specimens to be used by the laboratory procedure |
| id_xtehr | EHDSServiceRequest.specimen |
| path_xtehr | EHDSServiceRequest.specimen |
| short_xtehr | Specimen |
| type_xtehr | EHDSSpecimen |

### Comments



## EHDSServiceRequest.encounter

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.encounter |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | An encounter that provides additional information about the healthcare context in which this request is made. |
| id_xtehr | EHDSServiceRequest.encounter |
| path_xtehr | EHDSServiceRequest.encounter |
| short_xtehr | Encounter |
| type_xtehr | EHDSEncounter |

### Comments



## EHDSServiceRequest.occurrence[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.occurrence[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | When service should occur |
| id_xtehr | EHDSServiceRequest.occurrence[x] |
| path_xtehr | EHDSServiceRequest.occurrence[x] |
| short_xtehr | Occurrence |
| type_xtehr | dateTime |

### Comments
Het is vreemd dat de zib Aanvrager geen gegevens heeft m.b.t. het tijdinterval waarin de aangevraagde activiteit moet worden uitgevoerd. Dit gegeven is belangrijk voor het plannen van de aangevraagde activiteit.


## EHDSServiceRequest.patientInstructions

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.patientInstructions |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Patient or consumer-oriented instructions |
| id_xtehr | EHDSServiceRequest.patientInstructions |
| path_xtehr | EHDSServiceRequest.patientInstructions |
| short_xtehr | Patient instructions |
| type_xtehr | string |

### Comments



## EHDSServiceRequest.coverage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSServiceRequest.coverage |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Insurance or medical plan or a payment agreement. |
| id_xtehr | EHDSServiceRequest.coverage |
| path_xtehr | EHDSServiceRequest.coverage |
| short_xtehr | Coverage |
| type_xtehr | EHDSCoverage |

### Comments



## zib: OrderData.Requester::HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.Requester::HealthProfessional |
| alias_zib | NL: Aanvrager::Zorgverlener |
| card._zib | 1 |
| definition_zib | The person who ordered the action (procedure, test, etc.). |
| id_zib | NL-CM:22.2.4 |
| name_zib | Requester::HealthProfessional |
| path_zib | OrderData.Requester::HealthProfessional |
| stereotype_zib | data,reference |

### Comments
"in een deel van de EHDS modellen is de auteur in de header gescheiden van een health professional met een specifieke rol: zo heeft Condition de auteur in de header, maar ook daarnaast expliciet de 'asserter' (diagnosesteller).
Het lijkt niet wenselijk om een gegeven in de header een dubbelrol te geven, waarbij het twee betekenissen moet representeren. Het is wenselijk om naast het element in de header voor de administratieve verantwoordelijkheid als auteur (die voor elk model geldt) een apart element te hebben voor de zorgverlener die verantwoordelijk is voor een interpretatie, een besluit of het uitvoeren van een activiteit."


## zib: OrderData.OrderDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.OrderDateTime |
| alias_zib | NL: AanvraagDatumTijd |
| card._zib | 1 |
| definition_zib | Date and if relevant time when the order is made. |
| id_zib | NL-CM:22.2.2 |
| name_zib | OrderDateTime |
| path_zib | OrderData.OrderDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments
AanvraagDatumTijd heeft niet zonder meer dezelfde betekenis als authorship.dateTime, want het moment van indienen hoeft niet per se gelijk te zijn aan het moment waarop de aanvraag wordt aangemaakt. Het lijkt wenselijk om in EHDSServiceRequest een expliciet element voor het moment van indienen van de aanvraag naast de registratiedatum/tijd van de aanvraag (authorship.dateTime).


## zib: OrderData.OrderId

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.OrderId |
| alias_zib | NL: Aanvraagnummer |
| card._zib | 1 |
| definition_zib | Order identification number. |
| id_zib | NL-CM:22.2.3 |
| name_zib | OrderId |
| path_zib | OrderData.OrderId |
| stereotype_zib | data |
| type_zib | II |

### Comments



## zib: OrderData.Status

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | OrderData.Status |
| alias_zib | NL: Status |
| card._zib | 1 |
| definition_zib | Status of the order in the ordering process, such as e.g. 'requested', 'planned', 'completed' |
| id_zib | NL-CM:22.2.7 |
| name_zib | Status |
| path_zib | OrderData.Status |
| stereotype_zib | data |
| type_zib | CD |

### Comments
"Het is vreemd dat het model EHDSServiceRequest geen element heeft voor de status van de voortgang van de aanvraag. In de header zit een veld 'status', maar dat veld komt in elk Xt-EHR logical model voor.
Er zijn modellen, zoals EHDSCondition waar naast header.status ook een apart element is voor de conceptspecifieke status, zoals het element diagnosisAssertionStatus.
Het is belangrijk dat EHDS in haar logical models de administratieve status in de headersectie apart modelleert van een conceptspecifieke status die vaak ook een specifieke waardenlijst heeft.
In FHIR is de voortgangsstatus niet gemodelleerd bij ServiceRequest, maar bij Procedure. Het element status heeft als valueset EventStatus. Dit element vind ik niet in EHDSServiceRequest en ook niet in EHDSProcedure."
