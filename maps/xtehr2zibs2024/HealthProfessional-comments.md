# HealthProfessional
## Overall conclusion
The models mostly match up, but there is one fundamental difference: the zib model is tightly coupled to process that it is instantiated for, while the Xt-EHR model is generic description of the health professional and its role in an organization (presumably). This results in:

* A role definition for the zib (like performer, case manager, etc.) which is not present and unwanted in the Xt-EHR model
* A single specialty, which should be interpreted in the context of the healthcare process

Whereas the Xt-EHR model has:

* Multiple specialties, which should be interpreted in the context of the employment at an organization
* A role, which _probably_ should be interpreted in the context of the employment at an organization. Note that this role is ill defined.

This difference means that the models themselves are not readily compatible. However, compatibility in an actual exchange depends on the way the models are mapped. In the current FHIR implementation of zib HealhProfessional, the HealthProfessionalRole concept is broken out of the health professional model and mapped to the resources where it is reference from.

Furthermore:

* there are several cardinality differences (address, telecom)
* the zib specifies the gender of the health professional while the Xt-EHR model does not
* the analyses of Address, Telecom, HumanName and Location/Organization apply


| zib                                                       | xtehr                               | type_zib   | type_xtehr       | card._zib   | card._xtehr   |
|:----------------------------------------------------------|:------------------------------------|:-----------|:-----------------|:------------|:--------------|
| HealthProfessional                                        | EHDSHealthProfessional              |            |                  |             | 0..*          |
| HealthProfessional.AddressInformation                     | EHDSHealthProfessional.address      |            | EHDSAddress      | 0..*        | 0..1          |
| HealthProfessional.HealthProfessionalIdentificationNumber | EHDSHealthProfessional.identifier   | II         | Identifier       | 0..*        | 0..*          |
| HealthProfessional.NameInformation                        | EHDSHealthProfessional.name         |            | EHDSHumanName    | 0..1        | 0..1          |
| HealthProfessional.HealthcareProvider                     | EHDSHealthProfessional.organization |            | EHDSOrganization | 0..1        | 0..1          |
|                                                           | EHDSHealthProfessional.role         |            | CodeableConcept  |             | 0..*          |
| HealthProfessional.Specialty                              | EHDSHealthProfessional.specialty    | CD         | CodeableConcept  | 0..1        | 0..*          |
| HealthProfessional.ContactInformation                     | EHDSHealthProfessional.telecom      |            | EHDSTelecom      | 0..1        | 0..*          |
| HealthProfessional.Gender                                 |                                     | CD         |                  | 0..1        |               |
| HealthProfessional.HealthProfessionalRole                 |                                     | CD         |                  | 0..1        |               |



## EHDSHealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional |
| zib | HealthProfessional |
| alias_zib | NL: Zorgverlener |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for Health professional (HP) |
| definition_zib | Root concept of the HealthProfessional information model. This root concept contains all data elements of the HealthProfessional information model.
When referring to this information model the role the health professional fulfils in the healthcare process can be addressed additionally. For health professionals, this could be for example main practitioner or referrer. |
| definitioncode_zib | SNOMED CT: 223366009 Healthcare professional |
| id_xtehr | EHDSHealthProfessional |
| id_zib | NL-CM:17.1.1 |
| name_zib | HealthProfessional |
| path_xtehr | EHDSHealthProfessional |
| path_zib | HealthProfessional |
| short_xtehr | Health professional model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSHealthProfessional.address

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.address |
| zib | HealthProfessional.AddressInformation |
| alias_zib | NL: Adresgegevens |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..* |
| definition_xtehr | Mailing and office or home addresses. The addresses are always sequences of address parts (e.g. street address line, country, postcode, city) even if postal address formats may vary depending on the country. An address may or may not include a specific use code; if this attribute is not present it is assumed to be the default address useful for any purpose. |
| definition_zib | Health professional�s address information. |
| definitioncode_zib |  |
| id_xtehr | EHDSHealthProfessional.address |
| id_zib | NL-CM:17.1.7 |
| name_zib | AddressInformation |
| path_xtehr | EHDSHealthProfessional.address |
| path_zib | HealthProfessional.AddressInformation |
| short_xtehr | Mailing and office or home addresses. The addresses are always sequences of address parts (e.g. street address line, country, postcode, city) even if postal address formats may vary depending on the country. An address may or may not include a specific use code; if this attribute is not present it is assumed to be the default address useful for any purpose. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSAddress |
| type_zib |  |

### Comments
See the analysis on Address


## EHDSHealthProfessional.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.identifier |
| zib | HealthProfessional.HealthProfessionalIdentificationNumber |
| alias_zib | NL: ZorgverlenerIdentificatienummer |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | An identifier of the health professional that is unique within a defined scope. Example: National health professional ID. Multiple identifiers could be provided. |
| definition_zib | The health professional identification number is a number that uniquely identifies the health professional.

The following numbers are used in the Netherlands: 
1. UZI Health Professionals. Identification of health professionals (people) in the Dutch healthcare industry. 
2. VEKTIS AGB-Z. Identifies health professionals and healthcare organizations 
3. BIG-ID. The ID of the health professional listed in the BIG-Register. 

This information is not readily available for foreign health professionals. |
| definitioncode_zib |  |
| id_xtehr | EHDSHealthProfessional.identifier |
| id_zib | NL-CM:17.1.2 |
| name_zib | HealthProfessionalIdentificationNumber |
| path_xtehr | EHDSHealthProfessional.identifier |
| path_zib | HealthProfessional.HealthProfessionalIdentificationNumber |
| short_xtehr | An identifier of the health professional that is unique within a defined scope. Example: National health professional ID. Multiple identifiers could be provided. |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | II |

### Comments
The Xt-EHR specifies this as any health professional identifier, which the zib refines to the situation in the Netherlands: UZI, AGB-Z or BIG. The zib doesn't impose any restrictions, so this element is compatible in both ways.


## EHDSHealthProfessional.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.name |
| zib | HealthProfessional.NameInformation |
| alias_zib | NL: Naamgegevens |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Name of the health professional that has been treating or taking responsibility for the patient. |
| definition_zib | Health professional�s full name. If a health professional identification number is entered, it will be the name as listed in UZI, AGB or by the healthcare center. |
| definitioncode_zib |  |
| id_xtehr | EHDSHealthProfessional.name |
| id_zib | NL-CM:17.1.3 |
| name_zib | NameInformation |
| path_xtehr | EHDSHealthProfessional.name |
| path_zib | HealthProfessional.NameInformation |
| short_xtehr | Name of the health professional that has been treating or taking responsibility for the patient. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSHumanName |
| type_zib |  |

### Comments
See the analysis of Name


## EHDSHealthProfessional.organization

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.organization |
| zib | HealthProfessional.HealthcareProvider |
| alias_zib | NL: Zorgaanbieder |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | The organization where this role is available |
| definition_zib | The organization the health professional works for. |
| definitioncode_zib |  |
| id_xtehr | EHDSHealthProfessional.organization |
| id_zib | NL-CM:17.1.6 |
| name_zib | HealthcareProvider |
| path_xtehr | EHDSHealthProfessional.organization |
| path_zib | HealthProfessional.HealthcareProvider |
| short_xtehr | The organization where this role is available |
| stereotype_zib | context,reference |
| type_xtehr | EHDSOrganization |
| type_zib |  |

### Comments
There's is a mismatch in the definition. The zib defines this concept as the organization the health professional _works_ for, whereas the Xt-EHR model defines this as the organization the health professional _fulfills the specified role_ for.

This makes sense if one takes the view that a zib instance is tightly couple to a healthcare process. The instance is then about a specific combination of health professional, organization, specialty and role in the process.


## EHDSHealthProfessional.role

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.role |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'ISCO, SNOMED CT'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Health professional role. Multiple roles could be provided. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSHealthProfessional.role |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSHealthProfessional.role |
| path_zib |  |
| short_xtehr | Health professional role. Multiple roles could be provided. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
Although the zib also defines a "role", it _probably_ has different semantics than the Xt-EHR role. The zib defines the HealthProfessionalRole as the role the health professional plays in the _healthcare process_ (for which the zib is instantiated), like referrer, performer, or case manager. What the Xt-EHR concept is about, is not really clear. However, the terminology binding hints as [ISCO](https://www.who.int/publications/m/item/classifying-health-workers), which is about (broad level) specialty's of health professionals.

This Xt-EHR thus seems to be different than HealthProfessionalRole in the zib, _and_ overlaps with the specialty concept in the Xt-EHR model.

## EHDSHealthProfessional.specialty

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.specialty |
| zib | HealthProfessional.Specialty |
| alias_zib | NL: Specialisme |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | The specialty of a practitioner that describes the functional role they are practicing at a given organization |
| definition_zib | Health professional�s medical specialty. This refers to the recognized medical specialties as stated in the BIG Act. For example general practitioner or cardiologist. |
| definitioncode_zib | SNOMED CT: 394658006 Clinical specialty |
| id_xtehr | EHDSHealthProfessional.specialty |
| id_zib | NL-CM:17.1.4 |
| name_zib | Specialty |
| path_xtehr | EHDSHealthProfessional.specialty |
| path_zib | HealthProfessional.Specialty |
| short_xtehr | The specialty of a practitioner that describes the functional role they are practicing at a given organization |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
There's a slight mismatch in definition and a big one in cardinalities (see also the comment on .organization). The zib defines this concept as the specialty of the health professional, while the Xt-EHR model combines this with the organization. Also, the zib recognizes at most one specialty for a health professional, while the Xt-EHR model recognizes multiple specialties (per organization).

## EHDSHealthProfessional.telecom

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHealthProfessional.telecom |
| zib | HealthProfessional.ContactInformation |
| alias_zib | NL: Contactgegevens |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Telecommunication contact information (addresses) associated with a person, such as phone number, email, or messaging service. Multiple telecommunication addresses might be provided. |
| definition_zib | Health professional�s telephone number(s) or e-mail address(es). |
| definitioncode_zib |  |
| id_xtehr | EHDSHealthProfessional.telecom |
| id_zib | NL-CM:17.1.8 |
| name_zib | ContactInformation |
| path_xtehr | EHDSHealthProfessional.telecom |
| path_zib | HealthProfessional.ContactInformation |
| short_xtehr | Telecommunication contact information (addresses) associated with a person, such as phone number, email, or messaging service. Multiple telecommunication addresses might be provided. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSTelecom |
| type_zib |  |

### Comments
See the analysis of Telecom. There's also a cardinality mismatch, the Xt-EHR model is 0..* whereas the zib restricts this to 0..1


## zib: HealthProfessional.Gender

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HealthProfessional.Gender |
| alias_zib | NL: Geslacht |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Health professional�s administrative gender. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:17.1.9 |
| name_zib | Gender |
| path_xtehr |  |
| path_zib | HealthProfessional.Gender |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments
Not present in the Xt-EHR model


## zib: HealthProfessional.HealthProfessionalRole

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HealthProfessional.HealthProfessionalRole |
| alias_zib | NL: ZorgverlenerRol |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The role the health professional fulfils in the healthcare process. For health professionals, this could be for example attender, referrer or performer. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:17.1.5 |
| name_zib | HealthProfessionalRole |
| path_xtehr |  |
| path_zib | HealthProfessional.HealthProfessionalRole |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments
See the comment on EHDSHealthProfessional.role