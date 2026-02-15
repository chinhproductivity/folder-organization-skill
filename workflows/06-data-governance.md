---
description: Rules for file naming, security classification, version control, and data lifecycle.
---

# 06. Data Governance Rules

Standardized rules to ensure data is easy to find, secure, and properly managed.

## 1. Naming Conventions

### General Rule

`YYYY-MM-DD_Project_Description_vX`

- **Date**: ISO format (`2024-03-20`) for chronological sorting.
- **Description**: Short, clear details (replace spaces with `_` or `-`).
- **Version**: `v01`, `v02` (avoid `final`, `new`, `latest`).

### Examples

- `2024-03-20_Proposal_DSS_Mien_Nam_v01.docx` (Good)
- `Proposal final new.docx` (Bad)
- `Meeting_Notes_2024.txt` (Bad - put date first)

## 2. Security Classification

Tag files/folders using these prefixes if strictly necessary, or generally categorize them:

- **[PUBLIC]**: Information suitable for external sharing (Marketing materials, public offers).
- **[INTERNAL]**: Company-wide access (Policies, Templates, Training).
- **[CONFIDENTIAL]**: Restricted access (Salaries, Contracts, Strategy). *Store in secure, restricted folders.*
- **[PERSONAL]**: Private to the individual.

## 3. Version Control

- **Working Drafts**: Use `v01`, `v02`.
- **Final Release**: When a document is signed or published, append `_FINAL` or `_SIGNED`.
- **Old Versions**: Move to an `_Archive` or `_Old` subfolder rather than deleting immediately.

## 4. Folder Structure Standards

- **00-99 Numbering**: Use numbers to control sort order (e.g., `01. Admin`, `02. Projects`).
- **Max Depth**: Try to keep nesting to less than 4 levels deep.
- **Inbox/To-Sort**: Every major area can have a `00_Inbox` for quick dumps, but it must be processed weekly.

## 5. Lifecycle Management

- **Active**: Current year/project files.
- **Reference**: Past projects, kept for reuse.
- **Archive**: >2 years old or closed projects. Move to `Z_Archive` at the end of the year.
- **Delete**: Trivial data (temp files, duplicates) should be deleted monthly.

## 6. Audit Checklist (Quarterly)

- [ ] Are sensitive files in the correct restricted folders?
- [ ] Are old projects moved to Archive?
- [ ] Is the `00_Inbox` empty?
