---
title: Newborn Hearing Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_newborn_hearing.html
summary: "The FHIR profiles used for the Newborn Hearing Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Newborn Hearing Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to '​​newborn-hearing-1 \| ​Newborn Hearing'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)
- [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)
- [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)


## Bundle structure

Specifies mandatory referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-newbornhearing1.png" target="_blank"><img src="images/explore/dch-newbornhearing1.png"></a><br/>
	Newborn Hearing <a href="images/explore/dch-newbornhearing1.png" target="_blank">(open in new TAB)</a>
	<a href="images/explore/dch-newbornhearing2.png" target="_blank"><img src="images/explore/dch-newbornhearing2.png"></a><br/>
	Newborn Hearing Bundle <a href="images/explore/dch-newbornhearing2.png" target="_blank">(open in new TAB)</a>
</div>



## Resource population requirements and guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

### [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)

The Bundle resource included as part of the event message SHALL conform to the [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1)

The Event-MessageHeader-1 resource included as part of the event message SHALL conform to the [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)

The CareConnect-Organization-1 resource included as part of the event message SHALL conform to the [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)

The CareConnect-HealthcareService-1 resource included as part of the event message SHALL conform to the [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)

The CareConnect-Patient-1 resource included as part of the event message SHALL conform to the [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)

The CareConnect-Encounter-1 resource included as part of the event message SHALL conform to the [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)

The CareConnect-Location-1 resource included as part of the event message SHALL conform to the [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)

The CareConnect-Practitioner-1 resource included as part of the event message SHALL conform to the [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

The CareConnect-PractitionerRole-1 resource included as part of the event message SHALL conform to the [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1)

The CareConnect-Procedure-1 resource included as part of the event message SHALL conform to the [CareConnect-Procedure-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Procedure-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1)

The CareConnect-Observation-1 resource included as part of the event message SHALL conform to the [CareConnect-Observation-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Observation-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |



### [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)

The CareConnect-Communication-1 resource included as part of the event message SHALL conform to the [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1) constrained FHIR profile and the additional population guidance as per the table below:

| Resource Cardinality | TBC |

| Element | Cardinality | Additional Guidance |
| --- | --- | --- |
|  |  |  |


## PDS Change of Address Example ##
Placeholder for Newborn Hearing example - like it says, it's CoA
<script src="https://gist.github.com/IOPS-DEV/828562b2e3edaec1ed43f48645f5376a.js"></script>


## Profile Change Mappings for Newborn Hearing ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1                                                   | Bundle |
| DCH-MessageHeader-1                                            | Event-MessageHeader-1 |
| CareConnect-Organization-1                                     | CareConnect-Organization-1 |
| DCH-HealthcareService-1                                        | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1                                      | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1                                    | CareConnect-Encounter-1 |
| CareConnect-Location-1                                         | CareConnect-Location-1 |
| CareConnect-DCH-Practitioner-1                                 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1                             | CareConnect-PractitionerRole-1 |
| CareConnect-DCH-AABRHearingTest-Procedure-1                    | CareConnect-Procedure-1 |
| CareConnect-DCH-AOAEHearingTest-Procedure-1                    | CareConnect-Procedure-1 |
| CareConnect-DCH-HearingScreeningSummaryOutcome-Observation-1   | CareConnect-Observation-1 |
| DCH-ProfessionalComment-Communication-1                        | CareConnect-Communication-1 |


<hr/>
<hr/>

### Newborn Hearing Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](./explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:
                                                                     
| DCH Data Item                  | FHIR resource element                               | Mandatory/<br/>Required/<br/>Optional | Note                                                                  |
|--------------------------------|-----------------------------------------------------|---------------------------------------|-----------------------------------------------------------------------|
| Date/Time                      | CareConnect-DCH-Encounter-1.period.start            | Mandatory                             |                                                                       |
| Location (ODS Site Code)       | CareConnect-Location-1.identifier                   | Required                              |                                                                       |
| Performing Professional        | CareConnect-DCH-Practitioner-1.name                 | Required                              |                                                                       |
| SDS Job Role Name              | CareConnect-DCH-PractitionerRole-1.codeableConcept  | Required                              | * |
| Hearing Test Results (AABR)    | CareConnect-DCH-AABRHearingTest-Procedure-1.outcome | Required                              | two occurrences of this resource are required, one for each ear |
| Hearing Test Result (AOAE)     | CareConnect-DCH-AOAEHearingTest-Procedure-1.outcome |Required                               | up to four occurrences of this resource are required, with two for each test performed |
| Summary Outcome                | CareConnect-DCH-HearingScreeningSummaryOutcome-Observation-1.valueCodeableConcept           | Mandatory                   |                                          |
| Comment                        | DCH-ProfessionalComment-Communication-1                  | Optional                         |                                                                        |

**\*** Northgate do not record SDS Job Role Codes as part of their Child Health Screening record. As the code is typed CodeableConcept, and sliced on system, a system must be present. i.e. we can't just send:
```
        <!-- Do not do this -->
        <code>
            <text value="Specialist Registrar"/>
        </code>
```

We therefore use the UNC code from the HL7 nullFlavor codesystem to indicate there is no SDS Job Role Code. The Job Role Name is contained in the text element. Example below:
```
        <code>
            <coding>
                <system value="http://hl7.org/fhir/v3/NullFlavor"/>
                <code value="UNC"/>
                <display value="un-encoded"/>
            </coding>
            <text value="Specialist Registrar"/>
        </code>
```

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/NewbornHearing1.png">

Allowed Child Health Observations are: 

<img src="images/explore/NewbornHearing2.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/b8f0d3a8da033037ad0dfbd60a662d93.js"></script>

<script src="https://gist.github.com/IOPS-DEV/d50001b1a618a5ae1f89394cfeaa7ae8.js"></script>
