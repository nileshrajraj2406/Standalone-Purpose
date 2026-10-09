# AiXPurpose – Donor Management – Members

> **Document type:** Business Requirements Document – Workflow

## Document Control

| Field                   | Details                                                                                     |
| ----------------------- | ------------------------------------------------------------------------------------------- |
| Document Name           | AiXPurpose – Members – Workflow                                                             |
| Product                 | AiXPurpose                                                                                  |
| Module                  | Donor Management                                                                            |
| Capability              | Members                                                                                     |
| Document Type           | Business Requirements Document – Workflow                                                   |
| Version                 | 1.0                                                                                         |
| Status                  | Draft for Business Review                                                                   |
| Related Goals           | AiXPurpose – Members – Goals v1.0                                                           |
| Related Feature Catalog | AiXPurpose – Members – Feature Catalog                                                      |
| Scope                   | Existing Members functionality and standalone enhancements                                  |
| Source                  | Existing application walkthrough, screenshots, requirements and approved business decisions |

## Overview

This document describes the end-to-end workflows for the Members capability, distinguishing current-state (As-Is) behaviour from target-state (To-Be) requirements.

## Contents

- [1. Purpose and Scope](#1-purpose-and-scope)
- [2. End-to-End Members Workflow](#2-end-to-end-members-workflow)
- [3. Systems and Responsibilities](#3-systems-and-responsibilities)
- [4. Actor Entry Rules](#4-actor-entry-rules)
- [5. Workflow Inventory](#5-workflow-inventory)
- [6. Detailed Members Workflows](#6-detailed-members-workflows)
- [7. Shared Validation Rules](#7-shared-validation-rules)
- [8. Screenshot Reference Mapping](#8-screenshot-reference-mapping)
- [9. Goals-to-Workflow Traceability](#9-goals-to-workflow-traceability)
- [10. Feature Catalog Handoff](#10-feature-catalog-handoff)
- [11. Decisions Requiring Detail](#11-decisions-requiring-detail)
- [12. Workflow Validation Summary](#12-workflow-validation-summary)

## 1. Purpose and Scope

This document defines the operational workflows for the Members capability, translating the approved Members business goals into functional processes.

It covers the existing application (As-Is) and the enhanced standalone application (To-Be), including member creation, multi-source data ingestion, duplicate prevention, member status management, import, KPIs, filtering, export and donation integration.

The document uses the approved `MEM-GO-###` and `MEM-BR-###` identifiers from Members Goals.

As-Is indicates existing functionality. To-Be identifies enhancements required for standalone AiXPurpose. Proposed implementation decisions are identified separately where relevant.

## 2. End-to-End Members Workflow

### 2.1 Existing Application – As-Is

![Existing Application – As-Is](Members/workflow_screenshot/2.1%20Existing%20Application%20%E2%80%93%20As-Is.png)

### 2.2 Standalone Application – To-Be

![Standalone Application – To-Be](Members/workflow_screenshot/2.2%20Standalone%20Application%20%E2%80%93%20To-Be.png)

## 3. Systems and Responsibilities

| System / Capability          | Responsibility                                                        |
| ---------------------------- | --------------------------------------------------------------------- |
| Tenant Management            | Isolated organisation workspace and tenant context                    |
| Existing Identity and Access | Authentication, existing roles and permissions                        |
| Members                      | Member records, forms, profiles, statuses and listing                 |
| Integrations                 | Receive member information from supported applications                |
| Import Processing            | Template upload, validation, duplicate checks and processing outcomes |
| Campaigns                    | Authoritative campaign selection data                                 |
| Donations                    | Donation creation, transaction records and giving information         |
| KPI / Reporting              | Existing and additional KPI calculations                              |
| Export                       | Authorised CSV extraction                                             |
| Audit                        | Record actions, imports, merge decisions and material changes         |

These responsibilities describe logical capabilities, not mandatory separate technical services.

## 4. Actor Entry Rules

| Actor                  | Permitted Business Activities                                                              |
| ---------------------- | ------------------------------------------------------------------------------------------ |
| Tenant Administrator   | Manage configuration and authorised Member operations                                      |
| Members Administrator  | Add, edit, import, review duplicates and correct records according to existing permissions |
| Authorised User        | Search, view, filter, access KPIs and export where permitted                               |
| External Integration   | Submit member data to its authorised tenant                                                |
| Donation User          | Initiate donation entry for an existing member                                             |
| Platform Administrator | Manage platform functions subject to authorised access boundaries                          |

### 4.1 Member Access Flow

![Member Access Flow](Members/workflow_screenshot/4.1%20Member%20Access%20Flow.png)

Existing role-based permissions are retained. New actions must be mapped to the established permission framework.

## 5. Workflow Inventory

| ID        | Workflow                                | Classification              |
| --------- | --------------------------------------- | --------------------------- |
| MEM-WF-01 | Open Members Overview                   | As-Is + Enhance             |
| MEM-WF-02 | Create Member Manually                  | As-Is + Enhance             |
| MEM-WF-03 | Save and Resume Member Draft            | As-Is UI + To-Be Definition |
| MEM-WF-04 | Receive Integrated Member Data          | As-Is + Enhance             |
| MEM-WF-05 | Bulk Import Members                     | To-Be                       |
| MEM-WF-06 | Validate and Resolve Duplicates         | To-Be                       |
| MEM-WF-07 | Search, Filter and Paginate             | As-Is + Enhance             |
| MEM-WF-08 | View Member Profile                     | As-Is + Enhance             |
| MEM-WF-09 | Edit Member                             | As-Is + Enhance             |
| MEM-WF-10 | Manage Member Status                    | As-Is + To-Be Separation    |
| MEM-WF-11 | Display and Configure KPIs              | As-Is + Enhance             |
| MEM-WF-12 | KPI Drill-Down                          | To-Be                       |
| MEM-WF-13 | Advanced Filters                        | To-Be                       |
| MEM-WF-14 | Export Member Records                   | As-Is + Enhance             |
| MEM-WF-15 | Refresh Members and KPIs                | To-Be                       |
| MEM-WF-16 | Initiate Donation from Member           | As-Is + Enhance             |
| MEM-WF-17 | Tenant Configuration and Feature Access | To-Be                       |
| MEM-WF-18 | Audit and Error Handling                | To-Be Governance            |

## 6. Detailed Members Workflows

### MEM-WF-01 – Open Members Overview

Goal: MEM-GO-001, MEM-GO-005, MEM-GO-013

Actor: Authorised user.

As-Is:

1. Navigate to Donor Management → Members.
2. Display the existing Members overview.
3. Load active members by default.
4. Display four existing KPI cards and member list.

To-Be: Retain the existing experience with tenant-isolated data, existing permission enforcement, configurable KPIs, enhanced filters and additional import/refresh actions.

![Open Members Overview](Members/workflow_screenshot/6.%20Detailed%20Members%20Workflows.png)

Exception: Unauthorised access is denied. An empty register displays an empty state rather than fabricated records.

### MEM-WF-02 – Create Member Manually

Goal: MEM-GO-006, MEM-GO-025

Actor: Authorised Members user.

As-Is: The Add Member interface has five sections and accepts manually entered member information.

To-Be: Preserve the five sections, apply applicable validations, check duplicates and update relevant KPIs after successful creation.

| Section                   | Existing Fields                                                                                    |
| ------------------------- | -------------------------------------------------------------------------------------------------- |
| Contact Information       | Donor Type, Title, First Name, Last Name, Email, Mobile/Home/Business Phone                        |
| Address and Communication | Address, ZIP Code, State, City, Anonymous Donor, Do Not Solicit                                    |
| Campaign and Giving       | Current Campaign, Giving Status, Current Solicitor, Pledged Amount                                 |
| Recognition and Social    | Publication/recognition details, spouse details, alternate phone numbers and types                 |
| Advanced / System         | iWave, Capacity, Propensity, Affinity Scores, Profile URL, guest details and other existing fields |

![Create Member Manually](Members/workflow_screenshot/MEM-WF-02%20%E2%80%93%20Create%20Member%20Manually.png)

Business rule: The record must be associated with the current tenant. Exact mandatory fields, particularly for organisations and foundations, require field-level approval.

### MEM-WF-03 – Save and Resume Member Draft

Goal: MEM-GO-006

As-Is: The Add New Member screenshot shows a Save Draft action. Its backend persistence behaviour is not confirmed.

To-Be: Define a controlled draft lifecycle where incomplete data may be saved without being treated as a completed member.

![Save and Resume Member Draft](Members/workflow_screenshot/MEM-WF-03%20%E2%80%93%20Save%20and%20Resume%20Member%20Draft.png)

Proposed rule: Drafts must remain separate from committed member counts until successfully submitted. Draft visibility, expiry and deletion rules require approval.

### MEM-WF-04 – Receive Integrated Member Data

Goal: MEM-GO-004, MEM-GO-005, MEM-GO-012

As-Is: Existing external applications supply member data to AiXPurpose.

To-Be: Apply tenant validation, source mapping, duplicate detection and controlled updates before records enter the consolidated register.

![Receive Integrated Member Data](Members/workflow_screenshot/MEM-WF-04%20%E2%80%93%20Receive%20Integrated%20Member%20Data.png)

Exception: Failed integration processing must not overwrite previously committed member information.

### MEM-WF-05 – Bulk Import Members

Goal: MEM-GO-007, MEM-GO-008, MEM-GO-009

Actor: Authorised import user.

To-Be: Import Excel/CSV member records through predefined templates, validate data, identify duplicates, report results and automatically refresh affected KPIs.

![Bulk Import Members](Members/workflow_screenshot/MEM-WF-05%20%E2%80%93%20Bulk%20Import%20Members.png)

Import result categories:

| Result         | Meaning                                                                 |
| -------------- | ----------------------------------------------------------------------- |
| Created        | New member successfully committed                                       |
| Updated        | Existing member updated under approved rules                            |
| Rejected       | Invalid row not committed                                               |
| Pending Review | Potential duplicate or conflicting data awaiting administrator decision |
| Skipped        | Row intentionally not processed under an approved rule                  |

Partial-success handling, import limits and template versioning must be finalised in the Feature Catalog.

### MEM-WF-06 – Validate and Resolve Duplicates

Goal: MEM-GO-010, MEM-GO-011

Approved rule: Potential duplicates must be detected, and conflicting member records require administrator review before merging or updating.

![Validate and Resolve Duplicates](Members/workflow_screenshot/MEM-WF-06%20%E2%80%93%20Validate%20and%20Resolve%20Duplicates.png)

Exception: No automatic merge or conflicting overwrite is permitted without the required administrator approval. Matching criteria and non-conflicting update policy must be formally defined.

### MEM-WF-07 – Search, Filter and Paginate

Goal: MEM-GO-013

As-Is: Search by name, email or phone; filter by donor type or giving status; navigate paginated records.

To-Be: Preserve the existing controls, standardise filter combinations and support additional approved criteria.

![Search, Filter and Paginate](Members/workflow_screenshot/MEM-WF-07%20%E2%80%93%20Search%2C%20Filter%20and%20Paginate.png)

Existing list columns remain Name, Donor Type, Contact, Location, Member Status, Pledged 2024, Created and Actions. The standalone application should use an approved dynamic reporting period rather than permanently displaying 2024.

### MEM-WF-08 – View Member Profile

Goal: MEM-GO-005, MEM-GO-019

As-Is: Clicking a member row or View icon opens the same Member Detail page.

The current profile includes member classification, status, contact information, Total Donations, Pledged Amount 2024, iWave Score, Edit and Add Donation.

To-Be: Retain the profile and add approved source, quality and audit indicators.

![View Member Profile](Members/workflow_screenshot/MEM-WF-08%20%E2%80%93%20View%20Member%20Profile.png)

### MEM-WF-09 – Edit Member

Goal: MEM-GO-011, MEM-GO-019

As-Is: Edit opens the same five-section structure as Add Member, populated with existing values.

To-Be: Apply permissions, validations, change tracking and conflict review when required.

![Edit Member](Members/workflow_screenshot/MEM-WF-09%20%E2%80%93%20Edit%20Member.png)

Exception: Unapproved conflicting updates are not committed.

### MEM-WF-10 – Manage Member Status

Goal: MEM-GO-025

Confirmed To-Be: Maintain two separate statuses.

| Status Type           | Values                             | Purpose                                 |
| --------------------- | ---------------------------------- | --------------------------------------- |
| Administrative Status | Active, Inactive                   | Controls administrative record activity |
| Giving Status         | Prospect, Pledged, Donated, Lapsed | Describes giving-related classification |

![Manage Member Status](Members/workflow_screenshot/MEM-WF-10%20%E2%80%93%20Manage%20Member%20Status.png)

Business rules:

- Members default listing uses Administrative Status = Active.
- Giving Status is a separate search/filter attribute.
- An inactive member may retain historical giving information.
- A member with a qualifying donation is also a donor.
- A giving-status change does not automatically change administrative activity.
- Donation-triggered giving-status transitions require defined and approved rules.

### MEM-WF-11 – Display and Configure KPIs

Goal: MEM-GO-014, MEM-GO-015

As-Is: Existing KPI calculations are already implemented.

| Existing KPI     | To-Be Enhancement                     |
| ---------------- | ------------------------------------- |
| Total Members    | Clickable member-list drill-down      |
| Conversion Ready | Clickable qualified-member drill-down |
| Email Verified   | Filter verified-email members         |
| Phone Verified   | Filter verified-phone members         |

To-Be: Allow selection of additional KPIs using approved calculation definitions.

![Display and Configure KPIs](Members/workflow_screenshot/MEM-WF-11%20%E2%80%93%20Display%20and%20Configure%20KPIs.png)

Proposed additional KPIs: Active Members, New Members, Members by Type, Members by Location, Members by Source, Members with Pledges, Data Completeness, Conversion Rate and Pending Duplicate Reviews.

Additional KPI definitions must follow the established calculation framework and use authoritative member data.

### MEM-WF-12 – KPI Drill-Down

Goal: MEM-GO-014

To-Be: Selecting a KPI filters the member list to matching records.

![KPI Drill-Down](Members/workflow_screenshot/MEM-WF-12%20%E2%80%93%20KPI%20Drill-Down.png)

Example: Selecting Phone Verified displays members matching the existing phone-verification calculation.

The interaction between KPI selection, search and other filters must be consistent and visible to the user.

### MEM-WF-13 – Advanced Member Filtering

Goal: MEM-GO-016

As-Is: Donor Type and Member Status filters are available.

To-Be: Support additional filters relevant to tenant requirements.

| Filter                 | Classification      |
| ---------------------- | ------------------- |
| Donor Type             | As-Is               |
| Giving Status          | As-Is, standardised |
| Administrative Status  | To-Be separation    |
| Country / State / City | To-Be               |
| Created Date           | To-Be               |
| Campaign               | To-Be               |
| Data Source            | To-Be               |
| Contact Verification   | To-Be               |
| Pledge Range           | To-Be               |
| Data Completeness      | Proposed            |

![Advanced Member Filtering](Members/workflow_screenshot/MEM-WF-13%20%E2%80%93%20Advanced%20Member%20Filtering.png)

### MEM-WF-14 – Export Member Records

Goal: MEM-GO-017

As-Is: Export CSV is available.

To-Be: Export the authorised records matching the applied filters or approved selection.

![Export Member Records](Members/workflow_screenshot/MEM-WF-14%20%E2%80%93%20Export%20Member%20Records.png)

Business rule: Exported records must remain within the user's authorised tenant and data scope.

### MEM-WF-15 – Refresh Members and KPIs

Goal: MEM-GO-024

To-Be: Refresh the Members list and KPI summaries using the latest committed data.

![Refresh Members and KPIs](Members/workflow_screenshot/MEM-WF-15%20%E2%80%93%20Refresh%20Members%20and%20KPIs.png)

Confirmed rule: Successfully imported records automatically update affected KPI figures.

The Refresh button reloads the current information; it must not be required to trigger import-related KPI recalculation.

### MEM-WF-16 – Initiate Donation from Member

Goal: MEM-GO-021, MEM-GO-022

As-Is: The member row's dollar icon and profile Add Donation action open donation entry.

Confirmed business relationship: Every donor must be associated with an existing member, but not every member is a donor.

![Initiate Donation from Member](Members/workflow_screenshot/MEM-WF-16%20%E2%80%93%20Initiate%20Donation%20from%20Member.png)

Boundary: Donation amounts, payment processing, campaign validation and transaction statuses belong to the Donors/Donations workflows. Member preselection after navigation is a recommended enhancement requiring verification.

### MEM-WF-17 – Tenant Configuration and Feature Access

Goal: MEM-GO-001, MEM-GO-002, MEM-GO-003, MEM-GO-020

As-Is: Existing role-based permissions are implemented.

To-Be: Support independent organisation configurations and approved optional functionality while using the existing access framework.

![Tenant Configuration and Feature Access](Members/workflow_screenshot/MEM-WF-17%20%E2%80%93%20Tenant%20Configuration%20and%20Feature%20Access.png)

Configuration may govern permitted KPI choices, supported fields, filters, import options and eligible optional capabilities.

Platform security restrictions and tenant isolation cannot be disabled through tenant configuration.

### MEM-WF-18 – Audit and Exception Handling

Goal: MEM-GO-023

To-Be: Record material member-management events and handle failures without corrupting committed data.

| Event              | Required Business Outcome                  |
| ------------------ | ------------------------------------------ |
| Member created     | Record creator/source and creation outcome |
| Member updated     | Preserve material change history           |
| Import processed   | Record batch outcome and processing counts |
| Duplicate reviewed | Record administrator decision              |
| Integration error  | Preserve committed data and report failure |
| Export completed   | Record authorised export activity          |
| Access denied      | Prevent restricted operation               |
| Update conflict    | Prevent unapproved overwrites              |

![Audit and Exception Handling](Members/workflow_screenshot/MEM-WF-18%20%E2%80%93%20Audit%20and%20Exception%20Handling.png)

## 7. Shared Validation Rules

| Area                  | Business Requirement                                                                   |
| --------------------- | -------------------------------------------------------------------------------------- |
| Tenant                | Every read/write must respect tenant isolation                                         |
| Permissions           | Existing permission framework governs all actions                                      |
| Member identity       | Each donor must reference an existing member                                           |
| Administrative status | Active / Inactive                                                                      |
| Giving status         | Prospect / Pledged / Donated / Lapsed                                                  |
| Duplicates            | Detect possible duplicates; administrator review required for conflicting merge/update |
| Imports               | Validate mandatory fields and supported file formats                                   |
| Import results        | Distinguish created, updated, rejected and review-pending rows                         |
| KPIs                  | Retain existing calculation logic; extend for approved measures                        |
| KPI refresh           | Recalculate affected values automatically after successful import                      |
| Export                | Respect authorised filters and tenant boundaries                                       |
| Member updates        | Prevent unapproved conflicting changes                                                 |
| Audit                 | Preserve evidence of material actions                                                  |

## 8. Screenshot Reference Mapping

| Screenshot       | Existing UI                                     | Workflow References   |
| ---------------- | ----------------------------------------------- | --------------------- |
| Members Overview | KPIs, list, search, filters, export, add member | MEM-WF-01, 07, 11, 14 |
| Add New Member   | Five-section form and Save Draft                | MEM-WF-02, 03         |
| Member Details   | Profile, giving KPIs, Edit and Add Donation     | MEM-WF-08, 09, 16     |
| Donors Overview  | Related donor records and donor KPIs            | MEM-WF-16 dependency  |
| Add Donor        | Existing-member selection and donation fields   | MEM-WF-16 dependency  |
| Donor Details    | Giving summaries and donor information          | MEM-WF-16 dependency  |

Screenshots are UX references. Confirmed business rules remain authoritative where displayed values or prototype interactions are incomplete.

## 9. Goals-to-Workflow Traceability

| Business Goals | Workflows         |
| -------------- | ----------------- |
| MEM-GO-001–003 | MEM-WF-01, 17     |
| MEM-GO-004–005 | MEM-WF-02, 04, 05 |
| MEM-GO-006     | MEM-WF-02, 03, 09 |
| MEM-GO-007–009 | MEM-WF-05         |
| MEM-GO-010–012 | MEM-WF-04, 06, 09 |
| MEM-GO-013     | MEM-WF-07         |
| MEM-GO-014–015 | MEM-WF-11, 12     |
| MEM-GO-016–018 | MEM-WF-07, 13, 14 |
| MEM-GO-019     | MEM-WF-08, 09     |
| MEM-GO-020     | MEM-WF-01, 17     |
| MEM-GO-021–022 | MEM-WF-16         |
| MEM-GO-023–024 | MEM-WF-15, 18     |
| MEM-GO-025     | MEM-WF-02, 10     |

## 10. Feature Catalog Handoff

The Members Feature Catalog must break these workflows into independently identifiable and testable features covering:

- Tenant access, existing permissions and optional feature configuration.
- Member listing, search, filters, sorting and pagination.
- Five-section member registration, edit and draft handling.
- Integration ingestion, file import and source provenance.
- Duplicate identification and administrator resolution.
- Administrative and giving statuses.
- Member profile and donation relationship.
- Existing/additional KPIs and clickable drill-downs.
- Automatic KPI updates after committed data changes.
- Filtered export and refresh.
- Error handling, security and audit requirements.

Features must reference the relevant `MEM-GO`, `MEM-BR` and `MEM-WF` identifiers.

## 11. Decisions Requiring Detail

The following are implementation details requiring definition or business approval, rather than unresolved questions about the overall product objective.

| Area                | Detail to Finalise                                                   |
| ------------------- | -------------------------------------------------------------------- |
| Member registration | Exact mandatory fields, formats and type-specific validation         |
| Save Draft          | Persistence, visibility and resume rules                             |
| Duplicate matching  | Match identifiers, review queue and non-conflicting update handling  |
| Bulk import         | Template columns, limits, partial processing and re-import rules     |
| Member statuses     | Allowed status transitions and giving-status calculation             |
| KPIs                | Additional catalogue, drill-down criteria and preference persistence |
| Filters             | Combination, reset and default behaviour                             |
| Export              | Column selection and precise dataset boundaries                      |
| Integrations        | Source priority, sync errors and update conflicts                    |
| Donations           | Member preselection and confirmed transaction-driven status changes  |

## 12. Workflow Validation Summary

| Review Area                  | Result                                                |
| ---------------------------- | ----------------------------------------------------- |
| Existing functionality       | Preserved and distinguished from enhancements         |
| Standalone capability        | Tenant isolation and configuration incorporated       |
| Member–Donor relationship    | Updated to confirmed rule                             |
| Administrative/Giving status | Separate attributes documented                        |
| Duplicate handling           | Administrator review required for conflicting records |
| Permissions                  | Corrected to existing functionality                   |
| KPI calculations             | Existing logic retained; additions supported          |
| Import KPI updates           | Automatic recalculation included                      |
| Workflow coverage            | 18 functional workflows                               |
| Flowcharts                   | 20 process diagrams, including end-to-end journeys    |
| Goals alignment              | Mapped to MEM-GO-001–025                              |
| Document terminology         | No phase-based labels                                 |
| Next document                | Members BRD Feature Catalog                           |

This revised Workflow establishes the operating behaviour for the Members capability, preserving existing functionality while detailing the enhancements needed for standalone AiXPurpose.

The Members Feature Catalog can now be reviewed against these 18 workflows and the confirmed business rules.
