# Specimen as of 3-9-2025

## Version history

v1: 03-09-2025, initial version

## Actions

## Compared
### Scope
EHDS describes both data on the collection of the sample as the sample itself, where there is a seperate zib CollectionData for describing the collection of a sample. 
A Laboratory Result can only be based on a single monster in a single container(type) within the zib. The EHDS lab results can be based on multiple specimens that are contained in multiple containers.
The zib does not explicitly describe any other subject than the patient for specimen collection (and is not intended for this purpose), where as EHDS can describe different subjects like patient animal, Location, Substance or Device (These also have there own models in EHDS). However it is not completely clear what exactly is the difference with sourceDevice. 

### Other
Specimen is also used in imaging and servicerequest. The zib can currently only be used in context of a LaboratoryTestResult. 

## Discussions (4-9-2025:) Specimen
# Notulen  
**Aantekeningen Duiding verschillen Lab - XtEHR consultatie**

---

## Specimen

- In **EHDS Lab result** kan een specimen meerdere specimens en containers bevatten.  
  In **ZIB** is dit één-op-één.  
  **Actie:** Lab checkt hoe dit in Nederland werkt en komt hierop terug.
  

- In de **Zib** moet specimen los zijn van *LaboratoryTestResult*.  
  **Actie:** ZIB issue maken Wouter.  

- **EHDS BodyStructure Laterality** en **BodyStucture Qualified** lijken dubbel.  
  **Actie:** Wouter bespreekt dit met Astrid. (Gedaan). Consultatie inbrengen om FHIR Bodystructure/openEHR ananatomical locations/relative anatomical locations te volgen, omdat complexe bodystructures niet kunnen worden beschreven. 
  **Actie** aangeven in de valueset dat Lateraliteit niet zou moeten voorkomen in qualifier (want dubbel)
  **Actie** een binding naar twee takken in SNOMED voor Qualifier zou beter zijn (Navragen welke takken bij Astrid)


- **CollectionProcedure**  
  **Actie:** ZIB issue maken Wouter let op dit geeft twee mogelijk modelleringen via een reference naar procedure en via Proceduremethod om een procedure te beschrijven is er verschil?.  

- **CollectionProcedureMethod** lijkt dubbel met *CollectionProcedure*.  
  Voor nu zo laten.  

- **EHDS Specimen.container**  
  **Actie:** Michal zoekt uit hoe in FHIR wordt omgegaan met specimen conatainer multiplicity. 
  in **nl core** LaboratoryTestResult.Specimen, container staat op 0...*, dus er zal geen problemen zijn met multiplicty (ten minste in FHIR)
  **Actie**: Zib issue om te kijken of dit ook in NL zou moeten.

  **EHDS Specimen.container.device**   
  Verschil tussen EHDS (`706041008 | Device for body fluid and tissue collection/transfer/processing |`)  
  en ZIB (`<260787004|Fysiek voorwerp|`).  
  **Actie:** Terminologie geeft in de consultatie aan dat ehDS binding verkeerd is.  

- **EHDS Specimen.container.specimenQuantity**  
  **Acties:**  
  - Consultatie: Wouter vraagt verduidelijking bij EHDS.  
  - Zib issue: Wouter onderzoekt hoe hiermee om te gaan in de ZIB.  

- **EHDS SpecimenIdentifier**  
  In ZIB: één ID.  
  In EHDS: meerdere ID’s, en verplicht.  
  **Acties:**  
  -Consultatie: Lab vraagt aan EHDS: Hoe kan een specimen meerdere ID’s hebben?  
  - Consultatie: Lab vraagt aan EHDS: Waarom is het ID verplicht?  
  - Lab zoekt een voorbeeld waar een specimen geen ID heeft.  

- **EHDS SpecimenMaterial**  
  **Actie:** Wouter bespreekt dit met Terminologie. Besproken substance gaat over 5 jaar ook uit de zib weg issue maken (EHDS implementatie meenemen).

- **EHDS SpecimenSourceDevice**  
  **Actie:** Consultatie: In overleg met terminologie kijken of hier geen waardelijst of expressie voorgesteld kan worden.  Overlegd geen verdere actie nodig. Snomed CT (is voldoende) en EMDN (niet ideaal maar toestaan). ZIB issue om te kijken of EMDN wel of niet toegevoegd moet worden?

- **EHDS Subject** zijn te gedetailleerd in de context van LAB.  
  **Acties:**  
  - Wouter bespreekt dit met Terminologie. Dit is eigenlijk wel wenselijk. 

- **EHDS SpecimenNumberExtension**  
  Hier hoeven wij niets mee.  
  **Actie:** Lab geeft gap met Nederland aan in gerichte consultatie.  

- **EHDS MicroOrganism**  
  **Acties:**  
  - Consultatie issue: Lab brengt dit in bij EHDS (Terminologie reviewt).  
  - ZIB issue: Terminologie check nodig of dit onder *TypeOfSpecies* valt.  Nee maar wel wenselijk om op te nemen in ZIB als we niet menselijke onderzoeken toestaan (subject).

- **EHDS Morphology** is te mappen.  
  **Actie:** ZIB issue: overweeg of dit binnen *AnatomicalLocation* moet komen. Scope niet pathology???

- **EHDS Comment**  
  **Actie:** Lab onderzoekt of een comment in specimen nodig is.  


## Actiepuntenlijst

  



| zib                                                   | xtehr                                   | type_zib   | type_xtehr        | card._zib   | card._xtehr   |
|:------------------------------------------------------|:----------------------------------------|:-----------|:------------------|:------------|:--------------|
| LaboratoryTestResult.Specimen                         | EHDSSpecimen                            |            |                   | 0..1        | 0..*          |
| LaboratoryTestResult.Specimen.AnatomicalLocation      | EHDSSpecimen.bodySite                   |            | EHDSBodyStructure | 0..1        | 0..1          |
|                                                       | EHDSSpecimen.collectionPeriod           |            | Period            |             | 0..1          |
|                                                       | EHDSSpecimen.collectionProcedure        |            | EHDSProcedure     |             | 0..1          |
|                                                       | EHDSSpecimen.collectionProcedureMethod  |            | CodeableConcept   |             | 0..1          |
|                                                       | EHDSSpecimen.container                  |            | Base              |             | 0..*          |
| LaboratoryTestResult.Specimen.ContainerType           | EHDSSpecimen.container.containerDevice  | CD         | EHDSDevice        | 0..1        | 1..1          |
|                                                       | EHDSSpecimen.container.specimenQuantity |            | Quantity          |             | 0..1          |
| LaboratoryTestResult.Specimen.SpecimenId              | EHDSSpecimen.identifier                 | II         | Identifier        | 0..1        | 1..*          |
| LaboratoryTestResult.Specimen.SpecimenMaterial        | EHDSSpecimen.material                   | CD         | CodeableConcept   | 0..1        | 0..1          |
|                                                       | EHDSSpecimen.receivedDate               |            | dateTime          |             | 0..1          |
| LaboratoryTestResult.Specimen.SpecimenSource          | EHDSSpecimen.sourceDevice               | CD         | CodeableConcept   | 0..1        | 0..1          |
|                                                       | EHDSSpecimen.subject[x]                 |            | EHDSPatient       |             | 0..1          |
|                                                       | EHDSSpecimen.typeOfSpecies              |            | CodeableConcept   |             | 0..1          |
| LaboratoryTestResult.Specimen.SpecimenNumberExtension |                                         | INT        |                   | 0..1        |               |
| LaboratoryTestResult.Specimen.Microorganism           |                                         | CD         |                   | 0..1        |               |
| LaboratoryTestResult.Specimen.Morphology              |                                         | CD         |                   | 0..1        |               |
| LaboratoryTestResult.Specimen.Comment                 |                                         | ST         |                   | 0..1        |               |



## EHDSSpecimen

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen |
| zib | LaboratoryTestResult.Specimen |
| alias_zib | NL: Monster |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | EHDS refined base model for A sample to be used for Analysis |
| definition_zib | Container of the concept Specimen. This container contains all data elements of the concept Specimen. A completed container is related to a sample from the Snomed Hierarchy. <br> <br>If the TestCode implicitly also describes a specimen (often the case if coded in LOINC), elements within the concept specimen may not conflict with it. However, if desired, these data can provide a more detailed description.This is in line with the agreements made in the IHE/Nictiz e-Lab programme. |
| definitioncode_zib | SNOMED CT: 123038009 Specimen |
| id_xtehr | EHDSSpecimen |
| id_zib | NL-CM:13.1.2 |
| name_zib | Specimen |
| path_xtehr | EHDSSpecimen |
| path_zib | LaboratoryTestResult.Specimen |
| short_xtehr | Specimen model |
| stereotype_zib | container |

### Comments
Scope matches


## EHDSSpecimen.bodySite

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.bodySite |
| zib | LaboratoryTestResult.Specimen.AnatomicalLocation |
| alias_zib | NL: AnatomischeLocatie |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Anatomic location (body location, laterality) where the material is collected, e.g. Elbow, left |
| definition_zib | Anatomical location where the material is collected, e.g. elbow. |
| definitioncode_zib | SNOMED CT: 405814001 Procedure site - Indirect |
| id_xtehr | EHDSSpecimen.bodySite |
| id_zib | NL-CM:13.1.36 |
| name_zib | AnatomicalLocation |
| path_xtehr | EHDSSpecimen.bodySite |
| path_zib | LaboratoryTestResult.Specimen.AnatomicalLocation |
| short_xtehr | Anatomic location (body location, laterality) where the material is collected, e.g. Elbow, left |
| stereotype_zib | data,reference |
| type_xtehr | EHDSBodyStructure |

### Comments
Scope matches, Cardinality matches


## EHDSSpecimen.collectionPeriod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.collectionPeriod |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The period or date and time of specimen collection. |
| id_xtehr | EHDSSpecimen.collectionPeriod |
| path_xtehr | EHDSSpecimen.collectionPeriod |
| short_xtehr | The period or date and time of specimen collection. |
| type_xtehr | Period |

### Comments
Not in this zib but can be matched to Afnamegegevens.Verzamelperiode.


## EHDSSpecimen.collectionProcedure

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.collectionProcedure |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The procedure that collects the specimen. |
| id_xtehr | EHDSSpecimen.collectionProcedure |
| path_xtehr | EHDSSpecimen.collectionProcedure |
| short_xtehr | The procedure that collects the specimen. |
| type_xtehr | EHDSProcedure |

### Comments
Reference to procedure is not available in the zib LaboratoryTestResult or CollectionData.


## EHDSSpecimen.collectionProcedureMethod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.collectionProcedureMethod |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | If relevant for the results, the method of obtaining the specimen. |
| id_xtehr | EHDSSpecimen.collectionProcedureMethod |
| path_xtehr | EHDSSpecimen.collectionProcedureMethod |
| short_xtehr | Collection procedure method |
| type_xtehr | CodeableConcept |

### Comments
Not in this zib but can be matched to Afnamegegevens.AfnameProcedure.


## EHDSSpecimen.container

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.container |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | The container holding the specimen. |
| id_xtehr | EHDSSpecimen.container |
| path_xtehr | EHDSSpecimen.container |
| short_xtehr | The container holding the specimen. |
| type_xtehr | Base |

### Comments
There is no container in the zib model for the specimen container


## EHDSSpecimen.container.containerDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.container.containerDevice |
| zib | LaboratoryTestResult.Specimen.ContainerType |
| alias_zib | NL: Containertype |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | The device resource for the the container holding the specimen. |
| definition_zib | Container type describes the envelope in which the material is collected or sent. Examples include blood tubes, transport container, possibly including culture medium. |
| definitioncode_zib | SNOMED CT: 706046003 Specimen receptacle |
| id_xtehr | EHDSSpecimen.container.containerDevice |
| id_zib | NL-CM:13.1.21 |
| name_zib | ContainerType |
| path_xtehr | EHDSSpecimen.container.containerDevice |
| path_zib | LaboratoryTestResult.Specimen.ContainerType |
| short_xtehr | Container device |
| stereotype_zib | data |
| type_xtehr | EHDSDevice |
| type_zib | CD |

### Comments
Scope match, cardinality does not match, because the cardinality of xtEHR is within a FHIR container. the cardinilaty of the container is important here. Container has a 0..* cardinality vs the zib 0..1. 

Different terminology binding in EHDS decendents of:
706041008 | Device for body fluid and tissue 
collection/transfer/processing |  
Zib: <260787004|Fysiek voorwerp|
  


## EHDSSpecimen.container.specimenQuantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.container.specimenQuantity |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Quantity of specimen within container. |
| id_xtehr | EHDSSpecimen.container.specimenQuantity |
| path_xtehr | EHDSSpecimen.container.specimenQuantity |
| short_xtehr | Specimen quantity |
| type_xtehr | Quantity |

### Comments
The quantity per container is not available in the zib. The cardinality of the relationship between CollectionData and Specimen is not defined in the zib and therefor the cardinality is not known. Perhaps this could be mapped to CollectionData.CollectedVolume if collectionData only refers to one specimen (one container), but it is also unclear if quantity can refer to a volume only.


## EHDSSpecimen.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.identifier |
| zib | LaboratoryTestResult.Specimen.SpecimenId |
| alias_zib | NL: Monsternummer |
| card._xtehr | 1..* |
| card._zib | 0..1 |
| definition_xtehr | An identifier of the specimen which is unique within in a defined scope. Example: identifier assigned by ordering system, identifier assigned by laboratory etc. Multiple identifiers can be used. |
| definition_zib | Identification number of the material obtained, as a reference for inquiries to the source organization. In a transmural setting, this number will consist of a specimen number including the identification of the issuing organization, to be unique outside of the borders of an organization. |
| id_xtehr | EHDSSpecimen.identifier |
| id_zib | NL-CM:13.1.15 |
| name_zib | SpecimenId |
| path_xtehr | EHDSSpecimen.identifier |
| path_zib | LaboratoryTestResult.Specimen.SpecimenId |
| short_xtehr | An identifier of the specimen which is unique within in a defined scope. |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | II |

### Comments
SCope match, cardinality mismatch (multiplicity). 


## EHDSSpecimen.material

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.material |
| zib | LaboratoryTestResult.Specimen.SpecimenMaterial |
| alias_zib | NL: Monstermateriaal |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Material that forms the specimen. |
| definition_zib | Specimen material describes the base material or specimen type taken. For example: Urine, blood, Saliva etc or aspirate from jejunum, biopsy of cartilage etc.. This element refers to the Substance or Specimen hierarchy in Snomed. If the Specimen branch is used for this data element, it must not contradict other elements in this zib. |
| definitioncode_zib | SNOMED CT: 370133003 Specimen substance |
| id_xtehr | EHDSSpecimen.material |
| id_zib | NL-CM:13.1.16 |
| name_zib | SpecimenMaterial |
| path_xtehr | EHDSSpecimen.material |
| path_zib | LaboratoryTestResult.Specimen.SpecimenMaterial |
| short_xtehr | Material that forms the specimen. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Scope seems to match although the definition is not really clear. Specimen material binding to SNOMED is not defined in EHDS document or perhaps it is referred to as specimen type <123038009 | Specimen (which is confusing). In the latter case the zib also includes the <105590001|Substantie| besides <123038009 | Specimen.
Substance is part of the Subject field in the EHDS model and has a broader model for describing a substance. 


## EHDSSpecimen.receivedDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.receivedDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Date and time that the material is handed over at the laboratory or specimen collection centre. |
| id_xtehr | EHDSSpecimen.receivedDate |
| path_xtehr | EHDSSpecimen.receivedDate |
| short_xtehr | Date and time that the material is handed over at the laboratory or specimen collection centre. |
| type_xtehr | dateTime |

### Comments
Matches CollectionData.ReceivedDateTime fully.


## EHDSSpecimen.sourceDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.sourceDevice |
| zib | LaboratoryTestResult.Specimen.SpecimenSource |
| alias_zib | NL: BronMonster |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, EMDN'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Source device in case the material is not collected directly from the patient but comes from a patient-related object, e.g. a catheter |
| definition_zib | If the material is not collected directly from the patient but comes from a patient-related object, e.g. a cathetertip, this source of material can be recorded here. |
| definitioncode_zib | SNOMED CT: 898201001 Specimen from device |
| id_xtehr | EHDSSpecimen.sourceDevice |
| id_zib | NL-CM:13.1.29 |
| name_zib | SpecimenSource |
| path_xtehr | EHDSSpecimen.sourceDevice |
| path_zib | LaboratoryTestResult.Specimen.SpecimenSource |
| short_xtehr | Source device in case the material is not collected directly from the patient but comes from a patient-related object, e.g. a catheter |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Matches fully, however terminology binding is not defined in the EHDS model.


## EHDSSpecimen.subject[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.subject[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Where the specimen came from. This may be from patient(s), from a location (e.g., the source of an environmental sample), or a sampling of a substance, a biologically-derived product, or a device. |
| id_xtehr | EHDSSpecimen.subject[x] |
| path_xtehr | EHDSSpecimen.subject[x] |
| short_xtehr | Subject |
| type_xtehr | EHDSPatient |

### Comments
No zib equivelant. Subject types have there own model which can't be mapped except for patient.


## EHDSSpecimen.typeOfSpecies

### Table

| attribute | value |
|---|---|
| xtehr | EHDSSpecimen.typeOfSpecies |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| definition_xtehr | Biologic type of species for laboratory result reports bound to non-human subjects. |
| id_xtehr | EHDSSpecimen.typeOfSpecies |
| path_xtehr | EHDSSpecimen.typeOfSpecies |
| short_xtehr | Biologic type of species for laboratory result reports bound to non-human subjects. |
| type_xtehr | CodeableConcept |

### Comments
Geen equivalent in zib. Geen terminology defined in the 7.1 document valuesets.


## zib: LaboratoryTestResult.Specimen.SpecimenNumberExtension

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.Specimen.SpecimenNumberExtension |
| alias_zib | NL: Monstervolgnummer |
| card._zib | 0..1 |
| definition_zib | The specimen number extension is used when the collected material is distributed from the original tube or container across multiple tubes. In combination with the specimen Id the extension yield a unique identification of the tube or container |
| id_zib | NL-CM:13.1.20 |
| name_zib | SpecimenNumberExtension |
| path_zib | LaboratoryTestResult.Specimen.SpecimenNumberExtension |
| stereotype_zib | data |
| type_zib | INT |

### Comments
Not available in the EHDS model


## zib: LaboratoryTestResult.Specimen.Microorganism

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.Specimen.Microorganism |
| alias_zib | NL: Microorganisme |
| card._zib | 0..1 |
| definition_zib | In particular in microbiological determinations the subject of the test is an isolate of a certain microorganism rather then a material. This concept provides the ability to capture information about this microorganism. |
| id_zib | NL-CM:13.1.22 |
| name_zib | Microorganism |
| path_zib | LaboratoryTestResult.Specimen.Microorganism |
| stereotype_zib | data |
| type_zib | CD |

### Comments
Not avilable in the EHDS model


## zib: LaboratoryTestResult.Specimen.Morphology

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.Specimen.Morphology |
| alias_zib | NL: Morfologie |
| card._zib | 0..1 |
| definition_zib | Morphology describes morphological abnormalities of the anatomical location where the material is taken, for example wound, ulcer. |
| definitioncode_zib | SNOMED CT: 118168003 Specimen source morphology |
| id_zib | NL-CM:13.1.28 |
| name_zib | Morphology |
| path_zib | LaboratoryTestResult.Specimen.Morphology |
| stereotype_zib | data |
| type_zib | CD |

### Comments
Available in the Bodysite EHDS model and could be mapped.


## zib: LaboratoryTestResult.Specimen.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | LaboratoryTestResult.Specimen.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Comments on the specimen , such as drawing material after a (glucose) stimulus or taking medicine. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:13.1.19 |
| name_zib | Comment |
| path_zib | LaboratoryTestResult.Specimen.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments
Not available in the EHDS model.
