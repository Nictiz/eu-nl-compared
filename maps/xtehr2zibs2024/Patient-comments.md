# Patient as of 29-05-2025

### Overall conclusion
The EHDSPatient Logical Model and the Patient zib represent the same entity: an individual receiving healthcare. Despite structural or terminological differences, they refer to the same underlying subject. Below is an overview of the differences.

What is missing in the ZIB that is **mandatory/required** in the Xt-EHR?
It is expected that the zib provides sufficient coverage for the mandatory elements of the EHDSPatient model.

What is missing in the Xt-EHR that is **mandatory/required** in the ZIB?
- Patient.DeathIndicator
- Patient.MultipleBirthIndicator

What is mandatory/required in ZIB that is optional in Xt-EHR?
- Patient.Gender
- Patient.DateOfBirth
- Patient.NameInformation

What is mandatory/required in Xt-EHR that is optional in ZIB?
- EHDSPatient.personalIdentifier

What is missing in the ZIB that is **optional** in the Xt-EHR?
- EHDSPatient.citizenship (comparable to zib Nationality)
- EHDSPatient.communicationLanguage (comparable to zib LanguageProficiency)
- EHDSPatient.maritalStatus (comparable to zib MartitalStatus)
- EHDSPatient.telecom (comparable to partial information model ContactInformation)

What is missing in the Xt-EHR that is **optional** in the ZIB?
- Patient.ContactInformation (comparable to EHDSPatient.telecom)
- Patient.DateOfDeath
- Patient.GenderIdentity



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
Semantics: The EHDSPatient Logical Model and the Patient zib represent the same entity: an individual receiving healthcare. Despite potential structural or terminological differences, they refer to the same underlying subject.  
Datatype: N/A  
Cardinalities: N/A


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
Semantics: ✅  
Datatype: N/A  
Cardinalities:✅  
Note: EHDSAddress should be compared to partial information model AddressInformation https://zibs.nl/wiki/AddressInformation-v1.2(2024EN)


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
Semantics: Both the zib and EHDS models appear to conflate gender and sex, reflecting a common misconception that the two are equivalent, despite their distinct meanings. The term "Physiological gender" would be more accurately described as "biological sex," which is the standard term used to refer to physical and physiological characteristics such as chromosomes, hormones, and reproductive anatomy. Gender however refers to the characteristics of women, men, girls and boys that are socially constructed (https://www.who.int/health-topics/gender. The lack of a clear definition for "gender" in both the EHDS and zib models results in ambiguity regarding its intended meaning and use.  
Datatype: CodableConcept vs Coded descriptor (CD)
    - Terminology: Zib - https://terminologie.nictiz.nl/art-decor/loinc?conceptId=46098-0; 
    - valuesets: EHDSPatient.administrativeGender: Preferred {male, female, other, unknown} https://build.fhir.org/valueset-administrative-gender.html; Zib Patient.Gender: Required {male, female, undifferentiated, unknown}  
Cardinalities:Element is required in zib, but optional in EHDSPatient.



## EHDSPatient.citizenship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.citizenship |
| zib | NationalityRC/Nationality |
| binding_xtehr | {'strength': 'preferred', 'description': 'ISO 3166-1-2'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Citizenship/nationality of the patient. |
| definition_zib | Root concept of the Nationality information model. This concept contains all data elements of the Nationality information model. /Indicates the country of citizenship. GBA Tabel 32 (Nationaliteitentabel) |
| definitioncode_zib | 66476-3 Country of citizenship |
| id_xtehr | EHDSPatient.citizenship |
| id_zib | NL-CM:7.6.1 / NL-CM:7.6.3 |
| name_zib | NationalityRC/Nationality |
| path_xtehr | EHDSPatient.citizenship |
| path_zib | NationalityRC/NationalityRC.Nationality |
| short_xtehr | C.1.8 - Citizenship (nationality) |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
EHDSExclusive
Nationality is not part of the Patient zib, but there is a separate zib called "Nationality" that requires further analysis: https://zibs.nl/wiki/Nationality-v3.0(2024EN)
Difference in valueset used:  
The zib uses the GBA Tabel 32 (Nationaliteitentabel)'; Binding: Extensible  
EHDSPatient.citizenship uses ISO 3166-1-2; Binding: Preferred


## EHDSPatient.communicationLanguage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSPatient.communicationLanguage |
| zib | LanguageProficiency(.CommunicationLanguage) |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The language which can be used to communicate with the patient about his or her health. |
| definition_zib | Linguistic proficiency is the ability to express oneself in a certain language and understand statements made in that language. This includes both oral and written communication.( / CommunicationLanguage: The language of communication. ) |
| definitioncode_zib | 284530008 / 161139007 |
| id_xtehr | EHDSPatient.communicationLanguage |
| id_zib | NL-CM:7.12.1 |
| name_zib | LanguageProficiency(.CommunicationLanguage) |
| path_xtehr | EHDSPatient.communicationLanguage |
| path_zib | LanguageProficiency(.CommunicationLanguage) |
| short_xtehr | C.1.9 - Communcation language |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
EHDSExclusive
CommunicationLanguage is not part of the Patient zib, but there is a separate zib called "LanguageProficiency" that requires further analysis: https://zibs.nl/wiki/LanguageProficiency-v4.0(2024EN)
LanguageProficiency.CommunicationLanguage is a required element of the zib LanguageProficiency with cardinality 1..1.
Zib has CommunicationLanguageCodelist which consists of all values of ISO-639-2 alpha codevalues with binding: required.
Xt-EHR model uses 'BCP 47' to describe CommunicationLanguage binding: preferred.



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
Semantics: Xtehr requires a complete date of birth YYYY-MM-DDThh:mm:ss+zz:zz; in the zib a vague date (such as only the year) is permitted.  
Datatype: ✅  
Cardinalities:Element is required in zib, but optional in EHDSPatient.  
Note: Which format is used in zib Patient?  


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
EHDSExclusive
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
Semantics: ?  
Datatype: ?  
Cardinalities: Name information is optional in xtehr, but required in zib and further specified in the partial information model NameInformation.  
Note: Further analysis required of EHDSHumanName and https://zibs.nl/wiki/NameInformation-v1.2(2024EN)


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
Semantics: ✅  
Datatype: ✅  
Cardinalities: In extehr at least one type of identifier is required; in zib it's optional.


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
The zib refers to the partial information model ContactInformation which consists of Telecommunication contact information, should be further analyzed.


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
The zib refers to the partial information model ContactInformation which consists of Telecommunication contact information, should be further analyzed.


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
ZibExclusive


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
ZibExclusive


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
ZibExclusive


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
ZibExclusive


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
ZibExclusive
