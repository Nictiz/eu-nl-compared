# HumanName as of 2025-05-28

## Actions

### Structuur achternaam

De XtEHR heeft family (niet opgedeeld), de zib alleen opgedeeld. De zib erkent eigenlijk alleen NL namen volgens GBA.

- zib issue: de zib moet buitenlandse achternamen ondersteunen (voor cross border, vluchteling, toerist)

### Voornamen

Hier heeft de zib 1 string met voornamen, XtEHR heeft given 0..*. De zib onderscheidt given, initials, roepnaam

- zib issue: moet buitenlandse voornamen ondersteunen (voor cross border, vluchteling, toerist). Dit gaat met name om niet-officiele voornamen.

### Titels

De XtEHR heeft 0..* pre- en suffix, de zib heeft alleen titulatuur.

- issue zib: wat te doen als je niet weet of het voor of achter de naam moet (b.v. buitenlandse titels)

### Volledige 

De XtEHR heeft volledige naam (1 string voor de hele naam als delen niet bekend zijn). Dit laten we even liggen, is bekend zib issue.

## Overall Discussion
The Xt-EHR model and the zib have significant granularity differences, leading to incompatibilities on all parts comprising the name:

* Family name: one or more strings in Xt-EHR, without restrictions on how to accommodate the parts of a family name, while the zib exactly defines the four parts a family name can consist of plus an indicator on how to combine them.
* Given names: one or more strings in Xt-EHR, with different types of name possible, while the zib exactly defines either all official names, concatenated to a single string, or one nickname.
* Prefix and suffix: as many as needed in the Xt-EHR, while the zib defines at most one string for all noble and scientific titles.
* Full rendered name: the Xt-EHR model provides a fully rendered name instead of or in addition to the structured name parts, while the zib disallows this.


| zib                                             | xtehr                | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:------------------------------------------------|:---------------------|:-----------|:----------------|:------------|:--------------|
| NameInformation                                 | EHDSHumanName        |            |                 |             | 0..*          |
|                                                 | EHDSHumanName.family |            | string          |             | 0..*          |
| NameInformation.FirstNames                      | EHDSHumanName.given  | ST         | string          | 0..1        | 0..*          |
| NameInformation.GivenName                       | EHDSHumanName.given  | ST         | string          | 0..1        | 0..*          |
| NameInformation.Titles                          | EHDSHumanName.prefix | ST         | string          | 0..1        | 0..*          |
| NameInformation.Titles                          | EHDSHumanName.suffix | ST         | string          | 0..1        | 0..*          |
|                                                 | EHDSHumanName.text   |            | string          |             | 0..1          |
|                                                 | EHDSHumanName.use    |            | CodeableConcept |             | 0..1          |
| NameInformation.GivenName                       |                      | ST         |                 | 0..1        |               |
| NameInformation.Initials                        |                      | ST         |                 | 0..1        |               |
| NameInformation.LastNamePartner                 |                      |            |                 | 0..1        |               |
| NameInformation.LastNamePartner.PartnerLastName |                      | ST         |                 | 1           |               |
| NameInformation.LastNamePartner.PartnerPrefix   |                      | ST         |                 | 0..1        |               |
| NameInformation.NameUsage                       |                      | CD         |                 | 0..1        |               |
| NameInformation.Surname                         |                      |            |                 | 0..1        |               |
| NameInformation.Surname.LastName                |                      | ST         |                 | 1           |               |
| NameInformation.Surname.Prefix                  |                      | ST         |                 | 0..1        |               |



## EHDSHumanName

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName |
| zib | NameInformation |
| alias_zib | NL: Naamgegevens |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | C.27 - EHDS refined base model for Human name |
| definition_zib | Root concept of the NameInformation partial information model. This root concept contains all data elements of the NameInformation partial information model. |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName |
| id_zib | NL-CM:20.4.1 |
| name_zib | NameInformation |
| path_xtehr | EHDSHumanName |
| path_zib | NameInformation |
| short_xtehr | Human name model |
| stereotype_zib | rootconcept |
| type_xtehr |  |
| type_zib |  |

### Comments



## EHDSHumanName.family

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.family |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib |  |
| definition_xtehr | The family name/surname/last name of the patient. This field can contain more than one  element or multiple fields could be present. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.family |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSHumanName.family |
| path_zib |  |
| short_xtehr | C.27.3 - Family |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
The Xt-EHR model uses a straightforward concept for representing family names, using one or more family names. Guidance is how to use this is missing, but one can assume that if more than one name is present, they should be concatenated in the given order. One can also assume that it is up to the user on how to split the family name over multiple family elements.

The zib on the other hand has very strict rules about family names (which only seem to be relevant to patients); they must always be built from prefix + name, prefix + name from the partner, and a coded indication on how to combine them.

A family name according to the zib _could_ be encoded using multiple Xt-EHR family elements, but information on what parts are from the partner etc. would be lost.

A family name according to the Xt-EHR cannot be interpreted by the zib.


## EHDSHumanName.given

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.given |
| zib | NameInformation.FirstNames |
| alias_zib | NL: Voornamen |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | The given name/first name  (also known as forename or first name). |
| definition_zib | The person�s official first names. |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.given |
| id_zib | NL-CM:20.4.4 |
| name_zib | FirstNames |
| path_xtehr | EHDSHumanName.given |
| path_zib | NameInformation.FirstNames |
| short_xtehr | C.27.4 - Given |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
The zib restricts the "given names" two to kinds: 

* a _full_ list of official first names concept, encoded in a single string. This may be represented as such (the FirstNames concept), as a string of initials (Initials concept), or both.
* a single nickname (GivenName concept)

The Xt-EHR model is more liberal, different kinds of given names could be encoded (as indicated by the "use" concept), and there is no requirement that the list of official names is complete. Although specific guidance is missing, one can assume that a list of names is represented by a sequence of given elements rather than that they are concatenated in a single string.

A zib FirstNames string could probably not be interpreted by the Xt-EHR model, as it would require to have distinct names. Official names encoded using the Xt-EHR model cannot be interpreted by the zib for the same reason. In addition, from Xt-EHR there is no guarantee that the list is complete or has all names written out.

A zib GivenName could be interpreted in Xt-EHR context (as a single "given" in combination with "use" set to something indicating a nickname/common name). A nickname encoded using the Xt-EHR model could be interpreted by the zib, but only if there's just one.

## EHDSHumanName.given

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.given |
| zib | NameInformation.GivenName |
| alias_zib | NL: Roepnaam |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | The given name/first name  (also known as forename or first name). |
| definition_zib | The name normally used to address the person. |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.given |
| id_zib | NL-CM:20.4.6 |
| name_zib | GivenName |
| path_xtehr | EHDSHumanName.given |
| path_zib | NameInformation.GivenName |
| short_xtehr | C.27.4 - Given |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
See the remark above.


## EHDSHumanName.prefix

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.prefix |
| zib | NameInformation.Titles |
| alias_zib | NL: Titels |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Name parts that come before the name. Prefixes appear in the correct order for presenting the name. |
| definition_zib | Noble and scientific titles. These can assist in formulating oral and formal addresing titles. |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.prefix |
| id_zib | NL-CM:20.4.12 |
| name_zib | Titles |
| path_xtehr | EHDSHumanName.prefix |
| path_zib | NameInformation.Titles |
| short_xtehr | C.27.5 - Prefix |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Not really sure about this one, but a prefix might include noble and scientific titles, which overlaps with the zib Titles concept. However, the zib doesn't specify whether the title are a prefix or a suffix. There is also just a single string possible in the zib.


## EHDSHumanName.suffix

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.suffix |
| zib | NameInformation.Titles |
| alias_zib | NL: Titels |
| binding_xtehr |  |
| card._xtehr | 0..* |
| card._zib | 0..1 |
| definition_xtehr | Name parts that come after the name. Suffixes appear in the correct order for presenting the name. |
| definition_zib | Noble and scientific titles. These can assist in formulating oral and formal addresing titles. |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.suffix |
| id_zib | NL-CM:20.4.12 |
| name_zib | Titles |
| path_xtehr | EHDSHumanName.suffix |
| path_zib | NameInformation.Titles |
| short_xtehr | C.27.6 - Suffix |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
Not really sure about this one, but a suffux might include noble and scientific titles, which overlaps with the zib Titles concept. However, the zib doesn't specify whether the title are a prefix or a suffix. There is also just a single string possible in the zib.


## EHDSHumanName.text

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.text |
| zib |  |
| alias_zib |  |
| binding_xtehr |  |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Specifies the entire name as it should be displayed e.g. on an application UI. This may be provided instead of or as well as the specific parts. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.text |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSHumanName.text |
| path_zib |  |
| short_xtehr | C.27.2 - Text |
| stereotype_zib |  |
| type_xtehr | string |
| type_zib |  |

### Comments
This concept overlaps with the other fields, which goes against zib design principles.


## EHDSHumanName.use

### Table

| attribute | value |
|---|---|
| xtehr | EHDSHumanName.use |
| zib |  |
| alias_zib |  |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:NameUse'} |
| card._xtehr | 0..1 |
| card._zib |  |
| definition_xtehr | Identifies the purpose for this name. |
| definition_zib |  |
| definitioncode_zib |  |
| id_xtehr | EHDSHumanName.use |
| id_zib |  |
| name_zib |  |
| path_xtehr | EHDSHumanName.use |
| path_zib |  |
| short_xtehr | C.27.1 - Use |
| stereotype_zib |  |
| type_xtehr | CodeableConcept |
| type_zib |  |

### Comments
Not present in the zib as the zib already is explicit about two uses: official names and nickname. The Xt-EHR model might have other uses as well.


## zib: NameInformation.GivenName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.GivenName |
| alias_zib | NL: Roepnaam |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The name normally used to address the person. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.6 |
| name_zib | GivenName |
| path_xtehr |  |
| path_zib | NameInformation.GivenName |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the remark above.


## zib: NameInformation.Initials

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.Initials |
| alias_zib | NL: Initialen |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | The person�s initials. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.5 |
| name_zib | Initials |
| path_xtehr |  |
| path_zib | NameInformation.Initials |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the remark above.


## zib: NameInformation.LastNamePartner

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.LastNamePartner |
| alias_zib | NL: GeslachtsnaamPartner |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Container of the LastNamePartner concept. This container contains all data elements of the LastNamePartner concept. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.3 |
| name_zib | LastNamePartner |
| path_xtehr |  |
| path_zib | NameInformation.LastNamePartner |
| short_xtehr |  |
| stereotype_zib | container |
| type_xtehr |  |
| type_zib |  |

### Comments
See the remark above.


## zib: NameInformation.LastNamePartner.PartnerLastName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.LastNamePartner.PartnerLastName |
| alias_zib | NL: AchternaamPartner |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | Partner�s official last name. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.8 |
| name_zib | PartnerLastName |
| path_xtehr |  |
| path_zib | NameInformation.LastNamePartner.PartnerLastName |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the remark above.


## zib: NameInformation.LastNamePartner.PartnerPrefix

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.LastNamePartner.PartnerPrefix |
| alias_zib | NL: VoorvoegselsPartner |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Prefix to the partner�s last name. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.9 |
| name_zib | PartnerPrefix |
| path_xtehr |  |
| path_zib | NameInformation.LastNamePartner.PartnerPrefix |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the remark above.


## zib: NameInformation.NameUsage

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.NameUsage |
| alias_zib | NL: Naamgebruik |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | This concept indicates the last name or order of last names with which the person is to be addressed. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.7 |
| name_zib | NameUsage |
| path_xtehr |  |
| path_zib | NameInformation.NameUsage |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | CD |

### Comments
See the remark above.


## zib: NameInformation.Surname

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.Surname |
| alias_zib | NL: Geslachtsnaam |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Container of the Surname concept. This container contains all data elements of the Surname concept. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.2 |
| name_zib | Surname |
| path_xtehr |  |
| path_zib | NameInformation.Surname |
| short_xtehr |  |
| stereotype_zib | container |
| type_xtehr |  |
| type_zib |  |

### Comments
See the remark above.


## zib: NameInformation.Surname.LastName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.Surname.LastName |
| alias_zib | NL: Achternaam |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 1 |
| definition_xtehr |  |
| definition_zib | The person�s official last name |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.10 |
| name_zib | LastName |
| path_xtehr |  |
| path_zib | NameInformation.Surname.LastName |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the remark above.


## zib: NameInformation.Surname.Prefix

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | NameInformation.Surname.Prefix |
| alias_zib | NL: Voorvoegsels |
| binding_xtehr |  |
| card._xtehr |  |
| card._zib | 0..1 |
| definition_xtehr |  |
| definition_zib | Prefix to the person�s own last name. |
| definitioncode_zib |  |
| id_xtehr |  |
| id_zib | NL-CM:20.4.11 |
| name_zib | Prefix |
| path_xtehr |  |
| path_zib | NameInformation.Surname.Prefix |
| short_xtehr |  |
| stereotype_zib | data |
| type_xtehr |  |
| type_zib | ST |

### Comments
See the remark above.
