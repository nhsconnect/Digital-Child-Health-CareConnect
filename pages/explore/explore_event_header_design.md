---
title: Digital Child Health Event Header Design
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_event_header_design.html
summary: "The standard event header information applicable to Digital Child Health (DCH) event messages"
---

## Event header information ##
Each event message will carry a standard set of event header information to help identify the patient, publisher, actual event, etc.

This event header information must consist of the following **mandatory** items and their corresponding FHIR profiles and elements:

| DCH Event Header item requirement      | FHIR resource            | FHIR element                                                     |Constraints            |
|----------------------------------------|--------------------------|------------------------------------------------------------------|-----------------------|
| patient identification data:           | CareConnect-Patient-1   	|                                                                  |            |
| NHS Number                             | CareConnect-Patient-1   	| identifier using NHS Number slice                                |            |
| Date of Birth                          | CareConnect-Patient-1   	| birthDate                                                        |            |
| name                                   | CareConnect-Patient-1   	| name                                                             |            |
| event type                             | Event-MessageHeader-1    | event                                                            |            |
| type of service originating the event  | CareConnect-HealthcareService-1  | type 			                                           |This will contain a code from the ValueSet [DCH-Specialty-1.](https://fhir.nhs.uk/STU3/ValueSet/DCH-Specialty-1)|
| service provider originating the event | CareConnect-Encounter-1 	| serviceProvider                                                  |            |
| IT system holding the event data       | Event-MessageHeader-1      | source                                                         |            |
| location at which the event occurred   | CareConnect-Location-1 	| location                                                         |            |
| event date time                        | CareConnect-Encounter-1 	| period.start                                                     |           |
| event publisher                        | Event-MessageHeader-1    | responsible                                                      |            |
| event published date                   | Event-MessageHeader-1    | timestamp                                                        |            |
| a publication reference number         | Event-MessageHeader-1    | The resource identifier for the MessageHeader 				   |This will use a UUID format.|

An **optional** event-sequence element may be sent which, if included, **must** contain at least one of:

| DCH Event Header item requirement      | FHIR resource            | FHIR element                                                     |
|----------------------------------------|--------------------------|------------------------------------------------------------------|
| change timestamp         				 | Event-MessageHeader-1    | The resource meta.lastUpdated for the MessageHeader 				   |
| sequence number         | Event-MessageHeader-1    | The resource meta.versionId for the MessageHeader 				   |



The remaining resources in the bundle depend on the Digital Child Health Event listed under the [Messages](explore.html) section.

## Linkage Diagram ##

This Linkage diagram defines the required references that SHALL be made between resources within the Event Message bundle. It includes both Header and Payload resources (but omits the Bundle wrapper).

<img src="images/explore/MessageHeader.png">


## Example Message Header ##

<script src="https://gist.github.com/IOPS-DEV/a1d4a7f89b0658f3b9a0ace6dda09df9.js"></script>






