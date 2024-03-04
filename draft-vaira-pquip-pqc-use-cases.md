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
  latest: "https://avaira77.github.io/pq-ietf-usecase/draft-vaira-pquip-pq-use-cases.html"

docname: draft-vaira-pquip-pqc-use-cases-latest

title: Post-quantum cryptography migration use cases
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
- name: Alexander Railean
  org: Siemens
  abbrev: Siemens
  street: Werner-von-Siemens-Strasse 1
  code: '80333'
  city: Munich
  country: Germany
  email: alexander.railean@siemens.com
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

informative:
  IEEE.802.1AR-2018: DOI.10.1109/IEEESTD.2018.8423794
  RFC3161:
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
  RFC8551:
  RFC5652:
  I-D.ounsworth-pq-composite-sigs:
  I-D.bonnell-lamps-chameleon-certs:
  I-D.ietf-lamps-cert-binding-for-multi-auth:
  ANSI/ASHRAE.Standard.135-2016:
    target: https://webstore.ansi.org/standards/ashrae/ansiashraestandard1352016
    title: >
      BACnetTM A Data Communication Protocol For Building Automation And Control Network
    author:
      org: American National Standards Institute (ANSI)
    date: 2016
    seriesinfo:
      ANSI: Standard 135-2016
  Addendum.bj.to.ANSI/ASHRAE.Standard.135-2016:
    target: https://www.ashrae.org/File%20Library/Technical%20Resources/Standards%20and%20Guidelines/Standards%20Addenda/135_2016_bj_20191118.pdf
    title: >
      Addendum bj to BACnetTM A Data Communication Protocol For Building Automation And Control Network
    author:
      org: American National Standards Institute (ANSI)
    date: 2016
    seriesinfo:
      ANSI: Addendum bj to Standard 135-2016
  bsi.quantum-safe.crypto:
    target: https://www.bsi.bund.de/SharedDocs/Downloads/EN/BSI/Publications/Brochure/quantum-safe-cryptography.pdf?__blob=publicationFile&v=4
    title: >
      Quantum-safe cryptography – fundamentals, current developments and recommendations
    author:
      org: Bundesamt fuer Sicherheit in der Informationstechnik
    date: 2021
    seriesinfo:
      BSI: Recommendations for action by the BSI
  entrust.composite-pki:
    target: https://www.entrust.com/newsroom/press-releases/2024/entrust-introduces-first-commercially-available-post-quantum-ready-pki-platform
    title: >
      Entrust introduces first commerically available post quantum ready pki platform
    author:
      org: Entrust
    date: 2024
  CNSA2-0:
    target: https://media.defense.gov/2022/Sep/07/2003071834/-1/-1/0/CSA_CNSA_2.0_ALGORITHMS_.PDF
    title: >
      Announcing the Commercial National Security Algorithm Suite 2.0
    author:
      org: National Security Agency (NSA)
    date: 2022
  Dilithium.des.team:
    target: https://pq-crystals.org/dilithium/
    title: >
      CRYSTALS-Dilithium design team web page
    author:
      org: CRYSTALS-Dilithium design team
    date: 2023
  Google.Sec.Blog:
    target: https://security.googleblog.com/2023/08/toward-quantum-resilient-security-keys.html?m=1
    title: >
      Toward Quantum Resilient Security Keys
    author:
      org: Google
    date: 2023
  Hybrid.pqc.sig.hsk:
    target: https://doi.org/10.1007/978-3-031-41181-6_26
    title: >
      Hybrid Post-quantum Signatures in Hardware Security Keys
    author:
      - name: Diana Ghinea
      - name: Fabian Kaczmarczyck
      - name: Jennifer Pullman
      - name: Julien Cretin
      - name: Stefan Koebl
      - name: Rafael Misoczki
      - name: Jean-Michel Picod
      - name: Luca Invernizzi
      - name: Elie Bursztein
    date: 2023
  NIST.FIPS.204:
    target: https://csrc.nist.gov/pubs/fips/204/ipd
    title: >
      Module-Lattice-Based Digital Signature Standard
    author:
      org: National Institute of Standards and Technology (NIST)
    date: 2023
    seriesinfo:
      NIST: FIPS 204 (Initial Public Draft)
  NIST.FIPS.205:
    target: https://csrc.nist.gov/pubs/fips/205/ipd
    title: >
      Stateless Hash-Based Digital Signature Standard
    author:
      org: National Institute of Standards and Technology (NIST)
    date: 2023
    seriesinfo:
      NIST: FIPS 205 (Initial Public Draft)
  NIST.SP.800-57.P1R5:
    target: https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-57pt1r5.pdf
    title: >
      Recommendation for Key Management: Part 1 – General
    author:
      org: National Institute of Standards and Technology (NIST)
    date: 2020
    seriesinfo:
      NIST: Special Publication 800-57
  X.509:
    title: >
      Information technology – Open Systems Interconnection – The Directory: Public-key and attribute certificate frameworks
    author:
      org: International Telecommunications Union
    date: 2019
    seriesinfo:
      ITU-T: Recommendation X.509
  CAMM:
    target: http://arxiv.org/abs/2202.07645
    title: >
      Towards a maturity model for crypto-agility assessment
    author:
      - name: Julian Hohm
      - name: Andreas Heinemann
      - name: Alexander Wiesmaier
    date: 2022

--- abstract

This document is meant to be continuously updated, to incorporate emerging Post-Quantum Cryptography (PQC) migration use cases, with a focus on the migration from traditional signature algorithms (e.g., RSA, DSA, ECDSA) to PQC signature algorithms (e.g., LMS, XMSS, ML-DSA, SLH-DSA). This document aims at categorizing real-world scenarios based on a set of distinctive features. The primary goal is to facilitate discussions on migration strategies by offering a systematic taxonomy and a shared understanding among stakeholders.

--- middle

# Introduction

How to transition to post-quantum cryptography is a question likely to stay with us for a considerable period. Within several working groups at the IETF, a variety of strategies are under discussion, gradually finding their way into RFCs. The existence of multiple choices makes it more difficult to select the most suitable approach for any given use case.

For example:

- An Original Equipment Manufacturer (OEM) must issue its products today with manufacturer X.509 certificates that might be used at any time during their lifespan. These certificates will eventually be utilized to enroll in a domain PKI (Public Key Infrastructure). The choice of algorithms and the type of hybrid cryptography to support become critical.

- A PKI must start preparing its CAs today for issuing S/MIME certificates, necessitating the inclusion of hybrid capabilities. The question arises: which path should be pursued?

In this document, intended to be a dynamic resource, our main objective is to compile a list of digital signature use cases and categorize them based on prominent features. Examples include distinguishing between long-lived and short-lived scenarios, whether they include a negotiated protocol, or if backward compatibility is required.

We also explore the migration strategies that have appeared so far, proposing the most suitable fit for each of the properties identified in each use case. Some of these migration strategies make use of hybrid cryptography, i.e., use both traditional and post-quantum cryptography. <!-- There are several concepts for hybrid cryptography. -->

The motivation to take into account hybrid cryptography during the migration phase arises from the requirement of having long-lived assertions, i.e., digital signatures that require long term validation, as well as the uncertainty surrounding the longevity of traditional cryptographic methods and lack of complete trust in emerging PQC algorithms.

An additional factor to consider is represented by the requirements coming from regulatory bodies, which, in several cases will differ among legislations, in regard to post-quantum algorithms and acceptable migration strategies. For example {{bsi.quantum-safe.crypto}}, recommends the incorporation of post-quantum cryptographic algorithms within hybrid cryptographic schemes, as a proactive response to the quantum threat. On the contrary, {{CNSA2-0}} recommends specific post-quantum cryptographic algorithms for each use case.

## Requirements Language

{::boilerplate bcp14-tagged}

# Reference Use Cases {#sec-usecases}

This section is the core of this document. For each use case, we present a concise overview and highlight the features that can help to categorize it. This list is not exhaustive, and if you think we have missed some important use case please consider contributing to it.

## Industrial communication protocols

Several industrial communication protocols, traditionally do not use IP network infrastructure, are progressively being updated to make use of standard IP network infrastructure hence rely on standard security mechanisms, like for example TLS 1.3 {{RFC8446}}.

The protocol 'Building Automation and Control Networks / Secure Connect' (BACnet/SC) {{ANSI/ASHRAE.Standard.135-2016}} is a good example. BACnet was defined before 1995, when the TCP/IP protocol suite was expensive and not available for smaller devices common in building automation. BACnet/SC proposes a new datalink layer option that makes full use of TLS secured WebSocket connections. This new BACnet/SC datalink layer option uses a virtual hub-and-spoke topology where the spokes are WebSocket connections from the nodes to the hub.

BACnet/SC's implementation adheres to established industry standards defined in IETF RFCs. Specifically the {{Addendum.bj.to.ANSI/ASHRAE.Standard.135-2016}} references to text encoding of PKIX, PKCS, and CMS structures in {{RFC7468}}, when defining the format in which operational certificates and signing CA should be installed onto the target device at configuration time.

The security of the BACnet/SC protocol, as well as of similar industrial protocols, relies on TLS 1.3 {{RFC8446}}, therefore implications of post-quantum cryptography have to be considered in both the TLS handshake and in the X.509 certificates used for the authentication.

Lifetime: Long-lived.

Protocol: Active Negotiation.

Backward compatibility: Limited.

## Software and Firmware update

Secure firmware updates are crucial for ensuring long-term security of the device, especially in industrial, and critical infrastructure fields, where devices can stay active for decades. Such updates encompass tasks like introducing new trust anchors and upgrading cryptographic algorithm capabilities. However, upgrading every device's security capabilities isn't always feasible due to resource, accessibility, and cost constraints. Some devices may not support secure firmware updates at all.

Firmware updates are typically authenticated by the Original Equipment Manufacturer (OEM) by means of a digital signing process. An update is distributed to target devices, which will validate its signature against a Trust Anchor (TA). The TA can be an X.509 certificate, a public key, or a hash of a combination of both, depending on the OEM's security measures.

These devices are typically deployed in highly regulated environments, in remote or physically constrained locations where performing upgrades is challenging, or in cases where the cost of upgrading is prohibitively high. The immutability of these devices can also be viewed as a security feature, as it restricts potential attack vectors associated with over-the-air updates. These devices are designed with a long operational lifespan in mind, often spanning several decades. Notable examples of such devices encompass:

- Vehicles - scale of deployment or vehicle recall difficulties.
- Satellites - no 'on-site' service reasonably possible.
- Servers and network devices - air-gapped, locked-down DCs, geographically distributed.
- Government infrastructure - power grids, nuclear power station equipment, etc.
- Smart meters - device owned by the utility company, deployed in private homes.
- Smart cards – used for authenticating to workstations and buildings, or electronic document signing.
- Security Tokens – such as FIDO2, cheap devices that users will typically not patch.

Lifetime: Long-lived.

Protocol: Passive Negotiation.

Backward compatibility: Limited.

## Trust Anchor deployment

Trust Anchors, such as X.509 Root CA certificates and raw public keys, must be made accessible before they can be used for signature validation. In scenarios like remote software updates, a Trust Anchor X.509 certificate, for instance, must be installed on a target device to enable the validation of certificate chains. While deployment of Trust Anchors may be relatively straightforward for "corporate IT" and "public web" applications, it can still be a time-consuming process to ensure that a new Trust Anchor X.509 certificate is propagated throughout the entire ecosystem. Additionally, when dealing with post-quantum Trust Anchors, an extra layer of complexity arises as the desired underlying cryptography may not yet be supported by the target platform.

There are two common variations of this use case.

- Injection within a factory: in industrial contexts, Trust Anchors are typically injected into target devices during the manufacturing phase. To bootstrap a Trust Anchor, the device is placed in a physically secure environment accessible only to trusted personnel. This injection can occur during manufacturing or when a device is being resold. It is important to note that some devices might not support updating the Trust Anchor in the field, requiring the return of the device to the OEM for post-quantum Trust Anchor injection or, in some cases, it may be even not supported at all, because, for example, the Trust Anchor is burnt onto the device at manufacturing time.
- Injection via software and firmware updates: for devices where the Trust Anchor is not burned onto the device, for example in less constrained devices and IT equipment, post-quantum Trust Anchors can be injected through software or firmware update mechanisms. The deployment of these Trust Anchors may leverage existing update mechanisms and traditional cryptography to minimize effort. However, this approach necessitates the distribution of the new Trust Anchors well in advance of any suspicion that traditional cryptography may become vulnerable. Given the lead time required to ensure widespread distribution, the time window where this mechanism is suitable is further reduced.

Lifetime: Long-lived.

Protocol: Passive Negotiation.

Backward compatibility: Limited.

## CMS (S/MIME) {#cms}

The Cryptographic Message Syntax (CMS) {{RFC5652}} establishes a standard syntax for creating secure messages, incorporating digital signatures, encryption, and authentication codes.
In practical terms, CMS finds application in scenarios such as secure email communication, document signing, and PKI-based security services. Organizations use CMS for secure file transfers and end-to-end encryption of documents, ensuring confidentiality and integrity.
It is a key component in secure messaging protocols, contributing to the confidentiality, integrity, and authenticity of communication over networks. One of the notable features of CMS is flexibility, allowing the choice of cryptographic algorithms based on specific security requirements.
An important consideration to be made is the non-uniform adoption and potential challenges in implementing CMS, particularly in the context of email clients. Varying levels of maturity and maintenance among email clients will slow down the adoption of post-quantum algorithms, which will not be uniform across different clients.

It is worth noting that, similarly to CMS, JOSE and (JSON Object Signing and Encryption) and COSE (CBOR Object Signing and Encryption) are data structures used to support signing and encryption of data, respectively, in JSON and CBOR format. Therefore, several considerations that are applicable for CMS will extend to JOSE and COSE as well.

Lifetime: Short-lived and long-lived.

Protocol: Passive Negotiation.

Backward compatibility: Mandatory.

## Timestamping

A time-stamping service supports assertions of proof that a datum existed before a particular time, as defined in {{RFC3161}}.
Timestamps, are particularly important in the following scenarios.

- Code and Document Signing: In code and document signing use cases, timestamps play a critical role in ensuring the ongoing validity of digital signatures. It is not sufficient to validate the signature at the time of creation; it must be verifiable even after the signature certificate has expired. This is particularly important for long-term archival and verification purposes, where the historical integrity of the signed code or document needs to be maintained over time. The timestamp is stored in a CMS data structure, cf. {{cms}}.
- Non-repudiation: timestamps enhance non-repudiation by preventing parties from later denying the authenticity or validity of their digital signatures. Non-repudiation plays a major role in Legal and regulatory compliance, Intellectual property protection and Electronic commerce, where the reliability of timestamps is key for establishing clear timelines with legal and financial implications.

Lifetime: Long-lived.

Protocol: Passive Negotiation.

Backward compatibility: Optional.

<!--
## OAuth
TODO

## SUIT Manifest
TODO
-->

## Additional use cases

Future updates of this document may include use cases which cover additional aspects, such as FAA airworthiness certifications, medical records, etc.

# Post-quantum Migration Strategies for Signing

People are considering which technological concepts are suitable to solve the problem of a secure migration from classical cryptography to quantum computer safe cryptographic algorithms. A variety of approaches are being discussed. In the following, we would like to briefly introduce the approaches under discussion and refer to the respective relevant documents for further details.
For a general introduction, we also refer to {{I-D.ietf-pquip-pqc-engineers}}.

## Multiple Signatures

Several signatures have the approach of defining a second alternative signature in addition to the primary signature in the protocol or format, which can be transported in the protocol or format. In addition to the definition of the alternative signature, the associated signing algorithm and, if applicable, the associated public key or a reference to it must also be transferred. For X.509 public key certificates, this is defined in {{X.509}}. Work is also underway for other protocols and formats. This approach overlaps with the protocol and format extension approach described in {{protocols}}.

An alternative approach is to encode a second signature in a second certificate and bind it to the first one by a reference. For example, an implementation can decide based on its policy whether only the first certificate or the second or both certificates should be used for authentication. Further descriptions of this approach can be found in A Mechanism for Encoding Differences in Paired Certificates {{I-D.bonnell-lamps-chameleon-certs}} and Related Certificates for Use in Multiple Authentications within a Protocol {{I-D.ietf-lamps-cert-binding-for-multi-auth}}.

## Composite Signatures

The goal of composite signatures is to define a signature object to be used with any protocol or format. It contains two signatures in a single atomic container that have been generated using two different cryptographic algorithms. The goal of this approach is to define a signature format which requires both contained signatures to be verified.  In this way, the security properties of the classical signature and another signature that is secure when attacked by a quantum computer are used in the protocol or format without having to adapt them.

In order for this approach to be applicable in arbitrary protocols and formats, a composite key must be defined in addition to the composite signature. According to the definition of composite signatures, a composite public is a single atomic container composed of two public keys. The associated composite private key is a single atomic private key that is composed of the two private keys which correspond to the two public keys contained in the composite public key.

This concept is described in Composite Signatures For Use In Internet PKI {{I-D.ounsworth-pq-composite-sigs}} in more detail.

## Employing Stateful Hash-based Signature Schemes

Stateful hash-based signature (HBS) schemes, such as XMSS {{RFC8391}} and LMS {{RFC8554}}, including their multi-tree variants, have been the first post-quantum algorithms to be standardized by NIST in {{NIST.SP.800-208}}.
Stateful HBS algorithms offer better key and signature sizes than stateless HBS algorithms, and the underlying cryptographic building blocks are generally considered well-understood. However, a critical consideration is the management of state, which is a fundamental aspect of security. The absence of standardized operating procedures for state management poses challenges to the adoption of stateful HBS. This is especially critical when signing data over extended periods using the same key pair; i.e., the resulting signatures will be validated with the same public key over a long period of time.
Another aspect worth considering is that, without solutions for hardware security module replacements and disaster recovery scenarios, using stateful HBS might lead to a solution with limited resilience.

## Employing Stateless Hash-based Signature Schemes

{{NIST.FIPS.205}} specifies the SLH-DSA (SPHINCS+) algorithm.  It is a stateless hash-based signature algorithm and is considered safe against attacks by quantum computers.  The advantage of this algorithm is that the state problem is resolved as part of the algorithm.  However, the tradeoff is that signature sizes are often an order of magnitude larger than XMSS or LMS.  This may make deploying these algorithms on constrained devices infeasible.

## Employing Module-Lattice-Based Digital Signature Schemes

{{NIST.FIPS.204}} specifies the ML-DSA (Dilithium) algorithm, a digital signature algorithm based on the hardness of lattice problems over module lattices. It serves as a general purpose post-quantum signature algorithm, offering smaller key sizes in comparison to SLH-DSA and fast signature generation. For more details, refer to {{I-D.ietf-pquip-pqc-engineers}}.

## Cryptographic Agility {#protocols}

Migration to post-quantum cryptographic algorithms can be regarded as an instance of the general pattern of *cryptographic agility*, rather than be viewed as a special, one-off event. A system that approaches migration this way can undergo multiple transitions without requiring major architectural changes. Thus, when planning the transition to post-quantum cryptography, consider that when future cryptanalysis will trigger a transition to *post-post-quantum* cryptography, it is better to be agile than to start from scratch.

Hohm et al. identified circa 30 interpretations of the term "cryptographic agility" in their literature survey {{CAMM}}, therefore referring to agility without defining it brings the potential of being misunderstood. In this document, we encourage readers to reason about agility by relying on these guiding questions:

1. Can one **select** algorithms based on a specific context?
2. Can one **add** new cryptographic primitives or parameters?
3. Can obsolete crypto be **retired**?

System and protocol designers can adjust the definition for their particular context, while ensuring that the adjusted definition is clearly stated, to avoid ambiguities.


Agility in security protocols and message formats, such as IP Security (IPsec) and Internet Key Exchange (IKE) {{RFC6071}}, Transport Layer Security (TLS){{RFC8446}}, Secure/Multipurpose Internet Mail Extensions (S/MIME){{RFC8551}}, is understood as the dynamic referencing of the algorithms to be used - the "select" component above. A migration strategy that allows the existing and future cryptographic algorithms to be used simultaneously during a transition period (the "add" part) is not described in the respective standards.

Revised versions of standards would be needed to integrate agility into protocols and formats. This requires effort for standardization and implementation if a basic functionality, such as multiple signatures, e.g., in Cryptographic Message Syntax (CMS) {{RFC5652}}, is not already available. But even in the case of S/MIME and CMS, profiling is still necessary to describe how the multiple signatures are to be used specifically for the migration.

# Map of Migration Strategies to Reference Use Cases

In this section, we establish a mapping between the reference use cases and their primary features, as summarized in the table below, and the digital signature migration strategies identified in the preceding section.

| Use Case                           | Lifetime                   | Protocol            | Backward Compatibility |
|------------------------------------|----------------------------|---------------------|------------------------|
| Industrial communication protocols | Long-lived                 | Active Negotiation  | Limited                |
| Software and Firmware update       | Long-lived                 | Passive Negotiation | Limited                |
| Trust Anchor deployment            | Long-lived                 | Passive Negotiation | Limited                |
| CMS (S/MIME)                       | Short-lived and Long-lived | Passive Negotiation | Mandatory              |
| Timestamping                       | Long-lived                 | Passive Negotiation | Optional               |
{: title="Summary of use cases and main features"}

The map is constructed as a decision tree, which is available at: <https://github.com/avaira77/pq-ietf-usecase/tree/main/flowchart>.

# IANA Considerations {#IANA}

This memo includes no request to IANA.

# Security Considerations {#Security}

This document should not affect the security of the Internet.

--- back

# Post-Quantum Migration Properties

This section aims to establish a collection of characteristics for categorizing the use cases outlined in {{sec-usecases}}. The objective is to enhance the document's utility by providing a framework for classifying use cases not explicitly addressed here. For instance, implementors can categorize their own use case and subsequently identify a similar one in this document based on shared properties/classification.

##Lifetime
This classification distinguishes between short-lived and long-lived use cases. However, in practical terms, this distinction is challenging due to the nature of each use case's lifespan, which can be on a spectrum.

1. Short-lived: In this context, a short-lived use case is characterized by a duration of less than 5 years. This timeframe aligns with common organizational practices, where hardware, for example servers in a data center, is typically replaced within a 5-year cycle.
2. Long-lived: In the context of this document, a long-lived use case spans more than 10 years. While there isn't a specific rationale for this timeframe, it is noteworthy that cryptographic recommendations, for example {{NIST.SP.800-57.P1R5}}, often provide guidance for a duration of up to ten years from the time of their publication.

##Protocol
Cryptographic protocols can be divided in Active Negotiation (real-time cryptography), Passive Negotiation (asynchronous cryptography), and Non Agile (no graceful migration).

1. Active Negotiation: Protocols with existing mechanisms for real-time cryptographic negotiation such as TLS and IKE already contain mechanisms for upgraded clients to downgrade the cryptography in a given session in order to communicate with a legacy peer. These protocols provide the easiest migration path as these mechanisms should be used to bridge across traditional and post-quantum cryptography.
2. Passive Negotiation: Protocols with existing mechanisms for non-real-time or asynchronous cryptographic negotiation. For example a PKI end entity who publishes multiple encryption certificates for themselves, each containing a public key for a different algorithm, or code signing object carrying multiple signatures on different algorithms.
3. Non-agile: Non-agile or flag day implies no graceful migration is possible; the community decides that as of a certain date legacy clients will no longer be able to interoperate with upgraded clients.

##Backward compatibility
The following scenarios may arise:

1. Optional: Backward compatibility isn't needed, either because post-quantum migration is unnecessary or already addressed within a specific protocol.
2. Limited: Backward compatibility is necessary for a defined period, such as during a migration time window.
3. Mandatory: Backward compatibility is essential throughout the use case's entire lifespan due to the absence of identifiable migration strategies.

# Composite Signature individual and organization position statements

1. BSI - The document {{bsi.quantum-safe.crypto}} recommends requiring that PQC lattice schemes only be used within a PQ/T hybrid.  More specifically this document includes the following recommendation:

    "Therefore, quantum computer-resistant methods should not be used alone - at least in a transitional period - but only in hybrid mode, i.e. in combination with a classical method. For this purpose, protocols must be modified or supplemented accordingly. In addition, public key infrastructures, for example, must also be adapted"

    Also Stavros Kousidis from BSI says: "from a strategic point of view we don’t want to replace our current RSA algorithm with standalone Dilithium since: If Dilithium does not withstand cryptanalysis in the future then all our efforts are for nothing. With a composite signature Dilithium+ECDSA in AND-mode we can buy ourselves some time in case the Dilithium security guarantees do not withstand future cryptanalysis."

2. Google: according to {{Google.Sec.Blog}}: "Relying on a hybrid signature is critical as the security of Dilithium and other recently standardized quantum resistant algorithms haven’t yet stood the test of time and recent attacks on Rainbow (another quantum resilient algorithm) demonstrate the need for caution. This cautiousness is particularly warranted for security keys as most can’t be upgraded – although we are working toward it for OpenSK. The hybrid approach is also used in other post-quantum efforts like Chrome’s support for TLS".

3. Entrust: During the transition to post-quantum cryptography, there will be uncertainty as to the strength of cryptographic algorithms; we will no longer fully trust traditional cryptography such as RSA, Diffie-Hellman, DSA and their elliptic curve variants, but we will also not fully trust their post-quantum replacements until they have had sufficient scrutiny and time to discover and fix implementation bugs. Unlike previous cryptographic algorithm migrations, the choice of when to migrate and which algorithms to migrate to, is not so clear.  Even after the migration period, it may be advantageous for an entity's cryptographic identity to be composed of multiple public-key algorithms.
In 2024 Entrust added support for composite signatures in PKI infrastructure ({{entrust.composite-pki}}):

    "With this launch, the company’s cloud-based PKI as a Service offering now can provide both composite and pure quantum-safe certificate authority hierarchies, enabling customers to test or implement quantum-safe scenarios and infrastructure."

4. Robert Hulshof: "The rationale behind combined keys is that I can see an important use-case for very sensitive data (government, financial or other high value data) to combine multiple (PQ) key algorithms, and that this migration to PQ is a good time to start supporting that by default in the crypto libraries.
Trying to estimate the probability that a NIST standardized Crypto algorithm gets broken in the next 5-10 years is very difficult. However I assume that everybody agrees that this probability is definitely not zero. Personally I would put that probability somewhere in the range of 0.1% – 1%.
If I were the government/bank etc. I would not like to have a 1% risk that all my secrets get exposed. Adding one or two more PQ algorithms would reduce that probability to 1 in 5 million or 1 in a Billion would be much more acceptable."

5. MTG - Falko Strenzke: "Without hybrid signatures, a decision to move away from traditional signatures to Dilithium (or other non-hash-based signatures) has a certain risk to make things worse and I think many decision makers will not be ready to take the responsibility for it until the quantum computer threat becomes imminent. If composite signature is not standardised, non-composite hybrids would be left. This implies protocol changes which will:
    1. need more discussion,
    2. need more changes to existing applications,
    3. and thus be more bug prone.
    4. Not having hybrid signatures at all will likely cause many decision makers to
    5. use hash-based schemes where possible / affordable
    6. and elsewhere stick to traditional schemes as long as possible, thus effectively delaying the migration to PQC."

6. Transmute - Orie Steele: "There are use cases for long lived verifiable credentials, and attribute cert like stuff we work on in supply chain, with DHS / CBP."

7. CRYSTALS-Dilithium design team states in {{Dilithium.des.team}} that: “For users who are interested in using Dilithium, we recommend the following: Use Dilithium in a so-called hybrid mode in combination with an established "pre-quantum" signature scheme.”
8. Hybrid Post-Quantum Signatures in Hardware Security Keys: the paper {{Hybrid.pqc.sig.hsk}} describes a hybrid signature scheme. Below an excerpt from it:
“A hybrid signature scheme combines a classical signature algorithm with a post-quantum secure signature algorithm. Before discussing the design of our hybrid scheme, we explain why such an approach is relevant instead of simply replacing classically secure schemes with post-quantum secure schemes. We present the assumptions below:
    1. Cryptographically-Relevant Quantum Computers (i.e. with enough qubits to break ECDSA) are not available yet.
    2. Classical signature algorithms withstands attacks from classical computers.
    3. The post-quantum secure signature algorithm might be breakable by classical computers due to design or implementation bugs.
If any of these assumptions fails, using a hybrid approach instead of replacing classical schemes with post-quantum schemes indeed does not add any security. We believe that all of these assumptions are currently correct. The third assumption is motivated by a newly discovered attack against Rainbow, one of the NIST standardization finalists.
We can now discuss the informal requirements a hybrid scheme H should satisfy:
    1. If a quantum computer becomes available, and hence H’s underlying classical scheme is broken, H should maintain the security of its underlying post-quantum scheme.
    2. If a classical attack for H’s underlying post-quantum secure scheme is discovered, H should maintain the security of its underlying classical scheme."

# Acknowledgements {#Acknowledgements}
{: numbered="false"}

This draft would not be possible without the support of a great number of contributors.   We thank Stavros Kousidis, Robert Hulshof, Falko Strenzke and Orie Steele for allowing us to use their statements regarding composite signatures.
