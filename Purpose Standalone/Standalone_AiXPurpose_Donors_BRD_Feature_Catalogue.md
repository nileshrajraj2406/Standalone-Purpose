# Standalone AiXPurpose Donors — BRD Feature Catalogue

> Status: Draft for review
> Primary sources: User Donors requirements and screenshots, `Standalone_AiXPurpose_Donors_BRD_Goals.md`, `Standalone_AiXPurpose_Donors_BRD_Workflow.md`, `master_prompt_brd_feature_catalogue(1).md`
> ID convention: `DON-F-001` onward; document-local stable feature IDs.
> Evidence legend: Confirmed = directly supported behaviour; Approved assumption = user-authorised unbuilt proposal; Proposed = future candidate requiring confirmation.
> Scope note: No existing role matrix, formulas, processing APIs or test case IDs are presumed.

## Overview
This document captures the Donors feature catalogue for the Standalone AiXPurpose product in a README-style format. It breaks down goals and workflows into individually reviewable, testable product features and tracks open decisions, feature traceability, and implementation handoff information.

The catalogue is intentionally scoped to observable product behaviour derived from source materials and screenshots. It avoids guessing unsupported permissions, formulas, backend interfaces, or generic acceptance criteria.

## Table of Contents
- [Overview](#overview)
- [Scope and Document Relationship](#1-scope-and-document-relationship)
- [Evidence and Screenshots](#2-evidence-and-screenshots)
- [Feature Inventory](#3-feature-inventory)
- [Detailed Feature Catalogue](#4-detailed-feature-catalogue)
- [Applicable Functional Matrices](#5-applicable-functional-matrices)
- [Goal → Workflow → Feature Coverage](#6-goal--workflow--feature-coverage)
- [Workflow → Feature Coverage](#7-workflow--feature-coverage)
- [Reverse Feature Traceability](#8-reverse-feature-traceability)
- [Pending Decisions and Coverage Gaps](#9-pending-decisions-and-coverage-gaps)
- [Product, Engineering and QA Handoff](#10-product-engineering-and-qa-handoff)
- [Validation Summary](#11-validation-summary)

## 1. Scope and Document Relationship
This catalogue decomposes Donors goals and workflows into individually reviewable functional requirements. Goals describe why; workflows describe how; features define observable product behaviour. The same product features are available across client tenants; client data and access remain isolated.

Campaigns, Members, Tasks, Communications, and external connectors are included only as dependencies of Donors page behaviour. Member manual-creation fields are specified in the separate Members catalogue.

## 2. Evidence and Screenshots
| UI ID | Source asset | Feature evidence |
|---|---|---|
| UI-DON-01 | `image(20261009-111130).png` | List, KPIs, search, tier filters, Export CSV, Add Donor, row selection/actions |
| UI-DON-02 | `image(20261009-111809).png` | Add Donor modal and fields |
| UI-DON-03 | `image(20261009-112014).png` | Advanced Filters drawer |
| UI-DON-04 | `image(20261009-112113).png` | Donor profile, identity and score |
| UI-DON-05 | `image(20261009-112213).png` | Profile actions and scoring breakdown |

Screenshots confirm visible UI, not persistence, identity matching, formula correctness, permissions, notification delivery or payment processing. Screenshot files must accompany this Markdown file to render the relative image references; paths are not embedded into feature descriptions unnecessarily.

## 3. Feature Inventory
| ID | Feature | Group | Goal(s) | Workflow(s) | Evidence |
|---|---|---|---|---|---|
| DON-F-001 | Tenant-scoped Donor Access | Tenant and Navigation | BG-DON-001 | WF-DON-01 | Confirmed |
| DON-F-002 | Donors Page Navigation | Tenant and Navigation | BG-DON-002 | WF-DON-01 | Confirmed |
| DON-F-003 | Shared Header Entry Points | Tenant and Navigation | BG-DON-004 | WF-DON-01 | Confirmed |
| DON-F-004 | Donor Table Presentation | Donor Listing | BG-DON-004 | WF-DON-01; WF-DON-02 | Confirmed |
| DON-F-005 | Search Donors by Name Email or Tier | Donor Listing | BG-DON-004 | WF-DON-02 | Confirmed |
| DON-F-006 | Quick Tier Filtering | Donor Listing | BG-DON-004 | WF-DON-02 | Confirmed |
| DON-F-007 | Advanced Filter Drawer | Donor Listing | BG-DON-004 | WF-DON-02 | Confirmed |
| DON-F-008 | Engagement Segment Choices | Donor Listing | BG-DON-004 | WF-DON-02 | Confirmed |
| DON-F-009 | Apply and Clear Advanced Filters | Donor Listing | BG-DON-004 | WF-DON-02 | Confirmed |
| DON-F-010 | Donor Row Selection Controls | Donor Listing | BG-DON-004 | WF-DON-02 | Confirmed |
| DON-F-011 | Open Donor from Row or Ellipsis | Donor Listing | BG-DON-004 | WF-DON-03 | Confirmed |
| DON-F-012 | Donor Identity and Classification | Donor Profile | BG-DON-007 | WF-DON-03 | Confirmed |
| DON-F-013 | Profile Donor Score Display | Donor Profile | BG-DON-007 | WF-DON-03 | Confirmed |
| DON-F-014 | Giving Summary Cards | Donor Profile | BG-DON-007 | WF-DON-03 | Confirmed |
| DON-F-015 | Profile Tabs | Donor Profile | BG-DON-007 | WF-DON-03 | Confirmed |
| DON-F-016 | Donor Score Breakdown Overview | Donor Profile | BG-DON-007 | WF-DON-03 | Confirmed |
| DON-F-017 | Donor Profile Action Entry Points | Donor Profile | BG-DON-007 | WF-DON-10 | Confirmed |
| DON-F-018 | Add Donor Modal Entry | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-019 | Required Existing Member Lookup | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-020 | Required Donation Amount | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-021 | Campaign Selection from Campaigns | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-022 | Payment Method Selection | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-023 | Donation Date Entry | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-024 | Donation Notes | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-025 | Save or Cancel Donation Entry | Donation Entry | BG-DON-003 | WF-DON-04 | Confirmed |
| DON-F-026 | Record Donation from Profile | Donation Entry | BG-DON-003; BG-DON-007 | WF-DON-04; WF-DON-10 | Confirmed |
| DON-F-027 | Donor CSV Export | Exports and Integrations | BG-DON-008 | WF-DON-05 | Confirmed |
| DON-F-028 | Integrated Giving Information Presentation | Exports and Integrations | BG-DON-002 | WF-DON-06 | Confirmed |
| DON-F-029 | KPI Card Drill-down | Proposed Analytics | BG-DON-005 | WF-DON-07 | Proposed |
| DON-F-030 | User-selectable Donor KPIs | Proposed Analytics | BG-DON-005 | WF-DON-07 | Proposed |
| DON-F-031 | Organisation-defined Donor Tier Bands | Proposed Analytics | BG-DON-006 | WF-DON-08 | Proposed |
| DON-F-032 | Predefined Donor Import Template | Proposed Import | BG-DON-008 | WF-DON-09 | Approved assumption |
| DON-F-033 | Upload and Validate Donor File | Proposed Import | BG-DON-008 | WF-DON-09 | Approved assumption |
| DON-F-034 | Import Outcome and Record Review | Proposed Import | BG-DON-008 | WF-DON-09 | Approved assumption |
| DON-F-035 | Additional Donor Filtering and Targeted Export | Proposed Analytics | BG-DON-004; BG-DON-008 | WF-DON-02; WF-DON-05 | Proposed |

## 4. Detailed Feature Catalogue

### Tenant and Navigation

#### DON-F-001 — Tenant-scoped Donor Access
- **Evidence:** Confirmed. **Traceability:** BG-DON-001; BR-DON-001; BR-DON-002; WF-DON-01. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Expose Donors information within the currently selected client workspace; the same Donors capability is available to all clients.
- **Acceptance outcome:** Given a user accesses their client workspace, when Donors opens, only that workspace’s donor context is presented.
- **Open decision(s):** OD-DON-09.

#### DON-F-002 — Donors Page Navigation
- **Evidence:** Confirmed. **Traceability:** BG-DON-002; BR-DON-003; WF-DON-01. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Open Donor Management → Donors and show the summary and listing with All tier selected.
- **Acceptance outcome:** When Donors is opened, four named KPI cards and the donor list appear with All tier selected.

#### DON-F-003 — Shared Header Entry Points
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; No separately numbered business rule; WF-DON-01. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Present Search everything, notifications, AI Copilot and signed-in profile/sign-out controls in the shared header.
- **Acceptance outcome:** On Donors, the four shared entry points are visible. Their unspecified internal behaviour is not asserted.
- **Open decision(s):** OD-DON-07.

### Donor Listing

#### DON-F-004 — Donor Table Presentation
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; BR-DON-003; WF-DON-01; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Show donor selection checkbox, Donor identity/email, Type, Tier, Total Given, Last Gift, Status and per-row three-dot action.
- **Acceptance outcome:** Given donor data, the table presents the specified columns and actions.

#### DON-F-005 — Search Donors by Name Email or Tier
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; No separately numbered business rule; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide list search labelled Filter by name, email, or tier and display matching donor records.
- **Acceptance outcome:** When a search value matches donor name, email or tier, the corresponding donor row can be located.

#### DON-F-006 — Quick Tier Filtering
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; BR-DON-003; BR-DON-008; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Offer All, Platinum, Gold, Silver and Bronze tier chips; show All by default and filter the list on tier choice.
- **Acceptance outcome:** When Gold is selected, the list is limited to Gold-labelled donor records; selecting All returns to the un-tier-filtered view.
- **Open decision(s):** OD-DON-03.

#### DON-F-007 — Advanced Filter Drawer
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; BR-DON-009; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Open Advanced Filters panel with Donation Range minimum/maximum, donor score slider labelled 0–100 and engagement segment choices.
- **Acceptance outcome:** When Advanced is opened, every listed control is available.
- **Open decision(s):** OD-DON-04.

#### DON-F-008 — Engagement Segment Choices
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; BR-DON-009; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Offer New Donors, Lapsing, Major Prospects and Monthly Donors within Advanced Filters.
- **Acceptance outcome:** When Advanced is opened, the four segments can be selected in the UI.
- **Open decision(s):** OD-DON-04.

#### DON-F-009 — Apply and Clear Advanced Filters
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; BR-DON-009; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Apply selected advanced filter conditions to list results or clear selected conditions using Clear All.
- **Acceptance outcome:** When Apply Filters is selected after entering conditions, list results reflect the applied criteria; Clear All clears those conditions.
- **Open decision(s):** OD-DON-04; OD-DON-10.

#### DON-F-010 — Donor Row Selection Controls
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; No separately numbered business rule; WF-DON-02. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Display checkboxes in listing rows and the header as depicted. No bulk operation is specified.
- **Acceptance outcome:** Each displayed donor row offers a selectable checkbox.
- **Open decision(s):** OD-DON-08.

#### DON-F-011 — Open Donor from Row or Ellipsis
- **Evidence:** Confirmed. **Traceability:** BG-DON-004; BR-DON-007; WF-DON-03. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Open the same donor details page when either its table row or the row ellipsis is selected.
- **Acceptance outcome:** Given a donor row, when clicking the row or its ellipsis, the same donor profile is shown.

### Donor Profile

#### DON-F-012 — Donor Identity and Classification
- **Evidence:** Confirmed. **Traceability:** BG-DON-007; No separately numbered business rule; WF-DON-03. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Display donor name, email, phone, location, Type, Tier and Status.
- **Acceptance outcome:** When a donor profile opens, the supplied identity, contact and classification fields are visible.

#### DON-F-013 — Profile Donor Score Display
- **Evidence:** Confirmed. **Traceability:** BG-DON-007; BR-DON-010; WF-DON-03. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Display the donor score in the donor profile. Computing or recalculating the score is not established.
- **Acceptance outcome:** When the profile opens, the donor score indicator is visible.
- **Open decision(s):** OD-DON-04.

#### DON-F-014 — Giving Summary Cards
- **Evidence:** Confirmed. **Traceability:** BG-DON-007; No separately numbered business rule; WF-DON-03. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Display Lifetime Giving, Last Gift and Total Gifts cards for the donor.
- **Acceptance outcome:** When the donor profile opens, those three named giving summary cards are displayed.
- **Open decision(s):** OD-DON-04.

#### DON-F-015 — Profile Tabs
- **Evidence:** Confirmed. **Traceability:** BG-DON-007; BR-DON-010; WF-DON-03. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide Overview, History, Engagement and Notes tabs within the donor detail page.
- **Acceptance outcome:** A user can select each of the four named tabs. Tab-specific content beyond Overview is not claimed.
- **Open decision(s):** OD-DON-07.

#### DON-F-016 — Donor Score Breakdown Overview
- **Evidence:** Confirmed. **Traceability:** BG-DON-007; BR-DON-010; WF-DON-03. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** On Overview, display Value Score (40%), Recency Score (30%), Frequency Score (30%) and Engagement Score (Extra) with bar-style indicators. These displayed weights are not established computational rules.
- **Acceptance outcome:** When Overview opens, all four labelled score components are displayed.
- **Open decision(s):** OD-DON-04.

#### DON-F-017 — Donor Profile Action Entry Points
- **Evidence:** Confirmed. **Traceability:** BG-DON-007; No separately numbered business rule; WF-DON-10. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Present Record Donation, Add Task and Send Message actions on the donor profile. Full Task/Messaging workflows are unspecified.
- **Acceptance outcome:** The three actions are available as visible profile entry points.
- **Open decision(s):** OD-DON-07.

### Donation Entry

#### DON-F-018 — Add Donor Modal Entry
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-004; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Selecting Add Donor opens a modal with Member Selection and Donation Details sections.
- **Acceptance outcome:** When Add Donor is selected, the donation-entry modal opens.

#### DON-F-019 — Required Existing Member Lookup
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-004; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide required Select Member lookup accepting name, email or phone and use existing member records.
- **Acceptance outcome:** When Add Donor opens, Select Member is marked required and searchable by name/email/phone.
- **Open decision(s):** OD-DON-01.

#### DON-F-020 — Required Donation Amount
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-005; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide a Donation Amount input marked required. Numeric validation beyond its required indication is unspecified.
- **Acceptance outcome:** When Add Donor opens, Donation Amount displays a required indicator.
- **Open decision(s):** OD-DON-05.

#### DON-F-021 — Campaign Selection from Campaigns
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-005; BR-DON-006; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide a required Campaign dropdown populated by Campaigns page data.
- **Acceptance outcome:** When entering donation details, Campaign is marked required and can be selected from Campaigns source options.
- **Open decision(s):** OD-DON-05.

#### DON-F-022 — Payment Method Selection
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-005; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide required Payment Method selection; Credit Card is depicted and UPI is cited by the user; final option set unspecified.
- **Acceptance outcome:** When Add Donor opens, Payment Method is marked required and supports available options.
- **Open decision(s):** OD-DON-05.

#### DON-F-023 — Donation Date Entry
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-005; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide a Donation Date input with required indicator and a date-selection control.
- **Acceptance outcome:** When Add Donor opens, Donation Date is visibly required.
- **Open decision(s):** OD-DON-05.

#### DON-F-024 — Donation Notes
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-005; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide a Notes field without a required indicator.
- **Acceptance outcome:** When Add Donor opens, a Notes entry field is available.

#### DON-F-025 — Save or Cancel Donation Entry
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BR-DON-004; BR-DON-005; WF-DON-04. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide Save Donation and Cancel controls; Save initiates donation record submission. Persistence, payment processing and validation responses remain open.
- **Acceptance outcome:** When the modal is displayed, Save Donation and Cancel are present; Save initiates the intended entry action.
- **Open decision(s):** OD-DON-01; OD-DON-05.

#### DON-F-026 — Record Donation from Profile
- **Evidence:** Confirmed. **Traceability:** BG-DON-003; BG-DON-007; No separately numbered business rule; WF-DON-04; WF-DON-10. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide a Record Donation entry point for the selected donor, without asserting unconfirmed form-routing or status changes.
- **Acceptance outcome:** When viewing a donor, Record Donation is available to begin donor-specific donation capture.
- **Open decision(s):** OD-DON-01; OD-DON-05.

### Exports and Integrations

#### DON-F-027 — Donor CSV Export
- **Evidence:** Confirmed. **Traceability:** BG-DON-008; No separately numbered business rule; WF-DON-05. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Provide Export CSV on Donors list for donor dataset extraction. File columns and active filter scope remain undecided.
- **Acceptance outcome:** When viewing the donor list, the user can invoke Export CSV.
- **Open decision(s):** OD-DON-08.

#### DON-F-028 — Integrated Giving Information Presentation
- **Evidence:** Confirmed. **Traceability:** BG-DON-002; No separately numbered business rule; WF-DON-06. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Make donor and giving records from connected external sources available in consolidated AiXPurpose views as described; connector mechanisms are not specified.
- **Acceptance outcome:** When data has been supplied from an integration, its associated donor/giving information can be reviewed in the consolidated application.
- **Open decision(s):** OD-DON-02.

### Proposed Analytics

#### DON-F-029 — KPI Card Drill-down
- **Evidence:** Proposed. **Traceability:** BG-DON-005; No separately numbered business rule; WF-DON-07. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Make KPI cards clickable so a chosen KPI such as Active Pledges filters the donor list to relevant records.
- **Acceptance outcome:** Proposed: selecting Active Pledges updates the list to the KPI-relevant subset, after KPI definition approval.
- **Open decision(s):** OD-DON-04; OD-DON-10.

#### DON-F-030 — User-selectable Donor KPIs
- **Evidence:** Proposed. **Traceability:** BG-DON-005; No separately numbered business rule; WF-DON-07. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Allow selection of additional data-supported KPIs for display while maintaining the same feature set for every tenant.
- **Acceptance outcome:** Proposed: choosing an available KPI adds it to the visible dashboard selection.
- **Open decision(s):** OD-DON-10.

#### DON-F-031 — Organisation-defined Donor Tier Bands
- **Evidence:** Proposed. **Traceability:** BG-DON-006; BR-DON-008; WF-DON-08. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Permit organisation-specific tier assignment criteria after approval; example $100k/$50k values are not binding thresholds.
- **Acceptance outcome:** Proposed: applying approved organisation tier settings determines displayed tier labels consistently.
- **Open decision(s):** OD-DON-03.

### Proposed Import

#### DON-F-032 — Predefined Donor Import Template
- **Evidence:** Approved assumption. **Traceability:** BG-DON-008; AS-DON-001; WF-DON-09. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Offer a predefined Excel/CSV template identifying required fields for donor import; exact fields need confirmation.
- **Acceptance outcome:** Assumption: administrator can obtain an applicable donor import template.
- **Open decision(s):** OD-DON-06.

#### DON-F-033 — Upload and Validate Donor File
- **Evidence:** Approved assumption. **Traceability:** BG-DON-008; AS-DON-001; WF-DON-09. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Allow administrator to upload completed Excel/spreadsheet/CSV data and validate it against approved template rules.
- **Acceptance outcome:** Assumption: a prepared donor file can be submitted for import; validation rules are pending.
- **Open decision(s):** OD-DON-01; OD-DON-06.

#### DON-F-034 — Import Outcome and Record Review
- **Evidence:** Approved assumption. **Traceability:** BG-DON-008; AS-DON-001; WF-DON-09. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Show imported-record count and permit review/correction of imported donor data; precise edit target and partial-failure rules open.
- **Acceptance outcome:** Assumption: after import an administrator sees a result count, such as 250 imported, and can inspect data for correction.
- **Open decision(s):** OD-DON-01; OD-DON-06.

### Proposed Analytics

#### DON-F-035 — Additional Donor Filtering and Targeted Export
- **Evidence:** Proposed. **Traceability:** BG-DON-004; BG-DON-008; PE-DON-004; WF-DON-02; WF-DON-05. **Source:** Donors page user walkthrough and matching workflow/UI references.
- **Requirement:** Evaluate client-relevant additional donor filters and export of a filtered donor subset; specification remains pending.
- **Acceptance outcome:** Proposed: after an approved filter/export rule exists, export contains the requested subset.
- **Open decision(s):** OD-DON-08; OD-DON-10.

## 5. Applicable Functional Matrices
### 5.1 Donation Entry Field Matrix
| Input | Requirement evidence | Source / constraint |
|---|---|---|
| Select Member | Required (asterisk) | Lookup by name/email/phone, based on existing Members |
| Donation Amount | Required (asterisk) | Numeric bounds/currency rules not specified |
| Campaign | Required (asterisk) | Options sourced from Campaigns page |
| Payment Method | Required (asterisk) | Credit Card shown; UPI mentioned; final methods undefined |
| Donation Date | Required (asterisk) | Format/date restrictions not specified |
| Notes | Not marked required | Notes visible; content rules not specified |

### 5.2 Donors List and Profile Matrix
| Area | Source-backed detail | Unresolved |
|---|---|---|
| Listing columns | Checkbox, Donor, Type, Tier, Total Given, Last Gift, Status, ellipsis | Row selection bulk purpose |
| Tier quick chips | All (default), Platinum, Gold, Silver, Bronze | Assignment boundaries / currency / period |
| Advanced filter | Min/max donation, 0–100 Donor Score, four engagement segments | AND/OR combination / score semantics |
| Summary KPIs | Total Donors, Active Pledges, Retention Rate, Prospects | Formula, time window, permissions |
| Profile cards | Lifetime Giving, Last Gift, Total Gifts | Aggregation definitions and source freshness |
| Score components | Value (40%), Recency (30%), Frequency (30%), Engagement (Extra) | Actual algorithm / rounding / applicability |
| Profile tabs | Overview, History, Engagement, Notes | Content and edit rights |
| Profile actions | Record Donation, Add Task, Send Message | Task and message workflow; future outreach distinction |

## 6. Goal → Workflow → Feature Coverage
| Goal | Workflow(s) | Feature IDs | Qualification |
|---|---|---|---|
| BG-DON-001 | WF-DON-01 | DON-F-001 | Source-backed, open decisions noted |
| BG-DON-002 | WF-DON-01; WF-DON-06 | DON-F-002, DON-F-028 | Source-backed, open decisions noted |
| BG-DON-003 | WF-DON-04; WF-DON-10 | DON-F-018, DON-F-019, DON-F-020, DON-F-021, DON-F-022, DON-F-023, DON-F-024, DON-F-025, DON-F-026 | Source-backed, open decisions noted |
| BG-DON-004 | WF-DON-01; WF-DON-02; WF-DON-03; WF-DON-05 | DON-F-003, DON-F-004, DON-F-005, DON-F-006, DON-F-007, DON-F-008, DON-F-009, DON-F-010, DON-F-011, DON-F-035 | Contains proposed or assumption-based features |
| BG-DON-005 | WF-DON-07 | DON-F-029, DON-F-030 | Contains proposed or assumption-based features |
| BG-DON-006 | WF-DON-08 | DON-F-031 | Contains proposed or assumption-based features |
| BG-DON-007 | WF-DON-03; WF-DON-10; WF-DON-04 | DON-F-012, DON-F-013, DON-F-014, DON-F-015, DON-F-016, DON-F-017, DON-F-026 | Source-backed, open decisions noted |
| BG-DON-008 | WF-DON-05; WF-DON-09; WF-DON-02 | DON-F-027, DON-F-032, DON-F-033, DON-F-034, DON-F-035 | Contains proposed or assumption-based features |

### Rule-Level Coverage
| Rule | Feature IDs |
|---|---|
| BR-DON-001 | DON-F-001 |
| BR-DON-002 | DON-F-001 |
| BR-DON-003 | DON-F-002, DON-F-004, DON-F-006 |
| BR-DON-004 | DON-F-018, DON-F-019, DON-F-025 |
| BR-DON-005 | DON-F-020, DON-F-021, DON-F-022, DON-F-023, DON-F-024, DON-F-025 |
| BR-DON-006 | DON-F-021 |
| BR-DON-007 | DON-F-011 |
| BR-DON-008 | DON-F-006, DON-F-031 |
| BR-DON-009 | DON-F-007, DON-F-008, DON-F-009 |
| BR-DON-010 | DON-F-013, DON-F-015, DON-F-016 |

## 7. Workflow → Feature Coverage
| Workflow ID | Supporting feature IDs |
|---|---|
| WF-DON-01 | DON-F-001, DON-F-002, DON-F-003, DON-F-004 |
| WF-DON-02 | DON-F-004, DON-F-005, DON-F-006, DON-F-007, DON-F-008, DON-F-009, DON-F-010, DON-F-035 |
| WF-DON-03 | DON-F-011, DON-F-012, DON-F-013, DON-F-014, DON-F-015, DON-F-016 |
| WF-DON-04 | DON-F-018, DON-F-019, DON-F-020, DON-F-021, DON-F-022, DON-F-023, DON-F-024, DON-F-025, DON-F-026 |
| WF-DON-05 | DON-F-027, DON-F-035 |
| WF-DON-06 | DON-F-028 |
| WF-DON-07 | DON-F-029, DON-F-030 |
| WF-DON-08 | DON-F-031 |
| WF-DON-09 | DON-F-032, DON-F-033, DON-F-034 |
| WF-DON-10 | DON-F-017, DON-F-026 |

## 8. Reverse Feature Traceability
The feature inventory in Section 3 provides an index for backward lookup; the explicit mapping below connects each feature to its underlying goal, workflow and testable outcome in Section 4. No QA test IDs have been invented.

| Feature | Goal(s) | Workflow(s) | Acceptance reference |
|---|---|---|---|
| DON-F-001 | BG-DON-001 | WF-DON-01 | Section 4 / DON-F-001 |
| DON-F-002 | BG-DON-002 | WF-DON-01 | Section 4 / DON-F-002 |
| DON-F-003 | BG-DON-004 | WF-DON-01 | Section 4 / DON-F-003 |
| DON-F-004 | BG-DON-004 | WF-DON-01; WF-DON-02 | Section 4 / DON-F-004 |
| DON-F-005 | BG-DON-004 | WF-DON-02 | Section 4 / DON-F-005 |
| DON-F-006 | BG-DON-004 | WF-DON-02 | Section 4 / DON-F-006 |
| DON-F-007 | BG-DON-004 | WF-DON-02 | Section 4 / DON-F-007 |
| DON-F-008 | BG-DON-004 | WF-DON-02 | Section 4 / DON-F-008 |
| DON-F-009 | BG-DON-004 | WF-DON-02 | Section 4 / DON-F-009 |
| DON-F-010 | BG-DON-004 | WF-DON-02 | Section 4 / DON-F-010 |
| DON-F-011 | BG-DON-004 | WF-DON-03 | Section 4 / DON-F-011 |
| DON-F-012 | BG-DON-007 | WF-DON-03 | Section 4 / DON-F-012 |
| DON-F-013 | BG-DON-007 | WF-DON-03 | Section 4 / DON-F-013 |
| DON-F-014 | BG-DON-007 | WF-DON-03 | Section 4 / DON-F-014 |
| DON-F-015 | BG-DON-007 | WF-DON-03 | Section 4 / DON-F-015 |
| DON-F-016 | BG-DON-007 | WF-DON-03 | Section 4 / DON-F-016 |
| DON-F-017 | BG-DON-007 | WF-DON-10 | Section 4 / DON-F-017 |
| DON-F-018 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-018 |
| DON-F-019 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-019 |
| DON-F-020 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-020 |
| DON-F-021 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-021 |
| DON-F-022 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-022 |
| DON-F-023 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-023 |
| DON-F-024 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-024 |
| DON-F-025 | BG-DON-003 | WF-DON-04 | Section 4 / DON-F-025 |
| DON-F-026 | BG-DON-003; BG-DON-007 | WF-DON-04; WF-DON-10 | Section 4 / DON-F-026 |
| DON-F-027 | BG-DON-008 | WF-DON-05 | Section 4 / DON-F-027 |
| DON-F-028 | BG-DON-002 | WF-DON-06 | Section 4 / DON-F-028 |
| DON-F-029 | BG-DON-005 | WF-DON-07 | Section 4 / DON-F-029 |
| DON-F-030 | BG-DON-005 | WF-DON-07 | Section 4 / DON-F-030 |
| DON-F-031 | BG-DON-006 | WF-DON-08 | Section 4 / DON-F-031 |
| DON-F-032 | BG-DON-008 | WF-DON-09 | Section 4 / DON-F-032 |
| DON-F-033 | BG-DON-008 | WF-DON-09 | Section 4 / DON-F-033 |
| DON-F-034 | BG-DON-008 | WF-DON-09 | Section 4 / DON-F-034 |
| DON-F-035 | BG-DON-004; BG-DON-008 | WF-DON-02; WF-DON-05 | Section 4 / DON-F-035 |

## 9. Pending Decisions and Coverage Gaps
The following Goals BRD decision IDs remain unresolved; this catalogue does not silently approve any of them.

| Decision | Feature impact | Required business decision |
|---|---|---|
| OD-DON-01 | DON-F-019, 025, 026, 033, 034 | Member-to-Donor lifecycle and import object association |
| OD-DON-02 | DON-F-028, 033, 034 | Source precedence, identity resolution and duplicate matching |
| OD-DON-03 | DON-F-006, 031 | Tier thresholds, period, currency, configurator, recalculation |
| OD-DON-04 | DON-F-007–009, 013–016, 029 | KPI, segment and scoring definitions |
| OD-DON-05 | DON-F-020–026 | Save behaviour, donation/processing distinction, validations and payment methods |
| OD-DON-06 | DON-F-032–034 | Template schema, errors, import counts, partial success |
| OD-DON-07 | DON-F-003, 015, 017 | Contents and authorised actions of profile tabs, Add Task, Send Message |
| OD-DON-08 | DON-F-010, 027, 035 | CSV dataset/export privileges and row selection purpose |
| OD-DON-09 | DON-F-001, 025 | Tenant/record-level grants and data protection requirements |
| OD-DON-10 | DON-F-009, 029, 030, 035 | KPI choices and combined filter interaction |

> Future boundary: Full campaign donor outreach and email communication (FUT-DON-001) is a later enhancement. The current Send Message button is catalogued as a visible entry point only, not as a complete communication service.

## 10. Product, Engineering and QA Handoff
- **Product/BA:** confirm the decision log, formal donor/member conversion policy, donation record outcome, terminology and tier/score definitions; then update Goals → Workflow → Features consistently.
- **Engineering/data/integrations:** use the approved features to determine source field ownership, identity reconciliation, tenant isolation, Campaign/Member lookup, record creation and import contracts. No API paths/database schema are mandated here.
- **QA/UAT:** derive tests from the acceptance outcomes in Section 4; extend positive/negative/boundary cases only after unresolved validations, permission checks and formulas are approved.

## 11. Validation Summary
- **Total features:** 35
- **Confirmed:** 28
- **Proposed:** 4
- **Approved assumption:** 3
- **Groups:** Tenant and Navigation (3), Donor Listing (8), Donor Profile (6), Donation Entry (9), Exports and Integrations (2), Proposed Analytics (4), Proposed Import (3)
- **Goal and workflow coverage:** All eight BG-DON goals and all ten WF-DON workflows appear in the coverage tables; applicable rules BR-DON-001…010 are separately indexed. Traceability is at workflow level because precise numbered steps were not universally established for all source records.
- **Known limits:** UI evidence does not prove backend processing, donor counts or score formulas; proposed and assumption-based entries require approval. Material decisions OD-DON-01…10 remain open.
