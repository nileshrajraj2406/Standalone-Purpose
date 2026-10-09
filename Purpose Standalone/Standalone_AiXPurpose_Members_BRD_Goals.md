# Standalone AiXPurpose | Donor Management | Members | BRD Goals

**Status:** Draft for review  
**Scope:** Standalone AiXPurpose, Donor Management → Members  
**Basis:** User-supplied AiXPurpose prototype screenshots, page walkthroughs, standalone product clarifications, and `master_prompt_brd_goals.md`.

## Selected Structure

This document covers purpose, context, goals, product positioning, scope, actors, confirmed business rules, information boundaries, dependencies, proposed enhancements, open decisions, and traceability. It deliberately leaves detailed form logic, click-by-click flows, validations, exception handling, and acceptance criteria to **BRD Workflow** and **BRD Feature Catalogue**. Numerical business success targets and technical architecture details have not been supplied and are not fabricated.

## 1. Purpose

Define the business goals and boundaries for making the **Members** page of AiXPurpose reusable across multiple independent client organisations. This is the first document in the sequence **BRD Goals → BRD Workflow → BRD Feature Catalogue**.

## 2. Business Context and Problem

The existing AiXPurpose application was built for a specific client to consolidate member, donor, and donation-related information from multiple external software applications into one platform. The Members page already supports manual member creation and displays consolidated member records.

A standalone AiXPurpose product must also serve organisations that do not use donation-source integrations, organisations that maintain records in files, and organisations that primarily want to examine their data through simple lists and visualisations. The product must therefore support differing ways of supplying and reviewing member data without becoming a bespoke application for each client.

**Product-wide confirmed decisions:** Every client has an isolated tenant/workspace and access to its own data; every client receives the same feature set. Client-specific data and settings are not the same as enabling or disabling product features.

## 3. Business Goals and Desired Outcomes

| Goal ID | Business goal | Desired outcome | Basis / classification |
|---|---|---|---|
| BG-MEM-001 | Make member management usable beyond the original client. | Different client organisations can use a common Members capability within their own isolated workspace. | Confirmed standalone product objective and tenancy decision. |
| BG-MEM-002 | Consolidate member information from supported source methods. | Administrators can review members received through integrations and entered manually in one Members list. | Confirmed existing behaviour. |
| BG-MEM-003 | Reduce dependence on integrated third-party systems. | A client without external integrations can still maintain its members directly in AiXPurpose. | Confirmed requirement for standalone use. |
| BG-MEM-004 | Enable efficient onboarding of existing member datasets. | Administrators can bring in member data through predefined spreadsheet/CSV templates, with import feedback and subsequent review or correction. | **Proposed enhancement / authorised assumption**, not confirmed existing functionality. |
| BG-MEM-005 | Make member records discoverable and maintainable. | Authorised users can find, inspect, and update member information using the Members list and profile. | Confirmed existing Members page behaviour; specific access permissions remain open. |
| BG-MEM-006 | Make member metrics actionable. | Users can select useful available KPIs and use a KPI to narrow the member list to matching records. | **Proposed enhancement**; current four KPI cards are shown in the prototype. |
| BG-MEM-007 | Support focused member analysis and extraction. | Users can search and filter relevant member data and export the records they intend to review. | Existing search, filters, and CSV export; **filtered export and additional filters proposed**. |
| BG-MEM-008 | Preserve the connection from a member record to donation activity. | Users can initiate donation entry from a member row or profile, with the selected member as the intended context. | Confirmed navigation/actions; exact record association after saving is to be confirmed. |

### 3.1 Business Objectives and Success Measures

The supplied material identifies desired capabilities and on-screen KPI names but **does not specify numerical adoption, accuracy, processing-time, import-success, or fundraising performance targets for this initiative**. Such targets require separate approval; the prototype's sample KPI values are not project success targets.

## 4. Business Capability and Product Positioning

**Members** is the constituent/member record management capability within **Donor Management**. It provides a single view of member details, status, contact information, campaign-related fields, and the entry point to donation activity.

For the standalone product, the same Members functionality must be available to every client within its own tenant, whether records originate through integrations, manual input, or the proposed bulk-import path.

The Member and Donor concepts must remain distinct: the Members page maintains member details, while the Donors page supports donor records and donation entry based on selecting a member. The precise membership-to-donor relationship remains a business decision to define.

## 5. Stakeholders and Actors

| Actor / stakeholder | Supported involvement | Unresolved boundary |
|---|---|---|
| Client organisation | Uses AiXPurpose within its isolated tenant/workspace. | Tenant ownership and account administration details are not specified. |
| Administrator | Creates and edits members; proposed user of import, verification, and filtered export capabilities. | Exact permissions and access scope are not specified. |
| Application user | Searches, filters, views members, and uses displayed page functions as permitted. | Role definitions and authorisations are not specified. |
| External source application | Supplies member data through existing integrations. | Connector list, sync cadence, and system-of-record policies are not specified. |

## 6. In Scope: Members Page

### 6.1 Existing prototype capabilities described or shown

- Member records originating from integrations and manual member creation appear in the Members list.
- Members listing with search by **name, email, or phone**, donor-type and member-status filters, and pagination.
- Donor-type options: **Individual, Organisation, Foundation**.
- Member-status options described as **Prospect, Pledge, Donated/Donation, Lapsed**; final terminology requires confirmation.
- Default listing behaviour stated by the user: **active members only**.
- Current list columns: **Name, Donor Type, Contact, Location, Member Status, Pledged 2024, Created, Actions**.
- Current top KPI cards: **Total Members, Conversion Ready, Email Verified, Phone Verified**.
- **Export CSV**, **Add Member**, and a global **Search everything** control that can search beyond the Members page.
- Member entry/editing across five existing form sections: **Constituent Contact Information; Address and Communication; Campaign & Giving; Recognition & Social; Advanced / System Fields**.
- Clicking a member row or the **View** action opens the same Member Detail/Profile page. **Edit** opens the Add Member form structure with existing data to update. The **$** row action and profile **Add Donation** take the user to donation entry.
- Member profile shows classification/status, contact information, **Total Donations**, **Pledged Amount 2024**, and **iWave Score**; the details available depend on the record.
- Shared application header: global search, notifications, logged-in user/profile/sign-out, and **AI Copilot** entry point. AI Copilot behaviour has not been defined for this page.

### 6.2 Proposed standalone product enhancements (not yet approved as existing)

| Ref | Proposal | Business purpose |
|---|---|---|
| PE-MEM-001 | Predefined template-based member import from Excel/spreadsheet/CSV, with mandatory columns. | Allow clients to initialise or update member records without integration or one-by-one entry. |
| PE-MEM-002 | Import confirmation showing processed/successful counts; administrator review and correction of incomplete or inaccurate records. | Make bulk uploads understandable and correctable. |
| PE-MEM-003 | **Import** action on Members page and **Refresh** action for updated listing data. | Make the proposed bulk-import route and latest results accessible. |
| PE-MEM-004 | Clickable KPI cards that filter the Members list to matching records. | Convert summary metrics into directly reviewable subsets. |
| PE-MEM-005 | User-selectable Members KPIs from a defined set of available measures. | Allow users to focus on relevant member metrics without changing the product feature set by tenant. |
| PE-MEM-006 | Additional Members filters based on approved client needs and data availability. | Support more precise investigation and reporting. |
| PE-MEM-007 | Export only the records matching an applied selection/filter (for example, location). | Support targeted operational extracts. |

**Future enhancement boundary:** Donor communications such as campaign email outreach are intended as a future product enhancement; they are not part of the current Members-page core release definition.

## 7. Out of Scope and Boundaries

- Detailed specification of **Donors**, **Segments**, **Prospecting**, or other modules/pages as independent modules. The related **Add Donation** path is in scope only as a Members-page dependency.
- Detailed design of Campaigns, Donations, integrations, messaging, or AI Copilot beyond what is needed to identify Members-page dependencies.
- Donor communication execution in the current core release; it is a **future enhancement**.
- Client-specific enable/disable feature packaging; the confirmed decision is the **same feature set for every client**.
- Detailed technical designs, API contracts, schemas, deployment specifications, screen validations, or QA test cases in this **Goals** document.

## 8. Confirmed Business Rules and Constraints

| Rule ID | Confirmed rule or constraint | Source basis | Handoff impact |
|---|---|---|---|
| BR-MEM-001 | Each client uses an isolated tenant/workspace and has isolated access to its own data. | User's standalone product clarification. | Apply the tenant boundary across Members workflows and features. |
| BR-MEM-002 | Every client receives the same application feature set. | User's standalone product clarification. | Settings/data may differ, but do not define optional per-client feature packages. |
| BR-MEM-003 | Member records can be created manually and received from external integrations. | Members walkthrough. | Define record creation and visibility for each confirmed source. |
| BR-MEM-004 | The Members list displays **active members by default**, as stated by the user. | Members walkthrough. | Define how Active relates to the documented status values. |
| BR-MEM-005 | Clicking a member row and clicking that row's **View** icon lead to the same Member Detail page. | Members row-action clarification. | Ensure equivalent navigation outcomes. |
| BR-MEM-006 | Editing a member opens the same form structure as Add Member, populated for modification. | Members row-action clarification. | Define update path against current member details. |
| BR-MEM-007 | Members list row **$** and profile **Add Donation** provide access to donation entry. | Members row-action and profile walkthroughs. | Define member context and donation association downstream. |
| BR-MEM-008 | Donor communications are reserved for a future enhancement. | User's standalone product clarification. | Do not assume communication execution in current Members workflows. |

The bulk-upload template, mandatory import fields, KPI interaction, additional filters, and filtered export remain **proposals**, not confirmed rules.

## 9. Member Information Boundaries and Dependencies

- **Data sources:** External integrations and direct manual entry are confirmed; template-based bulk import is proposed.
- **Member information:** The five sections in the existing Add Member form establish the current field groups. Exact field-level requirements belong to the Feature Catalogue. Some fields relate to campaigns, pledges, contact preferences, scoring, and recognition.
- **Campaign dependency:** Member entry includes current campaign and related giving fields. The source and maintenance rules for those reference values have not been fully specified.
- **Donation dependency:** Member profiles and actions refer to total donations, pledges, and donation entry; how donations update member status and measures needs confirmation.
- **Provenance:** The user wants visibility into which source application supplied donation information. The exact display placement and origin rules have not been defined; do not assume it is a current Members KPI.
- **Global search and AI Copilot:** Shown as shared controls. Their search authorisation, question-handling, and cross-tenant limits are not described; no behaviour is invented here.
- **Tenant boundary:** Member data and access belong to the relevant isolated client workspace. The physical data-storage implementation is not specified.

## 10. Open Questions and Decisions Required

| ID | Decision needed | Why it matters |
|---|---|---|
| OQ-MEM-001 | What is the approved business distinction between **Member**, **Donor**, **Prospect**, and a member who has donated? | Governs status updates, conversion, and the relationship to the Donors page. |
| OQ-MEM-002 | What does **Active** mean for the default Members list, given the documented Prospect/Pledge/Donated/Lapsed statuses? | Prevents inconsistent default filtering and counts. |
| OQ-MEM-003 | Which fields are mandatory for manual member creation and each donor type? | Needed for forms and validation. |
| OQ-MEM-004 | For proposed bulk import, what template fields, file formats, mapping rules, duplicate checks, rejection/partial-success handling, and correction process are required? | Needed before confirming import workflow and features. |
| OQ-MEM-005 | Which user roles may see, create, edit, import, export, or initiate donation activity, and are there data visibility restrictions? | Needed to authorise page actions safely. |
| OQ-MEM-006 | Which KPIs may be selected, how is **Conversion Ready** defined, and do KPI clicks combine with or replace existing filters? | Needed for reliable metric calculations and drill-downs. |
| OQ-MEM-007 | Which additional filters and export selection rules must be supported? | Needed to turn a general enhancement idea into testable behaviour. |
| OQ-MEM-008 | When a donation is started from a member, is the member preselected and how does a saved donation affect the Members profile/status/KPIs? | Needed for consistent cross-page behaviour. |
| OQ-MEM-009 | Which integrations are supported for the standalone product, and how are matching, updates, source attribution, and sync conflicts handled? | Needed for consolidation across varied client source systems. |
| OQ-MEM-010 | What do the year-specific **Pledged 2024** list column and **Pledged Amount 2024** profile card represent in a reusable standalone product? | Avoids hard-coding a year or assuming an unapproved date-period control. |
| OQ-MEM-011 | What are the approved success measures for Members functionality? | Required before documenting measurable business targets. |

## 11. Traceability and Downstream Handoff

| Source topic supplied by user | Goals / rules | BRD Workflow to elaborate | BRD Feature Catalogue to define |
|---|---|---|---|
| Standalone multi-client goal; isolated tenants; same features | BG-MEM-001, BR-MEM-001, BR-MEM-002 | Tenant-scoped Members access and record operations | Tenant-bound record access and settings requirements, once confirmed |
| Multiple integrations and manual member entry | BG-MEM-002, BG-MEM-003, BR-MEM-003 | External-source appearance; manual create/update | Member form, list refresh, source mapping and record handling where specified |
| Proposed Excel/CSV import and correction | BG-MEM-004, PE-MEM-001–003 | Import, review, error and correction paths | Template, upload, results, validations and status requirements after decisions |
| List, search, filters, profile, edit/view | BG-MEM-005, BR-MEM-004–006 | Find, view, update, pagination | Fields, list columns, filters, and actions |
| KPI cards and proposed selection/drill-down | BG-MEM-006, PE-MEM-004–005 | KPI-to-list exploration | KPI definitions, selection, link/filter behaviour |
| CSV export and proposed targeted filtering/export | BG-MEM-007, PE-MEM-006–007 | Filter and extract | Export data scope, filter combinations, availability |
| Row $ and profile Add Donation | BG-MEM-008, BR-MEM-007 | Start donation from member | Navigation context and association after decision |

Traceability references above are **document-local**. Workflow and Feature Catalogue identifiers will be assigned in their own documents; unconfirmed associations will not be presented as approved requirements.

## 12. Relationship to Next Documents

1. **BRD Workflow – Members:** Describe the supported end-to-end member journeys, including viewing, creating, updating, search/filter/export, integration-fed data, proposed import, donation handoff, alternate/error paths, and applicable tenant boundaries. Mark unresolved decisions rather than guessing.
2. **BRD Feature Catalogue – Members:** Convert approved workflows into atomic capabilities with precise fields, conditions, permissions, states, validations, and acceptance criteria only when supported by evidence or subsequent approvals.

## 13. Validation Summary

- **Confirmed:** Existing Members page behaviours described above; standalone isolated workspaces; common feature set for every tenant; future-only donor communications.
- **Proposed, not yet approved as existing:** Member file import, refresh, configurable/clickable KPIs, additional filters, and filtered export.
- **Material open decisions:** Member/donor definitions and status semantics; role permissions; bulk import policies; KPI calculations; record matching; year-specific pledge display; donation association.
- **Source contradictions/ambiguities:** The user uses **Donation/Donated** and **Pledge/Pledged** inconsistently as status labels; the active-only default is not reconciled with the four stated member statuses. These are intentionally left open.
- **Traceability:** Goal and rule IDs are provided; later workflow/feature IDs await creation. No unsupported completion claim is made.
