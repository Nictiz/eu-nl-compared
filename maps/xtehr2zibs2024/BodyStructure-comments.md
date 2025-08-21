# BodyStructure as of 2025-06-17

## Actions

Er is al een analyse gedaan op anatomische locatie bij het zibcemtrum

- zib issue: XtEHR BodyStructure model meenemen bij verdere ontwikkeling zib. Overwegen .locationQualifier en .morpholoy over te nemen.

## Overall Discussion

### Partial zib vs. stand-alone Xt-EHR model

Zib AnatomicalLocation is the universal way to describe anatomical locations in all zibs. It is a partial zib, meaning that it is meant to become part of the zib model where it is used.

This contrasts with the Xt-EHR model, which describes a model that can be instantiated independently. For this reason, it defines (the possibility to add) an identifier, allowing re-use across different models. It should be noted though that the Xt-EHR model is not the only way to describe anatomical locations in the Xt-EHR model. At least the Xt-EHR Condition model allows for a simple coded value as well.

What the result is of these different approaches, will depend on the concrete implementation in FHIR.

## Interpretation of the Xt-EHR model
The Xt-EHR model lacks terminology bindings, which makes it hard to compare with the zib; however, it is clear that the Xt-EHR model is directly modelled on the FHIR BodyStructure resource, so we'll use this as a proxy to interpret the meaning of the different components.

It should be noted that the BodyStructure model seems immature at this moment, because of the lack of proper meaning and the overlap of the laterality and locationQualifier elements.

## Differences and compatibility
The zib models an anatomical location as a location with a laterality, both as coded values. Both concepts are optional; the laterality may be irrelevant or pre-coordinated in the location code, and the location may be irrelevant in the context of the larger dataset (e.g. the location is redundant in a description of a cataract).

Just like the zib, the Xt-EHR model recognizes a location and a laterality (both coded, both optional), but in addition it recognizes a more generic coded locationQualifier, which (at least in the examples) also has laterality in scope. (Note that this deviates from the FHIR resource, which only recognizes locationQualifier, which has laterality in scope).

In contrast to the zib, the Xt-EHR model allows for a free text description instead of, or in addition to, the coded form.

In addition, it allows for defining the _kind_ of body structure. Although no formal constraint exists in the FHIR resource, the description makes it clear that it should be used in combination with the location, so I assume that this is the case for the Xt-EHR model as well.

Because of the lack of terminology in the Xt-EHR model and the use alignment of the two main elements from the zib, a valid instance of the zib is guaranteed to be a valid instance of the Xt-EHR model.

This is not true the other way around

* The Xt-EHR instance might use a code system not recognized by the zib
* The Xt-EHR instance might use a free text description instead of coded information
* The Xt-EHR instance might carry important information in free text in addition to the coded information, which cannot be interpreted by the zib.
* The Xt-EHR instance might define laterality information using the locationQualifier element instead of the location element



| zib                           | xtehr                               | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:------------------------------|:------------------------------------|:-----------|:----------------|:------------|:--------------|
| AnatomicalLocation            | EHDSBodyStructure                   |            |                 |             | 0..*          |
|                               | EHDSBodyStructure.description       |            | string          |             | 0..1          |
|                               | EHDSBodyStructure.identifier        |            | Identifier      |             | 0..*          |
| AnatomicalLocation.Laterality | EHDSBodyStructure.laterality        | CD         | CodeableConcept | 0..1        | 0..1          |
| AnatomicalLocation.Location   | EHDSBodyStructure.location          | CD         | CodeableConcept | 0..1        | 0..1          |
|                               | EHDSBodyStructure.locationQualifier |            | CodeableConcept |             | 0..*          |
|                               | EHDSBodyStructure.morphology        |            | CodeableConcept |             | 0..1          |



## EHDSBodyStructure

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure |
| zib | AnatomicalLocation |
| alias_zib | NL: AnatomischeLocatie |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | EHDS refined base model for Body structure |
| definition_zib | Root concept of the AnatomicalLocation partial information model. This root concept contains all data elements of the AnatomicalLocation partial information model. |
| definitioncode_zib | SNOMED CT: 123037004 Body structure |
| id_xtehr | EHDSBodyStructure |
| id_zib | NL-CM:20.7.1 |
| name_zib | AnatomicalLocation |
| path_xtehr | EHDSBodyStructure |
| path_zib | AnatomicalLocation |
| short_xtehr | Body structure model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSBodyStructure.description

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure.description |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Textual description of the body structure |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSBodyStructure.description |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSBodyStructure.description |
| path_zib |  |
| short_xtehr | Textual description of the body structure |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments



## EHDSBodyStructure.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure.identifier |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Identifier for this instance of the anatomical structure. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSBodyStructure.identifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSBodyStructure.identifier |
| path_zib |  |
| short_xtehr | Identifier for this instance of the anatomical structure. |
| stereotype_zib |  |
| type_xtehr | Identifier |
| type_zib |  |

### Comments



## EHDSBodyStructure.laterality

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure.laterality |
| zib | AnatomicalLocation.Laterality |
| alias_zib | NL: Lateraliteit |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Body structure laterality (e.g. left, right). |
| definition_zib | Laterality adds information about the body side to the anatomic location, e.g. left. |
| definitioncode_zib | SNOMED CT: 272741003 Laterality |
| id_xtehr | EHDSBodyStructure.laterality |
| id_zib | NL-CM:20.7.3 |
| name_zib | Laterality |
| path_xtehr | EHDSBodyStructure.laterality |
| path_zib | AnatomicalLocation.Laterality |
| short_xtehr | Body structure laterality (e.g. left, right). |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSBodyStructure.location

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure.location |
| zib | AnatomicalLocation.Location |
| alias_zib | NL: Locatie |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Body site |
| definition_zib | Location on/in the body. |
| definitioncode_zib | SNOMED CT: 363698007 Finding site |
| id_xtehr | EHDSBodyStructure.location |
| id_zib | NL-CM:20.7.4 |
| name_zib | Location |
| path_xtehr | EHDSBodyStructure.location |
| path_zib | AnatomicalLocation.Location |
| short_xtehr | Body site |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments



## EHDSBodyStructure.locationQualifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure.locationQualifier |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | Additional qualifier of the body structure (e.g. upper, lower, left side). |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSBodyStructure.locationQualifier |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSBodyStructure.locationQualifier |
| path_zib |  |
| short_xtehr | Additional qualifier of the body structure (e.g. upper, lower, left side). |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments



## EHDSBodyStructure.morphology

### Table

| attribute | value |
|---|---|
| xtehr | EHDSBodyStructure.morphology |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'SNOMED CT'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | The kind of structure being represented by the body structure at BodyStructure.location. This can define both normal and abnormal morphologies. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSBodyStructure.morphology |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSBodyStructure.morphology |
| path_zib |  |
| short_xtehr | The kind of structure being represented by the body structure at BodyStructure.location. This can define both normal and abnormal morphologies. |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments

