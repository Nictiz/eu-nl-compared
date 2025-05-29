# Patient as of 29-05-2025

| zib                                 | xtehr                             | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:------------------------------------|:----------------------------------|:-----------|:----------------|:------------|:--------------|
| Patient                             | EHDSPatient                       |            |                 |             | 0..*          |
| Patient.AddressInformation          | EHDSPatient.address               |            | EHDSAddress     | 0..*        | 0..*          |
| Patient.Gender                      | EHDSPatient.administrativeGender  | CD         | CodeableConcept | 1           | 0..1          |
|                                     | EHDSPatient.citizenship           |            | CodeableConcept |             | 0..*          |
|                                     | EHDSPatient.communicationLanguage |            | CodeableConcept |             | 0..*          |
| Patient.DateOfBirth                 | EHDSPatient.dateOfBirth           | TS         | dateTime        | 1           | 0..1          |
|                                     | EHDSPatient.maritalStatus         |            | CodeableConcept |             | 0..1          |
| Patient.NameInformation             | EHDSPatient.name                  |            | EHDSHumanName   | 1           | 0..*          |
| Patient.PatientIdentificationNumber | EHDSPatient.personalIdentifier    | II         | Identifier      | 0..*        | 1..*          |
|                                     | EHDSPatient.telecom               |            | EHDSTelecom     |             | 0..*          |
| Patient.ContactInformation          |                                   |            |                 | 0..1        |               |
| Patient.DateOfDeath                 |                                   | TS         |                 | 0..1        |               |
| Patient.DeathIndicator              |                                   | BL         |                 | 1           |               |
| Patient.GenderIdentity              |                                   | CD         |                 | 0..1        |               |
| Patient.MultipleBirthIndicator      |                                   | BL         |                 | 1           |               |
| Patient.MultipleBirthSequence       |                                   | INT        |                 | 0..1        |               |



## EHDSPatient

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient |
| zib | Patient |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.1 - EHDS refined base model for Patient/subject information |
| definition_zib | Root concept of the Patient information model. This root concept contains all data elements of the Patient information model. |
| definitioncode_zib | 116154003 Patient |
| id_xtehr | EHDSPatient |
| id_zib | NL-CM:0.1.1 |
| name_zib | Patient |
| path_xtehr | EHDSPatient |
| path_zib | Patient |
| short_xtehr | Patient model |
| type_xtehr |  |
| type_zib |  |

### Comments
The EHDSPatient Logical Model and the Patient zib represent the same entity: an individual receiving healthcare. Despite potential structural or terminological differences, they refer to the same underlying subject.


## EHDSPatient.address

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.address |
| zib | Patient.AddressInformation |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Mailing and home or office addresses. The addresses are always sequences of address parts (e.g. street address line, country, ZIP code, city) even if postal address formats may vary depending on the country. An address may or may not include a specific use code; if this attribute is not present it is assumed to be the default address useful for any purpose. |
| definition_zib | Patient's address information. |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.address |
| id_zib | NL-CM:0.1.4 |
| name_zib | AddressInformation |
| path_xtehr | EHDSPatient.address |
| path_zib | Patient.AddressInformation |
| short_xtehr | C.1.5 - Address |
| type_xtehr | EHDSAddress |
| type_zib |  |

### Comments
Scope match ✅


## EHDSPatient.administrativeGender

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.administrativeGender |
| zib | Patient.Gender |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 Administrative Gender'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | This field must contain a recognized valid value for "administrative gender". If different, "physiological gender" should be communicated elsewhere.  |
| definition_zib | Patient’s administrative gender. |
| definitioncode_zib | 46098-0 Sex |
| id_xtehr | EHDSPatient.administrativeGender |
| id_zib | NL-CM:0.1.9 |
| name_zib | Gender |
| path_xtehr | EHDSPatient.administrativeGender |
| path_zib | Patient.Gender |
| short_xtehr | C.1.4 - Administrative gender |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Element is required in zib, but optional in EHDSPatient.
Valueset EHDSPatient.administrativeGender: Preferred {male, female, other, unknown} https://build.fhir.org/valueset-administrative-gender.html
Valueset zib Patient.Gender: Required {male, female, undifferentiated, unknown}
Notably, both the zib and EHDS models appear to conflate gender and sex, reflecting a common misconception that the two are equivalent, despite their distinct meanings. The term "Physiological gender" would be more accurately described as "biological sex," which is the standard term used to refer to physical and physiological characteristics such as chromosomes, hormones, and reproductive anatomy. Gender however refers to the characteristics of women, men, girls and boys that are socially constructed (https://www.who.int/health-topics/gender. The lack of a clear definition for "gender" in both the EHDS and zib models results in ambiguity regarding its intended meaning and use.


## EHDSPatient.citizenship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.citizenship |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'ISO 3166-1-2'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Citizenship/nationality of the patient. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.citizenship |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSPatient.citizenship |
| path_zib |  |
| short_xtehr | C.1.8 - Citizenship (nationality) |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
Nationality is not part of the Patient zib, but there is a separate zib called "Nationality" that requires further analysis: https://zibs.nl/wiki/Nationality-v3.0(2024EN)


## EHDSPatient.communicationLanguage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.communicationLanguage |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The language which can be used to communicate with the patient about his or her health. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.communicationLanguage |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSPatient.communicationLanguage |
| path_zib |  |
| short_xtehr | C.1.9 - Communcation language |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
CommunicationLanguage is not part of the Patient zib, but there is a separate zib called "LanguageProficiency" that requires further analysis: https://zibs.nl/wiki/LanguageProficiency-v4.0(2024EN)


## EHDSPatient.dateOfBirth

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.dateOfBirth |
| zib | Patient.DateOfBirth |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | The date of birth of the patient [ISO TS 22220]. As age of the patient might be important for correct interpretation of the test result values, complete date of birth should be provided. |
| definition_zib | Patient’s date of birth. The date of birth is mandatory for a patient. A vague date (such as only the year) is permitted. |
| definitioncode_zib | 21112-8 Birth date |
| id_xtehr | EHDSPatient.dateOfBirth |
| id_zib | NL-CM:0.1.10 |
| name_zib | DateOfBirth |
| path_xtehr | EHDSPatient.dateOfBirth |
| path_zib | Patient.DateOfBirth |
| short_xtehr | C.1.3 - Date of birth |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
Element is required in zib, but optional in EHDSPatient.


## EHDSPatient.maritalStatus

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.maritalStatus |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 marital-status'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Marital (civil) status of a patient |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.maritalStatus |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSPatient.maritalStatus |
| path_zib |  |
| short_xtehr | C.1.7 - Marital status |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
MaritalStatus is not part of the Patient zib, but there is a separate zib called "MaritalStatus" that requires further analysis: https://zibs.nl/wiki/MaritalStatus-v3.2(2024EN)


## EHDSPatient.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.name |
| zib | Patient.NameInformation |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | Name associated with the patient/subject. Name might consist of name parts, e.g. Given name or names, family name/surname, name prefix etc. |
| definition_zib | Patient's full name. |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.name |
| id_zib | NL-CM:0.1.6 |
| name_zib | NameInformation |
| path_xtehr | EHDSPatient.name |
| path_zib | Patient.NameInformation |
| short_xtehr | C.1.2 - Name |
| type_xtehr | EHDSHumanName |
| type_zib |  |

### Comments



## EHDSPatient.personalIdentifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.personalIdentifier |
| zib | Patient.PatientIdentificationNumber |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib | 0..* |
| definition_xtehr | An identifier of the patient that is unique within a defined scope. Example: National ID (birth number) or National patient identifier for the Czech patient. Multiple identifiers could be provided.  |
| definition_zib | The patient’s identification number. In transfer situations, use of the social security number (BSN) must comply with the Use of Social Security Numbers in Healthcare Act (Wbsn-z). In other situations, other number systems can be used, such as internal hospital patient numbers for example. |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.personalIdentifier |
| id_zib | NL-CM:0.1.7 |
| name_zib | PatientIdentificationNumber |
| path_xtehr | EHDSPatient.personalIdentifier |
| path_zib | Patient.PatientIdentificationNumber |
| short_xtehr | C.1.1 - Personal identifier |
| type_xtehr | Identifier |
| type_zib | II |

### Comments



## EHDSPatient.telecom

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.telecom |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Telecommunication contact information (addresses) associated to a person. Multiple telecommunication addresses might be provided. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSPatient.telecom |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSPatient.telecom |
| path_zib |  |
| short_xtehr | C.1.6 - Telecom |
| type_xtehr | EHDSTelecom |
| type_zib |  |

### Comments



## zib: Patient.ContactInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Patient.ContactInformation |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Patient’s telephone number(s) or e-mail address(es). |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:0.1.5 |
| name_zib | ContactInformation |
| path_xtehr |  |
| path_zib | Patient.ContactInformation |
| short_xtehr |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: Patient.DateOfDeath

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Patient.DateOfDeath |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The date on which the patient died. A ‘vague’ date, such as only the year, is permitted. |
| definitioncode_zib | 81954-0 Date of death [Date] |
| id_xtehr |  |
| id_zib | NL-CM:0.1.33 |
| name_zib | DateOfDeath |
| path_xtehr |  |
| path_zib | Patient.DateOfDeath |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | TS |

### Comments



## zib: Patient.DeathIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Patient.DeathIndicator |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | An indication stating whether the patient has died. |
| definitioncode_zib | 419099009 Dead |
| id_xtehr |  |
| id_zib | NL-CM:0.1.32 |
| name_zib | DeathIndicator |
| path_xtehr |  |
| path_zib | Patient.DeathIndicator |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | BL |

### Comments



## zib: Patient.GenderIdentity

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Patient.GenderIdentity |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The gender with which the person identifies. |
| definitioncode_zib | 33821000087103 Gender identity |
| id_xtehr |  |
| id_zib | NL-CM:0.1.34 |
| name_zib | GenderIdentity |
| path_xtehr |  |
| path_zib | Patient.GenderIdentity |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: Patient.MultipleBirthIndicator

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Patient.MultipleBirthIndicator |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | An indication stating whether the patient is of a multiple birth. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:0.1.31 |
| name_zib | MultipleBirthIndicator |
| path_xtehr |  |
| path_zib | Patient.MultipleBirthIndicator |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | BL |

### Comments



## zib: Patient.MultipleBirthSequence

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Patient.MultipleBirthSequence |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The birth number in the sequence of a multiple birth. The first birth is given value 1. The middle birth in a triplet birth would be given value 2 and the third birth would have value 3. If multiple birth order is filled then the value of the MultipleIndicator must be "True". |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:0.1.35 |
| name_zib | MultipleBirthSequence |
| path_xtehr |  |
| path_zib | Patient.MultipleBirthSequence |
| short_xtehr |  |
| type_xtehr |  |
| type_zib | INT |

### Comments

