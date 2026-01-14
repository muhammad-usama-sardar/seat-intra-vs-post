---
title: "Pre-, Intra- and Post-handshake Attestation"
abbrev: "TODO - Abbreviation"
category: info

docname: draft-usama-seat-intra-vs-post-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Security"
workgroup: "Secure Evidence and Attestation Transport"
keyword:
 - remote attestation
 - TLS 1.3
 - attested TLS
venue:
  group: "Secure Evidence and Attestation Transport"
  type: "Working Group"
  mail: "seat@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/seat"
  github: "muhammad-usama-sardar/seat-intra-vs-post"
  latest: "https://muhammad-usama-sardar.github.io/seat-intra-vs-post/draft-usama-seat-intra-vs-post.html"

author:
 -
    fullname: "Muhammad Usama Sardar"
    organization: TU Dresden
    email: "muhammad_usama.sardar@tu-dresden.de"

normative:

informative:
  RFC9334: rfc9334
  Tech-Concepts:
     title: "Perspicuity of Attestation Mechanisms in Confidential Computing: Technical Concepts"
     date: October 2025,
     target: https://www.researchgate.net/publication/396199290_Perspicuity_of_Attestation_Mechanisms_in_Confidential_Computing_Technical_Concepts
     author:
      - ins: M. U. Sardar
  I-D.ietf-tls-rfc8446bis:
  ID-Crisis:
    title: "Identity Crisis in Confidential Computing: Formal Analysis of Attested TLS"
    date: November 2025,
    target: https://www.researchgate.net/publication/398839141_Identity_Crisis_in_Confidential_Computing_Formal_Analysis_of_Attested_TLS
    author:
      - ins: M. U. Sardar
      - ins: M. Moustafa
      - ins: T. Aura
  RA-TLS:
    title: "Towards Validation of TLS 1.3 Formal Model and Vulnerabilities in Intel's RA-TLS Protocol"
    date: 13 November 2024,
    target: https://www.researchgate.net/publication/385384309_Towards_Validation_of_TLS_13_Formal_Model_and_Vulnerabilities_in_Intel's_RA-TLS_Protocol
    author:
      - ins: M. U. Sardar
      - ins: A. Niemi
      - ins: H. Tschofenig
      - ins: T. Fossati
  RelayAttacks:
     title: "Relay Attacks in Intra-handshake Attestation for Confidential Agentic AI Systems"
     date: 11 January 2026,
     target: https://mailarchive.ietf.org/arch/msg/seat/x3eQxFjQFJLceae6l4_NgXnmsDY/
     author:
     - ins: M. U. Sardar
  I-D.jiang-seat-dynamic-attestation:
  SEAT-Charter:
     title: "Secure Evidence and Attestation Transport (SEAT): Charter for Working Group"
     date: 2025,
     target: https://datatracker.ietf.org/wg/seat/about/
     author:
      - ins: IETF
  MCR-LAKE:
     title: "Comments for remote attestation over EDHOC"
     date: 25 May 2024,
     target: https://mailarchive.ietf.org/arch/msg/lake/RseQknOug41sTzW7xBJ60oRdvq0/
     author:
      - ins: Michael Richardson
  Goran-LAKE:
     title: "Comments for remote attestation over EDHOC"
     date: 28 May 2024,
     target: https://mailarchive.ietf.org/arch/msg/lake/Bb3eTcQxDA-F1AYJ0hZZy3p9wpQ/
     author:
      - ins: Göran Selander
  Keith-STET-CCC:
     title: "Split-Trust Encryption Tool Attested Session Handling"
     date: 15 March 2022,
     target: https://github.com/CCC-Attestation/meetings/blob/main/materials/KeithMoyer_STET.pdf
     author:
      - ins: Keith Moyer
  Stunes-vTPM-CCC:
     title: "Azure vTPM Attestation and Binding"
     date: 29 July 2025,
     target: https://www.youtube.com/watch?v=J7SibeZmQsE
     author:
      - ins: Mike Stunes
  SoK-Attestation:
    title: "SoK: Attestation in Confidential Computing"
    date: January 2023,
    target: https://www.researchgate.net/publication/367284929_SoK_Attestation_in_Confidential_Computing
    author:
      - ins: M. U. Sardar
      - ins: T. Fossati
      - ins: S. Frost

...

--- abstract

This document presents a taxonomy of extending TLS protocol with remote attestation,
referred to as attested TLS. It also presents high-level analysis of the three potential options for
attested TLS, namely pre-handshake
attestation, intra-handshake
attestation and post-handshake attestation.


--- middle

# Introduction

Based on our extensive analysis of attested TLS {{Tech-Concepts}},
we classify attested TLS into three main categories:

* pre-handshake attestation,
* intra-handshake attestation, and
* post-handshake attestation.

In pre-handshake attestation, the signing of Claims {{Tech-Concepts}} precedes the
TLS handshake, while post-handshake attestation applies the reverse.
Intra-handshake attestation requires the signing of Claims to
be done within the TLS handshake protocol.

We note that:

{:quote}
>  Remote attestation provides guarantees about the state of
Attester **only** at the time at which signing of Claims
is done to generate Evidence {{Tech-Concepts}}.


# Conventions and Definitions

{::boilerplate bcp14-tagged}

We use terminology from {{-rfc9334}} and {{I-D.ietf-tls-rfc8446bis}}.

In addition, we define three temporal terms:

* **Evidence Generation Time**: Time when Evidence is generated (more specifically when Claims are signed)

* **Connection Establishment Time**: Time at which TLS handshake is performed

* **Lifetime of Connection**: Time period starting from Evidence Generation Time until the connection exists.


# Pre-handshake Attestation

Since the Evidence Generation Time could be at any
arbitrary point of time in the past compared to the connection
establishment time, pre-handshake attestation provides no guarantees about the state of Attester
at the Evidence Generation Time and during the Lifetime of Connection.

# Intra-handshake Attestation
Intra-handshake attestation improves the situation where Evidence Generation Time
is the same as Evidence Generation Time.


[comment]: <> (If RA appraisal succeeds, client and server agree on current transcript hash. We do not have all guarantees about authentication and security of the connection at the point at which the Evidence is conveyed.)


## Benefits

### No Changes at Application Layer
It does not require any changes in application layer.

### Avoids Extra Round Trips
It avoids extra round trips for use cases which require remote attestation only once
during Connection Establishment Time.


## Limitations

### Limited Claims Availability
Since limited Claims are available at the Evidence Generation Time, it does not provide
complete security posture of the Attester, such as runtime integrity of Attester.

### Invasive Changes in TLS
To be made secure, it requires invasive changes in TLS protocol, as deep as key
schedule and adding or modifying existing handshake messages {{ID-Crisis}}.

### State After Connection Establishment Not Covered
It provides no guarantees about the state of Attester during the lifetime
of connection. This is a security concern in long-lived connections where
state of Attester may change after Connection Establishment Time.

### High Handshake Latency
Because of signature in Evidence generation and verification of signatures during appraisal,
this leads to high handshake latency. This may not be desirable for some applications.


# Post-handshake Attestation

Post-handshake attestation improves the situation further by signing the Claims
during Lifetime of Connection, i.e., at the time when it is actually required.
Hence, together with use cases requiring one-time attestation, it covers the use cases of
long-lived connections requiring re-attestation.
For post-handshake attestation, first round of remote attestation MUST be done
immediately after Connection Establishment Time, and Relying Party (RP)
{{-rfc9334}} MUST not send any secure data until Evidence is successfully appraised.

## Benefits

In general, it allows re-authentication and re-attestation without tearing down the connection.

### Full Claims Availability
Since all Claims are available at the time of post-handshake attestation (during
Lifetime of Connection), it provides complete security posture of the Attester.

### No Change in TLS
It does not require any change in TLS protocol.

### State After Connection Establishment Is Covered
It provides guarantees about the state of Attester during the Lifetime of Connection.
This is particularly helpful in long-lived connections where
state of Attester may change after Connection Establishment Time.

### Standard Handshake Latency
Since the signature in Evidence generation and verification of signatures during appraisal
happen after Connection Establishment Time, there is no additional latency.

### Avoids Extra Round Trips
Except for first round of remote attestation, post-handshake attestation outperforms the
intra-handshake attestation (one round trip), which requires re-establishing the connection
(1.5 round trip).

## Limitations

### Changes at Application Layer
It may require changes in application layer. Note that changes in application layer does not
necessarily mean changes in application logic itself.


# Need for Post-handshake Attestation
We argue that post-handshake attestation is unavoidable (e.g., re-attestation to
track changes after Connection Establishment Time for long-lived connections).
Use cases where pre-handshake attestation and intra-handshake attestation are
insufficient include include AI agents/agentic AI {{I-D.jiang-seat-dynamic-attestation}}.

Intra-handshake attestation only adds unnecessary complexity which is avoidable.
All use cases of intra-handshake attestation can be covered by post-handshake
attestation (by doing attestation round immediately after Connection Establishment Time)
but not the other way around.

## IoT Constraints

{{SEAT-Charter}} includes TLS client as RATS Attester. Client could be a low-power IoT device.
There are use cases where periodic
or on-demand attestation is required, such as periodic
attestation for long-lived, low-power IoT devices or in IoT
swarms that need to synchronize software versions before
coordinated operations or after configuration updates.


Moreover, we note some observations from LAKE WG:

Michael Richardson shares his insight {{MCR-LAKE}}:

{:quote}
>  I have a half-written document on putting EAT into the full BRSKI protocol.
A reason that I stopped is that I realized that doing security posture
evaluation at onboarding time (only) wasn't enough.  It has to be done
regularly.  So having a protocol used at onboarding time and another one
during normal operation meant that the onboarding one would have bugs that
never get fixed, since the code only runs once.


Göran Selander observes {{Goran-LAKE}}:

{:quote}
>  Indeed, if the authentication procedure is repeated at a later stage, for
whatever reason, e.g. key rotation, it should be possible to repeat the attestation procedure.

# Existing Implementations

## Intra-handshake Attestation
Prominent implementations of intra-handshake attestation are all vulnerable to
relay attacks {{RelayAttacks}}. Some of them are abusing the extensions of TLS, such as
SNI and ALPN, for conveyance of attestation nonce {{RelayAttacks}}.

## Post-handshake Attestation
Google {{Keith-STET-CCC}}, Microsoft {{Stunes-vTPM-CCC}}, and SCONE {{SoK-Attestation}}
are all using post-handshake attestation.


# Security Considerations

Most of the document is about security considerations. Also,
Security Considerations of {{-rfc9334}} and {{I-D.ietf-tls-rfc8446bis}} apply. In addition:

* Pre-handshake attestation is vulnerable to **replay** {{RA-TLS}} and **diversion**
{{ID-Crisis}} attacks.
* Without significant changes to the TLS protocol: Intra-handshake attestation is
vulnerable to **diversion** attacks {{ID-Crisis}}. It also does not bind the Evidence
to the application traffic secrets, resulting in **relay** attacks {{RelayAttacks}}.
* No attacks on post-handshake attestation are currently known. Post-handshake attestation
avoids replay attacks by using fresh attestation nonce. Moreover, it avoids diversion and relay attacks
by binding the Evidence to the underlying TLS connection.

## Exploit of Sensitive Hardware-level Information

From the view of the TLS server, post-handshake attestation offers better security
than intra-handshake attestation when the server acts as the Attester. In intra-handshake
attestation, due to the inherent asymmetry of the TLS protocol, a malicious TLS client
could potentially retrieve sensitive hardware-level information from the Evidence **without
the client's trustworthiness (i.e., authentication) first being established by the server**.
This information (e.g., vulnerable firmware version) can be exploited for attacks.
In post-handshake attestation, the server can ask for client authentication and only
send the Evidence after successful client authentication.


# IANA Considerations

This document has no IANA actions.


--- back

# Acknowledgments
{:numbered="false"}

We gratefully thank Peg Jones and Pavel Nikonorov for review and useful feedback.
