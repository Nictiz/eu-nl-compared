# Address as of 2025-05-28
## Overall conclusion
The zib specifies the house number at a much higher granularity than the Xt-EHR model, making this aspect incompatible; a house number according to the Xt-EHR is a "rendered" version of all the information in the zib.

In addition, the Xt-EHR model includes a rendered version of the full address, potentially duplicating data present in other concepts. This conflicts with the zib design principles.

Both the zib and the Xt-EHR model contain information on how the address is used. However, the Xt-EHR model specifies this information on two axes while the zib combines this in a single axis. From previous FHIR mapping of the zib, it is known that this relation is not straightforward.

Both the zib and the Xt-EHR model define optional concepts that the other doesn't recognize (resp. Municipality and postBox), this doesn't seem to introduce any conflicts.

| zib                                      | xtehr                   | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:-----------------------------------------|:------------------------|:-----------|:----------------|:------------|:--------------|
| AddressInformation                       | EHDSAddress             |            |                 |             | 0..*          |
| AddressInformation.PlaceOfResidence      | EHDSAddress.city        | ST         | string          | 0..1        | 0..1          |
| AddressInformation.Country               | EHDSAddress.country     | CD         | CodeableConcept | 0..1        | 0..1          |
| AddressInformation.HouseNumber           | EHDSAddress.houseNumber | ST         | string          | 0..1        | 0..1          |
|                                          | EHDSAddress.postBox     |            | string          |             | 0..1          |
| AddressInformation.Postcode              | EHDSAddress.postalCode  | ST         | string          | 0..1        | 0..1          |
| AddressInformation.Street                | EHDSAddress.street      | ST         | string          | 0..1        | 0..1          |
|                                          | EHDSAddress.text        |            | string          |             | 0..1          |
| AddressInformation.AddressType           | EHDSAddress.type        | CD         | CodeableConcept | 0..1        | 0..1          |
| AddressInformation.AddressType           | EHDSAddress.use         | CD         | CodeableConcept | 0..1        | 0..1          |
| AddressInformation.AdditionalInformation |                         | ST         |                 | 0..1        |               |
| AddressInformation.HouseNumberAddition   |                         | ST         |                 | 0..1        |               |
| AddressInformation.HouseNumberIndication |                         | CD         |                 | 0..1        |               |
| AddressInformation.HouseNumberLetter     |                         | ST         |                 | 0..1        |               |
| AddressInformation.Municipality          |                         | ST         |                 | 0..1        |               |



## EHDSAddress

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress |
| zib | AddressInformation |
| alias_zib | NL: Adresgegevens |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for Address structure |
| definition_zib | Root concept of the AddressInformation partial information model. This root concept contains all data elements of the AddressInformation partial information model. |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress |
| id_zib | NL-CM:20.5.1 |
| name_zib | AddressInformation |
| path_xtehr | EHDSAddress |
| path_zib | AddressInformation |
| short_xtehr | Address model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSAddress.city

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.city |
| zib | AddressInformation.PlaceOfResidence |
| alias_zib | NL: Woonplaats |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | City |
| definition_zib | A geographically determined area which forms part of the municipal area. 
For Dutch places of residence, preferably use the name from the GBA, table 33 (OID: 2.16.840.1.113883.2.4.6.14). |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.city |
| id_zib | NL-CM:20.5.3 |
| name_zib | PlaceOfResidence |
| path_xtehr | EHDSAddress.city |
| path_zib | AddressInformation.PlaceOfResidence |
| short_xtehr | City |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
The zib defines two kinds of "city": PlaceOfResidence (Woonplaats) and Municipality (Gemeente). For the address as found on a letter, the PlaceOfResidence is relevant. I _assume_ this is what the city concept is about as well.


## EHDSAddress.country

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.country |
| zib | AddressInformation.Country |
| alias_zib | NL: Land |
| binding_xtehr | {'strength': 'preferred', 'description': 'ISO 3166-1 alpha-2'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Country name and country code |
| definition_zib | Country in which the address is located. |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.country |
| id_zib | NL-CM:20.5.5 |
| name_zib | Country |
| path_xtehr | EHDSAddress.country |
| path_zib | AddressInformation.Country |
| short_xtehr | Country name and country code |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
The zib requires the country to be coded using either ISO 3166-1 (alpha-2) or GBA Tabel 34. The Xt-EHR model doesn't have a requirement but prefers ISO 3166-1 (alpha-2). Zib instances are thus valid Xt-EHR instances, but there's no guarantee that the other way around is true as well.


## EHDSAddress.houseNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.houseNumber |
| zib | AddressInformation.HouseNumber |
| alias_zib | NL: Huisnummer |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | House number |
| definition_zib | House number of the address. |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.houseNumber |
| id_zib | NL-CM:20.5.12 |
| name_zib | HouseNumber |
| path_xtehr | EHDSAddress.houseNumber |
| path_zib | AddressInformation.HouseNumber |
| short_xtehr | House number |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
The zib has a total of five concepts that contribute to the house number (HouseNumber, HouseNumberLetter, HouseNumberAddition, HouseNumberIndication and AdditionalInformation), whereas Xt-EHR has one or two, depending on the way of counting (houseNumber and text). The Xt-EHR houseNumber concept doesn't specify exactly what it is, but it is reasonable to assume it simply is "the thing you put next to the street name".

There's a discrepancy here; a zib HouseNumber potentially contains much less information than an Xt-EHR houseNumber (e.g. a house number of "3-bis" would become Xt-EHR houseNumber "3-bis", but zib HouseNumber "3"). Note that this is a different situation then where a zib specifies _additional_ concept compared to Xt-EHR; here the zib defines the _same_ concept but spreads it out over different elements.


## EHDSAddress.postBox

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.postBox |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Post box |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.postBox |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAddress.postBox |
| path_zib |  |
| short_xtehr | Post box |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSAddress.postalCode

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.postalCode |
| zib | AddressInformation.Postcode |
| alias_zib | NL: Postcode |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Postal code |
| definition_zib | Postcode of the address. 
In Dutch addresses, preferably use the postcode from the Postcode table (OID: 2.16.840.1.113883.2.4.4.15). |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.postalCode |
| id_zib | NL-CM:20.5.6 |
| name_zib | Postcode |
| path_xtehr | EHDSAddress.postalCode |
| path_zib | AddressInformation.Postcode |
| short_xtehr | Postal code |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
✅ these concepts align


## EHDSAddress.street

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.street |
| zib | AddressInformation.Street |
| alias_zib | NL: Straat |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Name of the street |
| definition_zib | Street name of the address. |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.street |
| id_zib | NL-CM:20.5.2 |
| name_zib | Street |
| path_xtehr | EHDSAddress.street |
| path_zib | AddressInformation.Street |
| short_xtehr | Name of the street |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
✅ these concepts align


## EHDSAddress.text

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.text |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Text representation of the address |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.text |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSAddress.text |
| path_zib |  |
| short_xtehr | Text representation of the address |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
If a text representation is present next to the other elements, there is duplication of data, which goes against the zib design principes.


## EHDSAddress.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.type |
| zib | AddressInformation.AddressType |
| alias_zib | NL: AdresSoort |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 AddressType'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Distinguishes between physical addresses (those you can visit) and mailing addresses (e.g. PO Boxes and care-of addresses). Most addresses are both. |
| definition_zib | The type of address in question, such as a home address or mailing address. |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.type |
| id_zib | NL-CM:20.5.8 |
| name_zib | AddressType |
| path_xtehr | EHDSAddress.type |
| path_zib | AddressInformation.AddressType |
| short_xtehr | Distinguishes between physical addresses (those you can visit) and mailing addresses (e.g. PO Boxes and care-of addresses). Most addresses are both. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
The AddressTyoe contains aspects of both Xt-EHR concepts type and use. The mapping is not straightforward. At the moment, the preferred binding for the Xt-EHR concepts is the same as in the FHIR data type _Address_, for which the mapping has been defined in the following way in the zib FHIR profile:

| zib                               | use   | type      |
| --------------------------------- | ----- | --------- |
| Postal Address/Postadres          |       | postal    |
| Primary Home/Officieel adres      | home  | both      |
| Visit Address/Woon-/verblijfadres | home  | physical  |
| Temporary Address/Tijdelijk adres | temp 	|           |
| Work Place/Werkadres              | work 	|           |
| Vacation Home/Vakantie adres      | temp 	|           |

This mapping is inexact; the FHIR profile requires the original code to be used in an extension as well.

## EHDSAddress.use

### Table

| attribute | value |
|---|---|
| xtehr | EHDSAddress.use |
| zib | AddressInformation.AddressType |
| alias_zib | NL: AdresSoort |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 AddressUse'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Purpose of the address |
| definition_zib | The type of address in question, such as a home address or mailing address. |
| definitioncode_zib |  |
| id_xtehr | EHDSAddress.use |
| id_zib | NL-CM:20.5.8 |
| name_zib | AddressType |
| path_xtehr | EHDSAddress.use |
| path_zib | AddressInformation.AddressType |
| short_xtehr | Purpose of the address |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
See the comment for type


## zib: AddressInformation.AdditionalInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AddressInformation.AdditionalInformation |
| alias_zib | NL: AdditioneleInformatie |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Extra information such as the building name, building number, entrance, route number. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.5.7 |
| name_zib | AdditionalInformation |
| path_xtehr |  |
| path_zib | AddressInformation.AdditionalInformation |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the comment for EHDSAddress.houseNumber


## zib: AddressInformation.HouseNumberAddition

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AddressInformation.HouseNumberAddition |
| alias_zib | NL: Huisnummertoevoeging |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The letters or signs needed to locate the mailbox, in addition to the house number and letter. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.5.10 |
| name_zib | HouseNumberAddition |
| path_xtehr |  |
| path_zib | AddressInformation.HouseNumberAddition |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the comment for EHDSAddress.houseNumber


## zib: AddressInformation.HouseNumberIndication

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AddressInformation.HouseNumberIndication |
| alias_zib | NL: AanduidingBijNummer |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The indication used for addresses which do not consist of the usual street name and house number. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.5.9 |
| name_zib | HouseNumberIndication |
| path_xtehr |  |
| path_zib | AddressInformation.HouseNumberIndication |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments
See the comment for EHDSAddress.houseNumber


## zib: AddressInformation.HouseNumberLetter

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AddressInformation.HouseNumberLetter |
| alias_zib | NL: Huisnummerletter |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | A letter following the house number as assigned by the municipal authorities. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.5.11 |
| name_zib | HouseNumberLetter |
| path_xtehr |  |
| path_zib | AddressInformation.HouseNumberLetter |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the comment for EHDSAddress.houseNumber


## zib: AddressInformation.Municipality

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | AddressInformation.Municipality |
| alias_zib | NL: Gemeente |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Municipality of residence.  
For Dutch municipalities, preferably use the name from the GBA, table 33 (OID: 2.16.840.1.113883.2.4.6.14). |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.5.4 |
| name_zib | Municipality |
| path_xtehr |  |
| path_zib | AddressInformation.Municipality |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the comment for EHDSAddress.placeOfResidence