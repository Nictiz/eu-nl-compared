# Medication
## Overall discussion
The most striking difference between the zib model and the Xt-EHR model is the Xt-EHR concept EHDSMedication.item, unknown in the zib. This is to represent an item in a combination pack, which the zib cannot represent. The identifying codes in the Xt-EHR model are on package level. The zib can thus only represent a package containing one single item.  
The Xt-EHR model has EHDSMedication.device of which the zib has no equivalent. It is an administration device included in the product.  
The Xt-EHR model has EHDSMedication.Characteristic of which the zib has no equivalent but a free text description. It is a key-value pair and can represent any type of characteristic of the product.  

| zib                                                                                   | xtehr                                                                | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:--------------------------------------------------------------------------------------|:---------------------------------------------------------------------|:-----------|:----------------|:------------|:--------------|
| PharmaceuticalProduct                                                                 | EHDSMedication                                                       |            |                 |             | 0..*          |
|                                                                                       | EHDSMedication.batch                                                 |            | Base            |             | 0..1          |
|                                                                                       | EHDSMedication.batch.expirationDate                                  |            | dateTime        |             | 0..1          |
| PharmaceuticalProduct.ProductSpecifications.Batch/lotNumber                           | EHDSMedication.batch.lotNumber                                       | ST         | string          | 0..1        | 0..1          |
|                                                                                       | EHDSMedication.characteristic                                        |            | Base            |             | 0..*          |
|                                                                                       | EHDSMedication.characteristic.type                                   |            | CodeableConcept |             | 1..1          |
|                                                                                       | EHDSMedication.characteristic.value[x]                               |            | boolean         |             | 0..1          |
|                                                                                       | EHDSMedication.classification                                        |            | CodeableConcept |             | 0..*          |
|                                                                                       | EHDSMedication.device                                                |            | Base            |             | 0..*          |
|                                                                                       | EHDSMedication.device.deviceQuantity                                 |            | Quantity        |             | 1..1          |
|                                                                                       | EHDSMedication.device.device[x]                                      |            | CodeableConcept |             | 1..1          |
|                                                                                       | EHDSMedication.doseForm                                              |            | CodeableConcept |             | 0..1          |
| PharmaceuticalProduct.MedicationCode                                                  | EHDSMedication.identifyingCode[x]                                    | CD         | CodeableConcept | 0..1        | 0..*          |
|                                                                                       | EHDSMedication.item                                                  |            | Base            |             | 0..*          |
|                                                                                       | EHDSMedication.item.amount                                           |            | Quantity        |             | 0..1          |
|                                                                                       | EHDSMedication.item.containedQuantity                                |            | Ratio           |             | 0..1          |
| PharmaceuticalProduct.ProductSpecifications.PharmaceuticalForm                        | EHDSMedication.item.doseForm                                         | CD         | CodeableConcept | 0..1        | 0..1          |
| PharmaceuticalProduct.ProductSpecifications.Ingredient                                | EHDSMedication.item.ingredient                                       |            | Base            | 0..*        | 1..*          |
|                                                                                       | EHDSMedication.item.ingredient.isActive                              |            | boolean         |             | 0..1          |
|                                                                                       | EHDSMedication.item.ingredient.strengthInfo                          |            | Base            |             | 0..1          |
|                                                                                       | EHDSMedication.item.ingredient.strengthInfo.basisOfStrengthSubstance |            | CodeableConcept |             | 0..1          |
| PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration                  | EHDSMedication.item.ingredient.strengthInfo.strength                 |            | Ratio           | 0..1        | 1..1          |
| PharmaceuticalProduct.ProductSpecifications.Ingredient.SubstanceCode                  | EHDSMedication.item.ingredient.substance                             | CD         | CodeableConcept | 0..1        | 1..1          |
|                                                                                       | EHDSMedication.item.packageType                                      |            | CodeableConcept |             | 0..1          |
|                                                                                       | EHDSMedication.item.unitOfPresentation                               |            | CodeableConcept |             | 0..1          |
|                                                                                       | EHDSMedication.marketingAuthorisationHolder                          |            | Base            |             | 0..1          |
|                                                                                       | EHDSMedication.marketingAuthorisationHolder.organisationIdentifier   |            |                 |             |               |
|                                                                                       | EHDSMedication.marketingAuthorisationHolder.organisationName         |            |                 |             |               |
|                                                                                       |                                                                      |            | Identifier      |             | 0..*          |
|                                                                                       |                                                                      |            | string          |             | 0..1          |
|                                                                                       | EHDSMedication.packSize                                              |            | Quantity        |             | 0..*          |
| PharmaceuticalProduct.ProductSpecifications.Medication                                | EHDSMedication.productName                                           | ST         | string          | 0..1        | 0..1          |
| PharmaceuticalProduct.ProductSpecifications                                           |                                                                      |            |                 | 0..1        |               |
| PharmaceuticalProduct.ProductSpecifications.Description                               |                                                                      | ST         |                 | 0..1        |               |
| PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.IngredientAmount |                                                                      | PQ         |                 | 0..1        |               |
| PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.ProductAmount    |                                                                      | PQ         |                 | 0..1        |               |
| PharmaceuticalProduct.ProductSpecifications.SerieNumber                               |                                                                      | ST         |                 | 0..1        |               |







## EHDSMedication

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication |
| zib | PharmaceuticalProduct |
| alias_zib | NL: FarmaceutischProduct |
| card._xtehr | 0..* |
| definition_xtehr | Logical model for prescribed/dispensed medication. The model is shared by statements, requests, dispensations, and treatment lines. Each of those may have different restrictions in FHIR profile. Model is suitable for generic/virtual medications as well as branded/real products. |
| definition_zib | Root concept of the PharmaceuticalProduct partial information model. This root concept contains all data elements of the PharmaceuticalProduct partial information model. |
| id_xtehr | EHDSMedication |
| id_zib | NL-CM:9.7.19926 |
| name_zib | PharmaceuticalProduct |
| path_xtehr | EHDSMedication |
| path_zib | PharmaceuticalProduct |
| short_xtehr | Medication model |
| stereotype_zib | rootconcept |

### Comments



## EHDSMedication.batch

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.batch |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Batch information of a medicinal product. Typically recorded during dispense or administration, rarely known or relevant for a prescription/request. |
| id_xtehr | EHDSMedication.batch |
| path_xtehr | EHDSMedication.batch |
| short_xtehr | Batch information of a medicinal product. Typically recorded during dispense or administration, rarely known or relevant for a prescription/request. |
| type_xtehr | Base |

### Comments
The container is to hold .lotNumber and .expirationDate. Since the zib has only one concept characterizing the batch, the zib has no container. 



## EHDSMedication.batch.expirationDate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.batch.expirationDate |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Batch expiration date of the medicinal product. |
| id_xtehr | EHDSMedication.batch.expirationDate |
| path_xtehr | EHDSMedication.batch.expirationDate |
| short_xtehr | Batch expiration date of the medicinal product. |
| type_xtehr | dateTime |

### Comments
The zib doesn't have this concept.



## EHDSMedication.batch.lotNumber

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.batch.lotNumber |
| zib | PharmaceuticalProduct.ProductSpecifications.Batch/lotNumber |
| alias_zib | NL: Batch/lotNummer |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Batch identifier of the medicinal product |
| definition_zib | The batch/lot number provides a unique identification of the origin of information such as the production batch or machine number. The number is constructed according to the GS1 standard AI(10).( https://www.gs1.nl/sectorafspraken-over-standaarden/unieke-identificatie-en-productdata-gezondheidszorg/gs1-barcodes-2#application-identifiers-ais ) |
| id_xtehr | EHDSMedication.batch.lotNumber |
| id_zib | NL-CM:9.7.22279 |
| name_zib | Batch/lotNumber |
| path_xtehr | EHDSMedication.batch.lotNumber |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Batch/lotNumber |
| short_xtehr | Batch identifier of the medicinal product |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Match.



## EHDSMedication.characteristic

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.characteristic |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Other features of the product |
| id_xtehr | EHDSMedication.characteristic |
| path_xtehr | EHDSMedication.characteristic |
| short_xtehr | Other features of the product |
| type_xtehr | Base |

### Comments
The zib has no equivalent. The zib has .ProductSpecification.Description, with which relevant properties of the composition and preparation method can be represented as free text.  


## EHDSMedication.characteristic.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.characteristic.type |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | A code expressing the type of characteristic |
| id_xtehr | EHDSMedication.characteristic.type |
| path_xtehr | EHDSMedication.characteristic.type |
| short_xtehr | A code expressing the type of characteristic |
| type_xtehr | CodeableConcept |

### Comments
See .characteristic



## EHDSMedication.characteristic.value[x]


### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.characteristic.value[x] |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Description of the characteristic |
| id_xtehr | EHDSMedication.characteristic.value[x] |
| path_xtehr | EHDSMedication.characteristic.value[x] |
| short_xtehr | Description of the characteristic |
| type_xtehr | boolean |

### Comments
See .characteristic


## EHDSMedication.classification

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.classification |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'WHO ATC'} |
| card._xtehr | 0..* |
| definition_xtehr | Classification (e.g. ATC; narcotic/psychotropic; orphan drug; etc.) |
| id_xtehr | EHDSMedication.classification |
| path_xtehr | EHDSMedication.classification |
| short_xtehr | Classification (e.g. ATC; narcotic/psychotropic; orphan drug; etc.) |
| type_xtehr | CodeableConcept |

### Comments
The zib has no separate classification element. However, PharmaceuticalProduct.MedicationCode can be populated with medication classes from classification systems like SNOMED and ATC. 



## EHDSMedication.device

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.device |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Administration device included in the product |
| id_xtehr | EHDSMedication.device |
| path_xtehr | EHDSMedication.device |
| short_xtehr | Administration device included in the product |
| type_xtehr | Base |

### Comments
The zib has no concept that represents an administration device.



## EHDSMedication.device.deviceQuantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.device.deviceQuantity |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Number of such devices |
| id_xtehr | EHDSMedication.device.deviceQuantity |
| path_xtehr | EHDSMedication.device.deviceQuantity |
| short_xtehr | Number of such devices |
| type_xtehr | Quantity |

### Comments
See EHDSMedication.device.


## EHDSMedication.device.device[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.device.device[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Device coded |
| id_xtehr | EHDSMedication.device.device[x] |
| path_xtehr | EHDSMedication.device.device[x] |
| short_xtehr | Device coded |
| type_xtehr | CodeableConcept |

### Comments
See EHDSMedication.device.



## EHDSMedication.doseForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.doseForm |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'EDQM Standard Terms'} |
| card._xtehr | 0..1 |
| definition_xtehr | Dose form(s) on a product level. Dose form for a single package item is defined below. |
| id_xtehr | EHDSMedication.doseForm |
| path_xtehr | EHDSMedication.doseForm |
| short_xtehr | Dose form(s) on a product level. Dose form for a single package item is defined below. |
| type_xtehr | CodeableConcept |

### Comments
The zib has no distinction between dose form on a package level and on item level. See EHDSMedication.item.doseForm for the mapping on item level. 



## EHDSMedication.identifyingCode[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.identifyingCode[x] |
| zib | PharmaceuticalProduct.MedicationCode |
| alias_zib | NL: ProductCode |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Identifier or code for the product (virtual product, branded product or package). If several identifiers are specified, they shall not have conflicting meanings or very different granularities. |
| definition_zib | Coding medication in the Netherlands is done on the basis of the G standard (issued by Z index), which is filled under the direction of KNMP. <br>The coded medication can be expressed as:<br>-  Global Trade Item Number (GTIN) <br>-  Z index number (ZI number) <br>-  Trade product code (HPK) <br>-  Prescription code (PRK) <br>-  Generic product code (GPK) <br>-  Anatomic Therapeutic Classification code (ATC) <br>-  SNOMED CT code<br>The GTIN enables identification of the product including its origin with a barcode.<br>The ZI number represents the trade product and the package size. <br>The HPK is the code for the trade product (with the brand name) as used per dose/per time the medication is taken (1 pill, 1 puff, 1ml).<br>The PRK contains als GPK information supplemented with information needed to prescribe the right product. This level is intended to facilitate generic prescription of drugs. <br>The GPK defines the pharmaceutical characteristics of a product: ingredients, strengths, units, pharmaceutical form and route of administration. <br>The Substance Name Code (SNK) is the (active) compound. <br>Further information about the G Standaard levels see https://www.z-index.nl .<br>So-called 90.000.000 numbers are used in local IT systems. These numbers shall not be used for external communication. In this case only the description (not the code) may be included. This is in accordance with national agreements (Nictiz Standard).<br><br><br>SNOMED CT can be used as an alternative coding of a pharmaceutical product, it is used, for example, to more generically describe vaccinations from the National Vaccination Programme based on the combination of substances (e.g. DKTP vaccine). For vaccines registered in the past, a code from the G-standard is not always present, but it is recommended to record it for current processing. In addition, the SNOMED CT code can be registered as an alternative for the same product. |
| id_xtehr | EHDSMedication.identifyingCode[x] |
| id_zib | NL-CM:9.7.19927 |
| name_zib | MedicationCode |
| path_xtehr | EHDSMedication.identifyingCode[x] |
| path_zib | PharmaceuticalProduct.MedicationCode |
| short_xtehr | Identifier or code for the product (virtual product, branded product or package). If several identifiers are specified, they shall not have conflicting meanings or very different granularities. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
EHDSMedictaion.identifyingCode can be either a CodeableConcept or an Identifier, while the zib specifies this to be a CodeableConcept. There is a cardinality mismatch. 
Note that the Xt-EHR allows for specification of both an Identifying code and a classification. The zib does not.



## EHDSMedication.item

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | A medication item. For combination packs, this can be manufactured items with each item having its own dose form and ingredients+strengths defined |
| id_xtehr | EHDSMedication.item |
| path_xtehr | EHDSMedication.item |
| short_xtehr | A medication item. For combination packs, this can be manufactured items with each item having its own dose form and ingredients+strengths defined |
| type_xtehr | Base |

### Comments
The zib cannot represent a product consisting of more than one item.


## EHDSMedication.item.amount

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.amount |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'UCUM for units of measure. EDQM Standard Terms for units of presentation.'} |
| card._xtehr | 0..1 |
| definition_xtehr | Number of such manufactured items in this product (5 vials) |
| id_xtehr | EHDSMedication.item.amount |
| path_xtehr | EHDSMedication.item.amount |
| short_xtehr | Number of such manufactured items in this product (5 vials) |
| type_xtehr | Quantity |

### Comments
The zib cannot represent a product consisting of more than one item.



## EHDSMedication.item.containedQuantity

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.containedQuantity |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Manufactured item quantity for liquids (3ml / 1 vial) |
| id_xtehr | EHDSMedication.item.containedQuantity |
| path_xtehr | EHDSMedication.item.containedQuantity |
| short_xtehr | Manufactured item quantity for liquids (3ml / 1 vial) |
| type_xtehr | Ratio |


### Comments
EHDSMediation.item.containedQuantity does not match the zib .ProductAmount concept. It's datatype is a ratio, so this can be 10ml / 2 vials. Moreover, the zib doesn't model items within a package.   



## EHDSMedication.item.doseForm

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.doseForm |
| zib | PharmaceuticalProduct.ProductSpecifications.PharmaceuticalForm |
| alias_zib | NL: FarmaceutischeVorm |
| binding_xtehr | {'strength': 'preferred', 'description': 'EDQM Standard Terms'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Dose form |
| definition_zib | The pharmaceutical form indicates the form of the medication. Examples include: tablet, suppository, infusion liquid, ointment. If the product has a GPK code in the G standard, the form will be known in the G standard. For products without a code (free text, preparation by the pharmacy), the means of administration can be entered. |
| id_xtehr | EHDSMedication.item.doseForm |
| id_zib | NL-CM:9.7.19931 |
| name_zib | PharmaceuticalForm |
| path_xtehr | EHDSMedication.item.doseForm |
| path_zib | PharmaceuticalProduct.ProductSpecifications.PharmaceuticalForm |
| short_xtehr | Dose form |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Exact match. Note that the Xt-EHR has also a dosage form on package level.



## EHDSMedication.item.ingredient

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.ingredient |
| zib | PharmaceuticalProduct.ProductSpecifications.Ingredient |
| alias_zib | NL: Ingredient |
| card._xtehr | 1..* |
| card._zib | 0..* |
| definition_xtehr | Ingredients |
| definition_zib | Container of the Ingredient concept. This container contains all data elements of the Ingredient concept. <br>A product contains one or more active substances and excipients. These are usually determined by the product code. For medication prepared or compounded by the local pharmacy, each ingredient must be entered separately. <br><br>The active substances play an important role, as they: <br>a) determine the pharmacotherapeutic effect of the medication and <br>b) serve as the basis for the indication of the strength of the medication (e.g. 200 mg). |
| id_xtehr | EHDSMedication.item.ingredient |
| id_zib | NL-CM:9.7.19932 |
| name_zib | Ingredient |
| path_xtehr | EHDSMedication.item.ingredient |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Ingredient |
| short_xtehr | Ingredients |
| stereotype_zib | container |
| type_xtehr | Base |

### Comments
Exact match.




## EHDSMedication.item.ingredient.isActive

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.ingredient.isActive |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Marks if the ingredient is considered an active ingredient. Typically excipients are not needed, so by default active ingredients are expected. |
| id_xtehr | EHDSMedication.item.ingredient.isActive |
| path_xtehr | EHDSMedication.item.ingredient.isActive |
| short_xtehr | Marks if the ingredient is considered an active ingredient. Typically excipients are not needed, so by default active ingredients are expected. |
| type_xtehr | boolean |

### Comments
There's no equivalent in the zib.



## EHDSMedication.item.ingredient.strengthInfo

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.ingredient.strengthInfo |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Strength of the product - amount of substance per unit |
| id_xtehr | EHDSMedication.item.ingredient.strengthInfo |
| path_xtehr | EHDSMedication.item.ingredient.strengthInfo |
| short_xtehr | Strength of the product - amount of substance per unit |
| type_xtehr | Base |

### Comments
This container is actually present in the zib, but the zib container has been mapped to .strenghInfo.strength.



## EHDSMedication.item.ingredient.strengthInfo.basisOfStrengthSubstance

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.ingredient.strengthInfo.basisOfStrengthSubstance |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'EMA SPOR SMS'} |
| card._xtehr | 0..1 |
| definition_xtehr | Substance that the strength refers to, in case it's different from the main substance |
| id_xtehr | EHDSMedication.item.ingredient.strengthInfo.basisOfStrengthSubstance |
| path_xtehr | EHDSMedication.item.ingredient.strengthInfo.basisOfStrengthSubstance |
| short_xtehr | Substance that the strength refers to, in case it's different from the main substance |
| type_xtehr | CodeableConcept |

### Comments
This concept is absent in the zib.



## EHDSMedication.item.ingredient.strengthInfo.strength

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.ingredient.strengthInfo.strength |
| zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration |
| alias_zib | NL: Sterkte |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Concentration or presentation strength, e.g 100mg/1ml or 500mg per 1 tablet |
| definition_zib | The relative amount of this ingredient in this product.  <br>Calculation of Concentration = Ingredient Amount ÷ Product Amount. <br> <br>This could be a concentration if the medication is dissolved in liquid, for example. |
| id_xtehr | EHDSMedication.item.ingredient.strengthInfo.strength |
| id_zib | NL-CM:9.7.19933 |
| name_zib | Concentration |
| path_xtehr | EHDSMedication.item.ingredient.strengthInfo.strength |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration |
| short_xtehr | Concentration or presentation strength, e.g 100mg/1ml or 500mg per 1 tablet |
| stereotype_zib | container |
| type_xtehr | Ratio |

### Comments
The Xt-EHR concept .strength (datatype Ratio) maps to the zib concept .Concentration (type Container) as it is the intention of .Concentration to provide the numerator and the denominator for the calculation of the strength. The Xt-EHR concept can also be used to represent the amount per tablet (which is not really a ratio), as per example in the definition. It is not clear if the .Concentration container can be used for tablets.    


## EHDSMedication.item.ingredient.substance

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.ingredient.substance |
| zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.SubstanceCode |
| alias_zib | NL: IngredientCode |
| binding_xtehr | {'strength': 'preferred', 'description': 'EMA SPOR SMS'} |
| card._xtehr | 1..1 |
| card._zib | 0..1 |
| definition_xtehr | Substance |
| definition_zib | Active substance or excipient. <br>Here, the same codes can be used as for the ProductCode (for dilutions and compounds in particular), but now, the SSK and SNK codes can also be used to indicate a substance (to list ingredients of local products prepared by the pharmacy).<br>-  GTIN International Article Number <br>-  Z-index number (ZI-number) <br>-  Trade product code (HPK) <br>-  Prescription code (PRK) <br>-  Generic product code (GPK) <br>-  Anatomic therapeutic classification (ATC) <br>-  Substance name code (SNK) <br>-  Substance name code with route of administration (SKK) |
| id_xtehr | EHDSMedication.item.ingredient.substance |
| id_zib | NL-CM:9.7.19934 |
| name_zib | SubstanceCode |
| path_xtehr | EHDSMedication.item.ingredient.substance |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.SubstanceCode |
| short_xtehr | Substance |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
These concepts match.


## EHDSMedication.item.packageType

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.packageType |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'EDQM Standard Terms for packaging.'} |
| card._xtehr | 0..1 |
| definition_xtehr | Type of package of the medication item |
| id_xtehr | EHDSMedication.item.packageType |
| path_xtehr | EHDSMedication.item.packageType |
| short_xtehr | Type of package of the medication item |
| type_xtehr | CodeableConcept |

### Comments
This concept is absent in the zib.


## EHDSMedication.item.unitOfPresentation

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.item.unitOfPresentation |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'EDQM Standard Terms'} |
| card._xtehr | 0..1 |
| definition_xtehr | Unit of presentation for the manufactured item (tablet, vial, tube). Typically, the smallest countable object in the package. |
| id_xtehr | EHDSMedication.item.unitOfPresentation |
| path_xtehr | EHDSMedication.item.unitOfPresentation |
| short_xtehr | Unit of presentation for the manufactured item (tablet, vial, tube). Typically, the smallest countable object in the package. |
| type_xtehr | CodeableConcept |

### Comments
This concept is absent in the zib.


## EHDSMedication.marketingAuthorisationHolder

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.marketingAuthorisationHolder |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Marketing authorisation holder or manufacturer of the medicinal product. Relevant for identifying the exact product. |
| id_xtehr | EHDSMedication.marketingAuthorisationHolder |
| path_xtehr | EHDSMedication.marketingAuthorisationHolder |
| short_xtehr | Marketing authorisation holder or manufacturer of the medicinal product. Relevant for identifying the exact product. |
| type_xtehr | Base |

### Comments
This concept is absent in the zib.


## EHDSMedication.marketingAuthorisationHolder.organisationIdentifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.marketingAuthorisationHolder.organisationIdentifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Identifier of the organisation and/or its physical location |
| id_xtehr | EHDSMedication.marketingAuthorisationHolder.organisationIdentifier |
| path_xtehr | EHDSMedication.marketingAuthorisationHolder.organisationIdentifier |
| short_xtehr | Identifier of the organisation and/or its physical location |
| type_xtehr | Identifier |

### Comments
This concept is absent in the zib.



## EHDSMedication.marketingAuthorisationHolder.organisationName

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.marketingAuthorisationHolder.organisationName |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Name of the organisation holding the authorisation for marketing/mahufacturing |
| id_xtehr | EHDSMedication.marketingAuthorisationHolder.organisationName |
| path_xtehr | EHDSMedication.marketingAuthorisationHolder.organisationName |
| short_xtehr | Name of the organisation holding the authorisation for marketing/mahufacturing |
| type_xtehr | string |

### Comments
This concept is absent in the zib.


## EHDSMedication.packSize

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.packSize |
| zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'UCUM for units of measure. EDQM Standard Terms for units of presentation.'} |
| card._xtehr | 0..* |
| definition_xtehr | Overall amount of product in one package (100ml; 20 tablets; 1 creme & 6 pessaries) |
| id_xtehr | EHDSMedication.packSize |
| path_xtehr | EHDSMedication.packSize |
| short_xtehr | Overall amount of product in one package (100ml; 20 tablets; 1 creme & 6 pessaries) |
| type_xtehr | Quantity |

### Comments
This concept is absent in the zib. The zib has .Concentration.ProductAmount, but this seems dedicated to computation of the concentration of liquid ingredients, and not to represent the number of, for example, tablets.


## EHDSMedication.productName

### Table

| attribute | value |
|---|---|
| xtehr | EHDSMedication.productName |
| zib | PharmaceuticalProduct.ProductSpecifications.Medication |
| alias_zib | NL: ProductNaam |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Name of the product (full name, invented name, other). When the product has different names, the appropriate one for the context should be used. Translations of names can be provided. |
| definition_zib | For medication which has no code, enter the complete name of the pharmaceutical product here. |
| id_xtehr | EHDSMedication.productName |
| id_zib | NL-CM:9.7.19929 |
| name_zib | Medication |
| path_xtehr | EHDSMedication.productName |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Medication |
| short_xtehr | Name of the product (full name, invented name, other). When the product has different names, the appropriate one for the context should be used. Translations of names can be provided. |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
These concepts match, although the use of the concept in the zib is restricted to medication which has no code.



## zib: PharmaceuticalProduct.ProductSpecifications

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | PharmaceuticalProduct.ProductSpecifications |
| alias_zib | NL: ProductSpecificatie |
| card._zib | 0..1 |
| definition_zib | Container of the ProductSpecifications concept. This container contains all data elements of the ProductSpecifications concept. <br>Product specifications are required if the product code is not sufficient to ascertain the active substances and strength. |
| id_zib | NL-CM:9.7.19928 |
| name_zib | ProductSpecifications |
| path_zib | PharmaceuticalProduct.ProductSpecifications |
| stereotype_zib | container |

### Comments
This container is absent in the Xt-EHR model.



## zib: PharmaceuticalProduct.ProductSpecifications.Description

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | PharmaceuticalProduct.ProductSpecifications.Description |
| alias_zib | NL: Omschrijving |
| card._zib | 0..1 |
| definition_zib | A textual description of the type of medication (including relevant properties of the composition and preparation method if possible), which is only used if no coded indication from the G Standard is available (historical data regarding magistral preparation which has been entered as free text instead of entering the substance codes). |
| id_zib | NL-CM:9.7.19784 |
| name_zib | Description |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Description |
| stereotype_zib | data |
| type_zib | ST |

### Comments
This concept is absent in the Xt-EHR model. However, relevant properties of the composition and preparation method can be represented in .characteristic of the XT-EHR model.


## zib: PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.IngredientAmount

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.IngredientAmount |
| alias_zib | NL: IngredientHoeveelheid |
| card._zib | 0..1 |
| definition_zib | The amount and unit of this ingredient. This is the numerator for the calculation of the concentration. The unit should be selected from the G Standard (Table 902). |
| id_zib | NL-CM:9.7.22277 |
| name_zib | IngredientAmount |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.IngredientAmount |
| stereotype_zib | data |
| type_zib | PQ |

### Comments
This concept is absent in the Xt-EHR model. In the Xt-EHR model, .strength is present, which is the ratio of the ingredient amount and the product amount.

## zib: PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.ProductAmount

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.ProductAmount |
| alias_zib | NL: ProductHoeveelheid |
| card._zib | 0..1 |
| definition_zib | Amount of the product. This is the denominator for the calculation of the concentration. Optionally a translation to NHG table Gebruiksvoorschriften (Table 25) is also allowed. |
| id_zib | NL-CM:9.7.22278 |
| name_zib | ProductAmount |
| path_zib | PharmaceuticalProduct.ProductSpecifications.Ingredient.Concentration.ProductAmount |
| stereotype_zib | data |
| type_zib | PQ |

### Comments


## zib: PharmaceuticalProduct.ProductSpecifications.SerieNumber

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | PharmaceuticalProduct.ProductSpecifications.SerieNumber |
| alias_zib | NL: SerieNummer |
| card._zib | 0..1 |
| definition_zib | The serial number uniquely identifies the source of information of the dose itself. The number is constructed according to the GS1 standard AI(21). (https://www.gs1.nl/sectorafspraken-over-standaarden/unieke-identificatie-en-productdata-gezondheidszorg/gs1-barcodes-2#application-identifiers-ais) |
| id_zib | NL-CM:9.7.22280 |
| name_zib | SerieNumber |
| path_zib | PharmaceuticalProduct.ProductSpecifications.SerieNumber |
| stereotype_zib | data |
| type_zib | ST |

### Comments
There is no distinct serial number of type String in the Xt-EHR model. The Xt-EHR model has .identifyingCode (0..*) but this is either a CodeableConcept or an identifier. 

