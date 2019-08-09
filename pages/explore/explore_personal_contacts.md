---
title: Personal Contacts Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_personal_contacts.html
summary: "The FHIR profiles used for the Personal Contacts Event Message Bundle"
---

The following FHIR profiles are used to form the Personal Contacts Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH023 - Personal Contacts'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-RelatedPerson-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-RelatedPerson-1)

### Personal Contacts Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item           | FHIR resource element                                          | Mandatory/<br/>Required/<br/>Optional  | Note                                          |
|-------------------------|----------------------------------------------------------------|----------------------------------------|-----------------------------------------------|
| Date/Time               | CareConnect-DCH-Encounter-1.period.start                       | Mandatory                              | Date/Time the personal contact was recorded.<br/>  Format: YYYY-MM-DD”T”HH:MM:SS   |
| First Given Name        | DCH-RelatedPerson-1.name.given                                 | Mandatory                   | The first forename or given name of the related or significant person. |
| Family Name             | DCH-RelatedPerson-1.name.family                                | Mandatory                   | That part of a person's name which is used to describe family, clan, tribal group, or marital association of the related or significant person.   |
| Contact Details         | DCH-RelatedPerson-1.address and/or DCH-RelatedPerson-1.telecom | Required                    | Contact details of the person (e.g. telephone number, email address etc.). |
| Relationship Type       | DCH-RelatedPerson-1.relationship                               | Mandatory                   | For Personal Contacts, the relationship type must be drawn from the given valueSet. |
| Household member        | DCH-RelatedPerson-1.householdMember - extension                | Required                    | For Personal Contacts, do not send the Household Member Description.*  |
| Parental Responsibility | DCH-RelatedPerson-1.parentalResponsibility - extension         | Required                    | Flag to indicate whether the related or significant person has parental responsibility.*  |
| Significant Individual  | DCH-RelatedPerson-1.significantIndividual - extension          | Required                    | Flag as to whether the people are deemed as key by family or Health Care Professional in the child's life that do not live in the home (s).*  |

*Only send these data items where the answer is "true" 

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/PersonalContacts.png">

### Personal Contacts Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/faf85a26f5b36944022cb5c76be489f7.js"></script>

### Personal Contacts Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/3791ee116a1598b9134b2bb74f91913d.js"></script>
