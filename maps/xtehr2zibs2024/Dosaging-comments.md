# Dosaging

## Overall discussion
The Xt-EHR model contains far more concepts to represent dosaging parameters for more complex dosaging schemes than the zib. The zib has RepeatesPeriodCyclicalSchedule to represent the repeated period in a cyclical schedule which the XT-EHR model has not, but it lacks the possibilities to represent the entire scheme for such a period.
Note that the compared version of the XT-EHR model has no bindings.

Concerns/issues with the EHDS model:
+ name and defnition of the .doseAndRate.rate[x] concept do not match
+ the way of specifying .repeat.frequency (in separate concepts .numberOfTimes and .period seems unusual)



## 

| zib                                                                                   | xtehr                                                 | type_zib   | type_xtehr      | card._zib   | card._xtehr   |
|:--------------------------------------------------------------------------------------|:------------------------------------------------------|:-----------|:----------------|:------------|:--------------|
| InstructionsForUse                                                                    | EHDSDosaging                                          |            |                 |             | 0..*          |
| InstructionsForUse.AdditionalInstructions                                             | EHDSDosaging.additionalInstruction                    | CD         | CodeableConcept | 0..*        | 0..*          |
|                                                                                       | EHDSDosaging.asNeeded                                 |            | boolean         |             | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.AsNeeded.Condition                       | EHDSDosaging.asNeededFor                              | CD         | CodeableConcept | 0..*        | 0..*          |
|                                                                                       | EHDSDosaging.bodySite                                 |            | CodeableConcept |             | 0..1          |
|                                                                                       | EHDSDosaging.doseAndRate                              |            | Base            |             | 0..*          |
| InstructionsForUse.DosingInstructions.Dosage.Dose::Range                              | EHDSDosaging.doseAndRate.dose[x]                      |            | Quantity        | 0..1        | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSpeed::Range                | EHDSDosaging.doseAndRate.rate[x]                      |            | Ratio           | 0..1        | 0..1          |
|                                                                                       | EHDSDosaging.doseAndRate.type                         |            | CodeableConcept |             | 0..1          |
|                                                                                       | EHDSDosaging.maxDose                                  |            | Base            |             | 0..*          |
|                                                                                       | EHDSDosaging.maxDose.maxDosePerAdministration         |            | Quantity        |             | 0..1          |
|                                                                                       | EHDSDosaging.maxDose.maxDosePerLifetime               |            | Quantity        |             | 0..1          |
|                                                                                       | EHDSDosaging.maxDose.maxDosePerPeriod                 |            | Ratio           |             | 0..*          |
|                                                                                       | EHDSDosaging.methodOfAdministration                   |            | CodeableConcept |             | 0..1          |
|                                                                                       | EHDSDosaging.patientInstruction                       |            | string          |             | 0..1          |
|                                                                                       | EHDSDosaging.renderedDescription                      |            | string          |             | 0..1          |
| InstructionsForUse.RouteOfAdministration                                              | EHDSDosaging.routeOfAdministration                    | CD         | CodeableConcept | 0..1        | 0..1          |
| InstructionsForUse.DosingInstructions.SequenceNumber                                  | EHDSDosaging.sequence                                 | INT        | integer         | 0..1        | 0..1          |
| InstructionsForUse.Description                                                        | EHDSDosaging.text                                     | ST         | string          | 0..1        | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule                    | EHDSDosaging.timing                                   |            | Base            | 0..1        | 0..1          |
|                                                                                       | EHDSDosaging.timing.code                              |            | CodeableConcept |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.event                             |            | dateTime        |             | 0..*          |
|                                                                                       | EHDSDosaging.timing.repeat                            |            | Base            |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.bounds                     |            | Base            |             | 0..1          |
| InstructionsForUse.DosingInstructions.DoseDuration                                    | EHDSDosaging.timing.repeat.bounds.duration            | PQ         | Quantity        | 0..1        | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.bounds.period              |            | Period          |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.bounds.range               |            | Range           |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.count                      |            | Base            |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.count.count                |            | integer         |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.count.countMax             |            | integer         |             | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.WeekDay            | EHDSDosaging.timing.repeat.dayOfWeek                  | CD         | CodeableConcept | 0..*        | 0..*          |
|                                                                                       | EHDSDosaging.timing.repeat.duration                   |            | Base            |             | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.DurationOfAdministration::TimeInterval   | EHDSDosaging.timing.repeat.duration.duration          |            | Quantity        | 0..1        | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.duration.durationMax       |            | Quantity        |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.eventTime                  |            | Base            |             | 0..*          |
|                                                                                       | EHDSDosaging.timing.repeat.eventTime.offset           |            | integer         |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.eventTime.when             |            | CodeableConcept |             | 0..*          |
|                                                                                       | EHDSDosaging.timing.repeat.frequency                  |            | Base            |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.frequency.maxNumberOfTimes |            | integer         |             | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Frequency::Range   | EHDSDosaging.timing.repeat.frequency.numberOfTimes    |            | integer         | 0..1        | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.frequency.period           |            | Quantity        |             | 0..1          |
|                                                                                       | EHDSDosaging.timing.repeat.frequency.periodMax        |            | Quantity        |             | 0..1          |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.AdministrationTime | EHDSDosaging.timing.repeat.timeOfDay                  | TS         | time            | 0..*        | 0..*          |
| InstructionsForUse.DosingInstructions                                                 |                                                       |            |                 | 0..*        |               |
| InstructionsForUse.DosingInstructions.Dosage                                          |                                                       |            |                 | 0..*        |               |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule                    |                                                       |            |                 | 0..1        |               |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Interval           |                                                       | PQ         |                 | 0..1        |               |
| InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.PartOfDay          |                                                       | CD         |                 | 0..*        |               |
| InstructionsForUse.DosingInstructions.Dosage.AsNeeded                                 |                                                       |            |                 | 0..1        |               |
| InstructionsForUse.DosingInstructions.Dosage.AsNeeded.MaximumDose                     |                                                       | PQ         |                 | 0..1        |               |
| InstructionsForUse.RepeatPeriodCyclicalSchedule                                       |                                                       | PQ         |                 | 0..1        |               |



## EHDSDosaging

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging |
| zib | InstructionsForUse |
| alias_zib | NL: GebruiksInstructie |
| card._xtehr | 0..* |
| definition_xtehr | Logical model for usage instructions for administring the requested product. Based on FHIR Dosage complex data type. When implemented, this model may be reduced significantly according to the specific use case. |
| definition_zib | Root concept of the InstructionsForUse partial information model. This root concept contains all data elements of the InstructionsForUse partial information model. |
| id_xtehr | EHDSDosaging |
| id_zib | NL-CM:9.12.22504 |
| name_zib | InstructionsForUse |
| path_xtehr | EHDSDosaging |
| path_zib | InstructionsForUse |
| short_xtehr | Dosaging model |
| stereotype_zib | rootconcept |

### Comments
The zib and the Xt-EHR model match 1 to 1.



## EHDSDosaging.additionalInstruction

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.additionalInstruction |
| zib | InstructionsForUse.AdditionalInstructions |
| alias_zib | NL: AanvullendeInstructies |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Coded instructions, e.g warnings to the patient, like 'may cause drowsiness' etc |
| definition_zib | The additional instructions contain extra information on the use of the current prescription.<br>This includes all instructions for use. The text can come from the original �paper" medication prescription, but can also be generated from the coded information. <br>This concept may contain more information than what is structurally coded in the information below, but may not conflict with it. <br>The instructions may not conflict with other components of the request for administration. <br>The instructions can also refer to an existing protocol. <br>The texts in the G-standard that can support this attribute are included in table 362 and are a copy of the texts from the general practitioner' standard 'NHG-tabel Gebruiksvoorschrift' which are included in the CIM. These texts can be used to structure this concept. |
| id_xtehr | EHDSDosaging.additionalInstruction |
| id_zib | NL-CM:9.12.19944 |
| name_zib | AdditionalInstructions |
| path_xtehr | EHDSDosaging.additionalInstruction |
| path_zib | InstructionsForUse.AdditionalInstructions |
| short_xtehr | Coded instructions, e.g warnings to the patient, like 'may cause drowsiness' etc |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
These concepts match. Note that in the zib, the concept is bound to NHG table 25. The NHG code is in fact a composition of a number of other concepts in the zib: frequency, duration, dosage per administration, additional information.



## EHDSDosaging.asNeeded

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.asNeeded |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Take as needed |
| id_xtehr | EHDSDosaging.asNeeded |
| path_xtehr | EHDSDosaging.asNeeded |
| short_xtehr | Take as needed |
| type_xtehr | boolean |

### Comments
This boolean is not present in the zib. This means that when using the zib, one can not prescribe "as needed" without specifying one ore more conditions and/or a maximum dose.  


## EHDSDosaging.asNeededFor

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.asNeededFor |
| zib | InstructionsForUse.DosingInstructions.Dosage.AsNeeded.Condition |
| alias_zib | NL: Criterium |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Take as needed for the coded reason |
| definition_zib | The condition for administering medication can be: <br>-  a physiological measurement value (plasma glucose concentration, body temperature, blood pressure);<br>-  a symptom or other circumstance (in the event of a headache, or itch).<br>Supplemental information from G-standard bst362 make up the list of values for coded entering of this concept. Also always include the textual description of that code. <br>Physiological measurement values or other conditions that do not occur in bst362 do not need to be coded. These can be expressed in free text in the Description concept. |
| id_xtehr | EHDSDosaging.asNeededFor |
| id_zib | NL-CM:9.12.19945 |
| name_zib | AsNeeded.Condition |
| path_xtehr | EHDSDosaging.asNeededFor |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AsNeeded.Condition |
| short_xtehr | Take as needed for the coded reason |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Exact match.


## EHDSDosaging.bodySite

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.bodySite |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Body site of administration |
| id_xtehr | EHDSDosaging.bodySite |
| path_xtehr | EHDSDosaging.bodySite |
| short_xtehr | Body site of administration |
| type_xtehr | CodeableConcept |

### Comments
There is no equivalent in the zib. 


## EHDSDosaging.doseAndRate

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.doseAndRate |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Amount of medication administered per one dose (= one timing) |
| id_xtehr | EHDSDosaging.doseAndRate |
| path_xtehr | EHDSDosaging.doseAndRate |
| short_xtehr | Amount of medication administered per one dose (= one timing) |
| type_xtehr | Base |

### Comments
This container is not present in the zib.



## EHDSDosaging.doseAndRate.dose[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.doseAndRate.dose[x] |
| zib | InstructionsForUse.DosingInstructions.Dosage.Dose::Range |
| alias_zib | NL: Keerdosis::Bereik |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Amount of medication per one dose. (1 tablet, 2-3 tablets, 20ml) |
| definition_zib | The dose indicates the amount/unit per administration. The unit can be any unit that can occur with this particular medicine. |
| id_xtehr | EHDSDosaging.doseAndRate.dose[x] |
| id_zib | NL-CM:9.12.19940 |
| name_zib | Dose::Range |
| path_xtehr | EHDSDosaging.doseAndRate.dose[x] |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.Dose::Range |
| short_xtehr | Amount of medication per one dose. (1 tablet, 2-3 tablets, 20ml) |
| stereotype_zib | data,reference |
| type_xtehr | Quantity |

### Comments
These concepts match. Note that the zib datatype Range includes FHIR datatypes Quantity and Range used in the XT-EHR model. 


## EHDSDosaging.doseAndRate.rate[x]

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.doseAndRate.rate[x] |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSpeed::Range |
| alias_zib | NL: Toedieningssnelheid::Bereik |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Time period during which one defined dose is administered (per 1 hour, per 5-10 minutes) |
| definition_zib | The administering speed is used in slow administration of liquid. In practice, the measuring unit is almost always ml/hour. <br>Entering an interval (such as 0-10 ml/hour) is also a commonly used option. <br><br>For example, with an administering speed of 10ml/hour: <br>-  amount = 10, <br>  <li>dose unit = ml, <br>  <li>time unit = hour <br>-  dose unit = ml, <br>  <li>time unit = hour <br>-  time unit = hour  |
| id_xtehr | EHDSDosaging.doseAndRate.rate[x] |
| id_zib | NL-CM:9.12.19942 |
| name_zib | AdministeringSpeed::Range |
| path_xtehr | EHDSDosaging.doseAndRate.rate[x] |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSpeed::Range |
| short_xtehr | Time period during which one defined dose is administered (per 1 hour, per 5-10 minutes) |
| stereotype_zib | data,reference |
| type_xtehr | Ratio |

### Comments
The zib and Xt-EHR concepts are equivalent, on the assumption that EHDSDosaging.doseAndRate rate is really a rate (an amount per unit of time) and the definition (Time period which one defined dose is administered) is wrong. This definition conflicts with the name of the concept.  
There are differences however: 
+ EHDSDosaging.rate has datatypes Ratio, Quantity and Range. The latter could be used to represent e.g. "5 ml in 8 minutes". This is not possible in the zib.  
+ The zib restricts the use of .AdministeringSpeed to the use case of slow administration of liquid. The Xt-EHR model does not.

## EHDSDosaging.doseAndRate.type

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.doseAndRate.type |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | The kind of dose or rate specified (e.g calculated, ordered, etc). |
| id_xtehr | EHDSDosaging.doseAndRate.type |
| path_xtehr | EHDSDosaging.doseAndRate.type |
| short_xtehr | The kind of dose or rate specified (e.g calculated, ordered, etc). |
| type_xtehr | CodeableConcept |

### Comments
There is no equivalent concept in the zib.



## EHDSDosaging.maxDose

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.maxDose |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Maximum dose for the patient |
| id_xtehr | EHDSDosaging.maxDose |
| path_xtehr | EHDSDosaging.maxDose |
| short_xtehr | Maximum dose for the patient |
| type_xtehr | Base |

### Comments
There's no equivalent concept in the zib. The zib has .AsNeeded.MaximumDose, which is the maximum dose in an "as needed" prescription. It not clear why this concept should be relevant in other prescriptions than "as needed". 



## EHDSDosaging.maxDose.maxDosePerAdministration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.maxDose.maxDosePerAdministration |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Upper limit on medication per one administration |
| id_xtehr | EHDSDosaging.maxDose.maxDosePerAdministration |
| path_xtehr | EHDSDosaging.maxDose.maxDosePerAdministration |
| short_xtehr | Upper limit on medication per one administration |
| type_xtehr | Quantity |

### Comments
There's no equivalent concept in the zib. 



## EHDSDosaging.maxDose.maxDosePerLifetime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.maxDose.maxDosePerLifetime |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Upper limit on medication per lifetime of the patient |
| id_xtehr | EHDSDosaging.maxDose.maxDosePerLifetime |
| path_xtehr | EHDSDosaging.maxDose.maxDosePerLifetime |
| short_xtehr | Upper limit on medication per lifetime of the patient |
| type_xtehr | Quantity |

### Comments
There's no equivalent concept in the zib. 


## EHDSDosaging.maxDose.maxDosePerPeriod

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.maxDose.maxDosePerPeriod |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Upper limit on medication per unit of time |
| id_xtehr | EHDSDosaging.maxDose.maxDosePerPeriod |
| path_xtehr | EHDSDosaging.maxDose.maxDosePerPeriod |
| short_xtehr | Upper limit on medication per unit of time |
| type_xtehr | Ratio |

### Comments
The zib has .AsNeeded.MaximumDose.MaximumDose, which is the maximum usage per unit of time in an "as needed" prescription. The Xt-EHR concept can be used for all prescriptions. It is not clear why it should be relevant in other prescriptions than "as needed" prescriptions. 


## EHDSDosaging.methodOfAdministration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.methodOfAdministration |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Method of administration |
| id_xtehr | EHDSDosaging.methodOfAdministration |
| path_xtehr | EHDSDosaging.methodOfAdministration |
| short_xtehr | Method of administration |
| type_xtehr | CodeableConcept |

### Comments
Exact match.



## EHDSDosaging.patientInstruction

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.patientInstruction |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Patient oriented instructions as free text |
| id_xtehr | EHDSDosaging.patientInstruction |
| path_xtehr | EHDSDosaging.patientInstruction |
| short_xtehr | Patient oriented instructions as free text |
| type_xtehr | string |

### Comments
There is no equivalent concept in the zib. The zib has only coded instructions in .AdditionalInstructions.


## EHDSDosaging.renderedDescription

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.renderedDescription |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Text representation rendered from all dosaging data elements with a value |
| id_xtehr | EHDSDosaging.renderedDescription |
| path_xtehr | EHDSDosaging.renderedDescription |
| short_xtehr | Text representation rendered from all dosaging data elements with a value |
| type_xtehr | string |

### Comments
This concept is not present in the Workpackage 6.2 branch of the logical models. There is no equivalent in the zib, as per design principle.



## EHDSDosaging.routeOfAdministration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.routeOfAdministration |
| zib | InstructionsForUse.RouteOfAdministration |
| alias_zib | NL: Toedieningsweg |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Route of administration |
| definition_zib | The route through which the medication is administered (oral, nasal, intravenous, etc.). |
| id_xtehr | EHDSDosaging.routeOfAdministration |
| id_zib | NL-CM:9.12.19941 |
| name_zib | RouteOfAdministration |
| path_xtehr | EHDSDosaging.routeOfAdministration |
| path_zib | InstructionsForUse.RouteOfAdministration |
| short_xtehr | Route of administration |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Exact match.



## EHDSDosaging.sequence

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.sequence |
| zib | InstructionsForUse.DosingInstructions.SequenceNumber |
| alias_zib | NL: Volgnummer |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Order of the dosage instruction, in case one treatment consists of several dosaging schemes |
| definition_zib | This indicates the sequence of the dosing instructions within the medication agreement. |
| id_xtehr | EHDSDosaging.sequence |
| id_zib | NL-CM:9.12.22503 |
| name_zib | SequenceNumber |
| path_xtehr | EHDSDosaging.sequence |
| path_zib | InstructionsForUse.DosingInstructions.SequenceNumber |
| short_xtehr | Order of the dosage instruction, in case one treatment consists of several dosaging schemes |
| stereotype_zib | data |
| type_xtehr | integer |
| type_zib | INT |

### Comments
Match, but zib definition is "sequence within medication agreement" and Xt-EHR definition is "order within one treatment". 



## EHDSDosaging.text

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.text |
| zib | InstructionsForUse.Description |
| alias_zib | NL: Omschrijving |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Free text usage/dosage instructions when structured dosage information is not fully provided |
| definition_zib | Textual description of the complete instructions for use including the period of use. |
| id_xtehr | EHDSDosaging.text |
| id_zib | NL-CM:9.12.9581 |
| name_zib | Description |
| path_xtehr | EHDSDosaging.text |
| path_zib | InstructionsForUse.Description |
| short_xtehr | Free text usage/dosage instructions when structured dosage information is not fully provided |
| stereotype_zib | data |
| type_xtehr | string |
| type_zib | ST |

### Comments
The zib and Xt-EHR concepts are equivalent, but the Xt-EHR definition restricts the use to "when structured dosage information is not fully provided".



## EHDSDosaging.timing

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule |
| alias_zib | NL: Toedieningsschema |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | When medication should be administered (period, time of day, frequency, etc) |
| definition_zib | Specifications of the times at which the medication is to be administered. This is indicated as follows: <br>-  Time(s) (16:00) or indications (�before meals�) at which the medication is to be taken each day.<br>-  A specific number of times the medication is to be taken each day ("3x a day"), indicated with the frequency.<br>-  A time interval between consecutive doses (�Every 2 hours�, �every 3 days�), indicated with the word Interval.<br>-  Combined periods with an interval and duration (�1 daily for three out of four weeks: the pill schedule�)<br><br>If a certain medication is not to be taken daily, the aforementioned can be combined with daily indications: <br>-  One or more week days on which the medication is to be administered (e.g. �Monday, Wednesday, Friday�)<br>-  �3x a week�, �2x a month�.<br><br>The specified administration �infinite� is automatically to be repeated until:  <br>-  The end date and time has been reached<br>-  The total administration duration has been reached (14 days)<br>-  A specific amount of administrations has been reached (�20 doses�), to be entered in the Frequency concept. |
| id_xtehr | EHDSDosaging.timing |
| id_zib | NL-CM:9.12.19948 |
| name_zib | AdministeringSchedule |
| path_xtehr | EHDSDosaging.timing |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule |
| short_xtehr | When medication should be administered (period, time of day, frequency, etc) |
| stereotype_zib | container |
| type_xtehr | Base |

### Comments
These container concepts are equivalent.


## EHDSDosaging.timing.code

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.code |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Timing abbreviation (AM - morning, Q4H - once in every 4 hours, BID - twice a day, etc) |
| id_xtehr | EHDSDosaging.timing.code |
| path_xtehr | EHDSDosaging.timing.code |
| short_xtehr | Timing abbreviation (AM - morning, Q4H - once in every 4 hours, BID - twice a day, etc) |
| type_xtehr | CodeableConcept |

### Comments
The .code concept seems to be a combination of frequency and part of day. The zib has both, but not a combination.



## EHDSDosaging.timing.event


### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.event |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Exact date and/or time of the administration |
| id_xtehr | EHDSDosaging.timing.event |
| path_xtehr | EHDSDosaging.timing.event |
| short_xtehr | Exact date and/or time of the administration |
| type_xtehr | dateTime |

### Comments
The zib has .AdministeringSchedule.AdministrationTime which maps to .timing.repeat.timeOfDay in the EHDS model. One could argue that this concept is not necessary as it can be expressed as a schedule whith only one administration.


## EHDSDosaging.timing.repeat

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Repetition of the administration. |
| id_xtehr | EHDSDosaging.timing.repeat |
| path_xtehr | EHDSDosaging.timing.repeat |
| short_xtehr | Repetition of the administration. |
| type_xtehr | Base |

### Comments
This container is not present in the zib.



## EHDSDosaging.timing.repeat.bounds

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.bounds |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Time bounds for the treatment (current dosaging scheme). Only one of the following can exist. |
| id_xtehr | EHDSDosaging.timing.repeat.bounds |
| path_xtehr | EHDSDosaging.timing.repeat.bounds |
| short_xtehr | Time bounds for the treatment (current dosaging scheme). Only one of the following can exist. |
| type_xtehr | Base |

### Comments
This container is not present in the zib.


## EHDSDosaging.timing.repeat.bounds.duration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.bounds.duration |
| zib | InstructionsForUse.DosingInstructions.DoseDuration |
| alias_zib | NL: Doseerduur |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Number of time units, e.g 10 days |
| definition_zib | The intended time duration for these dosing instructions, e.g. 5 days or 8 weeks. <br>In the case of medication for an indefinite period, the dosing duration is left empty in the last dosing instruction.<br>Permitted units for the duration: hour, day, week, year. |
| id_xtehr | EHDSDosaging.timing.repeat.bounds.duration |
| id_zib | NL-CM:9.12.22506 |
| name_zib | DoseDuration |
| path_xtehr | EHDSDosaging.timing.repeat.bounds.duration |
| path_zib | InstructionsForUse.DosingInstructions.DoseDuration |
| short_xtehr | Number of time units, e.g 10 days |
| stereotype_zib | data |
| type_xtehr | Quantity |
| type_zib | PQ |

### Comments
Exact match.


## EHDSDosaging.timing.repeat.bounds.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.bounds.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Start and end date, 05.08.2023 - 10.08.2023 |
| id_xtehr | EHDSDosaging.timing.repeat.bounds.period |
| path_xtehr | EHDSDosaging.timing.repeat.bounds.period |
| short_xtehr | Start and end date, 05.08.2023 - 10.08.2023 |
| type_xtehr | Period |

### Comments
This concept has no equivalent in the zib. Only a duration can be specified in .DoseDuration.


## EHDSDosaging.timing.repeat.bounds.range

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.bounds.range |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | A range of numbers of time units, 5-10 days |
| id_xtehr | EHDSDosaging.timing.repeat.bounds.range |
| path_xtehr | EHDSDosaging.timing.repeat.bounds.range |
| short_xtehr | A range of numbers of time units, 5-10 days |
| type_xtehr | Range |

### Comments
This concept has no equivalent in the zib. Only an exact duration can be specified in .DoseDuration.



## EHDSDosaging.timing.repeat.count

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.count |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Number of times to repeat, exact or range |
| id_xtehr | EHDSDosaging.timing.repeat.count |
| path_xtehr | EHDSDosaging.timing.repeat.count |
| short_xtehr | Number of times to repeat, exact or range |
| type_xtehr | Base |

### Comments
This container has no equivalent in the zib.


## EHDSDosaging.timing.repeat.count.count

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.count.count |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Number of times (e.g 'once', '10 times') |
| id_xtehr | EHDSDosaging.timing.repeat.count.count |
| path_xtehr | EHDSDosaging.timing.repeat.count.count |
| short_xtehr | Number of times (e.g 'once', '10 times') |
| type_xtehr | integer |

### Comments
This concept has no equivalent in the zib. 


## EHDSDosaging.timing.repeat.count.countMax

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.count.countMax |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Maximum number of times (e.g 'maximum 10 times') |
| id_xtehr | EHDSDosaging.timing.repeat.count.countMax |
| path_xtehr | EHDSDosaging.timing.repeat.count.countMax |
| short_xtehr | Maximum number of times (e.g 'maximum 10 times') |
| type_xtehr | integer |

### Comments
This concept has no equivalent in the zib. 


## EHDSDosaging.timing.repeat.dayOfWeek

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.dayOfWeek |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.WeekDay |
| alias_zib | NL: Weekdag |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | The day of the week of administration, e.g Mon, Tue, etc |
| definition_zib | WeekDay indicates a pattern of doses on fixed week days. |
| id_xtehr | EHDSDosaging.timing.repeat.dayOfWeek |
| id_zib | NL-CM:9.12.19952 |
| name_zib | AdministeringSchedule.WeekDay |
| path_xtehr | EHDSDosaging.timing.repeat.dayOfWeek |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.WeekDay |
| short_xtehr | The day of the week of administration, e.g Mon, Tue, etc |
| stereotype_zib | data |
| type_xtehr | CodeableConcept |
| type_zib | CD |

### Comments
Exact match.



## EHDSDosaging.timing.repeat.duration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.duration |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Duration of one administration, exact or range |
| id_xtehr | EHDSDosaging.timing.repeat.duration |
| path_xtehr | EHDSDosaging.timing.repeat.duration |
| short_xtehr | Duration of one administration, exact or range |
| type_xtehr | Base |

### Comments
This container has no equivalent in the zib.



## EHDSDosaging.timing.repeat.duration.duration

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.duration.duration |
| zib | InstructionsForUse.DosingInstructions.Dosage.DurationOfAdministration::TimeInterval |
| alias_zib | NL: Toedieningsduur::TijdsInterval |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Duration of administration (e.g '5 minutes', '1 hour') |
| definition_zib | The duration of administration defines the length of time during which the drug is administered and is mainly used in the slow parenteral administration of fluids.<br>Permitted units for the duration: second, minute, hour, day. |
| id_xtehr | EHDSDosaging.timing.repeat.duration.duration |
| id_zib | NL-CM:9.12.23141 |
| name_zib | DurationOfAdministration::TimeInterval |
| path_xtehr | EHDSDosaging.timing.repeat.duration.duration |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.DurationOfAdministration::TimeInterval |
| short_xtehr | Duration of administration (e.g '5 minutes', '1 hour') |
| stereotype_zib | data,reference |
| type_xtehr | Quantity |

### Comments
Match, but different data type. The zib has TimeInterval, which includes .Duration but also .StartEvent and .EndEvent. Theoretically, only .StartEvent can be used: in that case, the zib information can not be mapped.


## EHDSDosaging.timing.repeat.duration.durationMax

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.duration.durationMax |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Maximum duration of administration (e.g 'maximum 1 hour') |
| id_xtehr | EHDSDosaging.timing.repeat.duration.durationMax |
| path_xtehr | EHDSDosaging.timing.repeat.duration.durationMax |
| short_xtehr | Maximum duration of administration (e.g 'maximum 1 hour') |
| type_xtehr | Quantity |

### Comments
This concept has no equivalnt in the zib.



## EHDSDosaging.timing.repeat.eventTime

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.eventTime |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | An event the administration is bound to, e.g 'before meal', '30 min before meal' |
| id_xtehr | EHDSDosaging.timing.repeat.eventTime |
| path_xtehr | EHDSDosaging.timing.repeat.eventTime |
| short_xtehr | An event the administration is bound to, e.g 'before meal', '30 min before meal' |
| type_xtehr | Base |

### Comments
This container has no equivalnt in the zib.


## EHDSDosaging.timing.repeat.eventTime.offset

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.eventTime.offset |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | minutes from event, before or after (?not sure how to show before/after with only positive integers) |
| id_xtehr | EHDSDosaging.timing.repeat.eventTime.offset |
| path_xtehr | EHDSDosaging.timing.repeat.eventTime.offset |
| short_xtehr | minutes from event, before or after (?not sure how to show before/after with only positive integers) |
| type_xtehr | integer |

### Comments
This concept has no equivalent in the zib. 


## EHDSDosaging.timing.repeat.eventTime.when

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.eventTime.when |
| zib |  |
| card._xtehr | 0..* |
| definition_xtehr | Time period or event ('before meal', 'immediately', 'morning') |
| id_xtehr | EHDSDosaging.timing.repeat.eventTime.when |
| path_xtehr | EHDSDosaging.timing.repeat.eventTime.when |
| short_xtehr | Time period or event ('before meal', 'immediately', 'morning') |
| type_xtehr | CodeableConcept |

### Comments
This concept has no equivalent in the zib, although it was intended to be there, seen the definition of the AdministeringSchedule container. The instructions may be pre-coordionated in the AdditionalInstructionsCodelist of the zib.


## EHDSDosaging.timing.repeat.frequency

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.frequency |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Frequency of intake/administration (e.g 'three times a day') |
| id_xtehr | EHDSDosaging.timing.repeat.frequency |
| path_xtehr | EHDSDosaging.timing.repeat.frequency |
| short_xtehr | Frequency of intake/administration (e.g 'three times a day') |
| type_xtehr | Base |

### Comments
This container has no equivalent in the zib.


## EHDSDosaging.timing.repeat.frequency.maxNumberOfTimes

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.frequency.maxNumberOfTimes |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Maximum number of times per period (e.g. 'maximum 3 times') |
| id_xtehr | EHDSDosaging.timing.repeat.frequency.maxNumberOfTimes |
| path_xtehr | EHDSDosaging.timing.repeat.frequency.maxNumberOfTimes |
| short_xtehr | Maximum number of times per period (e.g. 'maximum 3 times') |
| type_xtehr | integer |

### Comments
The concept has no direct equivalent in the zib, but the maximum frequency can be specified in the range of AdmnisteringSchedule.Frequency::Range in the zib.



## EHDSDosaging.timing.repeat.frequency.numberOfTimes

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.frequency.numberOfTimes |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Frequency::Range |
| alias_zib | NL: Frequentie::Bereik |
| card._xtehr | 0..1 |
| card._zib | 0..1 |
| definition_xtehr | Number of times per period (e.g '3 times') |
| definition_zib | The frequency indicates the number of dose moments per time unit, usually per day. If this frequency is included, then the Interval will not have been included. Usually, frequency comprises both amount and time unit (3 times a day), but it can occur without the time unit (single use). <br><br>In that case, a reasonable distribution over the day is expected, but exact times are not given. This is left to the patient. It is the most common manner of extramural prescription. In the case of Baxter packs and intramural care, such a prescription is used to draw up a (location-specific) outline for distribution times (logistics). <br><br>The time unit of the frequency must be the same as how it is indicated in the textual description of the dose. <br><br>Example: <br>for a '2x a day...' dose: <br>-  amount = 2 <br>-  time unit = 'day'.<br>for a '3x a week...' dose: <br>-  amount = 3 <br>-  time unit = 'week'.<br><br>Permitted units for the duration: minute, hour, day, week, month, year. |
| id_xtehr | EHDSDosaging.timing.repeat.frequency.numberOfTimes |
| id_zib | NL-CM:9.12.19949 |
| name_zib | AdministeringSchedule.Frequency::Range |
| path_xtehr | EHDSDosaging.timing.repeat.frequency.numberOfTimes |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Frequency::Range |
| short_xtehr | Number of times per period (e.g '3 times') |
| stereotype_zib | data,reference |
| type_xtehr | integer |

### Comments
AdministeringSchedule.Frequency is a range of physical quantities (for example 5 to 10 times/day.) In the Xt-EHR model, one has to specify a .numberOfTimes and a .period, anh the frequency would be the quotinet betwee the two. For example: 5 times in 3 days. This seems a very unusual way to specify a frequency.



## EHDSDosaging.timing.repeat.frequency.period

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.frequency.period |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Duration to which the frequency applies (e.g '... / 1 day') |
| id_xtehr | EHDSDosaging.timing.repeat.frequency.period |
| path_xtehr | EHDSDosaging.timing.repeat.frequency.period |
| short_xtehr | Duration to which the frequency applies (e.g '... / 1 day') |
| type_xtehr | Quantity |

### Comments
The .period has no equivalent in the zib, but is needed to express the frequency, which is present in the zib.



## EHDSDosaging.timing.repeat.frequency.periodMax

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.frequency.periodMax |
| zib |  |
| card._xtehr | 0..1 |
| definition_xtehr | Upper limit of the period (e.g ... / 4-6 hours) |
| id_xtehr | EHDSDosaging.timing.repeat.frequency.periodMax |
| path_xtehr | EHDSDosaging.timing.repeat.frequency.periodMax |
| short_xtehr | Upper limit of the period (e.g ... / 4-6 hours) |
| type_xtehr | Quantity |

### Comments
This concept has no equivalnt in the zib.


## EHDSDosaging.timing.repeat.timeOfDay

### Table

| attribute | value |
|---|---|
| xtehr | EHDSDosaging.timing.repeat.timeOfDay |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.AdministrationTime |
| alias_zib | NL: Toedientijd |
| card._xtehr | 0..* |
| card._zib | 0..* |
| definition_xtehr | Time of day of administration (e.g '10:00') |
| definition_zib | The time of administration is a specific time of day (on the clock). This time usually isn�t (intended to be) exact. There can be multiple administering times in one day. <br> <br>The ideal time of administration can also be entered as a time of day (morning, afternoon, evening, night-time). The administration time is then to be left empty, and the time of day can be entered in the TimeOfDay concept. |
| id_xtehr | EHDSDosaging.timing.repeat.timeOfDay |
| id_zib | NL-CM:9.12.19951 |
| name_zib | AdministeringSchedule.AdministrationTime |
| path_xtehr | EHDSDosaging.timing.repeat.timeOfDay |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.AdministrationTime |
| short_xtehr | Time of day of administration (e.g '10:00') |
| stereotype_zib | data |
| type_xtehr | time |
| type_zib | TS |

### Comments
Exact match.


## zib: InstructionsForUse.DosingInstructions

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions |
| alias_zib | NL: Doseerinstructie |
| card._zib | 0..* |
| definition_zib | Dosing instructions |
| id_zib | NL-CM:9.12.22095 |
| name_zib | DosingInstructions |
| path_zib | InstructionsForUse.DosingInstructions |
| stereotype_zib | container |

### Comments
This container has no equivalent in the Xt-EHR model.


## zib: InstructionsForUse.DosingInstructions.Dosage

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions.Dosage |
| alias_zib | NL: Dosering |
| card._zib | 0..* |
| definition_zib | Container of the Dosage concept. This container contains all data elements of the Dosage concept. <br> <br>Instructions for the administrator to administer the medication (the patient themselves, a nurse or other aid). When taking stock of medication use, the dosage describes the pattern of use established by the patient. <br> <br>Once the dose schedule (distribution of doses over time) and the dose have been determined, then there should be one single instruction for use. <br> <br>Multiple parallel instructions for use can be included in the event of a changing dose within one day and in the event of a variable use frequency. <br> <br>Multiple sequential instructions for use can be included in the event of changing doses within one period and/or in the event of a changing dose schedule. |
| id_zib | NL-CM:9.12.19935 |
| name_zib | Dosage |
| path_zib | InstructionsForUse.DosingInstructions.Dosage |
| stereotype_zib | container |

### Comments
This container has no equivalent in the Xt-EHR model.


## zib: InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule |
| alias_zib | NL: Toedieningsschema |
| card._zib | 0..1 |
| definition_zib | Specifications of the times at which the medication is to be administered. This is indicated as follows: <br>-  Time(s) (16:00) or indications (�before meals�) at which the medication is to be taken each day.<br>-  A specific number of times the medication is to be taken each day ("3x a day"), indicated with the frequency.<br>-  A time interval between consecutive doses (�Every 2 hours�, �every 3 days�), indicated with the word Interval.<br>-  Combined periods with an interval and duration (�1 daily for three out of four weeks: the pill schedule�)<br><br>If a certain medication is not to be taken daily, the aforementioned can be combined with daily indications: <br>-  One or more week days on which the medication is to be administered (e.g. �Monday, Wednesday, Friday�)<br>-  �3x a week�, �2x a month�.<br><br>The specified administration �infinite� is automatically to be repeated until:  <br>-  The end date and time has been reached<br>-  The total administration duration has been reached (14 days)<br>-  A specific amount of administrations has been reached (�20 doses�), to be entered in the Frequency concept. |
| id_zib | NL-CM:9.12.19948 |
| name_zib | AdministeringSchedule |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule |
| stereotype_zib | container |

### Comments
This container has no equivalent in the Xt-EHR model.


## zib: InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Interval

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Interval |
| alias_zib | NL: Interval |
| card._zib | 0..1 |
| definition_zib | Interval indicates the time between dose times. If this is included, then the Frequency will not have been included. <br><br>Examples: every 4 hours. <br><br>The times can now be chosen freely, but distribution throughout the day is more precise, and the interval between times is important (e.g. in the case of antibiotics) <br>In the case of Baxter packs and intramural care, such a prescription is used to draw up a (location-specific) outline for distribution times (logistics). |
| id_zib | NL-CM:9.12.19950 |
| name_zib | AdministeringSchedule.Interval |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.Interval |
| stereotype_zib | data |
| type_zib | PQ |

### Comments
This concept has no equivalent in the Xt-EHR model, in which only the frequency is included.


## zib: InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.PartOfDay

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.PartOfDay |
| alias_zib | NL: Dagdeel |
| card._zib | 0..* |
| definition_zib | Time of day: morning, afternoon, evening, night. |
| id_zib | NL-CM:9.12.19953 |
| name_zib | AdministeringSchedule.PartOfDay |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AdministeringSchedule.PartOfDay |
| stereotype_zib | data |
| type_zib | CD |

### Comments
This concept has no equivalent in the Xt-EHR model, in which only a timeOdDay can be specified, or a relative time with respect to an event.


## zib: InstructionsForUse.DosingInstructions.Dosage.AsNeeded

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions.Dosage.AsNeeded |
| alias_zib | NL: Zonodig |
| card._zib | 0..1 |
| definition_zib | As needed means that the dose is only to be administered under certain conditions.<br>See also the Instructions section for more information about use of the element. |
| id_zib | NL-CM:9.12.22512 |
| name_zib | AsNeeded |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AsNeeded |
| stereotype_zib | container |

### Comments
This container has no equivalent in the zib.



## zib: InstructionsForUse.DosingInstructions.Dosage.AsNeeded.MaximumDose

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.DosingInstructions.Dosage.AsNeeded.MaximumDose |
| alias_zib | NL: MaximaleDosering |
| card._zib | 0..1 |
| definition_zib | A MaximumDose maximizes (in time) the usage of a drug in an 'as needed' prescription.<br><br>Permitted units for the duration: minute, hour, day, week, year |
| id_zib | NL-CM:9.12.19946 |
| name_zib | AsNeeded.MaximumDose |
| path_zib | InstructionsForUse.DosingInstructions.Dosage.AsNeeded.MaximumDose |
| stereotype_zib | data |
| type_zib | PQ |

### Comments
This concept had no equivalent in teh Xt-EHR model. There is a maxDose container, but its use is not restricted to the AsNeeded precriptions. It can be used for this purpose in the AsNeeded prescriptions. 



## zib: InstructionsForUse.RepeatPeriodCyclicalSchedule

### Table

| attribute | value |
|---|---|
| xtehr |  |
| zib | InstructionsForUse.RepeatPeriodCyclicalSchedule |
| alias_zib | NL: HerhaalperiodeCyclischSchema |
| card._zib | 0..1 |
| definition_zib | The repeated period in a cyclical schedule (of one or more dosing instructions). A cyclic schedule is noted in days, the corresponding dosing duration is also in days.<br><br>Examples of a cyclical schedule:  <br>contraceptive pill (21 days, 1 pill 1x a day, then skip for 7 days, repeat), repeat period here is 28 days<br>Permitted units for the duration:  day. |
| id_zib | NL-CM:9.12.22505 |
| name_zib | RepeatPeriodCyclicalSchedule |
| path_zib | InstructionsForUse.RepeatPeriodCyclicalSchedule |
| stereotype_zib | data |
| type_zib | PQ |

### Comments
This concept has no equivalent in the Xt-EHR model.
