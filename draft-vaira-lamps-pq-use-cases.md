---
stand_alone: true
ipr: trust200902
cat: info
submissiontype: IETF
area: "Security"
workgroup: "Post-Quantum Use In Protocols"
venue:
  group: "Post-Quantum Use In Protocols"
  type: "Working Group"
  mail: "pqc@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/pqc/"
  github: "avaira77/pq-ietf-usecase"
  latest: "https://avaira77.github.io/pq-ietf-usecase/draft-vaira-lamps-pq-use-cases.html"

docname: draft-vaira-pquip-pqc-use-cases-00

title: Post-quantum cryptography use case
abbrev: PQC use cases
lang: en
kw:
  - post-quantum cryptography
  - PQC use cases
author:
- name: Antonio Vaira
  org: Siemens
  abbrev: Siemens
  street: Werner-von-Siemens-Strasse 1
  code: '80333'
  city: Munich
  country: Germany
  email: antonio.vaira@siemens.com
  uri: https://www.siemens.com
- name: Hendrik Brockhaus
  org: Siemens
  abbrev: Siemens
  street: Werner-von-Siemens-Strasse 1
  code: '80333'
  city: Munich
  country: Germany
  email: hendrik.brockhaus@siemens.com
  uri: https://www.siemens.com
- name: John Gray
  org: Entrust
  abbrev: Entrust
  street: 1187 Park Place
  region: MN
  code: '55379'
  city: Minneapolis
  country: United States of America
  email: john.gray@entrust.com
  uri: https://www.entrust.com
- name: Mike Ounsworth
  org: Entrust
  abbrev: Entrust
  street: 1187 Park Place
  region: MN
  code: '55379'
  city: Minneapolis
  country: United States of America
  email: mike.ounsworth@entrust.com
  uri: https://www.entrust.com

normative:
  RFC5234:

informative:
  IEEE.802.1AR-2018: DOI.10.1109/IEEESTD.2018.8423794
  RFC4949:
  RFC4998:
  RFC5280:
  RFC5652:
  RFC6421:
  RFC7468:
  RFC8446:
  RFC9019:
  I-D.ietf-pquip-pqc-engineers:
  I-D.ietf-pquip-pqt-hybrid-terminology:
  NIST.SP.800-208:
  NIST.FIPS.186-5:
  RFC8391:
  RFC8554:
  RFC6071:
  RFC8446:
  RFC8551:
  RFC5652:
  I-D.ounsworth-pq-composite-sigs:
  I-D.ounsworth-pq-composite-keys:
  I-D.bonnell-lamps-chameleon-certs:
  I-D.ietf-lamps-cert-binding-for-multi-auth:
  X.509:
    title: >
      Information technology – Open Systems Interconnection – The Directory: Public-key and attribute certificate frameworks
    author:
      org: International Telecommunications Union
    date: 2019
    seriesinfo:
      ITU-T: Recommendation X.509
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

The transition to post-quantum cryptography poses a distinctive challenge in the domain of modern digital cryptography. This peculiarity stems from the absence of complete trust in both the outgoing and incoming cryptographic algorithms, crucial for ensuring data security throughout their required lifespans. This is of particular significance in guaranteeing the security of long-lived digital signatures, which are integral to secure software update workflows and manufacturer certificates, among other applications. Despite having NIST finalists for post-quantum cryptographic signature algorithms, concerns persist regarding their long-term security. At present, only stateful Hash-Based Signature schemes are considered secure.
At the same time, regulatory bodies (TODO: add references) mandate the incorporation of post-quantum cryptographic techniques, and in some cases, hybrid cryptography, as a proactive response to the quantum threat. As of now, the most effective strategies for transitioning to protect long-lasting digital signatures across diverse usage scenarios remain uncertain.

## Scope

The scope of this document is to compile a list of real-life use cases characterized by long-term security requirements, which are typically challenging to update, for example no over the air update mechanisms are available. These scenarios necessitate an early implementation of post-quantum cryptography migration strategies. Consequently, mitigation mechanisms must be introduced, given the limited experience with post-quantum cryptography to date. Furthermore, it is essential to consider regional regulations that may mandate the use of hybrid cryptography in specific instances.

## Terminology

This document makes use of the terminology defined in {{RFC4949}}, {{RFC5280}}, {{RFC9019}},  {{I-D.ietf-pquip-pqc-engineers}}, {{I-D.ietf-pquip-pqt-hybrid-terminology}} and TODO: add ref to composite signature drafts.

# Post-quantum Migration Mechanisms for Signing

People are considering which technological concepts are suitable to solve the problem of a secure migration from classical cryptography to quantum computer safe cryptographic algorithms. A variety of approaches are being discussed. In the following, we would like to briefly introduce the approaches under discussion and refer to the respective relevant documents for further details.
For a general introduction, we also refer to {{I-D.ietf-pquip-pqc-engineers}}.

## Stateful Hash-based Signatures Schemes

The only algorithms that are considered safe against attacks with quantum computers are the stateful hash-bases signature (HBS) schemes {{NIST.SP.800-208}} {{NIST.FIPS.186-5}} XMSS {{RFC8391}} and LMS {{RFC8554}}.
According to NIST, these stateful HBS algorithms offer better performance than stateless HBS algorithms, and the underlying technology is considered well understood. More stateful HBS algorithms are considered safe against attacks by quantum computers but cannot be widely used due to the state management that is very important for the security of stateful HBS. Especially for the secure signing of data that can be signed repeatedly over a very long period of time and whose signatures must be able to be securely validated with the same public key, stateful HBS do not appear to be suitable. This is because there are currently insufficient solutions for the replacement of the hardware security modules used and for disaster recovery cases.

## Stateless Hash-based Signature Schemes

NIST FIPS 205 specifies the ML-SLH (SPHINCS+) algorithm.  It is a stateless hashed based signature and is considered safe against attacks by quantum computers.  The advantage of this algorithm is that the state problem is resolved as part of the algorithm.  However, this tradeoff is that signature sizes are often an order of magnatude larger than XMSS or LMS.  This may make deploying these algorithms on constrained devices infeasible.  

## Protocol Revision (Cryptographic Agility)

Agility in security protocols and message formats, such as IP Security (IPsec) and Internet Key Exchange (IKE) {{RFC6071}}, Transport Layer Security (TLS){{RFC8446}}, Secure/Multipurpose Internet Mail Extensions (S/MIME){{RFC8551}}, is usually understood as the dynamic referencing of the algorithms to be used. A concrete migration strategy that allows the existing and future cryptographic algorithms to be used simultaneously during a transition period is usually not described in the respective standards.

An extension of the existing standards would be needed to integrate the required agility into the existing protocols and formats. This is a lot of effort for standardization and implementations if a basic functionality, such as multiple signatures, e.g., in Cryptographic Message Syntax (CMS) {{RFC5652}}, is not already available. But even in the case of S/MIME and CMS, a corresponding profiling is still necessary to describe how the multiple signatures are to be used specifically for the migration.

## Multiple Signatures

Several signatures have the approach of defining a second alternative signature in addition to the primary signature in the protocol or format, which can be transported in the protocol or format. In addition to the definition of the alternative signature, the associated signing algorithm and, if applicable, the associated public key or a reference to it must also be transferred. For X.509 PublicKey certificates, this is defined in {{X.509}}. Work is also underway for other protocols and formats. This approach overlaps with the protocol and format extension approach described in Section 3.1.

An alternative approach is to encode a second signature in a second certificate and bind it to the first one by a reference. For example, an implementation can decide based on the policy whether only the first certificate or the second or both certificates should be used for authentication. Further descriptions of this approach can be found in A Mechanism for Encoding Differences in Paired Certificates {{I-D.bonnell-lamps-chameleon-certs}} and Related Certificates for Use in Multiple Authentications within a Protocol {{I-D.ietf-lamps-cert-binding-for-multi-auth}}.

## Composite Signatures

The goal of composite signatures is to define a signature object to be used with any protocol or format. It contains two signatures in a single atomic container that have been generated using two different cryptographic algorithms. The goal of this approach is to define a signature format which requires both contained signtures to be verified.  In this way, the security properties of the classical signature and another signature that is secure when attacked by a quantum computer are used in the protocol or format without having to adapt them.

In order for this approach to be applicable in arbitrary protocols and formats, a composite key must be defined in addition to the composite signature. According to the definition of composite signatures, a composite public is a single atomic container composed of two public keys. 
The associated composite private key is a single atomic private key that is composed of the two private keys which correspond to the two public keys contained in the composite public key.  

This concept is described in Composite Signatures For Use In Internet PKI {{I-D.ounsworth-pq-composite-sigs}} in more detail.

# Use cases collection {#sec-usecases}

This section is the core this document. For each use case, we present a concise overview of the use case, the relevant categories it aligns with, and a list of potential migration methods. For each migration method, we highlight the advantages and disadvantages that stem from considering real-world deployment scenarios.

## Industrial communication protocols (that rely on IETF RFCs)
EDNOTE2: the title is an attempt at generalizing what BACnet is and why it should be interesting to take it into account while discussing pqc migration approaches within the IETF.

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

### Suitable migration mechanisms
TBD

## Software update
TBD

## Firmware update

EDNOTE3: As a generic note "we should contribute short use cases that we are familiar with", we could later on rephrase this use case to "update distributed industrial systems" for example like here: https://datatracker.ietf.org/doc/html/draft-ietf-anima-brski-async-enroll-00#section-3.2

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

### Suitable migration mechanisms
Given the long term requirements of the signatures and physically contrained locations, a signature used in these environments must be able to withstand future crytanalysis attacks as well as technological advancements.  Therefore the following migration mechanisms should be considerd for these enviornments:
- Multiple Signatures - These can be used to give the environment resilience to crytanalysis attacks and technological advancements because should a critical break happen, the secondary signature should allow for addition time for upgrade which will be welcome given the location constraints.  This would require cryptographic library updates as well as protocol level changes to support multiple signatures.   
- Composite Signatures - Similar to multiple signatures but would only require updates to the cryptographic libraries as well as a signature algorithm update in protocols.  It is likely composite signatures would be easier to deploy as single key and signature objects are used which is similar to what has historically be used.  
- Stateful hash based signatures - In constrained locations where larger signature sizes are acceptable, direct upgrade to a stateful hash based signature may be sufficient.
 

## Trust Anchor deployment

Trust Anchors, such as X.509 Root CA certificates and raw public keys, must be made accessible before they can be used for signature validation. In scenarios like remote software updates, a Trust Anchor X.509 certificate, for instance, must be installed on a target device to enable the validation of certificate chains. While deployment of Trust Anchors may be relatively straightforward for "corporate IT" and "public web" applications, it can still be a time-consuming process to ensure that a new Trust Anchor X.509 certificate is propagated throughout the entire ecosystem. Additionally, when dealing with post-quantum Trust Anchors, an extra layer of complexity arises as the desired underlying cryptography may not yet be supported by the target device or software.

Two common variations of this use case are:

- injection within a factory: in industrial contexts, Trust Anchors are typically injected into target devices during the manufacturing phase. Devices leaving the assembly line do not possess any credentials or Trusted Anchors initially. To bootstrap a Trust Anchor, the device is placed in a physically secure environment accessible only to trustworthy personnel. This injection can occur during manufacturing or when a device is being resold, but it's critical to note that not all scenarios support this method, potentially requiring the return of the device to the OEM for post-quantum Trust Anchor injection or it may be even not supported at all.

- injection via software and firmware updates: for devices where the Trust Anchor is not burned onto the device, for example in less constrained devices and IT equipment, post-quantum Trust Anchors can be injected through software or firmware update mechanisms. The deployment of these Trust Anchors may leverage existing update mechanisms and traditional cryptography to minimize effort. However, this approach necessitates the distribution of the new Trust Anchors well in advance of any suspicion that traditional cryptography may become vulnerable. Given the lead time required to ensure widespread distribution, the time window where this mechanism is suitable is further reduced.

### Suitable migration mechanisms
Trust anchors that have limited to no ability to be upgraded but which must be able to be trusted for a long time will require the use of signatures which must be able to withstand future crytanalysis attacks as well as technological advancements.  The following migration mechanisms should be considered for these environments:
- Multiple Signatures - These can be used to give the environment resilience to crytanalysis attacks and technological advancements because should a critical break happen, the secondary signature should allow for addition time for upgrade which will be welcome given the location constraints.  This would require cryptographic library updates as well as protocol level changes to support multiple signatures.   
- Composite Signatures - Similar to multiple signatures but would only require updates to the cryptographic libraries as well as a signature algorithm update in protocols.  It is likely composite signatures would be easier to deploy as single key and signature objects are used which is similar to what has historically be used.  
- Stateful hash based signatures - In constrained locations where larger signature sizes are acceptable, direct upgrade to a stateful hash based signature may be sufficient.

## Timestamping

EDNOTE5: RFC 4998 - we could study this to understand how to re-sign old timestamp messages. Question: does re-signing give protection against a full break of the original algorithm.
AV: an example is provided by "ETSI EN 319 142-1" (and "ETSI EN 319 142-2"), the standards define PDF advanced electronic signatures which have legal value EU. I assume that this concept may be extended to similar use cases, i.e., wherever long term validation is required new time-stamps may be added using post-quantum cryptography

### Suitable migration mechanisms
TBD

## CMS (S/MIME)

EDNOTE6: You can do infinite nesting in CMS.

EDNOTE7: The difficulty here will be non-uniform adoption: there are many many many email clients in the world at varying levels of maturity and maintenance. It is expected that some email clients will support PQ algorithms quickly while others may take more time or never adopt them fully. Suggestion to IETF: Study be put into RFC5652 the Cryptographic Message Syntax into signing messages with multiple signatures in a way that un-supported signatures will be ignored (likely this already "just works"). Email encryption probably requires either a flag day (you simply cannot encrypt a message for a recipient if you do not understand their PQ certificate)

### Suitable migration mechanisms
TBD

## Additional use cases

EDNOTE8: TO-DOs:

- add additional post-quantum relevant use cases which cover aspects not covered so far, this could also include use cases that are not common in our line of work (e.g., FAA airworthiness certifications, medical records, etc.), maybe contributed by other participants,
- any party that would be interested in contributing in this work may add additional post-quantum relevant use cases that are closer to her experience/field,
- the goal is to cover as much ground as possible in terms of use cases and to be able to define categories of use cases,

# IANA Considerations {#IANA}

This memo includes no request to IANA.

# Security Considerations {#Security}

This document should not affect the security of the Internet.

--- back

# Appendix 1 - post-quantum migration properties

The purpose of this section is to define a set of properties that can be used to classify each of the use-cases listed in  {{#sec-usecases}} in a consistent way. The goal is to make the document a resource to help classify use cases which are not covered herein because, for example, implementors could classify their own use-case and then find one in this document with the same properties / classification.

## Active Negotiation

TBD

Protocols with existing mechanisms for real-time cryptographic negotiation such as TLS and IKE already contain mechanisms for upgraded clients to downgrade the cryptography in a given session in order to communicate with a legacy peer. These protocols provide the easiest migration path as these mechanisms should be used to bridge across traditional and post-quantum cryptography.

## Passive Negotiation

TBD

Protocols with existing mechanisms for non-real-time or asynchronous cryptographic negotiation. For example a PKI end entity who publishes multiple encryption certificates for themselves, each containing a public key for a different algorithm, or code signing object carrying multiple signatures on different algorithms.

## Non Agile

TBD

Non-agile or flag day implies no graceful migration is possible; the community decides that as of a certain date legacy clients will no longer be able to interoperate with upgraded clients.

# Appendix 2 - Composite Signature individual and organization position statements

## BSI - Stavros Kousidis
"from a strategic point of view we don’t want to replace our current RSA algorithm with standalone Dilithium since: If Dilithium does not withstand cryptanalysis in the future then all our efforts are for nothing. With a composite signature Dilithium+ECDSA in AND-mode we can buy ourselves some time in case the Dilithium security guarantees do not withstand future cryptanalysis." 

## Google
Relying on a hybrid signature is critical as the security of Dilithium and other recently standardized quantum resistant algorithms haven’t yet stood the test of time and recent attacks on Rainbow (another quantum resilient algorithm) demonstrate the need for caution. This cautiousness is particularly warranted for security keys as most can’t be upgraded – although we are working toward it for OpenSK. The hybrid approach is also used in other post-quantum efforts like Chrome’s support for TLS.
TODO: How to reference this page:  https://security.googleblog.com/2023/08/toward-quantum-resilient-security-keys.html?m=1

## Entrust
During the transition to post-quantum cryptography, there will be uncertainty as to the strength of cryptographic algorithms; we will no longer fully trust traditional cryptography such as RSA, Diffie-Hellman, DSA and their elliptic curve variants, but we will also not fully trust their post-quantum replacements until they have had sufficient scrutiny and time to discover and fix implementation bugs. Unlike previous cryptographic algorithm migrations, the choice of when to migrate and which algorithms to migrate to, is not so clear.  Even after the migration period, it may be advantageous for an entity's cryptographic identity to be composed of multiple public-key algorithms.

Entrust will support composite signatures in PKI infrastructure

## Charter - Robert Hulshof
"The rationale behind combined keys is that I can see an important use-case for very sensitive data (government, financial or other high value data) to combine multiple (PQ) key algorithms, and that this migration to PQ is a good time to start supporting that by default in the crypto libraries.  
Trying to estimate the probability that a NIST standardized Crypto algorithm gets broken in the next 5-10 years is very difficult. However I assume that everybody agrees that this probability is definitely not zero. Personally I would put that probability somewhere in the range of 0.1% – 1%. 
If I were the government/bank etc. I would not like to have a 1% risk that all my secrets get exposed. Adding one or two more PQ algorithms would reduce that probability to 1 in a million or 1 in a Billion would be much more acceptable." 

## MTG - Falko Strenzke
"Without hybrid signatures, a decision to move away from traditional signatures to Dilithium (or other non-hash-based signatures) has a certain risk to make things worse and I think many decision makers will not be ready to take the responsibility for it until the quantum computer threat becomes imminent. 
- If composite signature is not standardised, non-composite hybrids would be left. This implies protocol changes which will: 
  - need more discussion,
  - need more changes to existing applications,
  - and thus be more bug prone.
- Not having hybrid signatures at all will likely cause many decision makers to
  - use hash-based schemes where possible / affordable
  - and elsewhere stick to traditional schemes as long as possible, thus effectively delaying the migration to PQC."

## Transmute - Orie Steele
TODO but something about this:  There are use cases for long lived verifiable credentials, and attribute cert like stuff we work on in supply chain, with DHS / CBP.

## CRYSTALS-Dilithium design team
- https://pq-crystals.org/dilithium/ (accessed: 2023-08-21):
“For users who are interested in using Dilithium, we recommend the following:
- Use Dilithium in a so-called hybrid mode in combination with an established "pre-quantum" signature scheme.”

## Hybrid Post-Quantum Signatures in Hardware Security Keys
https://storage.googleapis.com/pub-tools-public-publication-data/pdf/8becef5ac3da51c3b2e36d2dbcd18a4bd3d220d9.pdf

“A hybrid signature scheme combines a classical signature algorithm with a post-quantum secure signature algorithm. Before discussing the design of our hybrid scheme, we explain why such an approach is relevant instead of simply replacing classically secure schemes with post-quantum secure schemes. We present the assumptions below:

 1. Cryptographically-Relevant Quantum Computers (i.e. with enough qubits to break ECDSA) are not available yet.
 2. Classical signature algorithms withstands attacks from classical computers. 
 3. The post-quantum secure signature algorithm might be breakable by classical computers due to design or implementation bugs. If any of these assumptions fails, using a hybrid approach instead of replacing classical schemes with post-quantum schemes indeed does not add any security. We believe that all of these assumptions are currently correct. The third assumption is motivated by a newly discovered attack against Rainbow, one of the NIST standardization finalists.”

We can now discuss the informal requirements a hybrid scheme H should satisfy:
1. If a quantum computer becomes available, and hence H’s underlying classical scheme is broken, H should maintain the security of its underlying post-quantum scheme. 
2. If a classical attack for H’s underlying post-quantum secure scheme is discovered, H should maintain the security of its underlying classical scheme.


# Acknowledgements {#Acknowledgements}
{: numbered="false"}

This draft would not be possible without the support of a great number of contributers.   We thank Stavros Kousidis, Robert Hulshof, Falko Strenzke and Orie Steele for allowing us to use their statements regarding composite signatures. 
TBD.
