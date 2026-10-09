# Standalone AiXPurpose | Donor Management | Members | BRD Feature Catalogue

**Status:** Draft for review  
**Scope:** Donor Management → Members, standalone multi-tenant AiXPurpose  
**Evidence:** User walkthrough and Members screenshots; `Standalone_AiXPurpose_Members_BRD_Goals.md`; `Standalone_AiXPurpose_Members_BRD_Workflow.md`; `master_prompt_brd_feature_catalogue(1).md`.

## Selected Structure

Includes source/scope, atomic feature inventory and specifications, field matrix, forward/reverse traceability, screenshot mapping, decision log, handoff and validation. Omits speculative permission matrices, status-state machines, KPI formulas, source connectors and technical/API design because the supplied requirements do not establish those details.

## 1. Purpose, Classification and Boundaries

The Feature Catalogue converts eight Members business goals (`BG-MEM-001`–`008`), eight Members business rules (`BR-MEM-001`–`008`), and ten related workflows (`WF-MEM-01`–`10`) into testable capabilities. **Confirmed** identifies an explicitly described existing behaviour or product-wide decision, not an independent production verification. **Approved assumption** labels an enhancement expressly proposed by the user, not a current release approval. **Open decision** indicates a rule required before fully specifying certain tests. The source Goals label bulk import and KPI/filter enhancements as proposals; those are deliberately segregated below.

Clients use isolated tenant/workspaces and receive the **same product feature set** (`BR-MEM-001/002`). Tenant-specific member data or chosen displayed KPI values do not mean feature enablement by client. The Members catalogue includes only Members behaviours and the navigation handoff to donation entry. Donation processing, full Donors workflows, Campaigns administration, Segments, Prospecting, and AI Copilot interaction logic are not specified here. Communications remain a **future enhancement** (`BR-MEM-008`).

**ID convention:** `MEM-F-001` onward, assigned only in this document. Existing goal (`BG-MEM-*`), rule (`BR-MEM-*`), workflow (`WF-MEM-*`), enhancement (`PE-MEM-*`) and decision (`OQ-MEM-*`) IDs are preserved.

## 2. Source-backed Feature Inventory

| Feature ID | Feature | Status | Goal ID(s) | Workflow ID(s) | Rule / proposal |
|---|---|---|---|---|---|
| `MEM-F-001` | Tenant-scoped Members workspace | Confirmed | BG-MEM-001 | WF-MEM-01 | BR-MEM-001, BR-MEM-002 |
| `MEM-F-002` | Default active-members listing | Confirmed | BG-MEM-005 | WF-MEM-01, WF-MEM-04 | BR-MEM-004 |
| `MEM-F-003` | Members list columns | Confirmed | BG-MEM-005 | WF-MEM-01, WF-MEM-04 | BR-MEM-004 |
| `MEM-F-004` | Members list pagination | Confirmed | BG-MEM-005 | WF-MEM-04 | BR-MEM-004 |
| `MEM-F-005` | Search members by identity/contact | Confirmed | BG-MEM-005, BG-MEM-007 | WF-MEM-04 | — |
| `MEM-F-006` | Filter Members by donor type | Confirmed | BG-MEM-005, BG-MEM-007 | WF-MEM-04 | — |
| `MEM-F-007` | Filter Members by status | Confirmed | BG-MEM-005, BG-MEM-007 | WF-MEM-04 | BR-MEM-004 |
| `MEM-F-008` | Global cross-module search entry | Confirmed | BG-MEM-005 | WF-MEM-01 | — |
| `MEM-F-009` | Shared notification, account and Copilot entries | Confirmed | BG-MEM-001 | WF-MEM-01 | — |
| `MEM-F-010` | Open Add Member form | Confirmed | BG-MEM-002, BG-MEM-003 | WF-MEM-02 | — |
| `MEM-F-011` | Capture constituent contact details | Confirmed | BG-MEM-003 | WF-MEM-02, WF-MEM-05 | — |
| `MEM-F-012` | Capture address and communication details | Confirmed | BG-MEM-003 | WF-MEM-02, WF-MEM-05 | — |
| `MEM-F-013` | Capture campaign and giving details | Confirmed | BG-MEM-003 | WF-MEM-02, WF-MEM-05 | — |
| `MEM-F-014` | Capture recognition and social details | Confirmed | BG-MEM-003 | WF-MEM-02, WF-MEM-05 | — |
| `MEM-F-015` | Capture advanced and system details | Confirmed | BG-MEM-003 | WF-MEM-02, WF-MEM-05 | — |
| `MEM-F-016` | Save manually entered member | Confirmed | BG-MEM-002, BG-MEM-003 | WF-MEM-02 | BR-MEM-003 |
| `MEM-F-017` | Open prefilled member edit form | Confirmed | BG-MEM-005 | WF-MEM-05 | BR-MEM-006 |
| `MEM-F-018` | Update existing member information | Confirmed | BG-MEM-005 | WF-MEM-05 | BR-MEM-006 |
| `MEM-F-019` | Open profile from row or View action | Confirmed | BG-MEM-005 | WF-MEM-04 | BR-MEM-005 |
| `MEM-F-020` | Display member profile details and summary | Confirmed | BG-MEM-005 | WF-MEM-04 | — |
| `MEM-F-021` | Navigate to donation entry from member list | Confirmed | BG-MEM-008 | WF-MEM-10 | BR-MEM-007 |
| `MEM-F-022` | Navigate to donation entry from member profile | Confirmed | BG-MEM-008 | WF-MEM-10 | BR-MEM-007 |
| `MEM-F-023` | Surface integration-fed member records | Confirmed | BG-MEM-002 | WF-MEM-03 | BR-MEM-003 |
| `MEM-F-024` | Export Members to CSV | Confirmed | BG-MEM-007 | WF-MEM-06 | — |
| `MEM-F-025` | Provide member import entry point | Approved assumption | BG-MEM-004 | WF-MEM-07 | PE-MEM-001, PE-MEM-003 |
| `MEM-F-026` | Supply member import templates | Approved assumption | BG-MEM-004 | WF-MEM-07 | PE-MEM-001 |
| `MEM-F-027` | Accept member file upload | Approved assumption | BG-MEM-004 | WF-MEM-07 | PE-MEM-001 |
| `MEM-F-028` | Validate import-required member data | Approved assumption | BG-MEM-004 | WF-MEM-07 | PE-MEM-001, PE-MEM-002 |
| `MEM-F-029` | Create member records from imported data | Approved assumption | BG-MEM-004 | WF-MEM-07 | PE-MEM-001 |
| `MEM-F-030` | Display import result count | Approved assumption | BG-MEM-004 | WF-MEM-07 | PE-MEM-002 |
| `MEM-F-031` | Review and correct imported member information | Approved assumption | BG-MEM-004, BG-MEM-005 | WF-MEM-07, WF-MEM-05 | PE-MEM-002; existing member edit behaviour |
| `MEM-F-032` | Refresh Members listing | Approved assumption | BG-MEM-004, BG-MEM-005 | WF-MEM-07, WF-MEM-01 | PE-MEM-003 |
| `MEM-F-033` | Filter Members list by selected KPI | Approved assumption | BG-MEM-006 | WF-MEM-08 | PE-MEM-004 |
| `MEM-F-034` | Choose displayed KPI cards | Approved assumption | BG-MEM-006 | WF-MEM-08 | PE-MEM-005 |
| `MEM-F-035` | Offer additional member filters | Approved assumption | BG-MEM-007 | WF-MEM-09 | PE-MEM-006 |
| `MEM-F-036` | Export filtered member subset | Approved assumption | BG-MEM-007 | WF-MEM-09 | PE-MEM-007 |

## 3. Detailed Feature Specifications

Acceptance outcomes below intentionally avoid unsupported error strings, roles, formulas, thresholds and server behaviour. All features inherit tenant isolation (`BR-MEM-001`) and common availability (`BR-MEM-002`); exact role permissions remain `OQ-MEM-005`.

### Workspace and listing

#### MEM-F-001 — Tenant-scoped Members workspace
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-001; WF-MEM-01; BR-MEM-001, BR-MEM-002; Standalone tenant and common-feature decisions.
- **Supported functional behaviour:** Opening Members exposes the current client workspace’s member records; other clients’ member information is outside its accessible data scope. The same Members feature set is available in every tenant.
- **Acceptance outcome:** Given a user is operating in one client workspace, when Members is opened, records displayed belong to that workspace.
- **Open dependencies:** `OQ-MEM-005`.

#### MEM-F-002 — Default active-members listing
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-01, WF-MEM-04; BR-MEM-004; User Members listing walkthrough.
- **Supported functional behaviour:** Initial list displays active members by default; retain distinction from the separate member-status filter.
- **Acceptance outcome:** When Members is first opened, the listing applies the active-only default described by the user.
- **Open dependencies:** `OQ-MEM-002`.

#### MEM-F-003 — Members list columns
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-01, WF-MEM-04; BR-MEM-004; User-supplied Members column headers.
- **Supported functional behaviour:** Display Name, Donor Type, Contact, Location, Member Status, Pledged 2024, Created and Actions.
- **Acceptance outcome:** When the Members list is displayed, the specified headers are available.
- **Open dependencies:** `OQ-MEM-010`.

#### MEM-F-004 — Members list pagination
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-04; BR-MEM-004; User Members listing explanation.
- **Supported functional behaviour:** Provide pagination for member records in the listing. Page size and navigation mechanics are unspecified.
- **Acceptance outcome:** Given records span more than one page, a user can navigate paginated Members results.

#### MEM-F-005 — Search members by identity/contact
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005, BG-MEM-007; WF-MEM-04; User Member list search description.
- **Supported functional behaviour:** Support Members list searching by name, phone and email. Match semantics are unspecified.
- **Acceptance outcome:** When a user searches with a member name, email or phone, the list displays matching member records.

#### MEM-F-006 — Filter Members by donor type
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005, BG-MEM-007; WF-MEM-04; User Members filter description.
- **Supported functional behaviour:** Donor-type filter offers Individual, Organisation, Foundation and an all-types selection.
- **Acceptance outcome:** Selecting Organisation limits the listed records to that donor type.

#### MEM-F-007 — Filter Members by status
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005, BG-MEM-007; WF-MEM-04; BR-MEM-004; User Members filter description.
- **Supported functional behaviour:** Status filter offers Prospect, Pledge, Donated/Donation and Lapsed, plus all-status selection; terminology and Active interaction await approval.
- **Acceptance outcome:** Selecting a defined member status shows records identified with that status, subject to the unresolved Active default interaction.
- **Open dependencies:** `OQ-MEM-001`, `OQ-MEM-002`.

#### MEM-F-008 — Global cross-module search entry
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-01; User common application header description.
- **Supported functional behaviour:** Provide the shared Search Everything entry point, which supports searching beyond Members, including donor or campaign details; result navigation specifics are unspecified.
- **Acceptance outcome:** From Members, the application exposes global search capable of finding information beyond the Members list.

#### MEM-F-009 — Shared notification, account and Copilot entries
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-001; WF-MEM-01; User common header walkthrough.
- **Supported functional behaviour:** Show notification bell, logged-in user/profile and sign-out control, and Copilot entry point. Message behaviour and Copilot answers are outside this page’s defined behaviour.
- **Acceptance outcome:** The stated shared header controls are accessible on Members.
- **Open dependencies:** `OQ-MEM-005`.

### Manual member management

#### MEM-F-010 — Open Add Member form
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-002, BG-MEM-003; WF-MEM-02; User manual creation walkthrough.
- **Supported functional behaviour:** Selecting Add Member opens a new member entry form with the five supplied groups.
- **Acceptance outcome:** When Add Member is selected, the five-section member entry form opens.
- **Open dependencies:** `OQ-MEM-003`.

#### MEM-F-011 — Capture constituent contact details
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-003; WF-MEM-02, WF-MEM-05; User Add Member section 1.
- **Supported functional behaviour:** Capture Donor Type (Individual, Organisation, Foundation), Title, First Name, Last Name, Email and Phone Number. Mandatory-field rules are not supplied.
- **Acceptance outcome:** The creation/edit form provides the stated constituent fields and type options.
- **Open dependencies:** `OQ-MEM-003`.

#### MEM-F-012 — Capture address and communication details
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-003; WF-MEM-02, WF-MEM-05; User Add Member section 2.
- **Supported functional behaviour:** Capture Address, ZIP Code, State, City, Anonymous Donor checkbox and Do Not Solicit option. Their downstream effects are not defined.
- **Acceptance outcome:** The form allows an administrator to enter the stated address information and select the two supplied preferences.
- **Open dependencies:** `OQ-MEM-003`.

#### MEM-F-013 — Capture campaign and giving details
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-003; WF-MEM-02, WF-MEM-05; User Add Member section 3.
- **Supported functional behaviour:** Capture Current Campaign, Current Status (Prospect, Pledge, Donated/Donation, Lapsed), Current Solicitor and Pledged Amount. Campaign catalogue and pledge-calculation rules are not supplied.
- **Acceptance outcome:** The form presents the named campaign/giving fields and documented status options.
- **Open dependencies:** `OQ-MEM-001`, `OQ-MEM-003`.

#### MEM-F-014 — Capture recognition and social details
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-003; WF-MEM-02, WF-MEM-05; User Add Member section 4.
- **Supported functional behaviour:** Capture Donor Publication, Spouse Last Name, Spouse Middle Name, Alternate Phone 1, Alternate Phone Type 1 (e.g. Home/Work) and Alternate Phone 2.
- **Acceptance outcome:** The form presents each named recognition and alternate-contact field.
- **Open dependencies:** `OQ-MEM-003`.

#### MEM-F-015 — Capture advanced and system details
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-003; WF-MEM-02, WF-MEM-05; User Add Member section 5.
- **Supported functional behaviour:** Capture iWave Score, Capacity Score, Propensity Score, Affinity Score, Profile URL, Name of First Guest, Name of Second Guest, Previous Home Number and Alternate Phone Type 2. No score formula or valid score range is specified.
- **Acceptance outcome:** The form exposes the identified advanced/system fields for entry or maintenance.
- **Open dependencies:** `OQ-MEM-003`.

#### MEM-F-016 — Save manually entered member
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-002, BG-MEM-003; WF-MEM-02; BR-MEM-003; User manual creation and listing behaviour.
- **Supported functional behaviour:** Completion of Add Member creates a record in the tenant’s member dataset; its immediate visibility depends on the active-only list filter. Save-time validation and error messaging are unspecified.
- **Acceptance outcome:** When a member is successfully created manually, it is available as a Members record, including through suitable list selection.
- **Open dependencies:** `OQ-MEM-002`, `OQ-MEM-003`.

#### MEM-F-017 — Open prefilled member edit form
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-05; BR-MEM-006; User Edit action clarification.
- **Supported functional behaviour:** Edit opens the same five-section structure as Add Member, populated with the selected member’s existing available details.
- **Acceptance outcome:** When Edit is selected on a member, the creation-form field groups open populated with that member’s available information.
- **Open dependencies:** `OQ-MEM-005`.

#### MEM-F-018 — Update existing member information
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-05; BR-MEM-006; User edit/complete missing data description.
- **Supported functional behaviour:** Permit editing/correcting existing member data and adding previously missing details; define precedence versus later integration updates as an open decision.
- **Acceptance outcome:** When an administrator completes a successful edit, the member profile reflects the updated details.
- **Open dependencies:** `OQ-MEM-003`, `OQ-MEM-009`.

### Member profile and donation link

#### MEM-F-019 — Open profile from row or View action
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-04; BR-MEM-005; User row click and View equivalence.
- **Supported functional behaviour:** Selecting a member row or its View icon opens the same selected-member detail/profile page.
- **Acceptance outcome:** For a given member, row selection and View show the same member detail page.
- **Open dependencies:** `OQ-MEM-005`.

#### MEM-F-020 — Display member profile details and summary
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-005; WF-MEM-04; User profile screenshot and walkthrough.
- **Supported functional behaviour:** Display available member identity, classification/status, constituent/contact data and summary cards Total Donations, Pledged Amount 2024, iWave Score. Specific calculation rules and source provenance display are not confirmed.
- **Acceptance outcome:** When a member profile is opened, available details and the three named summary cards are shown.
- **Open dependencies:** `OQ-MEM-006`, `OQ-MEM-010`.

#### MEM-F-021 — Navigate to donation entry from member list
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-008; WF-MEM-10; BR-MEM-007; User $ action clarification.
- **Supported functional behaviour:** The $ row action redirects from the selected member to the donation-entry page; automatic member preselection is not confirmed.
- **Acceptance outcome:** When the $ action is selected, the user reaches donation entry from the relevant member context.
- **Open dependencies:** `OQ-MEM-008`.

#### MEM-F-022 — Navigate to donation entry from member profile
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-008; WF-MEM-10; BR-MEM-007; User Add Donation clarification.
- **Supported functional behaviour:** Add Donation from a member profile opens donation-entry functionality. Actual payment completion, link persistence and member-status changes belong to the separate donation specification.
- **Acceptance outcome:** When Add Donation is selected on the member profile, donation entry opens.
- **Open dependencies:** `OQ-MEM-001`, `OQ-MEM-008`.

### Integration and extraction

#### MEM-F-023 — Surface integration-fed member records
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-002; WF-MEM-03; BR-MEM-003; User integration-source explanation.
- **Supported functional behaviour:** Member records provided through supported external integrations appear in the consolidated Members dataset/profile with their available fields. Connector configuration, matching, precedence and sync failures are unspecified.
- **Acceptance outcome:** After a supported integration supplies a member record successfully, that member is available in Members for the relevant tenant.
- **Open dependencies:** `OQ-MEM-009`.

#### MEM-F-024 — Export Members to CSV
- **Evidence status:** Confirmed. **Traceability:** BG-MEM-007; WF-MEM-06; User Members Export CSV control.
- **Supported functional behaviour:** Provide Export CSV to export member listing data. The exact row scope (all/paginated/filtered/selected) and columns remain open.
- **Acceptance outcome:** When Export CSV is invoked successfully, a CSV file of Members data is produced.
- **Open dependencies:** `OQ-MEM-005`, `OQ-MEM-007`.

### Proposed import and refresh

#### MEM-F-025 — Provide member import entry point
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004; WF-MEM-07; PE-MEM-001, PE-MEM-003.
- **Supported functional behaviour:** Offer Import near Export CSV on Members for template-based member uploads.
- **Acceptance outcome:** Selecting the proposed Import control opens the member file-import process.
- **Open dependencies:** `OQ-MEM-004`, `OQ-MEM-005`.

#### MEM-F-026 — Supply member import templates
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004; WF-MEM-07; PE-MEM-001.
- **Supported functional behaviour:** Provide a predefined member template for Excel/spreadsheet/CSV uploads with mandatory template fields once approved. Exact columns and versions await decision.
- **Acceptance outcome:** A user can obtain an applicable member import template; its required fields are identifiable once approved.
- **Open dependencies:** `OQ-MEM-004`.

#### MEM-F-027 — Accept member file upload
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004; WF-MEM-07; PE-MEM-001.
- **Supported functional behaviour:** Allow an administrator to upload a completed Excel/spreadsheet/CSV member dataset using the predefined template; accepted extension rules and size limits are not defined.
- **Acceptance outcome:** Given a completed supported template file, when it is uploaded, the member import process accepts the file for processing.
- **Open dependencies:** `OQ-MEM-004`, `OQ-MEM-005`.

#### MEM-F-028 — Validate import-required member data
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004; WF-MEM-07; PE-MEM-001, PE-MEM-002.
- **Supported functional behaviour:** Check imported records against approved mandatory template fields and present issues for review; precise rejection, partial success and duplicate policies are pending.
- **Acceptance outcome:** An import containing missing mandatory information does not silently treat that missing information as complete; the discrepancy is surfaced for administrative review.
- **Open dependencies:** `OQ-MEM-004`.

#### MEM-F-029 — Create member records from imported data
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004; WF-MEM-07; PE-MEM-001.
- **Supported functional behaviour:** Successfully imported member records join the same tenant Members dataset as manually created and integrated members. Updating existing members on import is not yet a confirmed rule.
- **Acceptance outcome:** After a successful member import, imported records are available in the Members dataset, subject to the active-only default.
- **Open dependencies:** `OQ-MEM-002`, `OQ-MEM-004`, `OQ-MEM-009`.

#### MEM-F-030 — Display import result count
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004; WF-MEM-07; PE-MEM-002.
- **Supported functional behaviour:** Present feedback of imported records, such as “250 donor/member records imported” with the actual applicable member count; failure counts and message detail await policy.
- **Acceptance outcome:** After a successful member import, the administrator sees an import success count reflecting the import outcome.
- **Open dependencies:** `OQ-MEM-004`.

#### MEM-F-031 — Review and correct imported member information
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004, BG-MEM-005; WF-MEM-07, WF-MEM-05; BR-MEM-006; PE-MEM-002; existing member edit behaviour.
- **Supported functional behaviour:** Administrators can cross-verify imported member details and use the standard Edit flow to complete/correct data after import.
- **Acceptance outcome:** Given an imported member record, selecting Edit enables corrections to fields as in ordinary member editing.
- **Open dependencies:** `OQ-MEM-003`, `OQ-MEM-004`, `OQ-MEM-005`.

#### MEM-F-032 — Refresh Members listing
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-004, BG-MEM-005; WF-MEM-07, WF-MEM-01; PE-MEM-003.
- **Supported functional behaviour:** Provide Refresh on Members so the user can request an updated view after imports or changes; background sync semantics are not specified.
- **Acceptance outcome:** When Refresh is used after successful new member data is available, the listing reflects the latest accessible dataset consistent with current filters.
- **Open dependencies:** `OQ-MEM-002`, `OQ-MEM-004`.

### Proposed KPIs and analysis

#### MEM-F-033 — Filter Members list by selected KPI
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-006; WF-MEM-08; PE-MEM-004.
- **Supported functional behaviour:** Make displayed KPI cards clickable to show member records relevant to the chosen KPI (e.g. Phone Verified). Exact eligibility formula, filter interaction and reset are pending.
- **Acceptance outcome:** Selecting Phone Verified narrows the Members list to the members represented by that measure once verification criteria are approved.
- **Open dependencies:** `OQ-MEM-006`.

#### MEM-F-034 — Choose displayed KPI cards
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-006; WF-MEM-08; BR-MEM-002; PE-MEM-005.
- **Supported functional behaviour:** Allow users to choose from available Members KPIs for display. All clients have the same feature capability, while the chosen displayed KPIs may differ.
- **Acceptance outcome:** When a user selects an available KPI for display, the Members summary presents that KPI.
- **Open dependencies:** `OQ-MEM-006`.

#### MEM-F-035 — Offer additional member filters
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-007; WF-MEM-09; PE-MEM-006.
- **Supported functional behaviour:** Allow more filtering dimensions when specified by the client, such as member location; the approved filter catalogue and combination rules are pending.
- **Acceptance outcome:** When an approved additional filter is applied, matching Members records are displayed.
- **Open dependencies:** `OQ-MEM-007`.

#### MEM-F-036 — Export filtered member subset
- **Evidence status:** Approved assumption. **Traceability:** BG-MEM-007; WF-MEM-09; PE-MEM-007.
- **Supported functional behaviour:** Export only the member records matching an applied filter/selection, e.g. an approved location criterion; rules for selection and export columns require confirmation.
- **Acceptance outcome:** Given an approved location filter, when a filtered export is requested, the produced CSV contains records matching that criterion.
- **Open dependencies:** `OQ-MEM-005`, `OQ-MEM-007`.

## 4. Manual Entry and Editing Field Matrix

The user supplied these fields as present in the Add Member form; **mandatory indicators, constraints and type-dependent rules are not specified** (`OQ-MEM-003`). The same groups apply to Edit (`BR-MEM-006`).

| Form section | Fields and known options | Covered by |
|---|---|---|
| Constituent Contact Information | Donor Type: Individual, Organisation, Foundation; Title; First Name; Last Name; Email; Phone Number | MEM-F-011 |
| Address and Communication | Address; ZIP Code; State; City; Anonymous Donor; Do Not Solicit | MEM-F-012 |
| Campaign & Giving | Current Campaign; Current Status: Prospect, Pledge, Donated/Donation, Lapsed; Current Solicitor; Pledged Amount | MEM-F-013 |
| Recognition & Social | Donor Publication; Spouse Last Name; Spouse Middle Name; Alternate Phone 1; Alternate Phone Type 1 (e.g. Home, Work); Alternate Phone 2 | MEM-F-014 |
| Advanced / System Fields | iWave Score; Capacity Score; Propensity Score; Affinity Score; Profile URL; Name of First Guest; Name of Second Guest; Previous Home Number; Alternate Phone Type 2 | MEM-F-015 |

**Terminology conflict:** *Donation* versus *Donated* (and *Pledge* versus *Pledged*) is not silently standardised. **Active** is a described default listing criterion, but its relation to these status values has not been confirmed (`OQ-MEM-001/002`).

## 5. Goals → Workflows → Features (Forward Traceability)

| Business goal / rule | Relevant workflow(s) | Supporting feature(s) | Coverage / decision |
|---|---|---|---|
| BG-MEM-001 | WF-MEM-01 | MEM-F-001, MEM-F-009 | Existing/confirmed coverage plus proposals where noted |
| BG-MEM-002 | WF-MEM-02, WF-MEM-03 | MEM-F-010, MEM-F-016, MEM-F-023 | Existing/confirmed coverage plus proposals where noted |
| BG-MEM-003 | WF-MEM-02, WF-MEM-05 | MEM-F-010, MEM-F-011, MEM-F-012, MEM-F-013, MEM-F-014, MEM-F-015, MEM-F-016 | Existing/confirmed coverage plus proposals where noted |
| BG-MEM-004 | WF-MEM-01, WF-MEM-05, WF-MEM-07 | MEM-F-025, MEM-F-026, MEM-F-027, MEM-F-028, MEM-F-029, MEM-F-030, MEM-F-031, MEM-F-032 | Proposed enhancement-dependent |
| BG-MEM-005 | WF-MEM-01, WF-MEM-04, WF-MEM-05, WF-MEM-07 | MEM-F-002, MEM-F-003, MEM-F-004, MEM-F-005, MEM-F-006, MEM-F-007, MEM-F-008, MEM-F-017, MEM-F-018, MEM-F-019, MEM-F-020, MEM-F-031, MEM-F-032 | Existing/confirmed coverage plus proposals where noted |
| BG-MEM-006 | WF-MEM-08 | MEM-F-033, MEM-F-034 | Proposed enhancement-dependent |
| BG-MEM-007 | WF-MEM-04, WF-MEM-06, WF-MEM-09 | MEM-F-005, MEM-F-006, MEM-F-007, MEM-F-024, MEM-F-035, MEM-F-036 | Existing/confirmed coverage plus proposals where noted |
| BG-MEM-008 | WF-MEM-10 | MEM-F-021, MEM-F-022 | Existing/confirmed coverage plus proposals where noted |
| BR-MEM-001 | Cross-cutting / no current workflow | All tenant-scoped Members features (shared constraint) | Confirmed rule / cross-cutting constraint |
| BR-MEM-002 | Cross-cutting / no current workflow | All tenant-scoped Members features (shared constraint) | Confirmed rule / cross-cutting constraint |
| BR-MEM-003 | WF-MEM-02, WF-MEM-03 | MEM-F-016, MEM-F-023 | Confirmed rule / cross-cutting constraint |
| BR-MEM-004 | WF-MEM-01, WF-MEM-04 | MEM-F-002, MEM-F-003, MEM-F-004, MEM-F-007 | Confirmed rule / cross-cutting constraint |
| BR-MEM-005 | WF-MEM-04 | MEM-F-019 | Confirmed rule / cross-cutting constraint |
| BR-MEM-006 | WF-MEM-05, WF-MEM-07 | MEM-F-017, MEM-F-018, MEM-F-031 | Confirmed rule / cross-cutting constraint |
| BR-MEM-007 | WF-MEM-10 | MEM-F-021, MEM-F-022 | Confirmed rule / cross-cutting constraint |
| BR-MEM-008 | Cross-cutting / no current workflow | No current execution feature; donor communications are future-only | Future boundary |

## 6. Workflow → Features Mapping

| Workflow | Relevant features | Notes |
|---|---|---|
| WF-MEM-01 | MEM-F-001, MEM-F-002, MEM-F-003, MEM-F-008, MEM-F-009, MEM-F-032 | Source-backed workflow; exceptions may remain open |
| WF-MEM-02 | MEM-F-010, MEM-F-011, MEM-F-012, MEM-F-013, MEM-F-014, MEM-F-015, MEM-F-016 | Source-backed workflow; exceptions may remain open |
| WF-MEM-03 | MEM-F-023 | Source-backed workflow; exceptions may remain open |
| WF-MEM-04 | MEM-F-002, MEM-F-003, MEM-F-004, MEM-F-005, MEM-F-006, MEM-F-007, MEM-F-019, MEM-F-020 | Source-backed workflow; exceptions may remain open |
| WF-MEM-05 | MEM-F-011, MEM-F-012, MEM-F-013, MEM-F-014, MEM-F-015, MEM-F-017, MEM-F-018, MEM-F-031 | Source-backed workflow; exceptions may remain open |
| WF-MEM-06 | MEM-F-024 | Source-backed workflow; exceptions may remain open |
| WF-MEM-07 | MEM-F-025, MEM-F-026, MEM-F-027, MEM-F-028, MEM-F-029, MEM-F-030, MEM-F-031, MEM-F-032 | Proposed workflow, subject to decisions |
| WF-MEM-08 | MEM-F-033, MEM-F-034 | Proposed workflow, subject to decisions |
| WF-MEM-09 | MEM-F-035, MEM-F-036 | Proposed workflow, subject to decisions |
| WF-MEM-10 | MEM-F-021, MEM-F-022 | Source-backed workflow; exceptions may remain open |

## 7. Reverse Feature Traceability

The **Feature Inventory** (section 2) provides each feature’s source-backed goal/workflow links, and the **Detailed Specifications** (section 3) provide its testable acceptance outcome. The following compact reverse index ties each feature to its evidence and acceptance location; no external QA/UAT test IDs were supplied.

| Feature ID | Evidence source | Goal/workflow and testable outcome |
|---|---|---|
| MEM-F-001 | Standalone tenant and common-feature decisions | Inventory §2; acceptance in §3/MEM-F-001 |
| MEM-F-002 | User Members listing walkthrough | Inventory §2; acceptance in §3/MEM-F-002 |
| MEM-F-003 | User-supplied Members column headers | Inventory §2; acceptance in §3/MEM-F-003 |
| MEM-F-004 | User Members listing explanation | Inventory §2; acceptance in §3/MEM-F-004 |
| MEM-F-005 | User Member list search description | Inventory §2; acceptance in §3/MEM-F-005 |
| MEM-F-006 | User Members filter description | Inventory §2; acceptance in §3/MEM-F-006 |
| MEM-F-007 | User Members filter description | Inventory §2; acceptance in §3/MEM-F-007 |
| MEM-F-008 | User common application header description | Inventory §2; acceptance in §3/MEM-F-008 |
| MEM-F-009 | User common header walkthrough | Inventory §2; acceptance in §3/MEM-F-009 |
| MEM-F-010 | User manual creation walkthrough | Inventory §2; acceptance in §3/MEM-F-010 |
| MEM-F-011 | User Add Member section 1 | Inventory §2; acceptance in §3/MEM-F-011 |
| MEM-F-012 | User Add Member section 2 | Inventory §2; acceptance in §3/MEM-F-012 |
| MEM-F-013 | User Add Member section 3 | Inventory §2; acceptance in §3/MEM-F-013 |
| MEM-F-014 | User Add Member section 4 | Inventory §2; acceptance in §3/MEM-F-014 |
| MEM-F-015 | User Add Member section 5 | Inventory §2; acceptance in §3/MEM-F-015 |
| MEM-F-016 | User manual creation and listing behaviour | Inventory §2; acceptance in §3/MEM-F-016 |
| MEM-F-017 | User Edit action clarification | Inventory §2; acceptance in §3/MEM-F-017 |
| MEM-F-018 | User edit/complete missing data description | Inventory §2; acceptance in §3/MEM-F-018 |
| MEM-F-019 | User row click and View equivalence | Inventory §2; acceptance in §3/MEM-F-019 |
| MEM-F-020 | User profile screenshot and walkthrough | Inventory §2; acceptance in §3/MEM-F-020 |
| MEM-F-021 | User $ action clarification | Inventory §2; acceptance in §3/MEM-F-021 |
| MEM-F-022 | User Add Donation clarification | Inventory §2; acceptance in §3/MEM-F-022 |
| MEM-F-023 | User integration-source explanation | Inventory §2; acceptance in §3/MEM-F-023 |
| MEM-F-024 | User Members Export CSV control | Inventory §2; acceptance in §3/MEM-F-024 |
| MEM-F-025 | PE-MEM-001, PE-MEM-003 | Inventory §2; acceptance in §3/MEM-F-025 |
| MEM-F-026 | PE-MEM-001 | Inventory §2; acceptance in §3/MEM-F-026 |
| MEM-F-027 | PE-MEM-001 | Inventory §2; acceptance in §3/MEM-F-027 |
| MEM-F-028 | PE-MEM-001, PE-MEM-002 | Inventory §2; acceptance in §3/MEM-F-028 |
| MEM-F-029 | PE-MEM-001 | Inventory §2; acceptance in §3/MEM-F-029 |
| MEM-F-030 | PE-MEM-002 | Inventory §2; acceptance in §3/MEM-F-030 |
| MEM-F-031 | PE-MEM-002; existing member edit behaviour | Inventory §2; acceptance in §3/MEM-F-031 |
| MEM-F-032 | PE-MEM-003 | Inventory §2; acceptance in §3/MEM-F-032 |
| MEM-F-033 | PE-MEM-004 | Inventory §2; acceptance in §3/MEM-F-033 |
| MEM-F-034 | PE-MEM-005 | Inventory §2; acceptance in §3/MEM-F-034 |
| MEM-F-035 | PE-MEM-006 | Inventory §2; acceptance in §3/MEM-F-035 |
| MEM-F-036 | PE-MEM-007 | Inventory §2; acceptance in §3/MEM-F-036 |

## 8. Screenshot / UI Evidence Index

| UI ID | Supplied image | Evidence used | Limitations |
|---|---|---|---|
| UI-01 | `image(20261009-094934).png` | Application navigation and Donor Management → Members boundary; MEM-F-001 | UI cannot prove tenant access enforcement. |
| UI-02 | `image(20261009-101351).png` | Members list/KPI controls and columns; MEM-F-002–007, 010 | Visible values do not confirm filter algorithms or save logic. |
| UI-03 | `image(20261009-110406).png` | Member profile details and summary; MEM-F-019–022 | Source attribution, formulas and donation persistence cannot be inferred. |

Files were supplied as separate images. The names above are factual source references rather than fabricated relative links within this standalone Markdown document. Detailed Add Member field inventory is additionally supported by the user’s written walkthrough.

## 9. Open Decisions and Coverage Gaps

| Decision | Clarification required | Affected features |
|---|---|---|
| OQ-MEM-001 | Define Member/Donor/Prospect and status conversion semantics | 007,013,022 |
| OQ-MEM-002 | Define Active default and relationship to status filtering / newly created records | 002,007,016,029,032 |
| OQ-MEM-003 | Confirm mandatory fields, field validation, type-dependent applicability and cancellation | 010–018,031 |
| OQ-MEM-004 | Approve import templates, duplicate/match handling, partial success and error resolution | 025–032 |
| OQ-MEM-005 | Approve view/create/edit/import/export/donation authorisation and record visibility | 001,009,010,017,021,022,024,025,027,031,036 |
| OQ-MEM-006 | Define KPI formulas, selectable measures, click-filter precedence and reset | 020,033,034 |
| OQ-MEM-007 | Define additional filtering dimensions, combination and CSV export row scope | 024,035,036 |
| OQ-MEM-008 | Define donation-entry member prefill and saved donation effects | 021,022 |
| OQ-MEM-009 | Identify supported connectors, matching, update ownership, source attribution and conflicts | 018,023,029 |
| OQ-MEM-010 | Replace or contextualise Pledged 2024 without assuming a year selector | 003,020 |
| OQ-MEM-011 | Supply business success metrics if required; no numerical target is supplied | Goals-level; not a feature prerequisite |

**Not established by supplied requirements:** a concrete RBAC matrix, field-level required markers, duplicate-matching policy, data-source precedence, integration retry behaviour, imported-record rejection policy, KPI formulas, current-year pledge calculation, export CSV row-selection precedence, audit event catalogue, notification triggers or AI Copilot response rules. These have not been introduced as confirmed capabilities.

## 10. Technical, Story and QA Handoff

Engineering handoff should address tenant-scoped persistence/access behaviour, member create/edit fields, existing integration data provenance, listing/query consistency, download semantics and donation-navigation context where corresponding decisions are approved. For the proposed import, KPI drill-down and enhanced filtering flows, define operational policies before detailed API/data contracts or exhaustive QA cases. Stories and tests should reference the feature IDs rather than renumbering them.

## 11. Validation Summary

- **Feature count:** 36 features, of which 24 are classified Confirmed (existing behaviour or confirmed product decision) and 12 are Approved assumption proposals. Future donor communications are deliberately excluded from current execution features.
- **Capability groups:** Workspace and listing; Manual member management; Member profile and donation link; Integration and extraction; Proposed import and refresh; Proposed KPIs and analysis.
- **Coverage:** Eight business goals, eight business rules and ten workflows are indexed; `BR-MEM-008` is intentionally a future-only boundary. Proposed goals and workflows retain their non-baseline classification.
- **Outstanding decisions:** `OQ-MEM-001`–`011` from BRD Goals remain open. No unsupported data-policy, security or recovery behaviour was silently added.
- **Next step:** Confirm decisions affecting validation, import, KPI definitions and permissions before deriving final implementation stories and QA/UAT scenarios.
