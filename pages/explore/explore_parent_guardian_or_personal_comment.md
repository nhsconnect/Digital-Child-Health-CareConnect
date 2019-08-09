---
title: Parent, Guardian or Personal Comment Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_parent_guardian_or_personal_comment.html
summary: "The FHIR profiles used for the Parent, Guardian or Personal Comment Event Message Bundle"
---

## FHIR Profiles ##

The following FHIR profiles are used to form the Parent, Guardian or Personal Comment Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to ‘​parent-guardian-or-personal-comment-1 \| Parent Guardian Or Personal Comment’
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-Communication-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Communication-1)
- [CareConnect-RelatedPerson-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-RelatedPerson-1)

## Bundle Structure

Specifies referencing within the Event Message Bundle.

#### _placeholder using additional demographics ####

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-personalcontacts.png" target="_blank"><img src="images/explore/dch-personalcontacts.png"></a><br/>
	Parent, Guardian or Personal Comment <a href="images/explore/dch-personalcontacts.png" target="_blank">(open in new TAB)</a>
</div>

## Parent, Guardian or Personal Comment Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item       | FHIR resource element                     | Mandatory/Required/Optional | Note                                      |
|---------------------|-------------------------------------------|-----------------------------|-------------------------------------------|
| Date/Time           | CareConnect-Communication-1.sent  | Mandatory           |                                      |
| Name of Person recording the comment    | CareConnect-RelatedPerson-1.name         | Required                    |                                      |
| Details             | CareConnect-Communication-1.payload.contentString | Required                    |                                      |
| Relationship Status | CareConnect-RelatedPerson-1.relationship          | Required                    | **\***                |

**\*** For Parent, Guardian or Personal Comment, the Relationship Status SHALL come from the bound ValueSet [DCH-PersonRelationshipType-1](https://fhir.nhs.uk/STU3/ValueSet/DCH-PersonRelationshipType-1).  
Where one of the 'Other' codes (ORO, ORX, OTX) are used text must be provided describing the relationship.


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Parent, Guardian or Personal Comment Example ##

<script src="https://gist.github.com/IOPS-DEV/96be84949607bc7678a62c098642acf4.js"></script>


## Profile Change Mappings for Parent, Guardian or Personal Comment ##

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
| DCH-ParentGuardianOrPersonalComment-Communication-1 | CareConnect-Communication-1 |
| DCH-RelatedPerson-1 | CareConnect-RelatedPerson-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####


The following FHIR profiles are used to form the Parent, Guardian or Personal Comment Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to  'CH022 - Parent Guardian Or Personal Comment'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-ParentGuardianOrPersonalComment-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ParentGuardianOrPersonalComment-Communication-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)


### Parent, Guardian or Personal Comment Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item       | FHIR resource element                     | Mandatory/Required/Optional | Note                                      |
|---------------------|-------------------------------------------|-----------------------------|-------------------------------------------|
| Date/Time           | DCH-ParentOrGuardianComment-Communication-1.sent  | Mandatory           |                                      |
| Name of Person recording the comment    | DCH-RelatedPerson-1.name         | Required                    |                                      |
| Details             | DCH-ParentOrGuardianComment-Communication-1.payload.contentString | Required                    |                                      |
| Relationship Status | DCH-RelatedPerson-1.relationship          | Required                    | **\***                |

**\*** For Parent, Guardian or Personal Comment, the Relationship Status SHALL come from the bound ValueSet [DCH-PersonRelationshipType-1](https://fhir.nhs.uk/STU3/ValueSet/DCH-PersonRelationshipType-1).  
Where one of the 'Other' codes (ORO, ORX, OTX) are used text must be provided describing the relationship.


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/PersonalComment.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/d147f1bd3dfa911ca267b25137051a9e.js"></script>

<script src="https://gist.github.com/IOPS-DEV/c6f59aa25a451d04077722e10b8e380c.js"></script>
