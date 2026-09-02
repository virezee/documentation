# PRD Standard

## About This Standard

There is no official standard for a product requirements document. No standards body has ever published a specification under that name. The term comes from industry practice, not from ISO, IEEE, or IETF.

What is standardised is requirements engineering. ISO/IEC/IEEE 29148:2018 covers it, and it superseded IEEE 830-1998, IEEE 1233-1998, and IEEE 1362-1998. A revision is in progress, with the project authorisation approved on 10 September 2025. That standard is precise and auditable, but it has no concept of product goals, priority, or release planning. Industry PRD templates cover those, but they provide no unique identifiers, no verification, and no traceability.

This document combines the two. The structure and the discipline come from 29148. The product sections come from PRD practice. Every section below is traceable to one or both. The full mapping and the source list are at the end of this document.

## 1. Title & Owner

Identifies the document. States the feature or product name, the document ID, the person accountable for it, its current status, the version number, and the date of the last update. Readers use this block to confirm they are looking at the current version and to know who to ask when something is unclear.

## 2. Overview

A single paragraph summarising the entire document. It states what is being built, who it is for, and what outcome is expected. This section is written last and read first. It does not carry justification or history, which belong in the two sections that follow.

## 3. Problem Statement

Describes the problem itself: what goes wrong, who it affects, how often it occurs, and what evidence supports the claim. It must describe the problem rather than the solution. If the wording already names a feature, it belongs in a later section.

## 4. Background

Explains how the situation came about. Covers what has been tried before, why the current approach is no longer sufficient, and any prior decisions that constrain this work. Where the Overview answers what this document is about, this section answers how the team arrived here.

## 5. Goals

States the outcomes the work is intended to produce, expressed as changes in condition rather than as a list of features. Three to five entries, ordered by importance. "Users can complete checkout without re-entering payment details" is a goal. "Build a saved payment screen" is not.

## 6. Non-goals

Lists what the work deliberately excludes, together with a short reason for each exclusion. These are permanent exclusions for this product, not deferrals. Recording them here prevents the same question being raised repeatedly in review.

## 7. Success Metrics

Defines the measurements that will show whether the goals were met. Each entry gives the metric, the current baseline, the target, when it will be measured, and where the data comes from. Include guardrail metrics that must not degrade even if the primary targets are met. A metric without a known baseline is not yet a metric.

## 8. Users

Describes the people who will use the product, stated as fact rather than as personas. For each group, record the role, the task being performed, the conditions under which the product is used, and the level of technical skill. These four attributes are what shape the requirements.

## 9. Scenarios

Describes how users interact with the system, one entry per flow. Every entry is written as a condensed use case with five fixed parts: the actor, the trigger, the main flow as numbered steps, the failure paths, and the resulting end state.

This section covers the ground that other formats split between user stories and use cases, and it uses the use case form for all of it. A user story states intent in one sentence and has nowhere to record failure paths, which are the most frequent source of defects and rework. User stories are still written, but they belong in the backlog as tickets rather than in this document. Anything recorded here carries all five parts.

## 10. Requirements

Lists what the system must do and how well it must do it. Requirements are split into two subsections because they are grouped differently: functional requirements are grouped by feature, while non-functional requirements are grouped by quality attribute and apply across the system.

Every requirement carries a unique identifier that is never reused, a priority level, a statement written in the form "[condition] [subject] MUST [action] [object] [measurable constraint]", and the method by which it will be verified. A requirement with no verification method is not finished.

Priority levels: P0 blocks release, P1 ships in a later release, P2 is optional.

### 10.1 Functional

Observable system behaviour. What the system does in response to input, stated in terms of what a user or another system can see, not in terms of how it is built.

### 10.2 Non-functional

Quality attributes, categorised as performance, security, reliability, usability, maintainability, and compatibility. Only the categories that apply are written. Constraints must be numeric. "Fast" and "reliable" are not requirements.

## 11. UI/UX Design

Links to the agreed design assets, not the assets themselves. Each entry names the screen, gives the link, and states whether the design is final or still in draft. The status column matters, because without it people build against mockups that have not been approved. Remove this section for products with no user interface.

## 12. Out of Scope

Lists work that is excluded from this release but expected in a later one. This differs from non-goals, which are excluded permanently. The purpose is to close the question of why a particular capability is missing without having to answer it repeatedly during review.

## 13. Assumptions, Dependencies & Risks

Three related tables in one section, kept together because they form a chain. Assumptions are things taken to be true without proof. If an assumption turns out to be wrong, the contents of this document change. Dependencies are concrete items outside the team's control that must be completed first, each with a named owner and a date. Risks are things that may go wrong, recorded with their impact and the planned response.

Mitigation is a column within the risk table rather than a section of its own. It may be preventive, reducing the chance of the risk occurring, or contingent, describing what will be done if it occurs anyway.

## 14. Milestones

Marks the points at which defined work is complete, giving the milestone name, its contents, and the target date. Milestones record what has been finished, not how long each task takes.

Detailed schedules are not recorded in this document. A schedule changes weekly and would leave this document permanently out of date. Scheduling belongs to the delivery team and lives in the issue tracker. Milestones are the point where the two meet: the product owner sets the targets, and the delivery team plans the route.

## 15. Release Criteria

The conditions that must be satisfied before the work may be released. Written as a checklist with yes or no answers rather than as a judgement. Typical entries cover completion and verification of all P0 requirements, the absence of open severity 1 defects, performance results meeting the stated non-functional requirements, and a tested rollback procedure.

## 16. Rollout

Describes how the work reaches users once the release criteria have been met. Records the release method, whether staged, behind a feature flag, or released in full. It also records the order in which groups of users receive it, and the rollback plan, including what triggers it, how it is performed, and how long it takes.

## 17. Open Questions

Records questions that remain unanswered and could still change the contents of this document. Each entry names the question, the person or team who must answer it, the date by which an answer is needed, and its current status.

Once a question is answered, the answer is moved into the section it affects and the entry is closed. Questions left to accumulate here turn the section into a graveyard. If open questions affecting P0 requirements remain unresolved as release approaches, the document is not ready.

## 18. Appendix

Supporting material, placed last because it is reference rather than narrative. Empty subsections are removed.

### 18.1 References

Research, data, and documents this work relies on, including related product requirement documents.

### 18.2 Glossary

Domain terms and abbreviations, recorded only where a term could genuinely be misread.

### 18.3 Change Log

Revision history of this document: version, date, what changed, and who made the change.