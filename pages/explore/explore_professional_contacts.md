---
title: Professional Contacts Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_professional_contacts.html
summary: "The FHIR profiles used for the Professional Contacts Event Message Bundle"
---
## FHIR Profiles ##

The following FHIR profiles are used to form the Professional Contacts Event Message Bundle:

- [Bundle](http://hl7.org/fhir/STU3/StructureDefinition/Bundle)
- [Event-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/Event-MessageHeader-1) - where the coding and display elements for the ‘event’ type are fixed to "​professional-contacts-1 \| ​Professional Contacts"
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [CareConnect-HealthcareService-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-HealthcareService-1)
- [CareConnect-Patient-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Patient-1)
- [CareConnect-Encounter-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-EpisodeOfCare-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-EpisodeOfCare-1)
Then for Professional Contacts (Team) Event
- [CareConnect-CareTeam-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-CareTeam-1)
Or for Professional Contacts (Professional) Event
- [CareConnect-Practitioner-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Practitioner-1)
- [CareConnect-PractitionerRole-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-PractitionerRole-1)

## Bundle Structure


Specifies referencing within the Event Message Bundle.

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-professionalcontacts2professional.png" target="_blank"><img src="images/explore/dch-professionalcontacts2professional.png"></a><br/>
	Professional Contacts (Professional)<a href="images/explore/dch-professionalcontacts2professional.png" target="_blank">(open in new TAB)</a>
</div>

<div style="text-align:center; margin-bottom:20px" >
	<a href="images/explore/dch-professionalcontacts1team.png" target="_blank"><img src="images/explore/dch-professionalcontacts1team.png"></a><br/>
	Professional Contacts (Team)<a href="images/explore/dch-professionalcontacts1team.png" target="_blank">(open in new TAB)</a>
</div>

## Professional Contacts Event data item mapping to FHIR profiles ##

This Mapping table defines the FHIR elements that SHALL be used to encode the Healthy Child Event Specification data items for each DCH Event Message payload.  
Some common data item mappings, such as patient, publisher or Date/Time of event information, are defined within the [Header mapping table](explore_event_header_design.html) and SHALL be considered in parallel with the payload mapping.

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

| DCH Data Item                 | FHIR resource element                                                                            | Mandatory/Required/Optional |
|-------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------|
| Organisation                  | CareConnect-Organization-1.identifier (ODS Code or ODS Site Code)                       | Mandatory                    |
| Team                          | CareConnect-CareTeam-1.name                                                         | Required                   |
| Role                          | CareConnect-CareTeam-1.participant.role                                      | Required                   |
| Name                          | CareConnect-Practitioner-1.name                                                     | Optional                    |
| Role                          | CareConnect-PractitionerRole-1.code (careProfessionalType)                          | Optional                  |
| Specialty                     | CareConnect-PractitionerRole-1.specialty                                            | Optional |
| Key Worker                    | CareConnect-PractitionerRole-1.code (keyWorker)                                     | Optional |
| Care Professional Association | CareConnect-EpisodeOfCare-1.type                                                                         | Mandatory                   |
| Contact details               | CareConnect-Organization-1.telecom                                                              | Required                    |
| Start date                    | CareConnect-EpisodeOfCare-1.period.start                                                                 | Required                   |
| End date                      | CareConnect-EpisodeOfCare-1.period.end                                                                   | Required                   |
| Reason                        | CareConnect-EpisodeOfCare-1.type.text                                                                   | Optional                   |


## Resource Population Requirements and Guidance ##

The following requirements and resource population guidance should be followed in addition to the requirements and guidance outlined in the data item mapping above and in the [Event Header](https://developer.nhs.uk/apis/ems-beta/explore_event_header_information.html) requirements page.

#### _list profiles used (and sustituted L3 variants)_ ####

## Professional Contacts Professional Example ##

<script src="https://gist.github.com/IOPS-DEV/92016f8c3f7c882112a4850e3d109c34.js"></script>

## Professional Contacts Team Example ##

<script src="https://gist.github.com/IOPS-DEV/e81780340604f6f383c965f2b98210b4.js"></script>


## Profile Change Mappings for Professional Contacts ##

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
| DCH-ProfessionalContact-EpisodeOfCare-1 | CareConnect-EpisodeOfCare-1 |
| **for Professional Contacts (Team) Event** |
| DCH-CareTeam-1 | CareConnect-CareTeam-1 |
| **for Professional Contacts (Professional) Event** |
| CareConnect-DCH-Practitioner-1 | CareConnect-Practitioner-1 |
| CareConnect-DCH-PractitionerRole-1 | CareConnect-PractitionerRole-1 |

<hr/>
<hr/>

## Old Stuff ##

#### retain until new content completed then remove ####

There are two versions of the Professional Contacts Event Message Bundle.
- **Professional Contacts (Team) Event** records a child's contact with a Care Team
- **Professional Contacts (Professional) Event** records a child's contact with a Healthcare Professional

The following FHIR profiles are used to form the Professional Contacts Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH027 - Professional Contacts'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [DCH-ProfessionalContact-EpisodeOfCare-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-ProfessionalContact-EpisodeOfCare-1)

Then for Professional Contacts (Team) Event
- [DCH-CareTeam-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-CareTeam-1)

Or for Professional Contacts (Professional) Event
- [CareConnect-DCH-Practitioner-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Practitioner-1)
- [CareConnect-DCH-PractitionerRole-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-PractitionerRole-1)

### Professional Contacts Event data item mapping to FHIR profiles ###

Depending on the association, the Child Health Event data items are fulfilled by elements within the FHIR resources listed below.

## Professional Contacts (Team) Event ##
                                                                                                   
| DCH Data Item                 | FHIR resource element                                                                            | Mandatory/Required/Optional |
|-------------------------------|--------------------------------------------------------------------------------------------------|-----------------------------|
| Organisation                  | CareConnect-Organization-1.identifier (ODS Code or ODS Site Code)                       | Mandatory                    |
| Team                          | DCH-CareTeam-1.name                                                         | Required                   |
| Role                          | DCH-CareTeam-1.participant.role                                      | Required                   |
| Name                          | CareConnect-DCH-Practitioner-1.name                                                     | Optional                    |
| Role                          | CareConnect-DCH-PractitionerRole-1.code (careProfessionalType)                          | Optional                  |
| Specialty                     | CareConnect-DCH-PractitionerRole-1.specialty                                            | Optional |
| Key Worker                    | CareConnect-DCH-PractitionerRole-1.code (keyWorker)                                     | Optional |
| Care Professional Association | DCH-ProfessionalContact-EpisodeOfCare-1.type                                                                         | Mandatory                   |
| Contact details             | CareConnect-Organization-1.telecom                                                              | Required                    |
| Start date                    | DCH-ProfessionalContact-EpisodeOfCare-1.period.start                                                                 | Required                   |
| End date                      | DCH-ProfessionalContact-EpisodeOfCare-1.period.end                                                                   | Required                   |
| Reason                        | DCH-ProfessionalContact-EpisodeOfCare-1.reason                                                                   | Optional                   |

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Professional Contacts (Team) Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/ProfessionalContacts1.png">

### Professional Contacts - Team XML Example ###

<script src="https://gist.github.com/IOPS-DEV/92a856811035c1768c64a1d3ccaba17f.js"></script>

### Professional Contacts - Team JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/c6d8852e3c4755af6983342ceb215d9a.js"></script>

## Professional Contacts (Professional) Event ##  
                                                                                                
| DCH Data Item                 | FHIR resource element                                                                            | Mandatory/Required/Optional |
|-------------------------------|-----------------------------------------------------------------------------------------|-----------------------------|
| Organisation                  | CareConnect-Organization-1.identifier (ODS Code or ODS Site Code)                       | Mandatory                    |
| Name                          | CareConnect-DCH-Practitioner-1.name                                                     | Required                    |
| Role                          | CareConnect-DCH-PractitionerRole-1.code (careProfessionalType)                          | Required                  |
| Specialty                     | CareConnect-DCH-PractitionerRole-1.specialty                                            | Optional |
| Key Worker                    | CareConnect-DCH-PractitionerRole-1.code (keyWorker)                                     | Optional |
| Care Professional Association | DCH-ProfessionalContact-EpisodeOfCare-1.type                                                                         | Mandatory                   |
| Contact details              | CareConnect-DCH-Practitioner-1.telecom                                                           | Required                    |
| Start date                    | DCH-ProfessionalContact-EpisodeOfCare-1.period.start                                                                 | Required                   |
| End date                      | DCH-ProfessionalContact-EpisodeOfCare-1.period.end                                                                   | Required                   |
| Reason                        | DCH-ProfessionalContact-EpisodeOfCare-1.reason                                                                   | Optional                   |

### Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Professional Contacts (Professional) Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/ProfessionalContacts2.png">

### Professional Contacts - Professional XML Example ###

<script src="https://gist.github.com/IOPS-DEV/3135e953849215f11b00956b2d0a9aa4.js"></script>

### Professional Contacts - Professional JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/3f8d7fe39211e3cad09abfcc591ddaab.js"></script>