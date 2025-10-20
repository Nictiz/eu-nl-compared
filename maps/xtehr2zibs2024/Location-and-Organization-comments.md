# Location and Organization as of 2025-06-17
## Comments added by Jacob 20-10
+ EHDSLocation lacks concept to describe specific location within a building
+ EHDSLocation.partOf is reference to EHDSOrganization. Should be EHDSLocation as per definition.

## Overall Discussion
The Location and Organization Xt-EHR models cover the same information as zib HealthcareProvider does, but it is hard to match zib and Xt-EHR. This is largely due to the fact that the zib [suffers from the known issue](https://nictiz.atlassian.net/browse/ZIB-2471) that it is an amalgamation of both a location where care is delivered, and the managing organization of this location. In [ZIB-1539](https://nictiz.atlassian.net/browse/ZIB-1359) it is clarified that the zib in the first place represents a location, but from its use in other zibs and the description of the concepts it becomes clear that this is not the entire picture.

This makes comparison hard, as most zib concepts could potentially be equivalent to the Xt-EHR Location counterpart or to the Xt-EHR Organization counterpart, depending on interpretation and context of use.

For this analysis, the view was taken that the zib primarily represents a location, but the Discussion should be considered very weak.

Apart from this issue with the zib, the Xt-EHR model has a concept of hierarchy (a location is part of an organization, and organizations can be hierarchically organized). The zib lacks this kind of hierarchical relationships.


| zib                                                       | xtehr                             | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:----------------------------------------------------------|:----------------------------------|:-----------|:----------------|:------------|:--------------|
| HealthcareProvider                                        | EHDSLocation                      |            |                 |             | 0..*          |
| HealthcareProvider.AddressInformation                     | EHDSLocation.address              |            | EHDSAddress     | 0..*        | 0..1          |
| HealthcareProvider.OrganizationLocation.LocationName      | EHDSLocation.description          | ST         | string          | 0..1        | 0..1          |
| HealthcareProvider.OrganizationLocation.LocationNumber    | EHDSLocation.description          | INT        | string          | 0..1        | 0..1          |
|                                                           | EHDSLocation.identifier           |            | Identifier      |             | 0..*          |
|                                                           | EHDSLocation.managingOrganization |            | Reference       |             | 0..1          |
|                                                           | EHDSLocation.name                 |            | string          |             | 0..1          |
|                                                           | EHDSLocation.partOf               |            | Reference       |             | 0..1          |
|                                                           | EHDSLocation.position(*)          |            | Base            |             | 0..1          |
|                                                           | EHDSLocation.position.latitude(*) |            | decimal         |             | 1..1          |
|                                                           | EHDSLocation.position.longitude(*)|            | decimal         |             | 1..1          |
|                                                           | EHDSLocation.type                 |            | CodeableConcept |             | 0..*          |
|                                                           | EHDSOrganization                  |            |                 |             | 0..*          |
|                                                           | EHDSOrganization.address          |            | EHDSAddress     |             | 0..*          |
| HealthcareProvider.HealthcareProviderIdentificationNumber | EHDSOrganization.identifier       | II         | Identifier      | 0..*        | 0..*          |
| HealthcareProvider.OrganizationName                       | EHDSOrganization.name             | ST         | string          | 0..1        | 0..1          |
|                                                           | EHDSOrganization.partOf           |            | Reference       |             | 0..1          |
|                                                           | EHDSOrganization.telecom          |            | EHDSTelecom     |             | 0..*          |
| HealthcareProvider.OrganizationType                       | EHDSOrganization.type             | CD         | CodeableConcept | 0..1        | 0..*          |
| HealthcareProvider.ContactInformation                     |                                   |            |                 | 0..1        |               |
| HealthcareProvider.DepartmentSpecialty                    |                                   | CD         |                 | 0..1        |               |
|                                                           |                                   |            |                 | 0..1        |               |

(*) 20-10-2025: not in main branch

## EHDSLocation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation |
| zib | HealthcareProvider |
| alias_zib | NL: Zorgaanbieder |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.17 - EHDS refined base model for Details and position information for a place where services are provided and resources and participants may be stored, found, contained, or accommodated. |
| definition_zib | Root concept of the Healthcare Provider information model. This root concept contains all data elements of the Healthcare Provider information model. |
| definitioncode_zib | SNOMED CT: 257622000 Healthcare facility |
| id_xtehr | EHDSLocation |
| id_zib | NL-CM:17.2.1 |
| name_zib | HealthcareProvider |
| path_xtehr | EHDSLocation |
| path_zib | HealthcareProvider |
| short_xtehr | Location model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSLocation.address

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.address |
| zib | HealthcareProvider.AddressInformation |
| alias_zib | NL: Adresgegevens |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..* |
| definition_xtehr | Physical location address |
| definition_zib | The physical address of the healthcare provider�s location. |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.address |
| id_zib | NL-CM:17.2.5 |
| name_zib | AddressInformation |
| path_xtehr | EHDSLocation.address |
| path_zib | HealthcareProvider.AddressInformation |
| short_xtehr | C.17.5 - Address |
| stereotype_zib | data,reference |
| type_xtehr | EHDSAddress |
| type_zib |  |

### Comments
The zib allows for multiple addresses, but the Xt-EHR models allows for just one address, defined as "the physical address". This make sense as the address here is meant to define "where somebody should be" (as opposed to the Organization, which can have multiple types of addresses). It's possible that the location/organization duality of the zib is the reason for this.
Note: a concept describing a specific location within a building seems to be missing. 


## EHDSLocation.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.description |
| zib | HealthcareProvider.OrganizationLocation.LocationName |
| alias_zib | NL: LocatieNaam |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Additional details about the location that could be displayed as further information to identify the location beyond its name |
| definition_zib | Name of the location, in case a healthcare organization has more than one location. |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.description |
| id_zib | NL-CM:17.2.8 |
| name_zib | LocationName |
| path_xtehr | EHDSLocation.description |
| path_zib | HealthcareProvider.OrganizationLocation.LocationName |
| short_xtehr | C.17.3 - Description |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments

The zib OrganizationLocation/LocationName/LocationNumber mechanism to refine information about the exact location, so has a degree of overlap with the Xt-EHR description concept. It is not an exact match however.

## EHDSLocation.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.description |
| zib | HealthcareProvider.OrganizationLocation.LocationNumber |
| alias_zib | NL: LocatieNummer |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Additional details about the location that could be displayed as further information to identify the location beyond its name |
| definition_zib | Number of the location Number, if a numerical location identification is used next to or instead of a location name. |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.description |
| id_zib | NL-CM:17.2.10 |
| name_zib | LocationNumber |
| path_xtehr | EHDSLocation.description |
| path_zib | HealthcareProvider.OrganizationLocation.LocationNumber |
| short_xtehr | C.17.3 - Description |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | INT |

### Comments

The zib OrganizationLocation/LocationName/LocationNumber mechanism to refine information about the exact location, so has a degree of overlap with the Xt-EHR description concept. It is not an exact match however.

## EHDSLocation.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.identifier |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Location identifier |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.identifier |
| path_zib |  |
| short_xtehr | C.17.1 - Identifier |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSLocation.managingOrganization

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.managingOrganization |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The organization responsible for the provisioning and upkeep of the location |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.managingOrganization |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.managingOrganization |
| path_zib |  |
| short_xtehr | C.17.7 - Managing organization |
| stereotype_zib |  |
| type_xtehr | Reference |
| type_zib |  |

### Comments

_If_ the zib represents a location, this information is part of the zib, kind of.

## EHDSLocation.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.name |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Name of the location as used by humans |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.name |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.name |
| path_zib |  |
| short_xtehr | C.17.2 - Name |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSLocation.partOf

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.partOf |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Another Location of which this Location is physically a part of |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.partOf |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.partOf |
| path_zib |  |
| short_xtehr | C.17.8 - Part of |
| stereotype_zib |  |
| type_xtehr | Reference |
| type_zib |  |

### Comments

This kind of hierarchical relationships are outside of the scope of the zib.
Note: the reference is of type EHDSOrganization. That should probably be EHDSLocation, as per definition.

## EHDSLocation.position

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.position |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The absolute geographic location of the Location, expressed using the WGS84 datum (This is the same co-ordinate system used in KML). |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.position |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.position |
| path_zib |  |
| short_xtehr | C.17.6 - Position |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSLocation.position.latitude

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.position.latitude |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Latitude with WGS84 datum |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.position.latitude |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.position.latitude |
| path_zib |  |
| short_xtehr | C.17.6.2 - Latitude |
| stereotype_zib |  |
| type_xtehr | decimal |
| type_zib |  |

### Comments



## EHDSLocation.position.longitude

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.position.longitude |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Longitude with WGS84 datum |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.position.longitude |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.position.longitude |
| path_zib |  |
| short_xtehr | C.17.6.1 - Longitude |
| stereotype_zib |  |
| type_xtehr | decimal |
| type_zib |  |

### Comments



## EHDSLocation.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSLocation.type |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 ServiceDeliveryLocationRoleType'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Type of function performed at the location |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSLocation.type |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSLocation.type |
| path_zib |  |
| short_xtehr | C.17.4 - Type |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSOrganization

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.3 - EHDS refined base model for Health provider or any other type of organization |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSOrganization |
| path_zib |  |
| short_xtehr | Organization model |
| stereotype_zib |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSOrganization.address

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization.address |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Mailing and home or office addresses. The addresses are always sequences of address parts (e.g. street address line, country, postcode, city) even if postal address formats may vary depending on the country. An address may or may not include a specific use code; if this attribute is not present it is assumed to be the default address useful for any purpose. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization.address |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSOrganization.address |
| path_zib |  |
| short_xtehr | C.3.4 - Address |
| stereotype_zib |  |
| type_xtehr | EHDSAddress |
| type_zib |  |

### Comments



## EHDSOrganization.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization.identifier |
| zib | HealthcareProvider.HealthcareProviderIdentificationNumber |
| alias_zib | NL: ZorgaanbiederIdentificatienummer |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Health provider organisation identifier |
| definition_zib | The organization�s identification number. For Dutch healthcare providers, the URA number or the AGB number is used, if possible. Depending on the context other IDs are also possible. For foreign or non-affiliated healthcare providers, another unique identification number can be used. This must be accompanied by the name and/or code of the issuing organization. |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization.identifier |
| id_zib | NL-CM:17.2.2 |
| name_zib | HealthcareProviderIdentificationNumber |
| path_xtehr | EHDSOrganization.identifier |
| path_zib | HealthcareProvider.HealthcareProviderIdentificationNumber |
| short_xtehr | C.3.1 - Identifier |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | II |

### Comments



## EHDSOrganization.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization.name |
| zib | HealthcareProvider.OrganizationName |
| alias_zib | NL: OrganisatieNaam |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Health provider organisation name |
| definition_zib | Name of the organization. If an identification number is given, the name must match the name that corresponds to the identification number. |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization.name |
| id_zib | NL-CM:17.2.3 |
| name_zib | OrganizationName |
| path_xtehr | EHDSOrganization.name |
| path_zib | HealthcareProvider.OrganizationName |
| short_xtehr | C.3.3 - Name |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSOrganization.partOf

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization.partOf |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The organization of which this organization forms a part |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization.partOf |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSOrganization.partOf |
| path_zib |  |
| short_xtehr | C.3.6 - Part of |
| stereotype_zib |  |
| type_xtehr | Reference |
| type_zib |  |

### Comments

This kind of hierarchical relationship is outside the scope of the zib

## EHDSOrganization.telecom

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization.telecom |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Telecommunication contact information (addresses) associated with a person, such as phone number, email, or messaging service. Multiple telecommunication addresses might be provided. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization.telecom |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSOrganization.telecom |
| path_zib |  |
| short_xtehr | C.3.5 - Telecom |
| stereotype_zib |  |
| type_xtehr | EHDSTelecom |
| type_zib |  |

### Comments



## EHDSOrganization.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSOrganization.type |
| zib | HealthcareProvider.OrganizationType |
| alias_zib | NL: OrganisatieType |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 organization_type'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Kind of organization |
| definition_zib | The type of healthcare provider, such as general hospital, or nursing home. If this field is filled in and an AGB code is used for the HealthcareProviderIdentificationNumber, the type must match the type implicitly contained in the AGB code. |
| definitioncode_zib |  |
| id_xtehr | EHDSOrganization.type |
| id_zib | NL-CM:17.2.4 |
| name_zib | OrganizationType |
| path_xtehr | EHDSOrganization.type |
| path_zib | HealthcareProvider.OrganizationType |
| short_xtehr | C.3.2 - Type |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments

There is _probably_ a match between zib OrganizationType and the Xt-EHR type concept, as the type according to the RoleCodeNL code system (part of the UZI register) seems to apply to the _organization_ rather than a _location_.

There is a mismatch on both cardinality and terminology binding, although the terminology binding in the Xt-EHR model is only _preferred_.

## zib: HealthcareProvider.ContactInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HealthcareProvider.ContactInformation |
| alias_zib | NL: Contactgegevens |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The information needed to contact the healthcare organization via telephone and/or e-mail. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:17.2.6 |
| name_zib | ContactInformation |
| path_xtehr |  |
| path_zib | HealthcareProvider.ContactInformation |
| short_xtehr |  |
| stereotype_zib | data,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: HealthcareProvider.DepartmentSpecialty

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | HealthcareProvider.DepartmentSpecialty |
| alias_zib | NL: AfdelingSpecialisme |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The specialty of the healthcare provider�s department. The departmental specialty can be filled in if further indication of the healthcare provider is needed. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:17.2.7 |
| name_zib | DepartmentSpecialty |
| path_xtehr |  |
| path_zib | HealthcareProvider.DepartmentSpecialty |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |
| alias_zib | NL: OrganisatieLocatie |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Container of the OrganizationLocation concept. This container contains all data elements of the OrganizationLocation concept. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:17.2.9 |
| name_zib | OrganizationLocation |
| path_xtehr |  |
| path_zib | HealthcareProvider.OrganizationLocation |
| short_xtehr |  |
| stereotype_zib | container |
| type_xtehr |  |
| type_zib |  |

### Comments


