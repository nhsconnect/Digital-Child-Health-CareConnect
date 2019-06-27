---
title: Referral Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_referral.html
summary: "The FHIR profiles used for the Referral Event Message Bundle"
---

The following FHIR profiles are used to form the Referral Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH028 - Referral' 
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-ReferralRequest-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ReferralRequest-1)


### Referral Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:
                                                                                                   
| DCH Data Item                | FHIR resource element                                               | Mandatory/Required/Optional | Note     |
|------------------------------|---------------------------------------------------------------------|-----------------------------|----------|
| Date/Time of Referral        | DCH-ReferralRequest-1.authoredOn                                    | Mandatory                   |          |
| ODS/ORD Site Code            | CareConnect-Location-1.identifier (ODS/ORD Site Code)               | Required                    |          |
| Performing Professional      | CareConnect-DCH-Practitioner-1.name                                 | Required                    |          |
| SDS Job Role Name            | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)         | Required                    |          |
| Service Referred to          | DCH-ReferralRequest-1.serviceRequested                              | Mandatory                   |          |
| Source of Referral           | DCH-ReferralRequest-1.sourceOfReferral (extension)                  | Required                    |          |
| Urgency                      | DCH-ReferralRequest-1.priority                                      | Required                    | **\***   |
| Reason for Referral          | DCH-ReferralRequest-1.reasonCode                                    | Mandatory                   |          |
| Comment                      | DCH-ReferralRequest-1.note                                          | Optional                    |          |

**\*** Note that there is a mandatory FHIR valueSet for ReferralRequest.priority. The NHS Data Dictionary Priority Type valueSet has been mapped on to the mandated FHIR valueSet in the following way:

| FHIR request-priority          | NHS Data Dictionary Priority Type           |
|--------------------------------|---------------------------------------------|
| routine - Routine              | 1 - Routine                                 |
| urgent - Urgent                | 2 - Urgent                                  |
| asap - ASAP                    | 3 - Two Week Wait                           |


### Linkage Diagram ###

<img src="images/explore/Referral.png">



### Examples ###

<script src="https://gist.github.com/IOPS-DEV/3a533dbed34f30392d2341c9a5b9c313.js"></script>



<script src="https://gist.github.com/IOPS-DEV/e83f29d5cab77d53605be6b56dd6902a.js"></script>
