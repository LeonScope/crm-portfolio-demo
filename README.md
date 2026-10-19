# Scope CRM

### Customer work, with clear ownership.

**Business application · Laravel · Local portfolio demo**

[Deutsch](README.de.md) · [Case study](docs/CASE-STUDY.md) · [Verification](docs/VERIFICATION.md)

A customer record is useful when the next person can see who is responsible, what was discussed and what happens next. Scope CRM brings assignments, appointments, notes and change history into one workspace. Built by **[LeonScope](https://github.com/LeonScope)** with AI assistance as an independent demo using fictional data.

![Scope CRM overview with team responsibilities, appointments and direct CSV import access](assets/dashboard-desktop.png)

## A working day in the CRM

| Work | Visible behavior |
| :--- | :--- |
| Prepare a conversation | Find the customer, review notes and see upcoming appointments. |
| Assign responsibility | Administrators manage the team view; employees work with their assigned customers. The server enforces access. |
| Keep a useful record | Customer and appointment changes are stored together with their history entries. |
| Bring in new customers | Upload a CSV, inspect every row and confirm before anything is imported. |

The revised overview puts customer work ahead of decoration: a compact introduction, a visible role label and direct access to the customer list and administrator import. The green business interface keeps navigation familiar.

## Import with a review step

**Upload → validation and preview → explicit confirmation.** Invalid imports create no customers. Checks cover duplicates, archived records, ownership, expired previews and changed files; imports add new records rather than updating existing ones.

![CSV import preview with validation before confirmation](assets/import-preview-desktop.png)

<details>
<summary><strong>Phone views</strong> — customer search and import errors</summary>

<table><tr>
<td valign="top"><strong>Customer list</strong><br /><img src="assets/customers-mobile.png" width="300" alt="Mobile CRM customer list and search" /></td>
<td valign="top"><strong>Import validation</strong><br /><img src="assets/import-errors-mobile.png" width="300" alt="Mobile CSV preview showing invalid and duplicate rows" /></td>
</tr></table>

</details>

## What this project demonstrates

Role-based workflows, transactional history and a guarded data import in **Laravel 13, PHP 8.4, Blade, SQLite and Vite**. The local demo starts with 40 fictional customers and three generated accounts.

**53 application tests / 430 assertions and four browser workflows passed.** The interface was rechecked on 19 October 2026; the earlier clean-install verification remains documented separately. [Results, environment and limits](docs/VERIFICATION.md).

LeonScope set the portfolio objective, confirmed product direction and scope, and steered the iterations. Codex generated the implementation, interface, synthetic data and tests and performed the documented verification. The CRM itself does not call an AI model.

## Project access

This is a **presentation-only repository** for a functional local application. Source, credentials, databases and installable packages remain private. There is no public hosted application or public application CI. The independent demo contains no former-client code or business data.

No open-source license, Creative Commons license or general reuse permission is granted for original portfolio material. Statutory rights, GitHub platform terms and third-party rights remain unaffected. [Rights notice](RIGHTS.md).

[Case study and interview walkthrough](docs/CASE-STUDY.md) · [Verification](docs/VERIFICATION.md) · [LeonScope](https://github.com/LeonScope)
