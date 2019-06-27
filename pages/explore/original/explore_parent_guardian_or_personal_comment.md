---
title: Parent, Guardian or Personal Comment Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_parent_guardian_or_personal_comment.html
summary: "The FHIR profiles used for the Parent, Guardian or Personal Comment Event Message Bundle"
---

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
