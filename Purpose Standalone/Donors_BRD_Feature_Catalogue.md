# AiXPurpose – Donor Management – Donors

> **Document type:** Business Requirements Document – Feature Catalogue

## Document Control

| Field              | Details                                                                                              |
| ------------------ | ---------------------------------------------------------------------------------------------------- |
| Document Name      | AiXPurpose – Donors – Feature Catalogue                                                              |
| Product            | AiXPurpose                                                                                           |
| Application Type   | Standalone, Multi-Tenant Application                                                                 |
| Module             | Donor Management                                                                                     |
| Page               | Donors                                                                                               |
| Document Type      | Business Requirements Document – Feature Catalogue                                                   |
| Version            | 1.0                                                                                                  |
| Status             | Draft for Business Review                                                                            |
| Related Goals      | AiXPurpose – Donors – Goals v1.0                                                                     |
| Related Workflow   | AiXPurpose – Donors – Workflow v1.0                                                                  |
| Related Module     | AiXPurpose – Members                                                                                 |
| Feature ID Format  | DON-F-###                                                                                            |
| Requirement Source | Existing application, Donors screenshots, approved business requirements and standalone enhancements |

## Overview

This document specifies the functional features, validations, and acceptance criteria for the Donors capability, with traceability to the related Goals and Workflow documents.

## Contents

- [1. Feature Catalogue Purpose](#1-feature-catalogue-purpose)
- [2. Feature Catalogue Summary](#2-feature-catalogue-summary)
- [3. Detailed Feature Catalogue](#3-detailed-feature-catalogue)
- [3.1 Tenant Access and Navigation](#31-tenant-access-and-navigation)
- [3.2 Donor Listing and Search](#32-donor-listing-and-search)
- [3.3 Donor Profile and Scoring](#33-donor-profile-and-scoring)
- [3.4 Donation Entry and Member Selection](#34-donation-entry-and-member-selection)
- [3.5 Export and Integration](#35-export-and-integration)
- [3.6 KPIs and Tier Configuration](#36-kpis-and-tier-configuration)
- [3.7 Donor Bulk Import](#37-donor-bulk-import)
- [3.8 Member–Donor Identity and Transactions](#38-memberdonor-identity-and-transactions)
- [3.9 Import Validation and Reconciliation](#39-import-validation-and-reconciliation)
- [3.10 Donor Tier, KPI and Reporting Enhancements](#310-donor-tier-kpi-and-reporting-enhancements)
- [3.11 Tenant Configuration and Security](#311-tenant-configuration-and-security)
- [3.12 Data Consistency, Audit and Reliability](#312-data-consistency-audit-and-reliability)
- [4. Donation Entry Field Catalogue](#4-donation-entry-field-catalogue)
- [4.1 Donation Form Validation Matrix](#41-donation-form-validation-matrix)
- [5. Donors List and Profile Matrix](#5-donors-list-and-profile-matrix)
- [6. Member–Donor Business Rules](#6-memberdonor-business-rules)
- [6.1 Status Alignment](#61-status-alignment)
- [7. Import and Reconciliation Matrix](#7-import-and-reconciliation-matrix)
- [7.1 Import Result Definitions](#71-import-result-definitions)
- [7.2 Transaction Matching Principles](#72-transaction-matching-principles)
- [8. KPI Feature Catalogue](#8-kpi-feature-catalogue)
- [8.1 Existing KPIs](#81-existing-kpis)
- [8.2 Additional KPI Candidates](#82-additional-kpi-candidates)
- [8.3 KPI Synchronisation Rules](#83-kpi-synchronisation-rules)
- [9. Goals-to-Feature Traceability](#9-goals-to-feature-traceability)
- [10. Workflow-to-Feature Mapping](#10-workflow-to-feature-mapping)
- [11. Dependencies and Boundaries](#11-dependencies-and-boundaries)
- [12. Open Business Decisions](#12-open-business-decisions)
- [13. Acceptance and QA Coverage](#13-acceptance-and-qa-coverage)
- [14. Product Management Validation Summary](#14-product-management-validation-summary)
- [15. Document Conclusion](#15-document-conclusion)

## 1. Feature Catalogue Purpose

This document defines the functional capabilities of the Donors page within standalone AiXPurpose.

It translates the approved Donors BRD Goals and Workflow into detailed feature requirements, including expected functionality, validations, business outcomes and acceptance criteria.

The catalogue covers:

- Existing Donors functionality to be retained.
- Enhancements required for standalone operation.
- New donor-management features.
- Member-linked donation recording.
- Donor classification and scoring.
- Bulk imports and integrations.
- Duplicate detection and reconciliation.
- KPI configuration, filtering and reporting.
- Tenant configuration, security and auditability.
- Traceability between Goals, Workflows and Features.

This catalogue does not replace the independent feature specifications for Members, Campaigns, Donations, Communications or other AiXPurpose capabilities.

### 1.1 Feature Classification

| Classification      | Definition                                              |
| ------------------- | ------------------------------------------------------- |
| As-Is               | Existing application functionality to retain            |
| As-Is + Enhancement | Existing functionality requiring additional capability  |
| To-Be               | Required standalone product functionality               |
| Proposed            | Recommended additional functionality requiring approval |

A visible screenshot control confirms the presence of the UI element, not necessarily its complete backend behaviour.

### 1.2 Requirements Traceability

| Identifier | Description                   |
| ---------- | ----------------------------- |
| DON-GO-### | Donors Business Goal          |
| DON-BR-### | Donors Business Rule          |
| DON-WF-##  | Donors Workflow               |
| DON-F-###  | Donors Feature                |
| DON-OD-### | Outstanding Business Decision |
| DON-SC-### | Business Success Criterion    |

All features inherit the applicable tenant isolation and existing role-permission requirements.

## 2. Feature Catalogue Summary

The original document defines 35 features. These identifiers have been retained, and additional features have been included to cover the 26 Goals and 22 Workflows established in the revised documentation.

| Feature Range | Functional Area                         | Count |
| ------------- | --------------------------------------- | ----- |
| DON-F-001–003 | Tenant Access and Navigation            | 3     |
| DON-F-004–011 | Donor Listing and Search                | 8     |
| DON-F-012–017 | Donor Profile and Scoring               | 6     |
| DON-F-018–026 | Donation Entry and Member Selection     | 9     |
| DON-F-027–028 | Export and Integration                  | 2     |
| DON-F-029–031 | KPIs and Tier Configuration             | 3     |
| DON-F-032–034 | Donor Bulk Import                       | 3     |
| DON-F-035     | Enhanced Filtering and Export           | 1     |
| DON-F-036–042 | Member–Donor Identity and Transactions  | 7     |
| DON-F-043–050 | Import Validation and Reconciliation    | 8     |
| DON-F-051–059 | Tier, KPI and Reporting Enhancements    | 9     |
| DON-F-060–065 | Tenant Configuration and Security       | 6     |
| DON-F-066–072 | Data Consistency, Audit and Reliability | 7     |
| Total         |                                         | 72    |

Existing IDs remain stable. Additional features begin at `DON-F-036`.

## 3. Detailed Feature Catalogue

## 3.1 Tenant Access and Navigation

### DON-F-001 – Tenant-Scoped Donors Access

Classification: As-Is + Enhancement Goals: DON-GO-001, 002, 024 Workflow: DON-WF-01, 20 Rules: DON-BR-001, 003, 005

Functional Requirements:

1. Users must access Donors within their authenticated tenant workspace.
2. The system must load only authorised donor information.
3. Existing role-based permissions must govern page access.
4. Cross-tenant donor information must not be accessible.
5. Approved optional capabilities must follow tenant configuration.

Acceptance Criteria:

- Authorised users can access their organisation's Donors page.
- Users cannot retrieve another organisation's donor records.
- Unauthorised access is denied.

### DON-F-002 – Donors Page Navigation

Classification: As-Is Goals: DON-GO-002, 014 Workflow: DON-WF-01

Functional Requirements:

1. Donors must be accessible through Donor Management → Donors.
2. The page must display the existing overview KPIs.
3. The default tier selection must be All.
4. Existing page actions must remain available according to permissions.

Acceptance Criteria:

- Navigating to Donors opens the correct page.
- All is the default tier selection.
- Existing KPI cards and donor records are displayed.

### DON-F-003 – Shared Application Header

Classification: As-Is Workflow: DON-WF-01

Functional Requirements:

Retain:

- Search Everything.
- Notifications.
- User profile.
- Sign-out.
- AI Copilot entry point.

Acceptance Criteria:

- Shared application controls remain accessible.
- Global search and related functions respect existing permissions.
- Donors enhancements do not disrupt shared application functionality.

## 3.2 Donor Listing and Search

### DON-F-004 – Donors Table Presentation

Classification: As-Is + Enhancement Goals: DON-GO-002, 017, 026 Workflow: DON-WF-01, 02

Functional Requirements:

Retain the following columns:

| Column      | Description                                   |
| ----------- | --------------------------------------------- |
| Selection   | Donor record checkbox                         |
| Donor       | Donor name and available identity information |
| Type        | Individual, Organisation or Foundation        |
| Tier        | Platinum, Gold, Silver or Bronze              |
| Total Given | Relevant qualifying giving amount             |
| Last Gift   | Most recent eligible contribution             |
| Status      | Existing donor status                         |
| Actions     | Three-dot record action                       |

The displayed values must reflect the applicable authorised dataset and approved calculation definitions.

Acceptance Criteria:

- Required columns are displayed.
- Each row represents the correct donor record.
- Giving summaries remain consistent with the donor profile.

### DON-F-005 – Search Donors

Classification: As-Is Goals: DON-GO-017 Workflow: DON-WF-02

Functional Requirements:

1. Support search by donor name, email or tier, as indicated in the existing UI.
2. Search only authorised tenant data.
3. Allow search with applicable filters.
4. Display an empty state when no records match.

Acceptance Criteria:

- Searching returns matching donors.
- Search does not expose another tenant's records.
- Clearing search restores the applicable list view.

### DON-F-006 – Quick Donor Tier Filters

Classification: As-Is + Enhancement Goals: DON-GO-011, 012, 017 Workflow: DON-WF-02, 12 Rules: DON-BR-016, 017

Functional Requirements:

Provide tier options:

- All.
- Platinum.
- Gold.
- Silver.
- Bronze.

The standalone application must use approved tenant-specific classification rules when calculating donor tiers.

Acceptance Criteria:

- All is selected by default.
- Selecting Gold displays matching Gold-tier records.
- Tier filtering reflects the tenant's approved classifications.

### DON-F-007 – Advanced Filter Drawer

Classification: As-Is Goals: DON-GO-017 Workflow: DON-WF-03

Functional Requirements:

Provide the existing Advanced Filters interface containing:

- Minimum Donation Amount.
- Maximum Donation Amount.
- Donor Score range.
- Engagement Segments.
- Apply Filters.
- Clear All.

Acceptance Criteria:

- Advanced opens the filter interface.
- Existing controls remain available.
- Applied criteria affect donor results.

### DON-F-008 – Engagement Segment Filters

Classification: As-Is + Enhancement Goals: DON-GO-017 Workflow: DON-WF-03

Functional Requirements:

Retain:

| Segment         | Intended Purpose                                         |
| --------------- | -------------------------------------------------------- |
| New Donors      | Identify recently acquired donors                        |
| Lapsing         | Identify donors meeting approved lapse criteria          |
| Major Prospects | Identify high-potential prospective contributors         |
| Monthly Donors  | Identify donors meeting approved monthly-giving criteria |

The system must reuse existing segment logic unless explicitly revised.

Acceptance Criteria:

- Existing engagement segments remain selectable.
- Segment results use the applicable established definitions.
- Segment filtering does not incorrectly convert prospects into qualifying donors.

### DON-F-009 – Apply and Clear Filters

Classification: As-Is + Enhancement Goals: DON-GO-017 Workflow: DON-WF-03

Functional Requirements:

1. Apply selected advanced-filter criteria.
2. Support compatible filter combinations.
3. Clear selected advanced filters.
4. Preserve unrelated criteria according to the approved reset behaviour.

Acceptance Criteria:

- Apply Filters updates the displayed donor population.
- Clear All removes the applicable advanced-filter selections.
- Invalid filter ranges cannot produce misleading results.

### DON-F-010 – Donor Row Selection

Classification: As-Is Goals: DON-GO-017 Workflow: DON-WF-02

Functional Requirements:

1. Retain donor selection checkboxes.
2. Allow individual row selection.
3. Retain the existing header selection control.
4. Define bulk actions separately when approved.

Acceptance Criteria:

- Users can select and deselect donor rows.
- Selection does not trigger an unintended donation or record modification.
- Bulk operations are not assumed solely because checkboxes are visible.

### DON-F-011 – Open Donor Details

Classification: As-Is Goals: DON-GO-026 Workflow: DON-WF-04 Rules: DON-BR-018

Functional Requirements:

1. Clicking a donor row must open its detail view.
2. Clicking the corresponding three-dot action must open the same view.
3. The correct selected donor must be displayed.

Acceptance Criteria:

- Both actions open the same donor profile.
- The displayed data belongs to the selected donor.

## 3.3 Donor Profile and Scoring

### DON-F-012 – Donor Identity and Classification

Classification: As-Is + Enhancement Goals: DON-GO-006, 026 Workflow: DON-WF-04, 06

Functional Requirements:

Display:

- Donor name.
- Email.
- Phone.
- Location.
- Constituent type.
- Donor tier.
- Donor status.
- Applicable administrative and giving statuses.

Member identity and contact information must remain consistent with the corresponding Members record.

Acceptance Criteria:

- Profile identity corresponds to the linked member.
- Donor classification reflects approved business rules.
- Member changes do not create duplicate donor identities.

### DON-F-013 – Donor Score Display

Classification: As-Is + Enhancement Goals: DON-GO-013 Workflow: DON-WF-13

Functional Requirements:

1. Retain the existing Donor Score display.
2. Use the existing calculation framework.
3. Apply approved tenant-specific scoring settings where supported.
4. Display an appropriate unavailable state when a score cannot be calculated.

Acceptance Criteria:

- The correct calculated score appears.
- The score is consistent with approved scoring inputs.
- Missing score data is not automatically presented as zero.

### DON-F-014 – Giving Summary Cards

Classification: As-Is + Enhancement Goals: DON-GO-026 Workflow: DON-WF-04, 18

Functional Requirements:

Retain:

| Metric          | Business Purpose                             |
| --------------- | -------------------------------------------- |
| Lifetime Giving | Total eligible historical contribution value |
| Last Gift       | Latest qualifying contribution information   |
| Total Gifts     | Count of eligible recorded gifts             |

Eligibility rules must follow the authoritative transaction model.

Acceptance Criteria:

- Existing cards are displayed.
- Summary values reconcile with eligible giving history.
- Rejected or uncommitted transactions do not inflate the figures.

### DON-F-015 – Donor Profile Tabs

Classification: As-Is Goals: DON-GO-026 Workflow: DON-WF-04, 18, 19

Functional Requirements:

Retain:

- Overview.
- History.
- Engagement.
- Notes.

Acceptance Criteria:

- Users can navigate between tabs.
- Each tab displays the selected donor's relevant authorised information.
- Existing tab behaviour remains operational.

The specific editing behaviour within Engagement and Notes must be verified against the application.

### DON-F-016 – Donor Score Breakdown

Classification: As-Is + Enhancement Goals: DON-GO-013 Workflow: DON-WF-13

Functional Requirements:

Display the existing score components:

| Component  | Current UI |
| ---------- | ---------- |
| Value      | 40%        |
| Recency    | 30%        |
| Frequency  | 30%        |
| Engagement | Extra      |

The actual scoring algorithm must be documented from the existing implementation.

Acceptance Criteria:

- All existing score components are displayed.
- Component values correspond to the approved scoring definition.
- Displayed weights are not automatically treated as complete formulas.

### DON-F-017 – Donor Profile Actions

Classification: As-Is Goals: DON-GO-007, 026 Workflow: DON-WF-19

Functional Requirements:

Retain:

- Record Donation.
- Add Task.
- Send Message.

Acceptance Criteria:

- Existing actions remain available where authorised.
- Record Donation opens the associated donation-entry capability.
- Tasks and messaging follow their existing applicable functional boundaries.

The full communication workflow is documented separately.

## 3.4 Donation Entry and Member Selection

### DON-F-018 – Add Donor Modal

Classification: As-Is Goals: DON-GO-007 Workflow: DON-WF-05

Functional Requirements:

1. Provide Add Donor on the Donors overview.
2. Open the existing donation-entry modal.
3. Display Member Selection and Donation Details.
4. Provide Save Donation and Cancel controls.

Acceptance Criteria:

- Authorised users can open Add Donor.
- The expected form sections and controls appear.

### DON-F-019 – Existing Member Lookup

Classification: As-Is + Enhancement Goals: DON-GO-006, 007 Workflow: DON-WF-05, 06 Rules: DON-BR-006–009

Functional Requirements:

1. Select Member is mandatory.
2. Search existing members by name, email or phone.
3. Restrict results to the authorised tenant.
4. Require selection of a valid member identity.
5. Do not create an unrelated donor identity.

Acceptance Criteria:

- A valid member must be selected before donation submission.
- Cross-tenant members are unavailable.
- The saved donation references the intended existing member.

### DON-F-020 – Donation Amount

Classification: As-Is + Enhancement Goals: DON-GO-007, 008 Workflow: DON-WF-05

Functional Requirements:

1. Retain the required Donation Amount input.
2. Validate the value according to approved financial rules.
3. Apply the relevant currency and precision policy.
4. Prevent invalid values from being successfully committed.

Acceptance Criteria:

- The field is mandatory.
- Invalid values are rejected according to approved validation rules.
- The committed amount matches the accepted input.

Exact minimums, decimal precision and supported currencies remain business decisions.

### DON-F-021 – Campaign Selection

Classification: As-Is Goals: DON-GO-007, 008 Workflow: DON-WF-05 Rules: DON-BR-012

Functional Requirements:

1. Campaign is mandatory in the existing form.
2. Populate options from the Campaigns capability.
3. Save the selected campaign reference with the donation.
4. Enforce applicable tenant and campaign eligibility rules.

Acceptance Criteria:

- Available authorised campaigns can be selected.
- Invalid or cross-tenant campaign references cannot be committed.

### DON-F-022 – Payment Method Selection

Classification: As-Is + Enhancement Goals: DON-GO-007, 008 Workflow: DON-WF-05

Functional Requirements:

1. Retain mandatory Payment Method selection.
2. Support the methods approved for the tenant/application.
3. Preserve the selected method with the donation record.
4. Distinguish payment-method selection from actual payment processing.

Acceptance Criteria:

- A supported method must be selected.
- Unsupported methods cannot be submitted.
- Selecting Credit Card or UPI does not independently establish successful payment.

### DON-F-023 – Donation Date

Classification: As-Is Goals: DON-GO-007, 008 Workflow: DON-WF-05

Functional Requirements:

1. Retain mandatory Donation Date.
2. Provide the existing date-selection mechanism.
3. Validate dates according to approved business rules.
4. Preserve the relevant date with the donation.

Acceptance Criteria:

- A valid date is required.
- The saved donation retains the accepted date.

Rules for future-dated and backdated donations require confirmation.

### DON-F-024 – Donation Notes

Classification: As-Is Goals: DON-GO-007 Workflow: DON-WF-05

Functional Requirements:

1. Provide optional Notes.
2. Associate saved notes with the relevant donation.
3. Restrict note visibility and editing according to existing permissions.

Acceptance Criteria:

- A donation can be submitted without Notes.
- Entered notes remain associated with the correct donation when successfully saved.

### DON-F-025 – Save and Cancel Donation

Classification: As-Is + Enhancement Goals: DON-GO-007, 008 Workflow: DON-WF-05

Functional Requirements:

1. Save Donation submits the entered information for validation.
2. Validate member, amount, campaign, method and date.
3. Check potential duplicate transactions.
4. Commit eligible data according to the approved transaction model.
5. Cancel exits the process without submitting a new transaction.
6. Prevent repeated submission from unintentionally recording duplicates.

Acceptance Criteria:

- Valid eligible submissions can be recorded.
- Invalid submissions show applicable errors.
- Cancelling without submission does not create a donation.
- A conflicting donation is not silently committed as an additional gift.

Payment gateway processing is not assumed.

### DON-F-026 – Record Donation from Profile

Classification: As-Is + Enhancement Goals: DON-GO-007, 026 Workflow: DON-WF-05, 19

Functional Requirements:

1. Retain Record Donation.
2. Launch donation entry from the selected donor context.
3. Preserve or resolve the correct existing Member ID.
4. Apply the same validation and duplicate controls as Add Donor.

Acceptance Criteria:

- Donation entry opens from the donor profile.
- A completed qualifying donation links to the intended member.
- The transaction does not create another member identity.

## 3.5 Export and Integration

### DON-F-027 – Donor CSV Export

Classification: As-Is + Enhancement Goals: DON-GO-018 Workflow: DON-WF-16

Functional Requirements:

1. Retain Export CSV on the Donors page.
2. Apply existing export permissions.
3. Support exports based on the current authorised filtered dataset.
4. Preserve approved field formatting.
5. Exclude unauthorised information.

Acceptance Criteria:

- Authorised users can generate a donor CSV.
- Filtered exports contain the applicable matching records.
- Export cannot disclose another tenant's data.

### DON-F-028 – Integrated Giving Records

Classification: As-Is + Enhancement Goals: DON-GO-004, 005, 023 Workflow: DON-WF-07

Functional Requirements:

1. Retain existing external donation integrations.
2. Associate incoming information with its authorised tenant.
3. Resolve the corresponding member identity.
4. Validate supported incoming donation fields.
5. Apply transaction duplicate and reconciliation controls.
6. Preserve source identifiers where available.
7. Update eligible donor summaries after successful commits.

Acceptance Criteria:

- Successfully processed integrated records appear in the correct tenant.
- Unresolved or conflicting transactions do not incorrectly inflate giving totals.
- Existing records are protected from unapproved overwrites.

## 3.6 KPIs and Tier Configuration

### DON-F-029 – Donor KPI Drill-Down

Classification: To-Be Goals: DON-GO-015 Workflow: DON-WF-15

Functional Requirements:

1. Make supported KPI cards interactive.
2. Resolve the selected KPI's approved calculation and record criteria.
3. Display related donor records or analytical breakdowns.
4. Preserve tenant restrictions.
5. Allow users to clear the selection.

Acceptance Criteria:

- Selecting Total Donors displays qualifying supporting records.
- Selecting Retention Rate provides a meaningful supporting cohort or breakdown.
- Users can return to the default Donors view.

### DON-F-030 – Configurable KPI Selection

Classification: To-Be Goals: DON-GO-016 Workflow: DON-WF-14, 20

Functional Requirements:

1. Provide a governed list of available Donors KPIs.
2. Allow permitted users to select KPI cards.
3. Apply tenant configuration and existing permissions.
4. Retain selected measures according to the approved preference model.

Acceptance Criteria:

- Permitted KPIs can be added or removed from the display.
- Existing KPI calculations remain unchanged unless explicitly revised.
- Unauthorised measures cannot be selected.

### DON-F-031 – Organisation-Defined Donor Tiers

Classification: To-Be Goals: DON-GO-011, 012 Workflow: DON-WF-11, 12

Functional Requirements:

1. Retain Platinum, Gold, Silver and Bronze categories.
2. Permit authorised tenant configuration of approved tier criteria.
3. Support relevant thresholds, currencies and measurement periods.
4. Validate tier boundaries and conflicting settings.
5. Recalculate affected donor classifications after approved changes.

Acceptance Criteria:

- Approved tenant rules determine donor tiers.
- Different tenants may use different permitted thresholds.
- Invalid configurations are not applied.
- Tier changes remain traceable.

No unapproved monetary values are introduced as defaults.

## 3.7 Donor Bulk Import

### DON-F-032 – Donor Import Template

Classification: To-Be Goals: DON-GO-020 Workflow: DON-WF-08

Functional Requirements:

1. Provide predefined downloadable Excel/CSV templates.
2. Identify mandatory and optional columns.
3. Include the information needed to associate imported giving records with existing members.
4. Support approved template versions.
5. Provide relevant usage instructions.

Acceptance Criteria:

- Authorised users can download an approved template.
- Required columns are identifiable.
- The template supports the approved member-linking policy.

### DON-F-033 – Upload and Validate Donor File

Classification: To-Be Goals: DON-GO-020, 021 Workflow: DON-WF-08, 09

Functional Requirements:

1. Accept approved Excel/CSV files.
2. Validate file structure and required fields.
3. Validate existing member references.
4. Check potential transaction duplicates.
5. Report invalid and unresolved records.

Acceptance Criteria:

- Supported files proceed to validation.
- Invalid files cannot create donation records.
- Unresolved member associations are reported for review.

### DON-F-034 – Import Results and Review

Classification: To-Be Goals: DON-GO-020, 021 Workflow: DON-WF-08, 09

Functional Requirements:

Provide processing outcomes including:

- Created.
- Updated.
- Rejected.
- Pending Member Review.
- Pending Duplicate Review.
- Skipped, where supported.

Administrators must be able to inspect errors and initiate authorised correction.

Acceptance Criteria:

- Results distinguish successfully committed and unresolved records.
- Unique donor counts are not confused with imported transaction counts.
- Rejected rows are not included in successful import totals.

### DON-F-035 – Enhanced Filtering and Targeted Export

Classification: To-Be Goals: DON-GO-017, 018 Workflow: DON-WF-03, 16

Functional Requirements:

1. Support additional approved filtering dimensions.
2. Combine filters according to established rules.
3. Allow export of the authorised filtered donor population.
4. Apply tenant and user access restrictions.

Acceptance Criteria:

- Users can filter by available additional criteria.
- Exported records match the resolved authorised selection.
- Unauthorised data is excluded.

## 3.8 Member–Donor Identity and Transactions

### DON-F-036 – Member–Donor Identity Relationship

Classification: Confirmed To-Be Business Rule Goals: DON-GO-006, 026 Workflow: DON-WF-06 Rules: DON-BR-006–008

Functional Requirements:

1. Every donor must reference a valid existing member.
2. A member may exist without donor activity.
3. Donor information must reuse the corresponding member identity.
4. Multiple donations by the same member must not create duplicate donor identities.
5. Member and donor references must belong to the same tenant.

Acceptance Criteria:

- Every donor resolves to one valid member identity.
- Multiple qualifying gifts do not generate duplicate donor identities.
- A member without qualifying gifts is not automatically classified as a donor.

### DON-F-037 – Donor Qualification Logic

Classification: To-Be Goals: DON-GO-006, 014 Workflow: DON-WF-06

Functional Requirements:

1. Determine donor qualification using approved donation eligibility rules.
2. Recognise donor status after the first qualifying committed donation.
3. Preserve the donor's existing member identity.
4. Re-evaluate dependent classification after relevant transaction corrections.
5. Distinguish prospects from qualifying donors.

Acceptance Criteria:

- A qualifying donation establishes the donor relationship.
- A pledge alone does not establish donor qualification under the confirmed member-donor rule.
- Prospect counts do not unintentionally increase qualifying donor counts.

Exact qualifying transaction statuses remain subject to approval.

### DON-F-038 – Donation-to-Member Association

Classification: To-Be Goals: DON-GO-006, 008 Workflow: DON-WF-05, 06

Functional Requirements:

1. Store the valid Member ID against the associated donation.
2. Validate tenant ownership.
3. Maintain member association through authorised corrections.
4. Prevent donation assignment to an unrelated member.

Acceptance Criteria:

- Saved transactions reference the correct member.
- Invalid member references are rejected.
- Linked donation history is accessible through the appropriate authorised donor profile.

### DON-F-039 – Donation Transaction Identity

Classification: To-Be Goals: DON-GO-008, 009 Workflow: DON-WF-05, 07, 10

Functional Requirements:

1. Maintain a stable identity for each committed donation transaction.
2. Preserve external transaction references where supplied.
3. Distinguish transaction identity from donor/member identity.
4. Prevent repeat processing from creating unintended duplicate transactions.

Acceptance Criteria:

- One member may have multiple distinct donation transactions.
- Reprocessing the same source transaction does not automatically create another gift.
- Each committed transaction is traceable.

### DON-F-040 – Duplicate Transaction Detection

Classification: To-Be Goals: DON-GO-009 Workflow: DON-WF-10

Functional Requirements:

1. Check potential duplicates during manual entry.
2. Check integrated transactions.
3. Check file-import transactions.
4. Compare incoming records within the relevant tenant.
5. Use approved transaction identifiers and matching rules.

Acceptance Criteria:

- Potential duplicates are identified.
- Uncertain or conflicting matches are flagged.
- Duplicate checks do not expose other tenants' transactions.

### DON-F-041 – Administrator Transaction Review

Classification: To-Be Goals: DON-GO-009, 010 Workflow: DON-WF-10, 21

Functional Requirements:

1. Present conflicting existing and incoming donation information.
2. Permit review by authorised administrators.
3. Support approved resolution actions, including accept correction, reject and keep distinct.
4. Prevent conflicting overwrites before approval.
5. Record the decision and reviewer.

Acceptance Criteria:

- Conflicting transactions cannot be automatically overwritten.
- Approved decisions are applied correctly.
- Rejected changes preserve authoritative committed information.

### DON-F-042 – Transaction Status and Eligibility

Classification: To-Be, Policy Dependent Goals: DON-GO-008, 026 Workflow: DON-WF-05, 18, 21

Functional Requirements:

1. Use the authoritative transaction status from the donation-processing capability.
2. Distinguish recorded donation information from confirmed payment completion.
3. Determine which transaction statuses contribute to giving summaries.
4. Apply the same eligibility rules to donor qualification, tiers and relevant KPIs.
5. Handle historical changes under approved correction policies.

Acceptance Criteria:

- Unqualified transactions do not inflate giving totals.
- Payment Method selection is not treated as payment confirmation.
- Eligibility changes trigger appropriate recalculation.

The exact transaction-status vocabulary must be verified before implementation.

## 3.9 Import Validation and Reconciliation

### DON-F-043 – Import File Structure Validation

Classification: To-Be Goals: DON-GO-020, 021 Workflow: DON-WF-08, 09

Functional Requirements:

1. Validate supported file format.
2. Validate template version and required headers.
3. Validate file readability and applicable size limits.
4. Reject unsupported structures before committing records.

Acceptance Criteria:

- Invalid files produce an understandable error.
- No transaction is committed from a structurally rejected file.

### DON-F-044 – Import Row-Level Validation

Classification: To-Be Goals: DON-GO-021 Workflow: DON-WF-09

Functional Requirements:

Validate imported rows against approved requirements for:

- Member identity.
- Donation amount.
- Campaign.
- Payment method.
- Donation date.
- Applicable transaction references.
- Tenant association.
- Any approved additional mandatory fields.

Acceptance Criteria:

- Invalid rows are identified individually.
- Each rejected row includes a reason.
- Rejected rows do not contribute to committed totals.

### DON-F-045 – Import Member Identity Resolution

Classification: To-Be Goals: DON-GO-006, 020, 021 Workflow: DON-WF-08, 09

Functional Requirements:

1. Match incoming donor information against existing Members records.
2. Apply approved matching criteria.
3. Flag ambiguous matches.
4. Hold unmatched records for correction or member-management review.
5. Never create a qualifying donor without a valid member association.

Acceptance Criteria:

- Existing members are linked correctly.
- Ambiguous identities require review.
- Unmatched donations cannot be committed as valid donor activity.

If a new member must be created, the separate Members workflow governs that creation.

### DON-F-046 – Import Preview and Confirmation

Classification: To-Be Goals: DON-GO-020, 021 Workflow: DON-WF-08

Functional Requirements:

1. Display the expected processing outcome before commit.
2. Identify eligible, invalid, matched and conflicting records.
3. Allow authorised confirmation.
4. Allow cancellation before processing.

Acceptance Criteria:

- Users can review eligible import records.
- Cancelling before confirmation commits no donation records from that operation.

### DON-F-047 – Partial Import Processing

Classification: To-Be, Processing Policy to Approve Goals: DON-GO-021 Workflow: DON-WF-08, 09

Functional Requirements:

1. Separate eligible and ineligible rows.
2. Commit eligible records according to the approved partial-processing policy.
3. Preserve rejected and pending-review records.
4. Report accurate processing counts.

Acceptance Criteria:

- Uncommitted rows are not reported as successful.
- Eligible transactions are processed only under the approved policy.
- A failed row does not corrupt other committed transactions.

### DON-F-048 – Import Duplicate Resolution

Classification: To-Be Goals: DON-GO-009, 010, 021 Workflow: DON-WF-08, 10

Functional Requirements:

1. Check imported records against existing transactions.
2. Check duplicates within the uploaded dataset.
3. Route conflicts for administrator review.
4. Prevent repeated uploads from unintentionally duplicating giving records.
5. Apply approved corrections without creating unnecessary donor identities.

Acceptance Criteria:

- Potential duplicate transactions are identified.
- Conflicting rows remain pending until approved.
- Re-importing a file does not bypass transaction matching.

### DON-F-049 – Import Error Reporting

Classification: To-Be Goals: DON-GO-021 Workflow: DON-WF-08, 09

Functional Requirements:

Provide:

- Import batch reference.
- Row reference.
- Field or issue category.
- Error description.
- Processing status.
- Correction guidance where applicable.

Acceptance Criteria:

- Administrators can identify rejected and pending records.
- Errors support correction and reprocessing.
- Error output does not reveal unauthorised data.

### DON-F-050 – Import History and Tracking

Classification: To-Be Goals: DON-GO-021, 025 Workflow: DON-WF-08, 22

Functional Requirements:

Track:

- Import batch identity.
- Initiating user.
- Import source and template.
- Processing timestamp.
- Record counts.
- Processing outcomes.
- Related reconciliation decisions.

Acceptance Criteria:

- Authorised users can inspect import history.
- Historical import outcomes remain traceable.
- Reprocessed records can be associated with their relevant import context.

## 3.10 Donor Tier, KPI and Reporting Enhancements

### DON-F-051 – Donor Tier Calculation

Classification: As-Is + Enhancement Goals: DON-GO-011, 012 Workflow: DON-WF-12

Functional Requirements:

1. Retain existing donor classification functionality.
2. Determine qualifying giving using approved financial rules.
3. Apply the relevant tenant's tier thresholds.
4. Assign the applicable donor tier.
5. Update donor profiles, list filters and dependent analytics.
6. Handle donors who do not match a valid tier rule without assigning an arbitrary category.

Acceptance Criteria:

- The same eligible giving data and tier configuration produce the same classification.
- Tier changes are reflected consistently across Donors views.
- Missing or invalid tier rules do not produce fabricated classifications.

### DON-F-052 – Tier Configuration Validation

Classification: To-Be Goals: DON-GO-011, 012 Workflow: DON-WF-11

Functional Requirements:

1. Validate permitted tier names and ranges.
2. Validate overlapping or conflicting thresholds.
3. Validate the applicable currency and measurement period.
4. Validate tier order and applicable boundary rules.
5. Prevent unauthorised changes.
6. Preserve approved configuration changes for audit.

Acceptance Criteria:

- Invalid tier configurations cannot be activated.
- Changes affect only the intended tenant.
- Approved changes trigger recalculation of affected donor tiers.

### DON-F-053 – Existing Donor KPI Calculation Reuse

Classification: As-Is + Enhancement Goals: DON-GO-014 Workflow: DON-WF-14

Functional Requirements:

Retain existing calculations for:

- Total Donors.
- Active Pledges.
- Retention Rate.
- Prospects.

Use the existing KPI calculation framework when introducing additional measures.

Acceptance Criteria:

- Existing KPI values continue to use the established formulas.
- New features do not silently alter existing calculations.
- Any approved formula changes are documented and testable.

### DON-F-054 – Additional Donor KPI Library

Classification: To-Be Goals: DON-GO-016, 019 Workflow: DON-WF-14

Functional Requirements:

Provide an approved catalogue of additional donor KPIs.

| KPI                        | Business Purpose                                     |
| -------------------------- | ---------------------------------------------------- |
| Total Giving               | Qualifying contribution value                        |
| New Donors                 | Recently qualified donors                            |
| Repeat Donors              | Donors with repeat contribution activity             |
| Average Gift Amount        | Average eligible transaction value                   |
| Largest Gift               | Highest eligible gift                                |
| Donors by Tier             | Donor distribution by classification                 |
| Donors by Campaign         | Campaign-linked giving population                    |
| Donors by Location         | Geographic donor distribution                        |
| Donors by Source           | Contribution-source analysis                         |
| Lapsed Donors              | Previously qualifying donors meeting lapse criteria  |
| Monthly Donors             | Donors meeting approved monthly-giving criteria      |
| Member-to-Donor Conversion | Eligible members converting to donors                |
| Giving Trend               | Donation activity across a selected period           |
| Pending Reconciliation     | Unresolved transaction review cases                  |
| Pledge Fulfilment          | Approved comparison of pledges and fulfilled amounts |

Acceptance Criteria:

- Additional KPIs use approved calculation definitions.
- Measures operate only on relevant authorised data.
- Unsupported measures are not presented as successfully calculated values.

### DON-F-055 – KPI Selection Persistence

Classification: To-Be, Configuration Policy to Approve Goals: DON-GO-003, 016 Workflow: DON-WF-14, 20

Functional Requirements:

1. Allow users to configure displayed KPI cards where authorised.
2. Retain preferences according to the approved user-level or tenant-level model.
3. Apply permitted KPI entitlements.
4. Restore saved selections when the dashboard is reopened.

Acceptance Criteria:

- Approved selections persist according to the configuration policy.
- Users cannot select unavailable or restricted measures.
- Tenant-specific selections do not affect other organisations.

### DON-F-056 – KPI Drill-Down Consistency

Classification: To-Be Goals: DON-GO-015 Workflow: DON-WF-15

Functional Requirements:

1. Use the selected KPI's approved calculation criteria.
2. Determine the supporting record population or analytical breakdown.
3. Apply tenant and role restrictions.
4. Support suitable interactions with active search and filters.
5. Provide a clear/reset action.

Acceptance Criteria:

- KPI drill-down information supports the selected measure.
- Count-based KPIs reconcile with their eligible record population when calculation scopes match.
- Rate-based KPIs provide the relevant cohort or analytical explanation rather than a misleading row-count equivalence.

### DON-F-057 – Automatic Donor KPI Recalculation

Classification: Confirmed To-Be Goals: DON-GO-022, 026 Workflow: DON-WF-17

Functional Requirements:

Automatically recalculate affected measures following successfully committed:

- Manual donations.
- Imported donations.
- Integrated donation updates.
- Approved transaction corrections.
- Donation eligibility changes.
- Tier-configuration changes where relevant.
- Member identity changes affecting donor association.

Acceptance Criteria:

- Successfully imported eligible donations update affected KPIs automatically.
- Users do not need to press Refresh to trigger underlying calculations.
- Rejected or unresolved records do not inflate KPI values.
- Updates to existing transactions do not incorrectly increase the number of unique donors.

### DON-F-058 – Giving Reporting Period and Currency

Classification: To-Be, Business Policy to Approve Goals: DON-GO-012, 019, 026 Workflow: DON-WF-12, 14, 18

Functional Requirements:

1. Apply approved reporting periods to period-dependent metrics.
2. Preserve source currency information where applicable.
3. Use approved currency treatment for aggregated giving.
4. Avoid summing different currencies without a defined conversion policy.
5. Present appropriate reporting context.

Acceptance Criteria:

- Figures use the relevant approved reporting period.
- Aggregates follow documented currency rules.
- Unavailable conversion data does not produce an unsupported aggregate.

### DON-F-059 – Donor Analytics and Visualisations

Classification: Proposed Enhancement Goals: DON-GO-019 Workflow: DON-WF-14, 15

Functional Requirements:

Support approved visualisations such as:

- Donor distribution by tier.
- Giving trends.
- Donors by location.
- Donors by campaign.
- New versus repeat donors.
- Giving distribution by source.

Acceptance Criteria:

- Visualisations reflect authorised giving data.
- Totals are consistent with the relevant KPI definitions.
- Visualisations provide appropriate labels and reporting context.

## 3.11 Tenant Configuration and Security

### DON-F-060 – Existing Role-Based Permissions

Classification: As-Is + Enhancement Goals: DON-GO-024 Workflow: DON-WF-01, 20

Functional Requirements:

1. Reuse existing application roles and permission functionality.
2. Apply existing permissions to Donors page operations.
3. Extend the permission framework to newly introduced actions.
4. Restrict unauthorised viewing, recording, import, export and reconciliation.

Acceptance Criteria:

- Existing access behaviour remains functional.
- New restricted actions cannot bypass authorisation.
- Action availability reflects applicable permissions.

### DON-F-061 – Tenant-Specific Feature Configuration

Classification: To-Be Goals: DON-GO-003 Workflow: DON-WF-20

Functional Requirements:

1. Support approved optional features by tenant.
2. Maintain a common core Donors capability.
3. Validate entitlement and dependency rules.
4. Prevent configuration changes affecting unrelated tenants.

Acceptance Criteria:

- Eligible optional capabilities can differ between organisations.
- Unavailable features cannot be enabled without appropriate entitlement.
- Changes are restricted to the intended tenant.

### DON-F-062 – Tenant Donor Settings

Classification: To-Be Goals: DON-GO-003, 011, 016 Workflow: DON-WF-11, 14, 20

Functional Requirements:

Provide approved settings for:

- Donor tier rules.
- KPI availability and selection.
- Additional permitted filters.
- Reporting periods.
- Approved scoring options.
- Supported import configurations.
- Other permitted donor settings.

Acceptance Criteria:

- Authorised settings can be saved.
- Configuration changes affect only the relevant tenant.
- Invalid or restricted settings are rejected.

### DON-F-063 – Donation Import and Export Permissions

Classification: To-Be Extension of Existing Permissions Goals: DON-GO-024 Workflow: DON-WF-08, 16, 20

Functional Requirements:

1. Control access to Donors Import.
2. Control CSV export.
3. Control import correction and transaction reconciliation.
4. Enforce permissions on the underlying operation, not only the visible button.

Acceptance Criteria:

- Users without the required permission cannot execute restricted actions.
- Direct or unauthorised requests do not bypass the permission framework.

### DON-F-064 – Tenant Data Isolation

Classification: Confirmed Standalone Requirement Goals: DON-GO-001, 024 Workflow: DON-WF-01, 07, 08, 20

Functional Requirements:

Apply tenant isolation to:

- Donor records.
- Member references.
- Donation transactions.
- Giving history.
- KPIs and donor scores.
- Tier settings.
- Imports and integrations.
- Export results.
- Audit and reconciliation records.

Acceptance Criteria:

- One tenant cannot retrieve or modify another tenant's donor information.
- Cross-tenant member association is rejected.
- Data operations preserve the authenticated tenant boundary.

### DON-F-065 – Donor Privacy and Communication Preferences

Classification: As-Is Dependency + Enhancement Goals: DON-GO-024, 026 Workflow: DON-WF-04, 19

Functional Requirements:

1. Reuse relevant member-level communication preferences.
2. Preserve Anonymous Donor and Do Not Solicit information.
3. Limit disclosure of sensitive donor details.
4. Pass approved preferences to related communication functionality where applicable.
5. Avoid inferring campaign outreach permission merely from the presence of Send Message.

Acceptance Criteria:

- Existing preferences remain associated with the member.
- Donors operations do not unintentionally clear communication preferences.
- Sensitive information is not exposed to unauthorised users.

## 3.12 Data Consistency, Audit and Reliability

### DON-F-066 – Donor Activity Audit

Classification: To-Be Goals: DON-GO-025 Workflow: DON-WF-22

Functional Requirements:

Record material events involving:

- Donation creation.
- Transaction correction.
- Import processing.
- Duplicate decisions.
- Tier configuration changes.
- Significant export activity.
- Relevant integration/reconciliation outcomes.

Acceptance Criteria:

- Authorised audit review can identify the relevant event, actor/source and outcome.
- Material changes can be traced to the affected record.
- Audit information respects access controls.

### DON-F-067 – Donation Correction and Reconciliation

Classification: To-Be Goals: DON-GO-008, 010, 025 Workflow: DON-WF-21

Functional Requirements:

1. Identify transactions requiring correction.
2. Present relevant existing and proposed data.
3. Obtain authorisation where conflicting changes exist.
4. Apply approved corrections without creating unintended duplicate transactions.
5. Preserve material history.
6. Update dependent giving summaries.

Acceptance Criteria:

- Only approved corrections alter the committed transaction.
- Rejected changes preserve existing values.
- Successful corrections update dependent information appropriately.

### DON-F-068 – Integration Failure Handling

Classification: To-Be Goals: DON-GO-004, 023 Workflow: DON-WF-07, 22

Functional Requirements:

1. Detect integration processing failures.
2. Distinguish successful and unsuccessful ingestion.
3. Preserve previously committed information.
4. Provide relevant processing status for authorised review.
5. Support approved correction or reprocessing procedures.

Acceptance Criteria:

- Failed processing does not corrupt existing donations.
- Failures are traceable.
- Uncommitted transactions do not affect giving KPIs.

### DON-F-069 – Donor Profile Data Consistency

Classification: To-Be Goals: DON-GO-026 Workflow: DON-WF-04, 17, 18

Functional Requirements:

1. Keep donor identity aligned with Members.
2. Keep Lifetime Giving, Last Gift and Total Gifts aligned with eligible donation records.
3. Keep tiers and scores aligned with approved calculations.
4. Reflect successfully committed changes in relevant Donors views.
5. Preserve historical information according to the transaction model.

Acceptance Criteria:

- Profile and list summaries reconcile under the same calculation scope.
- Member identity changes appear consistently where applicable.
- Updated donation information is reflected in affected donor summaries.

### DON-F-070 – Donation History and Source Attribution

Classification: As-Is + Enhancement Goals: DON-GO-023, 026 Workflow: DON-WF-18

Functional Requirements:

1. Retain donor giving-history visibility.
2. Associate history with the correct member.
3. Preserve available originating source information.
4. Distinguish manual, imported and integrated record origins.
5. Include relevant source references for investigation where available.

Acceptance Criteria:

- Authorised users can review the donor's linked giving history.
- Available source information can be identified.
- Unrelated members' transactions are not included.

### DON-F-071 – Transaction Status Change Recalculation

Classification: To-Be Goals: DON-GO-022, 026 Workflow: DON-WF-17, 21

Functional Requirements:

1. Identify status changes affecting donation eligibility.
2. Recalculate affected giving totals, gift counts, tiers, scores and KPIs.
3. Preserve historical status/change information where required.
4. Prevent unauthorised or failed changes from affecting reporting.

Acceptance Criteria:

- Approved eligibility changes update relevant calculations.
- Rejected changes do not alter committed figures.
- A refund or reversal is handled according to its approved transaction treatment.

### DON-F-072 – Donor Data Refresh and Synchronisation

Classification: To-Be Goals: DON-GO-022, 026 Workflow: DON-WF-17, 22

Functional Requirements:

1. Update affected donor information after committed changes.
2. Refresh displayed KPI values.
3. Refresh applicable list, profile, tier and score information.
4. Provide a user-facing data refresh action where approved.
5. Preserve current authorised filters where applicable.
6. Prevent refresh from triggering duplicate transactions or imports.

Acceptance Criteria:

- Committed changes become available in relevant Donors views.
- Import KPI updates occur automatically.
- Refresh does not duplicate donation records.
- Displayed information reflects the latest available committed dataset.

## 4. Donation Entry Field Catalogue

The following fields are taken from the existing Add Donor popup. Exact numeric limits, date restrictions and source-specific validation rules must be confirmed before implementation.

| Field           | Requirement                  | Mandatory | Source / Validation                        |
| --------------- | ---------------------------- | --------- | ------------------------------------------ |
| Select Member   | Existing member reference    | Yes       | Search name/email/phone; tenant-restricted |
| Donation Amount | Contribution value           | Yes       | Approved numeric and currency rules        |
| Campaign        | Campaign reference           | Yes       | Existing Campaigns data                    |
| Payment Method  | Recorded contribution method | Yes       | Approved available methods                 |
| Donation Date   | Date of contribution         | Yes       | Approved date rules                        |
| Notes           | Supporting information       | No        | Optional text                              |
| Save Donation   | Submit donation              | Action    | Validate, check duplicates and process     |
| Cancel          | Exit donation form           | Action    | Do not submit a new transaction            |

## 4.1 Donation Form Validation Matrix

| Scenario                         | Expected Behaviour                        |
| -------------------------------- | ----------------------------------------- |
| Member not selected              | Prevent successful submission             |
| Invalid member reference         | Reject association                        |
| Cross-tenant member              | Deny association                          |
| Donation amount missing          | Show validation error                     |
| Invalid donation amount          | Reject according to approved rules        |
| Campaign missing                 | Show validation error                     |
| Invalid campaign reference       | Reject submission                         |
| Payment method missing           | Show validation error                     |
| Donation date missing            | Show validation error                     |
| Invalid donation date            | Show applicable error                     |
| Potential duplicate donation     | Apply duplicate-matching and review rules |
| Conflicting existing transaction | Require administrator review              |
| Valid eligible donation          | Commit according to transaction policy    |
| User selects Cancel              | Exit without committing a new donation    |

The exact error messages, minimum donation amount, supported date boundaries and currency precision are configuration/policy details requiring approval.

## 5. Donors List and Profile Matrix

| Area             | Existing Information        | To-Be Enhancement                            |
| ---------------- | --------------------------- | -------------------------------------------- |
| Donor Name       | Available                   | Consistent Members identity                  |
| Constituent Type | Available                   | Governed type classification                 |
| Tier             | Available                   | Tenant-configurable criteria                 |
| Total Given      | Available                   | Authoritative eligible giving                |
| Last Gift        | Available                   | Approved transaction eligibility             |
| Status           | Available                   | Consistent donor and member status semantics |
| Search           | Available                   | Combined filter consistency                  |
| Advanced Filters | Available                   | Additional approved criteria                 |
| Profile          | Available                   | Source and reconciliation visibility         |
| Lifetime Giving  | Available                   | Consistent calculation                       |
| Total Gifts      | Available                   | Eligible transaction count                   |
| Donor Score      | Available                   | Governed calculation                         |
| Overview         | Available                   | Retain functionality                         |
| History          | Available                   | Enhanced source traceability                 |
| Engagement       | Available                   | Retain functionality                         |
| Notes            | Available                   | Retain functionality                         |
| Record Donation  | Available                   | Preserve member context                      |
| Add Task         | Available as visible action | Retain existing task dependency              |
| Send Message     | Available as visible action | Retain existing communication dependency     |

## 6. Member–Donor Business Rules

The relationship approved in the Members documentation applies throughout this catalogue.

| Condition                                           | Expected Result                                      |
| --------------------------------------------------- | ---------------------------------------------------- |
| Member registered, no donation                      | Member only                                          |
| Member makes first qualifying donation              | Member becomes a qualifying donor                    |
| Existing donor makes another donation               | Update giving history; no new donor identity         |
| Member makes a pledge only                          | Does not independently qualify as a donor            |
| Member is administratively inactive                 | Historical giving association remains                |
| Member Giving Status is manually changed to Donated | Does not independently create a donation transaction |
| Existing transaction is corrected                   | Recalculate affected giving information              |
| Donation is rejected or unresolved                  | No additional qualifying gift is counted             |
| Imported transaction cannot match a member          | Hold for identity review                             |
| Member identity conflict occurs                     | Follow approved Members duplicate-resolution rules   |

## 6.1 Status Alignment

| Status Category       | Values                                | Responsibility             |
| --------------------- | ------------------------------------- | -------------------------- |
| Administrative Status | Active, Inactive                      | Members                    |
| Giving Status         | Prospect, Pledged, Donated, Lapsed    | Members                    |
| Transaction Status    | Existing authorised donation statuses | Donations capability       |
| Donor Tier            | Platinum, Gold, Silver, Bronze        | Donor classification rules |

These concepts must remain separate. A Giving Status label must not replace actual donation transaction evidence.

## 7. Import and Reconciliation Matrix

## 7.1 Import Result Definitions

| Outcome                  | Transaction Effect           | KPI Effect                       |
| ------------------------ | ---------------------------- | -------------------------------- |
| Created                  | New transaction committed    | Update affected KPIs if eligible |
| Updated                  | Existing transaction updated | Recalculate affected KPIs        |
| Rejected                 | No committed transaction     | No additional contribution       |
| Pending Member Review    | Identity unresolved          | No additional contribution       |
| Pending Duplicate Review | Conflict awaiting decision   | No additional contribution       |
| Skipped                  | No committed change          | No additional contribution       |

Import row count, committed transaction count and unique donor count must be reported as distinct measures.

## 7.2 Transaction Matching Principles

| Match Condition                         | Required Behaviour                                      |
| --------------------------------------- | ------------------------------------------------------- |
| No potential transaction match          | Eligible for normal validation and creation             |
| Exact approved source reference match   | Apply the approved existing-transaction handling policy |
| Potential match with conflicting values | Administrator review                                    |
| Ambiguous member identity               | Member identity review                                  |
| Reviewer approves correction            | Apply controlled update                                 |
| Reviewer rejects correction             | Preserve current transaction                            |
| Reviewer confirms separate transactions | Process as distinct records if eligible                 |
| Repeated file upload                    | Apply existing duplicate checks again                   |

Matching must not rely solely on donation amount, because different valid gifts may have identical amounts.

## 8. KPI Feature Catalogue

## 8.1 Existing KPIs

| KPI            | Existing State          | Required Enhancement          |
| -------------- | ----------------------- | ----------------------------- |
| Total Donors   | Calculation implemented | Interactive drill-down        |
| Active Pledges | Calculation implemented | Supporting record/pledge view |
| Retention Rate | Calculation implemented | Relevant cohort explanation   |
| Prospects      | Calculation implemented | Supporting prospect view      |

The existing formulas must be documented from the running application rather than replaced with assumptions.

## 8.2 Additional KPI Candidates

| KPI                        | Proposed Business Definition                                                   |
| -------------------------- | ------------------------------------------------------------------------------ |
| Total Giving               | Value of eligible giving within approved scope                                 |
| New Donors                 | Distinct members first qualifying as donors during the defined period          |
| Repeat Donors              | Donors meeting approved repeat-giving criteria                                 |
| Average Gift Amount        | Eligible giving value divided by eligible gift count                           |
| Largest Gift               | Maximum eligible gift value                                                    |
| Donors by Tier             | Distinct donors grouped by qualifying tier                                     |
| Donors by Campaign         | Donors associated with approved campaign criteria                              |
| Donors by Location         | Donors grouped by approved geographic fields                                   |
| Donors by Source           | Donors classified using approved source-attribution rules                      |
| Lapsed Donors              | Donors meeting approved inactivity criteria                                    |
| Monthly Donors             | Donors meeting defined monthly-giving rules                                    |
| Member-to-Donor Conversion | Qualifying converted members divided by the defined eligible member population |
| Giving Trend               | Eligible giving across approved periods                                        |
| Pending Reconciliation     | Unresolved transaction review cases                                            |
| Pledge Fulfilment          | Fulfilled eligible amounts compared with applicable pledge obligations         |

These are candidate business definitions. Their exact population, financial treatment, time periods and calculation rules require approval.

## 8.3 KPI Synchronisation Rules

1. Existing KPI formulas must be preserved.
2. Additional KPIs must use approved definitions.
3. Eligible committed donations must update affected KPIs.
4. Successfully committed imports must trigger automatic KPI updates.
5. Rejected and pending rows must not inflate giving values.
6. A transaction update must not be counted as a new donor unless donor qualification genuinely changes.
7. The same authoritative records must support relevant profile summaries and dashboard calculations.
8. Tenant and user permissions must govern KPI visibility and drill-down.

## 9. Goals-to-Feature Traceability

The table below covers all 26 Donors business goals.

Feature ranges are shortened for readability. Every number represents a `DON-F-###` identifier.

| Goal                                   | Supporting Features         |
| -------------------------------------- | --------------------------- |
| DON-GO-001 – Multi-Tenant Donors       | 001, 060, 064               |
| DON-GO-002 – Reusable Capability       | 001–004, 061                |
| DON-GO-003 – Tenant Configuration      | 030, 031, 055, 061, 062     |
| DON-GO-004 – Centralised Giving        | 028, 038, 069, 070          |
| DON-GO-005 – Flexible Data Acquisition | 018–028, 032–034            |
| DON-GO-006 – Member–Donor Relationship | 019, 036–038, 045           |
| DON-GO-007 – Manual Donation Entry     | 018–026                     |
| DON-GO-008 – Reliable Transactions     | 020–025, 038, 039, 042, 067 |
| DON-GO-009 – Duplicate Prevention      | 039–041, 048                |
| DON-GO-010 – Controlled Reconciliation | 040, 041, 048, 067          |
| DON-GO-011 – Donor Tiers               | 006, 031, 051, 052          |
| DON-GO-012 – Tier Calculation          | 031, 051, 052, 058          |
| DON-GO-013 – Scoring                   | 013, 016                    |
| DON-GO-014 – Existing KPIs             | 002, 053                    |
| DON-GO-015 – KPI Drill-Down            | 029, 056                    |
| DON-GO-016 – KPI Selection             | 030, 054, 055               |
| DON-GO-017 – Filtering                 | 005–010, 035                |
| DON-GO-018 – Filtered Export           | 027, 035, 063               |
| DON-GO-019 – Visualisation             | 054, 058, 059               |
| DON-GO-020 – Bulk Import               | 032, 033, 043–046           |
| DON-GO-021 – Import Validation         | 033, 034, 043–050           |
| DON-GO-022 – KPI Synchronisation       | 057, 071, 072               |
| DON-GO-023 – Source Attribution        | 028, 050, 068, 070          |
| DON-GO-024 – Permissions               | 001, 060, 063–065           |
| DON-GO-025 – Auditability              | 041, 050, 066–068           |
| DON-GO-026 – Profile Consistency       | 011–017, 036, 042, 069–072  |

## 10. Workflow-to-Feature Mapping

| Workflow                              | Relevant Features           |
| ------------------------------------- | --------------------------- |
| DON-WF-01 – Donors Overview           | 001–004, 053, 060, 064      |
| DON-WF-02 – Search and Tier Filtering | 004–006, 010, 011           |
| DON-WF-03 – Advanced Filtering        | 007–009, 035                |
| DON-WF-04 – Donor Profile             | 011–017, 069                |
| DON-WF-05 – Donation Entry            | 018–026, 038–040, 042       |
| DON-WF-06 – Member–Donor Relationship | 019, 036–038, 045           |
| DON-WF-07 – External Integration      | 028, 039, 040, 068, 070     |
| DON-WF-08 – Bulk Import               | 032–034, 043–050            |
| DON-WF-09 – Import Validation         | 033, 043–049                |
| DON-WF-10 – Duplicate Resolution      | 039–041, 048                |
| DON-WF-11 – Tier Configuration        | 031, 052, 062               |
| DON-WF-12 – Tier Calculation          | 006, 031, 051, 058          |
| DON-WF-13 – Donor Scoring             | 013, 016, 069               |
| DON-WF-14 – KPI Configuration         | 030, 053–055, 059           |
| DON-WF-15 – KPI Drill-Down            | 029, 056, 059               |
| DON-WF-16 – Export                    | 027, 035, 063               |
| DON-WF-17 – Automatic Refresh         | 057, 071, 072               |
| DON-WF-18 – Giving History            | 014, 015, 042, 070          |
| DON-WF-19 – Profile Actions           | 017, 026, 065               |
| DON-WF-20 – Tenant Configuration      | 001, 030, 031, 055, 060–065 |
| DON-WF-21 – Donation Correction       | 041, 042, 067, 071          |
| DON-WF-22 – Audit and Exceptions      | 050, 063, 066–068, 072      |

## 11. Dependencies and Boundaries

| Capability            | Donors Dependency                                 |
| --------------------- | ------------------------------------------------- |
| Members               | Authoritative identity and member information     |
| Campaigns             | Available campaign references                     |
| Donations             | Transaction persistence and payment/record status |
| Tenant Management     | Isolated workspaces and approved settings         |
| Existing Permissions  | Donors action authorisation                       |
| External Integrations | Third-party giving data                           |
| Import Processing     | Template validation and import outcomes           |
| Reporting/KPI         | Donor calculations, scores and summaries          |
| Export                | Authorised CSV generation                         |
| Audit                 | Material activity history                         |
| Communications        | Existing Send Message entry point                 |
| Tasks                 | Existing Add Task entry point                     |
| AI Copilot            | Shared application entry point                    |
| Global Search         | Shared cross-module navigation                    |

These capabilities remain part of the wider AiXPurpose product. This catalogue specifies only their relevant Donors interactions.

## 12. Open Business Decisions

The following detailed policies remain subject to approval or existing-system verification.

| Decision ID | Required Clarification                                                   | Affected Features      |
| ----------- | ------------------------------------------------------------------------ | ---------------------- |
| DON-OD-001  | Which transaction statuses qualify a member as a donor?                  | 037, 042, 057          |
| DON-OD-002  | How are prospect-only records presented in the Donors list and KPIs?     | 004, 008, 037, 053     |
| DON-OD-003  | Does Save Donation record payment information or process a payment?      | 022, 025, 042          |
| DON-OD-004  | Which payment methods and transaction statuses are supported?            | 022, 042               |
| DON-OD-005  | Which identifiers and rules determine transaction duplicates?            | 039–041, 048           |
| DON-OD-006  | What are the final import templates, limits and partial-success rules?   | 032–034, 043–050       |
| DON-OD-007  | How are unmatched imported identities resolved through Members?          | 036, 045               |
| DON-OD-008  | What tier thresholds, currency and measurement rules apply?              | 031, 051, 052, 058     |
| DON-OD-009  | What are the verified existing and approved additional KPI formulas?     | 029, 053–057           |
| DON-OD-010  | What is the existing donor scoring formula and permitted configuration?  | 013, 016, 069          |
| DON-OD-011  | How should KPI, search, tier and advanced filters combine/reset?         | 005–009, 029, 035, 056 |
| DON-OD-012  | What export columns and record-selection rules apply?                    | 010, 027, 035          |
| DON-OD-013  | What are the existing profile-tab, Add Task and Send Message behaviours? | 015, 017               |
| DON-OD-014  | What are the refund, reversal and historical correction policies?        | 042, 067, 071          |
| DON-OD-015  | What source precedence rules govern integration updates?                 | 028, 040, 068          |
| DON-OD-016  | What currency conversion rules apply to multi-currency giving?           | 020, 031, 058          |
| DON-OD-017  | Which optional features and settings are tenant-configurable?            | 030, 055, 061, 062     |
| DON-OD-018  | What audit retention and visibility rules apply?                         | 050, 066, 070          |

These decisions do not reopen the confirmed Member–Donor relationship, existing permission framework or requirement for automatic KPI updates.

## 13. Acceptance and QA Coverage

Testing must be derived from each feature's acceptance criteria and applicable business rules.

| Test Category          | Required Coverage                                               |
| ---------------------- | --------------------------------------------------------------- |
| Existing UI            | Navigation, listing, profiles, filters and actions              |
| Member Association     | Valid, invalid and cross-tenant member references               |
| Donation Entry         | Required fields, invalid values and cancellation                |
| Transaction Duplicates | New, matching, ambiguous and conflicting records                |
| Bulk Import            | Valid files, malformed files, invalid rows, partial processing  |
| Import Results         | Created, updated, rejected, pending and skipped counts          |
| Donor Qualification    | First eligible gift, additional gift, pledge-only member        |
| Tiers                  | Threshold boundaries, overlapping rules and recalculation       |
| KPIs                   | Existing formulas, additional definitions and drill-down        |
| Automatic Refresh      | Post-commit updates without manual recalculation                |
| Exports                | Filter consistency, permission and tenant scope                 |
| Security               | Existing roles and cross-tenant restrictions                    |
| Audit                  | Material record and reconciliation events                       |
| Reliability            | Failed imports, interrupted processing and repeated submissions |

Where an underlying rule remains open, its exact expected test values must be agreed before final UAT execution.

## 14. Product Management Validation Summary

| Review Area               | Validation Result                                                              |
| ------------------------- | ------------------------------------------------------------------------------ |
| Original Features         | 35 identifiers preserved                                                       |
| Additional Features       | 37 introduced                                                                  |
| Total Features            | 72                                                                             |
| Goals Coverage            | DON-GO-001–026                                                                 |
| Workflow Coverage         | DON-WF-01–22                                                                   |
| Business Rules            | Aligned with DON-BR-001–040                                                    |
| Existing Functionality    | Retained                                                                       |
| Standalone Requirements   | Incorporated                                                                   |
| Member–Donor Relationship | Confirmed and reflected                                                        |
| Existing Permissions      | Classified as As-Is                                                            |
| Tenant Configuration      | Supports approved optional capabilities                                        |
| Donation Entry            | Required fields preserved                                                      |
| Data Imports              | Validation, matching, preview, review and results                              |
| Duplicate Handling        | Controlled transaction reconciliation                                          |
| Donor Tiers               | Configurable thresholds without invented values                                |
| Donor Scoring             | Existing components retained                                                   |
| KPIs                      | Existing logic reused; additional measures defined as candidates               |
| KPI Synchronisation       | Automatic after committed changes                                              |
| Filtering and Export      | Enhanced and permission-controlled                                             |
| Audit and Reliability     | Covered                                                                        |
| Flowcharts                | Omitted because detailed feature definitions and matrices are more appropriate |
| Open Decisions            | Clearly identified                                                             |

## 15. Document Conclusion

The Donors Feature Catalogue defines the functional requirements for extending the existing AiXPurpose Donors page into a reusable, configurable and secure multi-tenant capability.

It preserves the existing donor overview, donation recording, profile information, tiers, scoring, filters, KPI calculations and integrations while specifying the standalone requirements for bulk imports, controlled reconciliation, configurable reporting, filtered exports, auditability and automatic updates.

The established Member–Donor rule remains fundamental: every donor must be linked to an existing member, but not every member must be a donor.

The 72 identified features provide a traceable baseline for product review, detailed technical design, user stories and QA/UAT. All remaining policy-dependent calculations, transaction rules and configuration options must be confirmed before their respective acceptance tests are finalised.
