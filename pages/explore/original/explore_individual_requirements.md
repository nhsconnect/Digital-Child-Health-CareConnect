---
title: Individual Requirements Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_individual_requirements.html
summary: "The FHIR profiles used for the Individual Requirements Event Message Bundle"
---

The following FHIR profiles are used to form the Individual Requirements Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display for the event element is fixed to 'CH016 - Individual Requirements'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-IndividualRequirements-QuestionnaireResponse-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-IndividualRequirements-QuestionnaireResponse-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [DCH-ProfessionalComment-Communication-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ProfessionalComment-Communication-1)


### Individual Requirements Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                                                 | FHIR Resource element                                                    | Mandatory/Required/Optional | Note                                                           |
|---------------------------------------------------------------|--------------------------------------------------------------------------|-----------------------------|---------------------------------------------------------------------|
| Date/Time                                  | CareConnect-DCH-Encounter-1.period.start                            | Mandatory                   |                                                                |
| GP Opt Out Indicator                                          | DCH-IndividualRequirements-QuestionnaireResponse-1.gPOptOutIndicator     | Required                    |                                                                |
| Individual Needs Person Indicator                             | DCH-IndividualRequirements-QuestionnaireResponse-1.individualNeedsPersonIndicator | Mandatory                   |                                                                |
| Accessible Information - Communication Support                | DCH-IndividualRequirements-QuestionnaireResponse-1.communicationSupport                    | Required                    |                                                                |
| Accessible Information - Requires Communication Professional  | DCH-IndividualRequirements-QuestionnaireResponse-1.communicationProfessional               | Required                    |                                                                |
| Accessible Information - Requires Specific Contact Method     | DCH-IndividualRequirements-QuestionnaireResponse-1.specificContactMethod                           | Required                    |                                                                |
| Accessible Information - Requires Specific Information Format | DCH-IndividualRequirements-QuestionnaireResponse-1.specificInformationFormat                       | Required                    |                                                                |
| Mobility Needs                                                | DCH-IndividualRequirements-QuestionnaireResponse-1.mobilityNeeds                         | Required                    |                                                                |
| Individual Requirement Narrative Comment                      | DCH-ProfessionalComment-Communication-1.payload                                          | Optional                    | With Communication.category.coding.code and .display set to '015' and 'Individual Requirement' |


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/IndividualRequirements.png">

### Examples ###

<script src="https://gist.github.com/IOPS-DEV/0476c3b27e43ca27f814b82919d503b6.js"></script>

<script src="https://gist.github.com/IOPS-DEV/f1b51b3c37a3dce6c5aae5d4418bcd4d.js"></script>