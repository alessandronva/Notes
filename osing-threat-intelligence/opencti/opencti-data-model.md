# OpenCTI Data Model

OpenCTI uses a variety of knowledge schemas in structuring data, the main one being the Structured Threat Information Expression ([STIX2](https://oasis-open.github.io/cti-documentation/stix/intro)) standards. STIX is a serialised and standardised language format used in threat intelligence exchange. It allows for the data to be implemented as entities and relationships, effectively tracing the origin of the provided information.

This data model is supported by how the platform's architecture has been laid out. The image below gives an architectural structure for your know-how.

![OpenCTI Architecture](https://tryhackme-images.s3.amazonaws.com/user-uploads/5fc2847e1bbebc03aa89fbf2/room-content/3bbe38f3ae0edf761c9e0541a71d43ff.png)

Source: [OpenCTI Public Knowledge Base](https://luatix.notion.site/OpenCTI-Public-Knowledge-Base-d411e5e477734c59887dad3649f20518)

The highlight services include:

* **GraphQL API:** The API connects clients to the database and the messaging system.
* **Write workers:** Python processes utilised to write queries asynchronously from the RabbitMQ messaging system.
* Connectors: Another set of Python processes used to ingest, enrich or export data on the platform. These connectors provide the application with a robust network of integrated systems and frameworks to create threat intelligence relations and allow users to improve their defence tactics.

According to OpenCTI, connectors fall under the following classes:

| Class                              | Description                                                  | Examples                  |
| ---------------------------------- | ------------------------------------------------------------ | ------------------------- |
| **External Input Connector**       | Ingests information from external sources                    | CVE, MISP, TheHive, MITRE |
| **Stream Connector**               | Consumes platform data stream                                | History, Tanium           |
| **Internal Enrichment Connector**  | Takes in new OpenCTI entities from user requests             | Observables enrichment    |
| **Internal Import File Connector** | Extracts information from uploaded reports                   | PDFs, STIX2 Import        |
| **Internal Export File Connector** | Exports information from OpenCTI into different file formats | CSV, STIX2 export, PDF    |

Refer to the [connectors](https://github.com/OpenCTI-Platform/connectors) and [data model](https://luatix.notion.site/Data-model-4427344d93a74fe194d5a52ce4a41a8d) documentation for more details on configuring connectors and the data schema.
