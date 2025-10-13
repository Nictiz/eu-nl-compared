# RelatedPerson

| zib                              | xtehr                                | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:---------------------------------|:-------------------------------------|:-----------|:----------------|:------------|:--------------|
| ContactPerson                    | EHDSRelatedPerson                    |            |                 |             | 0..*          |
|                                  | EHDSRelatedPerson.personalIdentifier |            | Identifier      |             | 0..*          |
| ContactPerson.NameInformation    | EHDSRelatedPerson.name               |            | EHDSHumanName   | 0..1        | 0..*          |
|                                  | EHDSRelatedPerson.subject            |            | EHDSPatient     |             | 1..1          |
| ContactPerson.Relationship       | EHDSRelatedPerson.relationship       | CD         | CodeableConcept | 0..*        | 0..1          |
| ContactPerson.AddressInformation | EHDSRelatedPerson.address            |            | EHDSAddress     | 0..*        | 0..*          |
| ContactPerson.ContactInformation | EHDSRelatedPerson.telecom            |            | EHDSTelecom     | 0..1        | 0..*          |
|                                  |                                      |            |                 |             |               |
|                                  |                                      |            |                 |             |               |
|                                  |                                      |            |                 |             |               |
| ContactPerson.Role               |                                      | CD         |                 | 0..*        |               |
|                                  |                                      |            |                 |             |               |
| ContactPerson.Comment            |                                      | ST         |                 | 0..1        |               |



## EHDSRelatedPerson

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson |
| zib | ContactPerson |
| alias_zib | NL: Contactpersoon |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Patient/subject guardian and other related person information |
| definition_zib | Root concept of the ContactPerson information model.This root concept contains all data elements of the ContactPerson information model. |
| definitioncode_zib | SNOMED CT: 70862002 Contact person |
| id_xtehr | EHDSRelatedPerson |
| id_zib | NL-CM:3.1.1 |
| name_zib | ContactPerson |
| path_xtehr | EHDSRelatedPerson |
| path_zib | ContactPerson |
| short_xtehr | Related person model |
| stereotype_zib | rootconcept |

### Comments



## EHDSRelatedPerson.personalIdentifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson.personalIdentifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | An identifier of the related person that is unique within a defined scope. Example: National ID (birth number) for the Czech citizen. Multiple identifiers could be provided.  |
| id_xtehr | EHDSRelatedPerson.personalIdentifier |
| path_xtehr | EHDSRelatedPerson.personalIdentifier |
| short_xtehr | Personal identifier |
| type_xtehr | Identifier |

### Comments



## EHDSRelatedPerson.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson.name |
| zib | ContactPerson.NameInformation |
| alias_zib | NL: Naamgegevens |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Name associated with the person. Name might consists of name parts, e.g. Given name or names, family name/surname, name prefix etc. |
| definition_zib | Full name of the contact. In the case where the composition of the name information is unknown or irrelevant, the partial information model NameInformation cannot be used. |
| id_xtehr | EHDSRelatedPerson.name |
| id_zib | NL-CM:3.1.4 |
| name_zib | NameInformation |
| path_xtehr | EHDSRelatedPerson.name |
| path_zib | ContactPerson.NameInformation |
| short_xtehr | Name |
| stereotype_zib | data,reference |
| type_xtehr | EHDSHumanName |

### Comments
Het is niet duidelijk wat EHDSHumanName.family precies inhoudt: is het de achternaam die de betrokkene van geboorte meekreeg of de achternaam, zoals de persoon die in het dagelijks leven gebruikt? Het laatste is in de context van een RelatedPerson het meest aannemelijk.



## EHDSRelatedPerson.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson.subject |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | The patient in relation to whom the related person is defined. |
| id_xtehr | EHDSRelatedPerson.subject |
| path_xtehr | EHDSRelatedPerson.subject |
| short_xtehr | The patient in relation to whom the related person is defined. |
| type_xtehr | EHDSPatient |

### Comments



## EHDSRelatedPerson.relationship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson.relationship |
| zib | ContactPerson.Relationship |
| alias_zib | NL: Relatie |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 RoleCode'} |
| card._xtehr | 0..1 |
| card._zib | 0..* |
| definition_xtehr | Relationship between a patient and a contact person for that patient. This includes relatives, guardians, caring persons etc. |
| definition_zib | Specifies the relevant family or social relationship to the patient. |
| id_xtehr | EHDSRelatedPerson.relationship |
| id_zib | NL-CM:3.1.3 |
| name_zib | Relationship |
| path_xtehr | EHDSRelatedPerson.relationship |
| path_zib | ContactPerson.Relationship |
| short_xtehr | Relationship |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSRelatedPerson.address

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson.address |
| zib | ContactPerson.AddressInformation |
| alias_zib | NL: Adresgegevens |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Mailing and home or office addresses. The addresses are always sequences of address parts (e.g. street address line, country, ZIP code, city) even if postal address formats may vary depending on the country. An address may or may not include a specific use code; if this attribute is not present it is assumed to be the default address useful for any purpose. |
| definition_zib | Contact’s address information. |
| id_xtehr | EHDSRelatedPerson.address |
| id_zib | NL-CM:3.1.5 |
| name_zib | AddressInformation |
| path_xtehr | EHDSRelatedPerson.address |
| path_zib | ContactPerson.AddressInformation |
| short_xtehr | Address |
| stereotype_zib | data,reference |
| type_xtehr | EHDSAddress |

### Comments



## EHDSRelatedPerson.telecom

### Table

| attribute | value |
|---|---|
| xtehr | EHDSRelatedPerson.telecom |
| zib | ContactPerson.ContactInformation |
| alias_zib | NL: Contactgegevens |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Telecommunication contact information (addresses) associated to a person. Multiple telecommunication addresses might be provided. |
| definition_zib | The contact’s telephone number and/or e-mail address. |
| id_xtehr | EHDSRelatedPerson.telecom |
| id_zib | NL-CM:3.1.6 |
| name_zib | ContactInformation |
| path_xtehr | EHDSRelatedPerson.telecom |
| path_zib | ContactPerson.ContactInformation |
| short_xtehr | Telecom |
| stereotype_zib | data,reference |
| type_xtehr | EHDSTelecom |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |

### Comments



## zib: ContactPerson.Role

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | ContactPerson.Role |
| alias_zib | NL: Rol |
| card._zib | 0..* |
| definition_zib | Specifies the role of the contact in relation to the patient. |
| id_zib | NL-CM:3.1.2 |
| name_zib | Role |
| path_zib | ContactPerson.Role |
| stereotype_zib | data |
| type_zib | CD |

### Comments
Er is geen expliciet veld in EHDSRelatedPerson voor "Role''. Als de valueset voor EHDSRelatedPerson.relationship gebaseerd is op de valueset voor RelatedPerson.relationship in R4 dan omvat die wel een waarde voor 'Emergency Contact'. Dat is dan evt. te mappen op Eerste contactpersoon in de RolCodelijst van de zib.



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |

### Comments



## zib: ContactPerson.Comment

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | ContactPerson.Comment |
| alias_zib | NL: Toelichting |
| card._zib | 0..1 |
| definition_zib | Additional information about the contact. For example, information such as 'the father is also a medical doctor' can be included here. In addition, if the contact works at an organization, the organization can be mentioned here. If the organization is listed as a contact and no actual contact is known, this can also be stated here. In this case, the name information can be left blank. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_zib | NL-CM:3.1.7 |
| name_zib | Comment |
| path_zib | ContactPerson.Comment |
| stereotype_zib | data |
| type_zib | ST |

### Comments

