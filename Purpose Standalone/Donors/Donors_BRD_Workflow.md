# AiXPurpose – Donor Management – Donors

> **Document type:** Business Requirements Document – Workflow

## Document Control

| Field                     | Details                                                                                   |
| ------------------------- | ----------------------------------------------------------------------------------------- |
| Document Name             | AiXPurpose – Donors – BRD Workflow                                                        |
| Product                   | AiXPurpose                                                                                |
| Application Type          | Standalone, Multi-Tenant Application                                                      |
| Module                    | Donor Management                                                                          |
| Page                      | Donors                                                                                    |
| Document Type             | Business Requirements Document – Workflow                                                 |
| Version                   | 1.0                                                                                       |
| Status                    | Draft for Business Review                                                                 |
| Related Goals             | AiXPurpose – Donors – BRD Goals v1.0                                                      |
| Related Feature Catalogue | AiXPurpose – Donors – Feature Catalogue                                                   |
| Related Module Reference  | AiXPurpose – Members                                                                      |
| Workflow ID Convention    | DON-WF-##                                                                                 |
| Requirement Source        | Existing Donors application, screenshots, walkthrough and confirmed business requirements |

## Overview

This document describes the end-to-end workflows for the Donors capability, distinguishing current-state (As-Is) behaviour from target-state (To-Be) requirements.

## Contents

- [1. Document Purpose](#1-document-purpose)
- [2. Business Workflow Principles](#2-business-workflow-principles)
- [3. End-to-End Donors Workflow](#3-end-to-end-donors-workflow)
- [4. Workflow Inventory](#4-workflow-inventory)
- [5. Detailed Donors Workflows](#5-detailed-donors-workflows)
- [6. Shared Validation Rules](#6-shared-validation-rules)
- [7. Donor Import Outcome Rules](#7-donor-import-outcome-rules)
- [8. Data Consistency Requirements](#8-data-consistency-requirements)
- [9. Screenshot Reference Mapping](#9-screenshot-reference-mapping)
- [10. Goals-to-Workflow Traceability](#10-goals-to-workflow-traceability)
- [11. Feature Catalogue Handoff](#11-feature-catalogue-handoff)
- [12. Open Decisions and Clarifications](#12-open-decisions-and-clarifications)
- [13. Workflow Validation Summary](#13-workflow-validation-summary)
- [14. Document Conclusion](#14-document-conclusion)

## 1. Document Purpose

This document defines the end-to-end business workflows for the Donors page within AiXPurpose Donor Management.

It translates the 26 business goals and 40 business rules established in the Donors BRD Goals into functional processes covering existing application behaviour and standalone enhancements.

The document addresses:

- Donors overview and navigation.
- Member-linked donation creation.
- Donor search, tiers and advanced filters.
- Donor profile and giving history.
- External donation integrations.
- Excel/CSV bulk import.
- Duplicate detection and reconciliation.
- Configurable donor tiers and scoring.
- KPI configuration and drill-down.
- Filtered exports and automatic KPI updates.
- Tenant configuration, existing permissions and audit handling.

As-Is identifies existing application functionality. To-Be identifies required standalone enhancements. Proposed functionality and unresolved business-policy details are distinguished where applicable.

Detailed field validations, calculations, APIs and feature-level acceptance criteria belong in the Donors Feature Catalogue.

## 2. Business Workflow Principles

The following principles apply throughout Donors workflows.

| Principle                 | Confirmed Requirement                                                     |
| ------------------------- | ------------------------------------------------------------------------- |
| Tenant Isolation          | Every organisation operates within its own tenant                         |
| Existing Permissions      | Reuse the existing role-based permission framework                        |
| Configurability           | Approved optional capabilities and settings may differ by tenant          |
| Member–Donor Relationship | Every donor must be an existing member                                    |
| Member Independence       | Not every member must be a donor                                          |
| Donor Qualification       | Requires a qualifying recorded donation                                   |
| Data Sources              | Manual entry, external integrations and Excel/CSV imports                 |
| Duplicate Handling        | Conflicting identity and transaction records require administrator review |
| KPI Calculations          | Retain existing formulas and extend for approved KPIs                     |
| KPI Updates               | Automatically update affected values after successful committed changes   |
| Donor Tiers               | Retain existing categories; configure approved thresholds per tenant      |
| Data Governance           | Preserve authoritative giving records and material audit evidence         |

### 2.1 Workflow Actors

| Actor                        | Responsibility                                                        |
| ---------------------------- | --------------------------------------------------------------------- |
| Authorised User              | View donors, search, filter and inspect records                       |
| Donation Operator            | Record donations for existing members                                 |
| Fundraising Administrator    | Manage approved donor-related operations                              |
| Tenant Administrator         | Configure available donor settings                                    |
| Import Operator              | Upload and review donation files                                      |
| Reconciliation Administrator | Resolve duplicate or conflicting records                              |
| External Integration         | Supply donor and donation information                                 |
| AiXPurpose                   | Apply approved validation, identity, calculation and permission rules |

These are functional actors mapped to existing permissions, not newly mandated system roles.

## 3. End-to-End Donors Workflow

### 3.1 Existing Application – As-Is

![Existing Application – As-Is](screenshot%20goals/5.8%20As-Is%20Donors%20Workflow.png)

### 3.2 Standalone Application – To-Be

![Standalone Application – To-Be](screenshot%20goals/6.2%20Target%20Donors%20Operating%20Model.png)

Important: This is the target process. The exact payment completion statuses, transaction-matching identifiers and recalculation policies must follow approved business definitions.

## 4. Workflow Inventory

| Workflow ID | Workflow Name                           | Classification           |
| ----------- | --------------------------------------- | ------------------------ |
| DON-WF-01   | Access Donors Overview                  | As-Is + Enhance          |
| DON-WF-02   | Search and Filter Donors                | As-Is + Enhance          |
| DON-WF-03   | Advanced Donor Filtering                | As-Is + Enhance          |
| DON-WF-04   | View Donor Profile                      | As-Is + Enhance          |
| DON-WF-05   | Add Donor / Record Donation             | As-Is + Enhance          |
| DON-WF-06   | Resolve Member–Donor Relationship       | Confirmed Rule + Enhance |
| DON-WF-07   | Receive Integrated Donations            | As-Is + Enhance          |
| DON-WF-08   | Bulk Import Donor Data                  | To-Be                    |
| DON-WF-09   | Validate Imported Records               | To-Be                    |
| DON-WF-10   | Detect and Resolve Duplicates           | To-Be                    |
| DON-WF-11   | Donor Tier Configuration                | To-Be                    |
| DON-WF-12   | Calculate and Assign Donor Tiers        | As-Is + Enhance          |
| DON-WF-13   | Calculate and Display Donor Scores      | As-Is + Enhance          |
| DON-WF-14   | Display and Configure KPIs              | As-Is + Enhance          |
| DON-WF-15   | KPI Drill-Down                          | To-Be                    |
| DON-WF-16   | Export Donor Records                    | As-Is + Enhance          |
| DON-WF-17   | Refresh Donors and KPIs                 | To-Be                    |
| DON-WF-18   | Review Donation History                 | As-Is + Enhance          |
| DON-WF-19   | Donor Profile Actions                   | As-Is                    |
| DON-WF-20   | Tenant Configuration and Permissions    | As-Is + Enhance          |
| DON-WF-21   | Donation Corrections and Reconciliation | To-Be                    |
| DON-WF-22   | Audit and Exception Handling            | To-Be Governance         |

## 5. Detailed Donors Workflows

### DON-WF-01 – Access Donors Overview

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-001, 002, 014, 024 Rules: DON-BR-001–005, 016, 024 Actor: Authorised user.

As-Is:

1. User navigates to Donor Management → Donors.
2. System displays the four existing KPI cards.
3. Donors list loads with All as the default tier filter.
4. User can access search, Advanced Filters, Export CSV and Add Donor.
5. Shared application header remains available.

To-Be:

1. Resolve tenant and existing user permissions.
2. Load only authorised tenant donor information.
3. Display permitted and configured KPIs.
4. Apply the default tier selection.
5. Display permitted actions based on tenant settings.


Exceptions: Unauthorised access is denied. Where no eligible records exist, display an empty-state message.

### DON-WF-02 – Search and Filter Donors

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-017 Rules: DON-BR-016–018, 028 Actor: Authorised user.

As-Is:

1. Open Donors.
2. Enter donor-related search text.
3. Select All, Platinum, Gold, Silver or Bronze.
4. Review matching donor records.

To-Be:

- Preserve search and tier filtering.
- Apply approved search and filter combinations.
- Use the tenant's configured tier criteria.
- Maintain permitted filtering during list navigation.


Acceptance outcome: Only records matching the authorised criteria are displayed.

### DON-WF-03 – Advanced Donor Filtering

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-017, 018 Rules: DON-BR-028, 029

As-Is: The existing Advanced Filters interface provides donation amount range, donor score range (0–100) and engagement segments.

Available segments are New Donors, Lapsing, Major Prospects and Monthly Donors.

To-Be: Retain these controls and support additional approved filters such as campaign, donation source, payment method, location, giving status and donation period.


Exception: Invalid ranges must not produce misleading results. Filter availability depends on approved settings and data.

### DON-WF-04 – View Donor Profile

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-026, 013 Rules: DON-BR-018–021

As-Is:

1. User clicks a donor row or its three-dot action.
2. Both open the same donor detail view.
3. System displays donor identity, type, tier, status and score.
4. System displays Lifetime Giving, Last Gift and Total Gifts.
5. User can navigate Overview, History, Engagement and Notes.

To-Be:

- Preserve existing profile functionality.
- Display separate member administrative and giving statuses where relevant.
- Include approved source attribution and reconciliation indicators.
- Keep giving summaries, tiers and scores consistent with committed data.


Exception: Records outside the user's tenant or access scope must not be displayed.

### DON-WF-05 – Add Donor / Record Donation

Goals: DON-GO-006–008 Rules: DON-BR-006–013 Actor: Authorised donation operator.

As-Is: Add Donor opens a donation-entry modal.

| Field           | Existing Requirement                     |
| --------------- | ---------------------------------------- |
| Select Member   | Required; search by name, email or phone |
| Donation Amount | Required                                 |
| Campaign        | Required; options sourced from Campaigns |
| Payment Method  | Required                                 |
| Donation Date   | Required                                 |
| Notes           | Optional                                 |
| Save Donation   | Submit action                            |
| Cancel          | Exit action                              |

To-Be:

1. Resolve the user's tenant and permission.
2. Select an existing member within the tenant.
3. Capture required donation details.
4. Validate the submission.
5. Check possible duplicate transactions.
6. Hold conflicting records for authorised review.
7. Commit the eligible donation according to the approved transaction-status policy.
8. Update applicable donor records and giving summaries.

![Add Donor / Record Donation](screenshot%20goals/12.1%20Target%20Donation%20Lifecycle.png)

Important: Save Donation must not be assumed to initiate payment processing. That behaviour remains an open business decision.

### DON-WF-06 – Resolve Member–Donor Relationship

Goals: DON-GO-006, 026 Rules: DON-BR-006–008, 039, 040

Confirmed business requirement: Every donor must be an existing member. Not every member is a donor.

To-Be Process:

1. Resolve an existing member identity.
2. Verify that the record belongs to the current tenant.
3. Confirm a qualifying recorded donation.
4. Establish or retain the corresponding donor relationship.
5. Preserve the original member identity.
6. Update applicable donor summaries.

![Resolve Member–Donor Relationship](screenshot%20goals/4.2%20Member%E2%80%93Donor%20Relationship.png)

Special consideration: Prospects can appear in existing Donors-related insights. Their display and counting rules must distinguish prospects from members with qualifying donations.

### DON-WF-07 – Receive Integrated Donations

Goals: DON-GO-004, 005, 023 Rules: DON-BR-032, 035

As-Is: AiXPurpose receives donor/giving information through supported external applications.

To-Be:

1. Receive donation information from an authorised tenant integration.
2. Validate tenant/source identity.
3. Map incoming fields.
4. Resolve the member.
5. Check transaction duplication and source conflicts.
6. Commit eligible changes.
7. Update donor profile, giving history and affected KPIs.

![Receive Integrated Donations](screenshot%20goals/5.9%20Existing%20Data%20Sources.png)

Exception: Failed integration operations must not overwrite previously committed records.

### DON-WF-08 – Bulk Import Donor Data

Goals: DON-GO-020, 021 Rules: DON-BR-033–037

Actor: Authorised import operator.

To-Be:

1. Open Import Donors/Donations.
2. Download the approved Excel/CSV template.
3. Populate the file using existing member references and donation information.
4. Upload the dataset.
5. Validate file structure and individual records.
6. Resolve member identity and duplicate transactions.
7. Preview import outcomes.
8. Confirm eligible records.
9. View processing results.
10. Automatically update affected donor KPIs after successful commits.

![Bulk Import Donor Data](screenshot%20goals/17.3%20Import%20Workflow.png)

Important: One imported donor may have several donation rows. Unique donor counts must not be confused with successfully imported transaction counts.

### DON-WF-09 – Validate Imported Records

Goals: DON-GO-020, 021 Rules: DON-BR-034–037

To-Be Validation:

| Validation Area | Required Behaviour                |
| --------------- | --------------------------------- |
| File            | Supported format and template     |
| Columns         | Required headers and fields       |
| Member          | Valid existing tenant member      |
| Amount          | Valid amount under approved rules |
| Campaign        | Valid campaign reference          |
| Payment Method  | Approved method                   |
| Donation Date   | Valid date                        |
| Duplicate       | Potential repeated transaction    |
| Tenant          | No cross-tenant references        |

Processing Outcomes: Created, Updated, Rejected, Pending Member Review, Pending Duplicate Review or Skipped, as applicable.

Exception: Invalid or unresolved rows must not be counted as successfully committed transactions.

### DON-WF-10 – Detect and Resolve Duplicates

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-009, 010 Rules: DON-BR-014, 015, 035

To-Be: Detect potential donation duplication across manual entry, integrated sources and bulk imports.


Business rule: Conflicting transactions must not be automatically merged or overwritten without authorised review.

### DON-WF-11 – Configure Donor Tiers

Goals: DON-GO-003, 011 Rules: DON-BR-017, 022, 023 Actor: Authorised tenant administrator.

As-Is: Platinum, Gold, Silver and Bronze categories are displayed. The existing tier-setting interface and calculation rules have not been verified.

To-Be:

1. Open authorised donor-tier configuration.
2. View available tier categories.
3. Define approved thresholds, currency and calculation period.
4. Validate overlapping or incomplete rules.
5. Save the configuration.
6. Recalculate affected donor classifications.

![Configure Donor Tiers](screenshot%20goals/13.3%20Tier%20Classification.png)

Open decision: Actual threshold values, reporting period, currency, boundary rules and treatment of reversed donations.

### DON-WF-12 – Calculate and Assign Donor Tiers

Goals: DON-GO-011, 012 Rules: DON-BR-017, 022, 023

As-Is: The application displays donor tiers using existing classifications.

To-Be:

1. Identify eligible donation information.
2. Calculate qualifying giving according to approved rules.
3. Retrieve the tenant's tier configuration.
4. Evaluate matching thresholds.
5. Assign the appropriate tier.
6. Update the donor profile and filtering information.

![Calculate and Assign Donor Tiers](screenshot%20goals/13.3%20Tier%20Classification.png)

Exception: Missing or invalid tier configuration must not produce an arbitrary classification.

### DON-WF-13 – Calculate and Display Donor Scores

Goals: DON-GO-013, 026 Rules: DON-BR-021, 023

As-Is: Donor profiles show Donor Score and the following components:

| Component  | Existing UI Display |
| ---------- | ------------------- |
| Value      | 40%                 |
| Recency    | 30%                 |
| Frequency  | 30%                 |
| Engagement | Extra               |

To-Be:

1. Retrieve available donor giving and engagement data.
2. Apply the existing scoring logic.
3. Apply approved tenant-specific settings where supported.
4. Recalculate affected scores after eligible record changes.
5. Display scores in the profile and associated filters.

Exception: Missing input data must be handled according to approved scoring rules. The displayed percentages do not establish the full algorithm.

### DON-WF-14 – Display and Configure KPIs

Goals: DON-GO-014, 016, 019 Rules: DON-BR-024, 025, 027

As-Is: Existing KPI cards are Total Donors, Active Pledges, Retention Rate and Prospects. Their calculation logic already exists.

To-Be:

1. Load existing and available additional KPIs.
2. Retrieve the user's permitted KPI configuration.
3. Display selected KPI cards.
4. Allow authorised KPI selection.
5. Calculate additional KPIs using approved definitions.
6. Save preferences under the approved user-level or tenant-level configuration model.

![Display and Configure KPIs](screenshot%20goals/15.3%20KPI%20Interaction.png)

Suggested additional KPIs: Total Giving, New Donors, Repeat Donors, Average Gift, Largest Gift, Donors by Tier, Monthly Donors, Giving Trend, Pledge Fulfilment and Member-to-Donor Conversion.

Their precise calculations require approval.

### DON-WF-15 – KPI Drill-Down

Goals: DON-GO-015 Rules: DON-BR-026

To-Be:

1. User selects a KPI.
2. System resolves its approved selection criteria.
3. System applies tenant and user permissions.
4. System displays the relevant donor records or analytical breakdown.
5. User may refine filters, inspect donor details or export permitted data.
6. User may clear the KPI selection.

![KPI Drill-Down](screenshot%20goals/15.3%20KPI%20Interaction.png)

Example: Total Donors can drill into qualifying donors. Retention Rate may require a period-specific cohort breakdown rather than a list whose count is expected to equal the displayed percentage.

### DON-WF-16 – Export Donor Records

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-018 Rules: DON-BR-029

As-Is: Export CSV is available.

To-Be:

1. User applies applicable search, tier, advanced or KPI filters.
2. User selects Export CSV.
3. System verifies existing export permissions.
4. System resolves the authorised matching dataset.
5. System generates the export file.
6. System records the material export activity.


Business rule: An export of the full filtered population must not be incorrectly restricted to the current visible page.

### DON-WF-17 – Refresh Donors and KPIs

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-022, 026 Rules: DON-BR-030, 031

To-Be: Relevant donor information and KPIs must automatically reflect successful committed changes.


Confirmed requirement: Successfully committed imports must automatically update affected KPI values without requiring manual recalculation.

Exception: Rejected, unresolved or uncommitted records must not inflate donor counts or giving totals.

### DON-WF-18 – Review Donation History

Goals: DON-GO-026 Rules: DON-BR-019, 020

As-Is: The donor profile provides a History tab and giving-summary cards.

To-Be:

1. Open the selected donor profile.
2. Navigate to History.
3. Retrieve authorised donation information associated with the member.
4. Display recorded history according to the application's approved transaction model.
5. Keep Lifetime Giving, Last Gift and Total Gifts consistent with qualifying records.
6. Display source or reconciliation information where approved.

![Review Donation History](screenshot%20goals/12.1%20Target%20Donation%20Lifecycle.png)

Exception: Missing, reversed or unresolved records must follow approved transaction eligibility rules rather than being silently counted.

### DON-WF-19 – Donor Profile Actions

Goals: DON-GO-007, 026 Rules: DON-BR-019

As-Is: The existing donor profile presents Record Donation, Add Task and Send Message actions.

| Action          | Workflow Behaviour                                               |
| --------------- | ---------------------------------------------------------------- |
| Record Donation | Initiates donation entry for an existing member                  |
| Add Task        | Opens the associated task capability, if enabled and authorised  |
| Send Message    | Uses the relevant existing messaging capability, where supported |
| Overview        | Displays donor details and scoring information                   |
| History         | Provides giving history                                          |
| Engagement      | Provides the existing engagement view                            |
| Notes           | Provides the existing notes view                                 |

To-Be: Retain these entry points and apply existing permissions and tenant boundaries.

The detailed execution of Tasks and Communications is defined by those related capabilities. The visibility of Send Message does not establish that campaign-wide outreach functionality is already implemented.

### DON-WF-20 – Tenant Configuration and Permissions

Goals: DON-GO-001–003, 024 Rules: DON-BR-001–005

As-Is: Role-based permissions already exist.

To-Be:

1. Resolve authorised tenant administrator access.
2. Display available Donors configuration options.
3. Configure permitted tier, KPI, filter and optional-feature settings.
4. Validate configuration restrictions and dependencies.
5. Save tenant-specific settings.
6. Apply settings only within the relevant workspace.

![Tenant Configuration and Permissions](screenshot%20goals/21.%20Security%20and%20Privacy.png)

Exception: Tenant settings cannot disable mandatory security or grant access to another organisation's data.

### DON-WF-21 – Donation Corrections and Reconciliation

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-008–010, 026 Rules: DON-BR-014, 015, 035, 038

To-Be: Support authorised correction and reconciliation of conflicting donation information.

1. Identify an existing transaction requiring review.
2. Retrieve the related member, donation and source context.
3. Compare existing and incoming information.
4. Present the conflict to an authorised reviewer.
5. Approve, reject or defer the proposed change.
6. Apply only an authorised correction.
7. Preserve material history.
8. Recalculate affected giving summaries and KPIs.


Important: Refunds, reversals and payment corrections must follow the actual approved transaction model. Deleting and recreating financial transactions must not be assumed to be the standard correction mechanism.

### DON-WF-22 – Audit and Exception Handling

> Source diagram unavailable; refer to the workflow steps in this section.


Goals: DON-GO-021, 023, 025 Rules: DON-BR-034–038

To-Be: Material Donors operations must produce reliable outcomes and appropriate audit evidence.

| Event                      | Required Outcome                                     |
| -------------------------- | ---------------------------------------------------- |
| Donation recorded          | Record transaction outcome and relevant actor/source |
| Import processed           | Record batch status and processing counts            |
| Duplicate identified       | Preserve conflict for authorised review              |
| Reconciliation decision    | Record reviewer and decision                         |
| Tier configuration changed | Preserve configuration change history                |
| Donation corrected         | Record material changes and affected totals          |
| Export completed           | Record authorised export event                       |
| Integration failed         | Preserve committed donor data and report the failure |
| Permission denied          | Prevent unauthorised operation                       |


## 6. Shared Validation Rules

| Area              | Business Validation                                             |
| ----------------- | --------------------------------------------------------------- |
| Tenant            | All donor operations must respect tenant boundaries             |
| Permissions       | Existing role-based permissions govern actions                  |
| Member Identity   | Every donor must reference an existing member                   |
| Donation Creation | Required fields must be validated                               |
| Campaign          | Selected campaign must be a valid permitted reference           |
| Payment           | Recording and payment completion must not be assumed equivalent |
| Duplicates        | Conflicting records require authorised review                   |
| Import            | Validate format, fields, member references and transactions     |
| Tier Calculation  | Apply approved tenant thresholds                                |
| Donor Scoring     | Preserve established scoring logic                              |
| KPIs              | Recalculate affected measures after committed changes           |
| Export            | Apply filters, permission checks and tenant restrictions        |
| Audit             | Preserve evidence of material operations                        |
| Member Status     | Maintain separate Administrative and Giving Status attributes   |

## 7. Donor Import Outcome Rules

| Outcome                  | Definition                                            | KPI Effect                                |
| ------------------------ | ----------------------------------------------------- | ----------------------------------------- |
| Created                  | New eligible donation record committed                | Update affected KPIs                      |
| Updated                  | Existing transaction updated through authorised rules | Recalculate affected KPIs                 |
| Rejected                 | Invalid transaction not committed                     | No new contribution                       |
| Pending Member Review    | Member identity unresolved                            | No contribution until resolved            |
| Pending Duplicate Review | Transaction conflict awaiting decision                | No additional contribution until resolved |
| Skipped                  | Record excluded under approved policy                 | No additional contribution                |

Important distinction: Importing 250 donation transactions does not mean 250 new donors have been created. Unique donor counts must be based on qualifying members, not the number of imported rows.

## 8. Data Consistency Requirements

### 8.1 Members and Donors Consistency

| Event                         | Required Behaviour                                               |
| ----------------------------- | ---------------------------------------------------------------- |
| New Member Created            | Member remains non-donor unless qualifying donation exists       |
| First Qualifying Donation     | Existing member becomes a qualifying donor                       |
| Additional Donation           | Update donor giving history without creating another member      |
| Member Information Updated    | Reflect relevant shared identity/contact changes                 |
| Administrative Status Changed | Preserve historical giving information                           |
| Giving Status Changed         | Do not treat the status label alone as evidence of a transaction |
| Donation Corrected            | Recalculate affected giving totals and dependent measures        |
| Donation Import Completed     | Automatically update corresponding donor information and KPIs    |

### 8.2 Data Synchronisation Relationship

![Data Synchronisation Relationship](screenshot%20goals/5.9%20Existing%20Data%20Sources.png)

## 9. Screenshot Reference Mapping

| Screenshot            | Existing UI Evidence                                              | Related Workflows         |
| --------------------- | ----------------------------------------------------------------- | ------------------------- |
| Donors Overview       | KPIs, list, search, tier filters, Advanced, Export CSV, Add Donor | DON-WF-01, 02, 03, 14, 16 |
| Add Donor Modal       | Member selection, donation fields, Cancel and Save Donation       | DON-WF-05, 06             |
| Advanced Filters      | Donation range, score range, engagement segments, Apply/Clear     | DON-WF-03                 |
| Donor Details         | Identity, contact information, giving summaries, tier and tabs    | DON-WF-04, 13, 18         |
| Donor Profile Actions | Record Donation, Add Task, Send Message                           | DON-WF-19                 |
| Members Page          | Member identity and member-related donation navigation            | DON-WF-05, 06             |

Screenshots establish visible UI behaviour. They do not independently verify backend persistence, payment processing, permission enforcement or calculation formulas.

## 10. Goals-to-Workflow Traceability

| Business Goals | Supporting Workflows      |
| -------------- | ------------------------- |
| DON-GO-001     | DON-WF-01, 20             |
| DON-GO-002     | DON-WF-01, 20             |
| DON-GO-003     | DON-WF-11, 14, 20         |
| DON-GO-004     | DON-WF-07, 18             |
| DON-GO-005     | DON-WF-05, 07, 08         |
| DON-GO-006     | DON-WF-05, 06             |
| DON-GO-007     | DON-WF-05, 19             |
| DON-GO-008     | DON-WF-05, 09, 21         |
| DON-GO-009     | DON-WF-10                 |
| DON-GO-010     | DON-WF-10, 21             |
| DON-GO-011     | DON-WF-11                 |
| DON-GO-012     | DON-WF-12                 |
| DON-GO-013     | DON-WF-13                 |
| DON-GO-014     | DON-WF-01, 14             |
| DON-GO-015     | DON-WF-15                 |
| DON-GO-016     | DON-WF-14                 |
| DON-GO-017     | DON-WF-02, 03             |
| DON-GO-018     | DON-WF-16                 |
| DON-GO-019     | DON-WF-13, 14, 15         |
| DON-GO-020     | DON-WF-08                 |
| DON-GO-021     | DON-WF-08, 09, 22         |
| DON-GO-022     | DON-WF-17                 |
| DON-GO-023     | DON-WF-07, 18, 22         |
| DON-GO-024     | DON-WF-01, 20             |
| DON-GO-025     | DON-WF-21, 22             |
| DON-GO-026     | DON-WF-04, 06, 12, 17, 18 |

### 10.1 Requirements Traceability

![Requirements Traceability](screenshot%20goals/28.1%20Traceability%20Model.png)

## 11. Feature Catalogue Handoff

| Workflow Group | Required Feature Definitions                                           |
| -------------- | ---------------------------------------------------------------------- |
| DON-WF-01–03   | Tenant-scoped overview, search, tier filtering, advanced filters       |
| DON-WF-04–06   | Donor profile, donation modal, member selection and donor association  |
| DON-WF-07      | External integration ingestion, source mapping, validation             |
| DON-WF-08–09   | File template, upload, preview, validation, outcomes and correction    |
| DON-WF-10      | Transaction duplicate detection and administrator decisions            |
| DON-WF-11–12   | Tier settings, thresholds, classification and recalculation            |
| DON-WF-13      | Donor score inputs, calculation and display                            |
| DON-WF-14–15   | Existing KPIs, additional measures, configuration and drill-down       |
| DON-WF-16      | CSV export, filtered population and permissions                        |
| DON-WF-17      | Automatic recalculation and display refresh                            |
| DON-WF-18–19   | Giving history, profile tabs and existing actions                      |
| DON-WF-20      | Tenant configuration, existing permissions and optional-feature access |
| DON-WF-21–22   | Corrections, source reconciliation, audit and error handling           |

Each resulting feature must reference applicable `DON-GO`, `DON-BR` and `DON-WF` identifiers.

## 12. Open Decisions and Clarifications

These items require detailed verification or business approval. They do not reopen the confirmed standalone product requirements.

| Decision ID | Detail to Finalise                                                   |
| ----------- | -------------------------------------------------------------------- |
| DON-OD-001  | Qualifying donation statuses and donor eligibility                   |
| DON-OD-002  | Prospect visibility in the Donors list and KPI calculations          |
| DON-OD-003  | Save Donation semantics: payment recording versus payment processing |
| DON-OD-004  | Supported payment methods and transaction statuses                   |
| DON-OD-005  | Donation duplicate-matching identifiers and review actions           |
| DON-OD-006  | Import template columns, limits and partial-success behaviour        |
| DON-OD-007  | Unmatched imported donor/member identity resolution                  |
| DON-OD-008  | Tier thresholds, currency, reporting period and recalculation        |
| DON-OD-009  | Existing and new KPI definitions                                     |
| DON-OD-010  | Donor scoring calculation and permitted configuration                |
| DON-OD-011  | KPI/filter combination and reset behaviour                           |
| DON-OD-012  | Exported columns and precise dataset-selection rules                 |
| DON-OD-013  | Existing profile-tab, Add Task and Send Message behaviour            |
| DON-OD-014  | Refund, reversal and historical-correction rules                     |
| DON-OD-015  | Integration source priority and conflict reconciliation              |
| DON-OD-016  | Currency conversion and multi-currency aggregation                   |
| DON-OD-017  | Optional-feature entitlements and dependencies                       |
| DON-OD-018  | Audit visibility and data-retention rules                            |

## 13. Workflow Validation Summary

| Review Area               | Result                                                     |
| ------------------------- | ---------------------------------------------------------- |
| Original Document         | Reviewed and expanded                                      |
| Goals Alignment           | 26 Donors business goals                                   |
| Business Rules            | Aligned with 40 Donors rules                               |
| Workflow Coverage         | 22 workflows                                               |
| As-Is Functionality       | Retained and distinguished                                 |
| Standalone Requirements   | Incorporated                                               |
| Member–Donor Relationship | Confirmed and reflected                                    |
| Role Permissions          | Treated as existing functionality                          |
| Donation Entry            | Existing fields and navigation preserved                   |
| Data Integration          | Existing functionality retained                            |
| Bulk Imports              | Validation, member matching and outcomes included          |
| Duplicate Resolution      | Administrator-controlled conflicting records               |
| Tier Configuration        | Organisation-specific thresholds covered                   |
| KPIs                      | Existing calculations preserved, additional KPIs supported |
| KPI Updates               | Automatic after committed changes                          |
| Search and Filtering      | Existing and enhanced flows covered                        |
| Export                    | Filtered and tenant-restricted                             |
| Donor Profiles            | Existing summaries, tabs and actions preserved             |
| Flowcharts                | Included for meaningful decision and data flows            |
| Outstanding Decisions     | Identified without inventing policy                        |
| Documentation Terminology | No phase-based terminology                                 |

## 14. Document Conclusion

The Donors BRD Workflow defines how the existing AiXPurpose Donors capability will operate as part of a standalone, multi-tenant application.

It retains existing donor lists, profiles, donation recording, scoring, filters, KPI calculations and external integrations while introducing governed data imports, member-linked identity resolution, duplicate reconciliation, configurable donor tiers, enhanced KPIs and controlled exports.

The confirmed relationship that every donor is an existing member, but not every member is a donor is maintained throughout the workflows.

The 22 workflows provide the operational foundation for the Donors BRD Feature Catalogue, where the detailed functional definitions, field validations, acceptance criteria and traceability will be established.
