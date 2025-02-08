# Volume-1: Business Description

## Introduction

The xShare Yellow Button Download (YBD) specification describes the
following key things:

1.  A description of actors and transactions involved in
    operationalizing a Download functionality as described in the xShare
    D3.2 document;

2.  A list of downloadable documents expressed in terms of the European
    EHR eXchange Format (EEHRxF);

3.  A family of conformance-test assertions (expressed using the Gherkin
    language) that may be employed to confirm: (a) that a downloadable
    artefact is well-formed and correct; and (b) that the digital health
    solutions playing actor roles are conformant in their processing of
    EEHRxF artefacts.

The YBD specification is designed to support the use case where a
Patient, who is authenticated to an online digital health data
repository, identifies a document containing their personal health data
and downloads this document to a data store under their personal control
(e.g. a smartphone or a personal computer).

## Overview 

### Background

To provide an **overall** context, this section describes the envisaged
xShare Yellow Button basic functionalities. These functionalities are
derived from the xShare description of action (DoA), and the workflows
were defined in a workshop with the xShare Adoption Sites (adopters and
implementers) and the project’s technical partners. These basic
functionalities have the following pre-conditions and assumptions:

- The patient has an account and health data in the health provider.

- The patient is authenticated in the health provider portal/app.

- The HIS of the health provider is able to export and import health
  information in the EEHRxF.

This technical specification is focused on the **YB** **Download** (YBD)
functionality, but for context, the other two xShare Yellow Button
workflows are described, below.

#### One-time Share

This functionality enables the patient to share their health data (in
the EEHRxF) with a click-of-a-button, from a health provider portal/app
to a trusted one (e.g., healthcare provider, relative), according to the
following workflow:

1.  Citizen accesses the health institution portal/app.

2.  Visualises his/her health information.

3.  Clicks on the xShare Yellow Button.

4.  Selects the One-time share feature/functionality.

5.  Visualises the list of available health data.

6.  Selects which health data to share.

7.  (optional) data anonymisation, translation, sharing-period,
    password...

8.  Insert link for sharing the health data.

9.  Health data is transferred in the EEHRxF to the required
    destination.

#### Linked Option

This functionality enables the patient to share and link their health
data (in the EEHRxF) with a click-of-a-button, from a health provider
portal/app to a trusted one (e.g., healthcare provider, relative,
clinical trials, research institutions) for a period of time, according
to the following workflow:

1.  Citizen accesses the health institution portal/app.

2.  Visualises his/her health information.

3.  Clicks on the xShare Yellow Button.

4.  Selects the Linked share feature/functionality.

5.  Visualises the list of available health data.

6.  Selects which type of health data to share and the sharing period.

7.  (optional) data anonymisation, translation, password, ...

8.  Insert link for sharing the health data.

9.  Health data is transferred in the EEHRxF to the required
    destination.

### xShare YB Download

This functionality enables the patient to download their health data (in
the EEHRxF and e.g., PDF) with a click-of-a-button, from a health
provider portal/app to their computer or smartphone, according to the
following workflow:

1.  Citizen accesses the health institution portal/app.

2.  Visualises his/her health information.

3.  Clicks on the xShare Yellow Button.

4.  Selects the Download functionality.

5.  Visualises the list of available health data.

6.  Selects which health data to download. (with the option to add notes
    for citizen context, anonymisation, password definition)

7.  Selects download destination.

8.  Health data is transferred to his/her device in the EEHRxF and in
    human-readable format (e.g., PDF).

## Use Cases

### UC-1: Patient Empowerment for Accessing a 2<sup>nd</sup> Opinion

**Patient empowered by his data by using it for a second opinion:**

- A patient, Tom, opens the hospital's official mobile app to access his
  medical records.

- Using a secure two-factor authentication process, Tom logs in to the
  app, confirming his identity.

- Once authenticated, Tom selects requests his patient summary.

- The system generates the summary in the EEHRxF format, a standardized,
  machine-interoperable file (CDA or FHIR).

- Tom downloads the summary to his mobile device for personal use.

- The app displays the patient summary in a user-friendly interface,
  enabling Tom to review his medical history, lab results, and
  prescriptions easily. He can do what he wishes with his data,
  including sharing it (which is the subject of a companion YB
  specification).

- This scenario demonstrates how modern EHR systems empower patients
  with access, understanding, and control over his medical records.

<figure>
<img src="image1.png" style="max-width: 75%; object-fit: contain" />
<figcaption><p>Figure 1 - UC-1 Patient Empowerment from Accessing his health
data</p></figcaption>
</figure>

### UC-2: Patient Aggregating His Data at a Single Place

**Patient aggregating his data at a single place**

- Similar to the storyline above, Tom is able to access his IPS,
  download it in an interoperable format (EEHRxF) and use it to his
  advantage.

- However, Tom’s IPS is only part of his available health data. Other
  health care providers have created other records in the past, showing
  the development of his health.

- By following the process, described in the first storyline, multiple
  times across his previous health care providers, Tom is able to
  collect multiple instances of his IPS creating a healthcare timeline.

- By making use of a PHR, he is able to upload all instances of IPS in a
  standardized format creating an easily accessible overview of his
  medical data.

### UC-3: Content-type Permutations

This use case description illustrates the permutations of CDA- and
FHIR-based data exchange scenarios that can be expected across Europe
during the period of EHDS adoption. Billions of Euros have been spent on
digital health infrastructure that is based on the HL7 CDA content
persisted and exchanged using Cross-enterprise Document Sharing (XDS)
registries, repositories and transactions. Over time, the document
exchange traffic will evolve to become, eventually, FHIR-based documents
persisted in FHIR Servers and exchanged via RESTful transactions.

<figure>
<img src="image2.png"
style="max-width: 75%; object-fit: contain" />
<figcaption><p>Figure 2 - Document Query Scenarios</p></figcaption>
</figure>

It is expected that a two-way CDA/FHIR mapping service will provide an
important capability during this transitional period. The following six
use case scenarios are anticipated (two each of types A, B, and C):

1.  Either a client requests a CDA or FHIR document from an XDS
    Repository or a FHIR document from a FHIR Server

2.  Either a client requests a FHIR document from an XDS Repository
    containing CDAs or a CDA from a FHIR Server, and the transformations
    are done Server-side

3.  Either a client requests a FHIR document from an XDS Repository
    containing CDAs or a CDA from a FHIR Server, and the transformations
    are done Client-side

### UC-4: Implementation-approach Permutations

This use case description illustrates the permutations of deployment
options that can be expected across different xShare adoption sites in
Europe. As introduced in the previous UC section, significant
expenditures have been made on legacy digital health infrastructure.
Flexible implementation approaches that support the roll-out of EEHRxF
in a managed way will allow us to progress from success to success.

<figure>
<img src="image3.png" style="max-width: 100%; object-fit: contain" />
<figcaption><p>Figure 3 - YB Implementation Options</p></figcaption>
</figure>

Four distinct options might be considered for implementing Yellow Button
(YB) functionality in support of health data access and combinations of
these might also be possible. The distinct deployment scenarios are
illustrated in the figure above:

1.  YB functionality may be **natively** built into the health data
    server, itself. A simple browser may be used by a client to invoke
    the YB services. In this option, **<u>no</u>** conformance-testable
    interoperable transaction processing occurs and the health data
    server is responsible for natively creating EEHRxF-conformant
    content, executing all security mandates, and creating all required
    audit logs. It represents a self-contained *server-based ecosystem*.

2.  In this option YB functionality may be natively operationalized by a
    *client-server* *ecosystem* that is entirely self-contained. As with
    option \#1, there is **<u>no</u> interoperable data exchange** to
    test; the client- and server-side components may be non-standard as
    long as the functional pattern, from the point of view of the
    end-user, supports the YB use cases.

3.  Server-side YB-capable digital health solutions may be implemented
    using a façade pattern. These solutions would augment a
    standards-based server by exposing a set of YB features that can be
    invoked by a client using a simple browser (and/or an app). In this
    scenario, the conformance-testable transactions (shown in red) would
    be executed between the façade and the health data server. It would
    also be the responsibility of the façade to output EEHRxF conformant
    content.

4.  Digital health apps might operationalize YB features client-side.
    For content that is stored in standards-based health data servers,
    these apps may support functionality that brings to life one or more
    YB workflows. In this scenario, the conformance-testable
    transactions (shown in red) will be executed between the app and the
    health data server. Conformance to the EEHRxF format can be
    established server-side or client-side (including situations where
    the app may execute a format transformation).

Each of these options have different pros and cons and afford
implementers useful approaches that mitigate risks related to cost,
time-to-benefit, manageability and governance. Some of the approaches
create opportunities for “public goods” to have an accelerating impact.
Especially regarding option \#3, the availability of EU-provided
open-source façade options might support the rapid rollout of
EEHRxF-conformant FHIR document exchange services on top of (for
example) National Contact Points that already support the exchange of
cross-border content using CDA. In the alternative, option \#1 or \#2
may be favoured by adoption sites that have implemented **home-grown
solutions** and have the available software-development resources to
customize these solutions to execute the YB workflows. As a practical
matter, for option \#2, a non-standard client-side solution would need
to be customized specifically to work with a different (non-standard)
server outside of the self-contained ecosystem.

## Security considerations

The operations of YBD actors are subject to EHDS Article 50 (link to
full text, below). This article stipulates:

1.  The health data access bodies shall provide access to electronic
    health data only through a secure processing environment, with
    technical and organisational measures and security and
    interoperability requirements. In particular, they shall take the
    following security measures:

    1)  restrict access to the secure processing environment to
        authorised persons listed in the respective data permit;

    2)  minimise the risk of the unauthorised reading, copying,
        modification or removal of electronic health data hosted in the
        secure processing environment through state-of-the-art
        technological means;

    3)  limit the input of electronic health data and the inspection,
        modification or deletion of electronic health data hosted in the
        secure processing environment to a limited number of authorised
        identifiable individuals;

    4)  ensure that data users have access only to the electronic health
        data covered by their data permit, by means of individual and
        unique user identities and confidential access modes only;

    5)  keep identifiable logs of access to the secure processing
        environment for the period of time necessary to verify and audit
        all processing operations in that environment;

    6)  ensure compliance and monitor the security measures referred to
        in this Article to mitigate potential security threats.

2.  The health data access bodies shall ensure that electronic health
    data can be uploaded by data holders and can be accessed by the data
    user in a secure processing environment. The data users shall only
    be able to download non-personal electronic health data from the
    secure processing environment.

3.  The health data access bodies shall ensure regular audits of the
    secure processing environments.

4.  The Commission shall, by means of implementing acts, provide for the
    technical, information security and interoperability requirements
    for the secure processing environments. Those implementing acts
    shall be adopted in accordance with the advisory procedure referred
    to in Article 68(2).

<https://www.european-health-data-space.com/European_Health_Data_Space_Article_50_(Proposal_3.5.2022).html>
