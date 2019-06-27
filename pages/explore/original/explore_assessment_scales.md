---
title: Assessment Scales Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_assessment_scales.html
summary: "The FHIR profiles used for the Assessment Scales Event Message Bundle"
---

The following FHIR profiles are used to form the Assessment Scales Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH004 - Assessment Scales'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)
- [CareConnect-DCH-AssessmentScale-Observation-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-AssessmentScale-Observation-1)
                                                                                                   
### Assessment Scales Event data item mapping to FHIR profiles ###

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

**Assessment Scales Child Health Event**

| DCH Data Item              | FHIR Resource element                                                                     | Mandatory/<br/>Required/<br/>Optional | Note                    |
|----------------------------|-------------------------------------------------------------------------------------------|----------------------------------------|-------------------------|
| Date                       | CareConnect-DCH-Encounter-1.period.start                                                  | Mandatory                              | Format is YYYY-MM-DD”T”HH:MM:SS                        |
| ODS Site Code              | CareConnect-Location-1.identifier (ODS Site Code)                                         | Required                               |                         |
| Professional Name          | CareConnect-DCH-Practitioner.name                                                         | Required                               |                         |
| SDS Job Role Name          | CareConnect-DCH-PractitionerRole-1.code (SDS Job Role Name)	                             | Required                               |                         |
| Coded Assessment Tool Type (Total) | CareConnect-DCH-AssessmentScale-Observation-1.code 	                                     | Mandatory                              | This is the Assessment Scale Type.|
| Comment (Total Assessment Scale)   | CareConnect-DCH-AssessmentScale-Observation-1.comment                             | Optional                               | Supporting text may be given regarding the assessment scale as a whole. This could be the recording of a score of an assessment not in SNOMED CT (e.g. Griffiths). |
| Coded Assessment Tool Type Total Score | CareConnect-DCH-AssessmentScale-Observation-1.value[x]	                     | Required                               | Score entered for the Total Assessment Scale. |
| Coded Assessment Tool Type (Subscale) | CareConnect-DCH-AssessmentScale-Observation-1.related.target.Observation.code	                         | Mandatory                               | The type of Subscale Assessment Scale. Note, the Subscale may not always have a code, when the code is not available use code.text.|
| Comment (Subscale Assessment Scale)   | CareConnect-DCH-AssessmentScale-Observation-1.related.target.Observation.comment | Optional                            | Supporting text may be given regarding the assessment scale as a Subscale. This could be the recording of a Subscale score of an assessment not in SNOMED CT. |
| Coded Assessment Tool Type Subscale Score | CareConnect-DCH-AssessmentScale-Observation-1.related.target.Observation.value[x]	                      | Required                               | Score entered for the Subscale Assessment Scale. |

**This is the recommended option to share Subscale Score.**

For systems that hold the Coded Assessment Tool Type Total Score score, the Subscale scores and the associated observations:
* The overall Coded Assessment Tool Type Total Score score is held in the CareConnect-DCH-AssessmentScale-Observation-1 profile.
* The Subscale Assessment scores are held in the observation profile, <a href="https://www.hl7.org/fhir/references.html#contained" target="_blank">**contained**</a> within the CareConnect-DCH-AssessmentScale-Observation-1 profile. The CareConnect-DCH-AssessmentScale-Observation-1 profile links to each Subscale score profile using the a related link.
* The observations are referenced by the Subscale scores using the related links.

<!--
**ASQ-3 (Ages and Stages Questionnaires Third Edition)**

| DCH Data Item              | FHIR Resource element                                                                     | Mandatory/Required/Optional |
|----------------------------|-------------------------------------------------------------------------------------------|-----------------------------|
| Coded Assessment Tool Type | CareConnect-DCH-ASQ3AssessmentScale-Observation-1.code 									 | Mandatory                   |
| Score                      | CareConnect-DCH-ASQ3AssessmentScale-Observation-1.component.valueQuantity				 | Mandatory                   |

**Ages and Stages Questionnaires: Social-Emotional**

| DCH Data Item              | FHIR Resource element                                                                       | Mandatory/Required/Optional |
|----------------------------|---------------------------------------------------------------------------------------------|-----------------------------|
| Coded Assessment Tool Type | CareConnect-DCH-ASQSE-AssessmentScale-Observation-1.code 									   | Mandatory                   |
| Score                      | CareConnect-DCH-ASQSE-AssessmentScale-Observation-1.component.valueQuantity				   | Mandatory                   |

**Other Assessment Tools**

| DCH Data Item              | FHIR Resource element                                                                                   | Mandatory/Required/Optional |
|----------------------------|---------------------------------------------------------------------------------------------------------|-----------------------------|
| Coded Assessment Tool Type | CareConnect-DCH-AssessmentScale-Observation-1.code 													   | Required                    |
| Score                      | CareConnect-DCH-AssessmentScale-Observation-1.value[x] or CareConnect-DCH-AssessmentScale-Observation-1.componentvalue[x]										       		   | Required                   |-->

### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/AssessmentScales.png">

### Assessment Scales Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/817e839787c3d2fa62e51114a158e85e.js"></script>

###  Assessment Scales Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/a7091fb37cfecff8aca2d92a0ac04ba5.js"></script>

