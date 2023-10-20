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

Post-quantum cryptography comes with two main challenges:

- technical challenges: related to the difficulties of adopting and implementing the new post-quantum cryptographic algorithms. This includes understanding how these algorithms work and integrating them into existing systems securely.

- "sorting/clustering" challenges: that arise from the limitations of post-quantum cryptographic algorithms. Organizations face the complexity of selecting the most suitable algorithm for a given use case. With numerous algorithms available and diverse use case requirements, it becomes challenging to identify the best-fit solution.

This document aims at providing means to overcome the "sorting/clustering" challenges and identify best-fit migration solutions.

## Scope

The scope of this document is to compile a list of real-life use cases characterized by long-term security requirements, which are typically challenging to update, for example no over the air update mechanisms are available. These scenarios necessitate an early implementation of post-quantum cryptography migration strategies. Consequently, mitigation mechanisms must be introduced, given the limited experience with post-quantum cryptography to date. Furthermore, it is essential to consider regional regulations that may mandate the use of hybrid cryptography in specific instances.

## Terminology

This document makes the assumption that the reader is familiar with post-quantum cryptography terminology and with draft-ietf-pquip-pqt-hybrid-terminology. The subsequent section provides clarifications on terminology to facilitate a smoother reading experience.

- Cryptographic agility: also referred to as "crypto-agility", despite no precise definition is available at the time of writing, some intuitive working definitions have been proposed. In {{RFC6421}}, "crypto-agility is the ability of a protocol to adapt to evolving cryptography and security requirements. This may include the provision of a modular mechanism to allow cryptographic algorithms to be updated without substantial disruption to fielded implementations. It may provide for the dynamic negotiation and installation of cryptographic algorithms within protocol implementations (think of Dynamic-Link Libraries (DLL))". A more generic definition may be found in "NIST Cryptographic Agility and Interoperability: Proceedings of a Workshop", i.e.: crypto-agility includes (1) the ability for machines to select their security algorithms in real time and based on their combined security functions; (2) the ability to add new cryptographic features or algorithms to existing hardware or software, resulting in new, stronger security features; and (3) the ability to gracefully retire cryptographic systems that have become either vulnerable or obsolete.

- Manufacturer issued certificate : also referred to as "IDevID" are X.509 certificates used for authentication purposes and typically issued to a physical device, by the OEM, during the manufacturing phase. These certificate may be used to prove authenticity of the device, as an original part, and to bootstrap the device within an operational context, see draft-ietf-anima-bootstrapping-keyinfra-45.

- Trust Anchor (TA): as defined in {{RFC4949}} a TA is an established point of trust (usually based on the authority of some person, office, or organization) from which a certificate user begins the validation of a certification path. A trust anchor may be defined as being based on a public key, a CA, a public-key certificate, or some combination or variation of those. Additionally, TAs may be imprinted within a device at manufacturing time as it is done for IDevID certificates.

- Secure Boot: is a security standard whose purpose it to ensure that only software trusted by the OEM is used during the boot phase of a device. At boot time of a device, the firmware checks the signature of each component of the boot software. The device will boot upon successful validation of the digital signatures of each software component involved in the boot process. The TAs required to validate the signatures have to be stored onto the device, e.g. within its firmware. EDNOTE20: we should align this terminology with SUIT RFC9019.

- Stateful hash-based signature scheme: is a signature scheme whose private key changes over time and if a secret key state is used twice, all cryptographic security guarantees are lost. As a consequence of that, it becomes feasible to forge a signature on a new message. At the time of this writing there are two RFC that specify XMSS/XMSS^MT and LMS/HSS and the NIST SP 800 208 that describes deployment strategies.

# Post-quantum migration properties

The purpose of this section is to define a set of properties that can be used to classify each of the use-cases listed in  {{#}} in a consistent way. The goal is to make the document a resource to help classify use cases which are not covered herein because, for example, implementors could classify their own use-case and then find one in this document with the same properties / classification.

## Active Negotiation

TBD

Protocols with existing mechanisms for real-time cryptographic negotiation such as TLS and IKE already contain mechanisms for upgraded clients to downgrade the cryptography in a given session in order to communicate with a legacy peer. These protocols provide the easiest migration path as these mechanisms should be used to bridge across traditional and post-quantum cryptography.

## Passive Negotiation

TBD

Protocols with existing mechanisms for non-real-time or asynchronous cryptographic negotiation. For example a PKI end entity who publishes multiple encryption certificates for themselves, each containing a public key for a different algorithm, or code signing object carrying multiple signatures on different algorithms.

## Non Agile

TBD

Non-agile or flag day implies no graceful migration is possible; the community decides that as of a certain date legacy clients will no longer be able to interoperate with upgraded clients.

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

Firmware, defined in {{RFC4949}}, refers to computer programs and data stored in hardware, typically in read-only memory (ROM) or programmable read-only memory (PROM). These programs and data are non-modifiable during execution, offering low-level hardware control.

Secure firmware updates are crucial for ensuring device security and long-term operation, especially in industrial, and critical infrastructure fields, where devices can stay active for decades. Such updates encompass tasks like introducing new trust anchors and upgrading cryptographic algorithm capabilities. However, upgrading every device's security capabilities isn't always feasible due to resource, accessibility, and cost constraints. Some "simple" devices may not support secure firmware updates at all.

Firmware updates are typically authenticated by the Original Equipment Manufacturer (OEM) by means of a digital signing process. At a high level, a usual process involves, a firmware build server, which requests a signature from a signing service. The signing service, often safeguarding the signing private key in secure environments like Hardware Security Modules (HSMs), returns the signature after authenticating the request.

Subsequently the firmware is distributed to target devices, which in turn must validate the firmware signature against a Trust Anchor (TA). The TA can be an X.509 certificate, a public key, or a hash of a combination of both, depending on the OEM's security measures.

These devices are typically deployed in highly regulated environments, in remote or physically constrained locations where performing upgrades is challenging, or in cases where the cost of upgrading is prohibitively high. The immutability of these devices can also be viewed as a security feature, as it restricts potential attack vectors associated with over-the-air updates. These devices are designed with a long operational lifespan in mind, often spanning several decades. Notable examples of such devices encompass:
- Vehicles - scale of deployment or vehicle recall difficulties
- Satellites - no 'on-site' service reasonably possible
- Servers and network devices - air-gapped, locked-down DCs, geographically distributed
- Government infrastructure - power grids, nuclear power station equipment, etc.
- Smart meters - device owned by the utility company, deployed in private homes.
- Smart cards – used for authenticating to workstations and buildings, or electronic document signing.
- Security Tokens – such as FIDO2, cheap devices that users typically will typically not patch.

### Category

This use case can be categorized as:

- "passive negotiation", if the entity that validates the firmware signature has a mechanism to update the Trust Anchor relied upon during signature validation. This is due to the fact that the SW package may be delivered with multiple signatures that use either traditional and/or post-quantum cryptography;

- "non agile", if the entity that validates the signature cannot update the Trust Anchor.

### Suitable migration mechanisms
TBD

## Trust Anchor deployment

Trust Anchors, such as X.509 Root CA certificates and raw public keys, must be made accessible before they can be used for signature validation. In scenarios like remote software updates, a Trust Anchor X.509 certificate, for instance, must be installed on a target device to enable the validation of certificate chains. While deployment of Trust Anchors may be relatively straightforward for "corporate IT" and "public web" applications, it can still be a time-consuming process to ensure that a new Trust Anchor X.509 certificate is propagated throughout the entire ecosystem. Additionally, when dealing with post-quantum Trust Anchors, an extra layer of complexity arises as the desired underlying cryptography may not yet be supported by the target device or software.

Two common variations of this use case are:

- injection within a factory: in industrial contexts, Trust Anchors are typically injected into target devices during the manufacturing phase. Devices leaving the assembly line do not possess any credentials or Trusted Anchors initially. To bootstrap a Trust Anchor, the device is placed in a physically secure environment accessible only to trustworthy personnel. This injection can occur during manufacturing or when a device is being resold, but it's critical to note that not all scenarios support this method, potentially requiring the return of the device to the OEM for post-quantum Trust Anchor injection or it may be even not supported at all.

- injection via software and firmware updates: for devices where the Trust Anchor is not burned onto the device, for example in less constrained devices and IT equipment, post-quantum Trust Anchors can be injected through software or firmware update mechanisms. The deployment of these Trust Anchors may leverage existing update mechanisms and traditional cryptography to minimize effort. However, this approach necessitates the distribution of the new Trust Anchors well in advance of any suspicion that traditional cryptography may become vulnerable. Given the lead time required to ensure widespread distribution, the time window where this mechanism is suitable is further reduced.

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
