# Device

| zib                                        | xtehr                                     | type_zib   | type_xtehr             | card._zib   | card._xtehr   |
|:-------------------------------------------|:------------------------------------------|:-----------|:-----------------------|:------------|:--------------|
| MedicalDevice.Product                      | EHDSDevice                                |            |                        | 1           | 0..*          |
|                                            | EHDSDevice.expiryDate                     |            | dateTime               |             | 0..1          |
|                                            |                                           |            | Identifier             |             | 1..*          |
|                                            | EHDSDevice.lotNumber                      |            | string                 |             | 0..1          |
|                                            | EHDSDevice.manufactureDate                |            | dateTime               |             | 0..1          |
|                                            | EHDSDevice.manufacturer                   |            | string                 |             | 0..1          |
|                                            | EHDSDevice.modelNumber                    |            | string                 |             | 0..1          |
|                                            | EHDSDevice.name                           |            | string                 |             | 0..*          |
|                                            | EHDSDevice.note                           |            | string                 |             | 0..*          |
|                                            | EHDSDevice.serialNumber                   |            | string                 |             | 0..1          |
| MedicalDevice.Product.ProductType          | EHDSDevice.type                           | CD         | CodeableConcept        | 0..1        | 0..*          |
|                                            | EHDSDevice.version                        |            | string                 |             | 0..1          |
| MedicalDevice                              | EHDSDeviceUse                             |            |                        |             | 0..*          |
| MedicalDevice.AnatomicalLocation           | EHDSDeviceUse.bodySite                    |            | EHDSBodyStructure      | 0..1        | 0..1          |
|                                            | EHDSDeviceUse.device[x]                   |            | CodeableConcept        |             | 1..1          |
| MedicalDevice.EndDate                      | EHDSDeviceUse.endDate                     | TS         | dateTime               | 0..1        | 0..1          |
|                                            | EHDSDeviceUse.header                      |            | Base                   |             | 1..1          |
|                                            | EHDSDeviceUse.header.authorship           |            | Base                   |             | 1..*          |
|                                            | EHDSDeviceUse.header.authorship.author[x] |            | EHDSHealthProfessional |             | 1..1          |
|                                            | EHDSDeviceUse.header.authorship.datetime  |            | dateTime               |             | 1..1          |
| MedicalDevice.Product.ProductID            | EHDSDeviceUse.header.identifier           | ST         | Identifier             | 0..1        | 0..*          |
|                                            | EHDSDeviceUse.header.language             |            | CodeableConcept        |             | 0..1          |
|                                            | EHDSDeviceUse.header.lastUpdate           |            | dateTime               |             | 0..1          |
|                                            | EHDSDeviceUse.header.status               |            | CodeableConcept        |             | 1..1          |
|                                            | EHDSDeviceUse.header.statusReason[x]      |            | CodeableConcept        |             | 0..1          |
|                                            | EHDSDeviceUse.header.subject              |            | EHDSPatient            |             | 1..1          |
|                                            | EHDSDeviceUse.header.version              |            | string                 |             | 0..1          |
| MedicalDevice.Comment                      | EHDSDeviceUse.note                        | ST         | string                 | 0..1        | 0..*          |
|                                            | EHDSDeviceUse.presentedForm               |            | EHDSAttachment         |             | 0..*          |
| MedicalDevice.Indication::Diagnosis        | EHDSDeviceUse.reason[x]                   |            | CodeableConcept        | 0..*        | 0..*          |
|                                            | EHDSDeviceUse.recorded                    |            |                        |             |               |
|                                            | EHDSDeviceUse.source[x]                   |            | EHDSPatient            |             | 0..1          |
| MedicalDevice.StartDate                    | EHDSDeviceUse.startDate                   | TS         | dateTime               | 0..1        | 0..1          |
|                                            | EHDSDeviceUse.status                      |            |                        |             |               |
| MedicalDevice.HealthProfessional           |                                           |            |                        | 0..1        |               |
| MedicalDevice.Location::HealthcareProvider |                                           |            |                        | 0..1        |               |
| MedicalDevice.ProductDescription           |                                           | ST         |                        | 0..1        |               |



## EHDSDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice |
| zib | MedicalDevice.Product |
| alias_zib | NL: Product |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | EHDS refined base model for Device information |
| definition_zib | The medical device (internally or externally). |
| definitioncode_zib | SNOMED CT: 405815000 Procedure device |
| id_xtehr | EHDSDevice |
| id_zib | NL-CM:10.1.2 |
| name_zib | Product |
| path_xtehr | EHDSDevice |
| path_zib | MedicalDevice.Product |
| short_xtehr | Device model |
| stereotype_zib | container |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSDevice.expiryDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.expiryDate |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The date and time beyond which this device is no longer valid or should not be used (if applicable). |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.expiryDate |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.expiryDate |
| path_zib |  |
| short_xtehr | The date and time beyond which this device is no longer valid or should not be used (if applicable). |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib |  |
| definition_xtehr | Normalised identifier of the device instance, such as UDI according to REGULATION (EU) 2017/745. Multiple identifiers can be used. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.identifier |
| path_zib |  |
| short_xtehr | Normalised identifier of the device instance, such as UDI according to REGULATION (EU) 2017/745. Multiple identifiers can be used. |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSDevice.lotNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.lotNumber |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Lot number of manufacture |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.lotNumber |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.lotNumber |
| path_zib |  |
| short_xtehr | Lot number of manufacture |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.manufactureDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.manufactureDate |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The date and time when the device was manufactured |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.manufactureDate |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.manufactureDate |
| path_zib |  |
| short_xtehr | The date and time when the device was manufactured |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDevice.manufacturer

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.manufacturer |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Name of device manufacturer |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.manufacturer |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.manufacturer |
| path_zib |  |
| short_xtehr | Name of device manufacturer |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.modelNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.modelNumber |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The manufacturer's model number for the device |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.modelNumber |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.modelNumber |
| path_zib |  |
| short_xtehr | The manufacturer's model number for the device |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.name |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The name and name type of the device as known to the manufacturer and/or patient |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.name |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.name |
| path_zib |  |
| short_xtehr | The name and name type of the device as known to the manufacturer and/or patient |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.note |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Device notes and comments |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.note |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.note |
| path_zib |  |
| short_xtehr | Device notes and comments |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.serialNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.serialNumber |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Serial number assigned by the manufacturer |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.serialNumber |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.serialNumber |
| path_zib |  |
| short_xtehr | Serial number assigned by the manufacturer |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.type |
| zib | MedicalDevice.Product.ProductType |
| alias_zib | NL: ProductType |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT, EMDN'} |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Device type |
| definition_zib | The code of the type of product. |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.type |
| id_zib | NL-CM:10.1.3 |
| name_zib | ProductType |
| path_xtehr | EHDSDevice.type |
| path_zib | MedicalDevice.Product.ProductType |
| short_xtehr | Device type |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSDevice.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.version |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The actual design of the device or software version running on the device |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.version |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDevice.version |
| path_zib |  |
| short_xtehr | The actual design of the device or software version running on the device |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDeviceUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse |
| zib | MedicalDevice |
| alias_zib | NL: MedischHulpmiddel |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for device use information |
| definition_zib | Root concept of the MedicalDevice information model. This root concept contains all data elements of the MedicalDevice information model. |
| definitioncode_zib | SNOMED CT: 49062001 Device |
| id_xtehr | EHDSDeviceUse |
| id_zib | NL-CM:10.1.1 |
| name_zib | MedicalDevice |
| path_xtehr | EHDSDeviceUse |
| path_zib | MedicalDevice |
| short_xtehr | Device use model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSDeviceUse.bodySite

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.bodySite |
| zib | MedicalDevice.AnatomicalLocation |
| alias_zib | NL: AnatomischeLocatie |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Anatomical location of the device. May include laterality. |
| definition_zib | Patient’s anatomical location of the medical device used. |
| definitioncode_zib | SNOMED CT: 363698007 Finding site |
| id_xtehr | EHDSDeviceUse.bodySite |
| id_zib | NL-CM:10.1.15 |
| name_zib | AnatomicalLocation |
| path_xtehr | EHDSDeviceUse.bodySite |
| path_zib | MedicalDevice.AnatomicalLocation |
| short_xtehr | Anatomical location of the device. May include laterality. |
| stereotype_zib | data,reference |
| type_xtehr | EHDSBodyStructure |
| type_zib |  |

### Comments



## EHDSDeviceUse.device[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.device[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | The details of the device used. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.device[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.device[x] |
| path_zib |  |
| short_xtehr | The details of the device used. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.endDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.endDate |
| zib | MedicalDevice.EndDate |
| alias_zib | NL: EindDatum |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date when the device was explanted from the patient or the external device was no longer in use. |
| definition_zib | The end date of the last use or explant of the medical device. A ‘vague’ date, such as only the year, is permitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.endDate |
| id_zib | NL-CM:10.1.14 |
| name_zib | EndDate |
| path_xtehr | EHDSDeviceUse.endDate |
| path_zib | MedicalDevice.EndDate |
| short_xtehr | Date when the device was explanted from the patient or the external device was no longer in use. |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSDeviceUse.header

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Common header for all patient-related data |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header |
| path_zib |  |
| short_xtehr | Common header for all patient-related data |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.authorship

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.authorship |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib |  |
| definition_xtehr | Resource authoring details |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.authorship |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.authorship |
| path_zib |  |
| short_xtehr | Authorship |
| stereotype_zib |  |
| type_xtehr | Base |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.authorship.author[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.authorship.author[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Author(s) by whom the resource was/were authored. Multiple authors could be provided. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.authorship.author[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.authorship.author[x] |
| path_zib |  |
| short_xtehr | Author |
| stereotype_zib |  |
| type_xtehr | EHDSHealthProfessional |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.authorship.datetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.authorship.datetime |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Date and time of the issuing the document/resource by its author. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.authorship.datetime |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.authorship.datetime |
| path_zib |  |
| short_xtehr | Date and time of authoring/issuing |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.identifier |
| zib | MedicalDevice.Product.ProductID |
| alias_zib | NL: ProductID |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Business identifier for the object |
| definition_zib | Globally unique identification of the product, for example the serial number or a UDI (unique device identifier). For some products, the law requires the use of a UDI. Commonly used coding systems are HIBC and GS1/GTIN.

A UDI often contains more information than just an ID, but also, for example, an expiration date. If a UDI is used, the entire code can be included as text in ProductID, so that no important information is lost. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.identifier |
| id_zib | NL-CM:10.1.16 |
| name_zib | ProductID |
| path_xtehr | EHDSDeviceUse.header.identifier |
| path_zib | MedicalDevice.Product.ProductID |
| short_xtehr | Business identifier for the object |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | ST |

### Comments



## EHDSDeviceUse.header.language

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.language |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'BCP 47'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Language in which the resource is written. Language is expressed by the IETF language tag. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.language |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.language |
| path_zib |  |
| short_xtehr | Language |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.lastUpdate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.lastUpdate |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Date and time of the last update to the document/information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.lastUpdate |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.lastUpdate |
| path_zib |  |
| short_xtehr | Date and time of the last update to the resource |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.status |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 device-statement-status'} |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Status of the resource |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.status |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.status |
| path_zib |  |
| short_xtehr | Current status of the device usage. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.statusReason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.statusReason[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Reason for the current status of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.statusReason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.statusReason[x] |
| path_zib |  |
| short_xtehr | Reason for the current status of the resource. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.subject |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | Patient/subject information |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.subject |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.subject |
| path_zib |  |
| short_xtehr | Subject |
| stereotype_zib |  |
| type_xtehr | EHDSPatient |
| type_zib |  |

### Comments



## EHDSDeviceUse.header.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.header.version |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Business version of the resource. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.header.version |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.header.version |
| path_zib |  |
| short_xtehr | Version |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDeviceUse.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.note |
| zib | MedicalDevice.Comment |
| alias_zib | NL: Toelichting |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Note about the device statement that were not represented at all or sufficiently in one of the attributes provided in a class. These may include for example a comment, an instruction, or a note associated with the statement. |
| definition_zib | Comment about use or information on the medical device used. |
| definitioncode_zib | LOINC: 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSDeviceUse.note |
| id_zib | NL-CM:10.1.10 |
| name_zib | Comment |
| path_xtehr | EHDSDeviceUse.note |
| path_zib | MedicalDevice.Comment |
| short_xtehr | Note about the device statement that were not represented at all or sufficiently in one of the attributes provided in a class. These may include for example a comment, an instruction, or a note associated with the statement. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments



## EHDSDeviceUse.presentedForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.presentedForm |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.presentedForm |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.presentedForm |
| path_zib |  |
| short_xtehr | A narrative easy-to-read representation of the full data set, e.g. PDF-version of a document |
| stereotype_zib |  |
| type_xtehr | EHDSAttachment |
| type_zib |  |

### Comments



## EHDSDeviceUse.reason[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.reason[x] |
| zib | MedicalDevice.Indication::Diagnosis |
| alias_zib | NL: Indicatie::Diagnose |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Reason or justification for the use of the device. |
| definition_zib | The diagnosis as indication for the medical device. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.reason[x] |
| id_zib | NL-CM:10.1.17 |
| name_zib | Indication::Diagnosis |
| path_xtehr | EHDSDeviceUse.reason[x] |
| path_zib | MedicalDevice.Indication::Diagnosis |
| short_xtehr | Reason or justification for the use of the device. |
| stereotype_zib | context,reference |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.recorded

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.recorded |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib |  |
| definition_xtehr |  |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib |  |
| name_zib |  |
| path_xtehr |  |
| path_zib |  |
| short_xtehr |  |
| stereotype_zib |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSDeviceUse.source[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.source[x] |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Who reported the device was being used by the patient. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.source[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.source[x] |
| path_zib |  |
| short_xtehr | Who reported the device was being used by the patient. |
| stereotype_zib |  |
| type_xtehr | EHDSPatient |
| type_zib |  |

### Comments



## EHDSDeviceUse.startDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.startDate |
| zib | MedicalDevice.StartDate |
| alias_zib | NL: BeginDatum |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date when the device was implantable to the patient or the external device was first in use. |
| definition_zib | The start date of the first use or implant of the medical device. A ‘vague’ date, such as only the year, is permitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.startDate |
| id_zib | NL-CM:10.1.11 |
| name_zib | StartDate |
| path_xtehr | EHDSDeviceUse.startDate |
| path_zib | MedicalDevice.StartDate |
| short_xtehr | Date when the device was implantable to the patient or the external device was first in use. |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSDeviceUse.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.status |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib |  |
| definition_xtehr |  |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib |  |
| name_zib |  |
| path_xtehr |  |
| path_zib |  |
| short_xtehr |  |
| stereotype_zib |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.HealthProfessional |
| alias_zib | NL: Zorgverlener |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The health professional involved in the indication for use of the medical device implant. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:10.1.9 |
| name_zib | HealthProfessional |
| path_xtehr |  |
| path_zib | MedicalDevice.HealthProfessional |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.Location::HealthcareProvider

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.Location::HealthcareProvider |
| alias_zib | NL: Locatie::Zorgaanbieder |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The healthcare provider where use of the medical device was initiated or where the aid was implanted. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:10.1.8 |
| name_zib | Location::HealthcareProvider |
| path_xtehr |  |
| path_zib | MedicalDevice.Location::HealthcareProvider |
| short_xtehr |  |
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.ProductDescription

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.ProductDescription |
| alias_zib | NL: ProductOmschrijving |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Textual description of the product. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:10.1.13 |
| name_zib | ProductDescription |
| path_xtehr |  |
| path_zib | MedicalDevice.ProductDescription |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments

