# Volume-1: Actors, Transactions, and Content Modules

This section describes the normative actors who will participate in
interoperable content exchange and the transactions that will
operationalize this exchange. No **new** actors are defined by this IHE
Profile. Rather, actor groups are defined that support the xShare Yellow
Button Download workflows.

## Actors and Transactions

Following the IHE Methodology, the functionality of the xShare Yellow
Button Download (YBD) is described using a set of actor-transaction
pairs. For clarity, a *single* digital health solution may play
*multiple* actor roles.

The actors that participate in operationalizing the YBD use cases are
pictorially illustrated by Figure 4.

<figure>
<img src="image4.png"
style="max-width: 100%; object-fit: contain" />
<figcaption><p>Figure 4 - Pictorial illustration of YBD actors</p></figcaption>
</figure>

The relevant YBD actors and their transactions are listed in Table 1.

**Table-1: YBD Actors and Transactions
+-----------------------+-------------------------------------+--------+
| **Actor**             | **Transaction**                     | **O    |
|                       |                                     | ptiona |
|                       |                                     | lity** |
+=======================+=====================================+========+
| Authorization Client  | ITI-71: Get Authorization Token     | R      |
|                       | (Initiator)                         |        |
+-----------------------+-------------------------------------+--------+
|                       | ITI-72: Incorporate Authorization   | R      |
|                       | Token (Initiator)                   |        |
+-----------------------+-------------------------------------+--------+
| Authorization Server  | ITI-71: Get Authorization Token     | R      |
|                       | (Responder)                         |        |
+-----------------------+-------------------------------------+--------+
| Resource Server       | ITI-72: Incorporate Authorization   | R      |
|                       | Token (Responder)                   |        |
+-----------------------+-------------------------------------+--------+
| Patient Demographics  | ITI-21: Patient Demographics Query  | R      |
| Consumer              | (Initiator)                         | Note-1 |
+-----------------------+-------------------------------------+--------+
|                       | ITI-78: Mobile Patient Demographics | R      |
|                       | Query (Initiator)                   | Note-1 |
+-----------------------+-------------------------------------+--------+
| Patient Demographics  | ITI-21: Patient Demographics Query  | R      |
| Supplier              | (Responder)                         | Note-1 |
+-----------------------+-------------------------------------+--------+
|                       | ITI-78: Mobile Patient Demographics | R      |
|                       | Query (Responder)                   | Note-1 |
+-----------------------+-------------------------------------+--------+
| Document Consumer     | ITI-66: Find Document Lists         | R      |
|                       | (Initiator)                         |        |
+-----------------------+-------------------------------------+--------+
|                       | ITI-67: Find Document Reference     | R      |
|                       | (Initiator)                         |        |
+-----------------------+-------------------------------------+--------+
|                       | ITI-68: Retrieve Document           | R      |
|                       | (Initiator)                         |        |
+-----------------------+-------------------------------------+--------+
| Document Responder    | ITI-66: Find Document Lists         | R      |
|                       | (Responder)                         |        |
+-----------------------+-------------------------------------+--------+
|                       | ITI-67: Find Document Reference     | R      |
|                       | (Responder)                         |        |
+-----------------------+-------------------------------------+--------+
|                       | ITI-68: Retrieve Document           | R      |
|                       | (Responder)                         |        |
+-----------------------+-------------------------------------+--------+
| Data Consumer         | CA:FeX-2: Search Data (Initiator)   | R      |
+-----------------------+-------------------------------------+--------+
|                       | CA:FeX-3: Retrieve Data (Initiator) | R      |
+-----------------------+-------------------------------------+--------+
| Data Responder        | CA:FeX-2: Search Data (Responder)   | R      |
+-----------------------+-------------------------------------+--------+
|                       | CA:FeX-3: Retrieve Data (Responder) | R      |
+-----------------------+-------------------------------------+--------+
| Audit Creator         | ITI-20: Record Audit Event          | R      |
|                       | (Initiator & Responder)             |        |
+-----------------------+-------------------------------------+--------+
| Content Consumer /    | PCC-1: Share content (Initiator /   | R      |
|                       | Responder)                          | Note-2 |
| Content Creator       |                                     |        |
+-----------------------+-------------------------------------+--------+
Note-1: In a FHIR infrastructure, both actors SHALL support ITI-78. In a
legacy (HL7v2) infrastructure, both actors SHALL support ITI-21. The
actors MAY support both transactions.

Note-2: PCC-1 is operationalized via the grouping to data exchange
actors. EEHRxF-conformant content options are defined below.

## Document Processing Options

The following options relate to document processing by xShare YBD
actors.

### Document View 

A Content Creator actor SHOULD provide access to a style sheet that
ensures consistent rendering of the document content as was intended by
the Content Creator. The Content Consumer actor SHALL be able to present
a view of the document using this style sheet if present.

### Document Save 

A Content Consumer actor that supports this option SHALL be able to
persist an EEHRxF-conformant document to a local datastore.

### Document Ingest 

A Content Consumer actor that supports this option SHALL support the
ability to ingest an EEHRxF-conformant document into a local datastore
that enables the discrete elements of the document to be individually
accessed.

### CDA-to-FHIR Transformation

A Content Consumer actor that supports this option SHALL map CDA
document content, during an automated or semi-automated process, to
create a lossless FHIR document that is functionally equivalent to the
source CDA document.

A Content Creator actor that supports this option SHALL map CDA document
content, during the document creation process, to generate a lossless
FHIR document that is functionally equivalent to the source CDA
document.

### FHIR-to-CDA Transformation

A Content Consumer actor that supports this option SHALL map FHIR
document content, during an automated or semi-automated process, to
create a lossless CDA document that is functionally equivalent to the
source FHIR document.

A Content Creator actor that supports this option SHALL map FHIR
document content, during the document creation process, to generate a
lossless CDA document that is functionally equivalent to the source FHIR
document.

## Document Content Options

For the YBD specification, the following documents may be downloaded:

- Patient Summary

- Electronic Prescription

- Electronic Dispensation

- Medical Image & Image Report

- Laboratory Results

- Discharge Report

- *Telemonitoring*[^1]

- *~~Care Plan~~*.[^2]

The normative content specifications are defined in Volume-3 of the YBD
Profile. An implementing jurisdiction (via its relevant IHE Deployment
Committee) may *contextualize* these specifications and, where
applicable, such contextualizations are documented in **Volume-4** of
this Profile.

## Actor groupings

To operationalize the YBD use cases, existing IHE actors may be grouped
to operationalize transactions against XDS-based health data
repositories or against FHIR servers. Referring to Figure 4, the actors
and their “typical” client-server groupings may be described as follows:

- Authentication and authorization is established by the Authorization
  Client, which obtains a token from an Authorization Server. The
  Authorization Server may be an actor external to the health data
  infrastructure.

- For all-in-one deployment options (reference options 1 & 2 in
  Figure 3) the Content Consumer and Content Creator actors are grouped
  only with the necessary authorization and audit actors as indicated in
  the black dashed rectangles in Figure 4.

- For YB workflows operationalized using an XDS-based data repository, a
  Content Consumer is grouped with the Authorization Client, a Patient
  Demographics Consumer, an Audit Creator and Aduit Record Repository,
  and a Document Consumer actor (shown grouped in the YB Initiator
  dashed blue rectangle). To service the document request, a Content
  Creator is grouped with a Resource Server, a Patient Demographic
  Supplier, an Audit Creator and Audit Record Repository, and a Document
  Responder actor. This is indicated by the YB Responder dashed blue
  rectangle on Figure 4.

- For YB workflows operationalized from a pure-FHIR-based server, a
  Content Consumer is grouped with a Patient Demographics Consumer, an
  Authorization Client, an Audit Creator and Audit Record Repository,
  and a Data Consumer actor (shown grouped in the YB Initiator dashed
  dark red rectangle). To service the document request, a Content
  Creator is grouped with a Patient Demographics Supplier, a Resource
  Server, an Audit Creator and Audit Record Repository, and a Data
  Responder actor. This is indicated by the YB Responder dashed dark red
  rectangle on Figure 4.

<figure>
<img src="image5.svg" style="max-width: 100%; object-fit: contain" />
<figcaption><p>Figure 5 - Grouped actors supporting YB Download</p></figcaption>
</figure>

Different actor groupings support different “product” configurations for
operationalizing YBD functionality. A YBD reference architecture, for
example, could be operationalized by a client-server configuration of
grouped actors supporting transactions against a pure-FHIR document
repository or an XDS repository. Such a configuration is illustrated in
Figure 5. A flexible range of deployment options is supported by such a
configuration. Where an implementation plans to leverage existing
digital health infrastructure to play the role of one or more actors,
this can be readily done as long as the replacement actor supports the
relevant transactions.

This YB Download configuration assumes a **patient** is accessing their
**own** health data. Therefore, simple access control SHALL be
operationalized via the interaction between a Patient Demographics
Consumer and Patient Demographics Supplier. Leveraging the identify of
the authenticated party (via ITI-71), and the unique patient
identifier(s) returned in the demographic record, health data access
will be scoped exclusively to content where the authenticated party
***is*** the document’s care subject.

<figure>
<img src="image6.svg"
style="max-width: 75%; object-fit: contain" />
<figcaption><p>Figure 6 - Un-grouped (or super-grouped) actor
configurations</p></figcaption>
</figure>

Un-grouped or super-grouped configurations are also possible. A digital
health product may support specialty functions that augment, but rely
upon, other actors. Similarly, a super-group of actors may
operationalize all-in-one functionality that obviates the need for
inter-actor transaction processing and so does not require
interoperability testing of these “inside-the-software-stack” exchanges.
Such ideas are illustrated by Figure 6. In this figure, a super-group of
actors support a Content Consumer in obtaining well-formed documents
from a Content Creator via IHE’s intentionally under-specified PCC-1
Share Content transaction. In this configuration, the
conformance-testability is limited to confirming the document content is
well-formed and normative functional requirements such as security and
auditing have been met by the complementary actors’ services.
Actor-transaction processing *inside* the super-group is not testable.

### Groupings related to Security and Auditing

To support the trusted execution of transactions within a regulated
healthcare domain, all actors in this specification are implicitly
grouped with IHE’s Secure Application[^3] and Time Client[^4] actors and
the Authorization Client[^5] actor. For audit record content, the IHE
Basic Audit Log Patterns SHALL be used:
<https://profiles.ihe.net/ITI/BALP/index.html>.

### Downloading content from an XDS-based repository

An Authorization Server actor is required in the infrastructure. This
MAY be an external actor.

**xShare Yellow Button Client**

To support YBD client transactions against an XDS-based repository, the
following actors are grouped:

- Content Consumer

- Authorization Client

- Audit Creator

- Audit Record Repository

- Patient Demographics Consumer

- Document Consumer

**xShare Yellow Button Server**

To support YBD responses from an XDS-based repository (as a server), the
following actors are grouped:

- Content Creator

- Resource Server

- Audit Creator

- Audit Record Repository

- Patient Demographics Supplier

- Document Responder

### Downloading content from a FHIR Server

An Authorization Server actor is required in the infrastructure. This
MAY be an external actor.

**xShare Yellow Button Client**

To support YBD client transactions being executed against a FHIR server,
the following actors are grouped:

- Content Consumer

- Authorization Client

- Audit Creator

- Audit Record Repository

- Patient Demographics Consumer

- Data Consumer

**xShare Yellow Button Server**

To support YBD responses from a FHIR server, the following actors are
grouped:

- Content Creator

- Resource Server

- Audit Creator

- Audit Record Repository

- Patient Demographics Supplier

- Data Responder

**Footnotes**

[^1]: Unlike the other content, Telemonitoring is really a use-case and
    is not specifically tied to a document type.

[^2]: The IHE Computable Care Guideline
    ([**CCG**](https://build.fhir.org/ig/IHE/QRPH.CCG/CCG_v1_over.html))
    Profile supports care planning workflows; it defines a different set
    of actors and transactions.

[^3]: <https://profiles.ihe.net/ITI/TF/Volume1/ch-9.html>

[^4]: <https://profiles.ihe.net/ITI/TF/Volume1/ch-7.html>

[^5]: <https://profiles.ihe.net/ITI/IUA/#341-iua-actors-transactions-and-content-modules>
