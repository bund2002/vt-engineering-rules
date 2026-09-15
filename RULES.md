# VT Shared Engineering Rules

Version 1.0.1. These rules govern VT project analysis and newly generated or corrected engineering outputs. Documentation, code enforcement and native validation are separate claims.

## Using the rules

Read this file and the project-specific approved evidence before proposing changes. Explicit user requirements take precedence. Resolve conflicts openly; do not silently adopt a local machine rule or a historical template. Preserve source files and keep unresolved mappings proposed.

## VT-ID-001 Physical labels and controller identities are independent

Preserve physical_label, graphic_object_path, u_base, PLC member, CC and CA separately. SB+ and OR+ digits may differ from the U-base digits. A difference alone is not an error and never authorizes renaming. Validate the association from drawings and controller evidence.

## VT-ID-002 Numeric sequence does not define topology

Preserve drawing and wiring order, including decreasing numbers, gaps, branches and reversals. Never sort beds or infer adjacency by equipment or tag number.

## VT-CAN-001 Resolve CAN and index per bed

Record ECG, ECC, CAN, index, zone, connection direction and source evidence per bed. Adjacent beds may switch CAN, index and feed direction midway through a physical run. Do not increment an index or carry forward ownership without wiring and controller evidence.

## VT-SRC-001 Use authority for each field

Drawings and PDFs establish intended physical layout, labels, wiring and addressing callouts. PLC/controller exports establish implemented members and exposure. DataWorX databases and exports establish configured source paths. Current graphics establish existing geometry and dynamics. No single file proves all fields. Preserve disagreements and revision context.

## VT-PATH-001 RSOPC Gateway for PLC-facing inputs

Every newly generated or corrected PLC-facing input string must use RSOPC Gateway with the evidenced controller/topic and member. RSLinx OPC Server and other legacy PLC server prefixes are not generation defaults. Retain legacy files as evidence; flag unresolved legacy paths for migration rather than release them as compliant outputs.

## VT-PATH-002 Preserve remote routing and aliases per row

Derive local versus remote routing from the DataWorX database, its matching CSV export and verified site configuration. Preserve evidenced <<CN>> and <<CN1>> aliases as distinct bindings. A workbook may alternate aliases by row. Never force a hard-coded IP, flatten all rows to one host, or invent alias bindings.

## VT-PATH-003 Keep path layers distinct

A PLC-facing DataWorX input uses RSOPC Gateway. A reference that reads a remote DataWorX tag uses its evidenced ICONICS.DataWorX32 or other verified product namespace. GraphWorX and AlarmWorX consumers may reference DataWorX. Do not replace a DataWorX or AlarmWorX namespace with RSOPC Gateway. Classify the path role before validation; preserve expression structure and each remote endpoint.

## VT-XLSX-001 Preserve the approved workbook contract

Use the existing approved VT workbook template and output tags.xlsx. Preserve required sheets, headers and column order. Carry the correct local or remote input and alias into each row. Do not add a Remote column or tab unless the import contract explicitly supports it; store routing metadata in the adjacent project synopsis.

## VT-VERIFY-001 Validate mappings before release

Cross-check label-to-tag relationships, per-bed CAN/index ownership, alias bindings, path roles and PLC member exposure against referenced sources. Verify saved workbook rows and corresponding CSV/database values. Unresolved mappings remain proposed; a native file reopen alone does not prove semantic correctness.

## VT-LEARN-001 Promote evidence-backed lessons

Record lesson ID, site, scope, source file hashes and locators, observation, proposed rule, caveats, reviewer, approval and affected versions. A successful site example does not automatically become a universal rule. Keep personnel and implementation dates unknown unless supported.

## VT-SYNC-001 Share rules across hosts with explicit versions

Use the canonical GitHub rules repository and a pinned commit or release in each project. Local desktop Brian, desktop main and laptop Brian profiles contain paths and capabilities only. Host preferences do not override engineering rules. Record rule version in each job and output manifest. If offline, identify the cached version; never claim it is current without checking.

## VT-PUBLIC-001 Publish generalized knowledge separately from site evidence

Public contributions contain generalized rules and synthetic examples only. Keep credentials, real IP mappings, private drawings, customer project files and access tokens in authorized project storage. Link private evidence by internal reference without copying it into the public rules repository.

## Synthetic routing examples

These are syntax illustrations, not verified site paths or actual alias bindings. Confirm the installed product, endpoint and template before generating rows.

```text
Local PLC input: RSOPC Gateway\[CC200]U123456.MF_LAT
Remote PLC input: \\<<CN>>\RSOPC Gateway\[CC200]U123456.MF_LAT
Remote DataWorX reference: \\<<CN1>>\ICONICS.DataWorX32\CA200.U123456_MF_LAT
```

A subsequent row may use <<CN>> where the preceding row uses <<CN1>> if the configuration proves that routing. Alias expansion belongs in protected project configuration. Do not assume CN means the local workstation.

A physical OR+654321 label may be associated with U123456. A following bed may have a lower physical number and belong to a different CAN feed. These differences are not faults by themselves.

## Evidence record for each mapped item

physical_label; graphic_object_path; u_base; controller; cc; ca; ecg; ecc; can; index; zone; direction; input_role; raw_input; server_alias; alias_binding_reference; source_path; source_hash; page_or_row; revision; status; reviewer. Unknown fields are null.

## Rule changes and experience sharing

Use a branch and pull request to propose rules, corrections and sanitized lessons. Give each rule a stable ID; explain scope and counterexamples. The repository owner reviews and merges. Other users can propose changes without direct write access. Add a changelog entry, bump the ruleset version and update pinned consumers after approval. Never silently widen a site-specific exception into a global requirement.

## Runtime adoption status

The initial release establishes shared guidance. Legacy generators, templates and audit checks must be checked separately. A rule download or Copilot instruction file does not patch a running VT executable.
