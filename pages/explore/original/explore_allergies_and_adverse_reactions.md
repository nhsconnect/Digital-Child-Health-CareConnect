---
title: Allergies and Adverse Reactions Event Message Bundle
keywords:  messaging, bundles
tags: [fhir,messaging]
sidebar: foundations_sidebar
permalink: explore_allergies_and_adverse_reactions.html
summary: "The FHIR profiles used for the Allergies and Adverse Reactions Event Message Bundle"
---

The following FHIR profiles are used to form the Allergies and Adverse Reactions Event Message Bundle:

- [DCH-Bundle-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-Bundle-1)
- [DCH-MessageHeader-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-MessageHeader-1) - where the coding and display elements for the 'event' type are fixed to 'CH003 - Allergies and Adverse Reactions'
- [CareConnect-Organization-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Organization-1)
- [DCH-HealthcareService-1](https://fhir.nhs.uk/STU3/StructureDefinition/DCH-HealthcareService-1)
- [CareConnect-DCH-Patient-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Patient-1)
- [CareConnect-DCH-Encounter-1](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-Encounter-1)
- [CareConnect-Location-1](https://fhir.hl7.org.uk/STU3/StructureDefinition/CareConnect-Location-1)
- [CareConnect-DCH-AllergyIntolerance-2](https://fhir.nhs.uk/STU3/StructureDefinition/CareConnect-DCH-AllergyIntolerance-2)


### Allergies and Drug Reactions Event data item mapping to FHIR profiles ###

The Child Health Event data items are fulfilled by elements within the FHIR resources listed below:

<table>
<tr><th>DCH Data Item</th><th>FHIR resource element</th><th>Mandatory/<br/>Required/<br/>Optional</th><th>Notes</th></tr>
<tr><td>Date/Time Recorded</td><td>CareConnect-DCH-AllergyIntolerance-2.assertedDate</td><td>Mandatory</td><td></td></tr>
<tr><td>Causative Agent</td><td>CareConnect-DCH-AllergyIntolerance-2.code</td><td>Required</td><td>Where a SNOMED CT code for a Causative Agent is not available, then code.text should be used to contain a text representation of the Causative Agent</td></tr>
<tr><td>Description of Reaction</td><td>CareConnect-DCH-AllergyIntolerance-2.reaction.manifestation.coding</td><td>Optional</td><td>When no code manifestation coded value is available, a description of the manifestation should be entered in manifestation.code.text</td></tr>
<tr><td>Type Of Reaction</td><td>CareConnect-DCH-AllergyIntolerance-2.type</td><td>Optional</td><td></td></tr>
<tr><td>Certainty</td><td>CareConnect-DCH-AllergyIntolerance-2.verificationStatus</td><td>Optional</td><td>Use the mapping defined in the verificationStatus valueSet (http://hl7.org/fhir/ValueSet/allergy-verification-status) to find the actual values to flow). When no code for Certainty is available (or a more detailed certainty description is needed), a free text representation in CareConnect-DCH-AllergyIntolerance-2.note should be sent*</td></tr>
<tr><td>Severity</td><td>CareConnect-DCH-AllergyIntolerance-2.reaction.manifestation.severity</td><td>Optional</td><td>Use the mapping defined in the CareConnect-ReactionEventSeverity-1 valueSet (https://fhir.hl7.org.uk/STU3/ValueSet/CareConnect-ReactionEventSeverity-1) to find the actual values to flow. When no code for Severity is available (or a more detailed severity description is needed), a free text representation in CareConnect-DCH-AllergyIntolerance-2.note should be sent*</td></tr>
<tr><td>Evidence</td><td>CareConnect-DCH-AllergyIntolerance-2.note*</td><td>Optional</td><td></td></tr>
<tr><td>Date First Experienced</td><td>CareConnect-DCH-AllergyIntolerance.onset</td><td>Optional</td><td></td></tr>
<tr><td>Comment</td><td>CareConnect-DCH-AllergyIntolerance-2.note*</td><td>Optional</td><td></td></tr>
</table>                                                                                                  
*Rather than split descriptive and user entered text across a number of note fields the AllergyIntolerance.note element is used as the single notes field to convey all qualifiers and user-entered text associated with the allergy or intolerance in a single place. Qualifiers and values expressed as text MUST be appropriately labelled and formatted and where user notes have been entered against explicit fields such as certainty then appropriate labels MUST be used.


### Reference Linkage Diagram ###

This Linkage diagram defines the required references that SHALL be made between resources within the DCH Event Message bundle. It includes both Header and Payload resources (but omits the DCH-Bundle-1 wrapper).

<img src="images/explore/Allergies.png">


### Allergies and Adverse Reactions Bundle XML Example ###

<script src="https://gist.github.com/IOPS-DEV/54940bfde3502a05a30decdea3f1e049.js"></script>

### Allergies and Adverse Reactions Bundle JSON Example ###

<script src="https://gist.github.com/IOPS-DEV/00c4c6ce83e3ae51d7abbcdae6a3ce49.js"></script> 