# AiXPurpose – Donor Management – Members

> **Document type:** Business Requirements Document – Feature Catalogue

## Document Control

| Field             | Details                                                                                       |
| ----------------- | --------------------------------------------------------------------------------------------- |
| Document Name     | AiXPurpose – Members – Feature Catalogue                                                      |
| Product           | AiXPurpose                                                                                    |
| Product Type      | Standalone Multi-Tenant Application                                                           |
| Module            | Donor Management                                                                              |
| Capability        | Members                                                                                       |
| Document Type     | Business Requirements Document – Feature Catalogue                                            |
| Version           | 1.0                                                                                           |
| Status            | Draft for Business Review                                                                     |
| Document Owner    | Product Management                                                                            |
| Business Owner    | Client Organisation / Fundraising Operations                                                  |
| Related Goals     | AiXPurpose – Members – Goals v1.0                                                             |
| Related Workflow  | AiXPurpose – Members – Workflow v1.0                                                          |
| Feature ID Format | MEM-F-###                                                                                     |
| Source            | Existing application, screenshots, approved business requirements and standalone enhancements |

## Overview

This document specifies the functional features, validations, and acceptance criteria for the Members capability, with traceability to the related Goals and Workflow documents.

## Contents

- [1. Feature Catalogue Purpose](#1-feature-catalogue-purpose)
- [2. Feature Summary](#2-feature-summary)
- [3. Detailed Feature Catalogue](#3-detailed-feature-catalogue)
- [3.1 Members Workspace and Listing](#31-members-workspace-and-listing)
- [3.2 Manual Member Management](#32-manual-member-management)
- [3.3 Member Profile and Donations](#33-member-profile-and-donations)
- [3.4 Bulk Import and Refresh](#34-bulk-import-and-refresh)
- [3.5 KPI Interaction and Filtering](#35-kpi-interaction-and-filtering)
- [3.6 Member Status and Identity Governance](#36-member-status-and-identity-governance)
- [3.7 Import Validation and Reconciliation](#37-import-validation-and-reconciliation)
- [3.8 KPI and Reporting Enhancements](#38-kpi-and-reporting-enhancements)
- [3.9 Tenant Configuration and Security](#39-tenant-configuration-and-security)
- [3.10 Audit, Reliability and Consistency](#310-audit-reliability-and-consistency)
- [4. Member Field Catalogue](#4-member-field-catalogue)
- [5. Member Status Definitions](#5-member-status-definitions)
- [5.1 Administrative Status](#51-administrative-status)
- [5.2 Giving Status](#52-giving-status)
- [6. Data Source and Import Rules](#6-data-source-and-import-rules)
- [6.1 Supported Source Methods](#61-supported-source-methods)
- [6.2 Import Outcome Rules](#62-import-outcome-rules)
- [6.3 Duplicate Handling Rules](#63-duplicate-handling-rules)
- [7. KPI Feature Catalogue](#7-kpi-feature-catalogue)
- [7.1 Existing KPI Baseline](#71-existing-kpi-baseline)
- [7.2 Recommended Additional KPIs](#72-recommended-additional-kpis)
- [7.3 KPI Calculation and Refresh Rules](#73-kpi-calculation-and-refresh-rules)
- [8. Goals-to-Workflow-to-Feature Traceability](#8-goals-to-workflow-to-feature-traceability)
- [9. Workflow-to-Feature Mapping](#9-workflow-to-feature-mapping)
- [10. Business and Technical Dependencies](#10-business-and-technical-dependencies)
- [11. Security and Governance Requirements](#11-security-and-governance-requirements)
- [12. Open Business Decisions](#12-open-business-decisions)
- [13. Feature Acceptance Summary](#13-feature-acceptance-summary)
- [14. Product Management Validation Summary](#14-product-management-validation-summary)
- [15. Document Conclusion](#15-document-conclusion)

## 1. Feature Catalogue Purpose

This Feature Catalogue translates the approved Members Goals and Workflow into detailed, traceable functional requirements for product, engineering and QA teams.

It defines:

- Existing functionality that must be retained.
- Functionality requiring enhancement.
- New capabilities for standalone AiXPurpose.
- Business validations and acceptance criteria.
- Tenant configuration and access requirements.
- Member data management and integration behaviour.
- KPI, reporting and export requirements.
- Dependencies, business rules and traceability.

The document covers the Members capability within Donor Management. Related Donors, Campaigns, Segments, Prospecting and communication capabilities are addressed where they interact with Members, without independently defining those modules.

### 1.1 Feature Classification

| Classification      | Definition                                             |
| ------------------- | ------------------------------------------------------ |
| As-Is               | Existing application functionality to retain           |
| As-Is + Enhancement | Existing capability requiring additional functionality |
| To-Be               | New standalone application requirement                 |
| Proposed            | Recommended functionality requiring business approval  |

Confirmed To-Be requirements are treated as part of the target product baseline, although they are not claimed to be implemented.

### 1.2 Traceability Standards

| Identifier | Purpose                |
| ---------- | ---------------------- |
| MEM-GO-### | Members Business Goal  |
| MEM-BR-### | Members Business Rule  |
| MEM-WF-##  | Members Workflow       |
| MEM-F-###  | Members Feature        |
| MEM-OD-### | Open Business Decision |

All features must inherit applicable tenant isolation, existing permission enforcement and audit requirements.

## 2. Feature Summary

The original catalogue contained 36 features. Their identifiers are preserved, and additional features are introduced to cover the approved standalone requirements and the expanded Members Workflow.

| Feature Range | Functional Area                         | Count |
| ------------- | --------------------------------------- | ----- |
| MEM-F-001–009 | Members Workspace and Listing           | 9     |
| MEM-F-010–018 | Manual Member Management                | 9     |
| MEM-F-019–024 | Profile, Donations and Data Sources     | 6     |
| MEM-F-025–032 | Bulk Import and Refresh                 | 8     |
| MEM-F-033–036 | KPI Interaction and Filtering           | 4     |
| MEM-F-037–043 | Member Status and Identity Governance   | 7     |
| MEM-F-044–051 | Import Validation and Reconciliation    | 8     |
| MEM-F-052–059 | KPI and Reporting Enhancements          | 8     |
| MEM-F-060–066 | Tenant Configuration and Security       | 7     |
| MEM-F-067–072 | Audit, Reliability and Data Consistency | 6     |
| Total         |                                         | 72    |

## 3. Detailed Feature Catalogue

## 3.1 Members Workspace and Listing

### MEM-F-001 – Tenant-Scoped Members Workspace

Classification: As-Is + Enhancement Goal: MEM-GO-001, 002 Workflow: MEM-WF-01, 17

Requirements:

1. Members must be accessible within the authenticated user's authorised tenant.
2. Member records and associated summaries must be restricted to the tenant.
3. Existing permissions must govern available actions.
4. Different tenants may have different approved settings and optional feature entitlements.

Acceptance Criteria:

- Authorised users can access their tenant's Members page.
- Records belonging to another tenant are not accessible.
- Tenant configuration does not compromise isolation.

### MEM-F-002 – Default Active Members Listing

Classification: As-Is + Enhancement Goal: MEM-GO-005, 013 Workflow: MEM-WF-01, 07, 10

Requirements:

1. Members must display Administrative Status = Active by default.
2. Giving Status must remain independent of Administrative Status.
3. Users with permission may filter Inactive members.
4. Returning to the default view must restore the approved initial filter state.

Acceptance Criteria:

- Active Prospect, Pledged, Donated and Lapsed members can appear in the default list.
- Inactive members are excluded from the default view.
- Permitted filtering can display inactive records.

### MEM-F-003 – Members List Columns

Classification: As-Is + Enhancement Goal: MEM-GO-013, 018 Workflow: MEM-WF-01, 07

Requirements:

Retain the existing columns:

| Column        | Requirement                                                     |
| ------------- | --------------------------------------------------------------- |
| Name          | Member display name                                             |
| Donor Type    | Individual / Organisation / Foundation                          |
| Contact       | Available phone and email                                       |
| Location      | Member address/location                                         |
| Member Status | Giving Status, with separately accessible administrative status |
| Pledged 2024  | Replace fixed year with approved reporting-period logic         |
| Created       | Member creation date                                            |
| Actions       | View, Edit, Add Donation                                        |

Acceptance Criteria:

- Existing columns remain available.
- Members display correct information.
- Historical year references are not permanently hard-coded in the enhanced product.

### MEM-F-004 – Members List Pagination

Classification: As-Is Goal: MEM-GO-013 Workflow: MEM-WF-07

Requirements:

1. Support pagination for member records.
2. Preserve active search and filter criteria during page navigation.
3. Display accurate result counts and page navigation.

Acceptance Criteria:

- Users can navigate between available pages.
- Pagination does not reset the current filters.
- Records are not duplicated or omitted because of pagination.

### MEM-F-005 – Search Members by Identity

Classification: As-Is Goal: MEM-GO-013 Workflow: MEM-WF-07

Requirements:

1. Search by Name, Email and Phone.
2. Search must operate within the authorised Members dataset.
3. Search must work with existing filters and pagination.

Acceptance Criteria:

- Searching for an existing member returns matching records.
- Non-matching searches show an appropriate empty result.
- Search does not expose records from another tenant.

### MEM-F-006 – Donor Type Filter

Classification: As-Is Goal: MEM-GO-013 Workflow: MEM-WF-07

Requirements:

Support:

- All Types.
- Individual.
- Organisation.
- Foundation.

Acceptance Criteria:

- Selecting a type displays matching members.
- All Types removes the donor-type restriction.

### MEM-F-007 – Giving Status Filter

Classification: As-Is + Enhancement Goal: MEM-GO-013, 025 Workflow: MEM-WF-07, 10

Requirements:

Support the standardised Giving Status values:

- Prospect.
- Pledged.
- Donated.
- Lapsed.
- All Statuses.

Acceptance Criteria:

- Filtering uses Giving Status, not Administrative Status.
- Selecting Donated displays members with the relevant giving classification.
- Giving Status filters can operate alongside Administrative Status filters.

### MEM-F-008 – Global Search Entry

Classification: As-Is Goal: MEM-GO-013 Workflow: MEM-WF-01

Requirements:

1. Retain the shared Search Everything control.
2. Permit searches across supported modules according to existing access permissions.
3. Keep global search separate from Members-specific search.

Acceptance Criteria:

- Global search remains accessible from Members.
- Cross-module results respect existing permissions.

### MEM-F-009 – Shared Application Controls

Classification: As-Is Workflow: MEM-WF-01

Requirements:

Retain:

- Notification bell.
- Logged-in user profile.
- Sign-out.
- Copilot entry point.

Acceptance Criteria:

- Existing shared controls remain accessible.
- Their existing platform functionality is not disrupted by Members enhancements.

## 3.2 Manual Member Management

### MEM-F-010 – Open Add Member

Classification: As-Is Goal: MEM-GO-006 Workflow: MEM-WF-02

Requirements:

1. Provide Add Member on the overview page.
2. Open the existing five-section registration form.
3. Use applicable tenant settings and permissions.

Acceptance Criteria:

- Authorised users can open the form.
- All five sections are accessible.

### MEM-F-011 – Constituent Contact Information

Classification: As-Is + Enhancement Goal: MEM-GO-006 Workflow: MEM-WF-02, 09

Requirements:

Capture:

| Field          | Options / Purpose                    |
| -------------- | ------------------------------------ |
| Donor Type     | Individual, Organisation, Foundation |
| Title          | Person's title                       |
| First Name     | Individual identity                  |
| Last Name      | Individual identity                  |
| Email          | Primary email                        |
| Mobile Phone   | Mobile contact                       |
| Home Phone     | Home contact                         |
| Business Phone | Business contact                     |

To-Be Enhancement: Support appropriate organisation/foundation identity fields rather than requiring person-name fields for every constituent type.

Acceptance Criteria:

- Existing fields remain available.
- Applicable field validation is enforced.
- Identity fields adapt according to approved member-type rules.

### MEM-F-012 – Address and Communication Details

Classification: As-Is + Enhancement Goal: MEM-GO-006 Workflow: MEM-WF-02, 09

Requirements:

Capture:

- Address.
- City.
- State.
- ZIP/Postal Code.
- Anonymous Donor.
- Do Not Solicit.

Acceptance Criteria:

- Existing information can be entered and edited.
- Communication preference values are stored accurately.
- The same preferences are available to authorised dependent capabilities.

The execution of outreach remains the responsibility of the Communications capability.

### MEM-F-013 – Campaign and Giving Information

Classification: As-Is + Enhancement Goal: MEM-GO-006, 025 Workflow: MEM-WF-02, 10

Requirements:

Capture:

- Current Campaign.
- Giving Status.
- Current Solicitor.
- Pledged Amount.

Acceptance Criteria:

- Campaign selection uses available authorised campaign data.
- Giving Status supports Prospect, Pledged, Donated and Lapsed.
- Pledged Amount is stored according to approved currency and validation rules.
- Administrative Status is managed independently.

### MEM-F-014 – Recognition and Social Information

Classification: As-Is Goal: MEM-GO-006 Workflow: MEM-WF-02, 09

Requirements:

Retain:

- Recognition / Donor Publication.
- Spouse Last Name.
- Spouse Middle Name.
- Alternate Phone 1.
- Alternate Phone Type 1.
- Alternate Phone 2.
- Related existing recognition fields.

Acceptance Criteria:

- Fields are available where applicable.
- Saved information is retained when members are edited.
- Member-type applicability follows approved rules.

### MEM-F-015 – Advanced and System Information

Classification: As-Is Goal: MEM-GO-006 Workflow: MEM-WF-02, 09

Requirements:

Retain:

- iWave Score.
- Capacity Score.
- Propensity Score.
- Affinity Score.
- Profile URL.
- First Guest Name.
- Second Guest Name.
- Previous Home Number.
- Alternate Phone Type 2.

Acceptance Criteria:

- Existing advanced fields remain available.
- Existing values are preserved during editing.
- Scoring calculations or external enrichment are not invented where no authoritative rules have been supplied.

### MEM-F-016 – Save Manually Created Member

Classification: As-Is + Enhancement Goal: MEM-GO-004, 006, 025 Workflow: MEM-WF-02, 06

Requirements:

1. Validate applicable mandatory fields.
2. Check for potential duplicate members.
3. Create the member when the record is eligible.
4. Store it within the current tenant.
5. Update the Members register and affected KPIs after commit.

Acceptance Criteria:

- Valid new members can be created.
- Unapproved conflicting records are not silently merged or overwritten.
- Newly committed members contribute to relevant KPI calculations.

### MEM-F-017 – Open Prefilled Edit Member Form

Classification: As-Is Goal: MEM-GO-011 Workflow: MEM-WF-09

Requirements:

1. Selecting Edit opens the existing five-section form.
2. Populate existing field values.
3. Maintain the selected Member ID throughout editing.

Acceptance Criteria:

- Existing member values are displayed.
- Editing does not unintentionally create a separate member.

### MEM-F-018 – Update Existing Member Information

Classification: As-Is + Enhancement Goal: MEM-GO-011, 019 Workflow: MEM-WF-09

Requirements:

1. Allow authorised users to modify existing details.
2. Validate modified fields.
3. Preserve member identity.
4. Record material changes.
5. Require administrator review for conflicting source/identity updates.
6. Refresh affected KPIs following successful changes.

Acceptance Criteria:

- Approved edits appear in the member profile.
- Unapproved conflicting updates do not overwrite current information.
- Relevant summary figures remain consistent.

## 3.3 Member Profile and Donations

### MEM-F-019 – Open Member Profile

Classification: As-Is Goal: MEM-GO-005 Workflow: MEM-WF-08

Requirements:

A member profile must open when the user:

1. Clicks a member row.
2. Clicks the View action.

Acceptance Criteria:

- Both actions open the same member record.
- Member details correspond to the selected Member ID.

### MEM-F-020 – Member Profile Summary

Classification: As-Is + Enhancement Goal: MEM-GO-005, 019 Workflow: MEM-WF-08

Requirements:

Retain:

- Member identity.
- Member type.
- Contact and address information.
- Member status.
- Total Donations.
- Pledged Amount.
- iWave Score.
- Edit and Add Donation actions.

To-Be Enhancements:

- Administrative and Giving Status visibility.
- Dynamic pledge reporting period.
- Approved data-source information.
- Relevant record-completeness indicators.

Acceptance Criteria:

- Existing profile information remains available.
- Giving summaries reflect authoritative linked records.
- Additional indicators appear only where supported by approved data.

### MEM-F-021 – Add Donation from Member List

Classification: As-Is + Enhancement Goal: MEM-GO-021, 022 Workflow: MEM-WF-16

Requirements:

1. Retain the dollar-icon action.
2. Open the existing donation-entry capability.
3. Pass the intended Member ID as context where supported.
4. Prevent cross-tenant member association.

Acceptance Criteria:

- Selecting the action opens donation entry.
- Any saved donation must reference an existing member within the tenant.

### MEM-F-022 – Add Donation from Member Profile

Classification: As-Is + Enhancement Goal: MEM-GO-021, 022 Workflow: MEM-WF-16

Requirements:

1. Retain Add Donation.
2. Resolve the selected member.
3. Establish donor association when a qualifying donation is successfully recorded.
4. Update relevant giving summaries from committed donation data.

Acceptance Criteria:

- Donation entry opens for the intended member context.
- A member without a donation is not automatically classified as a donor.
- No duplicate member identity is created solely because of donation activity.

### MEM-F-023 – Integrated Member Records

Classification: As-Is + Enhancement Goal: MEM-GO-004, 005, 012 Workflow: MEM-WF-04, 06

Requirements:

1. Retain supported external member integrations.
2. Map incoming records to the appropriate tenant.
3. Validate applicable member information.
4. Identify potential existing-member matches.
5. Require review for conflicting updates.
6. Preserve source information where available.
7. Refresh affected member information and KPIs after commit.

Acceptance Criteria:

- Successfully processed integration data appears in the correct Members register.
- Conflicting updates are held for review.
- Rejected or unresolved records do not incorrectly increase member totals.

### MEM-F-024 – Export Members to CSV

Classification: As-Is + Enhancement Goal: MEM-GO-017 Workflow: MEM-WF-14

Requirements:

1. Retain the existing Export CSV action.
2. Apply authorised tenant scope.
3. Support filtered export under the enhanced export capability.
4. Ensure exported information matches the resolved dataset.

Acceptance Criteria:

- Authorised users can export member data.
- Exported data excludes unauthorised records.
- Existing CSV functionality remains operational.

## 3.4 Bulk Import and Refresh

### MEM-F-025 – Import Members Entry

Classification: To-Be Goal: MEM-GO-007 Workflow: MEM-WF-05

Requirements:

1. Provide Import Members on the Members overview.
2. Make it available only to authorised users.
3. Open the member import interface.

Acceptance Criteria:

- Authorised administrators can initiate member imports.
- Unauthorised users cannot execute imports.

### MEM-F-026 – Member Import Templates

Classification: To-Be Goal: MEM-GO-007, 008 Workflow: MEM-WF-05

Requirements:

1. Provide predefined downloadable templates.
2. Identify mandatory and optional fields.
3. Support approved Excel and CSV formats.
4. Accommodate approved member-type differences.
5. Associate templates with an identifiable version.

Acceptance Criteria:

- Users can download a valid template.
- Required fields are identifiable.
- Unsupported template structures are rejected with an understandable explanation.

### MEM-F-027 – Upload Member Dataset

Classification: To-Be Goal: MEM-GO-007 Workflow: MEM-WF-05

Requirements:

1. Accept supported spreadsheet/CSV files.
2. Validate file format and applicable limits.
3. Ensure the import belongs to the current tenant.
4. Reject unreadable or unsupported files.

Acceptance Criteria:

- Supported files proceed to validation.
- Invalid files do not create member records.

### MEM-F-028 – Validate Imported Member Data

Classification: To-Be Goal: MEM-GO-008, 025 Workflow: MEM-WF-05

Requirements:

Validate:

- Mandatory fields.
- Member type.
- Supported giving status.
- Field formats.
- Required identity information.
- Duplicate candidates.
- Tenant-specific approved field rules.

Acceptance Criteria:

- Invalid rows are identified.
- Missing mandatory fields are reported.
- Invalid rows are not presented as successfully imported.

### MEM-F-029 – Create Members from Import

Classification: To-Be Goal: MEM-GO-007, 009 Workflow: MEM-WF-05

Requirements:

1. Process eligible validated rows.
2. Create new member records when no conflicting existing identity is found.
3. Route ambiguous or conflicting records for review.
4. Record successfully committed outcomes.
5. Make imported members available through the common Members register.

Acceptance Criteria:

- Eligible new members are committed.
- Unresolved duplicate conflicts remain uncommitted.
- Committed members appear according to applicable list filters.

### MEM-F-030 – Import Result Summary

Classification: To-Be Goal: MEM-GO-009 Workflow: MEM-WF-05

Requirements:

Display:

- Total rows processed.
- Successfully created.
- Successfully updated.
- Rejected.
- Pending review.
- Skipped, where supported.

Acceptance Criteria:

- Reported counts represent actual processing outcomes.
- The system does not describe rejected or pending records as successfully imported.

### MEM-F-031 – Review and Correct Imported Data

Classification: To-Be Goal: MEM-GO-009, 011, 019 Workflow: MEM-WF-05, 09

Requirements:

1. Allow authorised review of errors and incomplete records.
2. Provide correction using the existing Edit functionality for committed records.
3. Support appropriate correction and resubmission for rejected import rows.
4. Preserve linkage to the original import operation.

Acceptance Criteria:

- Administrators can identify affected records.
- Corrections do not create unintended duplicate members.
- Successfully corrected records update the consolidated register.

### MEM-F-032 – Refresh Members Listing

Classification: To-Be Goal: MEM-GO-024 Workflow: MEM-WF-15

Requirements:

1. Provide Refresh on the Members overview.
2. Reload current authorised records.
3. Preserve applicable user filters where possible.
4. Display the latest committed data and KPI values.

Acceptance Criteria:

- Refresh displays current records.
- Refresh does not create duplicate records.
- Import-driven KPI recalculation occurs automatically without requiring Refresh.

## 3.5 KPI Interaction and Filtering

### MEM-F-033 – Clickable KPI Cards

Classification: To-Be Goal: MEM-GO-014 Workflow: MEM-WF-12

Requirements:

1. Existing KPI cards must become interactive.
2. Selecting a KPI must apply its approved record-selection criteria.
3. Display matching authorised members.
4. Allow users to clear the KPI filter.

Acceptance Criteria:

- Selecting Phone Verified displays matching verified-phone members.
- Result totals reconcile with the KPI's authorised counting scope.
- Clearing the KPI selection restores the applicable list view.

### MEM-F-034 – Configurable KPI Selection

Classification: To-Be Goal: MEM-GO-015 Workflow: MEM-WF-11, 17

Requirements:

1. Provide a governed list of available Members KPIs.
2. Allow permitted users to select displayed KPI cards.
3. Apply existing permissions and tenant feature entitlements.
4. Preserve approved KPI calculation definitions.

Acceptance Criteria:

- Users can select permitted KPIs.
- Selected KPIs display correctly.
- Unavailable or unauthorised measures cannot be selected.

### MEM-F-035 – Additional Member Filters

Classification: To-Be Goal: MEM-GO-016 Workflow: MEM-WF-13

Requirements:

Support approved additional filters such as:

- Administrative Status.
- Country, State and City.
- Created Date.
- Campaign.
- Data Source.
- Contact Verification.
- Pledge Range.
- Data Completeness, where available.

Acceptance Criteria:

- Approved filters narrow the displayed dataset.
- Filter combinations remain consistent.
- Users cannot retrieve data outside their permitted scope.

### MEM-F-036 – Filtered Members Export

Classification: To-Be Goal: MEM-GO-017 Workflow: MEM-WF-14

Requirements:

1. Resolve the current applied search and filters.
2. Export the full authorised matching dataset, not merely the current paginated screen.
3. Support specifically selected records if record-selection export is approved.
4. Apply permitted export columns and access controls.

Acceptance Criteria:

- Exported records match the intended filtered dataset.
- Pagination does not incorrectly limit a filtered export.
- Unauthorised information is excluded.

## 3.6 Member Status and Identity Governance

### MEM-F-037 – Administrative Member Status

Classification: To-Be Goal: MEM-GO-025 Workflow: MEM-WF-10

Requirements:

1. Maintain Administrative Status independently.
2. Support Active and Inactive.
3. Use Active as the default Members list criterion.
4. Preserve historical information for inactive members.

Acceptance Criteria:

- An inactive member may retain existing donation history.
- Inactivation does not automatically change Giving Status.

### MEM-F-038 – Giving Status Management

Classification: As-Is + Enhancement Goal: MEM-GO-025 Workflow: MEM-WF-10

Requirements:

1. Standardise Prospect, Pledged, Donated and Lapsed.
2. Keep Giving Status separate from administrative activity.
3. Apply approved update and transition rules.
4. Preserve relevant historical giving information.

Acceptance Criteria:

- Giving Status can be viewed and filtered independently.
- Administrative Status changes do not automatically overwrite Giving Status.
- Giving-related transitions follow approved rules.

### MEM-F-039 – Member-to-Donor Identity Relationship

Classification: Confirmed Business Rule / Enhancement Goal: MEM-GO-021 Workflow: MEM-WF-16

Requirements:

1. Every donor must reference an existing member.
2. A member may exist without donor activity.
3. A qualifying donation creates or maintains the appropriate donor relationship.
4. Donor association must not generate a duplicate constituent identity.

Acceptance Criteria:

- A member without donations need not appear as a donor.
- Every donor resolves to an existing member.
- A donor's underlying member identity remains consistent.

### MEM-F-040 – Cross-Source Duplicate Detection

Classification: To-Be Goal: MEM-GO-010 Workflow: MEM-WF-06

Requirements:

1. Check potential duplicates during manual creation.
2. Apply the same principle to imports.
3. Apply duplicate checking to integration ingestion.
4. Compare records only within the authorised tenant.
5. Use approved matching identifiers and rules.

Acceptance Criteria:

- Potential duplicates are identified for handling.
- Duplicate checking does not expose another tenant's records.

### MEM-F-041 – Administrator Duplicate Review

Classification: To-Be Goal: MEM-GO-010, 011 Workflow: MEM-WF-06

Requirements:

1. Present potentially conflicting member records for authorised review.
2. Show relevant existing and incoming values.
3. Allow approved resolution actions.
4. Prevent conflicting merges or updates before administrator approval.
5. Record the decision.

Acceptance Criteria:

- Conflicting records are not automatically merged.
- Only authorised administrators can approve conflicting changes.
- Decisions are traceable.

### MEM-F-042 – Controlled Member Merge

Classification: To-Be Goal: MEM-GO-010, 021 Workflow: MEM-WF-06

Requirements:

1. Permit merging only after the applicable review and authorisation.
2. Preserve the surviving member identity.
3. Maintain associated donor and donation references correctly.
4. Record source identities and merge history.
5. Prevent unrelated members from being merged unintentionally.

Acceptance Criteria:

- Approved merges preserve associated business information.
- Rejected merges leave existing records unchanged.
- The merge outcome is auditable.

### MEM-F-043 – Source Attribution

Classification: To-Be Goal: MEM-GO-012 Workflow: MEM-WF-04, 08

Requirements:

Record applicable source information:

- Manual creation.
- Excel/CSV import.
- External integration.
- Source system reference.
- Relevant creation or synchronisation metadata.

Acceptance Criteria:

- Authorised users can identify the available source of a member record.
- Source metadata remains available for reconciliation and investigation.

## 3.7 Import Validation and Reconciliation

### MEM-F-044 – Import File Structure Validation

Classification: To-Be Goal: MEM-GO-008 Workflow: MEM-WF-05

Requirements:

Validate file format, template version, column structure, required headers and applicable processing limits.

Acceptance Criteria:

- Unsupported file structures are rejected before member creation.
- Users receive actionable error information.

### MEM-F-045 – Row-Level Import Validation

Classification: To-Be Goal: MEM-GO-008 Workflow: MEM-WF-05

Requirements:

1. Validate imported records individually.
2. Identify invalid or missing mandatory values.
3. Produce row-level error references.
4. Prevent invalid rows from being silently committed.

Acceptance Criteria:

- Administrators can identify which rows require correction.
- Rejected rows do not affect committed member totals.

### MEM-F-046 – Import Preview and Confirmation

Classification: To-Be Goal: MEM-GO-007, 009 Workflow: MEM-WF-05

Requirements:

1. Display validation results before committing eligible rows.
2. Identify new, matched, rejected and review-required records.
3. Require authorised confirmation before processing the eligible dataset.
4. Allow cancellation without committing the preview.

Acceptance Criteria:

- Users can review the intended import outcome.
- Cancelling before confirmation creates no member records from that operation.

### MEM-F-047 – Partial Import Processing

Classification: To-Be, Processing Policy to Approve Goal: MEM-GO-009 Workflow: MEM-WF-05

Requirements:

1. Support clear separation of eligible and ineligible records.
2. Commit eligible rows only under the approved partial-success policy.
3. Preserve rejected and pending-review outcomes.
4. Report actual committed counts.

Acceptance Criteria:

- A failed row is not counted as successfully created.
- Approved partial processing does not silently discard unresolved records.

### MEM-F-048 – Import Duplicate Resolution

Classification: To-Be Goal: MEM-GO-010 Workflow: MEM-WF-05, 06

Requirements:

1. Identify potential matches against existing members and relevant rows in the import.
2. Route conflicts for administrator review.
3. Permit updates or merges only according to approved decisions.
4. Prevent repeated imports from unintentionally creating duplicate identities.

Acceptance Criteria:

- Conflicting matches require review.
- Reprocessing the same dataset does not bypass duplicate checks.

### MEM-F-049 – Import Error Report

Classification: To-Be Goal: MEM-GO-009 Workflow: MEM-WF-05

Requirements:

Provide error information containing:

- Row reference.
- Field, where applicable.
- Error description.
- Processing outcome.
- Relevant correction guidance.

Acceptance Criteria:

- Users can identify and correct rejected rows.
- Errors do not reveal information outside the tenant.

### MEM-F-050 – Import History

Classification: To-Be Goal: MEM-GO-009, 023 Workflow: MEM-WF-05, 18

Requirements:

Track import batch, initiating user, processing time, file/template context, results and review decisions.

Acceptance Criteria:

- Authorised administrators can review previous import outcomes.
- Historical import counts remain identifiable.

### MEM-F-051 – Import-to-KPI Synchronisation

Classification: Confirmed To-Be Goal: MEM-GO-024 Workflow: MEM-WF-05, 15

Requirements:

1. Detect successfully committed member changes.
2. Update affected KPI calculations automatically.
3. Exclude rejected and unresolved rows.
4. Ensure KPI totals reconcile with committed records and approved KPI definitions.

Acceptance Criteria:

- Successful imports automatically update relevant KPI figures.
- KPI updates do not require clicking Refresh.
- Rejected import records do not increase member counts.

## 3.8 KPI and Reporting Enhancements

### MEM-F-052 – Existing KPI Calculation Reuse

Classification: As-Is + Enhancement Goal: MEM-GO-014, 015 Workflow: MEM-WF-11

Requirements:

Retain existing calculation logic for:

- Total Members.
- Conversion Ready.
- Email Verified.
- Phone Verified.

Use the established calculation framework for approved new measures.

Acceptance Criteria:

- Existing KPI calculations continue to operate.
- New KPIs use documented, approved definitions.
- Enhancements do not unintentionally alter current formulas.

### MEM-F-053 – Additional KPI Library

Classification: To-Be Goal: MEM-GO-015 Workflow: MEM-WF-11

Requirements:

Support an approved Members KPI catalogue, potentially including:

| KPI                        | Intended Insight                                   |
| -------------------------- | -------------------------------------------------- |
| Active Members             | Administratively active records                    |
| New Members                | Members created within an approved period          |
| Members by Type            | Individual / Organisation / Foundation composition |
| Members by Location        | Geographic distribution                            |
| Members by Source          | Manual / Import / Integration origin               |
| Members with Pledges       | Members with qualifying pledge information         |
| Member-to-Donor Conversion | Share of eligible members who became donors        |
| Data Completeness          | Completeness against defined fields                |
| Pending Duplicate Reviews  | Unresolved potential duplicates                    |

Acceptance Criteria:

- Only approved KPIs are available for selection.
- Calculation definitions are consistent across dashboard and drill-down views.

### MEM-F-054 – KPI Configuration Persistence

Classification: To-Be, Configuration Policy to Approve Goal: MEM-GO-015 Workflow: MEM-WF-11, 17

Requirements:

1. Permit authorised selection of displayed KPI cards.
2. Save selections according to the approved user-level or tenant-level preference model.
3. Respect available feature entitlements.

Acceptance Criteria:

- Saved KPI selections are restored according to the approved configuration scope.
- Users cannot select unauthorised KPIs.

### MEM-F-055 – KPI Filter Consistency

Classification: To-Be Goal: MEM-GO-014 Workflow: MEM-WF-12

Requirements:

1. Use the same approved business calculation scope for the KPI and its related member list.
2. Apply authorised tenant restrictions.
3. Combine KPI, search and other filters according to a defined policy.
4. Support clear/reset behaviour.

Acceptance Criteria:

- KPI drill-down records satisfy the selected KPI criteria.
- Displayed counts and records reconcile where the same filters and counting unit apply.

### MEM-F-056 – Dynamic Pledge Reporting Period

Classification: To-Be Goal: MEM-GO-018 Workflow: MEM-WF-07, 08

Requirements:

1. Remove permanent reliance on the 2024 label.
2. Use an approved reporting period.
3. Apply consistent period logic across list and profile summaries.

Acceptance Criteria:

- The selected/default reporting period is correctly labelled.
- Pledge summaries correspond to the applicable period.

### MEM-F-057 – Members Reporting Visualisations

Classification: Proposed Enhancement Goal: MEM-GO-015, 016 Workflow: MEM-WF-11, 13

Requirements:

Provide approved visualisations such as:

- Members by Type.
- Members by Location.
- Members by Giving Status.
- Member growth over time.
- Members by Data Source.

Acceptance Criteria:

- Visualisations reflect authorised member data.
- Displayed counts use approved underlying definitions.

### MEM-F-058 – Member Data Completeness

Classification: Proposed Enhancement Goal: MEM-GO-019 Workflow: MEM-WF-08, 09

Requirements:

1. Identify missing information using approved field-completeness rules.
2. Present completeness indicators to authorised users.
3. Provide navigation to existing editing functions.

Acceptance Criteria:

- Missing required data is identified consistently.
- Corrected fields update relevant completeness indicators.

### MEM-F-059 – Combined Filter and Export Consistency

Classification: To-Be Goal: MEM-GO-016, 017 Workflow: MEM-WF-13, 14

Requirements:

1. Support approved filter combinations.
2. Display the active filter criteria.
3. Apply the same criteria to exported records.
4. Keep export data within the user's authorised scope.

Acceptance Criteria:

- Filtered exports correspond to the applicable member results.
- Clearing filters restores the appropriate authorised list.

## 3.9 Tenant Configuration and Security

### MEM-F-060 – Existing Role-Based Permissions

Classification: As-Is + Enhancement Goal: MEM-GO-020 Workflow: MEM-WF-01, 17

Requirements:

1. Reuse the existing role and permission framework.
2. Apply permissions to existing Members actions.
3. Extend action-level permissions to newly introduced capabilities.

Acceptance Criteria:

- Existing authorisation behaviour remains intact.
- New member-management actions cannot bypass existing access restrictions.

### MEM-F-061 – Tenant-Level Feature Configuration

Classification: To-Be Goal: MEM-GO-003 Workflow: MEM-WF-17

Requirements:

1. Support tenant-specific approved optional capabilities.
2. Provide a common core Members feature set.
3. Validate entitlement dependencies.
4. Apply configuration only to the intended tenant.

Acceptance Criteria:

- Eligible optional capabilities can differ between tenants.
- A tenant cannot enable unavailable or unauthorised capabilities.

### MEM-F-062 – Tenant-Specific Member Fields

Classification: Proposed Enhancement Goal: MEM-GO-003, 006 Workflow: MEM-WF-02, 17

Requirements:

1. Support approved tenant-specific additional fields.
2. Define data type, applicability and validation.
3. Preserve standard mandatory identity requirements.
4. Make configured fields available in relevant create/edit workflows.

Acceptance Criteria:

- Approved fields appear for the correct tenant.
- Custom field configuration does not compromise shared member identity rules.

### MEM-F-063 – Import and Export Permissions

Classification: To-Be Extension of Existing Permissions Goal: MEM-GO-020 Workflow: MEM-WF-05, 14, 17

Requirements:

1. Control Import Members permission.
2. Control export eligibility.
3. Control import correction and duplicate-review permissions.
4. Apply server-side authorisation to material actions.

Acceptance Criteria:

- Unauthorised users cannot execute restricted import/export operations.
- Permission restrictions remain effective regardless of UI visibility.

### MEM-F-064 – Tenant Data Isolation

Classification: Confirmed Standalone Requirement Goal: MEM-GO-001 Workflow: MEM-WF-01, 17

Requirements:

Apply tenant isolation to:

- Members.
- Member profiles.
- Imported records.
- Integration mappings.
- KPI data.
- Exports.
- Duplicate reviews.
- Audit information.

Acceptance Criteria:

- Cross-tenant records cannot be read or modified without an expressly authorised platform operation.
- Ordinary tenant users cannot search or export another tenant's members.

### MEM-F-065 – Member Privacy Preferences

Classification: As-Is + Enhancement Goal: MEM-GO-020 Workflow: MEM-WF-02, 09

Requirements:

1. Retain Anonymous Donor and Do Not Solicit values.
2. Preserve these values during edit/import/integration processing according to approved data rules.
3. Expose preferences only to authorised dependent capabilities.

Acceptance Criteria:

- Preferences are retained accurately.
- Member updates do not unintentionally clear existing preferences.
- Communication-execution rules remain governed by the relevant communications capability.

### MEM-F-066 – Member Data Access Revalidation

Classification: To-Be Security Requirement Goal: MEM-GO-020 Workflow: MEM-WF-01, 17

Requirements:

1. Validate access to the specific member record.
2. Revalidate material write operations.
3. Apply the same checks to direct record access and permitted exports.

Acceptance Criteria:

- Unauthorised record access is denied.
- A stale or unauthorised screen does not permit restricted updates.

## 3.10 Audit, Reliability and Consistency

### MEM-F-067 – Member Activity Audit

Classification: To-Be Goal: MEM-GO-023 Workflow: MEM-WF-18

Requirements:

Track material events, including:

- Member creation.
- Member updates.
- Administrative status changes.
- Import processing.
- Duplicate decisions.
- Controlled merge/update.
- Export activity.

Acceptance Criteria:

\- Relevant actor/source, record and outcome information is available for authorised audit review.

### MEM-F-068 – Member Update Conflict Handling

Classification: To-Be Goal: MEM-GO-011 Workflow: MEM-WF-09, 18

Requirements:

1. Identify conflicting updates where relevant.
2. Prevent unapproved overwrites.
3. Preserve the authoritative committed record until an approved resolution.
4. Record applicable outcomes.

Acceptance Criteria:

- Conflicting updates do not silently replace existing data.
- Failed or rejected operations do not incorrectly change the member profile.

### MEM-F-069 – Integration Failure Handling

Classification: To-Be Goal: MEM-GO-004, 012 Workflow: MEM-WF-04, 18

Requirements:

1. Identify failed integration processing.
2. Preserve previously committed member information.
3. Provide relevant processing/error status.
4. Support authorised investigation and subsequent correction or reprocessing.

Acceptance Criteria:

- A failed integration does not corrupt current member data.
- Processing errors are distinguishable from successful ingestion.

### MEM-F-070 – Consistent Member Record Identity

Classification: To-Be Goal: MEM-GO-010, 021 Workflow: MEM-WF-04, 06, 16

Requirements:

1. Maintain a stable member identifier.
2. Use member references across the relevant Donors and Donations capabilities.
3. Preserve record relationships during authorised updates or merges.
4. Prevent ambiguous cross-member associations.

Acceptance Criteria:

- Every donor resolves to an existing member.
- Approved member corrections do not unintentionally break donation references.

### MEM-F-071 – Automatic KPI Recalculation

Classification: Confirmed To-Be Goal: MEM-GO-024 Workflow: MEM-WF-15

Requirements:

Recalculate affected KPIs after committed:

- Member creation.
- Member updates.
- Successful imports.
- Applicable integration updates.
- Approved duplicate merges.
- Relevant member-status changes.

Acceptance Criteria:

- Affected KPI values reflect successfully committed data.
- Rejected and pending records do not distort KPI counts.
- Users are not required to manually initiate recalculation.

### MEM-F-072 – Data Change and Display Consistency

Classification: To-Be Goal: MEM-GO-005, 024 Workflow: MEM-WF-15, 18

Requirements:

1. Maintain consistency between member data, list results, profiles and KPI summaries.
2. Refresh displayed values following successful changes.
3. Respect current tenant scope and applied filters.
4. Prevent display-only refresh operations from creating new records.

Acceptance Criteria:

- Successfully committed changes become available across relevant views.
- Member counts and summaries use the applicable authoritative records.
- Refreshing the page does not duplicate transactions or imports.

## 4. Member Field Catalogue

This section consolidates the fields currently identified from the existing application and walkthrough.

Final mandatory indicators, field-length limits, type-dependent rules and dropdown data sources require field-level validation against the running application.

| Section       | Field                                  | As-Is / To-Be                             |
| ------------- | -------------------------------------- | ----------------------------------------- |
| Contact       | Donor Type                             | As-Is                                     |
| Contact       | Title                                  | As-Is                                     |
| Contact       | First Name                             | As-Is                                     |
| Contact       | Last Name                              | As-Is                                     |
| Contact       | Email                                  | As-Is                                     |
| Contact       | Mobile Phone                           | As-Is                                     |
| Contact       | Home Phone                             | As-Is                                     |
| Contact       | Business Phone                         | As-Is                                     |
| Contact       | Organisation / Foundation Display Name | Proposed To-Be                            |
| Address       | Address                                | As-Is                                     |
| Address       | ZIP/Postal Code                        | As-Is                                     |
| Address       | State                                  | As-Is                                     |
| Address       | City                                   | As-Is                                     |
| Address       | Country                                | Proposed To-Be                            |
| Communication | Anonymous Donor                        | As-Is                                     |
| Communication | Do Not Solicit                         | As-Is                                     |
| Campaign      | Current Campaign                       | As-Is                                     |
| Campaign      | Current Solicitor                      | As-Is                                     |
| Giving        | Giving Status                          | As-Is, standardised To-Be                 |
| Giving        | Pledged Amount                         | As-Is                                     |
| Recognition   | Donor Publication                      | As-Is                                     |
| Recognition   | Spouse Last Name                       | As-Is                                     |
| Recognition   | Spouse Middle Name                     | As-Is                                     |
| Recognition   | Alternate Phone 1                      | As-Is                                     |
| Recognition   | Alternate Phone Type 1                 | As-Is                                     |
| Recognition   | Alternate Phone 2                      | As-Is                                     |
| Advanced      | iWave Score                            | As-Is                                     |
| Advanced      | Capacity Score                         | As-Is                                     |
| Advanced      | Propensity Score                       | As-Is                                     |
| Advanced      | Affinity Score                         | As-Is                                     |
| Advanced      | Profile URL                            | As-Is                                     |
| Advanced      | First Guest Name                       | As-Is                                     |
| Advanced      | Second Guest Name                      | As-Is                                     |
| Advanced      | Previous Home Number                   | As-Is                                     |
| Advanced      | Alternate Phone Type 2                 | As-Is                                     |
| System        | Administrative Status                  | To-Be                                     |
| System        | Member ID                              | Existing identity; governance enhancement |
| System        | Data Source                            | To-Be provenance enhancement              |
| System        | Source Reference                       | To-Be                                     |
| System        | Created Date                           | As-Is                                     |
| System        | Last Modified Date                     | To-Be visibility enhancement              |
| System        | Import Batch Reference                 | To-Be                                     |

Field applicability rule: Individual, Organisation and Foundation records may have different identity requirements. A universal mandatory-field policy for all three types should not be assumed without approval.

## 5. Member Status Definitions

## 5.1 Administrative Status

| Status   | Definition                              | List Behaviour                                         |
| -------- | --------------------------------------- | ------------------------------------------------------ |
| Active   | Administratively active member record   | Included in default Members list                       |
| Inactive | Administratively inactive member record | Excluded from default list; accessible when authorised |

## 5.2 Giving Status

| Status   | Business Meaning                                                                        |
| -------- | --------------------------------------------------------------------------------------- |
| Prospect | Member identified as a potential contributor without a qualifying recorded donation     |
| Pledged  | Member with a qualifying pledge or commitment                                           |
| Donated  | Member with qualifying recorded donation activity                                       |
| Lapsed   | Member whose qualifying giving activity has ceased according to approved lapse criteria |

The values are confirmed. The exact qualification, priority and automatic transition rules require approval.

A member's Giving Status must not be used as a substitute for Administrative Status.

A confirmed donor relationship is derived from qualifying donation activity linked to an existing member, rather than merely from an editable status label.

## 6. Data Source and Import Rules

## 6.1 Supported Source Methods

| Source               | Existing / New | Member Creation                  |
| -------------------- | -------------- | -------------------------------- |
| Manual Entry         | Existing       | Direct Add Member form           |
| External Integration | Existing       | Supported integration processing |
| Excel Import         | To-Be          | Template-based processing        |
| CSV Import           | To-Be          | Template-based processing        |

All source methods feed the same tenant-level Members register.

## 6.2 Import Outcome Rules

| Outcome        | Included in Import Success? | Member Register Effect                       |
| -------------- | --------------------------- | -------------------------------------------- |
| Created        | Yes                         | New member committed                         |
| Updated        | Yes                         | Existing member updated under approved rules |
| Rejected       | No                          | No committed change                          |
| Pending Review | No                          | Waits for authorised resolution              |
| Skipped        | No                          | No committed change                          |

Counts for successfully imported rows and net changes to Total Members may differ because updating an existing member does not create an additional member.

## 6.3 Duplicate Handling Rules

| Condition                               | Expected Behaviour                                           |
| --------------------------------------- | ------------------------------------------------------------ |
| No potential existing match             | Create when validation passes                                |
| Potential match, no conflict            | Apply approved matching/update policy                        |
| Conflicting existing values             | Hold for administrator review                                |
| Administrator approves update           | Modify existing member without creating a duplicate          |
| Administrator approves merge            | Merge according to approved identity-preservation rules      |
| Administrator rejects change            | Preserve existing member data                                |
| Administrator confirms distinct members | Retain separate identities, subject to applicable validation |

Exact matching keys, thresholds, conflict precedence and merge handling must be documented before implementation.

## 7. KPI Feature Catalogue

## 7.1 Existing KPI Baseline

| KPI              | Existing State          | To-Be Requirement                    |
| ---------------- | ----------------------- | ------------------------------------ |
| Total Members    | Calculation implemented | Preserve formula, support drill-down |
| Conversion Ready | Calculation implemented | Preserve formula, support drill-down |
| Email Verified   | Calculation implemented | Preserve formula, support drill-down |
| Phone Verified   | Calculation implemented | Preserve formula, support drill-down |

## 7.2 Recommended Additional KPIs

| KPI                             | Proposed Calculation Basis                                                              |
| ------------------------------- | --------------------------------------------------------------------------------------- |
| Active Members                  | Members with Administrative Status = Active                                             |
| New Members                     | Members created during the selected period                                              |
| Members by Type                 | Count by constituent type                                                               |
| Members by Location             | Count by approved geographic dimension                                                  |
| Members by Source               | Count by approved source-attribution logic                                              |
| Members with Pledges            | Distinct members meeting the approved pledge criteria                                   |
| Member-to-Donor Conversion Rate | Qualifying members who became donors divided by the approved eligible member population |
| Data Completeness               | Approved populated fields against applicable expected fields                            |
| Pending Duplicate Reviews       | Unresolved duplicate review cases                                                       |

These proposed definitions are a starting point. The calculation unit, applicable data population, reporting period, rounding and treatment of missing information must be approved.

## 7.3 KPI Calculation and Refresh Rules

1. Existing KPI calculation logic must be reused.
2. New KPIs must have approved definitions and authoritative data sources.
3. A KPI click must resolve its supporting records where a record-level drill-down is meaningful.
4. Successful import changes must automatically update affected measures.
5. Rejected import rows must not influence committed-record KPIs.
6. A member update may change a KPI without increasing Total Members.
7. Dashboard figures and filtered member records must use consistent scopes.

## 8. Goals-to-Workflow-to-Feature Traceability

The feature ranges below link the revised catalogue to the 25 Goals and 18 Workflows.

| Goal       | Workflow(s)           | Feature IDs                 |
| ---------- | --------------------- | --------------------------- |
| MEM-GO-001 | MEM-WF-01, 17         | 001, 060, 064               |
| MEM-GO-002 | MEM-WF-01, 17         | 001, 061                    |
| MEM-GO-003 | MEM-WF-17             | 034, 054, 061, 062          |
| MEM-GO-004 | MEM-WF-02, 04, 05     | 016, 023, 025–029           |
| MEM-GO-005 | MEM-WF-01, 04, 07, 08 | 001–009, 019, 020, 023, 072 |
| MEM-GO-006 | MEM-WF-02, 03, 09     | 010–018, 062                |
| MEM-GO-007 | MEM-WF-05             | 025–029, 044, 046           |
| MEM-GO-008 | MEM-WF-05             | 028, 044, 045               |
| MEM-GO-009 | MEM-WF-05             | 030, 031, 047, 049, 050     |
| MEM-GO-010 | MEM-WF-06             | 040–042, 048, 070           |
| MEM-GO-011 | MEM-WF-06, 09         | 018, 031, 041, 042, 068     |
| MEM-GO-012 | MEM-WF-04, 08         | 023, 043, 069               |
| MEM-GO-013 | MEM-WF-07             | 002–007                     |
| MEM-GO-014 | MEM-WF-11, 12         | 033, 052, 055               |
| MEM-GO-015 | MEM-WF-11             | 034, 053, 054, 057          |
| MEM-GO-016 | MEM-WF-13             | 035, 057, 059               |
| MEM-GO-017 | MEM-WF-14             | 024, 036, 059, 063          |
| MEM-GO-018 | MEM-WF-07, 08         | 003, 020, 056               |
| MEM-GO-019 | MEM-WF-08, 09         | 018, 020, 031, 058          |
| MEM-GO-020 | MEM-WF-01, 17         | 060, 063–066                |
| MEM-GO-021 | MEM-WF-16             | 021, 022, 039, 042, 070     |
| MEM-GO-022 | MEM-WF-16             | 021, 022, 039               |
| MEM-GO-023 | MEM-WF-18             | 041, 050, 067–069           |
| MEM-GO-024 | MEM-WF-15             | 032, 051, 071, 072          |
| MEM-GO-025 | MEM-WF-02, 10         | 013, 016, 037, 038          |

Feature IDs in this table omit the `MEM-F-` prefix for readability.

## 9. Workflow-to-Feature Mapping

| Workflow                          | Feature Coverage                                             |
| --------------------------------- | ------------------------------------------------------------ |
| MEM-WF-01 – Members Overview      | 001–009, 060, 064                                            |
| MEM-WF-02 – Manual Creation       | 010–016, 040, 062                                            |
| MEM-WF-03 – Draft Handling        | 010–016; dedicated draft feature pending confirmed lifecycle |
| MEM-WF-04 – Integration Ingestion | 023, 040, 043, 069, 070                                      |
| MEM-WF-05 – Bulk Import           | 025–031, 044–051                                             |
| MEM-WF-06 – Duplicate Resolution  | 040–042, 048, 070                                            |
| MEM-WF-07 – Search and Filter     | 002–007, 035, 056                                            |
| MEM-WF-08 – Member Profile        | 019, 020, 043, 058                                           |
| MEM-WF-09 – Edit Member           | 011–015, 017, 018, 031, 068                                  |
| MEM-WF-10 – Member Status         | 007, 013, 037, 038                                           |
| MEM-WF-11 – KPI Configuration     | 034, 052–054, 057                                            |
| MEM-WF-12 – KPI Drill-Down        | 033, 055                                                     |
| MEM-WF-13 – Advanced Filtering    | 035, 057–059                                                 |
| MEM-WF-14 – Export                | 024, 036, 059, 063                                           |
| MEM-WF-15 – Refresh               | 032, 051, 071, 072                                           |
| MEM-WF-16 – Donation Handoff      | 021, 022, 039, 070                                           |
| MEM-WF-17 – Tenant Configuration  | 001, 034, 054, 060–066                                       |
| MEM-WF-18 – Audit and Exceptions  | 041, 050, 067–072                                            |

Coverage note: Save Draft is visible in the existing UI, but its detailed persistence and resume rules remain unconfirmed. A dedicated feature definition and acceptance criteria must be added once those rules are approved.

## 10. Business and Technical Dependencies

| Dependency                              | Feature Impact                                      |
| --------------------------------------- | --------------------------------------------------- |
| Existing Authentication and Permissions | Members access and privileged actions               |
| Tenant Management                       | Isolation, configuration, feature entitlements      |
| Members Data Management                 | Identity, registration, updating and matching       |
| External Integrations                   | Member ingestion and source information             |
| Import Processing                       | Excel/CSV validation and processing                 |
| Campaign Management                     | Campaign references and relevant member data        |
| Donations                               | Member-linked donation records and giving summaries |
| KPI/Reporting                           | Existing and additional calculation definitions     |
| File Handling                           | Import upload and result processing                 |
| Export Processing                       | Authorised CSV extraction                           |
| Audit                                   | Material changes, imports, conflicts and exports    |

The table describes business and functional dependencies and does not mandate a particular implementation architecture.

## 11. Security and Governance Requirements

All Members features must comply with the following requirements:

1. Tenant data must remain isolated.
2. Existing application roles and permissions must be reused.
3. New privileged actions must integrate with existing permission controls.
4. Cross-tenant record access must be prevented.
5. Conflicting member updates require administrator review.
6. Member imports must validate incoming information.
7. Sensitive exports must be permission-controlled.
8. Significant member changes must be auditable.
9. Donor records must reference existing members.
10. Member information must not be modified through unauthorised integrations or imports.
11. Anonymous Donor and Do Not Solicit preferences must be preserved appropriately.
12. Tenant-specific configuration cannot override mandatory platform security controls.

## 12. Open Business Decisions

Confirmed business rules have been removed from the unresolved-decision list.

| ID         | Decision to Finalise                                                          |
| ---------- | ----------------------------------------------------------------------------- |
| MEM-OD-003 | Mandatory fields and member-type-specific validations                         |
| MEM-OD-004 | Organisation and Foundation identity fields                                   |
| MEM-OD-005 | Approved import templates and supported versions                              |
| MEM-OD-006 | Duplicate matching identifiers, non-conflicting update policy and merge rules |
| MEM-OD-007 | Integration source precedence and reconciliation                              |
| MEM-OD-009 | Exact existing KPI formula documentation and new KPI definitions              |
| MEM-OD-010 | KPI and filter combination/reset behaviour                                    |
| MEM-OD-011 | Additional KPI selection and configuration persistence                        |
| MEM-OD-012 | Full additional filter and export-column catalogue                            |
| MEM-OD-013 | Reporting-period and currency rules                                           |
| MEM-OD-014 | Save Draft persistence and resume behaviour                                   |
| MEM-OD-015 | Donation-entry preselection and qualifying-donation status transitions        |
| MEM-OD-016 | Tenant-specific field configuration limits                                    |
| MEM-OD-017 | Optional-feature entitlement and dependency rules                             |
| MEM-OD-018 | Data retention and audit visibility                                           |
| MEM-OD-019 | Import volume, performance and failure-recovery requirements                  |

These are detailed product decisions, not unresolved questions about the approved standalone product direction.

## 13. Feature Acceptance Summary

The Members capability satisfies the target business requirements when:

- Existing manual creation, listing, profile, editing and donation navigation continue functioning.
- Tenants can access only their authorised member data.
- Administrators can import member data using approved templates.
- Imported data undergoes validation and duplicate detection.
- Conflicting records require administrator review before updates or merges.
- Import results accurately distinguish successful and unsuccessful rows.
- Every donor remains associated with an existing member.
- Administrative Status and Giving Status remain separate.
- Existing KPI calculations continue to operate.
- Additional KPIs use approved calculation definitions.
- KPI cards support relevant record drill-downs.
- Successful imports automatically update affected KPI figures.
- Advanced filters and filtered exports return the correct authorised dataset.
- Member creation, updating and reconciliation preserve appropriate audit evidence.
- Approved tenant-specific settings and optional capabilities are supported.

## 14. Product Management Validation Summary

| Review Area                  | Validation Result                                                                                  |
| ---------------------------- | -------------------------------------------------------------------------------------------------- |
| Original Feature Catalogue   | Reviewed and retained 36 original feature IDs                                                      |
| New Requirements             | Added 36 features to cover expanded standalone requirements                                        |
| Total Feature Definitions    | 72                                                                                                 |
| Members Goals                | Aligned with MEM-GO-001–025                                                                        |
| Members Workflows            | Aligned with MEM-WF-01–18                                                                          |
| Member–Donor Relationship    | Confirmed and incorporated                                                                         |
| Administrative/Giving Status | Separate attributes incorporated                                                                   |
| Duplicate Resolution         | Administrator-controlled conflicting updates                                                       |
| Existing Permissions         | Correctly retained as As-Is                                                                        |
| KPI Calculations             | Existing calculation framework retained                                                            |
| Import KPI Updates           | Automatic post-commit update incorporated                                                          |
| Optional Tenant Features     | Corrected from the original identical-feature-set assumption                                       |
| Member Import                | Validation, reconciliation, outcomes and correction covered                                        |
| Filtered Export              | Included                                                                                           |
| Supporting Flowcharts        | Not included unnecessarily; behaviour defined through feature requirements and acceptance criteria |
| Remaining Decisions          | Detailed implementation/business-policy definitions identified                                     |

## 15. Document Conclusion

This Feature Catalogue defines the functional requirements for extending the existing AiXPurpose Members capability into a standalone, configurable, multi-tenant application.

It preserves existing member-management functionality while introducing structured bulk imports, controlled identity reconciliation, separate administrative and giving statuses, configurable KPIs, advanced filtering, filtered exports, automatic KPI updates and tenant-level governance.

The 72 identified features provide the functional baseline for downstream user stories, technical specifications, implementation planning and QA/UAT.

Recommended enhancements and unresolved business-policy details remain explicitly identified so they can be approved without changing the confirmed core requirements.

This document is ready for business review and detailed feature-level clarification before final implementation sign-off.
