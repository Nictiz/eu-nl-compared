# BodyStructure

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

