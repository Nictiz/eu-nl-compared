# Device

| zib                                        | xtehr                      | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:-------------------------------------------|:---------------------------|:-----------|:----------------|:------------|:--------------|
| MedicalDevice.Product                      | EHDSDevice                 |            |                 | 1           | 0..*          |
|                                            | EHDSDevice.expiryDate      |            | dateTime        |             | 0..1          |
| MedicalDevice.Product.ProductID            | EHDSDevice.identifier      | ST         | Identifier      | 0..1        | 1..*          |
|                                            | EHDSDevice.lotNumber       |            | string          |             | 0..1          |
|                                            | EHDSDevice.manufactureDate |            | dateTime        |             | 0..1          |
|                                            | EHDSDevice.manufacturer    |            | string          |             | 0..1          |
|                                            | EHDSDevice.modelNumber     |            | string          |             | 0..1          |
|                                            | EHDSDevice.name            |            | string          |             | 0..*          |
|                                            | EHDSDevice.note            |            | Narrative       |             | 0..*          |
|                                            | EHDSDevice.serialNumber    |            | string          |             | 0..1          |
| MedicalDevice.Product.ProductType          | EHDSDevice.type            | CD         | CodeableConcept | 0..1        | 0..*          |
|                                            | EHDSDevice.version         |            | string          |             | 0..1          |
| MedicalDevice                              | EHDSDeviceUse              |            |                 |             | 0..*          |
| MedicalDevice.AnatomicalLocation           | EHDSDeviceUse.bodySite     |            | CodeableConcept | 0..1        | 0..1          |
|                                            | EHDSDeviceUse.device       |            | Reference       |             | 1..1          |
| MedicalDevice.EndDate                      | EHDSDeviceUse.endDate      | TS         | dateTime        | 0..1        | 0..1          |
|                                            | EHDSDeviceUse.identifier   |            | Identifier      |             | 0..*          |
| MedicalDevice.StartDate                    | EHDSDeviceUse.implantDate  | TS         | dateTime        | 0..1        | 0..1          |
| MedicalDevice.Comment                      | EHDSDeviceUse.note         | ST         | Narrative       | 0..1        | 0..*          |
|                                            | EHDSDeviceUse.recorded     |            | dateTime        |             | 0..1          |
|                                            | EHDSDeviceUse.source       |            | Reference       |             | 0..1          |
|                                            | EHDSDeviceUse.status       |            | CodeableConcept |             | 0..1          |
|                                            | EHDSDeviceUse.subject      |            | Reference       |             | 1..1          |
| MedicalDevice.HealthProfessional           |                            |            |                 | 0..1        |               |
| MedicalDevice.Indication::Diagnosis        |                            |            |                 | 0..*        |               |
| MedicalDevice.Indication::Problem          |                            |            |                 |             |               |
| MedicalDevice.Location::HealthcareProvider |                            |            |                 | 0..1        |               |
| MedicalDevice.ProductDescription           |                            | ST         |                 | 0..1        |               |



## EHDSDevice

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice |
| zib | MedicalDevice.Product |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 1 |
| definition_xtehr | C.12 - EHDS refined base model for Device information |
| definition_zib | The medical device (internally or externally). |
| definitioncode_zib | 405815000 Procedure device |
| id_xtehr | EHDSDevice |
| id_zib | NL-CM:10.1.2 |
| name_zib | Product |
| path_xtehr | EHDSDevice |
| path_zib | MedicalDevice.Product |
| short_xtehr | Device model |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSDevice.expiryDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.expiryDate |
| zib |  |
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
| short_xtehr | C.12.4 - Expiry date |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDevice.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.identifier |
| zib | MedicalDevice.Product.ProductID |
| binding_xtehr |  |
| card._xtehr | 1..* |
| card._zib | 0..1 |
| definition_xtehr | An identifier of the device which is unique within in a defined scope. Multiple identifiers can be used. |
| definition_zib | Globally unique identification of the product, for example the serial number or a UDI (unique device identifier). For some products, the law requires the use of a UDI. Commonly used coding systems are HIBC and GS1/GTIN.
A UDI often contains more information than just an ID, but also, for example, an expiration date. If a UDI is used, the entire code can be included as text in ProductID, so that no important information is lost. |
| definitioncode_zib |  |
| id_xtehr | EHDSDevice.identifier |
| id_zib | NL-CM:10.1.16 |
| name_zib | ProductID |
| path_xtehr | EHDSDevice.identifier |
| path_zib | MedicalDevice.Product.ProductID |
| short_xtehr | C.12.1 - Identifier |
| type_xtehr | Identifier |
| type_zib | ST |

### Comments



## EHDSDevice.lotNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.lotNumber |
| zib |  |
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
| short_xtehr | C.12.5 - Lot number |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.manufactureDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.manufactureDate |
| zib |  |
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
| short_xtehr | C.12.3 - Manufacture date |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDevice.manufacturer

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.manufacturer |
| zib |  |
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
| short_xtehr | C.12.2 - Manufacturer |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.modelNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.modelNumber |
| zib |  |
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
| short_xtehr | C.12.8 - Model number |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.name

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.name |
| zib |  |
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
| short_xtehr | C.12.7 - Name |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.note |
| zib |  |
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
| short_xtehr | C.12.11 - Note |
| type_xtehr | Narrative |
| type_zib |  |

### Comments



## EHDSDevice.serialNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.serialNumber |
| zib |  |
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
| short_xtehr | C.12.6 - Serial number |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDevice.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.type |
| zib | MedicalDevice.Product.ProductType |
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
| short_xtehr | C.12.10 - Type |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSDevice.version

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.version |
| zib |  |
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
| short_xtehr | C.12.9 - Version |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSDeviceUse

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse |
| zib | MedicalDevice |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.25 - EHDS refined base model for Device Use |
| definition_zib | Root concept of the MedicalDevice information model. This root concept contains all data elements of the MedicalDevice information model. |
| definitioncode_zib | 49062001 Device |
| id_xtehr | EHDSDeviceUse |
| id_zib | NL-CM:10.1.1 |
| name_zib | MedicalDevice |
| path_xtehr | EHDSDeviceUse |
| path_zib | MedicalDevice |
| short_xtehr | Device use model |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSDeviceUse.bodySite

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.bodySite |
| zib | MedicalDevice.AnatomicalLocation |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Anatomical location of the device. May include laterality. |
| definition_zib | Patient’s anatomical location of the medical device used. |
| definitioncode_zib | 363698007 Finding site |
| id_xtehr | EHDSDeviceUse.bodySite |
| id_zib | NL-CM:10.1.15 |
| name_zib | AnatomicalLocation |
| path_xtehr | EHDSDeviceUse.bodySite |
| path_zib | MedicalDevice.AnatomicalLocation |
| short_xtehr | C.25.7 - Body site |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.device

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.device |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | The details of the device used. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.device |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.device |
| path_zib |  |
| short_xtehr | C.25.5 - Device |
| type_xtehr | Reference |
| type_zib |  |

### Comments



## EHDSDeviceUse.endDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.endDate |
| zib | MedicalDevice.EndDate |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date when the device was explanted from the patient or the external device was no longer in use; likewise when the device is planned to be explanted. |
| definition_zib | The end date of the last use or explant of the medical device. A ‘vague’ date, such as only the year, is permitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.endDate |
| id_zib | NL-CM:10.1.14 |
| name_zib | EndDate |
| path_xtehr | EHDSDeviceUse.endDate |
| path_zib | MedicalDevice.EndDate |
| short_xtehr | C.25.4 - End date |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSDeviceUse.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.identifier |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | An identifier for this statement. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.identifier |
| path_zib |  |
| short_xtehr | C.25.1 - Identifier |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSDeviceUse.implantDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.implantDate |
| zib | MedicalDevice.StartDate |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date when procedure was performed. |
| definition_zib | The start date of the first use or implant of the medical device. A ‘vague’ date, such as only the year, is permitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.implantDate |
| id_zib | NL-CM:10.1.11 |
| name_zib | StartDate |
| path_xtehr | EHDSDeviceUse.implantDate |
| path_zib | MedicalDevice.StartDate |
| short_xtehr | C.25.3 - Implant date |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments



## EHDSDeviceUse.note

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.note |
| zib | MedicalDevice.Comment |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Details about the device statement that were not represented at all or sufficiently in one of the attributes provided in a class. These may include for example a comment, an instruction, or a note associated with the statement. |
| definition_zib | Comment about use or information on the medical device used. |
| definitioncode_zib | 48767-8 Annotation comment [Interpretation] Narrative |
| id_xtehr | EHDSDeviceUse.note |
| id_zib | NL-CM:10.1.10 |
| name_zib | Comment |
| path_xtehr | EHDSDeviceUse.note |
| path_zib | MedicalDevice.Comment |
| short_xtehr | C.25.8 - Note |
| type_xtehr | Narrative |
| type_zib | ST |

### Comments



## EHDSDeviceUse.recorded

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.recorded |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Date and time at which the statement was made/recorded. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.recorded |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.recorded |
| path_zib |  |
| short_xtehr | C.25.9 - Recorded |
| type_xtehr | dateTime |
| type_zib |  |

### Comments



## EHDSDeviceUse.source

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.source |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Who reported the device was being used by the patient. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.source |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.source |
| path_zib |  |
| short_xtehr | C.25.10 - Source |
| type_xtehr | Reference |
| type_zib |  |

### Comments



## EHDSDeviceUse.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.status |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'HL7 device-statement-status'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Current status of the Device Usage. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.status |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.status |
| path_zib |  |
| short_xtehr | C.25.2 - Status |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.subject |
| zib |  |
| binding_xtehr |  |
| card._xtehr | 1..1 |
| card._zib |  |
| definition_xtehr | The patient using the device. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.subject |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.subject |
| path_zib |  |
| short_xtehr | C.25.6 - Subject |
| type_xtehr | Reference |
| type_zib |  |

### Comments



## zib: MedicalDevice.HealthProfessional

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.HealthProfessional |
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
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.Indication::Diagnosis

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.Indication::Diagnosis |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..* |
| definition_xtehr |  |
| definition_zib | The diagnosis as indication for the medical device. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:10.1.17 |
| name_zib | Indication::Diagnosis |
| path_xtehr |  |
| path_zib | MedicalDevice.Indication::Diagnosis |
| short_xtehr |  |
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.Indication::Problem

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.Indication::Problem |
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
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.Location::HealthcareProvider

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.Location::HealthcareProvider |
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
| type_xtehr |  |
| type_zib |  |

### Comments



## zib: MedicalDevice.ProductDescription

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | MedicalDevice.ProductDescription |
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
| type_xtehr |  |
| type_zib | ST |

### Comments

