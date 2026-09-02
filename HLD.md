# HLD Standard

## About This Standard

No standards body has published a specification for a document called a high level design. The terms HLD and LLD are industry usage. What has been standardised is the architecture description itself, by ISO/IEC/IEEE 42010:2022. That standard defines the rules an architecture description must follow, covering stakeholders, viewpoints, views, and the correspondence between them, but it deliberately prescribes no document outline. IEEE 1016-2009 has been Inactive-Reserved since 5 March 2020 and has no successor.

The outline therefore comes from arc42 version 9, whose twelve sections supply the concrete viewpoints that 42010 leaves open. Diagrams follow the C4 model, with UML sequence diagrams for runtime scenarios. Architectural decisions use the Nygard record format. Quality requirements use the six part scenario form from the Software Engineering Institute, with attribute names taken from ISO/IEC 25010.

This document is a derivative of the product requirements document rather than a parallel one. Sections 1, 2, and 12 refer to it instead of restating it. Section 5 carries the traceability that holds the chain together, since every building block records the requirement identifiers it satisfies.

This document stays at architectural level. It records structure, contracts, and decisions that carried a trade-off. It does not record implementation detail. The test is whether a detail could change without changing the structure of the system or a contract between components. If it could, it belongs in the low level design. Class and method names, database columns and indexes, algorithms, timeout values, and configuration are all out of bounds here. Sequence diagrams name components as participants, never classes.

## 1. Introduction & Goals

States what the system is required to do, in a form short enough to read in one sitting. Lists the three to five quality goals that shape the architecture more than anything else, such as response time, availability, or auditability. Names the stakeholders and records what each of them cares about, because a view that answers nobody's concern should not be drawn.

This section does not restate the requirements. It refers to the product requirements document by section and by requirement ID. If a goal here has no corresponding entry there, one of the two documents is wrong.

## 2. Constraints

Records what the architect is not free to decide. Technical constraints cover mandated or forbidden technologies, platforms, and versions. Organisational constraints cover team structure, budget, deadlines, and the skills available. Conventions cover coding standards, naming rules, and documentation formats already in force.

Constraints are inherited from the product requirements document rather than invented here. Anything listed must be traceable to a decision made outside this document.

## 3. Context & Scope

Fixes the boundary of the system. Everything inside is designed here. Everything outside is given.

The business context names the external parties, human and machine, and the information exchanged with each of them. The technical context names the interfaces through which that information travels, including protocols, formats, and channels.

Diagram: C4 Level 1, Context. The system appears as a single box with no internals.

## 4. Solution Strategy

The architecture in one page. Records the technology choices, the way the system is decomposed, the architectural patterns applied, and how each quality goal from section 1 is met.

This section is a summary written for someone who will not read the rest. Every claim made here is expanded in sections 5 through 9. If a decision is significant enough to be argued about, it is recorded as an entry in section 9 and referenced from here.

## 5. Building Block View

The static decomposition of the system, described in levels. The first level breaks the system into its major parts. Each part may then be opened up in a level of its own, but only where the complexity justifies it.

Every building block records its responsibility, its interfaces, and the requirement IDs it satisfies. That last column is what makes this document a derivative rather than a parallel one. Read downward it explains why a component exists. Read upward it shows whether any requirement has been left without a home.

Diagrams: C4 Level 2, Container, for the first level. C4 Level 3, Component, for building blocks that are opened further. A container here means anything separately deployable and runnable, such as an application, a service, a database, or a queue. It does not mean a Docker container.

## 6. Runtime View

How the building blocks work together while running, described one scenario at a time. Covers the scenarios that matter: the main paths, system startup and shutdown, and the failure paths.

The scenarios come from the product requirements document, but they are told from the system's side rather than the user's. Where the requirements document says what the user does, this section says which component receives it, what it calls next, and what happens when a call fails.

Diagrams: C4 Dynamic or UML sequence diagram for each scenario. UML state machine for any object with a lifecycle worth drawing.

## 7. Deployment View

Where the system runs. Records the environments, the infrastructure they are built from, and which building block runs on which node. A single container from section 5 may appear several times here if it runs in more than one place.

Also records what differs between environments, since configuration drift between staging and production is a common source of failure.

Diagram: C4 Deployment.

## 8. Crosscutting Concepts

Concepts that apply across the whole system and belong to no single component. Typical entries are authentication and authorisation, error handling, logging and monitoring, transaction and consistency rules, persistence, caching, configuration, and internationalisation.

Each concept is written once and referenced from everywhere it applies. A rule repeated inside several building blocks will eventually be repeated inconsistently.

The data model belongs here when data ownership is an architectural question. What is recorded is the conceptual model: the entities, their relationships, and which service owns which entity. Columns, types, indexes, and physical schema belong to the low level design. If the system has one database and no ownership question to settle, this concept is omitted entirely.

## 9. Architectural Decisions

The decisions that were genuinely open, recorded one entry per decision in the format popularised by Michael Nygard. Each entry carries a title, a status, the context that forced a choice, the decision itself, and its consequences, including the ones the team is not happy about.

Record the alternatives that were rejected and why they were rejected. A year later the value of this section lies almost entirely in that part, because it is what stops a settled question from being reopened.

Only decisions with real consequences are recorded. A choice with an obvious answer and no trade-off is not an architectural decision.

## 10. Quality Requirements

Turns the non-functional requirements into something an architecture can be tested against. A requirement stating that a response must arrive within 500 ms says nothing about which component carries that budget or under what load the figure holds.

Each entry follows the quality attribute scenario form used in the SEI evaluation methods, with six parts: the source of the stimulus, the stimulus itself, the artefact it reaches, the environment it occurs in, the expected response, and the measure by which that response is judged.

A quality tree may be used to organise the entries by attribute. Attribute names follow the same taxonomy as the product requirements document, so that the two remain comparable.

## 11. Risks & Technical Debt

Architectural risks and the technical debt taken on knowingly. These are not the delivery risks recorded in the product requirements document. A dependency arriving late is a delivery risk. A component that will not scale past a known load, or a library with no maintainer, is an architectural risk.

Each entry records the risk, what it would cost if it materialised, and what is planned about it. Debt entries also record why it was accepted and what would trigger paying it down.

## 12. Glossary

Domain and technical terms with a single agreed meaning, so that the same word is not used for two things across teams. Refers to the product requirements glossary rather than duplicating it, and adds only the terms that are specific to the architecture.