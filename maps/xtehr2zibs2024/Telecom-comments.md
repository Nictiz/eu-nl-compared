# Telecom as of 2025-05-28

This isn't a generated file, as the zib and the Xt-EHR model operate at a different level of granularity and one-to-one concept mapping is hard to make. However, a useful mapping can still be made. On a high level, zib instances can largely be accommodated by the Xt-EHR model, although some subtleties are missing. However, Xt-EHR model might contain codes not understood by the zib (web address and other information and old addresses).

The Xt-EHR model is based on the FHIR [_ContactPoint_](https://www.hl7.org/fhir/R4/datatypes.html#ContactPoint) data type. At this moment, there is a _preferred_ binding to the FHIR value sets used in this data type. The mapping with the zib hinges on these value sets, which are required in the FHIR implementation. So for the moment let's assume these value set bindings to be _required_.

_ContactPoint_ is a data type to accommodate e-mail, phone based, and online contact information, in a generic way. The zib ContactInformation provides a more focussed model for e-mail and phone based contact information respectively. These two types of contact information "fit in" the more general _ContactPoint_ data type:

## EmailAddresses
The "EmailAddresses" container of the zib can be modelled using Xt-EHR Telecom where "type" is fixed to _e-mail_. The values in EmailSoortCodelijst are a subset of the value set on the "use" concept.

An instance of zib ConctactInformation representing an e-mail address is compatibel with the Xt-EHR model. However, an Xt-EHR model representing in e-mail address might contain codes for the "use" concept not understood by the zib.

## TelephoneNumbers
The "TelephoneNumbers" container of the zib can largely be modelled using Xt-EHR model, but the "use" and "system" concepts of the Xt-EHR model and the "TelecomType" and "NumberType" concepts of the zib differ in their modelling:

| zib TelecomType | zib NumberType    | Xt-EHR use  | Xt-EHR type | Note                     |
| --------------- | ----------------- | ----------- | ----------- | ------------------------ |
| Land line       | Primary home      | home        | phone       |                          |
| Land line       | Temporary Address | temp        | phone       |                          |
| Land line       | Work place        | work        | phone       |                          |
| Fax             | Primary home      | home        | fax         |                          |
| Fax             | Temporary Address | temp        | fax         |                          |
| Fax             | Work place        | work        | fax         |                          |
| Mobile phone    | Primary home      | mobile      | phone       | Alternative: home/phone  |
| Mobile phone    | Temporary Address | mobile      | phone       | Alternative: temp/phone  |
| Mobile phone    | Work place        | mobile      | phone       | Alternative: work/phone  |
| Pager           | Primary home      | home        | pager       |                          |
| Pager           | Temporary Address | temp        | pager       |                          |
| Pager           | Work place        | work        | pager       |                          |

The mismatch is mainly in mobile phones; the Xt-EHR "use" concept is about _where_ the device is, while the zib TelecomType is about the _type_ of device. There is no clean mapping to be made without some data loss.

In addition, an Xt-EHR instance might contain codes for the "use" concept not understood by the zib.
