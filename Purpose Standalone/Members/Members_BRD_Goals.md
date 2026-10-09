# AiXPurpose Members — Business Requirements Document: Goals

> **Document type:** Business Requirements Document – Goals

## Document Control

| Field                   | Details                                                                                                                |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Document Name           | AiXPurpose – Members – Goals                                                                                           |
| Product                 | AiXPurpose                                                                                                             |
| Product Type            | Standalone, Multi-Tenant Application                                                                                   |
| Module                  | Donor Management                                                                                                       |
| Capability              | Members                                                                                                                |
| Document Type           | Business Requirements Document – Goals                                                                                 |
| Version                 | 1.0                                                                                                                    |
| Status                  | Draft for Business Review                                                                                              |
| Document Owner          | Product Management                                                                                                     |
| Business Owners         | Client Organisation / Fundraising Operations                                                                           |
| Related Workflow        | AiXPurpose – Members – Workflow                                                                                        |
| Related Feature Catalog | AiXPurpose – Members – Feature Catalog                                                                                 |
| Source References       | Existing AiXPurpose application, six prototype screenshots, functional walkthrough and standalone product requirements |
| Last Updated            | 9 October 2026                                                                                                         |

## Overview

This document defines the business goals, current operating state, standalone requirements, and intended outcomes for the Members capability in the AiXPurpose Donor Management module. It separates existing behaviour from proposed capabilities and highlights decisions that require approval.

Flowcharts are embedded as PNG images linked to their source assets in the repository.

## Contents

- [1. Document Purpose](#1-document-purpose)
- [2. Business Context](#2-business-context)
- [3. Business Problem Statement](#3-business-problem-statement)
- [4. Product Vision](#4-product-vision)
- [5. As-Is – Current Application State](#5-as-is--current-application-state)
- [6. To-Be – Future Application State](#6-to-be--future-application-state)
- [7. Business Goals and Objectives](#7-business-goals-and-objectives)
- [8. As-Is vs To-Be Capability Matrix](#8-as-is-vs-to-be-capability-matrix)
- [9. Business Capability Relationships](#9-business-capability-relationships)
- [10. Stakeholders and Actors](#10-stakeholders-and-actors)
- [11. Member Information Model](#11-member-information-model)
- [12. Business Rules and Constraints](#12-business-rules-and-constraints)
- [13. Member Data Lifecycle](#13-member-data-lifecycle)
- [14. Bulk Import Business Objectives](#14-bulk-import-business-objectives)
- [15. KPI and Visualisation Objectives](#15-kpi-and-visualisation-objectives)
- [16. Search, Filtering and Export](#16-search-filtering-and-export)
- [17. Member Profile and Detail Goals](#17-member-profile-and-detail-goals)
- [18. Member-Donor Business Relationship](#18-member-donor-business-relationship)
- [19. Data Ownership and Governance](#19-data-ownership-and-governance)
- [20. Security and Privacy Principles](#20-security-and-privacy-principles)
- [21. Business Dependencies](#21-business-dependencies)
- [22. Assumptions and Constraints](#22-assumptions-and-constraints)
- [23. Scope and Documentation Boundaries](#23-scope-and-documentation-boundaries)
- [24. Business Risks and Mitigations](#24-business-risks-and-mitigations)
- [25. Business Success Criteria](#25-business-success-criteria)
- [26. Open Business Decisions](#26-open-business-decisions)
- [27. Requirements Traceability Matrix](#27-requirements-traceability-matrix)
- [28. Relationship to BRD Workflow](#28-relationship-to-brd-workflow)
- [29. Relationship to Feature Catalog](#29-relationship-to-feature-catalog)
- [30. Product Management Validation Summary](#30-product-management-validation-summary)
- [31. Document Conclusion](#31-document-conclusion)

## 1. Document Purpose

This document defines the business goals, current operating state, standalone product requirements and expected business outcomes for the Members capability within the AiXPurpose Donor Management module.

AiXPurpose is an existing application developed for a client requiring consolidated visibility of member, donor and donation information originating from multiple applications.

The standalone product must retain the existing functionality while supporting different organisations with varying operational requirements, data sources, user permissions, reporting needs and configuration preferences.

This document establishes:

- The business purpose of Members management.
- The existing application capabilities (As-Is).
- The required standalone application capabilities (To-Be).
- Existing business limitations and enhancement opportunities.
- The relationship between members, donors, donations and campaigns.
- Business objectives, rules, dependencies and governance.
- Tenant-level configuration and isolation requirements.
- Business success criteria and acceptance outcomes.
- Traceability into the Workflow and Feature Catalog documents.

This document defines business intent and business rules. Detailed screen behaviour, validation scenarios, exception handling and feature-level acceptance criteria will be elaborated in the corresponding Workflow and Feature Catalog.

## 2. Business Context

### 2.1 Existing Business Context

The existing AiXPurpose application consolidates information from multiple external systems used by an organisation to maintain constituent, member, donor and donation records.

Data received through these systems is presented within AiXPurpose, allowing authorised administrators to access relevant information through a central interface.

The Members capability provides member registration, contact management, campaign-related information, membership status, record searching, filtering, basic KPI visibility and donation-related navigation.

The application also permits direct manual member entry, allowing authorised users to create records without depending entirely on external integrations.

### 2.2 Standalone Business Context

Different organisations may operate under different constituent-management models.

For example:

- Organisation A receives constituent and donation records from several integrated fundraising systems.
- Organisation B maintains member information manually.
- Organisation C has an existing spreadsheet containing thousands of member records.
- Organisation D requires centralised member visualisation and reporting without extensive operational functions.
- Organisation E requires configurable attributes, KPIs, filters and organisation-specific permissions.

A standalone AiXPurpose application must support these variations through a common product foundation, without requiring separately developed applications for every client.

### 2.3 Existing-to-Standalone Transition

![Existing-to-Standalone Transition](Screenshots/2.3%20Existing-to-Standalone%20Transition.png)

## 3. Business Problem Statement

### 3.1 Existing Application Limitations

The existing application was developed around the operational requirements of one client.

Although it provides useful member-management capabilities, its current design and available workflows do not yet establish all the capabilities required for broader standalone product adoption.

The following areas have been identified for enhancement.

| Area                       | Existing State                          | Business Limitation / Enhancement Need                                  |
| -------------------------- | --------------------------------------- | ----------------------------------------------------------------------- |
| Product configuration      | Existing client-specific implementation | Support differing organisational configurations through one application |
| Tenant management          | Developed for one client                | Support isolated tenant/workspace access                                |
| Data integration           | External integrations supported         | Support different client integration arrangements                       |
| Manual creation            | Existing Add Member functionality       | Retain and enhance validation and duplicate control                     |
| Bulk data import           | Not shown as existing functionality     | Provide spreadsheet and CSV member imports                              |
| Import validation          | Not established                         | Validate mandatory information and report errors                        |
| Data reconciliation        | Not fully specified                     | Prevent unintended duplicate or conflicting member records              |
| Member KPIs                | Four predefined dashboard cards         | Support configurable KPI selection and interactive filtering            |
| Member filters             | Type, status and search                 | Support additional tenant-relevant criteria                             |
| Data export                | Export CSV available                    | Support filtered and controlled exports                                 |
| Data refresh               | Not shown as a distinct action          | Provide refresh of current records and calculated summaries             |
| Member status              | Existing status labels                  | Clarify status definitions and lifecycle rules                          |
| Campaign and pledge fields | Existing year-specific presentation     | Support dynamic reporting periods                                       |
| Permissions                | Existing application access             | Establish tenant-scoped, role-based permissions                         |
| Data origin                | Multiple integrated sources             | Maintain source identification and reconciliation evidence              |
| Data completeness          | Fields can be updated                   | Provide clearer missing-data identification and correction              |
| Reporting                  | Existing metrics and list               | Support more flexible investigation and visualisation                   |

The objective is not to replace the application. It is to extend its existing capabilities into a configurable, reusable and governed standalone product.

## 4. Product Vision

To provide every organisation with a secure, configurable and centralised member-management capability that consolidates member information across supported sources and enables reliable member tracking, analysis and engagement-related decision-making.

The Members capability should support organisations regardless of whether their data originates from external applications, manual entry or spreadsheet-based imports.

### 4.1 Product Positioning

AiXPurpose Members is the central constituent-record management capability within Donor Management.

It establishes a trusted view of member information and supplies member context for related donor, campaign and donation operations.

The standalone product must provide common core functionality while allowing authorised organisational settings and eligible additional capabilities to vary by tenant.

### 4.2 Standalone Operating Model

![Standalone Operating Model](Screenshots/4.2%20Standalone%20Operating%20Model.png)

The diagram represents logical tenant isolation. The physical database and deployment architecture will be defined separately.

## 5. As-Is – Current Application State

### 5.1 Current Business Capability

The existing Members page enables authorised application users to view, create, search, filter, inspect and update member records.

It also provides KPI summaries and entry points into donation-related functionality.

Member records may originate from supported external integrations or from manual entry.

### 5.2 Existing Members Overview

The existing Members page contains:

| Component            | Current Functionality                            |
| -------------------- | ------------------------------------------------ |
| Total Members        | Displays total member metric                     |
| Conversion Ready     | Displays members identified as conversion-ready  |
| Email Verified       | Displays members with verified email information |
| Phone Verified       | Displays members with verified phone information |
| Member Search        | Searches member data by name, email or phone     |
| Donor Type Filter    | Filters Individual, Organisation and Foundation  |
| Member Status Filter | Filters Prospect, Pledged, Donated and Lapsed    |
| Member Listing       | Displays member records                          |
| Export CSV           | Exports member information                       |
| Add Member           | Opens the member creation interface              |
| Pagination           | Provides navigation across member records        |
| Row View             | Opens the selected member's profile              |
| Row Edit             | Opens the member's editable information          |
| Donation Action      | Opens donation-related entry/navigation          |

The supplied business walkthrough states that the existing Members list displays active members by default. The precise distinction between record activity and member lifecycle status requires confirmation.

### 5.3 Existing Members List Fields

The current list provides the following columns:

| Column        | Description                               |
| ------------- | ----------------------------------------- |
| Name          | Member or constituent name                |
| Donor Type    | Individual, Organisation or Foundation    |
| Contact       | Available email and phone information     |
| Location      | Member location                           |
| Member Status | Current member lifecycle classification   |
| Pledged 2024  | Existing year-specific pledge information |
| Created       | Record creation date                      |
| Actions       | View, Edit and Add Donation               |

The reference to 2024 is part of the current interface and must not become a permanently fixed year in the standalone product.

### 5.4 Current Member Creation

The existing member creation interface is organised into five sections.

| Section                            | Existing Information                                                                                                |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| 1. Constituent Contact Information | Donor type, title, first name, last name, email, mobile phone, home phone, business phone                           |
| 2. Address and Communication       | Address, ZIP/postal code, state, city, anonymous donor, Do Not Solicit                                              |
| 3. Campaign and Giving             | Current campaign, campaign status, solicitor, pledged amount                                                        |
| 4. Recognition and Social          | Recognition/publication fields, spouse information, alternate contact numbers and phone types                       |
| 5. Advanced / System Fields        | iWave score, capacity score, propensity score, affinity score, profile URL, guest details and other existing fields |

The screenshots also show a Save Draft option.

The exact persistence behaviour of draft records, field-level validation and ability to resume drafts have not yet been established and must be specified in the Workflow and Feature Catalog.

### 5.5 Existing Member Detail View

Selecting a record in the Members list opens a member profile containing relevant record information.

The displayed interface includes:

- Member name, classification and status.
- Contact information.
- Total Donations.
- Pledged Amount 2024.
- iWave Score.
- Member profile information.
- Edit action.
- Add Donation action.

Selecting the row and selecting the View icon must lead to the same record detail experience, as established in the functional walkthrough.

### 5.6 Existing Member Management Flow

![Existing Member Management Flow](Screenshots/5.6%20Existing%20Member%20Management%20Flow.png)

### 5.7 Current Data Sources

The existing application supports two confirmed paths for member data.

![Current Data Sources](Screenshots/5.7%20Current%20Data%20Sources.png)

The detailed transformation, matching and synchronisation rules for integrated records have not yet been provided.

### 5.8 Existing Application Constraints

The current application already has functional components suitable for reuse. However, the following standalone requirements are not yet established as existing capabilities:

- Structured bulk spreadsheet import.
- Import preview and row-level error handling.
- Organisation-specific feature enablement.
- Interactive KPI filtering.
- Custom KPI selection.
- Advanced location and data-source filtering.
- Filter-aware export behaviour.
- Formal source-priority and record reconciliation rules.
- Fully defined tenant-level permission and configuration governance.

These are enhancement requirements, not claims that the current application is defective.

## 6. To-Be – Future Application State

### 6.1 Standalone Business Objective

The enhanced Members capability must support independent client organisations with different member-management operating models.

The standalone application must allow authorised users to maintain a consolidated member register using supported data acquisition methods while ensuring tenant isolation, data quality, configurable insights and operational traceability.

### 6.2 Target Members Operating Model

![Target Members Operating Model](Screenshots/6.2%20Target%20Members%20Operating%20Model.png)

### 6.3 Target Business Capabilities

The standalone Members capability shall support:

1. Tenant-isolated member records.
2. Tenant-specific organisational configurations.
3. Configurable feature availability according to approved client entitlements.
4. External-system member ingestion.
5. Manual member creation and editing.
6. Predefined template-based spreadsheet import.
7. Import preview and validation.
8. Import results, error reporting and correction.
9. Duplicate member detection and controlled resolution.
10. Source attribution and record history.
11. Configurable member data fields within approved rules.
12. Member lifecycle and active/inactive record management.
13. Configurable KPI selection.
14. Clickable KPI-based list filtering.
15. Advanced member searching and filtering.
16. Filtered data exports.
17. Refresh of member records and summaries.
18. Dynamic pledge and reporting periods.
19. Permission-based member management.
20. Member profile visibility and data completeness.
21. Navigation to donor and donation operations.
22. Auditable record creation, modification and import activity.

These represent target capabilities. Detailed validation, calculation and implementation rules will be established through the corresponding BRD documents and the decisions recorded below.

## 7. Business Goals and Objectives

### 7.1 Standalone Product Goals

#### MEM-GO-001 – Multi-Tenant Member Management

Enable independent organisations to manage member data through isolated AiXPurpose tenant workspaces.

Expected outcome: Each organisation can access and maintain only its authorised records.

#### MEM-GO-002 – Reusable Product Capability

Provide a common Members management foundation that can operate across different organisations without client-specific redevelopment of core functionality.

Expected outcome: The existing Members capability becomes reusable across AiXPurpose clients.

#### MEM-GO-003 – Configurable Organisation Experience

Allow authorised tenant administrators to manage permitted settings, views, fields and optional capabilities according to their organisation's operational requirements.

Expected outcome: Organisations can configure their Members experience while retaining common platform standards.

#### MEM-GO-004 – Flexible Member Data Sources

Support member data originating from integrations, manual entry and approved bulk-import files.

Expected outcome: External software integrations are not mandatory for using Members management.

#### MEM-GO-005 – Centralised Member Register

Provide a unified tenant-level Members register that makes information from supported sources available through a consistent interface.

Expected outcome: Authorised users can find and manage member information without navigating multiple source applications.

### 7.2 Data Management Goals

#### MEM-GO-006 – Structured Manual Registration

Retain and enhance the existing five-section member registration capability.

Expected outcome: Authorised users can create and maintain member records directly within AiXPurpose.

#### MEM-GO-007 – Bulk Member Import

Allow authorised users to import member records from approved spreadsheet or CSV templates.

Expected outcome: Organisations can establish their member database without manually entering every existing record.

#### MEM-GO-008 – Import Data Validation

Validate uploaded records against defined mandatory fields, supported formats and data-quality rules.

Expected outcome: Administrators can identify missing or invalid information before it enters the trusted member register.

#### MEM-GO-009 – Import Transparency and Correction

Provide import summaries, record-level errors and administrator correction options.

Expected outcome: Users understand how many records were accepted, rejected or require attention.

#### MEM-GO-010 – Duplicate Record Prevention

Identify possible duplicate member records across manual entry, imports and integrations.

Expected outcome: Multiple data sources do not unintentionally create duplicate member identities.

#### MEM-GO-011 – Controlled Record Updates

Allow authorised users to update member information while retaining appropriate historical traceability.

Expected outcome: Corrections are reflected consistently without losing accountability.

#### MEM-GO-012 – Member Data Provenance

Maintain identification of the source from which a member record or update originated.

Expected outcome: Administrators can understand and investigate the origin of consolidated member information.

### 7.3 User Experience and Reporting Goals

#### MEM-GO-013 – Efficient Member Discovery

Enable users to locate relevant members through search, filtering, sorting and pagination.

Expected outcome: Member information remains accessible as tenant record volumes increase.

#### MEM-GO-014 – Actionable Member KPIs

Allow users to interact with member KPI cards and access the supporting member records.

Expected outcome: KPI information becomes directly actionable rather than only informational.

#### MEM-GO-015 – Configurable KPI Dashboard

Allow users or organisations to choose relevant member KPI cards from the measures permitted for their tenant.

Expected outcome: Different organisations can prioritise relevant member insights.

#### MEM-GO-016 – Advanced Member Filtering

Enable searching and filtering by additional approved member attributes.

Expected outcome: Users can investigate subsets of records relevant to their operations.

#### MEM-GO-017 – Targeted Data Export

Allow authorised users to export member records corresponding to approved filters and selection criteria.

Expected outcome: Data exports reflect the intended operational dataset.

#### MEM-GO-018 – Dynamic Reporting Periods

Replace fixed historical year references with approved reporting-period logic.

Expected outcome: Pledge-related member information remains relevant across reporting years.

#### MEM-GO-019 – Member Information Completeness

Enable administrators to identify and correct missing, incomplete or inconsistent member information.

Expected outcome: Member records become more reliable and useful for downstream activities.

### 7.4 Governance and Integration Goals

#### MEM-GO-020 – Role-Based Member Access

Control Members functionality according to assigned tenant roles and permissions.

Expected outcome: Users can perform only their authorised operations.

#### MEM-GO-021 – Consistent Member-Donor Relationship

Maintain reliable relationships between member records and related donor or donation information.

Expected outcome: Member and donor information remains connected without unintended duplication.

#### MEM-GO-022 – Reliable Donation Handoff

Retain the ability to initiate donation-related operations from the Members list and member profile.

Expected outcome: Relevant member context is preserved during donation entry.

#### MEM-GO-023 – Operational Auditability

Track material member creation, update, import, reconciliation and export activities.

Expected outcome: Administrators can investigate record changes and significant data operations.

#### MEM-GO-024 – Reliable Data Refresh

Allow users to refresh member lists and metrics to reflect the latest successfully committed data.

Expected outcome: Users can retrieve up-to-date member information without creating duplicate operations.

#### MEM-GO-025 – Consistent Member Business Rules

Apply defined member classifications, status rules and validations consistently across supported data-entry methods.

Expected outcome: The same tenant's member records follow common business rules regardless of their source.

## 8. As-Is vs To-Be Capability Matrix

| Capability                   | As-Is                                      | To-Be                                                | Change Classification    |
| ---------------------------- | ------------------------------------------ | ---------------------------------------------------- | ------------------------ |
| Members list                 | Available                                  | Retain with enhanced controls                        | Enhance                  |
| Add Member                   | Available                                  | Retain existing five sections; strengthen validation | Enhance                  |
| Edit Member                  | Available                                  | Retain with controlled updates                       | Enhance                  |
| Member profile               | Available                                  | Enrich with relevant source and quality information  | Enhance                  |
| Integrations                 | Available for existing client              | Support approved tenant-specific connectors          | Enhance                  |
| Manual entry                 | Available                                  | Continue independently of integrations               | Retain                   |
| Excel/CSV import             | Not established                            | Template-based import                                | New                      |
| Import preview               | Not established                            | Preview before commit                                | New                      |
| Import validation            | Not established                            | Mandatory-field and format checks                    | New                      |
| Import summary               | Not established                            | Success, failure and correction reporting            | New                      |
| Duplicate detection          | Not established                            | Cross-source identity checks                         | New                      |
| Tenant isolation             | Not established for multi-client operation | Isolated client data and access                      | New platform requirement |
| Tenant configurations        | Client-specific implementation             | Governed tenant-specific settings                    | Enhance                  |
| Optional feature entitlement | Not established                            | Approved feature availability by client              | New platform requirement |
| Total Members KPI            | Available                                  | Retain with defined calculation                      | Enhance                  |
| Conversion Ready KPI         | Available                                  | Retain with approved calculation and drill-down      | Enhance                  |
| Email Verified KPI           | Available                                  | Click to filter relevant records                     | Enhance                  |
| Phone Verified KPI           | Available                                  | Click to filter relevant records                     | Enhance                  |
| KPI selection                | Not established                            | Configurable KPI selection                           | New                      |
| Member search                | Available                                  | Retain and improve                                   | Enhance                  |
| Type/status filters          | Available                                  | Retain with consistent semantics                     | Enhance                  |
| Advanced filters             | Limited current filters                    | Add tenant-relevant filtering                        | Enhance                  |
| CSV export                   | Available                                  | Export authorised filtered records                   | Enhance                  |
| Refresh control              | Not shown                                  | Refresh current list and summaries                   | New                      |
| Fixed pledge year            | Existing 2024 reference                    | Dynamic period configuration                         | Enhance                  |
| Member donation navigation   | Available                                  | Retain with reliable member association              | Enhance                  |
| Audit trail                  | Not confirmed                              | Auditable material operations                        | New/verify existing      |

## 9. Business Capability Relationships

### 9.1 Member Management Architecture

![Member Management Architecture](Screenshots/9.1%20Member%20Management%20Architecture.png)

### 9.2 Relationship Between Members and Donations

The Members capability maintains constituent information, while donation-related capabilities record and present giving activity.

The standalone application must provide a consistent relationship between these records.

![Relationship Between Members and Donations](Screenshots/9.2%20Relationship%20Between%20Members%20and%20Donation.png)

The exact rules governing when a member becomes a donor, whether a donor is always linked to a member, and how historical donations are matched remain business decisions.

### 9.3 Tenant Configuration Relationship

![Tenant Configuration Relationship](Screenshots/9.3%20Tenant%20Configuration%20Relationship.png)

Each tenant's configuration must remain within platform-defined security, validation and data-governance boundaries.

## 10. Stakeholders and Actors

| Stakeholder / Actor                 | Business Responsibility                                                      |
| ----------------------------------- | ---------------------------------------------------------------------------- |
| Platform Product Owner              | Defines common AiXPurpose capabilities and approved optional functionality   |
| Platform Administrator              | Manages platform-level configurations and authorised tenant administration   |
| Tenant / Organisation Administrator | Manages organisational Members settings and permitted user access            |
| Members Administrator               | Creates, edits, imports, validates and maintains member records              |
| Fundraising / Development User      | Reviews member information, campaign involvement and related giving activity |
| Reporting / Analyst User            | Reviews KPIs, searches, filters and exports data where authorised            |
| Read-Only User                      | Views permitted member information without modification rights               |
| External Integration                | Supplies member information through approved connectors                      |
| Import Operator                     | Uploads approved member datasets and reviews processing results              |
| Audit / Compliance User             | Reviews permitted activity and data-operation history                        |
| Product / Engineering               | Implements and maintains the approved Members capability                     |
| QA / UAT                            | Validates requirements, expected outcomes and access boundaries              |

The actor list defines the proposed functional responsibilities. Exact role names and permission assignments must be configurable and approved.

## 11. Member Information Model

### 11.1 Core Member Information

Member data must be structured so that it can support individual people, organisations and foundations.

The current application uses a shared form structure for these types. The standalone product should retain a unified member model while supporting appropriate type-specific fields and validation.

### 11.2 Member Data Categories

| Category      | Existing Data                          | To-Be Consideration                                         |
| ------------- | -------------------------------------- | ----------------------------------------------------------- |
| Identity      | Donor type, title, name                | Appropriate display names for organisations and foundations |
| Contact       | Email, mobile, home and business phone | Normalisation, verification and completeness                |
| Address       | Address, city, state, ZIP/postal code  | Country-aware address support                               |
| Preferences   | Anonymous donor, Do Not Solicit        | Governed use of privacy and communication preferences       |
| Campaign      | Current campaign, solicitor, status    | Authoritative campaign references                           |
| Giving        | Pledged amount                         | Consistent period and currency treatment                    |
| Recognition   | Recognition/publication details        | Optional tenant-relevant attributes                         |
| Relationships | Spouse and guest fields                | Appropriate applicability to member type                    |
| Scoring       | iWave, capacity, propensity, affinity  | Optional values and source-specific interpretation          |
| System        | Created/updated metadata               | Source attribution, audit and data quality                  |

### 11.3 Member-Type Considerations

![Member-Type Considerations](Screenshots/11.3%20Member-Type%20Considerations.png)

Type-specific organisation and foundation forms are recommended enhancements. The existing screenshot shows person-oriented first-name and last-name fields even for an organisation record. The correct future display-name and validation rules must therefore be defined rather than assumed.

## 12. Business Rules and Constraints

The following rules establish the business baseline for standalone Members management. Rules marked Proposed require confirmation before being treated as final policy.

### 12.1 Tenant and Access Rules

| Rule ID    | Rule                                                                                                           | Classification           |
| ---------- | -------------------------------------------------------------------------------------------------------------- | ------------------------ |
| MEM-BR-001 | Every client organisation must operate within its own isolated tenant/workspace.                               | Confirmed                |
| MEM-BR-002 | Members data must not be accessible across unrelated tenants.                                                  | Confirmed                |
| MEM-BR-003 | The standalone product must support approved tenant-specific feature configurations and optional capabilities. | Confirmed                |
| MEM-BR-004 | Member read, create, edit, import and export operations must be authorised according to tenant permissions.    | To-Be requirement        |
| MEM-BR-005 | A user must not gain access to restricted member data by directly accessing a record URL or identifier.        | Proposed security rule   |
| MEM-BR-006 | Tenant configuration must not override mandatory platform security and isolation controls.                     | Proposed governance rule |

### 12.2 Member Record Rules

| Rule ID    | Rule                                                                                                  | Classification    |
| ---------- | ----------------------------------------------------------------------------------------------------- | ----------------- |
| MEM-BR-007 | A member record may originate through supported integrations or manual entry.                         | Confirmed As-Is   |
| MEM-BR-008 | Approved Excel/CSV imports must provide an additional member data source.                             | Confirmed To-Be   |
| MEM-BR-009 | Imported records must undergo defined validation before being committed.                              | To-Be requirement |
| MEM-BR-010 | The system must report successful and unsuccessful import outcomes.                                   | To-Be requirement |
| MEM-BR-011 | Authorised administrators must be able to correct incomplete or inaccurate member data.               | Confirmed To-Be   |
| MEM-BR-012 | Potential duplicate member records must be detected and handled according to approved matching rules. | Proposed          |
| MEM-BR-013 | Existing member data must not be silently overwritten by a conflicting external or imported value.    | Proposed          |
| MEM-BR-014 | Material member changes must preserve source and actor traceability.                                  | Proposed          |
| MEM-BR-015 | The same member identity must remain consistent across relevant member and donation relationships.    | To-Be requirement |

### 12.3 Existing Interaction Rules

| Rule ID    | Rule                                                                                                      | Classification    |
| ---------- | --------------------------------------------------------------------------------------------------------- | ----------------- |
| MEM-BR-016 | The current Members list displays active members by default.                                              | Confirmed As-Is   |
| MEM-BR-017 | Clicking a member row and selecting View must open the same Member Detail view.                           | Confirmed As-Is   |
| MEM-BR-018 | Selecting Edit must open the existing member form structure with the relevant record data.                | Confirmed As-Is   |
| MEM-BR-019 | Selecting Add Donation must open the associated donation-entry capability.                                | Confirmed As-Is   |
| MEM-BR-020 | The existing member form contains five principal sections.                                                | Confirmed As-Is   |
| MEM-BR-021 | Member status values must be standardised and used consistently across forms, lists, filters and reports. | To-Be requirement |
| MEM-BR-022 | Member activity state and lifecycle/giving status must be defined separately if both are required.        | Proposed          |

### 12.4 KPI and Reporting Rules

| Rule ID    | Rule                                                                                             | Classification    |
| ---------- | ------------------------------------------------------------------------------------------------ | ----------------- |
| MEM-BR-023 | Existing KPI definitions must be retained unless replaced by approved business rules.            | To-Be requirement |
| MEM-BR-024 | Clicking an enabled KPI must display the corresponding eligible records in the Members list.     | Confirmed To-Be   |
| MEM-BR-025 | Users must be able to select from approved available KPI measures.                               | Confirmed To-Be   |
| MEM-BR-026 | Additional filters must be supported according to agreed client requirements and available data. | Confirmed To-Be   |
| MEM-BR-027 | Exports must support the intended filtered member dataset.                                       | Confirmed To-Be   |
| MEM-BR-028 | Exported records must respect the requesting user's access permissions.                          | Proposed          |
| MEM-BR-029 | Reporting-period information must not rely on permanently hard-coded historical years.           | Proposed          |
| MEM-BR-030 | KPI totals and filtered records must use consistent authorised data scopes.                      | Proposed          |

### 12.5 Audit and Reliability Rules

| Rule ID    | Rule                                                                                                        | Classification    |
| ---------- | ----------------------------------------------------------------------------------------------------------- | ----------------- |
| MEM-BR-031 | Member imports must provide an auditable processing outcome.                                                | Proposed          |
| MEM-BR-032 | Refresh must retrieve current committed information without duplicating records.                            | To-Be requirement |
| MEM-BR-033 | Material record changes must identify the responsible user or source, where available.                      | Proposed          |
| MEM-BR-034 | Import failure must not incorrectly report rejected records as successfully imported.                       | Proposed          |
| MEM-BR-035 | Imported and integrated records must follow the same tenant isolation boundary as manually created records. | To-Be requirement |

## 13. Member Data Lifecycle

### 13.1 Target Member Lifecycle

![Target Member Lifecycle](Screenshots/13.1%20Target%20Member%20Lifecycle.png)

### 13.2 Member Status Model

The existing interface refers to the following member statuses:

- Prospect
- Pledged
- Donated
- Lapsed

The user has also confirmed that the list currently defaults to active members.

These two concepts require clear separation or an explicitly approved combined model.

Recommended To-Be design:

Use distinct fields for:

1. Record Activity Status: Active, Inactive or other approved administrative states.
2. Member Engagement/Giving Status: Prospect, Pledged, Donated, Lapsed or approved tenant-specific values.

This avoids treating an administratively inactive record as equivalent to a member whose giving activity has lapsed.

![Member Status Model](Screenshots/13.2%20Member%20Status%20Model.png)

This is a recommended data-model separation, not a claim about existing implementation. Rules for automatic status changes, including transitions after donation activity, require approval.

## 14. Bulk Import Business Objectives

### 14.1 Import Purpose

The bulk-import capability allows organisations to migrate or periodically provide member datasets without entering each record manually.

The system must support approved predefined templates and provide comprehensible outcomes to administrators.

### 14.2 Import Source Requirements

Required target formats include:

- CSV.
- Excel workbooks, subject to an approved format such as `.xlsx`.
- Other spreadsheet formats only where explicitly approved.

The import process should provide a downloadable template reflecting the required minimum fields.

### 14.3 Proposed Import Process

![Proposed Import Process](Screenshots/14.3%20Proposed%20Import%20Process.png)

### 14.4 Import Outcome Example

An import of 250 submitted rows should report results clearly.

For illustration only:

| Outcome                   | Example Count |
| ------------------------- | ------------- |
| Records submitted         | 250           |
| Successfully created      | 225           |
| Successfully updated      | 10            |
| Rejected due to errors    | 12            |
| Held for duplicate review | 3             |

These figures are examples, not guaranteed processing results.

A record awaiting correction or duplicate review must not be reported as successfully committed unless the approved workflow actually completes that operation.

### 14.5 Import Governance

Detailed rules must define:

- Mandatory columns by member type.
- Import permissions.
- Duplicate-matching criteria.
- Whether existing records may be updated through imports.
- Partial-success behaviour.
- Error reporting.
- File-size and row-count limits.
- Secure processing of uploaded information.
- Import history and auditability.
- Handling of interrupted or repeated imports.

## 15. KPI and Visualisation Objectives

### 15.1 Existing KPI Baseline

| KPI              | Existing Availability | Definition Status                                             |
| ---------------- | --------------------- | ------------------------------------------------------------- |
| Total Members    | Available             | Counting scope requires confirmation                          |
| Conversion Ready | Available             | Qualification rule requires confirmation                      |
| Email Verified   | Available             | Verification evidence and counting logic require confirmation |
| Phone Verified   | Available             | Verification evidence and counting logic require confirmation |

### 15.2 Proposed KPI Extensions

Additional suitable measures may include:

| Proposed KPI                             | Business Purpose                                                  |
| ---------------------------------------- | ----------------------------------------------------------------- |
| Active Members                           | Identify currently active records                                 |
| New Members                              | Monitor newly created member records                              |
| Members by Type                          | Understand composition by Individual, Organisation and Foundation |
| Members by Location                      | Understand geographic distribution                                |
| Members by Status                        | Analyse engagement/giving classifications                         |
| Members with Missing Contact Information | Identify data-quality gaps                                        |
| Members Imported Recently                | Review recent ingestion activity                                  |
| Members by Data Source                   | Understand origin of member information                           |
| Members with Pledges                     | Analyse pledge-related member records                             |
| Members Converted to Donors              | Monitor member-to-donor conversion once definitions are approved  |
| Duplicate Review Pending                 | Highlight potential identity conflicts                            |
| Member Data Completeness                 | Monitor missing or incomplete fields                              |

These are recommended KPI candidates. Their definitions, calculations, permitted audiences and availability depend on approved business rules and data quality.

### 15.3 KPI Interaction Model

![KPI Interaction Model](Screenshots/15.3%20KPI%20Interaction%20Model.png)

### 15.4 KPI Configuration

The standalone Members interface should allow authorised selection of KPI cards from a predefined, governed KPI library.

Configuration must distinguish:

- KPIs available to the tenant.
- KPIs permitted to the user.
- KPIs selected for display.
- KPI calculation definitions.
- Filters supported by each KPI.
- Reporting-period dependencies.

KPI configuration must not permit tenants to access data outside their authorised workspace.

## 16. Search, Filtering and Export

### 16.1 Search Capability

The existing Members page supports local searches by name, email or phone.

A separate application-wide Search Everything control is also present.

These must remain distinct capabilities.

- Members Search: Searches records within the authorised Members dataset.
- Global Search: Searches authorised information across supported AiXPurpose modules.

Global Search behaviour is a shared platform dependency and is not fully specified by this Members Goals document.

### 16.2 Target Advanced Filters

Recommended Members filter categories include:

| Filter               | Purpose                              |
| -------------------- | ------------------------------------ |
| Member Type          | Individual, Organisation, Foundation |
| Member Status        | Prospect, Pledged, Donated, Lapsed   |
| Record Activity      | Active / Inactive where supported    |
| Country              | Geographic selection                 |
| State / Region       | Regional analysis                    |
| City                 | Local analysis                       |
| Created Date         | Registration period                  |
| Updated Date         | Recently modified records            |
| Record Source        | Manual, Import, Integration          |
| Campaign             | Campaign-linked members              |
| Contact Verification | Email / phone verification           |
| Pledge Range         | Pledge-based filtering               |
| Missing Information  | Identify incomplete member records   |

Filter availability must depend on tenant configuration, actual data and user permissions.

### 16.3 Filter and Export Journey

![Filter and Export Journey](Screenshots/16.3%20Filter%20and%20Export%20Journey.png)

### 16.4 Export Principles

The standalone export capability should support:

- Export of the current filtered dataset.
- Export of specifically selected records, where selection functionality is approved.
- Export of approved member columns.
- Consistent field formatting.
- Exclusion of records outside the user's access scope.
- Auditability of significant exports.

Whether exports support configurable columns, saved reports and additional file formats remains subject to product approval.

## 17. Member Profile and Detail Goals

The member profile must provide a reliable, understandable representation of the selected constituent.

### 17.1 Existing Profile Information

The existing profile includes:

- Member identity.
- Member classification.
- Member status.
- Contact information.
- Total Donations.
- Pledged Amount 2024.
- iWave Score.
- Edit.
- Add Donation.

### 17.2 Recommended Profile Enhancements

Recommended additions include:

- Record source and source reference.
- Latest synchronisation or import status, where applicable.
- Data completeness indicator.
- Record creation and last-modified information.
- Relevant campaign and giving summaries.
- History of material member changes, subject to permission.
- Appropriate status and verification indicators.
- Clear identification of unresolved data inconsistencies.

### 17.3 Member Profile Journey

![Member Profile Journey](Screenshots/17.3%20Member%20Profile%20Journey.png)

The source and quality sections are To-Be recommendations. They are not identified as current UI components.

## 18. Member-Donor Business Relationship

### 18.1 Business Relationship Principle

The standalone application must maintain a clear distinction between member identity and donation activity.

The existing Add Donor interface requires selection of an existing member before donation details are entered.

This establishes a current dependency between member selection and donation entry.

However, the exact technical meaning of separate Members and Donors records has not been established.

### 18.2 Existing Donation Handoff

![Existing Donation Handoff](Screenshots/18.2%20Existing%20Donation%20Handoff.png)

Preselection and subsequent updates to member status, giving totals and donor scoring must be confirmed.

### 18.3 Target Relationship Objectives

The standalone product should ensure:

- Donation records are associated with the correct constituent.
- The same constituent is not unintentionally duplicated because of donation activity.
- Giving information displayed in member and donor views is consistent.
- Member status and donor classification follow approved business definitions.
- Imported donation history can be associated with existing members through governed matching.
- Tenant isolation applies to every relationship.

The precise data model, matching rules and status transitions will be addressed in the relevant detailed documentation.

## 19. Data Ownership and Governance

### 19.1 Information Ownership

| Information                       | Proposed Business Owner                                 |
| --------------------------------- | ------------------------------------------------------- |
| Tenant configuration              | Tenant Administration / Platform Governance             |
| Member identity and profile       | Members Capability                                      |
| Member contact information        | Members Capability                                      |
| External source record references | Integration / Data Management                           |
| Import batches and outcomes       | Import/Data Management                                  |
| Campaign definitions              | Campaigns Capability                                    |
| Donation transactions             | Donations Capability                                    |
| Pledge records                    | Authoritative giving/pledge capability, to be confirmed |
| Member KPI definitions            | Product / Reporting Governance                          |
| User permissions                  | Identity / Access Management                            |
| Audit records                     | Platform Audit Capability                               |

These represent target ownership boundaries and must be reconciled with the platform's actual architecture.

### 19.2 Governance Principles

1. Each organisation owns access to its tenant data.
2. Platform administrators must not be assumed to have unrestricted access to tenant constituent information.
3. Member records require stable identity and source attribution.
4. Data imported from external systems must follow approved reconciliation rules.
5. Financial giving information must remain consistent with authoritative donation records.
6. User permissions must govern sensitive reads, edits and exports.
7. Historical audit records must not be silently overwritten during member updates.
8. Optional product features must remain governed by platform configuration and entitlements.

## 20. Security and Privacy Principles

The standalone Members capability must apply privacy-aware management of constituent information.

### 20.1 Required Security Outcomes

- Tenant-level isolation.
- Authorised record access.
- Role-based create, edit, import and export privileges.
- Protected transmission and storage of personal data.
- Safe handling of uploaded files.
- Controlled access to sensitive member fields.
- Auditability of material data operations.
- Protection from unauthorised cross-tenant searching.
- Secure validation of integrations and import operations.
- Appropriate handling of anonymous donor and Do Not Solicit preferences.

### 20.2 Tenant Data Boundary

![Tenant Data Boundary](Screenshots/20.2%20Tenant%20Data%20Boundary.png)

Detailed security controls, retention requirements and applicable jurisdiction-specific obligations require separate approval.

## 21. Business Dependencies

The Members capability depends on the following services or capabilities.

| Dependency            | Requirement                                                                    |
| --------------------- | ------------------------------------------------------------------------------ |
| Tenant Management     | Client workspace and isolation                                                 |
| Authentication        | Secure user login and session management                                       |
| Authorisation         | Permission evaluation for member actions                                       |
| Member Data Storage   | Persistent member records                                                      |
| External Integrations | Approved source connectivity                                                   |
| Import Processing     | File validation and member ingestion                                           |
| Campaigns             | Campaign selection and references                                              |
| Donations             | Donation records and giving summaries                                          |
| Reporting/KPI Service | Member metric calculations                                                     |
| Export Service        | Controlled data extraction                                                     |
| File Storage          | Secure temporary import-file handling                                          |
| Audit Service         | Material activity tracking                                                     |
| Global Search         | Cross-module authorised searching                                              |
| AI Copilot            | Existing shared entry point; detailed behaviour to be specified separately     |
| Notification Service  | Shared notification interface; Members-specific events to be defined as needed |

The requirements do not establish that each dependency must be a separate technical microservice.

## 22. Assumptions and Constraints

### 22.1 Confirmed Constraints

- AiXPurpose already exists.
- Members is part of Donor Management.
- Multiple external integrations are part of the existing solution.
- Manual member creation is available.
- Member data must also be importable through approved templates in the standalone product.
- Each client requires an isolated tenant/workspace.
- Client-specific optional functionality must be supported.
- The existing Members experience provides four primary KPI cards.
- KPI cards should support relevant list drill-downs.
- More KPI choices and relevant filters are required.
- Members export must support targeted filtering.
- Member records support viewing, editing and donation-related navigation.
- Documentation must address both business and technical stakeholders.

### 22.2 Proposed Design Assumptions

The following require validation before final approval:

- Imported records can update existing members.
- Administrators can review possible duplicates before merging.
- A separate administrative Active/Inactive status exists.
- Member-type-specific identity fields are introduced.
- KPI display preferences can be saved per user or tenant.
- Members support configurable additional fields.
- Source provenance is visible within the member profile.
- Reporting years can be selected dynamically.
- Member data completeness is calculated.
- Export history is retained.
- Member changes produce detailed audit records.

These assumptions must not be presented as confirmed existing application functionality.

## 23. Scope and Documentation Boundaries

### 23.1 Included Members Capabilities

This document includes the business goals for:

- Members overview and listing.
- Member KPI visibility and interaction.
- Member search and filtering.
- Manual member creation.
- Member editing.
- Member profile viewing.
- Existing member data integrations.
- Member bulk import.
- Import validation and correction.
- Member source identification.
- Record matching and duplicate handling.
- Member status management.
- Filtered export.
- Refresh.
- Tenant configuration and access.
- Member-related donation navigation.
- Relevant audit and governance requirements.

### 23.2 Related Capability Boundaries

The following capabilities are connected to Members but are specified in their respective module/page documents:

| Capability            | Relationship to Members                                                    |
| --------------------- | -------------------------------------------------------------------------- |
| Donors                | Uses constituent/member information for donor-related functionality        |
| Donations and Finance | Provides giving transactions and donation summaries                        |
| Campaigns             | Provides campaign references and involvement context                       |
| Segments              | May use member data for grouping and segmentation                          |
| Prospecting           | May use member information and qualification attributes                    |
| Communications        | Uses eligible contact information and applicable communication preferences |
| Reports and Analytics | May consume member metrics and reporting datasets                          |
| AI Copilot            | May provide authorised assistance using available application context      |

These capabilities remain part of the broader AiXPurpose product. They are not excluded from the overall product scope.

This document does not independently define their full business workflows or implementation requirements.

## 24. Business Risks and Mitigations

| Risk                                   | Business Impact                                   | Recommended Mitigation                               |
| -------------------------------------- | ------------------------------------------------- | ---------------------------------------------------- |
| Cross-tenant data exposure             | Confidentiality and client trust risk             | Enforce tenant boundaries for every data operation   |
| Duplicate member records               | Inaccurate counts and fragmented giving history   | Matching rules and controlled duplicate review       |
| Invalid imported files                 | Incomplete or inaccurate member information       | Pre-import validation and clear errors               |
| Integration conflicts                  | Unintended data overwrites                        | Defined source priority and reconciliation           |
| Incorrect KPI definitions              | Misleading operational decisions                  | Approved KPI calculation catalogue                   |
| Uncontrolled exports                   | Exposure of sensitive constituent information     | Permission-controlled exports                        |
| Hard-coded client assumptions          | Limited standalone reusability                    | Tenant configuration and configurable business rules |
| Inconsistent member/donor relationship | Incorrect giving summaries and identities         | Agreed member-to-donor business model                |
| Fixed reporting year                   | Outdated pledge summaries                         | Dynamic reporting period                             |
| Unclear member status semantics        | Incorrect filters and dashboard counts            | Formal member lifecycle definitions                  |
| Excessive configuration freedom        | Inconsistent behaviour and maintenance complexity | Governed configuration catalogue                     |
| Unclear optional-feature dependencies  | Incomplete client experience                      | Feature entitlement and dependency controls          |

## 25. Business Success Criteria

The Members capability may be considered business-ready for standalone use when the following outcomes are demonstrably satisfied.

| ID         | Success Outcome                                                                                |
| ---------- | ---------------------------------------------------------------------------------------------- |
| MEM-SC-001 | Different organisations can use Members through isolated workspaces                            |
| MEM-SC-002 | Tenant configurations do not expose another organisation's data                                |
| MEM-SC-003 | Members can be created without third-party integrations                                        |
| MEM-SC-004 | Supported integrated member information can appear in the relevant tenant register             |
| MEM-SC-005 | Approved member files can be imported through predefined templates                             |
| MEM-SC-006 | Import results clearly distinguish accepted, rejected and unresolved records                   |
| MEM-SC-007 | Administrators can correct member data under their permissions                                 |
| MEM-SC-008 | Possible duplicates are addressed through defined business rules                               |
| MEM-SC-009 | Existing member viewing, editing and donation navigation remain functional                     |
| MEM-SC-010 | Users can interact with available KPIs to inspect relevant member records                      |
| MEM-SC-011 | Permitted KPIs can be configured for an organisation or user                                   |
| MEM-SC-012 | Advanced filters support approved investigation needs                                          |
| MEM-SC-013 | Filtered exports contain only eligible records                                                 |
| MEM-SC-014 | Member data and KPI information refresh consistently                                           |
| MEM-SC-015 | Member and donor relationships remain accurate according to approved definitions               |
| MEM-SC-016 | Material data changes can be investigated through appropriate audit evidence                   |
| MEM-SC-017 | Core Members functionality remains reusable across supported organisations                     |
| MEM-SC-018 | Approved optional capabilities can be enabled according to tenant entitlement and dependencies |

Numerical targets for performance, adoption, import throughput and data quality have not been supplied. Such targets should be established separately rather than invented.

## 26. Open Business Decisions

| ID         | Decision Required                                                             | Importance                                          |
| ---------- | ----------------------------------------------------------------------------- | --------------------------------------------------- |
| MEM-OD-001 | Define Member, Donor, Prospect and converted donor                            | Governs data relationships and KPIs                 |
| MEM-OD-002 | Define Active independently of Prospect/Pledged/Donated/Lapsed, if applicable | Governs default list and status filtering           |
| MEM-OD-003 | Confirm mandatory fields for each member type                                 | Governs manual entry and import                     |
| MEM-OD-004 | Confirm organisation/foundation naming rules                                  | Prevents person-name requirements on entity records |
| MEM-OD-005 | Approve import template fields and supported file formats                     | Governs bulk import                                 |
| MEM-OD-006 | Define duplicate-matching and merge/update rules                              | Prevents record corruption                          |
| MEM-OD-007 | Define source-of-truth and integration conflict priorities                    | Governs consolidated records                        |
| MEM-OD-008 | Confirm user roles and action-level permissions                               | Governs authorisation                               |
| MEM-OD-009 | Define Conversion Ready, Email Verified and Phone Verified calculations       | Governs KPI accuracy                                |
| MEM-OD-010 | Determine whether clicking a KPI combines with or replaces existing filters   | Governs KPI drill-down behaviour                    |
| MEM-OD-011 | Approve additional KPIs and their configuration scope                         | Governs dashboard personalisation                   |
| MEM-OD-012 | Approve advanced filter catalogue and export rules                            | Governs reporting and extraction                    |
| MEM-OD-013 | Define reporting-period defaults and pledge currency rules                    | Governs accurate pledge presentation                |
| MEM-OD-014 | Confirm Save Draft lifecycle                                                  | Governs incomplete member creation                  |
| MEM-OD-015 | Confirm member preselection and status changes after donation entry           | Governs Members/Donors consistency                  |
| MEM-OD-016 | Define configurable field rules and required field dependencies               | Governs tenant flexibility                          |
| MEM-OD-017 | Establish optional-feature entitlement model                                  | Governs client-specific functionality               |
| MEM-OD-018 | Define data retention, audit visibility and privacy rules                     | Governs compliance                                  |
| MEM-OD-019 | Confirm import size limits and operational performance expectations           | Governs scaling                                     |
| MEM-OD-020 | Define measurable business adoption and data-quality targets                  | Governs success measurement                         |

## 27. Requirements Traceability Matrix

The following matrix connects business goals with their expected Workflow and Feature Catalog coverage. The identifiers for the latter two documents are proposed references until those documents are reviewed.

| Goal References | Workflow Coverage Required                        | Feature Catalog Coverage Required                    |
| --------------- | ------------------------------------------------- | ---------------------------------------------------- |
| MEM-GO-001–003  | Tenant access and configuration                   | Tenant isolation, permissions, feature configuration |
| MEM-GO-004–005  | Multi-source member ingestion and register access | Integrations, manual creation, consolidated list     |
| MEM-GO-006      | Manual member creation and editing                | Five-section form, field applicability, save/draft   |
| MEM-GO-007–009  | Bulk import, validation and correction            | Import template, upload, preview, processing results |
| MEM-GO-010–012  | Matching, controlled updates and provenance       | Duplicate handling, source tracking, change history  |
| MEM-GO-013      | Search, sorting, filtering and pagination         | Members list controls                                |
| MEM-GO-014–015  | KPI interaction and selection                     | KPI library, calculations and drill-downs            |
| MEM-GO-016–018  | Advanced filtering, export and period selection   | Filter catalogue, export, dynamic reporting          |
| MEM-GO-019      | Data quality review and correction                | Missing-field indicators and permitted edits         |
| MEM-GO-020      | Role-based access                                 | Permission-controlled page and record operations     |
| MEM-GO-021–022  | Member-to-donor relationship and donation handoff | Record association, donation navigation              |
| MEM-GO-023–024  | Audit and refresh journeys                        | Audit evidence, refresh behaviour                    |
| MEM-GO-025      | Status and cross-source rule consistency          | Shared validation and lifecycle constraints          |

### 27.1 Traceability Model

![Traceability Model](Screenshots/27.1%20Traceability%20Model.png)

Every major To-Be Members capability must be traceable to an approved business goal and one or more business rules.

The Workflow must explain how the capability operates, while the Feature Catalog must define the functional behaviour sufficiently for implementation and validation.

## 28. Relationship to BRD Workflow

The Members Workflow document must elaborate the operational journeys derived from this Goals document.

Expected coverage includes:

1. Tenant access and Members navigation.
2. Members overview and initial loading.
3. Manual member creation.
4. Five-section form navigation.
5. Save Draft and resume behaviour, once defined.
6. Member type and field applicability.
7. View member and edit member.
8. External integration data ingestion.
9. Spreadsheet template selection.
10. Import file upload and structural validation.
11. Row validation and error handling.
12. Duplicate detection and controlled resolution.
13. Import confirmation and refresh.
14. Member source/history investigation.
15. KPI loading and selection.
16. KPI-click drill-down into Members.
17. Member search and combined filters.
18. Filtered export.
19. Record status and lifecycle management.
20. Dynamic pledge-period selection.
21. Member-to-donation navigation.
22. Tenant permissions and denial conditions.
23. Concurrency and update-conflict handling.
24. Audit and operational exception journeys.

Detailed flows must distinguish confirmed existing behaviour from approved standalone changes.

## 29. Relationship to Feature Catalog

The Members Feature Catalog must convert approved requirements into granular, independently identifiable functional capabilities.

Each applicable feature should include:

- Feature ID and name.
- Business purpose.
- Related business goals.
- Related workflow steps.
- Actor and permission context.
- Existing or new/enhanced classification.
- Preconditions.
- Required fields and validation rules.
- Processing and business logic.
- Expected results.
- Error and exception outcomes.
- Security and tenant restrictions.
- Audit requirements where relevant.
- Acceptance criteria.
- Dependencies and unresolved decisions.

The Feature Catalog must not silently assume that recommended options or unresolved business decisions are already approved.

## 30. Product Management Validation Summary

| Review Area                   | Validation Conclusion                                                         |
| ----------------------------- | ----------------------------------------------------------------------------- |
| Existing application retained | Existing Members functionality has been preserved as the As-Is baseline       |
| Standalone direction          | Multi-client product reuse is explicitly established                          |
| Tenant separation             | Isolated tenant/workspace is included as a core requirement                   |
| Tenant-specific features      | Corrected to support optional approved features and configurations            |
| Data acquisition              | Integrations, manual entry and file import are covered                        |
| Import controls               | Validation, outcomes, correction and matching are addressed                   |
| Member fields                 | Existing five-section structure is preserved                                  |
| KPIs                          | Current cards and proposed configurable interaction are addressed             |
| Filters and exports           | Existing controls and enhanced targeted filtering are included                |
| Member/Donor linkage          | Explicitly defined as a shared business dependency requiring consistent rules |
| Security and governance       | Tenant-scoped access and data-operation controls are included                 |
| Documentation structure       | Goals, rules, workflows and features are linked conceptually                  |
| Unsupported assumptions       | Significant unresolved business decisions are identified                      |
| Scope                         | Focus remains on Members while recognising related AiXPurpose capabilities    |
| Terminology                   | No phase-based documentation labels used                                      |

## 31. Document Conclusion

The standalone AiXPurpose Members capability must evolve from an existing client-specific member-management implementation into a configurable, secure and reusable constituent-management capability for multiple independent organisations.

The target solution must preserve established Members functions, introduce additional supported data-ingestion methods, strengthen record quality and governance, and make member information more actionable through configurable KPIs, advanced filters and targeted exports.

The Members capability must maintain reliable relationships with related donor, campaign and donation operations while supporting client-specific configurations without compromising tenant isolation or common platform standards.

This Goals document provides the business baseline for the Members Workflow and Feature Catalog. Detailed behaviour and acceptance criteria must be based on confirmed requirements and explicitly resolved business decisions.
