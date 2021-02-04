![OASIS Logo](http://docs.oasis-open.org/templates/OASISLogo-v3.0.png)
-------

# OpenC2 Actuator Profile for Endpoint Detection and Response Version 1.0

## Committee Specification Draft 01

## 02 December 2020

<!-- URI list start (commented out except during publication by OASIS TC Admin)

#### This version:
https://docs.oasis-open.org/openc2/ap-edr/v1.0/csd01/ap-edr-v1.0-csd01.md (Authoritative) \
https://docs.oasis-open.org/openc2/ap-edr/v1.0/csd01/ap-edr-v1.0-csd01.html \
https://docs.oasis-open.org/openc2/ap-edr/v1.0/csd01/ap-edr-v1.0-csd01.pdf

#### Previous version:
N/A

#### Latest version:
https://docs.oasis-open.org/openc2/ap-edr/v1.0/ap-edr-v1.0.md (Authoritative) \
https://docs.oasis-open.org/openc2/ap-edr/v1.0/ap-edr-v1.0.html \
https://docs.oasis-open.org/openc2/ap-edr/v1.0/ap-edr-v1.0.pdf

URI list end (commented out except during publication by OASIS TC Admin) -->

#### Technical Committee:
[OASIS Open Command and Control (OpenC2) TC](https://www.oasis-open.org/committees/openc2/)

#### Chairs:
Joe Brule (jmbrule@nsa.gov), [National Security Agency](https://www.nsa.gov/) \
Duncan Sparrell (duncan@sfractal.com), [sFractal Consulting LLC](http://www.sfractal.com/)

#### Editors:
Vasileios Mavroeidis (vasileim@ifi.uio.no), [University of Oslo](https://www.uio.no/english/) \
Martin Evandt (martifev@ifi.uio.no), [University of Oslo](https://www.uio.no/english/)

#### Additional artifacts:
This prose specification is one component of a Work Product that also includes:
* XML schemas: (list file names or directory name)
* Other parts (list titles and/or file names)
* `(Note: Any normative computer language definitions that are part of the Work Product, such as XML instances, schemas and Java(TM) code, including fragments of such, must be (a) well formed and valid, (b) provided in separate plain text files, (c) referenced from the Work Product; and (d) where any definition in these separate files disagrees with the definition found in the specification, the definition in the separate file prevails. Remove this note before submitting for publication.)`

#### Related work:
This specification replaces or supersedes:
* Specifications replaced by this specification (include hyperlink, preferably to HTML format)

This specification is related to:
* Related specifications (include hyperlink, preferably to HTML format) \
`(remove "Related work" section or the "replaces" or "related" subsections if no entries)`

#### Abstract:
Open Command and Control (OpenC2) is a concise and extensible language to enable the command and control of cyber defense components, subsystems and/or systems in a manner that is agnostic of the underlying products, technologies, transport mechanisms or other aspects of the implementation. Endpoint detection and response technologies provide a means for continuous monitoring and analysis to more readily identify, detect, and prevent advanced threats. This OpenC2 Actuator Profile defines the Actions, Targets, Specifiers and Options that are consistent with the Version 1.0 of the OpenC2 Language Specification ([OpenC2-Lang-v1.0]) in the context of command and control of various endpoint detection and response technologies.

#### Status:
This document was last revised or approved by the OASIS Open Command and Control (OpenC2) TC on the above date. The level of approval is also listed above. Check the "Latest version" location noted above for possible later revisions of this document. Any other numbered Versions and other technical work produced by the Technical Committee (TC) are listed at https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=openc2#technical.

TC members should send comments on this specification to the TC's email list. Others should send comments to the TC's public comment list, after subscribing to it by following the instructions at the "Send A Comment" button on the TC's web page at https://www.oasis-open.org/committees/openc2/.

This specification is provided under the [Non-Assertion](https://www.oasis-open.org/policies-guidelines/ipr#Non-Assertion-Mode) Mode of the OASIS  R Policy, the mode chosen when the Technical Committee was established. For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the Intellectual Property Rights section of the TC's web page (https://www.oasis-open.org/committees/openc2/ipr.php).

Note that any machine-readable content ([Computer Language Definitions](https://www.oasis-open.org/policies-guidelines/tc-process#wpComponentsCompLang)) declared Normative for this Work Product is provided in separate plain text files. In the event of a discrepancy between any such plain text file and display content in the Work Product's prose narrative document(s), the content in the separate plain text file prevails.

#### Key words:
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 [[RFC2119](#rfc2119)] and [[RFC8174](#rfc8174)] when, and only when, they appear in all capitals, as shown here.

#### Citation format:
When referencing this specification the following citation format should be used:

**[AP-EDR-v1.0]**

_OpenC2 Actuator Profile for Endpoint Detection and Response Version 1.0_. Edited by Vasileios Mavroeidis and Martin Evandt. 02 December 2020. OASIS Committee Specification Draft 01. https://docs.oasis-open.org/openc2/ap-edr/v1.0/csd01/ap-edr-v1.0-csd01.html. Latest version: https://docs.oasis-open.org/openc2/ap-edr/v1.0/ap-edr-v1.0.html.

-------

## Notices
Copyright © OASIS Open 2020. All Rights Reserved.

Distributed under the terms of the OASIS [IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr).

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs.

For complete copyright information please see the Notices section in the Appendix.

-------

# Table of Contents
[[TOC will be inserted here]]

-------

# 1 Introduction

_The content in this section is non-normative, except where it is marked normative._

OpenC2 is a suite of specifications that enables command and control of cyber defense systems and components. OpenC2 typically uses a request-response paradigm where a _Command_ is encoded by a _Producer_ (managing application) and transferred to a _Consumer_ (managed device or virtualized function) using a secure transfer protocol, and the Consumer can respond with status and any requested information.

OpenC2 allows the application producing the commands to discover the set of capabilities supported by the managed devices. These capabilities permit the managing application to adjust its behavior to take advantage of the features exposed by the managed device. The capability definitions can be easily extended in a noncentralized manner, allowing standard and non-standard capabilities to be defined with semantic and syntactic rigor.

## 1.1 IPR Policy
This specification is provided under the [Non-Assertion](https://www.oasis-open.org/policies-guidelines/ipr#Non-Assertion-Mode) Mode of the [OASIS IPR Policy](https://www.oasis-open.org/policies-guidelines/ipr), the mode chosen when the Technical Committee was established. For information on whether any patents have been disclosed that may be essential to implementing this specification, and any offers of patent licensing terms, please refer to the Intellectual Property Rights section of the TC's web page ([https://www.oasis-open.org/committees/openc2/ipr.php](https://www.oasis-open.org/committees/openc2/ipr.php)).

## 1.2 Terminology

_This section is normative._

* **Action**: The task or activity to be performed (e.g., 'deny').
* **Actuator**: The function performed by the Consumer that executes the Command (e.g., 'Endpoint Response').
* **Argument**: A property of a Command that provides additional information on how to perform the Command, such as date/time, periodicity, duration, etc.
* **Command**: A Message defined by an Action-Target pair that is sent from a Producer and received by a Consumer.
* **Consumer**: A managed device / application that receives Commands. Note that a single device / application can have both Consumer and Producer capabilities.
* **Message**: A content- and transport-independent set of elements conveyed between Consumers and Producers.
* **Producer**: A manager application that sends Commands.
* **Response**: A Message from a Consumer to a Producer acknowledging a Command or returning the requested resources or status to a previously received Command.
* **Specifier**: A property or field that identifies a Target or Actuator to some level of precision.
* **Target**: The object of the Action, i.e., the Action is performed on the Target (e.g., device).

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [[RFC2119]](#rfc2119) and [[RFC8174]](#rfc8174) when, and only when, they appear in all capitals, as shown here.

## 1.3 Normative References

The following documents are referenced in such a way that some or all of their content constitutes requirements of this document.

(Reference sources:
For references to IETF RFCs, use the approved citation formats at:  
http://docs.oasis-open.org/templates/ietf-rfc-list/ietf-rfc-list.html.  
For references to W3C Recommendations, use the approved citation formats at:  
http://docs.oasis-open.org/templates/w3c-recommendations-list/w3c-recommendations-list.html.  
Remove this note before submitting for publication.)

###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, <https://www.rfc-editor.org/info/rfc2119>.

###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, <https://www.rfc-editor.org/info/rfc8174>.

###### [OpenC2-HTTPS-v1.0]
_Specification for Transfer of OpenC2 Messages via HTTPS Version 1.0_. Edited by David Lemire. Latest version: http://docs.oasis-open.org/openc2/open-impl-https/v1.0/open-impl-https-v1.0.html

###### [Winnt.h-registry-types]
_Registry Value Types_. Microsoft Windows documentation, <https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry-value-types>


## 1.4 Non-Normative References

###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.

## 1.5 Document Conventions
### 1.5.1 Naming Conventions
* [[RFC2119]](#rfc2119)/[[RFC8174]](#rfc8174) key words (see [Section 1.2](#12-terminology)) are in all uppercase.
* All property names and literals are in lowercase, except when referencing canonical names defined in another standard (e.g., literal values from an IANA registry).
* Words in property names are separated with an underscore (_), while words in string enumerations and type names are separated with a hyphen (-).
* The term "hyphen" used here refers to the ASCII hyphen or minus character, which in Unicode is "hyphen-minus", U+002D.

### 1.5.2 Font Colors and Style
The following color, font and font style conventions are used in this document:

* A fixed width font is used for all type names, property names, and literals.
* Property names are in bold style – **'created_at'**.
* All examples in this document are expressed in JSON. They are in fixed width font, with straight quotes, black text and a light shaded background, and 4-space indentation. JSON examples in this document are representations of JSON Objects. They should not be interpreted as string literals. The ordering of object keys is insignificant. Whitespace before or after JSON structural characters in the examples are insignificant [[RFC8259]](#rfc8259).
* Parts of the example may be omitted for conciseness and clarity. These omitted parts are denoted with ellipses (...).

Example:

```json
{
    "action": "deny",
    "target": {
        "file": {
            "hashes": {
                "sha256": "22fe72a34f006ea67d26bb7004e2b6941b5c3953d43ae7ec24d41b1a928a6973"
            }
        }
    }
}
```

## 1.6 Overview
In general, there are two types of participants involved in the exchange of OpenC2 Messages, as depicted in Figure 1-1:
1. **Producers**: A Producer is an entity that creates Commands to provide instruction to one or more systems to act in accordance with the content of the Command. A Producer may receive and process Responses in conjunction with a Command.
2. **Consumers**: A Consumer is an entity that receives and may act upon a Command. A Consumer may create Responses that provide any information captured or necessary to send back to the Producer.

![OpenC2 Message Exchange](images/image_1.png)

**Figure 1-1. OpenC2 Message Exchange**

OpenC2 is a suite of specifications for Producers and Consumers to command and execute cyber defense functions. These specifications include the OpenC2 Language Specification, Actuator Profiles, and Transfer Specifications. The OpenC2 Language Specification and Actuator Profile specifications focus on the language content and meaning at the Producer and Consumer of the Command and Response while the transfer specifications focus on the protocols for their exchange.
* The **OpenC2 Language Specification ([[OpenC2-Lang-v1.0]](#openc2-lang-v10))** provides the semantics for the essential elements of the language, the structure for Commands and Responses, and the schema that defines the proper syntax for the language elements that represents the Command or Response.
* **OpenC2 Actuator Profiles** specify the subset of the OpenC2 language relevant in the context of specific Actuator functions. Cyber defense components, devices, systems and/or instances may (in fact are likely to) implement multiple Actuator profiles. Actuator profiles extend the language by defining Specifiers that identify the Actuator to the required level of precision. Actuator Profiles may define Command Arguments and Targets that are relevant and/or unique to those Actuator functions.
* **OpenC2 Transfer Specifications** utilize existing protocols and standards to implement OpenC2 in specific environments. These standards are used for communications and security functions beyond the scope of the language, such as message transfer encoding, authentication, and end-to-end transport of OpenC2 Messages.

The OpenC2 Language Specification defines a language used to compose Messages for command and control of cyber defense systems and components. A Message consists of a header and a payload (_defined_ as a Message body in the OpenC2 Language Specification Version 1.0 and _specified_ in one or more Actuator profiles).

The language defines two payload structures:

1. **Command**: An instruction from one system known as the Producer, to one or more systems, the Consumer(s), to act on the content of the Command.
2. **Response**: Any information sent back to the Producer as a result of the Command.

OpenC2 implementations integrate the related OpenC2 specifications described above with related industry specifications, protocols, and standards. Figure 1-2 depicts the relationships among OpenC2 specifications, and their relationships to other industry standards and environment-specific implementations of OpenC2. Note that the layering of implementation aspects in the diagram is notional, and not intended to preclude any particular approach to implementing the needed functionality (for example, the use of an application-layer message signature function to provide message source authentication and integrity).

![OpenC2 Documentation and Layering Model](images/image_2.png)

**Figure 1-2. OpenC2 Documentation and Layering Model**

OpenC2 is conceptually partitioned into four layers as shown in Table 1-1.

**Table 1-1. OpenC2 Protocol Layers**

| Layer | Examples |
| :--- | :--- |
| Function-Specific Content | Actuator Profiles<br>(standard and extensions) |
| Common Content | Language Specification<br>[[OpenC2-Lang-v1.0]](#openc2-lang-v10) |
| Message | Transfer Specifications<br>([[OpenC2-HTTPS-v1.0]](#openc2-https-v10), OpenC2-over-CoAP, ...) |
| Secure Transport | HTTPS, CoAP, MQTT, OpenDXL, ... |

* The **Secure Transport** layer provides a communication path between the Producer and the Consumer. OpenC2 can be layered over any standard transport protocol.
* The **Message** layer provides a transfer- and content-independent mechanism for conveying Messages. A transfer specification maps transfer-specific protocol elements to a transfer-independent set of message elements consisting of content and associated metadata.
* The **Common Content** layer defines the structure of Commands and Responses and a set of common language elements used to construct them.
* The **Function-specific Content** layer defines the language elements used to support a particular cyber defense function. An Actuator profile defines the implementation conformance requirements for that function. Producers and Consumers will support one or more profiles.

The components of a Command are an Action (what is to be done), a Target (what is being acted upon), an optional Actuator (what is performing the command), and Command Arguments, which influence how the Command is to be performed. An Action coupled with a Target is sufficient to describe a complete Command. Though optional, the inclusion of an Actuator and/or Command Arguments provides additional precision to a Command.

The components of a Response are a numerical status code, an optional status text string, and optional results. The format of the results, if included, depend on the type of Response being transferred.

## 1.7 Goal
The goal of the OpenC2 Language Specification is to provide a language for interoperating between functional elements of cyber defense systems. This language used in conjunction with OpenC2 Actuator Profiles and OpenC2 Transfer Specifications allows for vendor-agnostic cybertime response to attacks.

The Integrated Adaptive Cyber Defense (IACD) framework defines a collection of activities, based on the traditional OODA (Observe–Orient–Decide–Act) Loop [[IACD]](#iacd):

* Sensing:  gathering of data regarding system activities
* Sense Making:  evaluating data using analytics to understand what's happening
* Decision Making:  determining a course-of-action to respond to system events
* Acting:  Executing the course-of-action

The goal of OpenC2 is to enable coordinated defense in cyber-relevant time between decoupled blocks that perform cyber defense functions. OpenC2 focuses on the Acting portion of the IACD framework; the assumption that underlies the design of OpenC2 is that the sensing/analytics have been provisioned and the decision to act has been made. This goal and these assumptions guide the design of OpenC2:

* **Technology Agnostic:**  The OpenC2 language defines a set of abstract atomic cyber defense actions in a platform and implementation agnostic manner
* **Concise:**  A Command is intended to convey only the essential information required to describe the action required and can be represented in a very compact form for communications-constrained environments
* **Abstract:**  Commands and Responses are defined abstractly and can be encoded and transferred via multiple schemes as dictated by the needs of different implementation environments
* **Extensible:**  While OpenC2 defines a core set of Actions and Targets for cyber defense, the language is expected to evolve with cyber defense technologies, and permits extensions to accommodate new cyber defense technologies.

## 1.8 Purpose and Scope

An 'Endpoint Detection and Response' (EDR) system is a security mechanism which identifies malicious behaviours by recording system activities and comparing them to sets of signatures or heuristics. EDR systems facilitate in digital forensics and incident response by storing and indexing said events, as well as provide functionality to respond to security incidents as they pertain to actively exploited, infected or vulnerable endpoints.

This Actuator profile specifies the set of Actions, Targets, Specifiers, and Command Arguments that integrates EDR functionality with the Open Command and Control (OpenC2) Command set. Through this Command set, cyber security orchestrators may gain visibility into and provide control over the EDR functionality in a manner that is independent of the instance of the EDR function.

All components, devices and systems that provide EDR functionality will implement the OpenC2 Actions, Targets, Specifiers and Arguments identified as required in this document. Actions that are applicable, but not necessarily required, for EDR will be identified as optional.

The purpose of this document is to:

* Identify the required and optional OpenC2 Actions for Actuators with EDR functionality
* Identify the required and optional Target types for each Action in the EDR class of Actuators
* Identify Actuator-Specifiers and Arguments for each Action/Target pair that are applicable and/or unique to the EDR class of Actuators
* Annotate each Action/Target pair with a justification and example, and provide sample OpenC2 Commands to a EDR with corresponding Responses

This EDR profile:

* Does not define or implement Actions beyond those defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10)
* Is consistent with Version 1.0 of the OpenC2 Language Specification

Cyber defense systems that are utilizing OpenC2 may require the following components to implement the EDR profile:

* OpenC2 Producers: Devices that send Commands, receive Responses, and manage the execution of Commands involving one or more EDR or other Actuators with EDR capability. The OpenC2 Producer needs _a prior_ knowledge of which Commands the Actuator can process and execute, therefore must understand the profiles for any device that it intends to command
* OpenC2 Consumers: Devices or instances that provide endpoint detection and response functions. Typically these are Actuators that execute the cyber defense function, but could be orchestrators (i.e., a device or instance that forwards Commands to the Actuator)

## 1.9 Glossary

### 1.9.1 Definitions of terms
Sensor: A data capturing utility within the context of an EDR.

### 1.9.2 Acronyms and abbreviations
EDR: Endpoint Detection and Response

ED: Endpoint Detection

ER: Endpoint Response


-------

# 2 OpenC2 Language Binding for Endpoint Response

_This section is normative_

This section defines the set of Actions, Targets, Specifiers, and Arguments that are meaningful in the context of Endpoint Response (ER). This section also describes the appropriate format for the status and properties of a Response frame. This section is organized into three major subsections; Command Components, Response Components and Commands.

Extensions to the Language Specification are defined in accordance with [[OpenC2-Lang-v1.0]](#openc2-lang-v10), Section 3.1.5, where:

1. The unique name of the EDR schema is `oasis-open.org/openc2/v1.0/ap-edr`
2. The namespace identifier (nsid) referring to the EDR schema is:  `edr`
3. The definitions of and conformance requirements for these types are contained in this document

## 2.1 OpenC2 Command Components
The components of an OpenC2 Command include Actions, Targets, Actuators and associated Arguments and Specifiers. Appropriate aggregation of the components will define a Command-body that is meaningful in the context of an EDR.

This specification identifies the applicable components of an OpenC2 Command. The components of an OpenC2 Command include:

* Action:  A subset of the Actions defined in the OpenC2 Language Specification that are meaningful in the context of an EDR.
    * This profile SHALL NOT define Actions that are external to Version 1.0 of the [OpenC2 Language Specification](#openc2-lang-v10)
    * This profile MAY augment the definition of the Actions in the context of an EDR
    * This profile SHALL NOT define Actions in a manner that is inconsistent with version 1.0 of the OpenC2 Language Specification
* Target:  A subset of the Targets and Target-Specifiers defined in Version 1.0 of the OpenC2 Language Specification that are meaningful in the context of EDR and one Target (and its associated Specifier) that is defined in this specification
* Arguments:  A subset of the Arguments defined in the Language Specification and a set of Arguments defined in this specification
* Actuator:  A set of specifiers defined in this specification that are meaningful in the context of EDR

### 2.1.1 Actions
Table 2.1.1-1 presents the OpenC2 Actions defined in version 1.0 of the Language Specification which are meaningful in the context of an ER Actuator. The particular Action/Target pairs that are required or are optional are presented in [Section 2.3](#23-openc2-commands).

**Table 2.1.1-1. Actions Applicable to ER**

**_Type: Action (Enumerated)_**

| ID | Name | Description |
| :--- | :--- | :--- |
| 7 | **contain** | Isolate a device from communicating with other devices on a network. |
| 8 | **allow** | Un-isolate a previously isolated device. |
| 9 | **start** | Initiate a process, application, system, or activity. |
| 10 | **stop** | Halt a system or end an activity. |
| 11 | **restart** | Restart a device, system, or process. |
| 16 | **update** | Instructs the Actuator to retrieve, install, process, and operate in accordance with a software update, reconfiguration, or other update. |
| 19 | **create** | Add a new entity of a known type. (E.g., registry entry, file) |
| 20 | **delete** | Remove an entity (E.g., registry entry, file) |



### 2.1.2 Targets
Table 2.1.2-1 summarizes the Targets defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) as they relate to EDR functionality. Table 2.1.2-2 summarizes the Targets that are defined in this specification.

#### 2.1.2.1 Common Targets
Table 2.1.2-1 lists the Targets defined in the OpenC2 Language Specification that are applicable to EDR . The particular Action/Target pairs that are required or are optional are presented in [Section 2.3](#23-openc2-commands).

**Table 2.1.2-1. Targets Applicable to ER**

**_Type: Target (Choice)_**

| ID | Name | Type | Description |
| :--- | :--- | :--- | :--- |
| 3 | **device** | Device | The properties of a device |
| 9 | **features** | Features | A set of items such as Action/Target pairs, profiles versions, options that are supported by the Actuator. The Target is used with the query Action to determine an Actuator's capabilities |
| 10 | **file** | File | The properties of a file|
| 18 | **process** | Process | Common properties of an instance of a computer program as executed on an operating system |

#### 2.1.2.2 ER Targets
The list of common Targets is extended to include the additional Targets defined in this section and referenced with the edr namespace.

**Table 2.1.2-2. Targets Unique to ER**

**_Type: Target (Choice)_**

| ID | Name | Type | Description |
| :--- | :--- | :--- | :--- |
| 1101 | **registry_entry** | Registry-Entry | A registry entry applicable to Windows Operating Systems |



## 2.1.3 Type Definitions

### 2.1.3.1 Target Types

#### 2.1.3.1.1 Registry Entry

**_Type: Registry Entry (Record{1..*})_**

| ID | Name | Type | # | Description |
| :---: | :---: | :---: | :---: | :--- |
| 1 | **path** | String | 1 | The absolute path of the registry entry including the hive and optionally the key. If the key is not included then the key property MUST be populated.|
| 2 | **key** | String | 0\.\.1 | The registry key. They key may contain subkeys referenced with a backslash to indicate hierarchy. |
| 3 | **type** | String | 1 | The registry value type as defined in the Microsoft Windows [[Winnt.h header]](#winnth-registry-types) |
| 4 | **value** | String | 0\.\.1 | The value of the registry key. The actuator is responsible to format the value in accordance with the defined type. |

### 2.1.4 Command Arguments
Arguments provide additional precision to a Command by including information such as how, when, or where a Command is to be executed. Table 2.1.3-1 summarizes the Command Arguments defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) as they relate to ER functionality.

## 2.2 OpenC2 Response Components
Response messages originate from the Actuator as a result of a Command.

Responses associated with required Actions MUST be implemented. Implementations that include optional Actions MUST implement the RESPONSE associated with the implemented Action. Additional details regarding the Command and associated Response are captured in [Section 2.3](#23-openc2-commands). Examples are provided in [Annex A](#annex-a-sample-commands).

### 2.2.1 Common Results
Table 2.2.1-1 lists the Response Results properties defined in the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) that are applicable to EDR.

### 2.2.3 Response Status Codes
Table 2.2.1-2 lists the Response Status Codes defined in the OpenC2 Language Specification that are applicable to EDR.

**Table 2.2.1-2. Response Status Codes**

**_Type: Status-Code (Enumerated.ID)_**

| Value | Description |
| :--- | :--- |
| 102 | Processing. Command received but action not necessarily complete. |
| 200 | OK. |
| 400 | Bad Request. Unable to process Command, parsing error. |
| 500 | Internal Error. |

## 2.3 OpenC2 Commands

An OpenC2 Command consists of an Action/Target pair and associated Specifiers and Arguments. This section enumerates the allowed Commands and presents the associated Responses.

Table 2.3-1 defines the Commands that are valid in the context of the ER profile. An Action (the top row in Table 2.3-1) paired with a Target (the first column in Table 2.3-1) defines a valid Command. The subsequent subsections provide the property tables applicable to each OpenC2 Command.

**Table 2.3-1. Command Matrix**

|                    |Allow|Query|Delete|Update|Contain|Restart|Start|Stop |Create|
|:---                |:---:|:---:|:---: |:---: | :---: | :---: |:---:|:---:|:---: |
| **device** 		 |valid|     |      |      | valid | valid |     |valid|      |     
| **file** 			 |     |     |      |valid | valid |       |     |     |      |     
| **process** 		 |     |     |      |      | valid | valid |valid|valid|      |     
| **registry_entry** |     |     |valid |valid |       |       |     |     |valid |      
| **features** 		 |     |valid|      |      |       |       |     |     |      |     

-------

# Appendix F. Notices

Copyright © OASIS Open 2020. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr) may be found at the OASIS website.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.

As stated in the OASIS IPR Policy, the following three paragraphs in brackets apply to OASIS Standards Final Deliverable documents (Committee Specification, Candidate OASIS Standard, OASIS Standard, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this OASIS Standards Final Deliverable. OASIS may include such claims on its website, but disclaims any obligation to do so.\]

\[OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this OASIS Standards Final Deliverable or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Technical Committee can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Standards Final Deliverable, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.\]

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark for above guidance.
