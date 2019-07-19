---
title: Developmental Skills Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_developmental_skills.html
summary: "The FHIR profiles used for the Developmental Skills Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Developmental Skills Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display for the event element is fixed to "​developmental-skills-1 | ​Developmental Skills"
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Condition-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Condition-1)
and
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)
or
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.


<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-developmentalskills.png" target="_blank"><img src="images/explore/dch-developmentalskills.png"></a><br/>
	Developmental Skills <a href="images/explore/dch-developmentalskills.png" target="_blank">(open in new TAB)</a>
</div>

## Developmental Skills Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Comments</th>
</tr>
<tr>
<td>Date first achieved</td><td>CareConnect-Condition-1.onsetDateTime</td><td>Required</td><td></td>
</tr>
<tr>
<td>Date of observation</td><td>CareConnect-Condition-1.assertedDate</td><td>Required</td><td></td>
</tr>
<tr>
<td>Date of enquiry</td><td>CareConnect-Encounter-1.period.start</td><td>Required</td><td></td>
</tr>
<tr>
<td>Developmental Skill</td><td>CareConnect-DevelopmentalSkill-Condition-1.code</td><td>Required</td><td>If a coded value does not exist for the Development Skill then the element "code.text" can be used</td>
</tr>
<tr>
<td>Result of observation/enquiry</td><td>CareConnect-Condition-1.stage.summary</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Comments</td><td>CareConnect-Condition-1.note</td><td>Optional</td><td></td>
</tr>
</table> 


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Developmental Skills Example ##

<script src="https://gist.github.com/IOPS-DEV/7a4677f7d41b421622773dc354ac592d.js"></script>


## Profile Change Mappings for Developmental Skills ##

Profiles used in [Demographics Update Event Messages 1.2.1-Release Candidate](https://developer.nhs.uk/apis/demographicupdates-120-rc/index.html) are replaced with:

| Demographic-Event-Messages | Demographic-Event-Messages-CareConnect |
|----------------------------|----------------------------------------|
| DCH-Bundle-1 | Bundle |
| DCH-MessageHeader-1 | Event-MessageHeader-1 |
| CareConnect-Organization-1 | CareConnect-Organization-1 |
| DCH-HealthcareService-1 | CareConnect-HealthcareService-1 |
| CareConnect-DCH-Patient-1 | CareConnect-Patient-1 |
| CareConnect-DCH-Encounter-1 | CareConnect-Encounter-1 |
| CareConnect-Location-1 | CareConnect-Location-1 |
| CareConnect-DCH-DevelopmentalSkill-Condition-1 | CareConnect-Condition-1 |
| Reporter |
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |
| or |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####



The following FHIR profiles are used to form the Developmental Skills Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH020 - Developmental Skills'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-DevelopmentalSkill-Condition-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-DevelopmentalSkill-Condition-1)

- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)
or  
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)

### Developmental Skills Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr>
<th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Comments</th>
</tr>
<tr>
<td>Date first achieved</td><td>CareConnect-DCH-DevelopmentalSkill-Condition-1.onsetDateTime</td><td>Required</td><td></td>
</tr>
<tr>
<td>Date of observation</td><td>CareConnect-DCH-DevelopmentalSkill-Condition-1.assertedDate</td><td>Required</td><td></td>
</tr>
<tr>
<td>Date of enquiry</td><td>CareConnect-DCH-Encounter-1.period.start</td><td>Required</td><td></td>
</tr>
<tr>
<td>Developmental Skill</td><td>CareConnect-DCH-DevelopmentalSkill-Condition-1.code</td><td>Required</td><td>If a coded value does not exist for the Development Skill then the element "code.text" can be used</td>
</tr>
<tr>
<td>Result of observation/enquiry</td><td>CareConnect-DCH-DevelopmentalSkill-Condition-1.stage.summary</td><td>Mandatory</td><td></td>
</tr>
<tr>
<td>Comments</td><td>CareConnect-DCH-DevelopmentalSkill-Condition-1.note</td><td>Optional</td><td></td>
</tr>
</table> 

### Linkage Diagram ###

<img src="images/explore/DevelopmentSkills.png">

### Development Skills XML Example ###

<script src="https://gist.github.com/IOPS-DEV/14ae03d15ae23d0721a63f13a5ae816f.js"></script>

### Development Skills JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/647f1d989d1a30cbf2b87cb82e897663.js"></script>