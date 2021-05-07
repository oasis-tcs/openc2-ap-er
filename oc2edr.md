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

#### Related work:
This specification is related to:
* Related specifications (include hyperlink, preferably to HTML format) \
`(remove "Related work" section or the "replaces" or "related" subsections if no entries)`

#### Abstract:
Open Command and Control (OpenC2) is a concise and extensible language to enable the command and control of cyber defense components, subsystems and/or systems in a manner that is agnostic of the underlying products, technologies, transport mechanisms or other aspects of the implementation. Endpoint Detection and Response (EDR) technologies provide a means for continuous endpoint monitoring and analysis to more readily identify, detect, mitigate and remediate, or prevent advanced threats. This Actuator Profile defines OpenC2 Actions, Targets, Specifiers, and Command Arguments in the context of command and control of EDR technologies. The EDR specification is consistent with Version 1.0 of the OpenC2 Language Specification ([OpenC2-Lang-v1.0]).

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
- [1 Introduction](#1-introduction)
  - [1.1 IPR Policy](#11-ipr-policy)
  - [1.2 Terminology](#12-terminology)
  - [1.3 Glossary](#13-glossary)
    - [1.3.1 Definitions of terms](#131-definitions-of-terms)
    - [1.3.2 Acronyms and abbreviations](#132-acronyms-and-abbreviations)
  - [1.4 Document Conventions](#14-document-conventions)
    - [1.4.1 Naming Conventions](#141-naming-conventions)
    - [1.4.2 Font Colors and Style](#142-font-colors-and-style)
  - [1.5 Overview](#15-overview)
  - [1.6 Goal](#16-goal)
  - [1.7 Purpose and Scope](#17-purpose-and-scope)
- [2 OpenC2 Language Binding for Endpoint Response](#2-openc2-language-binding-for-endpoint-response)
  - [2.1 OpenC2 Command Components](#21-openc2-command-components)
    - [2.1.1 Actions](#211-actions)
    - [2.1.2 Targets](#212-targets)
    - [2.1.3 Type Definitions](#213-type-definitions)
    - [2.1.4 Command Arguments](#214-command-arguments)
    - [2.1.5 Actuator Specifiers](#215-actuator-specifiers)
  - [2.2 OpenC2 Response Components](#22-openc2-response-components)
    - [2.2.1 Response Status Codes](#221-response-status-codes)
  - [2.3 OpenC2 Commands](#23-openc2-commands)
    - [2.3.1 Query](#231-query)
    - [2.3.2 Deny](#232-deny)
    - [2.3.3 Contain](#233-contain)
    - [2.3.4 Allow](#234-allow)
    - [2.3.5 Start](#235-start)
    - [2.3.6 Stop](#236-stop)
    - [2.3.7 Restart](#237-restart)
    - [2.3.8 Set](#238-set)
    - [2.3.9 Update](#239-update)
    - [2.3.10 Create](#2310-create)
    - [2.3.11 Delete](#2311-delete)
- [3 Conformance statements](#3-conformance-statements)
  - [3.1 Clauses Pertaining to the OpenC2 Producer Conformance Target](#31-clauses-pertaining-to-the-openc2-producer-conformance-target)
    - [3.1.1 Conformance Clause 1: Baseline OpenC2 Producer](#311-conformance-clause-1-baseline-openc2-producer)
    - [3.1.2 Conformance Clause 2: Contain Device Producer](#312-conformance-clause-2-contain-device-producer)
    - [3.1.3 Conformance Clause 3: device-containment Producer](#313-conformance-clause-3-device-containment-producer)
    - [3.1.4 Conformance Clause 4: Stop Device Producer](#314-conformance-clause-4-stop-device-producer)
    - [3.1.5 Conformance Clause 5: Restart Device Producer](#315-conformance-clause-5-restart-device-producer)
    - [3.1.6 Conformance Clause 6: Deny File Producer](#316-conformance-clause-6-deny-file-producer)
    - [3.1.7 Conformance Clause 7: Contain File Producer](#317-conformance-clause-7-contain-file-producer)
    - [3.1.8 Conformance Clause 8: Allow/Deny IPv4 Net Producer](#318-conformance-clause-8-allowdeny-ipv4-net-producer)
    - [3.1.9 Conformance Clause 9: Allow/Deny IPv6 Net Producer](#319-conformance-clause-9-allowdeny-ipv6-net-producer)
    - [3.1.10 Conformance Clause 10: Set IPv4 Net Producer](#3110-conformance-clause-10-set-ipv4-net-producer)
    - [3.1.11 Conformance Clause 11: Set IPv6 Net Producer](#3111-conformance-clause-11-set-ipv6-net-producer)
    - [3.1.12 Conformance Clause 12: Process Producer](#3112-conformance-clause-12-process-producer)
    - [3.1.13 Conformance Clause 13: Registry Entry Producer](#3113-conformance-clause-13-registry-entry-producer)
    - [3.1.14 Conformance Clause 14: Account Producer](#3114-conformance-clause-14-account-producer)
    - [3.1.15 Conformance Clause 15: Account-Status Producers](#3115-conformance-clause-15-account-status-producers)
    - [3.1.16 Conformance Clause 16: Service Producer](#3116-conformance-clause-16-service-producer)
  - [3.2 Clauses Pertaining to the OpenC2 Consumer Conformance Target](#32-clauses-pertaining-to-the-openc2-consumer-conformance-target)
    - [3.2.1 Conformance Clause 17: Baseline OpenC2 Consumer](#321-conformance-clause-17-baseline-openc2-consumer)
    - [3.2.2 Conformance Clause 18: Contain Device Consumer](#322-conformance-clause-18-contain-device-consumer)
    - [3.2.3 Conformance Clause 19: device-containment Consumer](#323-conformance-clause-19-device-containment-consumer)
    - [3.2.4 Conformance Clause 20: Stop Device Consumer](#324-conformance-clause-20-stop-device-consumer)
    - [3.2.5 Conformance Clause 21: Restart Device Consumer](#325-conformance-clause-21-restart-device-consumer)
    - [3.2.6 Conformance Clause 22: Deny File Consumer](#326-conformance-clause-22-deny-file-consumer)
    - [3.2.7 Conformance Clause 23: Contain File Consumer](#327-conformance-clause-23-contain-file-consumer)
    - [3.2.8 Conformance Clause 24: Allow/Deny IPv4 Net Consumer](#328-conformance-clause-24-allowdeny-ipv4-net-consumer)
    - [3.2.9 Conformance Clause 25: Allow/Deny IPv6 Net Consumer](#329-conformance-clause-25-allowdeny-ipv6-net-consumer)
    - [3.2.10 Conformance Clause 26: Set IPv4 Net Consumer](#3210-conformance-clause-26-set-ipv4-net-consumer)
    - [3.2.11 Conformance Clause 27: Set IPv6 Net Consumer](#3211-conformance-clause-27-set-ipv6-net-consumer)
    - [3.2.12 Conformance Clause 28: Process Consumer](#3212-conformance-clause-28-process-consumer)
    - [3.2.13 Conformance Clause 29: Registry Entry Consumer](#3213-conformance-clause-29-registry-entry-consumer)
    - [3.2.14 Conformance Clause 30: Account Consumer](#3214-conformance-clause-30-account-consumer)
    - [3.2.15 Conformance Clause 31: Account-Status Consumer](#3215-conformance-clause-31-account-status-consumer)
    - [3.2.16 Conformance Clause 32: Service Consumer](#3216-conformance-clause-32-service-consumer)
- [Annex A: Sample Commands](#annex-a-sample-commands)
  - [A.1 deny, contain and allow](#a1-deny-contain-and-allow)
    - [A.1.1 Ban a binary by hash on every endpoint](#a11-ban-a-binary-by-hash-on-every-endpoint)
    - [A.1.2 Port isolate a specific endpoint](#a12-port-isolate-a-specific-endpoint)
    - [A.1.3 Allow unrestricted app execution on a group of endpoints](#a13-allow-unrestricted-app-execution-on-a-group-of-endpoints)
  - [A.2 Set](#a2-set)
    - [A.2.1 Set an account on a specific endpoint to be enabled](#a21-set-an-account-on-a-specific-endpoint-to-be-enabled)
    - [A.2.1 Set accounts on a group of endpoints to be disabled](#a21-set-accounts-on-a-group-of-endpoints-to-be-disabled)
- [Appendix A. References](#appendix-a-references)
  - [A.1 Normative References](#a1-normative-references)
  <!-- [A.2 Informative References](#a2-informative-references) -->
- [Appendix B. Acknowledgments](#appendix-b-acknowledgments)
  - [B.1 Participants](#b1-participants)
- [Appendix C. Revision History](#appendix-c-revision-history)
- [Appendix D. Notices](#appendix-d-notices)

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

## 1.3 Glossary

### 1.3.1 Definitions of terms
Sensor: A data capturing utility within the context of an EDR.

### 1.3.2 Acronyms and abbreviations
_This section is non-normative_

| Term | Expansion |
|:---|:---|
| EDR | Endpoint Detection and Response |
| ED | Endpoint Detection |
| ER | Endpoint Response |


## 1.4 Document Conventions
### 1.4.1 Naming Conventions
* [[RFC2119]](#rfc2119)/[[RFC8174]](#rfc8174) key words (see [Section 1.2](#12-terminology)) are in all uppercase.
* All property names and literals are in lowercase, except when referencing canonical names defined in another standard (e.g., literal values from an IANA registry).
* Words in property names are separated with an underscore (_), while words in string enumerations and type names are separated with a hyphen (-).
* The term "hyphen" used here refers to the ASCII hyphen or minus character, which in Unicode is "hyphen-minus", U+002D.

### 1.4.2 Font Colors and Style
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

## 1.5 Overview
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

## 1.6 Goal
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

## 1.7 Purpose and Scope

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

-------

# 2 OpenC2 Language Binding for Endpoint Response

_This section is normative_

This section defines the set of Actions, Targets, Specifiers, and Arguments that are meaningful in the context of Endpoint Response (ER). This section also describes the appropriate format for the status and properties of a Response frame. This section is organized into three major subsections; Command Components, Response Components and Commands.

Extensions to the Language Specification are defined in accordance with [[OpenC2-Lang-v1.0]](#openc2-lang-v10), Section 3.1.5, where:

1. The unique name of the EDR schema is `oasis-open.org/openc2/v1.0/ap-edr`
2. The namespace identifier (nsid) referring to the EDR schema is:  `edr`
3. The definitions and conformance requirements for these types are contained in this document

## 2.1 OpenC2 Command Components
The components of an OpenC2 Command include Actions, Targets, Actuators and associated Arguments and Specifiers. Appropriate aggregation of the components will define a Command-body that is meaningful in the context of an EDR.

This specification identifies the applicable components of an OpenC2 Command. The components of an OpenC2 Command include:

* Action:  A subset of the Actions defined in the OpenC2 Language Specification that are meaningful in the context of an EDR.
    * This profile SHALL NOT define Actions that are external to Version 1.0 of the [OpenC2 Language Specification](#openc2-lang-v10)
    * This profile MAY augment the definition of the Actions in the context of an EDR
    * This profile SHALL NOT define Actions in a manner that is inconsistent with version 1.0 of the OpenC2 Language Specification
* Target:  A subset of the Targets and Target-Specifiers defined in Version 1.0 of the OpenC2 Language Specification that are meaningful in the context of EDR and three Targets (and their associated Specifiers) that are defined in this specification
* Arguments:  A subset of the Arguments defined in the Language Specification and a set of Arguments defined in this specification
* Actuator:  A set of specifiers defined in this specification that are meaningful in the context of EDR

### 2.1.1 Actions
Table 2.1.1-1 presents the OpenC2 Actions defined in Version 1.0 of the Language Specification which are meaningful in the context of an ER Actuator. The combinations of Action/Target pairs that are valid for Endpoint Response purposes are presented in [Section 2.3](#23-openc2-commands).

**Table 2.1.1-1. Actions Applicable to ER**

**_Type: Action (Enumerated)_**

| ID | Name | Description |
| :--- | :--- | :--- |
| 3 | **query** | Query the EDR actuator for a list of available features. |
| 6 | **deny** | Deny a process or service from being executed on the endpoint. |
| 7 | **contain** | Isolate a device from communicating with other devices on a network, quarantine a file. |
| 8 | **allow** | Un-isolate a previously isolated device. |
| 9 | **start** | Initiate a process, application, system, or activity. |
| 10 | **stop** | Halt a system or end an activity. |
| 11 | **restart** | Restart a device, system, or process. |
| 15 | **set** | Change a value, configuration, or state of a managed entity (e.g., registry value, account). |
| 16 | **update** | Instructs the Actuator to retrieve, install, process, and operate in accordance with a software update, reconfiguration, or other update. |
| 19 | **create** | Add a new entity of a known type (e.g., registry entry, file). |
| 20 | **delete** | Remove an entity (e.g., registry entry, file). |


### 2.1.2 Targets
Table 2.1.2-1 summarizes the Targets defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) as they relate to EDR functionality. Table 2.1.2-2 summarizes the Targets that are defined in this specification.

#### 2.1.2.1 Common Targets
Table 2.1.2-1 lists the Targets defined in the OpenC2 Language Specification that are applicable to EDR . The particular Action/Target pairs that are required or are optional are presented in [Section 2.3](#23-openc2-commands).

**Table 2.1.2-1. Language Specification Targets Applicable to ER**

**_Type: Target (Choice)_**

| ID | Name | Type | Description |
| :--- | :--- | :--- | :--- |
| 3 | **device** | Device | The properties of a device. |
| 9 | **features** | Features | A set of items such as Action/Target pairs, profiles versions, options that are supported by the Actuator. The Target is used with the query Action to determine an Actuator's capabilities. |
| 10 | **file** | File | The properties of a file. |
| 13 | **ipv4_net** | IPv4-Net | An IPv4 address range including CIDR prefix length. |
| 14 | **ipv6_net** | IPv6-Net | An IPv6 address range including prefix length. |
| 18 | **process** | Process | Common properties of an instance of a computer program as executed on an operating system. |

#### 2.1.2.2 ER Targets
The list of common Targets is extended to include the additional Targets defined in this section and referenced with the `edr` namespace.

**Table 2.1.2-2. Targets Unique to ER**

**_Type: Target (Choice)_**

| ID | Name | Type | Description |
| :--- | :--- | :--- | :--- |
| 1101 | **registry_entry** | Registry-Entry | A registry entry applicable to Windows Operating Systems. |
| 1102 | **account** | Account | A user account on an endpoint. |
| 1103 | **service** | Service | A collection of one or more files which holds state information on an endpoint (configurations, execution on boot, utilization of windows registry, or similar). |

#### 2.1.2.3 External Namespace Targets
The list of external namespace Targets extend the Target list to include Targets from other Actuator Profiles.

**Table 2.1.2-3 Stateless Packet Filter Targets Applicable to ER**
| ID | Name | Type | Description |
| :--- | :--- | :--- | :--- |
| 13 | **ipv4_net** | IPv4-Net | An IPv4 address range including CIDR prefix length. |
| 14 | **ipv6_net** | IPv6-Net | An IPv6 address range including prefix length. |


### 2.1.3 Type Definitions

#### 2.1.3.1 Target Types

**Table 2.1.3-1. Registry Entry**

**_Type: Registry-Entry (Record{1..*})_**

| ID | Name | Type | # | Description |
| :--- | :--- | :--- | :---: | :--- |
| 1 | **path** | String | 1 | The absolute path of the registry entry including the hive and optionally the key. If the key is not included then the key property MUST be populated.|
| 2 | **key** | String | 0\.\.1 | The registry key. They key may contain subkeys referenced with a backslash to indicate hierarchy. |
| 3 | **type** | String | 1 | The registry value type as defined in [[Winnt.h header]](#winnth-registry-types). |
| 4 | **value** | String | 0\.\.1 | The value of the registry key. The actuator is responsible to format the value in accordance with the defined type. |

**Table 2.1.3-2. Account**

**_Type: Account (Map[1..*])_**

| ID | Name | Type | # | Description |
| :--- | :--- | :--- | :---: | :--- |
| 1 | **uid** | String | 0\.\.1 | The unique identifier of the account.|
| 2 | **account_name** | String | 0\.\.1 | The chosen display name of the account. |
| 3 | **directory** | String | 0\.\.1 | The path to the account's home directory. |


**Table 2.1.3-3. Service**

**_Type: Service (Map[1..*])_**

| ID | Name | Type | # | Description |
| :--- | :--- | :--- | :---: | :--- |
| 1 | **executable** | File | 0\.\.1 | The executable file that starts the service. |
| 2 | **registry_entries** | Registry-Entry | 0\.\.1 | The registry entries associated with this service. |
| 3 | **process** | process | 0\.\.1 | The process associated with the service (if it is running). |

### 2.1.4 Command Arguments
Arguments provide additional precision to a Command by including information such as how, when, or where a Command is to be executed. Table 2.1.3-1 summarizes the Command Arguments defined in Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10) as they relate to ER functionality.

**Table 2.1.4-1. Command Arguments applicable to ER**

**_Type: Args (Map)_**

| ID | Name | Type | # | Description |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **start_time** | Date-Time | 0..1 | The specific date/time to initiate the Action. |
| 2 | **stop_time** | Date-Time | 0..1 | The specific date/time to terminate the Action.|
| 3 | **duration** | Duration | 0..1 | The length of time for an Action to be in effect. |
| 4 | **response_requested** | Response-Type | 0..1 | The type of Response required for the Action: `none`, `ack`, `status`, `complete`. |

**Table 2.1.4-1. Command Arguments Unique to EDR**

**_Type: Args (Map)_**

| ID | Name | Type | # | Description |
| :--- | :--- | :--- | :--- | :--- |
| 1201 | **account_status** | Account-Status | 1 | Specifies whether the account is enabled or disabled. |
| 1202 | **device_containment** | Device-Containment | 1 | Specifies whether or not to isolate the host on a VLAN or restrict application execution. |

**_Type: Account-Status (Enumerated)_**

| ID | Name | Description |
| :--- | :--- | :--- |
| 1 | **enabled** | Enable the account and render it available on the endpoint. |
| 2 | **disabled** | Disable the account and render it unavailable on the endpoint. |

**_Type: Device-Containment (Enumerated)_**

| ID | Name | Description |
| :--- | :--- | :--- |
| 1 | **port_isolation** | Isolate the host in a VLAN .|
| 2 | **app_restriction** | Restrict the execution of applications to only those that are signed by a trusted party (e.g., Microsoft only). |
| 3 | **disable_nic** | Disable the Network Interface Controller(s) on the endpoint. |

### 2.1.5 Actuator Specifiers
An Actuator is the entity that provides the functionality and performs the Action. The Actuator executes the Action on the Target. In the context of this profile, the Actuator is the EDR and the presence of one or more Specifiers further refine which Actuator(s) shall execute the Action.

The Actuator Specifiers defined in this document are referenced under the `edr` namespace.

**Table 2.1.5-1. EDR Specifiers**

**_Type: Specifiers (Map)_**

| ID | Name | Type | # | Description |
| :--- | :--- | :--- | :--- | :--- |
| 1 | **hostname** | String | 0..1 | A hostname for a particular device with EDR functionality. [RFC1123]](#rfc1123) |
| 2 | **sensor_id** | String | 0..1 | Unique identifier for a particular EDR sensor. |
| 3 | **named_group** | arrayOf(String) | 0..1 | User defined collection of devices with EDR sensors installed. |


## 2.2 OpenC2 Response Components
Response messages originate from the Actuator as a result of a Command.

Responses associated with required Actions MUST be implemented. Implementations that include optional Actions MUST implement the RESPONSE associated with the implemented Action. Additional details regarding the Commands and associated Responses are captured in [Section 2.3](#23-openc2-commands). Examples are provided in [Annex A](#annex-a-sample-commands).

### 2.2.1 Response Status Codes
Table 2.2.1-1 lists the Response Status Codes defined in the OpenC2 Language Specification that are applicable to ER.

**Table 2.2.1-1. Response Status Codes**

**_Type: Status-Code (Enumerated.ID)_**

| Value | Description |
| :--- | :--- |
| 102 | Processing. The Command was received but the action is not necessarily completed. |
| 200 | OK. The Command was received and the action was performed. |
| 400 | Bad Request. Unable to process Command, parsing error. |
| 500 | Internal Error. |
| 501 | Not implemented. For "response_requested" value "complete", one of the following MAY apply:<br> * Target not supported<br> * Option not supported<br> * Command not supported |

## 2.3 OpenC2 Commands

An OpenC2 Command consists of an Action/Target pair and associated Specifiers and Arguments. This section enumerates the allowed Commands and presents the associated Responses.

Table 2.3-1 defines the Commands that are valid in the context of the ER profile. An Action (the top row in Table 2.3-1) paired with a Target (the first column in Table 2.3-1) defines a valid Command.

**Table 2.3-1. Command Matrix**
|                    |query|deny |contain|allow|start|stop |restart|set  |update|create|delete|
|:---                |:---:|:---:|:---:  |:---:|:---:|:---:| :---: |:---:|:---: |:---: |:---: |
| **device** 		 |     |     | valid |valid|     |valid| valid |     |      |      |      |
| **features** 		 |valid|     |       |     |     |     |       |     |      |      |      |
| **file** 			 |     |valid| valid |valid|valid|     |       |     |valid |      |valid |
| **ipv4_net**		 |     |valid|       |valid|     |     |       |valid|      |      |      |
| **ipv6_net**		 |     |valid|       |valid|     |     |       |valid|      |      |      |
| **process** 		 |     |     |       |     |valid|valid| valid |     |      |      |      |
| **registry_entry** |     |     |       |     |     |     |       |valid|      |valid |valid |
| **account** 		 |     |     |       |     |     |     |       |valid|      |      |      |
| **service** 		 |     |     |       |     |     |valid|       |     |      |      |valid |

Table 2.3-2 defines the Command Arguments that are allowed for a particular Command by the ER profile. An Argument (the top row in Table 2.3-2) paired with a Command (the first column in Table 2.3-2) defines an allowable combination.

**Table 2.3-2. Command Arguments Matrix**
|                         | **response_requested** | **Device-Containment** | **Account-Status**| 
|:---                     |:---:                   |:---:                   |:---:              |
|contain device			      |valid                   |valid                   |                   |
|contain file			        |valid                   |                        |                   |
|allow device			        |valid                   |                        |                   |
|allow file				        |valid                   |                        |                   |
|start process			      |valid                   |                        |                   |
|stop device			        |valid                   |                        |                   |
|stop file                |valid                   |                        |                   |
|stop service			        |valid                   |                        |                   |
|restart device			      |valid                   |                        |                   |
|restart process		      |valid                   |                        |                   |
|set ipv4-net			        |valid                   |                        |                   |
|set ipv6-net			        |valid                   |                        |                   |
|set edr:registry_entry	  |valid                   |                        |                   |
|set edr:account		      |valid                   |                        |valid              |
|create edr:registry_entry|valid                   |                        |                   |
|delete file			        |valid                   |                        |                   |
|delete edr:registry_entry|valid                   |                        |                   |
|delete service			      |valid                   |                        |                   |

### 2.3.1 Query
The valid Target type, associated Specifiers, and Options are summarized in [Section 2.3.3.1](#2331-query-features).

#### 2.3.1.1 Query features
The 'query features' Command MUST be implemented in accordance with Version 1.0 of the [[OpenC2-Lang-v1.0]](#openc2-lang-v10).

### 2.3.2 Deny

OpenC2 Consumers that receive a 'deny' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'deny' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'Command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.2.1 Deny file
Prevents the execution of a file.

OpenC2 Consumers that receive a 'deny file' Command:

* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access file' in the status text

#### 2.3.2.2 slpf:Deny ipv4 net
Must be implemented in accordance with [SLPF Deny Command](#SLPF-Deny) as well as the [SLPF Conformance Statements](#SLPF-Conformance).
#### 2.3.2.3 slpf:Deny ipv6 net
Must be implemented in accordance with [SLPF Deny Command](#SLPF-Deny) as well as the [SLPF Conformance Statements](#SLPF-Conformance).

### 2.3.3 Contain
OpenC2 Consumers that receive a 'contain' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'contain' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'Command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.3.1 Contain device
Limits the functionalities of an endpoint in relation to application execution and/or network communications. Table 2.3-2 summarizes the Command Arguments that apply to all of the Commands consisting of the 'contain' Command and the 'device' Target. The Producer and Consumer of the command MUST support the edr:device_containment Command Argument as defined in [Section 2.1.4](#214-command-arguments)

OpenC2 Producers that send 'contain device' Commands:

* MUST populate the Command Arguments field with a 'Device-Containment' argument

OpenC2 Consumers that receive a 'contain Device' Command:

* but the Command Arguments field is not populated with a 'Device-Containment' argument
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'Containment type argument not populated' in the status text
* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access device' in the status text

#### 2.3.3.2 Contain file
Quarantines a file, deleting it from the original location and creating a non-executable copy in a hidden folder.

OpenC2 Consumers that receive a 'contain file' Command:

* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access file' in the status text

### 2.3.4 Allow
'Allow' can be treated as the mathematical complement to 'deny' Actions as well as 'contain' Actions. Table 2.3-2 summarizes the Command Arguments that apply to all of the Commands consisting of the 'deny' and 'contain' Actions and their valid Target types.

OpenC2 Consumers that receive a 'allow' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'allow' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'command not supported' in the status text
    * MAY respond with status code 500


#### 2.3.4.1 Allow device
Removes a device from containment. This command SHOULD NOT be issued on an endpoint which has not previously received a 'contain device' command first.

OpenC2 Consumers that receive a 'allow device' Command:

* but the device is not contained
    * SHOULD respond with status code 400
    * SHOULD respond with 'device not contained' in the status text
* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access device' in the status text


#### 2.3.4.2 Allow file
Removes execution prevention from a file or takes a file out of quarantine. This command SHOULD NOT be issued towards a file which has not previously received a 'deny file' or a 'contain file' command first.

OpenC2 Consumers that receive a 'allow file' Command:

* but the file is not contained
    * SHOULD respond with status code 400
    * SHOULD respond with 'file not contained' in the status text
* but the file is not denied
    * SHOULD respond with status code 400
    * SHOULD respond with 'file not denied' in the status text
* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access file' in the status text

#### 2.3.4.3 slpf:Allow ipv4 net
Must be implemented in accordance with [SLPF Allow Command](#SLPF-Allow) as well as the [SLPF Conformance Statements](#SLPF-Conformance).
#### 2.3.4.4 slpf:Allow ipv6 net
Must be implemented in accordance with [SLPF Allow Command](#SLPF-Allow) as well as the [SLPF Conformance Statements](#SLPF-Conformance).

### 2.3.5 Start
OpenC2 Consumers that receive a 'start' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'start' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.5.1 Start process
Executes a process.

OpenC2 Producers that send 'start process' Commands
* MUST populate the 'executable' property of the Command Target

OpenC2 Consumers that receive a 'start process' Command:

* but the 'executable' property of the Command Target is not populated
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'executable Target property not specified' in the status text
* but cannot access the file specified in the process 'executable' property
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access file' in the status text

#### 2.3.5.2 Start file
Instructs the Actuator to retrieve, install, process, and operate a file.

OpenC2 Consumers that receive a 'start file' Commands:
* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access file' in the status text

### 2.3.6 Stop
OpenC2 Consumers that receive a 'stop' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'stop <target>' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.6.1 Stop device
Shuts down an endpoint.

OpenC2 Consumers that receive a 'stop device' Command:

* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access device' in the status text

#### 2.3.6.2 Stop process
Stops an active process. A 'process' Target MUST contain at least one property.
#### 2.3.6.3 Stop edr:service
Stops the running process associated with a service and prevents it from running again should the endpoint reboot.

OpenC2 Consumers that choose to implement the 'stop edr:service' Command MUST include all steps that are required for the disable service procedure such as ending the process of the service, editing configuration files/registry entries, restart/reboot of the host device etc. The end state shall be that the service is stopped, and that it does not restart upon device boot.

### 2.3.7 Restart
OpenC2 Consumers that receive a 'restart' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'restart' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.7.1 Restart device
Restarts an endpoint.

OpenC2 Consumers that receive a 'restart device' Command:

* but cannot access the device specified in the device Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access device' in the status text

#### 2.3.7.2 Restart process
Restarts a process. A 'process' Target MUST contain at least one property.

### 2.3.8 Set
OpenC2 Consumers that receive a 'set' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'set' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.8.1 Set ipv4_net
Sets the IPv4 address of the endpoint to the specified Target value.

OpenC2 Producers that send 'set ipv4_net' Commands:
* MUST include an IPv4 address withouth the CIDR prefix-length, or have it set to 32

OpenC2 Consumers thet receive 'set ipv4_net' Commands
* but the CIDR prefix-length is set to a value other than 32
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'IPv4 address not set to a single address' in the status text

#### 2.3.8.2 Set ipv6_net
Sets the IPv6 address of the endpoint to the specified Target value.

OpenC2 Producers that send 'set ipv4_net' Commands:
* MUST include an IPv4 address withouth the prefix-length, or have it set to 128

OpenC2 Consumers thet receive a 'set ipv4_net' Command:
* but the CIDR prefix-length is set to a value other than 128
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'IPv6 address not set to a single address' in the status text


#### 2.3.8.3 Set edr:registry_entry
Sets the 'value' property of a Registry Entry. The 'type' property MUST be populated and MUST conform to the registry entry types as defined in [Winnt.h header](#winnth-registry-types).

OpenC2 Producers that send 'set edr:registry_entry' Commands:
* MUST include the 'path' property of the edr:registry_entry Target
* MUST refer to the registry key
    * SHOULD refer to the registry key using the 'key' property
    * MAY refer to the registry key by including the key in the 'path' property

OpenC2 Consumers that receive a'set edr:registry_entry' Command:

* but cannot access the registry entry specified in the registry entry Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access registry entry' in the status text


#### 2.3.8.4 Set edr:account
Sets the status of the account to be either enabled or disabled. The producer and consumer of the command MUST support the edr:account_status Command Argument as defined in [Section 2.1.4](#214-command-arguments)

OpenC2 Producers that send 'set edr:account' Commands:
* MUST populate the Command Arguments field with a Account-Status argument

OpenC2 Consumers that receive a 'set edr:account' Command:
* but the Command Arguments field is not populated with a Account-Status argument
    * MUST NOT respond with status code OK/200
    * SHOULD respond with status code 400
    * MAY respond with status code 500
    * SHOULD respond with 'account-status type argument not populated' in the status text
* but cannot access the account specified in the edr:account Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access account' in the status text

### 2.3.9 Update
#### 2.3.9.1 Update file
The 'update file' Command is used to replace or update files such as configuration files, rule sets, etc. Implementation of the update file Command is OPTIONAL. OpenC2 Consumers that choose to implement the 'update file' Command MUST include all steps that are required for the update file procedure such as retrieving the file(s), install the file(s), restart/ reboot the device etc. The end state shall be that the EDR operates with the new file at the conclusion of the 'update file' Command. The atomic steps that take place are implementation specific.

### 2.3.10 Create
#### 2.3.10.1 Create edr:registry_entry
Creates a registry entry in the specified path. The 'type' property MUST be populated and MUST conform to the registry entry types as defined in [Winnt.h header](#winnth-registry-types).

OpenC2 Producers that send 'create edr:registry_entry' Commands:
* MUST include the 'path' property of the edr:registry entry Target
* MUST refer to the registry key
    * SHOULD refer to the registry key using the 'key' property
    * MAY refer to the registry key by including the key in the 'path' property

OpenC2 Consumers that receive a 'create edr:registry_entry' Command:
* but cannot access the registry entry specified in the registry entry Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access registry entry' in the status text

### 2.3.11 Delete
OpenC2 Consumers that receive a 'delete' Command:

* but cannot parse or process the Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 400
    * MAY respond with the 500 status code
* but do not support the 'delete <target>' Command
    * MUST NOT respond with a OK/200
    * SHOULD respond with status code 501
    * SHOULD respond with 'command not supported' in the status text
    * MAY respond with status code 500

#### 2.3.11.1 Delete file
Deletes the specified file from an endpoint.

OpenC2 Consumers that receive a'delete file' Command:
* but cannot access the file specified in the file Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access file' in the status text

#### 2.3.11.2 Delete edr:registry_entry
Deletes a registry entry. The 'type' property MUST be populated and MUST conform to the registry entry types as defined in [Winnt.h header](#winnth-registry-types).

OpenC2 Producers that send 'create edr:registry_entry' Commands:
* MUST include the 'path' property of the edr:registry entry Target
* MUST refer to the registry key
    * SHOULD refer to the registry key using the 'key' property
    * MAY refer to the registry key by including the key in the 'path' property

OpenC2 Consumers that receive a 'create edr:registry_entry' Command:
* but cannot access the registry entry specified in the registry entry Target
    * MUST respond with status code 500
    * SHOULD respond with 'cannot access registry entry' in the status text


#### 2.3.11.3 Delete edr:service
Deletes the registry key that executes a service on system boot.

OpenC2 Consumers that choose to implement the 'delete edr:service' Command MUST include all steps that are required for the delete service procedure such as ending the process of the service, removing the executable and other files, removing configuration files/registry entries, restart/reboot of the host device etc. The end state shall be that the service is stopped and removed from the endpoint.


# 3 Conformance statements
_This section is normative_
This section identifies the requirements for twenty-two conformance profiles as they pertain to two conformance targets. The two conformance targets are OpenC2 Producers and OpenC2 Consumers (as defined in [Section 1.8](#18-purpose-and-scope) of this specification).

## 3.1 Clauses Pertaining to the OpenC2 Producer Conformance Target
All OpenC2 Producers that are conformant to this specification MUST satisfy Conformance Clause 1 and MAY satisfy one or more of Conformance Clauses 2 through 11.

### 3.1.1 Conformance Clause 1: Baseline OpenC2 Producer
An OpenC2 Producer satisfies Baseline OpenC2 Producer conformance if:
* 3.1.1.1 **MUST** support JSON serialization of OpenC2 Commands that are syntactically valid in accordance with the property tables presented in [Section 2.1](#21-openc2-command-components)
* 3.1.1.2 All serializations **MUST** be implemented in a manner such that the serialization validates against and provides a one-to-one mapping to the property tables in [Section 2.1](#21-openc2-command-components) of this specification
* 3.1.1.3 **MUST** support the use of a Transfer Specification that is capable of delivering authenticated, ordered, lossless and uniquely identified OpenC2 messages
* 3.1.1.4 **SHOULD** support the use of one or more published OpenC2 Transfer Specifications which identify underlying transport protocols such that an authenticated, ordered, lossless, delivery of uniquely identified OpenC2 messages is provided as referenced in [Section 1](#1-introduction) of this specification
* 3.1.1.5 **MUST** be conformant with Version 1.0 of the OpenC2 Language Specification
* 3.1.1.6 **MUST** implement the 'query features' Command in accordance with the normative text provided in Version 1.0 of the OpenC2 Language Specification
* 3.1.1.7 **MUST** implement the 'response_requested' Command Argument as a valid option for any Command
* * 3.1.1.8 **MUST** conform to at least one of the following conformance clauses in this specification:
   * TBD
   * TBD

### 3.1.2 Conformance Clause 2: Contain Device Producer
An OpenC2 Producer satisfies 'Contain Device Producer' conformance if:
* 3.1.2.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.2.2 **MUST** implement the 'contain device' Command in accordance with [Section 2.3.3.1](#2331-contain-device) of this specification
* 3.1.2.3 **MUST** implement the 'allow device' Command in accordance with [Section 2.3.4.1](#2341-allow-device) of this specification

### 3.1.3 Conformance Clause 3: device-containment Producer
An OpenC2 Producer satisfies 'Device-Containment Producer' conformance if:
* 3.1.3.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.3.2 **MUST** implement the 'device-containment' Command Argument as a valid option for the 'contain device' command in accordance with [Section 2.3.3.1](#2331-contain-device) of this specification

### 3.1.4 Conformance Clause 4: Stop Device Producer
An OpenC2 Producer satisfies 'Stop Device Producer' conformance if:
#### 3.1.4.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
#### 3.1.4.2 **MUST** implement the 'stop device' Command in accordance with [Section 2.3.6.1](#2361-stop-device) of this specification

### 3.1.5 Conformance Clause 5: Restart Device Producer
An OpenC2 Producer satisfies 'Restart Device Producer' conformance if:
* 3.1.5.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.5.2 **MUST** implement the 'restart device' Command in accordance with [Section 2.3.7.1](#2371-restart-device) of this specification

### 3.1.6 Conformance Clause 6: Deny File Producer
An OpenC2 Producer satisfies 'Deny File Producer' conformance if:
* 3.1.6.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.6.2 **MUST** implement the 'deny file' Command in accordance with [Section 2.3.2.1](#2321-deny-file) of this specification
* 3.1.6.3 **MUST** implement the 'allow file' Command in accordance with [Section 2.3.4.2](#2342-allow-file) of this specification

### 3.1.7 Conformance Clause 7: Contain File Producer
An OpenC2 Producer satisfies 'Contain File Producer' conformance if:
* 3.1.2.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.6.2 **MUST** implement the 'contain file' Command in accordance with [Section 2.3.3.2](#2332-contain-file) of this specification
* 3.1.6.3 **MUST** implement the 'allow file' Command in accordance with [Section 2.3.4.2](#2342-allow-file) of this specification

### 3.1.8 Conformance Clause 8: Allow/Deny IPv4 Net Producer
An OpenC2 Producer satisfies 'Allow/Deny IPv4 Net Producer' conformance if:
* 3.1.8.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of [the conformance section of the Stateless Packet Filter specification](#slpf-conformance)
* 3.1.8.2 MUST implement the 'allow ipv4_net' Command in accordance with Section [2.3.1 of the Stateless Packet Filter specification](#slpf-allow)
* 3.1.8.3 MUST implement the 'deny ipv4_net' Command in accordance with Section [2.3.2 of the Stateless Packet Filter specification](#slpf-deny)

### 3.1.9 Conformance Clause 9: Allow/Deny IPv6 Net Producer
An OpenC2 Producer satisfies 'Allow/Deny IPv6 Net Producer' conformance if:
* 3.1.9.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of [the conformance section of the Stateless Packet Filter specification](#slpf-conformance)
* 3.1.9.2 MUST implement the 'allow ipv6_net' Command in accordance with Section [2.3.1 of the Stateless Packet Filter specification](#slpf-allow)
* 3.1.9.3 MUST implement the 'deny ipv6_net' Command in accordance with Section [2.3.2 of the Stateless Packet Filter specification](#slpf-deny)

### 3.1.10 Conformance Clause 10: Set IPv4 Net Producer
An OpenC2 Producer satisfies 'Set IPv4 Net Producer' conformance if:
* 3.1.10.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.10.2 **MUST** implement the 'set ipv4_net' Command in accordance with [Section 2.3.8.1](#2381-set-ipv4-net) of this specification

### 3.1.11 Conformance Clause 11: Set IPv6 Net Producer
An OpenC2 Producer satisfies 'Set IPv6 Net Producer' conformance if:
* 3.1.11.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.11.2 **MUST** implement the 'set ipv6_net' Command in accordance with [Section 2.3.8.2](#2382-set-ipv6-net) of this specification

### 3.1.12 Conformance Clause 12: Process Producer
An OpenC2 Producer satisfies 'Process Producer' conformance if:
* 3.1.12.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.12.2 **MUST** implement the 'start process' Command in accordance with [Section 2.3.5.1](#2351-start-process) of this specification
* 3.1.12.3 **MUST** implement the 'stop process' Command in accordance with [Section 2.3.6.2](#2362-stop-process) of this specification
* 3.1.12.4 **MUST** implement the 'restart process' Command in accordance with [Section 2.3.7.2](#2372-restart-process) of this specification

### 3.1.13 Conformance Clause 13: Registry Entry Producer
An OpenC2 Producer satisfies 'Registry Entry Producer' conformance if:
* 3.1.13.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.13.2 **MUST** implement the 'set registry_entry' Command in accordance with [Section 2.3.8.3](#2383-set-edrregistry-entry) of this specification
* 3.1.13.3 **MUST** implement the 'create registry_entry' Command in accordance with [Section 2.3.10.1](#23101-create-edrregistry-entry) of this specification
* 3.1.13.4 **MUST** implement the 'delete registry_entry' Command in accordance with [Section 2.3.11.2](#23112-delete-edrregistry-entry) of this specification

### 3.1.14 Conformance Clause 14: Account Producer
An OpenC2 Producer satisfies 'Account Producer' conformance if:
* 3.1.14.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.14.2 **MUST** implement the 'set account' Command in accordance with [Section 2.3.8.4](#2384-set-edraccount) of this specification

### 3.1.15 Conformance Clause 15: Account-Status Producers
An OpenC2 Producer satisfies 'Account-Status Producers' conformance if:
* 3.1.15.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.15.2 **MUST** implement the 'account-status' Command Argument as a valid option for the 'set account' command in accordance with [Section 2.3.8.4](#2384-set-edraccount) of this specification

### 3.1.16 Conformance Clause 16: Service Producer
An OpenC2 Producer satisfies 'Service Producer' conformance if:
* 3.1.16.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.1.16.2 **MUST** implement the 'stop service' Command in accordance with [Section 2.3.6.3](#2363-stop-edrservice) of this specification
* 3.1.16.2 **MUST** implement the 'delete service' Command in accordance with [Section 2.3.11.3](#23113-delete-edrservice) of this specification


## 3.2 Clauses Pertaining to the OpenC2 Consumer Conformance Target
All OpenC2 Consumers that are conformant to this specification MUST satisfy Conformance Clause 12 and MAY satisfy one or more of Conformance Clauses 13 through 22.

### 3.2.1 Conformance Clause 17: Baseline OpenC2 Consumer
An OpenC2 Consumer satisfies Baseline OpenC2 Consumer conformance if:
* 3.2.1.1 **MUST** support JSON serialization of OpenC2 Commands that are syntactically valid in accordance with the property tables presented in [Section 2.1](#21-openc2-command-components)
* 3.2.1.2 All serializations **MUST** be implemented in a manner such that the serialization validates against and provides a one-to-one mapping to the property tables in [Section 2.1](#21-openc2-command-components) of this specification
* 3.2.1.3 **MUST** support the use of a Transfer Specification that is capable of delivering authenticated, ordered, lossless and uniquely identified OpenC2 messages
* 3.2.1.4 **SHOULD** support the use of one or more published OpenC2 Transfer Specifications which identify underlying transport protocols such that an authenticated, ordered, lossless, delivery of uniquely identified OpenC2 messages is provided as referenced in [Section 1](#1-introduction) of this specification
* 3.2.1.5 **MUST** be conformant with Version 1.0 of the OpenC2 Language Specification
* 3.2.1.6 **MUST** implement the 'query features' Command in accordance with the normative text provided in version 1.0 of the OpenC2 Language Specification
* 3.2.1.7 **MUST** implement the 'response_requested' Command Argument as a valid option for any Command
    * 3.2.1.7.1 All Commands received with a 'response_requested' argument set to 'none' **MUST** process the Command and **MUST NOT** send a Response. This criteria supersedes all other normative text as it pertains to Responses
    * 3.2.1.7.2 All Commands received without the 'response_requested' argument **MUST** process the Command and Response in a manner that is consistent with "response_requested":"complete"
* 3.2.1.8 **MUST** conform to at least one of the following conformance clauses in this specification:
    * TBD
    * TBD

### 3.2.2 Conformance Clause 18: Contain Device Consumer
An OpenC2 Producer satisfies 'Contain Device Consumer' conformance if:
* 3.2.2.1 **MUST** meet all of conformance criteria identified in Conformance Clause 17 of this specification
* 3.2.2.2 **MUST** implement the 'contain device' Command in accordance with [Section 2.3.3.1](#2331-contain-device) of this specification
* 3.2.2.3 **MUST** implement the 'allow device' Command in accordance with [Section 2.3.4.1](#2341-allow-device) of this specification

### 3.2.3 Conformance Clause 19: device-containment Consumer
An OpenC2 Producer satisfies 'Device-Containment Consumer' conformance if:
* 3.2.3.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.3.2 **MUST** implement the 'device-containment' Command Argument as a valid option for the 'contain device' command in accordance with [Section 2.3.3.1](#2331-contain-device) of this specification

### 3.2.4 Conformance Clause 20: Stop Device Consumer
An OpenC2 Producer satisfies 'Stop Device Consumer' conformance if:
* 3.2.4.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.4.2 **MUST** implement the 'stop device' Command in accordance with [Section 2.3.6.1](#2361-stop-device) of this specification

### 3.2.5 Conformance Clause 21: Restart Device Consumer
An OpenC2 Producer satisfies 'Restart Device Consumer' conformance if:
* 3.2.5.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.5.2 **MUST** implement the 'restart device' Command in accordance with [Section 2.3.7.1](#2371-restart-device) of this specification

### 3.2.6 Conformance Clause 22: Deny File Consumer
An OpenC2 Producer satisfies 'Deny File Consumer' conformance if:
* 3.2.6.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.6.2 **MUST** implement the 'deny file' Command in accordance with [Section 2.3.2.1](#2321-deny-file) of this specification
* 3.2.6.3 **MUST** implement the 'allow file' Command in accordance with [Section 2.3.4.2](#2342-allow-file) of this specification

### 3.2.7 Conformance Clause 23: Contain File Consumer
An OpenC2 Producer satisfies 'Contain File Consumer' conformance if:
* 3.2.2.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.6.2 **MUST** implement the 'contain file' Command in accordance with [Section 2.3.3.2](#2332-contain-file) of this specification
* 3.2.6.3 **MUST** implement the 'allow file' Command in accordance with [Section 2.3.4.2](#2342-allow-file) of this specification

### 3.2.8 Conformance Clause 24: Allow/Deny IPv4 Net Consumer
An OpenC2 Producer satisfies 'Allow/Deny IPv4 Net Consumer' conformance if:
* 3.2.8.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of [the conformance section of the Stateless Packet Filter specification](#slpf-conformance)
* 3.2.8.2 MUST implement the 'allow ipv4_net' Command in accordance with Section [2.3.1 of the Stateless Packet Filter specification](#slpf-allow)
* 3.2.8.3 MUST implement the 'deny ipv4_net' Command in accordance with Section [2.3.2 of the Stateless Packet Filter specification](#slpf-deny)

### 3.2.9 Conformance Clause 25: Allow/Deny IPv6 Net Consumer
An OpenC2 Producer satisfies 'Allow/Deny IPv6 Net Consumer' conformance if:
* 3.2.9.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of [the conformance section of the Stateless Packet Filter specification](#slpf-conformance)
* 3.2.9.2 MUST implement the 'allow ipv6_net' Command in accordance with Section [2.3.1 of the Stateless Packet Filter specification](#slpf-allow)
* 3.2.9.3 MUST implement the 'deny ipv6_net' Command in accordance with Section [2.3.2 of the Stateless Packet Filter specification](#slpf-deny)

### 3.2.10 Conformance Clause 26: Set IPv4 Net Consumer
An OpenC2 Producer satisfies 'Set IPv4 Net Consumer' conformance if:
* 3.2.10.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.10.2 **MUST** implement the 'set ipv4_net' Command in accordance with [Section 2.3.8.1](#2381-set-ipv4-net) of this specification

### 3.2.11 Conformance Clause 27: Set IPv6 Net Consumer
An OpenC2 Producer satisfies 'Set IPv6 Net Consumer' conformance if:
* 3.2.11.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.11.2 **MUST** implement the 'set ipv6_net' Command in accordance with [Section 2.3.8.2](#2382-set-ipv6-net) of this specification

### 3.2.12 Conformance Clause 28: Process Consumer
An OpenC2 Producer satisfies 'Process Consumer' conformance if:
* 3.2.12.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.12.2 **MUST** implement the 'start process' Command in accordance with [Section 2.3.5.1](#2351-start-process) of this specification
* 3.2.12.3 **MUST** implement the 'stop process' Command in accordance with [Section 2.3.6.2](#2362-stop-process) of this specification
* 3.2.12.4 **MUST** implement the 'restart process' Command in accordance with [Section 2.3.7.2](#2372-restart-process) of this specification

### 3.2.13 Conformance Clause 29: Registry Entry Consumer
An OpenC2 Producer satisfies 'Registry Entry Consumer' conformance if:
* 3.2.13.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.13.2 **MUST** implement the 'set registry_entry' Command in accordance with [Section 2.3.8.3](#2383-set-edrregistry-entry) of this specification
* 3.2.13.3 **MUST** implement the 'create registry_entry' Command in accordance with [Section 2.3.10.1](#23101-create-edrregistry-entry) of this specification
* 3.2.13.4 **MUST** implement the 'delete registry_entry' Command in accordance with [Section 2.3.11.2](#23112-delete-edrregistry-entry) of this specification

### 3.2.14 Conformance Clause 30: Account Consumer
An OpenC2 Producer satisfies 'Account Consumer' conformance if:
* 3.2.14.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.14.2 **MUST** implement the 'set account' Command in accordance with [Section 2.3.8.4](#2384-set-edraccount) of this specification

### 3.2.15 Conformance Clause 31: Account-Status Consumer
An OpenC2 Producer satisfies 'Account-Status Consumer' conformance if:
* 3.2.15.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.15.2 **MUST** implement the 'account-status' Command Argument as a valid option for the 'set account' command in accordance with [Section 2.3.8.4](#2384-set-edraccount) of this specification

### 3.2.16 Conformance Clause 32: Service Consumer
An OpenC2 Producer satisfies 'Service Consumer' conformance if:
* 3.2.16.1 **MUST** meet all of conformance criteria identified in Conformance Clause 1 of this specification
* 3.2.16.2 **MUST** implement the 'stop service' Command in accordance with [Section 2.3.6.3](#2363-stop-edrservice) of this specification
* 3.2.16.2 **MUST** implement the 'delete service' Command in accordance with [Section 2.3.11.3](#23113-delete-edrservice) of this specification

-------
# Annex A: Sample Commands

_This section is non-normative_

This section will summarize and provide examples of OpenC2 Commands as they pertain to EDR systems. The sample Commands will be encoded in verbose JSON.

## A.1 deny, contain and allow

### A.1.1 Ban a binary by hash on every endpoint

**Command:**

```json
{
  "action": "deny",
  "target": {
    "file": {
      "hash": "0a73291ab5607aef7db23863cf8e72f55bcb3c273bb47f00edf011515aeb5894"
    }
  },
  "actuator": {
    "edr": {}
  }
}
```
**Responses:**

Case One: the Actuator successfully issued the deny.

```json
{
  "status": 200
}
```

Case Two: the Command failed due to a syntax error in the Command. Optional status text is ignored by the Producer, but may be added to provide error details for debugging or logging.

```json
{
  "status": 400,
  "status_text": "Validation Error: Target: flie"
}
```

Case Three: the Command failed because an Argument was not supported.

```json
{
  "status": 501
}
```

### A.1.2 Port isolate a specific endpoint

**Command:**

```json
{
  "action": "contain",
  "target": {
    "device": {
      "hostname": "DESKTOP-123ABC"
    }
  },
  "args": {
    "edr": {
      "containment":"port_isolation"
    }
   },
  "actuator": {
    "edr": {}
  }
}
```

### A.1.3 Allow unrestricted app execution on a group of endpoints

**Command:**

```json
{
  "action": "allow",
  "target": {
    "device": {}
  },
  "args": {
    "edr": {
      "containment":"app_restriction"
    }
   },
  "actuator": {
    "edr": {
       "named_group":"accounting"
    }
  }
}
```

## A.2 Set

### A.2.1 Set an account on a specific endpoint to be enabled

**Command:**

```json
{
  "action": "set",
  "target": {
    "account": {
       "uid":"S-1-5-21-7375663-6890924511-1272660413-2944159"
    }
  },
  "args": {
    "edr": {
      "account_status":"enabled"
    }
   },
  "actuator": {
    "edr": {
       "hostname": "edr_oslo"
    }
  }
}
```

### A.2.1 Set accounts on a group of endpoints to be disabled

**Command:**

```json
{
  "action": "set",
  "target": {
    "account": {
       "account_name":"sql_admin"
    }
  },
  "args": {
    "edr": {
      "account_status":"disabled"
    }
   },
  "actuator": {
    "edr": {
       "named_group":"production"
    }
  }
}
```

-------

# Appendix A. References

This appendix contains the normative and informative references that are used in this document. Normative references are specific (identified by date of publication and/or edition number or version number) and Informative references are either specific or non-specific.

While any hyperlinks included in this appendix were valid at the time of publication, OASIS cannot guarantee their long-term validity.

## A.1 Normative References

The following documents are referenced in such a way that some or all of their content constitutes requirements of this document.

(Reference sources:
For references to IETF RFCs, use the approved citation formats at:  
http://docs.oasis-open.org/templates/ietf-rfc-list/ietf-rfc-list.html.  
For references to W3C Recommendations, use the approved citation formats at:  
http://docs.oasis-open.org/templates/w3c-recommendations-list/w3c-recommendations-list.html.  
Remove this note before submitting for publication.)

###### [RFC1123]
Braden, R., Ed., "Requirements for Internet Hosts - Application and Support", STD 3, RFC 1123, DOI 10.17487/RFC1123, October 1989, <https://www.rfc-editor.org/info/rfc1123>.

###### [RFC2119]
Bradner, S., "Key words for use in RFCs to Indicate Requirement Levels", BCP 14, RFC 2119, DOI 10.17487/RFC2119, March 1997, <https://www.rfc-editor.org/info/rfc2119>.

###### [RFC8174]
Leiba, B., "Ambiguity of Uppercase vs Lowercase in RFC 2119 Key Words", BCP 14, RFC 8174, DOI 10.17487/RFC8174, May 2017, <https://www.rfc-editor.org/info/rfc8174>.

###### [OpenC2-HTTPS-v1.0]
_Specification for Transfer of OpenC2 Messages via HTTPS Version 1.0_. Edited by David Lemire. Latest version: http://docs.oasis-open.org/openc2/open-impl-https/v1.0/open-impl-https-v1.0.html

###### [Winnt.h-registry-types]
_Registry Value Types_. Microsoft Windows documentation, <https://docs.microsoft.com/en-us/windows/win32/sysinfo/registry-value-types>

###### [SLPF-Deny]
https://github.com/oasis-tcs/openc2-apsc-stateless-packet-filter/blob/master/oc2slpf.md#232-deny

###### [SLPF-Allow]
https://github.com/oasis-tcs/openc2-apsc-stateless-packet-filter/blob/master/oc2slpf.md#231-allow

###### [SLPF-Conformance]
https://github.com/oasis-tcs/openc2-apsc-stateless-packet-filter/blob/master/oc2slpf.md#3-conformance-statements
<!--
## A.2 Informative References

###### [RFC3552]
Rescorla, E. and B. Korver, "Guidelines for Writing RFC Text on Security Considerations", BCP 72, RFC 3552, DOI 10.17487/RFC3552, July 2003, https://www.rfc-editor.org/info/rfc3552.
-->

---
# Appendix B. Acknowledgments

Note: A Work Product approved by the TC must include a list of people who participated in the development of the Work Product. This is generally done by collecting the list of names in this appendix. This list shall be initially compiled by the Chair, and any Member of the TC may add or remove their names from the list by request. Remove this note before submitting for publication.

## B.1 Participants

<!-- A TC can determine who they list here, however, TC Observers must not be listed. It is common practice for TCs to list everyone that was part of the TC during the creation of the document, but this is ultimately a TC decision on who they want to list and not list. -->

The following individuals have participated in the creation of this specification and are gratefully acknowledged:

**OpenC2 TC Members:**

| First Name | Last Name | Company |
| :--- | :--- | :--- |
Alex | Everett | University of North Carolina at Chapel Hill
Martin | Evandt | University of Oslo
David | Kemp | National Security Agency
David | Lemire | G2
Vasileios | Mavroeidis | University of Oslo
Duncan | Sparrell | sFractal Consulting LLC

-------

# Appendix C. Revision History
| Revision | Date | Editor | Changes Made |
| :--- | :--- | :--- | :--- |
| edr-ap-v1.0-wd01 | yyyy-mm-dd | Vasileios Mavroeidis, Martin Evandt | Initial working draft |

-------

# Appendix D. Notices

Copyright © OASIS Open 2021. All Rights Reserved.

All capitalized terms in the following text have the meanings assigned to them in the OASIS Intellectual Property Rights Policy (the "OASIS IPR Policy"). The full [Policy](https://www.oasis-open.org/policies-guidelines/ipr) may be found at the OASIS website.

This document and translations of it may be copied and furnished to others, and derivative works that comment on or otherwise explain it or assist in its implementation may be prepared, copied, published, and distributed, in whole or in part, without restriction of any kind, provided that the above copyright notice and this section are included on all such copies and derivative works. However, this document itself may not be modified in any way, including by removing the copyright notice or references to OASIS, except as needed for the purpose of developing any document or deliverable produced by an OASIS Technical Committee (in which case the rules applicable to copyrights, as set forth in the OASIS IPR Policy, must be followed) or as required to translate it into languages other than English.

The limited permissions granted above are perpetual and will not be revoked by OASIS or its successors or assigns.

This document and the information contained herein is provided on an "AS IS" basis and OASIS DISCLAIMS ALL WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO ANY WARRANTY THAT THE USE OF THE INFORMATION HEREIN WILL NOT INFRINGE ANY OWNERSHIP RIGHTS OR ANY IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.

As stated in the OASIS IPR Policy, the following three paragraphs in brackets apply to OASIS Standards Final Deliverable documents (Committee Specification, Candidate OASIS Standard, OASIS Standard, or Approved Errata).

\[OASIS requests that any OASIS Party or any other party that believes it has patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable, to notify OASIS TC Administrator and provide an indication of its willingness to grant patent licenses to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this deliverable.\]

\[OASIS invites any party to contact the OASIS TC Administrator if it is aware of a claim of ownership of any patent claims that would necessarily be infringed by implementations of this OASIS Standards Final Deliverable by a patent holder that is not willing to provide a license to such patent claims in a manner consistent with the IPR Mode of the OASIS Technical Committee that produced this OASIS Standards Final Deliverable. OASIS may include such claims on its website, but disclaims any obligation to do so.\]

\[OASIS takes no position regarding the validity or scope of any intellectual property or other rights that might be claimed to pertain to the implementation or use of the technology described in this OASIS Standards Final Deliverable or the extent to which any license under such rights might or might not be available; neither does it represent that it has made any effort to identify any such rights. Information on OASIS' procedures with respect to rights in any document or deliverable produced by an OASIS Technical Committee can be found on the OASIS website. Copies of claims of rights made available for publication and any assurances of licenses to be made available, or the result of an attempt made to obtain a general license or permission for the use of such proprietary rights by implementers or users of this OASIS Standards Final Deliverable, can be obtained from the OASIS TC Administrator. OASIS makes no representation that any information or list of intellectual property rights will at any time be complete, or that any claims in such list are, in fact, Essential Claims.\]

The name "OASIS" is a trademark of [OASIS](https://www.oasis-open.org/), the owner and developer of this specification, and should be used only to refer to the organization and its official outputs. OASIS welcomes reference to, and implementation and use of, specifications, while reserving the right to enforce its marks against misleading uses. Please see https://www.oasis-open.org/policies-guidelines/trademark for above guidance.
