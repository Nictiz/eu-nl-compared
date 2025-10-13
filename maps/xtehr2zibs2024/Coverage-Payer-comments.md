# Coverage

| zib                                             | xtehr                             | type_zib   | type_xtehr       | card._zib   | card._xtehr   |
|:------------------------------------------------|:----------------------------------|:-----------|:-----------------|:------------|:--------------|
| Payer                                           | EHDSCoverage                      |            |                  |             | 0..*          |
|                                                 | EHDSCoverage.identifier           |            | Identifier       |             | 0..*          |
| Payer.InsuranceCompany.Insurance.InsuranceType  | EHDSCoverage.type                 | CD         | CodeableConcept  | 1           | 0..1          |
|                                                 | EHDSCoverage.patient              |            | EHDSPatient      |             | 1..1          |
| Payer                                           | EHDSCoverage.payor                |            | Base             |             | 1..*          |
|                                                 | EHDSCoverage.payor.payorEntity[x] |            | EHDSOrganisation |             | 1..1          |
| Payer.InsuranceCompany.InsurantNumber           | EHDSCoverage.payor.subscriberId   | ST         | Identifier       | 1           | 0..1          |
|                                                 |                                   |            |                  |             |               |
| Payer.PayerPerson                               |                                   |            |                  | (0..1)      |               |
| Payer.PayerPerson.PayerName                     |                                   | ST         |                  | 0..1        |               |
| Payer.PayerPerson.BankInformation               |                                   |            |                  | 0..*        |               |
| Payer.PayerPerson.BankInformation.BankName      |                                   | ST         |                  | 0..1        |               |
| Payer.PayerPerson.BankInformation.BankCode      |                                   | ST         |                  | 0..1        |               |
| Payer.PayerPerson.BankInformation.AccountNumber |                                   | ST         |                  | 1           |               |
| Payer.InsuranceCompany                          |                                   |            |                  | (0..1)      |               |
| Payer.InsuranceCompany.Insurance                |                                   |            |                  | 1..*        |               |
| Payer.InsuranceCompany.OrganizationName         |                                   | ST         |                  | 0..1        |               |
| Payer.InsuranceCompany.IdentificationNumber     |                                   | II         |                  | 0..1        |               |
| Payer.InsuranceCompany.Insurance.StartDateTime  |                                   | TS         |                  | 1           |               |
| Payer.InsuranceCompany.Insurance.EndDateTime    |                                   | TS         |                  | 1           |               |
| Payer.AddressInformation                        |                                   |            |                  | 0..*        |               |
| Payer.ContactInformation                        |                                   |            |                  | 0..1        |               |



## EHDSCoverage

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage |
| zib | Payer |
| alias_zib | NL: Betaler |
| card._xtehr | 0..* |
| definition_xtehr | EHDS refined base model for Coverage |
| definition_zib | Root concept of the Payer information model. This root concept contains all data elements of the Payer information model. |
| id_xtehr | EHDSCoverage |
| id_zib | NL-CM:1.1.1 |
| name_zib | Payer |
| path_xtehr | EHDSCoverage |
| path_zib | Payer |
| short_xtehr | Coverage model |
| stereotype_zib | rootconcept |

### Comments



## EHDSCoverage.identifier

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage.identifier |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Business Identifier for the coverage |
| id_xtehr | EHDSCoverage.identifier |
| path_xtehr | EHDSCoverage.identifier |
| short_xtehr | Business Identifier for the coverage |
| type_xtehr | Identifier |

### Comments
Komt mogelijk overeen met zib element: RegistrationData.IdentificationNumber.




## EHDSCoverage.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage.type |
| zib | Payer.InsuranceCompany.Insurance.InsuranceType |
| alias_zib | NL: Verzekeringssoort |
| binding_xtehr | {'strength': 'preferred', 'description': 'hl7:coverage-selfpay, hl7:v3-ActCoverageTypeCode'} |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Type of coverage: social program, medical plan, accident coverage (workers compensation, auto), group health or payment by an individual or organisation. |
| definition_zib | Type of insurance policy. Codes as returned in the Check for Right to Insurance |
| id_xtehr | EHDSCoverage.type |
| id_zib | NL-CM:1.1.15 |
| name_zib | InsuranceType |
| path_xtehr | EHDSCoverage.type |
| path_zib | Payer.InsuranceCompany.Insurance.InsuranceType |
| short_xtehr | Type of coverage: social program, medical plan, accident coverage (workers compensation, auto), group health or payment by an individual or organisation. |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Waarden van de value set overlappen weinig. Binding is preferred. Dit kan per land flink verschillen.




## EHDSCoverage.patient

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage.patient |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Patient who benefits from the insurance coverage when products and/or services are provided. |
| id_xtehr | EHDSCoverage.patient |
| path_xtehr | EHDSCoverage.patient |
| short_xtehr | Patient who benefits from the insurance coverage when products and/or services are provided. |
| type_xtehr | EHDSPatient |

### Comments
In de zibs zal hiervoor de zib Patient gebruikt moeten worden.




## EHDSCoverage.payor

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage.payor |
| zib | Payer |
| alias_zib | NL: Betaler |
| card._xtehr | 1..* |
| definition_xtehr | Payor including both insurance and non-insurance agreements, such as patient-pay agreements. |
| definition_zib | Root concept of the Payer information model. This root concept contains all data elements of the Payer information model. |
| id_xtehr | EHDSCoverage.payor |
| id_zib | NL-CM:1.1.1 |
| name_zib | Payer |
| path_xtehr | EHDSCoverage.payor |
| path_zib | Payer |
| short_xtehr | Payor including both insurance and non-insurance agreements, such as patient-pay agreements. |
| stereotype_zib | rootconcept |
| type_xtehr | Base |

### Comments
Ws verkeerd gespeld in de zib, want EHDS noemt het 'payor'. 'Payor' heeft in het Engels de voorkeur in de context van de zorg.



## EHDSCoverage.payor.payorEntity[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage.payor.payorEntity[x] |
| zib |  |
| card._xtehr | 1..1 |
| definition_xtehr | Payor entity |
| id_xtehr | EHDSCoverage.payor.payorEntity[x] |
| path_xtehr | EHDSCoverage.payor.payorEntity[x] |
| short_xtehr | Payor entity |
| type_xtehr | EHDSOrganisation |

### Comments
Volgens de specs van het LM (hier niet zichtbaar) kan dit een EHDSOrganisation of een EHDSPatient zijn. In de laatste vorm komt dit overeen met zib Patient. 
!!Betaler als persoon hoeft niet de patiënt zelf te zijn: kan bijv. ouder zijn van minderjarige patiënt. Advies voor EHDS: Verwijs naar Persoon óf verwijs naar zowel Patient als RelatedPerson.




## EHDSCoverage.payor.subscriberId

### Table

| attribute | value |
|---|---|
| xtehr | EHDSCoverage.payor.subscriberId |
| zib | Payer.InsuranceCompany.InsurantNumber |
| alias_zib | NL: VerzekerdeNummer |
| card._xtehr | 0..1 |
| card._zib | 1 |
| definition_xtehr | Number or code under which the insured person is registered at the insurance provider. |
| definition_zib | Number under which the insured person is registered at the insurance company <br>This item maps the ‘Identification number of the card’ on EHIC field 8 |
| id_xtehr | EHDSCoverage.payor.subscriberId |
| id_zib | NL-CM:1.1.6 |
| name_zib | InsurantNumber |
| path_xtehr | EHDSCoverage.payor.subscriberId |
| path_zib | Payer.InsuranceCompany.InsurantNumber |
| short_xtehr | Number or code under which the insured person is registered at the insurance provider. |
| stereotype_zib | data |
| type_xtehr | Identifier |
| type_zib | ST |

### Comments



## zib: nan

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib |  |

### Comments



## zib: Payer.PayerPerson

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.PayerPerson |
| alias_zib | NL: BetalerPersoon |
| card._zib | (0..1) |
| definition_zib | Container of the PayerPerson concept. This container contains all data elements of the PayerPerson concept.<br>In this a person is a natural person or a juridical person, such as an organization, municipality, etc. |
| id_zib | NL-CM:1.1.2 |
| name_zib | PayerPerson |
| path_zib | Payer.PayerPerson |
| stereotype_zib | container |

### Comments
EHDSCoverage verwijst alleen naar Patient als persoon en dat is onvoldoende. De betaler hoeft niet de patiënt zelf te zijn.




## zib: Payer.PayerPerson.PayerName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.PayerPerson.PayerName |
| alias_zib | NL: BetalerNaam |
| card._zib | 0..1 |
| definition_zib | Full name of the paying person or organization (legal entity). |
| id_zib | NL-CM:1.1.5 |
| name_zib | PayerName |
| path_zib | Payer.PayerPerson.PayerName |
| stereotype_zib | data |
| type_zib | ST |

### Comments
Als het de patiënt betreft, komt dit overeen met EHDSPatient.name.




## zib: Payer.PayerPerson.BankInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.PayerPerson.BankInformation |
| alias_zib | NL: Bankgegevens |
| card._zib | 0..* |
| definition_zib | Container of the BankInformation concept. This container contains all data elements of the BankInformation concept. |
| id_zib | NL-CM:1.1.4 |
| name_zib | BankInformation |
| path_zib | Payer.PayerPerson.BankInformation |
| stereotype_zib | container |

### Comments



## zib: Payer.PayerPerson.BankInformation.BankName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.PayerPerson.BankInformation.BankName |
| alias_zib | NL: BankNaam |
| card._zib | 0..1 |
| definition_zib | Name of the financial organization. |
| id_zib | NL-CM:1.1.9 |
| name_zib | BankName |
| path_zib | Payer.PayerPerson.BankInformation.BankName |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Payer.PayerPerson.BankInformation.BankCode

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.PayerPerson.BankInformation.BankCode |
| alias_zib | NL: Bankcode |
| card._zib | 0..1 |
| definition_zib | Code indicating the bank and branch. For European countries, this is the organization’s BIC or SWIFT code. |
| id_zib | NL-CM:1.1.10 |
| name_zib | BankCode |
| path_zib | Payer.PayerPerson.BankInformation.BankCode |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Payer.PayerPerson.BankInformation.AccountNumber

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.PayerPerson.BankInformation.AccountNumber |
| alias_zib | NL: Rekeningnummer |
| card._zib | 1 |
| definition_zib | The payer’s bank account number at the listed organization. For European countries, this is the IBAN. |
| id_zib | NL-CM:1.1.11 |
| name_zib | AccountNumber |
| path_zib | Payer.PayerPerson.BankInformation.AccountNumber |
| stereotype_zib | data |
| type_zib | ST |

### Comments



## zib: Payer.InsuranceCompany

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.InsuranceCompany |
| alias_zib | NL: Verzekeraar |
| card._zib | (0..1) |
| definition_zib | Container of the InsuranceCompany concept. This container contains all data elements of the InsuranceCompany concept. |
| id_zib | NL-CM:1.1.3 |
| name_zib | InsuranceCompany |
| path_zib | Payer.InsuranceCompany |
| stereotype_zib | container |

### Comments
Wij hebben geen zib voor 'Organisatie'.




## zib: Payer.InsuranceCompany.Insurance

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.InsuranceCompany.Insurance |
| alias_zib | NL: Verzekering |
| card._zib | 1..* |
| definition_zib | Container of the Insurance concept. This container contains all data elements of the Insurance concept. |
| id_zib | NL-CM:1.1.8 |
| name_zib | Insurance |
| path_zib | Payer.InsuranceCompany.Insurance |
| stereotype_zib | container |

### Comments



## zib: Payer.InsuranceCompany.OrganizationName

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.InsuranceCompany.OrganizationName |
| alias_zib | NL: OrganisatieNaam |
| card._zib | 0..1 |
| definition_zib | Full, official name of the healthcare insurance company. If the UZOVI number is entered as an identification number, this will be the name as listed in the UZOVI register and the name which is returned in the Check for Right to Insurance (COV). |
| id_zib | NL-CM:1.1.16 |
| name_zib | OrganizationName |
| path_zib | Payer.InsuranceCompany.OrganizationName |
| stereotype_zib | data |
| type_zib | ST |

### Comments
Komt overeen met EHDSOrganisation.Name.




## zib: Payer.InsuranceCompany.IdentificationNumber

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.InsuranceCompany.IdentificationNumber |
| alias_zib | NL: IdentificatieNummer |
| card._zib | 0..1 |
| definition_zib | Unique healthcare insurance company identification (the UZOVI number). |
| id_zib | NL-CM:1.1.7 |
| name_zib | IdentificationNumber |
| path_zib | Payer.InsuranceCompany.IdentificationNumber |
| stereotype_zib | data |
| type_zib | II |

### Comments
Lijkt overeen te komen met EHDSOrganisation.Identifier.




## zib: Payer.InsuranceCompany.Insurance.StartDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.InsuranceCompany.Insurance.StartDateTime |
| alias_zib | NL: BeginDatumTijd |
| card._zib | 1 |
| definition_zib | Date from which the insurance policy coverage applies. |
| id_zib | NL-CM:1.1.13 |
| name_zib | StartDateTime |
| path_zib | Payer.InsuranceCompany.Insurance.StartDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Payer.InsuranceCompany.Insurance.EndDateTime

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.InsuranceCompany.Insurance.EndDateTime |
| alias_zib | NL: EindDatumTijd |
| card._zib | 1 |
| definition_zib | Date until which the insurance policy coverage applies. <br>This item maps the ‘Expiry date’ on EHIC field 9. |
| id_zib | NL-CM:1.1.14 |
| name_zib | EndDateTime |
| path_zib | Payer.InsuranceCompany.Insurance.EndDateTime |
| stereotype_zib | data |
| type_zib | TS |

### Comments



## zib: Payer.AddressInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.AddressInformation |
| alias_zib | NL: Adresgegevens |
| card._zib | 0..* |
| definition_zib | The payer’s address information. |
| id_zib | NL-CM:1.1.17 |
| name_zib | AddressInformation |
| path_zib | Payer.AddressInformation |
| stereotype_zib | data,reference |

### Comments
Bij een organisatie komt het overeen met EHDSOrganisation.address.  
Bij een patiënt komt het overeen met EHDSPatient.address.  
EHDS heeft geen dataelement(en) op het niveau van 'Person'.



## zib: Payer.ContactInformation

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | Payer.ContactInformation |
| alias_zib | NL: Contactgegevens |
| card._zib | 0..1 |
| definition_zib | The payer’s telephone number and/or e-mail address. |
| id_zib | NL-CM:1.1.12 |
| name_zib | ContactInformation |
| path_zib | Payer.ContactInformation |
| stereotype_zib | data,reference |

### Comments
Bij een organisatie komt het overeen met EHDSOrganisation.telecom.  
Bij een patiënt komt het overeen met EHDSPatient.telecom.  
EHDS heeft geen dataelement(en) op het niveau van 'Person'.

