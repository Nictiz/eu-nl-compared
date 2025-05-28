# Device as of 2025-05-27
## Overall conclusion
Xt-EHR defines a device and its use as two distinct models, whereas the zib regards them as one, but this doesn't seem to introduce any conflicts.

Regarding Xt-EHR, the Device model defines some detailed optional metadata about the device, which is not _explicitly_ present in the zib (lot number, manufacture date, manufacturer, model number), although the information will be encoded in the ProductID if an UDI is used. As a matter of fact, the Xt-EHR model seems to make the UDI encoded information explicit.

The scope of the Xt-EHR model seems to be limited to concrete devices, that are actually used or have been used by patients. The zib also recognizes futures uses of devices, or classes of devices that don't need to be tracked individually (e.g. bandages). For this reason, Xt-EHR regards the identifier of a device as required, while the zib regards it optional. The concept in the zib can be made required in the use cases where it is used.

Regarding the product type, the zib is more constrained in terminology binding than Xt-EHR. The zib value set will be valid in Xt-EHR, but the other way around might be problematic, especially regarding negations in the IPS/EPS.

Some of the (optional) metadata in the DeviceUse model is not present in zib MedicalDevice, but still present in the zib layer due to zib RegistrationData (recorded, source) or by convention (subject). There is some other data present in Xt-EHR which is optional and does not seem to pose fundamental problems. The exception might be status, which Xt-EHR explicitly defines but which is fundamentally absent from the zibs.

On the other hand, the zib defines (optional) metadata which is not present in the Xt-EHR model. This also doesn't seem to be problematic, although it should be investigated if this data is or should be present in one of the other models (e.g. the healthcare provider could be part of the procedure rather than the DeviceUse). 


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
|                                            | EHDSDeviceUse.device       |            | EHDSDevice      |             | 1..1          |
| MedicalDevice.EndDate                      | EHDSDeviceUse.endDate      | TS         | dateTime        | 0..1        | 0..1          |
|                                            | EHDSDeviceUse.identifier   |            | Identifier      |             | 0..*          |
| MedicalDevice.StartDate                    | EHDSDeviceUse.implantDate  | TS         | dateTime        | 0..1        | 0..1          |
| MedicalDevice.Comment                      | EHDSDeviceUse.note         | ST         | string          | 0..1        | 0..*          |
| MedicalDevice.Indication::Diagnosis        | EHDSDeviceUse.reason       |            |                 | 0..*        |               |
|                                            |                            |            | EHDSCondition   |             | 0..*          |
|                                            | EHDSDeviceUse.recorded     |            | dateTime        |             | 0..1          |
|                                            | EHDSDeviceUse.source       |            |                 |             |               |
|                                            |                            |            | EHDSPatient     |             | 0..1          |
|                                            | EHDSDeviceUse.status       |            | CodeableConcept |             | 0..1          |
|                                            | EHDSDeviceUse.subject      |            | EHDSPatient     |             | 1..1          |
| MedicalDevice.HealthProfessional           |                            |            |                 | 0..1        |               |
| MedicalDevice.Location::HealthcareProvider |                            |            |                 | 0..1        |               |
| MedicalDevice.ProductDescription           |                            | ST         |                 | 0..1        |               |



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
| definition_xtehr | C.12 - EHDS refined base model for Device information |
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
✅ scope matches


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
| short_xtehr | C.12.4 - Expiry date |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments
Expiry date _can_ be implicitly present in the zib when ProductID is a UDI, but the concept is not discretely defined.


## EHDSDevice.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDevice.identifier |
| zib | MedicalDevice.Product.ProductID |
| alias_zib | NL: ProductID |
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
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | ST |

### Comments
The identifier is required in Xt-EHR, while it is optional in the zib. This makes sense from a scoping perspective. In Xt-EHR (at least patient summary and discharge report use cases), the model is about devices that are in use or have been in use by the patient, in which case there is a concrete identifiable device. The zib has a broader scope: devices that are needed or requested, or a general type of device like bandages. For these use cases, an identifier is not present yet or irrelevant. If the zib is used in a context of patient summary or discharge report, the use of identifier could be made mandatory there.

There is also an incompatibility the other way around: the zib recognizes at most 1 identifier, while Xt-EHR recognizes 0..* identifiers.

The identifier oftentimes is required an UDI, in which case the identifier carries more than just identifying information, but also lot number, production date and expiry date. This is recognized both by the zib and by the eHN guidelines. So some of the structured data which is made explicit by Xt-EHR might actually be present in the zib because of the UDI.

However, neither zib nor Xt-EHR _requires_ the identifier to be an UDI. Other identifiers are in scope as well.


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
| short_xtehr | C.12.5 - Lot number |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
Lot number _can_ be implicitly present in the zib when ProductID is a UDI, but the concept is not discretely defined.

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
| short_xtehr | C.12.3 - Manufacture date |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments
Manufacture date _can_ be implicitly present in the zib when ProductID is a UDI, but the concept is not discretely defined.

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
| short_xtehr | C.12.2 - Manufacturer |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
Manufacturer _can_ be implicitly present in the zib when ProductID is a UDI, but the concept is not discretely defined.


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
| short_xtehr | C.12.8 - Model number |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
Model number _can_ be implicitly present in the zib when ProductID is a UDI, but the concept is not discretely defined.


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
| short_xtehr | C.12.7 - Name |
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
| short_xtehr | C.12.11 - Note |
| stereotype_zib |  |
| type_xtehr | Narrative |
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
| short_xtehr | C.12.6 - Serial number |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
Serial number _can_ be implicitly present in the zib when ProductID is a UDI, but the concept is not discretely defined.


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
| short_xtehr | C.12.10 - Type |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
There is partial overlap here, but also a potential conflict:

1. The zib _requires_ the type to be SNOMED (physical objects and objects in the implantaten-refset only (which overlap)) or a local code that specifies "no hearing aid" or "no visual aid".
2. Xt-EHR has only a preference, of SNOMED or EMDN. So it's much more liberal.

Also note that in the IPS/EPS, negation is added to the value set, which is possible because there is no strong binding on the Xt-EHR level. However, the zib disallows this usage because of the _required_ binding.


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
| short_xtehr | C.12.9 - Version |
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
| definition_xtehr | EHDS refined base model for Device Use |
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
On the zib level, the device and its use are one model, while in Xt-EHR there are two.

Note: in FHIR the distinction between device and its use is also made.


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
| definition_zib | Patient\92s anatomical location of the medical device used. |
| definitioncode_zib | SNOMED CT: 363698007 Finding site |
| id_xtehr | EHDSDeviceUse.bodySite |
| id_zib | NL-CM:10.1.15 |
| name_zib | AnatomicalLocation |
| path_xtehr | EHDSDeviceUse.bodySite |
| path_zib | MedicalDevice.AnatomicalLocation |
| short_xtehr | Anatomical location of the device. May include laterality. |
| stereotype_zib | data,reference |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
On the Xt-EHR level, there is no preference for coding of the body site. For the zib, coding is restricted to SNOMED or ICD-O-3 only.

In addition, the zib recognizes laterality as an (optional) distinct concept (next to pre-coordinated codes), while Xt-EHR doesn't recognize this, or at least doesn't specify this.


## EHDSDeviceUse.device

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.device |
| zib |  |
| alias_zib |  |
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
| short_xtehr | The details of the device used. |
| stereotype_zib |  |
| type_xtehr | EHDSDevice |
| type_zib |  |

### Comments
This is inlined in the zib.


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
| definition_xtehr | Date when the device was explanted from the patient or the external device was no longer in use; likewise when the device is planned to be explanted. |
| definition_zib | The end date of the last use or explant of the medical device. A \91vague\92 date, such as only the year, is permitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.endDate |
| id_zib | NL-CM:10.1.14 |
| name_zib | EndDate |
| path_xtehr | EHDSDeviceUse.endDate |
| path_zib | MedicalDevice.EndDate |
| short_xtehr | Date when the device was explanted from the patient or the external device was no longer in use; likewise when the device is planned to be explanted. |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
✅ these concepts match.


## EHDSDeviceUse.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.identifier |
| zib |  |
| alias_zib |  |
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
| short_xtehr | An identifier for this statement. |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSDeviceUse.implantDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.implantDate |
| zib | MedicalDevice.StartDate |
| alias_zib | NL: BeginDatum |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Date when procedure was performed. |
| definition_zib | The start date of the first use or implant of the medical device. A \91vague\92 date, such as only the year, is permitted. |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.implantDate |
| id_zib | NL-CM:10.1.11 |
| name_zib | StartDate |
| path_xtehr | EHDSDeviceUse.implantDate |
| path_zib | MedicalDevice.StartDate |
| short_xtehr | Date when procedure was performed. |
| stereotype_zib | data |
| type_xtehr | dateTime |
| type_zib | TS |

### Comments
✅ these concepts match.


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
There's a conceptual match, but a cardinality mismatch. The Xt-EHR model is also more elaborate as it is of the Narrative data type, compared to simple string for the zib.


## EHDSDeviceUse.reason

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.reason |
| zib | MedicalDevice.Indication::Diagnosis |
| alias_zib | NL: Indicatie::Diagnose |
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
| stereotype_zib | context,reference |
| type_xtehr |  |
| type_zib |  |

### Comments
The reason in Xt-EHR can be a Condition, Observation or Procedure. In the zib it is more limited to Diagnosis, which _probably_ aligns with Condition.


## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Reason or justification for the use of the device. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSDeviceUse.reason[x] |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSDeviceUse.reason[x] |
| path_zib |  |
| short_xtehr | Reason or justification for the use of the device. |
| stereotype_zib |  |
| type_xtehr | EHDSCondition |
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
| short_xtehr | Date and time at which the statement was made/recorded. |
| stereotype_zib |  |
| type_xtehr | dateTime |
| type_zib |  |

### Comments
✅ This concept matches zib RegistrationData.RegistrationDateTime.


## EHDSDeviceUse.source

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.source |
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
✅ This concept matches zib RegistrationData.InformationSource.


## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
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



## EHDSDeviceUse.status

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.status |
| zib |  |
| alias_zib |  |
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
| short_xtehr | Current status of the Device Usage. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSDeviceUse.subject

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDeviceUse.subject |
| zib |  |
| alias_zib |  |
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
| short_xtehr | The patient using the device. |
| stereotype_zib |  |
| type_xtehr | EHDSPatient |
| type_zib |  |

### Comments
Implicit present in the zib.


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
