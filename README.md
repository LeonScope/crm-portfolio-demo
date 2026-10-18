# CRM Portfolio Demo

**A project presentation by [LeonScope](https://github.com/LeonScope)**
Full-Stack Developer · AI-Assisted Product Builder

[Deutsch](README.de.md) · [Case study](docs/CASE-STUDY.md) · [Verification](docs/VERIFICATION.md)

A CRM for small sales and service teams: manage customers, assign responsibility, record conversations and plan the next appointment. This repository presents the project through screenshots, engineering decisions and documented local checks. **The application source is kept private.**

![Dashboard with synthetic customers, appointments and activity](assets/dashboard-desktop.png)

## What the application demonstrates

- **Customer workflow:** searchable customer records, assignments, notes, appointments, archive and restore.
- **Two roles:** administrators manage the team’s customers; employees access only their assigned, unarchived records. The server enforces these rules.
- **Consistent history:** relevant changes and their activity entries are written together.
- **Reviewed CSV imports:** upload → validation and preview → explicit confirmation; an invalid import creates no customers.
- **A usable local demo:** German interface, desktop and mobile views, 40 synthetic customers and three generated local accounts.

## Selected screens

| Desktop import preview | Mobile validation feedback |
| --- | --- |
| [![CSV preview](assets/import-preview-desktop.png)](assets/import-preview-desktop.png) | <img src="assets/import-errors-mobile.png" width="220" alt="Mobile CSV preview with invalid and duplicate rows"> |

[Mobile customer list](assets/customers-mobile.png)

## Engineering evidence

**53 application tests · 430 assertions · 4 browser workflows passed.** These results were obtained in a fresh local checkout on 18 October 2026. Installation, repeat setup, PHP style, the production build and dependency checks also passed. This public presentation does not run or claim public application CI. See the [verification record and limits](docs/VERIFICATION.md).

The application uses **Laravel 13, PHP 8.4, Blade, SQLite and Vite**. PHPUnit covers business rules and failure cases; Playwright checks complete browser workflows. The [case study](docs/CASE-STUDY.md) explains the design choices and a short interview walkthrough.

## Role and AI assistance

LeonScope set the portfolio goal, approved the product scope and guided the iterations. Codex generated implementation, interface, synthetic data and tests, and ran the recorded checks. The project documents that assistance and the corrections made during verification. The CRM itself does not call an AI model.

## Availability and rights

This is a portfolio presentation, not a downloadable application or a hosted service. It contains no application source, installation package, local credentials or customer database. Screenshots show synthetic data from an independent demo.

**No open-source license or general permission to reuse the original portfolio material is granted.** Applicable law, GitHub’s platform terms and third-party rights remain unaffected. See [rights notice](RIGHTS.md).
