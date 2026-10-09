# AiXPurpose – Donor Management – Donors

> **Document type:** Business Requirements Document – Goals

## Document Control

| Field                | Details                                                                                        |
| -------------------- | ---------------------------------------------------------------------------------------------- |
| Document Name        | AiXPurpose – Donors – BRD Goals                                                                |
| Product              | AiXPurpose                                                                                     |
| Module               | Donor Management                                                                               |
| Page                 | Donors                                                                                         |
| Application Type     | Standalone, Multi-Tenant Application                                                           |
| Document Type        | Business Requirements Document – Goals                                                         |
| Version              | 1.0                                                                                            |
| Status               | Draft for Business Review                                                                      |
| Related Document     | Members BRD Goals                                                                              |
| Subsequent Documents | Donors BRD Workflow and Feature Catalogue                                                      |
| Requirement Source   | Existing application, screenshots, business walkthrough and standalone AiXPurpose requirements |

## Overview

This document defines the business goals, current state, target outcomes, assumptions, constraints, and decisions for the Donors capability.

## Contents

- [1. Document Purpose](#1-document-purpose)
- [2. Business Context](#2-business-context)
- [3. Business Problem Statement](#3-business-problem-statement)
- [4. Product Vision](#4-product-vision)
- [5. As-Is – Current Application State](#5-as-is--current-application-state)
- [6. To-Be – Standalone Application State](#6-to-be--standalone-application-state)
- [7. Business Goals and Objectives](#7-business-goals-and-objectives)
- [8. As-Is vs To-Be Comparison](#8-as-is-vs-to-be-comparison)
- [9. Member–Donor Business Relationship](#9-memberdonor-business-relationship)
- [10. Stakeholders and Actors](#10-stakeholders-and-actors)
- [11. Business Rules](#11-business-rules)
- [12. Donation Data Lifecycle](#12-donation-data-lifecycle)
- [13. Donor Tier Configuration](#13-donor-tier-configuration)
- [14. Donor Scoring Requirements](#14-donor-scoring-requirements)
- [15. KPI and Reporting Objectives](#15-kpi-and-reporting-objectives)
- [16. Search, Filtering and Export](#16-search-filtering-and-export)
- [17. Bulk Import Business Objectives](#17-bulk-import-business-objectives)
- [18. Donor Profile Objectives](#18-donor-profile-objectives)
- [19. Tenant Configuration](#19-tenant-configuration)
- [20. Data Governance and Ownership](#20-data-governance-and-ownership)
- [21. Security and Privacy](#21-security-and-privacy)
- [22. Business Dependencies](#22-business-dependencies)
- [23. Assumptions and Constraints](#23-assumptions-and-constraints)
- [24. Scope and Capability Boundaries](#24-scope-and-capability-boundaries)
- [25. Business Risks and Mitigations](#25-business-risks-and-mitigations)
- [26. Business Success Criteria](#26-business-success-criteria)
- [27. Open Business Decisions](#27-open-business-decisions)
- [28. Goals-to-Workflow Traceability](#28-goals-to-workflow-traceability)
- [29. Relationship to BRD Workflow](#29-relationship-to-brd-workflow)
- [30. Relationship to Feature Catalogue](#30-relationship-to-feature-catalogue)
- [31. Product Validation Summary](#31-product-validation-summary)
- [32. Document Conclusion](#32-document-conclusion)

## 1. Document Purpose

This document defines the business objectives, existing functionality, standalone enhancements, business rules and expected outcomes for the Donors page within AiXPurpose Donor Management.

AiXPurpose is an existing application originally developed for a specific client to consolidate donor and donation information from multiple external applications.

The standalone product must preserve its existing capabilities while enabling independent organisations to manage donor records, donation activity, donor classifications, KPIs and reporting according to their requirements.

This document establishes the business foundation for the Donors Workflow and Feature Catalogue.

## 2. Business Context

### 2.1 Existing Application Context

The existing AiXPurpose application consolidates donor and donation information originating from external systems.

It provides centralised visibility into donor records, donation amounts, giving history, donor tiers, donor scores and engagement-related information.

Users can also manually record donations against existing members.

### 2.2 Standalone Application Context

Different organisations may operate with different fundraising and donor-management processes.

| Organisation             | Example Operating Requirement                    |
| ------------------------ | ------------------------------------------------ |
| Church                   | Track registered members and their donations     |
| Charity                  | Manage contributors and donation history         |
| NGO                      | Consolidate donations from multiple sources      |
| Educational Foundation   | Track alumni giving and donor contributions      |
| Community Organisation   | Manage contributions and member activity         |
| Fundraising Organisation | Import historical donor and donation information |

The standalone product must support organisations that rely on integrations, manual entry, spreadsheet imports or primarily donor analysis and reporting.

### 2.3 Business Transformation

![Business Transformation](screenshot%20goals/2.3%20Business%20Transformation.png)

## 3. Business Problem Statement

The existing Donors functionality supports the original client's requirements. However, standalone adoption requires additional flexibility, data-ingestion capabilities, governance and organisation-specific configuration.

| Business Area             | As-Is                                                              | To-Be Requirement                                 |
| ------------------------- | ------------------------------------------------------------------ | ------------------------------------------------- |
| Product Usage             | Client-specific                                                    | Multiple independent organisations                |
| Tenant Management         | Multi-client separation not established in original implementation | Isolated tenant workspaces                        |
| Role Permissions          | Existing functionality                                             | Reuse and extend permissions                      |
| Donor Data Sources        | Integrations and manual entry                                      | Integrations, manual entry and bulk import        |
| Member–Donor Relationship | Existing Member selection                                          | Enforce consistent member-linked donor identity   |
| Donor Tiers               | Platinum, Gold, Silver, Bronze                                     | Configurable organisational thresholds            |
| KPIs                      | Four existing metrics                                              | Configurable and clickable KPIs                   |
| Filters                   | Tier and advanced filters                                          | Additional business-relevant filters              |
| Export                    | Existing CSV export                                                | Filtered, permission-controlled export            |
| Donor Profile             | Giving history, scoring and engagement                             | Enhanced source visibility and data consistency   |
| Duplicate Control         | Not fully established                                              | Duplicate detection and authorised reconciliation |
| Data Updates              | Existing calculations                                              | Automatic KPI updates after committed changes     |
| Reporting                 | Existing overview and profiles                                     | Enhanced donor analytics and visualisations       |

The objective is to extend existing functionality into a reusable standalone product, not rebuild it from scratch.

## 4. Product Vision

Provide organisations with a secure, centralised and configurable donor-management capability that connects donors to members, consolidates giving information and supports reliable fundraising decisions.

### 4.1 Core Product Principles

- Every donor must be associated with an existing member.
- Not every member is required to be a donor.
- Member identity and donation records must remain consistent.
- External integrations must not be mandatory.
- Each organisation must have isolated data and access.
- Existing functionality must be retained.
- Organisational donor tiers and eligible optional capabilities must be configurable.
- KPI calculations must remain consistent with the established calculation framework.
- Conflicting imported and integrated records must be governed.
- Donor reporting must use authoritative data.

### 4.2 Member–Donor Relationship

![Member–Donor Relationship](screenshot%20goals/4.2%20Member%E2%80%93Donor%20Relationship.png)

A qualifying donation establishes donor eligibility. The exact qualifying transaction statuses must be approved.

## 5. As-Is – Current Application State

### 5.1 Existing Donors Overview

The Donors page currently displays four KPI cards.

| KPI            | Existing Purpose                       |
| -------------- | -------------------------------------- |
| Total Donors   | Summarises donor population            |
| Active Pledges | Summarises active pledge information   |
| Retention Rate | Displays donor retention information   |
| Prospects      | Displays prospective donor information |

Existing KPI calculations are already implemented and must be retained.

Their exact formulas and reporting periods must be documented from the current application.

### 5.2 Existing Donors Listing

The current Donors page provides:

- Donor search.
- Tier-based filtering.
- Advanced Filters.
- Export CSV.
- Add Donor.
- Donor listing.
- Row selection.
- Three-dot actions for opening donor details.

The available tier options are:

All, Platinum, Gold, Silver and Bronze.

The default selection is All.

### 5.3 Existing Donor List Columns

| Column      | Description                            |
| ----------- | -------------------------------------- |
| Donor       | Donor identity                         |
| Type        | Individual, Organisation or Foundation |
| Tier        | Donor classification                   |
| Total Given | Recorded giving total                  |
| Last Gift   | Most recent gift information           |
| Status      | Existing donor status                  |

### 5.4 Existing Add Donor Functionality

The Add Donor popup provides:

| Field           | Required |
| --------------- | -------- |
| Select Member   | Yes      |
| Donation Amount | Yes      |
| Campaign        | Yes      |
| Payment Method  | Yes      |
| Donation Date   | Yes      |
| Notes           | No       |
| Save Donation   | Action   |

The member lookup supports searching by name, email or phone.

Campaign options are sourced from the existing Campaigns capability.

The meaning of Save Donation, including whether it records an already received payment or processes a payment, requires confirmation.

### 5.5 Existing Advanced Filters

| Filter              | Existing Options  |
| ------------------- | ----------------- |
| Donation Amount     | Amount range      |
| Donor Score         | Score range 0–100 |
| Engagement Segments | New Donors        |
| Engagement Segments | Lapsing           |
| Engagement Segments | Major Prospects   |
| Engagement Segments | Monthly Donors    |

The meanings and calculation rules behind these segments require verification.

### 5.6 Existing Donor Detail View

Clicking a donor row or its three-dot action opens the same donor detail view.

The profile provides:

- Donor name and identity.
- Contact information.
- Donor type.
- Donor tier.
- Donor status.
- Donor score.
- Lifetime Giving.
- Last Gift.
- Total Gifts.
- Overview tab.
- History tab.
- Engagement tab.
- Notes tab.
- Record Donation.
- Send Message.

### 5.7 Existing Donor Scoring

The screenshot shows the following score components:

| Component  | Displayed Weight |
| ---------- | ---------------- |
| Value      | 40%              |
| Recency    | 30%              |
| Frequency  | 30%              |
| Engagement | Extra            |

These weights are visible in the current interface but do not establish the complete scoring formula.

### 5.8 As-Is Donors Workflow

![As-Is Donors Workflow](screenshot%20goals/5.8%20As-Is%20Donors%20Workflow.png)

### 5.9 Existing Data Sources

![Existing Data Sources](screenshot%20goals/5.9%20Existing%20Data%20Sources.png)

The precise integration mappings, synchronisation frequency and duplicate rules have not been confirmed.

## 6. To-Be – Standalone Application State

### 6.1 Standalone Business Objective

The enhanced Donors capability must support different organisations through a common product foundation, while allowing tenant-specific configurations and multiple approved donation-data sources.

### 6.2 Target Donors Operating Model

![Target Donors Operating Model](screenshot%20goals/6.2%20Target%20Donors%20Operating%20Model.png)

An unresolved member identity must not result in an automatically created or incorrectly linked donor.

### 6.3 Target Capabilities

The standalone Donors capability shall support:

1. Isolated tenant donor records.
2. Existing role-based permissions.
3. Approved tenant-specific configurations.
4. Member-linked donor identification.
5. Manual donation recording.
6. Integrated donation records.
7. Excel/CSV bulk import.
8. File and row validation.
9. Duplicate donation detection.
10. Authorised conflict resolution.
11. Donor tier configuration.
12. Existing and additional KPI calculations.
13. KPI card drill-downs.
14. Configurable KPI selection.
15. Advanced filters.
16. Filtered exports.
17. Donor history and profile information.
18. Donor scoring and classification.
19. Data-source attribution.
20. Automatic KPI refresh after committed changes.
21. Relevant audit records.
22. Governed donor analysis and reporting.

## 7. Business Goals and Objectives

### 7.1 Standalone Product Goals

| Goal ID    | Business Goal                      | Expected Outcome                                              |
| ---------- | ---------------------------------- | ------------------------------------------------------------- |
| DON-GO-001 | Multi-Tenant Donor Management      | Independent organisations operate in isolated workspaces      |
| DON-GO-002 | Reusable Donors Capability         | Common functionality can serve different organisations        |
| DON-GO-003 | Tenant-Specific Configuration      | Approved functionality and settings can vary by tenant        |
| DON-GO-004 | Centralised Giving Information     | Supported donation sources feed a consolidated view           |
| DON-GO-005 | Flexible Donation Data Acquisition | Integrations, manual entry and approved imports are supported |

### 7.2 Donor Identity Goals

| Goal ID    | Business Goal                        | Expected Outcome                                               |
| ---------- | ------------------------------------ | -------------------------------------------------------------- |
| DON-GO-006 | Consistent Member–Donor Relationship | Every donor is linked to an existing member                    |
| DON-GO-007 | Controlled Manual Donation Entry     | Authorised users can record donations directly                 |
| DON-GO-008 | Reliable Donation Records            | Giving data is associated with the correct member and campaign |
| DON-GO-009 | Duplicate Donation Prevention        | Repeated source transactions do not inflate giving history     |
| DON-GO-010 | Controlled Reconciliation            | Conflicting transaction changes require authorised review      |

### 7.3 Donor Classification Goals

| Goal ID    | Business Goal               | Expected Outcome                                                  |
| ---------- | --------------------------- | ----------------------------------------------------------------- |
| DON-GO-011 | Configurable Donor Tiers    | Organisations define approved tier thresholds                     |
| DON-GO-012 | Consistent Tier Calculation | Donors are classified using the tenant's approved rules           |
| DON-GO-013 | Governed Donor Scoring      | Existing scores remain understandable and consistently calculated |

### 7.4 KPI and Reporting Goals

| Goal ID    | Business Goal              | Expected Outcome                                             |
| ---------- | -------------------------- | ------------------------------------------------------------ |
| DON-GO-014 | Preserve Existing KPIs     | Existing KPI calculations remain functional                  |
| DON-GO-015 | Interactive KPI Drill-Down | Users can inspect records supporting KPI results             |
| DON-GO-016 | Configurable KPI Selection | Users select approved available measures                     |
| DON-GO-017 | Advanced Donor Filtering   | Users can investigate relevant donor subsets                 |
| DON-GO-018 | Filtered Donor Export      | Authorised exports reflect applied criteria                  |
| DON-GO-019 | Enhanced Visualisation     | Organisations can analyse donor information more effectively |

### 7.5 Governance and Data Goals

| Goal ID    | Business Goal                    | Expected Outcome                                              |
| ---------- | -------------------------------- | ------------------------------------------------------------- |
| DON-GO-020 | Structured Donor Data Import     | Historical giving data can be imported through templates      |
| DON-GO-021 | Import Validation and Correction | Invalid or incomplete data is identified and corrected        |
| DON-GO-022 | Automatic KPI Synchronisation    | Committed changes automatically update affected KPIs          |
| DON-GO-023 | Donor Source Attribution         | Originating applications and data sources can be investigated |
| DON-GO-024 | Existing Permission Reuse        | Existing authorisation governs Donors functionality           |
| DON-GO-025 | Operational Auditability         | Material donor operations remain traceable                    |
| DON-GO-026 | Reliable Profile Consistency     | Profiles, tiers, giving summaries and KPIs remain aligned     |

## 8. As-Is vs To-Be Comparison

| Capability           | As-Is                          | To-Be                                     |
| -------------------- | ------------------------------ | ----------------------------------------- |
| Donor List           | Available                      | Retain and enhance                        |
| Donor KPIs           | Four existing metrics          | Clickable and configurable                |
| Tier Classification  | Four fixed visible categories  | Organisation-configurable thresholds      |
| Search               | Available                      | Enhanced filtering                        |
| Advanced Filters     | Existing controls              | Additional criteria                       |
| CSV Export           | Available                      | Filtered and controlled                   |
| Add Donor            | Available                      | Stronger validation and identity controls |
| Member Selection     | Available                      | Reliable member association               |
| Donor Profile        | Available                      | Enhanced quality and source information   |
| Donation History     | Available                      | Improved reconciliation                   |
| Donor Scoring        | Existing score display         | Governed calculations                     |
| Integrations         | Existing                       | Tenant-specific supported integrations    |
| Manual Donations     | Available                      | Retain                                    |
| Bulk Import          | Not established                | Excel/CSV import                          |
| Import Validation    | Not established                | File and row validation                   |
| Duplicate Detection  | Not established                | Controlled duplicate checking             |
| Tenant Configuration | Client-specific implementation | Configurable standalone product           |
| Role Permissions     | Existing                       | Reuse and extend                          |
| Automatic KPI Update | Existing calculation framework | Update after successful committed changes |
| Audit                | Existing extent to verify      | Governed material operations              |

## 9. Member–Donor Business Relationship

### 9.1 Confirmed Relationship

The relationship between Members and Donors is a fundamental business rule.

| Scenario                                   | Member | Donor                                            |
| ------------------------------------------ | ------ | ------------------------------------------------ |
| Registered person without donation         | Yes    | No                                               |
| Registered person with qualifying donation | Yes    | Yes                                              |
| Registered person with pledge only         | Yes    | Depends on qualifying donation, not pledge alone |
| Previously donated member                  | Yes    | Yes, where qualifying donation remains valid     |

The interface's Prospects KPI and Major Prospects filter must remain supported. However, prospect visibility must not automatically imply that a prospect has a qualifying donation.

### 9.2 Relationship Diagram

![Relationship Diagram](screenshot%20goals/9.2%20Relationship%20Diagram.png)

## 10. Stakeholders and Actors

| Actor                        | Business Responsibility                           |
| ---------------------------- | ------------------------------------------------- |
| Platform Product Owner       | Governs common and optional product capabilities  |
| Tenant Administrator         | Configures permitted organisational settings      |
| Fundraising Administrator    | Reviews donor activity and classifications        |
| Donation Operator            | Records donations against existing members        |
| Members Administrator        | Maintains authoritative member identity           |
| Import Operator              | Uploads and reviews giving datasets               |
| Reconciliation Administrator | Resolves duplicate and conflicting records        |
| Reporting User               | Reviews donor KPIs, filters and exports           |
| External Integration         | Provides information from approved source systems |
| Campaigns Capability         | Supplies campaign references                      |
| Audit / Compliance User      | Reviews authorised operational evidence           |

These functional actors must be mapped to the application's existing permission model.

## 11. Business Rules

### 11.1 Tenant and Access Rules

| Rule ID    | Business Rule                                                                                    |
| ---------- | ------------------------------------------------------------------------------------------------ |
| DON-BR-001 | Every client must have an isolated tenant/workspace                                              |
| DON-BR-002 | Approved optional functionality and configurations may differ between tenants                    |
| DON-BR-003 | Existing role-based permissions must be reused                                                   |
| DON-BR-004 | New import, reconciliation, configuration and export actions must enforce applicable permissions |
| DON-BR-005 | Cross-tenant donor information must not be exposed                                               |

### 11.2 Donor Identity and Donation Rules

| Rule ID    | Business Rule                                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------------------------- |
| DON-BR-006 | Every donor must be associated with an existing member                                                                 |
| DON-BR-007 | Not every member is a donor                                                                                            |
| DON-BR-008 | Donor identity must reuse the corresponding member identity                                                            |
| DON-BR-009 | Add Donor must support member lookup by name, email or phone                                                           |
| DON-BR-010 | Select Member, Donation Amount, Campaign, Payment Method and Donation Date are required in the existing Add Donor form |
| DON-BR-011 | Notes is optional                                                                                                      |
| DON-BR-012 | Campaign options must originate from available Campaigns data                                                          |
| DON-BR-013 | Cross-tenant donation associations are prohibited                                                                      |
| DON-BR-014 | Potential duplicate donations must be identified before committing a duplicate qualifying transaction                  |
| DON-BR-015 | Conflicting transaction changes require authorised review                                                              |

### 11.3 Donor List and Profile Rules

| Rule ID    | Business Rule                                                                  |
| ---------- | ------------------------------------------------------------------------------ |
| DON-BR-016 | Donors tier selection defaults to All                                          |
| DON-BR-017 | Existing tier categories are Platinum, Gold, Silver and Bronze                 |
| DON-BR-018 | Clicking a donor row or its three-dot action opens the same donor detail view  |
| DON-BR-019 | Donor profiles retain Overview, History, Engagement and Notes tabs             |
| DON-BR-020 | Donor profiles retain Lifetime Giving, Last Gift and Total Gifts               |
| DON-BR-021 | Existing score display includes Value, Recency, Frequency and Engagement       |
| DON-BR-022 | Approved tier thresholds and calculation rules must be configurable per tenant |
| DON-BR-023 | Donor classification and scoring must use governed data and calculation rules  |

### 11.4 KPI and Reporting Rules

| Rule ID    | Business Rule                                                                                 |
| ---------- | --------------------------------------------------------------------------------------------- |
| DON-BR-024 | Existing donor KPI calculations must be retained                                              |
| DON-BR-025 | Additional KPIs must follow the established KPI calculation approach                          |
| DON-BR-026 | KPI cards must support relevant record drill-downs or supporting analytical breakdowns        |
| DON-BR-027 | Users must be able to select permitted KPI cards                                              |
| DON-BR-028 | Existing and approved additional filters must be supported                                    |
| DON-BR-029 | Filtered exports must respect permissions and tenant boundaries                               |
| DON-BR-030 | Successfully committed imports and applicable updates must automatically update affected KPIs |
| DON-BR-031 | Rejected or unresolved transactions must not inflate giving figures                           |

### 11.5 Data Governance Rules

| Rule ID    | Business Rule                                                                                  |
| ---------- | ---------------------------------------------------------------------------------------------- |
| DON-BR-032 | Existing external integrations and manual donation entry must remain supported                 |
| DON-BR-033 | Approved Excel/CSV bulk imports must be supported                                              |
| DON-BR-034 | Imported records must undergo relevant validation                                              |
| DON-BR-035 | Potential identity matches and transaction duplicates must follow governed resolution rules    |
| DON-BR-036 | Import results must distinguish successful, rejected and pending-review records                |
| DON-BR-037 | Authorised administrators must be able to correct relevant imported data                       |
| DON-BR-038 | Material transaction changes and reconciliation decisions must be traceable                    |
| DON-BR-039 | Donors must remain consistent with Members Administrative Status and Giving Status definitions |
| DON-BR-040 | An editable Giving Status value alone must not establish a qualifying donation transaction     |

## 12. Donation Data Lifecycle

### 12.1 Target Donation Lifecycle

![Target Donation Lifecycle](screenshot%20goals/12.1%20Target%20Donation%20Lifecycle.png)

### 12.2 Transaction Status Considerations

The standalone solution must distinguish donation-record creation from successful payment completion.

The treatment of pending payments, completed donations, failed payments, reversals and refunds requires confirmation.

Only records eligible under the approved financial rules must contribute to giving KPIs and donor classification.

## 13. Donor Tier Configuration

### 13.1 Existing Categories

| Category | As-Is     |
| -------- | --------- |
| Platinum | Available |
| Gold     | Available |
| Silver   | Available |
| Bronze   | Available |

The current tier thresholds have not been supplied.

### 13.2 To-Be Tier Requirements

Authorised tenant settings should support:

- Tier definitions and labels.
- Minimum and maximum qualifying amounts.
- Currency.
- Eligible reporting period.
- Eligible donation statuses.
- Threshold inclusivity.
- Recalculation following giving changes.
- Handling of overlapping or missing tier ranges.

### 13.3 Tier Classification

![Tier Classification](screenshot%20goals/13.3%20Tier%20Classification.png)

Illustrative amount thresholds previously discussed must not be treated as approved values.

## 14. Donor Scoring Requirements

The existing profile presents Value, Recency, Frequency and Engagement scoring information.

The standalone capability must retain existing scoring while making its business definitions clear and consistent.

### 14.1 Required Outcomes

> Source flowchart unavailable; the requirements below define the outcomes for this section.


1. Preserve existing scoring behaviour.
2. Document actual calculation inputs and formulas.
3. Retain authorised score visibility.
4. Use consistent score values across profile and filters.
5. Recalculate scores after qualifying data changes.
6. Permit tenant-specific scoring configuration only where approved.


## 15. KPI and Reporting Objectives

### 15.1 Existing KPIs

| KPI            | Requirement                   |
| -------------- | ----------------------------- |
| Total Donors   | Preserve existing calculation |
| Active Pledges | Preserve existing calculation |
| Retention Rate | Preserve existing calculation |
| Prospects      | Preserve existing calculation |

### 15.2 Recommended Additional KPIs

| KPI                        | Purpose                                             |
| -------------------------- | --------------------------------------------------- |
| Total Giving               | Aggregate qualifying donation value                 |
| New Donors                 | Identify newly qualifying donors                    |
| Repeat Donors              | Identify multiple-gift donors                       |
| Average Gift Amount        | Analyse typical gift value                          |
| Largest Gift               | Identify highest qualifying donation                |
| Donors by Tier             | Analyse recognition distribution                    |
| Donors by Campaign         | Review campaign-linked donors                       |
| Donors by Location         | Geographic fundraising analysis                     |
| Donors by Source           | Source contribution analysis                        |
| Lapsed Donors              | Review previously active contributors               |
| Monthly Donors             | Analyse recurring giving behaviour                  |
| Member-to-Donor Conversion | Review conversion of eligible members               |
| Giving Trend               | Analyse contributions across periods                |
| Pending Reconciliation     | Identify unresolved donation conflicts              |
| Pledge Fulfilment          | Compare fulfilled giving against qualifying pledges |

All additional KPIs require approved definitions and data sources.

### 15.3 KPI Interaction

![KPI Interaction](screenshot%20goals/15.3%20KPI%20Interaction.png)

### 15.4 Automatic KPI Updates

Successful manual recordings, imports, integrations and approved transaction updates must trigger recalculation of affected KPIs.

The system must not count rejected or unresolved transactions as successfully committed giving.

## 16. Search, Filtering and Export

### 16.1 Existing Filtering

The Donors page currently supports tier, donation amount, score and engagement-segment filters.

### 16.2 Proposed Additional Filters

| Filter                | Purpose                               |
| --------------------- | ------------------------------------- |
| Member Type           | Filter constituent category           |
| Administrative Status | Active / Inactive member records      |
| Giving Status         | Prospect / Pledged / Donated / Lapsed |
| Donation Date         | Select giving period                  |
| Campaign              | Campaign-linked donations             |
| Payment Method        | Analyse recorded method               |
| Donation Source       | Manual, Import or Integration         |
| Location              | City, State or Country                |
| Last Gift Date        | Review giving recency                 |
| Total Giving Range    | Select giving-value population        |
| Pledge Status         | Review pledge-related records         |

### 16.3 Filtered Export Requirements

The To-Be export must:

- Use the applicable donor search and filters.
- Export the authorised matching dataset.
- Exclude unrelated tenant records.
- Respect existing and extended permissions.
- Preserve meaningful data formatting.
- Record material export activity where required.

## 17. Bulk Import Business Objectives

### 17.1 Import Purpose

Enable organisations to upload historical donor and donation information through approved Excel/CSV templates.

### 17.2 Import Requirements

The import capability must support:

- Approved templates.
- Required-field checks.
- Existing-member identification.
- Transaction duplicate detection.
- Error reporting.
- Preview and confirmation.
- Authorised corrections.
- Clear import result counts.
- Automatic KPI updates.

### 17.3 Import Workflow

![Import Workflow](screenshot%20goals/17.3%20Import%20Workflow.png)

An import containing multiple donations by the same member must preserve the distinct donation records without creating multiple donor identities.

## 18. Donor Profile Objectives

### 18.1 Existing Functionality

Retain:

- Donor information.
- Lifetime Giving.
- Last Gift.
- Total Gifts.
- Tier.
- Donor Score.
- Overview.
- History.
- Engagement.
- Notes.
- Record Donation.
- Send Message.

### 18.2 Proposed Enhancements

| Enhancement           | Business Value                  |
| --------------------- | ------------------------------- |
| Donation Source       | Understand record origin        |
| Latest Updated        | Review information freshness    |
| Reconciliation Status | Identify data conflicts         |
| Tier Explanation      | Understand classification       |
| Score Explanation     | Understand scoring factors      |
| Reporting Period      | Review relevant giving history  |
| Data Completeness     | Identify incomplete information |

The existing Send Message action must be preserved. Its detailed execution is governed by its associated communication functionality.

## 19. Tenant Configuration

The standalone application must permit approved organisational configurations.

| Configuration Area    | Purpose                                 |
| --------------------- | --------------------------------------- |
| Optional Features     | Tenant-specific entitled capabilities   |
| Donor Tier Rules      | Recognition thresholds                  |
| KPI Selection         | Relevant dashboard measures             |
| Filter Availability   | Approved organisation-specific criteria |
| Reporting Period      | Period selection                        |
| Import Templates      | Approved formats and fields             |
| Payment Methods       | Applicable donation methods             |
| Scoring Configuration | Approved calculation options            |
| Role Permissions      | Existing permission framework           |

Tenant configuration must never bypass mandatory security requirements.

## 20. Data Governance and Ownership

| Data Category          | Proposed Authority             |
| ---------------------- | ------------------------------ |
| Member Identity        | Members                        |
| Donor Relationship     | Donor Management               |
| Donation Transactions  | Donations capability           |
| Campaign Reference     | Campaigns                      |
| Tier Configuration     | Tenant Configuration           |
| KPI Calculations       | Reporting / KPI capability     |
| Scoring Definitions    | Product / Reporting Governance |
| Import History         | Import/Data Management         |
| Integration References | Integration/Data Management    |
| Permissions            | Existing Identity and Access   |
| Audit Records          | Audit capability               |

Final ownership must be aligned with the actual application implementation.

## 21. Security and Privacy

![Security and Privacy](screenshot%20goals/21.%20Security%20and%20Privacy.png)

The Donors capability must:

1. Enforce tenant isolation.
2. Reuse existing permissions.
3. Authorise donation recording.
4. Validate import and export access.
5. Prevent cross-tenant member selection.
6. Protect sensitive member and donation information.
7. Prevent unauthorised changes to financial records.
8. Maintain auditability.
9. Preserve authoritative records after failed operations.
10. Respect relevant member communication preferences.


## 22. Business Dependencies

| Dependency            | Business Requirement                   |
| --------------------- | -------------------------------------- |
| Members               | Existing member identity               |
| Campaigns             | Valid campaign reference               |
| Donations             | Donation records and status            |
| Payment Configuration | Supported payment methods              |
| Tenant Management     | Organisation isolation                 |
| Authentication        | Existing identity verification         |
| Permissions           | Existing authorisation                 |
| Integrations          | Supported external data                |
| Import Processing     | Template validation and reconciliation |
| KPI / Reporting       | Calculation and analytics              |
| Export                | Authorised data extraction             |
| Audit                 | Activity traceability                  |
| Communications        | Existing Send Message action           |
| Global Search         | Shared cross-module search             |
| AI Copilot            | Shared application entry point         |

## 23. Assumptions and Constraints

### 23.1 Confirmed Requirements

- AiXPurpose is an existing application.
- Standalone functionality must support independent organisations.
- Tenant data must remain isolated.
- Existing role permissions must be reused.
- Approved optional capabilities may differ by tenant.
- Every donor must be an existing member.
- Manual donation entry and integrations must remain.
- Excel/CSV bulk import must be supported.
- Existing donor KPIs must be preserved.
- Additional KPIs and KPI drill-downs are required.
- Donor-tier thresholds must support organisational configuration.
- Existing advanced filters must remain.
- Filtered exports must be supported.
- Successfully committed imports must update affected KPI values.

### 23.2 Decisions Requiring Approval

- Qualifying donation statuses.
- Exact transaction duplicate identifiers.
- Import matching and update policies.
- Payment completion and recording semantics.
- Tier measurement periods and currency.
- Scoring formula documentation.
- Additional KPI definitions.
- Donor history correction rules.
- Import size and partial-success policies.
- Detailed optional-feature entitlements.

## 24. Scope and Capability Boundaries

This document covers business requirements associated with the Donors page, its existing interface and approved standalone enhancements.

Related capabilities, including Members, Campaigns, Segments, Prospecting, Communications, Donations and Reporting, remain part of AiXPurpose.

Their independent functional specifications are maintained in their respective documentation.

## 25. Business Risks and Mitigations

| Risk                         | Impact                          | Mitigation                       |
| ---------------------------- | ------------------------------- | -------------------------------- |
| Incorrect Member Association | Donation linked to wrong member | Identity validation              |
| Duplicate Donations          | Inflated giving figures         | Transaction duplicate checking   |
| Incorrect Tier Thresholds    | Misclassified donors            | Approved tenant configuration    |
| Stale KPIs                   | Misleading reporting            | Automatic KPI recalculation      |
| Invalid Imports              | Inaccurate information          | File and row validation          |
| Integration Conflicts        | Data inconsistency              | Authorised reconciliation        |
| Cross-Tenant Access          | Data exposure                   | Tenant-scoped authorisation      |
| Unclear Transaction Status   | Incorrect giving totals         | Approved financial status rules  |
| Uncontrolled Export          | Information exposure            | Permission-controlled filtering  |
| Scoring Inconsistency        | Misleading donor insights       | Governed calculation definitions |

## 26. Business Success Criteria

| ID         | Expected Outcome                                                                |
| ---------- | ------------------------------------------------------------------------------- |
| DON-SC-001 | Organisations operate within isolated Donors workspaces                         |
| DON-SC-002 | Existing donor-management functionality is preserved                            |
| DON-SC-003 | Every donor is linked to an existing member                                     |
| DON-SC-004 | Members without qualifying donations are not automatically classified as donors |
| DON-SC-005 | Manual donation entry remains available                                         |
| DON-SC-006 | Supported integrated donation records are consolidated                          |
| DON-SC-007 | Approved Excel/CSV files can be imported                                        |
| DON-SC-008 | Invalid and duplicate records are identified                                    |
| DON-SC-009 | Conflicting records require authorised review                                   |
| DON-SC-010 | Donor tiers follow approved tenant rules                                        |
| DON-SC-011 | Existing KPI calculations remain operational                                    |
| DON-SC-012 | Additional KPIs follow approved formulas                                        |
| DON-SC-013 | KPI selections support relevant drill-downs                                     |
| DON-SC-014 | Advanced filtering and filtered export function consistently                    |
| DON-SC-015 | Donor profile and giving history remain consistent                              |
| DON-SC-016 | Successfully committed imports update KPIs automatically                        |
| DON-SC-017 | Existing permissions govern new actions                                         |
| DON-SC-018 | Material donor operations remain auditable                                      |

No unapproved numerical fundraising or performance targets are assumed.

## 27. Open Business Decisions

| ID         | Decision                                                                      |
| ---------- | ----------------------------------------------------------------------------- |
| DON-OD-001 | Which donation statuses qualify for donor recognition and giving totals?      |
| DON-OD-002 | How are prospect-only records represented in the Donors list and KPI counts?  |
| DON-OD-003 | Does Save Donation record an existing payment or initiate payment processing? |
| DON-OD-004 | Which payment methods and transaction statuses are supported?                 |
| DON-OD-005 | Which identifiers determine duplicate donation transactions?                  |
| DON-OD-006 | What are the approved donor import template fields and file limits?           |
| DON-OD-007 | How are unmatched donor imports resolved against Members?                     |
| DON-OD-008 | What are the approved tier thresholds and measurement rules?                  |
| DON-OD-009 | What are the existing and new KPI definitions?                                |
| DON-OD-010 | What is the documented donor scoring algorithm?                               |
| DON-OD-011 | How are KPI, search and advanced filters combined?                            |
| DON-OD-012 | What are the final export columns and selection rules?                        |
| DON-OD-013 | What are the existing tab and Send Message action behaviours?                 |
| DON-OD-014 | How are refunds, reversals and historical corrections handled?                |
| DON-OD-015 | How are integration conflicts and source priorities resolved?                 |
| DON-OD-016 | What currency and conversion rules apply to multi-currency giving?            |
| DON-OD-017 | What optional feature configurations are approved?                            |
| DON-OD-018 | What audit visibility and retention policies apply?                           |

## 28. Goals-to-Workflow Traceability

| Goals          | Workflow Coverage                             |
| -------------- | --------------------------------------------- |
| DON-GO-001–003 | Tenant access and configuration               |
| DON-GO-004–005 | Multi-source giving information               |
| DON-GO-006     | Member–Donor identity relationship            |
| DON-GO-007–008 | Add Donor and donation validation             |
| DON-GO-009–010 | Duplicate checking and reconciliation         |
| DON-GO-011–012 | Donor tier configuration and calculation      |
| DON-GO-013     | Donor scoring                                 |
| DON-GO-014–016 | KPI calculation, configuration and drill-down |
| DON-GO-017–019 | Search, filtering, export and visualisation   |
| DON-GO-020–021 | Bulk import and correction                    |
| DON-GO-022     | Automatic KPI updates                         |
| DON-GO-023     | Data-source identification                    |
| DON-GO-024     | Existing permission reuse                     |
| DON-GO-025     | Audit and exception handling                  |
| DON-GO-026     | Donor profile consistency                     |

### 28.1 Traceability Model

![Traceability Model](screenshot%20goals/28.1%20Traceability%20Model.png)

## 29. Relationship to BRD Workflow

The Donors Workflow must expand the business requirements into operational processes covering:

- Donors overview and tenant access.
- Search, tier and advanced filtering.
- Member lookup and Add Donor.
- Donation validation and saving.
- Donation identity and duplicate checks.
- External-source ingestion.
- Bulk import and reconciliation.
- Donor profile and history.
- Tier configuration and calculation.
- Donor scoring.
- KPI selection and drill-down.
- Filtered export.
- Automatic KPI updates.
- Authorisation and audit handling.
- Relevant dependencies with Members, Campaigns and Communications.

Each workflow must distinguish existing behaviour from standalone enhancements.

## 30. Relationship to Feature Catalogue

The Donors Feature Catalogue must convert workflows into individually testable functional features.

Each feature must include:

- Unique Feature ID.
- Feature name.
- As-Is or To-Be classification.
- Related business goals.
- Related workflows.
- Business rules.
- Functional behaviour.
- Required inputs.
- Validation requirements.
- Processing outcomes.
- Error conditions.
- Permission requirements.
- Acceptance criteria.
- Related dependencies.

Unapproved scoring formulas, tier thresholds and payment-status behaviour must not be invented.

## 31. Product Validation Summary

| Review Area                  | Result                              |
| ---------------------------- | ----------------------------------- |
| Existing Functionality       | Preserved                           |
| Standalone Product Objective | Included                            |
| Multi-Tenancy                | Included                            |
| Optional Tenant Capabilities | Included                            |
| Existing Permissions         | Reused                              |
| Member–Donor Relationship    | Confirmed and incorporated          |
| Manual Donation Entry        | Retained                            |
| Integration Support          | Retained                            |
| Bulk Import                  | Included                            |
| Duplicate Prevention         | Included                            |
| Tier Configuration           | Included                            |
| Existing KPIs                | Preserved                           |
| Additional KPIs              | Proposed and structured             |
| KPI Drill-Down               | Included                            |
| Automatic KPI Updates        | Included                            |
| Advanced Filtering           | Included                            |
| Filtered Export              | Included                            |
| Donor Scoring                | Preserved without invented formulas |
| Donor Profiles               | Retained                            |
| Audit and Governance         | Included                            |
| Business Goals               | 26                                  |
| Business Rules               | 40                                  |
| Success Criteria             | 18                                  |
| Open Decisions               | 18                                  |

## 32. Document Conclusion

The standalone AiXPurpose Donors capability must extend the existing client-specific donation-management solution into a secure, configurable and reusable capability for independent organisations.

It must preserve existing donor lists, giving profiles, donation entry, donor tiers, scoring, filtering and KPI calculations while introducing structured imports, controlled reconciliation, configurable business insights, filtered exports and automatic KPI updates.

The fundamental business relationship remains:

Every donor must be an existing member, but not every member is required to be a donor.

The Donors BRD Goals provides the baseline for the Donors Workflow and Feature Catalogue, ensuring that detailed functionality remains aligned with the agreed standalone AiXPurpose requirements.
