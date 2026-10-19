# Scope CRM — case study

[Deutsch](CASE-STUDY.de.md) · [Project overview](../README.md) · [Verification](VERIFICATION.md)

An independent, AI-assisted Laravel CRM by **LeonScope**. It demonstrates a complete customer workflow with server-side permissions, appointments, activity history and a confirmed CSV import. It runs locally with synthetic data and no external business service.

## What the demo is for

A small sales or service team needs customer details, notes and appointments to stay together. When responsibility changes, the new team member should be able to pick up the work, while the previous owner loses access.

The demo covers one team with two roles. It was built separately so these workflows can be demonstrated without using a former client's code or data.

## The working solution

An administrator can assign customers and manage the entire customer set. Employees can read and edit only their own active customers. Notes and appointments stay attached to the customer, and reassignment changes access immediately. Archive and restore preserve the history.

CSV import follows **upload → preview → confirmation**. All rows must be valid. Duplicates, stale assignments, expired previews and changed files prevent import. A successful confirmation writes all customers and their activity entries in one transaction; a failed audit write rolls the whole operation back. Repeating confirmation does not create another set of customers.

![CSV review before confirmation](../assets/import-preview-desktop.png)

## Engineering decisions

| Decision | Reason and tradeoff |
| --- | --- |
| Laravel, Blade and a single application | Keeps authentication, validation, views and domain rules together. A separate SPA/API would add boundaries without improving this demo's workflow. |
| SQLite | The local demo runs without a separate database service. MySQL and heavy concurrent use have not been tested. |
| Policies and scoped queries | Direct URLs and writes use the same ownership/archive rules as the interface. Hiding a control is not sufficient. |
| Shared field validation | Customer forms and CSV rows apply the same field limits, status values and email uniqueness rules. |
| Transactional writes with activity history | A business change and its audit entry succeed together. History is application-level traceability, not protection against a database administrator. |
| Private, expiring CSV previews | Uploaded bytes remain outside web-served paths. A content hash binds confirmation to the checked file. Cleanup failures remain tracked for retry. |
| UTC throughout | Avoids implicit time-zone conversion in this small demo; a future localized calendar would need a separate time-zone design. |

## Evidence and lessons

The local application suite contains **53 tests and 430 assertions**. Four browser workflows cover the customer lifecycle, permissions, keyboard navigation, mobile layouts and CSV import. The [verification record](VERIFICATION.md) identifies the source revisions and actual run scope. The results describe the tested behavior of the demo; they do not measure production use or business savings.

Two concrete implementation lessons emerged: an audit field named `changes` collided with Eloquent's internal property and required explicit attribute access; cleanup needed stable ID-based pagination so processed batches did not cause later ones to be skipped. Regression tests cover both behaviors. Invalid imports and simulated write failures are tested alongside the happy path.

## My role and the use of AI

I chose to build an independent CRM demo, confirmed the scope and guided the revisions. Codex generated the code, interface, sample data and tests and ran the documented checks.

AI was used during development. The CRM itself processes customer data using fixed rules and does not use an AI model.

## Walkthrough for an individual presentation

1. Start the demo and show the dashboard with 40 synthetic customers, 12 appointments and three local accounts.
2. Create a customer, assign Demo Alex, add a note and plan an appointment.
3. Compare Alex's access with Demo Sam's denied access, then reassign responsibility as admin.
4. Upload the CSV template, inspect the preview and confirm. Re-upload it to show duplicate feedback.
5. Show the tests and explain one failure case, one design tradeoff and one current limit.

## What is published here

The local application is implemented and tested. This repository contains its write-up, screenshots and test results. Source code remains private, with no open-source license granted. The walkthrough above refers to the local demo, which is not offered as a download.

Public hosting, external calendars or email, and separate customer tenants are not implemented. Production load testing has not been performed. The current operation of the earlier client project is separate from this demo. [Rights notice](../RIGHTS.md).
