---
title: "Pre-, Intra- and Post-handshake Attestation"
abbrev: "Intra-vs-post"
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
  RFC9261: rfc9261
  RFC9266: rfc9266
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
     title: "Re: Comments for remote attestation over EDHOC"
     date: 25 May 2024,
     target: https://mailarchive.ietf.org/arch/msg/lake/RseQknOug41sTzW7xBJ60oRdvq0/
     author:
      - ins: Michael Richardson
  MCR-LAKE2:
     title: "Evaluation of attestation results by EDHOC clients"
     date: 5 June 2024,
     target: https://mailarchive.ietf.org/arch/msg/lake/o2oujiDacHm2m9a5y7W50oUsY7o/
     author:
      - ins: Michael Richardson
  Goran-LAKE:
     title: "Re: Comments for remote attestation over EDHOC"
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
  Ayoub-16Jan:
     title: "Re: New Version Notification for draft-usama-seat-intra-vs-post-00.txt"
     date: 16 January 2026,
     target: https://mailarchive.ietf.org/arch/msg/seat/8eynK9ky5F-TcnL_UPbSRDKuK1E/
     author:
      - ins: Ayoub Benaissa
  Markus-16Jan:
     title: "Re: New Version Notification for draft-usama-seat-intra-vs-post-00.txt"
     date: 16 January 2026,
     target: https://mailarchive.ietf.org/arch/msg/seat/Pxr_12v6MIQIzGFTUdx04aVZYpM/
     author:
      - ins: Markus Rudy
  Usama-TLS-26Feb25:
     title: "Impersonation attacks on protocol in draft-fossati-tls-attestation (Identity crisis in Attested TLS) for Confidential Computing"
     date: 26 February 2025,
     target: https://mailarchive.ietf.org/arch/msg/tls/Jx_yPoYWMIKaqXmPsytKZBDq23o/
     author:
      - ins: Muhammad Usama Sardar
  ID-Crisis-Repo:
     title: "Identity Crisis in Confidential Computing: Formal analysis of attested TLS protocols"
     date: 2025,
     target: https://github.com/CCC-Attestation/formal-spec-id-crisis
     author:
      - ins: Muhammad Usama Sardar


...

--- abstract

This document presents a taxonomy of extending TLS protocol with remote attestation,
referred to as attested TLS. It also presents high-level analysis of benefits and limitations of each
category, namely pre-handshake attestation, intra-handshake attestation and post-handshake attestation.


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

## Scope

In this version, we analyze the three categories (without combinations) with a focus on the last two, i.e., intra-handshake attestation and post-handshake attestation.

The current scope of this draft is existing specifications and real-world implementations pointed in the
given references. Any theoretical solutions are currently out of scope until some specification or
implementation emerges.

For simplicity, we consider simple Attester with only one Attesting Environment and only one Target
Environment {{-rfc9334}}. That is, complicated scenarios such as Composite Device
{{-rfc9334}} etc. are out of scope in this version.

From RATS perspective, we consider Background Check Model {{-rfc9334}}. Future versions will add
Passport Model {{-rfc9334}}.

From TLS perspective, the scope is limited to TLS 1.3 as per {{SEAT-Charter}}.
That is, older versions of TLS are explicitly out of scope.

## Note
Regarding remote attestation, we note that:

{:quote}
>  Remote attestation provides guarantees about the state of
Attester **only** at the time at which signing of Claims
is done to generate Evidence {{Tech-Concepts}}.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

We use terminology from {{-rfc9334}} and {{I-D.ietf-tls-rfc8446bis}} slightly loosely (intentionally)
for readability. Future versions will tighten it.

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
is the same as Connection Establishment Time.

In following subsections, we present the benefits and limitations of intra-handshake attestation.

[comment]: <> (If RA appraisal succeeds, client and server agree on current transcript hash. We do not have all guarantees about authentication and security of the connection at the point at which the Evidence is conveyed.)


## Benefits

### No Additional Application-Level Protocol
{: #sec-intra-app-changes }
[comment2]: <> (It may not require any changes in application layer.)

Intra-handshake attestation does not require a new application-layer protocol or message exchange.
Evidence and related metadata are conveyed within handshake via TLS extensions.
TLS is responsible for conveyance of the Evidence; it does not perform appraisal of Evidence or authorization.
Appraisal of Evidence, policy evaluation, and trust decisions are performed by application-level components that
consume the attestation properties exposed by the TLS stack. As a result, while no new application-layer protocol
is required, applications do incorporate additional trust logic to interpret attested connection properties
and make security-relevant decisions.


### Avoid Extra Round Trips for One-time Attestation
It is claimed that intra-handshake attestation avoids extra round trips
for use cases which require remote attestation only once
during Connection Establishment Time.

However, this may only be valid in cases when the Connection Establishment
Time without remote attestation is significantly higher than the time
for generation and appraisal of Evidence.
For instance, Markus Rudy shares his practical experience {{Markus-16Jan}}:

{:quote}
>  I don't think saving extra roundtrips is an appropriate design
goal when attestation is required. Generating evidence alone takes
much longer than normal network roundtrip times, not even speaking
of verification.

Our experiments also support his practical experience. In our experience,
the generation of Evidence for Infineon Optiga SLB 9670,
a discrete hardware TPM (dTPM) implementing TPM 2.0, takes around 210 ms.
In our experience, the generation of Evidence for AMD SEV-SNP takes around
6 ms.

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
state of Attester may change after Connection Establishment Time. Note that session
resumption is a new connection {{I-D.ietf-tls-rfc8446bis}}.

### High Handshake Latency
Because of signature in Evidence generation and verification of signatures during appraisal,
this leads to high handshake latency. This may not be desirable for some applications.

Markus Rudy shares his practical experience {{Markus-16Jan}}:

{:quote}
>  Conveying the evidence is not enough, it needs to be verified as well
in order to end up with a trustworthy channel. We decided to integrate
verification into the handshake, too, but that has massive drawbacks:
Verification can take orders of magnitude longer than normal TLS handshakes,
and usually involves remote calls, affecting all sorts of timeouts.
However, doing the verification at the application level would require
forwarding information from the handshake (e.g. nonce), at which point
the application needs to be fully aware of the handshake protocol in
order to verify it, breaking the intended layering.


### Maturity of TEEs
With several attacks (see {{sec-sec-cons}}), attestation in
TEEs may not yet be mature enough to be integrated *within* TLS handshake.

Ayoub Benaissa remarks {{Ayoub-16Jan}}:

{:quote}
>  TLS might not be well suited to include this in its protocol. Not sure
TEEs are even as mature for the people to see that it should be included
right now. The plan to make it a post-handshake protocol makes more sense
right now. A future where it's incorporated into TLS might exist, but I
don't think there is enough motivation right now.

### Amount of Effort

Markus Rudy shares his practical experience {{Markus-16Jan}}:

{:quote}
>  "Keeping attestation out of the application logic" is not as straightforward
as it sounds. In the background-check model, the attester needs to collect
evidence in response to the relying party's challenge (nonce). We were
lucky that the Golang TLS stack can be supplied with arbitrary closures
that are called during the handshake, but in my experience this is a rare
design choice and may also be difficult to implement in other languages.

Ayoub Benaissa remarks {{Ayoub-16Jan}}:

{:quote}
>  An intra-handshake requires much more work compared to a post-handshake.
People need to agree on how to add this as optional in TLS (we can't force
everyone to use it of course), the standard needs to be implemented by
major libraries, and then it will be available in major client/server
applications. If any of the prior steps doesn't go through, it means you
have to patch your components to make it work, which is not convenient /
less secure.

### Difficulty of Debugging Attestation

Markus Rudy shares his practical experience {{Markus-16Jan}}:

{:quote}
>  There's only so much information in a TLS alert message, and it's
definitely not enough to understand remote verification failures.
While I understand this to be a deliberate design choice by TLS,
I found this to be a hindrance for operating and debugging a large
number of services in practice.

# Post-handshake Attestation

Post-handshake attestation improves the situation further by signing the Claims
during Lifetime of Connection, i.e., at the time when it is actually required.
Hence, together with use cases requiring one-time attestation, it covers the use cases of
long-lived connections requiring re-attestation.
For post-handshake attestation, first round of remote attestation MUST be done
immediately after Connection Establishment Time, and Relying Party (RP)
{{-rfc9334}} MUST not send any secure data until Evidence is successfully appraised.

In following subsections, we present the benefits and limitations of post-handshake attestation.

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

### Avoid Extra Round Trips
Except for first round of remote attestation, post-handshake attestation outperforms the
intra-handshake attestation (one round trip), which requires re-establishing the connection
(1.5 round trip).

### Ease of Implementation
Ayoub Benaissa remarks {{Ayoub-16Jan}}:

{:quote}
>  We already implemented a post-handshake protocol and have a full demo
working. We were able to do this in a matter of weeks. That's because you
don't need to modify any TLS implementation, but only add a few
verification steps after the usual TLS handshake. This is almost the same
on the client and server side.

### Ease of Verification and Audit
Post-handshake attestation has relatively easier formal analysis and
verification. The same may apply to audit.

Markus Rudy remarks {{Markus-16Jan}}:

{:quote}
>  (Formal) verification of a protocol and audit of its implementations
might be much easier if it ran on top of TLS. Existing proofs and
certifications would not need to be reevaluated.


### General Solution for Other Protocols
In post-handshake attestation, design, verification and audit effort
will be one-time and any protocol
(e.g., Noise) which has support for exporters can then use it without
changing each and every protocol.

Markus Rudy shares this requirement {{Markus-16Jan}}:

{:quote}
>  It should be possible to port the general shape of a post-handshake
attested TLS protocol to other protocols that provide secure channels
and session binding (Noise comes to mind).


## Limitations

### Impact on Application Layer
{: #sec-post-app-changes }
Post-handshake attestation may require changes at the application layer. However, changes at
the application layer do not necessarily imply modifications to application business logic
or data exchange protocols. Attestation-related functionality may be realized via application-level
signalling (Exported Authenticators {{-rfc9261}}) and trust logic, which may be implemented in
intermediary components (e.g., proxies, sidecars, or middleware) on both client and server sides.
These components are responsible for exchanging and appraising attestation evidence and enforcing
trust or authorization decisions before application data is processed. This is analogous to common
production deployments in which TLS termination and certificate handling are performed by a
fronting proxy, while the application itself remains unchanged and resides behind it.

# Need for Post-handshake Attestation
We argue that post-handshake attestation is unavoidable (e.g., re-attestation to
track changes after Connection Establishment Time for long-lived connections).
Use cases where pre-handshake attestation and intra-handshake attestation are
insufficient include AI agents/agentic AI {{I-D.jiang-seat-dynamic-attestation}}.

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

He further shares {{MCR-LAKE2}}:

{:quote}
>  My contention, which I think the group agreed with, is that one probably
wants to do continuous assurance, that is, to repeat the remote attestation.

{:quote}
>  Do you want to have two protocols and two code paths? (redundant code in a
constrained device?).  I suggested that *maybe* the remote attestation should
use it's own /.well-known Path, and that it would just occur after
onboarding, and regularly onwards.  Maybe it's weird to onboard a device only
to kick it out again immediately because it failed remote attestation, but
given continuous assurance, this could happen at any time.

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
{: #sec-sec-cons }

Most of the document is about security considerations. Also,
Security Considerations of {{-rfc9334}} and {{I-D.ietf-tls-rfc8446bis}} apply. In addition:

* Pre-handshake attestation is vulnerable to **replay** {{RA-TLS}} and **diversion**
{{ID-Crisis}} attacks. Moreover, pre-handshake attestation leads to a single point of
failure.

* Without significant changes to the TLS protocol: Intra-handshake attestation is
vulnerable to **diversion** attacks {{ID-Crisis}}. We reported these attacks to TLS WG in
February 2025 {{Usama-TLS-26Feb25}}. A formal proof is available
{{ID-Crisis-Repo}} for further research and
development. Since reporting to TLS WG, these attacks have been practically
exploited in [TEE.fail](https://tee.fail/), [Wiretap.fail](https://wiretap.fail/), and [BadRAM](https://badram.eu/).
More recently, we found that intra-handshake attestation also does not bind the Evidence
to the application traffic secrets, resulting in **relay** attacks {{RelayAttacks}}.

* No attacks on post-handshake attestation are currently known. Post-handshake attestation
avoids replay attacks by using fresh attestation nonce. Moreover, it avoids diversion and relay attacks
by binding the Evidence to the underlying TLS connection, such as using Exported Keying Material (EKM)
{{I-D.ietf-tls-rfc8446bis}}, as proposed in Section 9.2 of {{ID-Crisis}}.
{{-rfc9261}} and {{-rfc9266}} provide mechanisms for such bindings. Efforts for a formal proof
of security of post-handshake attestation are ongoing.

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

We gratefully thank the following:

* Peg Jones for review of early draft before submission
* Paul Wouters for review of section 4 of -00
* Ayoub Benaissa for review of -00 and sharing his practical experiences
* Markus Rudy for review of -00 and sharing his practical experiences

# Contributors
{:numbered="false"}

Pavel Nikonorov (GENXT / IIAP NAS RA) contributed text in {{sec-intra-app-changes}} and {{sec-post-app-changes}}.

# History
{:numbered="false"}

-01

* Added scope section to address comments of Paul Wouters
* Added comments of Ayoub Benaissa as quotes
* Added some subsections to incorporate practical experiences of Markus Rudy
* Extended security considerations
