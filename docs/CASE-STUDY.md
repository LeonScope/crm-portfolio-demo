# CRM Portfolio Demo — case study

[Deutsch](CASE-STUDY.de.md) · [Project overview](../README.md) · [Verification](VERIFICATION.md)

An independent, AI-assisted Laravel CRM by **LeonScope**. It demonstrates a complete customer workflow with server-side permissions, appointments, activity history and a confirmed CSV import. It runs locally with synthetic data and no external business service.

## The problem

A small sales or service team needs one place to answer four questions: Who is the customer? Who is responsible? What was discussed? What happens next? The same workflow must remain consistent when responsibility changes, customers are archived or a spreadsheet is imported.

The demo translates that scenario into a deliberately bounded application: one team, two roles and a small number of connected workflows. It makes the behavior inspectable without relying on a previous client's source code or data.

## The working solution

An administrator can assign customers and manage the entire customer set. Employees can read and edit only their own active customers. Notes and appointments stay attached to the customer, and reassignment changes access immediately. Archive and restore preserve the history.

CSV import follows **upload → preview → confirmation**. All rows must be valid. Duplicates, stale assignments, expired previews and changed files prevent import. A successful confirmation writes all customers and their activity entries in one transaction; a failed audit write rolls the whole operation back. Repeating confirmation does not create another set of customers.

![CSV review before confirmation](../assets/import-preview-desktop.png)

## Engineering decisions

| Decision | Reason and tradeoff |
| --- | --- |
| Laravel, Blade and a single application | Keeps authentication, validation, views and domain rules together. A separate SPA/API would add boundaries without improving this demo's workflow. |
| SQLite | A reviewer can run the project without a database service. MySQL and high-concurrency production behavior are not claimed. |
| Policies and scoped queries | Direct URLs and writes use the same ownership/archive rules as the interface. Hiding a control is not sufficient. |
| Shared field validation | Customer forms and CSV rows apply the same field limits, status values and email uniqueness rules. |
| Transactional writes with activity history | A business change and its audit entry succeed together. History is application-level traceability, not protection against a database administrator. |
| Private, expiring CSV previews | Uploaded bytes remain outside web-served paths. A content hash binds confirmation to the checked file. Cleanup failures remain tracked for retry. |
| UTC throughout | Avoids implicit time-zone conversion in this small demo; a future localized calendar would need a separate time-zone design. |

## Evidence and lessons

The local application suite contains **53 tests and 430 assertions**. Four browser workflows cover the customer lifecycle, permissions, keyboard navigation, mobile layouts and CSV import. The [verification record](VERIFICATION.md) identifies the source revisions and actual run scope. These are engineering checks, not claims about production adoption or business savings.

Two concrete implementation lessons emerged: an audit field named `changes` collided with Eloquent's internal property and required explicit attribute access; cleanup needed stable ID-based pagination so processed batches did not cause later ones to be skipped. Regression tests cover both behaviors. Invalid imports and simulated write failures are tested alongside the happy path.

## Role and AI-assisted working method

LeonScope selected the portfolio purpose, approved the independent product direction and functional scope, and guided the iterations. Codex generated the implementation, interface, fixtures and tests and ran the recorded checks. The repository documents this assistance rather than presenting the generated code as entirely hand-written.

The demonstrable work is requirements-to-product development with explicit boundaries, verifiable behavior and documented corrections. This CRM does not call an AI model or claim an AI feature. LeonScope's earlier robotics and machine-vision experience is separate professional background; this demo is a new web application.

## Walkthrough for an individual presentation

1. Start the demo and show the dashboard with 40 synthetic customers, 12 appointments and three local accounts.
2. Create a customer, assign Demo Alex, add a note and plan an appointment.
3. Compare Alex's access with Demo Sam's denied access, then reassign responsibility as admin.
4. Upload the CSV template, inspect the preview and confirm. Re-upload it to show duplicate feedback.
5. Show the tests and explain one failure case, one design tradeoff and one current limit.

## Presentation scope

The local core is implemented and verified. This public repository contains the case study, screenshots and a local verification summary. The application source remains private; no open-source license is granted. The walkthrough above refers to the local application, not a public download. No live hosting, external calendar/email, multitenancy, production load certification or current client deployment is claimed. [Rights notice](../RIGHTS.md).
