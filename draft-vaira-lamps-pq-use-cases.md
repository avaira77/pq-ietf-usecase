---
stand_alone: true
ipr: trust200902
cat: info
submissiontype: IETF
area: "Security"
workgroup: "Post-Quantum Use In Protocols (pquip)"
venue:
  group: "Limited Additional Mechanisms for PKIX and SMIME"
  type: "Working Group"
  mail: "spasm@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/spasm/"
  github: "avaira77/pq-ietf-usecase"
  latest: "https://avaira77.github.io/pq-ietf-usecase/draft-vaira-lamps-pq-use-cases.html"

docname: draft-vaira-lamps-pq-use-cases-00

title: Post-quantum cryptography use case
abbrev: PQC use cases
lang: en
kw:
  - post-quantum cryptography
  - PQC use cases
author:
- name: Antonio Vaira
  org: Siemens AG
  street: Otto Hahn Ring 6
  city: Munich
  code: 81739
  country: DE
  email: antonio.vaira@siemens.com
- name: Hendrik Brockhaus
  org: Siemens AG
  email: hendrik.brockhaus@siemens.com
- name: Mike Ounsworth
  org: Entrust Limited
  street: 2500 Solandt Road -- Suite 100
  city: Ottawa, Ontario
  code: K2K 3G5
  country: Canada
  email: mike.ounsworth@entrust.com
- name: John Gray
  org: Entrust Limited
  email: john.gray@entrust.com

normative:
  RFC5234:

informative:
  RFC4949:
  RFC4998:
  RFC5652:
  RFC6421:
  RFC7468:
  RFC8446:
  RFC9019:
  ASN.1:
    title: >
      Information Technology — ASN.1 encoding rules:
      Specification of Basic Encoding Rules (BER), Canonical Encoding
      Rules (CER) and Distinguished Encoding Rules (DER)
    author:
      org: International Telecommunications Union
    date: 1994
    seriesinfo:
      ITU-T: Recommendation X.690

--- abstract

This document focuses on the critical challenge of migrating long-term security assertions with security requirements spanning over a decade, encompassing X.509 certificates, including those that serve as IDevID credentials, signed firmware/software, and other electronic artifacts. We investigate a range of migration mechanisms, specifically hybrid cryptography and the feasibility of stateful Hash-Based Signatures (HBS) schemes, including its pros and cons. To offer a comprehensive context, we present a list of use cases centered around long-lived security assertions, categorize them, and evaluate them against the various migration approaches identified. We also aim at listing pros and cons associated with each method.

--- middle

# Introduction

The purpose of this document is to compile a list of real-world use cases, focusing on long-term security assertions, and categorize them according to their post-quantum migration properties. This document additionally aims at evaluating, for each use case category, a set of migration mechanisms, like hybrid cryptography, including multiple and composite signatures, and the feasibility of using stateful Hash-Based Signatures (HBS) schemes,  evaluating the pros and cons of each approach.

The document is structured into the following sections: "Post-quantum migration properties", defines the main features of each category;  "Post-quantum migration mechanisms", lists possible migration approaches; "Use case collection", describes, at a high level, of the use cases at hand, including prominent migration properties and an analysis of the pros and cons for each of the migration mechanisms applicable.

## Requirements Language

{::boilerplate bcp14-tagged}

## Problem Statement

EDNOTE14: I think this section is now obsolete

Post-quantum cryptography introduces two main types of challenges:

- technical challenges, related to the usage of the new post-quantum cryptographic algorithms, and

- "sorting/clustering" challenges related to the broad applicability of these algorithms and the uncertainty of which approach is a best fit within the boundaries of a selected use case. The large number of algorithms that can be used, and the diversity of requirements that come from post-quantum relevant use cases makes it difficult for organizations and businesses to deliver post-quantum secure solutions.

The main aspects of the problem space are:

- Cryptographically relevant quantum computers pose a treat to asymmetric cryptography, i.e., for all practical purposes it must be considered broken, and the security of symmetric cryptography must be considered degraded.

- No multi-purpose post-quantum cryptographic algorithm will be standardized in the forseeable future, rather a number of single-purpose post-quantum algorithms will be standardized at the same time. Three digital signature algorithms and one key encampsulation algorithm have been defined at the end of round 3 of NIST standardization. All post-quantum algorithms defined so far exhibit diverse features making them unfit for a simple drop-in replacement of existing traditional algorithms.

- Public Key Infrastructures and digital Signing Services will have to be upgraded with post-quantum capabilities long before they will be required.

- To the authors' knowledge, very limited discussions are taking place in public working groups, to discuss about post-quantum relevant use cases. This list may be of help in defining recommendations for businesses or organization in defining their post-quantum deployment strategies.

## Scope

The scope of this document is to compile a list of real-life use cases characterized by long-term security requirements, which are typically challenging to update, for example no over the air update mechanisms are available. These scenarios necessitate an early implementation of post-quantum cryptography migration strategies. Consequently, mitigation mechanisms must be introduced, given the limited experience with post-quantum cryptography to date. Furthermore, it is essential to consider regional regulations that may mandate the use of hybrid cryptography in specific instances.

## Terminology

EDNOTE15: some of the terminology may be removed.

This document assumes that the reader is familiar with post-quantum cryptography related terms, including those defined in draft-driscoll-pqt-hybrid-terminology. The following terms are defined herein for sake of clarity:

- Cryptographic agility: also referred to as "crypto-agility", despite no precise definition is available at the time of writing, some intuitive working definitions have been proposed. In {{RFC6421}}, "crypto-agility is the ability of a protocol to adapt to evolving cryptography and security requirements. This may include the provision of a modular mechanism to allow cryptographic algorithms to be updated without substantial disruption to fielded implementations. It may provide for the dynamic negotiation and installation of cryptographic algorithms within protocol implementations (think of Dynamic-Link Libraries (DLL))". A more generic definition may be found in "NIST Cryptographic Agility and Interoperability: Proceedings of a Workshop", i.e.: crypto-agility includes (1) the ability for machines to select their security algorithms in real time and based on their combined security functions; (2) the ability to add new cryptographic features or algorithms to existing hardware or software, resulting in new, stronger security features; and (3) the ability to gracefully retire cryptographic systems that have become either vulnerable or obsolete.

- Manufacturer issued certificate : also referred to as "IDevID" are X.509 certificates used for authentication purposes and typically issued to a physical device, by the OEM, during the manufacturing phase. These certificate may be used to prove authenticity of the device, as an original part, and to bootstrap the device within an operational context, see draft-ietf-anima-bootstrapping-keyinfra-45.

- Trust Anchor (TA): as defined in {{RFC4949}} a TA is an established point of trust (usually based on the authority of some person, office, or organization) from which a certificate user begins the validation of a certification path. A trust anchor may be defined as being based on a public key, a CA, a public-key certificate, or some combination or variation of those. Additionally, TAs may be imprinted within a device at manufacturing time as it is done for IDevID certificates.

- Secure Boot: is a security standard whose purpose it to ensure that only software trusted by the OEM is used during the boot phase of a device. At boot time of a device, the firmware checks the signature of each component of the boot software. The device will boot upon successful validation of the digital signatures of each software component involved in the boot process. The TAs required to validate the signatures have to be stored onto the device, e.g. within its firmware.

- Stateful hash-based signature scheme: is a signature scheme whose private key changes over time and if a secret key state is used twice, all cryptographic security guarantees are lost. As a consequence of that, it becomes feasible to forge a signature on a new message. At the time of this writing there are two RFC that specify XMSS/XMSS^MT and LMS/HSS and the NIST SP 800 208 that describes deployment strategies.

- Active negotiation: protocols with existing mechanisms for real-time cryptographic negotiation such as TLS and IKE already contain mechanisms for upgraded clients to downgrade the cryptography in a given session in order to communicate with a legacy peer. These protocols provide the easiest migration path as these mechanisms should be used to bridge across traditional and post-quantum cryptography.

- Passive negotiation: protocols with existing mechanisms for non-real-time or asynchronous cryptographic negotiation. For example a PKI end entity who publishes multiple encryption certificates for themselves, each containing a public key for a different algorithm, or code signing object carrying multiple signatures on different algorithms.

- Non-agile / flag day: no graceful migration is possible; the community decides that as of a certain date legacy clients will no longer be able to interoperate with upgraded clients.

# Post-quantum migration properties

The purpose of this section is to define a set of properties that can be used to classify each of the use-cases listed in  {{#}} in a consistent way. The goal is to make the document a resource to help classify use cases which are not covered herein because, for example, implementors could classify their own use-case and then find one in this document with the same properties / classification.

## Active Negotiation

TBD

## Passive Negotiation

TBD

## Non Agile

TBD

# Post-quantum migration mechanisms

The purpose of this section is to define a set of migration mechanisms that can be used by each of the use-cases in {{#}} in a consistent way.

## Composite Signatures
TBD

## Composite KEM

EDNOTE16: I would suggest to keep KEM out of the picture for the time being and focus on signatures only.

TBD

## Protocol Revision (Cryptographic Agility)

EDNOTE17: same as above. Additionally crypto agility is a concept quite difficult to grasp given the large amount of definitions available online. These definition that to focus on different aspects.

This mechanism may require a minimal update to an existing protocol.  In some cases the protocol may already contain built in mechanisms that may be used to perform the migration.

## Multiple Signatures

TBD

EDNOTE18: In this section we could cover multiple certificates, the isara and the camelion approach.

## Stateful hash-based signatures

TBD

EDNOTE19: despite not being a mechanism per se sHBS are relevant in use cases like FW and SW update due to CNSA2.0 and in my understanding if sHBS is used then typically there is no need for hybrid (this should be the position of BSI at least, REF needed!)

# Use cases collection {#}

This section is the core this document. For each use case, we present a concise overview of the use case, the relevant categories it aligns with, and a list of potential migration methods. For each migration method, we highlight the advantages and disadvantages that stem from considering real-world deployment scenarios.

## Industrial communication protocols (that rely on IETF RFCs)
EDNOTE11: the title is an attempt at generalizing what BACnet is and why it should be interesting to take it into account while discussing pqc migration approaches within the IETF.

Several industrial communication protocols, traditionally orthogonal to IP network infrastructure, are progressively being updated to make use of standard IP network infrastructure hence rely standard security mechanisms, like for example TLS 1.3.

An example of such protocol is BACnet/SC. BACnet is a data communication protocol for Building Automation and Control Networks. BACnet was defined before 1995, when the TCP/IP protocol suite was expensive and not available for smaller devices common in building automation. BACnet Secure Connect, known as BACnet/SC and defined in the addendum ANSI/ASHRAE Standard 135-2016, proposes a new datalink layer option that makes full use of TLS secured WebSocket connections. This new BACnet Secure Connect datalink layer option uses a virtual hub-and-spoke topology where the spokes are WebSocket connections from the nodes to the hub.

The main features of BACnet/SC are:

- it makes use of WebSockets secured via TLS1.3,

- it relies on X.509 certificates to authenticate the nodes in the network,

- DNS host name resolution and DHCP are supported,

- it is agnostic to IP versions (IPv4 or IPv6),

- it can be NATted.

BACnet/SC's implementation adheres to established industry standards defined in IETF RFCs. Specifically the Addendum bj to ANSI/ASHRAE Standard 135-2016 references RFC 7468, when defining the format in which operational certificates and signing CA should be installed onto the target device at configuration time.

The security of the BACnet/SC protocol, as well as of similar industrial protocols, relies on TLS 1.3 (RFC 8446), therefore implications of post-quantum cryptography have to be considered in both the TLS handshake and in the X.509 certificates used for the authentication.

Furthermore, the geographical locations of the BACnet/SC-enabled devices in operation may necessitate the inclusion of extra considerations related to post-quantum cryptography, like for example the use of hybrid cryptography.

### Category

This use case can be categorized as:

- "active negotiation", BACnet/SC hubs and spokes authenticate against each other frequently, for example on a daily basis.

- "Long-term migration strategies": The devices are rarely upgraded because they are typically operated in environments with limited access. Additionally, the BACnet/SC standards heavily rely on IETF RFC. To comply with regional requirements for supporting hybrid cryptography, they are prime candidates for implementing composite-hybrid mechanisms.

EDNOTE12: a limited number of categories has to be defined. We might introduce a category "hybrid support required" to tag the use cases for which an approach like hybrid-composite will be helpful.

### Suitable migration mechanisms
TBD

## Software update
TBD

### Category
TBD

### Suitable migration mechanisms
TBD

## Firmware update

EDNOTE13: Use terminology from SUIT for the firmware update use case (RFC 9019). Many people in the IETF are already familiar with it. Shorten!

Firmware, as defined in the {{RFC4949}}, is: computer programs and data stored in hardware -- typically in read-only memory (ROM) or programmable read-only memory (PROM) -- such that the programs and data cannot be dynamically written or modified during execution of the programs. It provides low-level access and control on the hardware.

Support for secure firmware update is key to ensure crypto-agility and that a device is operable in the field for long time, for example in industrial applications a device may be in the field for several decades.
The following tasks may be carried out as part of a firmware update:

- new trust anchors may be rolled out as part of firmware updates and,

- cryptographic algorithms capabilities can be updated with a firmware update.

It will not be generally possible to upgrade the security capabilities of each device because, different devices exhibit different constrains in terms of resources, deployment environment (physically accessible or not) and costs. In some cases it might be a deliberate business decision to keep a device "simple" and to not support any security update via firmware updates altogether.

Firmware updates are typically signed by the OEM and the signature workflow can be carried by using a Public Key Infrastructure and Signing Service. These services may be owned and operated directly by the OEM or by a third party.

At a high level the signature process can be described with the following steps:

1. the to-be-signed firmware updates are delivered to a build server (e.g. version control repository),
1. the build server in turn requests a signature at a Signing Service,
1. the Signing Service authenticates the requests and returns a signature back.

Typically the Signing Service hosts the signing private key in a highly secure environment, e.g. in a Hardware Security Modules (HSM) and performs auditable access control.

~~~~~~~~~~
+-------------------------------------------------------+
|                         +---------------------------+ |
|                         |   +-------------------+   | |
| +---------------+       |   |     +-------+     |   | |
| | +-----------+ |       |   |     |Signing|     |   | |
| | |SW artifact| |<----->|   |     |Key    |     |   | |
| | +-----------+ |       |   |     +-------+     |   | |
| |               |       |   |                   |   | |
| | SW repository |       |   |  Signing Service  |   | |
| +---------------+       |   +-------------------+   | |
|                         |                           | |
|                         |                           | |
|                         |   High security network   | |
| OEM network             +---------------------------+ |
+-------------------------------------------------------+
~~~~~~~~~~
{: #Central-sig-serv title="central Signing Service"}

In the previous figure all the signing entities, hence the entire signing process, are controlled by the Manufacturer but similar constrains and considerations applies if the Signing Service is provided by a third party. Further security considerations have to be made on the communication channels involved in the exchanges that are required to implement the signature workflow.
Additionally, the signing process described is very generic and not restricted to signing of firmware updates but could be easily extended to other use cases.

To install a firmware update the target device will have to successfully validate the firmware signature first. The validation of the firmware signature, and its associated trust chain if applicable, will be performed against a Trust Anchor. The TA can be a X.509 certificate (or a proprietary format certificate), a plain public key or a hash of a combination of both. In general the Trust Anchor format is highly dependent on the security measures implementation by the OEM.
An additional aspect to consider is how can the device "trust" the Trust Anchor. Typically, for hardware devices, this is done by injecting the Trust Anchor during manufacturing time and "burning" it into the hardware. Usually this also means that there is no simple mechanism that would allow to replace the Trust Anchor, e.g. in case the underlaying cryptography is no longer considered secure. Alternatively the Trust Anchor may be deployed via a firmware/software update, and to validate the signature an already trusted Trust Anchor must be present. If this approach is not viable then the initial trust must be established by using ad-hoc processes, e.g. a trusted operator may manually install the update in a trusted environment.

### Category

This use case can be categorized as:

- "passive negotiation", if the entity that validates the firmware signature has a mechanism to update the Trust Anchor relied upon during signature validation. This is due to the fact that the SW package may be delivered with multiple signatures that use either traditional and/or post-quantum cryptography;

- "non agile", if the entity that validates the signature cannot update the Trust Anchor.

### Suitable migration mechanisms
TBD

## Trust Anchor deployment

EDNOTE2: The content should be shortned and subsection removed.

Trust Anchors, like X.509 Root CA certificates, raw public keys, etc., have to be made available before they can be used to validate a signature. In the case of remote firmware update, for example, a Trust Anchor X.509 certificate has to be deployed onto a target device before it can be used to validate a certificate chain. For "corporate IT" and "public web" type of use cases, the deployment might be somehow easier but it might take a long time before a new Trust Anchor X.509 certificate is deployed across the entire ecosystem. For post-quantum Trust Anchor there might be the additional complication that the desired underlying cryptography might not yet be supported by the target device/software/etc.
In the following sections we attempt a description of few variation of this use case.

### Injection within a factory

In the industrial context a Trust Anchor is typically deployed onto a target device during manufacturing time. A device, which is coming out of the assembly line, does not hold any credentials nor Trusted Anchors yet. Therefore in order to inject a Trusted Anchor in a trustworthy manner, it may be placed in a physically secure environment where only trustworthy staff members have access. The Trust Anchor injection in a factory may take place at:

- manufacturing time, i.e. when the device is being assembled hence all the steps are taking place within a secure environment under sole control of the OEM, or during

- reservicing, i.e. when the device is being re-sold hence all the steps are taking place within an environment that is outside the control of the OEM. This use case may be not supported in all scenarios and it might be necessary to return the device to the OEM to inject a post-quantum Trust Anchor.

### Injection via software and firmware updates

For devices where the Trust Anchor is not "burned" into a ROM, typically these are also less constrained devices, and IT equipment, it may be possible to inject post-quantum Trust Anchor via either software of firmware update mechanisms. The deployment of the post-quantum Trust Anchors may rely on existing update mechanisms and traditional cryptography, to minimize the effort. Relying on traditional cryptography to deploy post-quantum Trust Anchors implies that the new Trust Anchors have to be distributed long before there is a suspicion that traditional cryptography is vulnerable. Factoring in the lead time required to distribute the Trust Anchors widely enough to make them useful, the time window where this mechanism is suitable is further reduced.

### Category
TBD

### Suitable migration mechanisms
TBD

## Timestamping

EDNOTE5: RFC 4998 - we could study this to understand how to re-sign old timestamp messages. Question: does re-signing give protection against a full break of the original algorithm.
AV: an example is provided by "ETSI EN 319 142-1" (and "ETSI EN 319 142-2"), the standards define PDF advanced electronic signatures which have legal value EU. I assume that this concept may be extended to similar use cases, i.e., wherever long term validation is required new time-stamps may be added using post-quantum cryptography

### Category
TBD

### Suitable migration mechanisms
TBD

## CMS (S/MIME)

EDNOTE6: You can do infinite nesting in CMS.

EDNOTE7: The difficulty here will be non-uniform adoption: there are many many many email clients in the world at varying levels of maturity and maintenance. It is expected that some email clients will support PQ algorithms quickly while others may take more time or never adopt them fully. Suggestion to IETF: Study be put into RFC5652 the Cryptographic Message Syntax into signing messages with multiple signatures in a way that un-supported signatures will be ignored (likely this already "just works"). Email encryption probably requires either a flag day (you simply cannot encrypt a message for a recipient if you do not understand their PQ certificate)

### Category
TBD

### Suitable migration mechanisms
TBD

## Additional use cases

EDNOTE8: The use cases in section 2.1.x do not actually mention post-quantum, but you do a little bit in 2.2. I was expecting at least some analysis of whether the use case will present particular challenges to adoption of post-quantum. This, I think, is where the interesting discussion will happen.
AV: as discussed in our call the plan, for the time being, is to defer these discussions to a follow up document to avoid tackling too much content at once.

EDNOTE9: TO-DOs:

- add additional post-quantum relevant use cases which cover aspects not covered so far, also use cases that are not common in our line of work (e.g., FAA airworthiness certifications, medical records, etc.),
- identify additional parties that would like to join this effort,
- any party that would be interested in contributing in this work may add additional post-quantum relevant use cases that are closer to her experience/field,
- the goal is to cover as much ground as possible in terms of use cases and to be able to define categories of use cases. A possible follow-up document could come up with proposals about which set of post-quantum algorithms, certificate-type, PKI/Signature Service component, etc. is the best fit for the give use case,
- this document should provide the ground for discussions in other documents where more analysis about whether each use case will have problematic points with regards to PQ migration and whether the IETF needs to take an active role in updating protocols or providing operational guidance,
- additionally, this document can  be referenced in the technical discussions to help frame/structure the discussion, where needed.

# IANA Considerations {#IANA}

This memo includes no request to IANA.

# Security Considerations {#Security}

This document should not affect the security of the Internet.

--- back

# Appendix 1

Place holder.

# Acknowledgements {#Acknowledgements}
{: numbered="false"}

TBD.
