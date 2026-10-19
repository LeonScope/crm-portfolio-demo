# Local verification record

[Deutsch](VERIFICATION.de.md) · [Project overview](../README.md)

## Interface review — 19 October 2026

Private application revision: `81eadec6dcd0711006fae2ac8dea94b73d37fb59`. Compact role-aware overview, direct administrator import access and consistent Scope CRM branding.

**53 application tests / 430 assertions and 4 browser workflows passed**, with no failures, skips or browser retries. PHP style checking and the production build passed. The workflows include desktop and 390-pixel mobile views; screenshots were visually reviewed and refreshed from this source.

Browser workflows ran in a new local clone with a newly created synthetic database. Existing installed dependencies were copied into this isolated check environment; they were not reinstalled. Application tests ran against the same source in the private application checkout. Dependency manifests and lockfiles are unchanged. No new live HTTP measurement, dependency advisory scan or fresh dependency installation is claimed for this interface revision.

The checks below retain their original date and scope.

## Earlier full verification — 18 October 2026

These are results from the private, independent CRM application, checked locally on **18 October 2026**. This presentation repository contains no application test suite and does not claim a GitHub-hosted application run. Detailed logs, source and generated access credentials are not published.

| Check | Observed result |
| --- | --- |
| Application suite | **53 tests, 430 assertions; 0 failures, errors or skips** |
| Browser suite | **4 workflows passed together**, with 0 failures, skipped tests or retries |
| Browser scope | Customer and appointment lifecycle, roles, reassignment, archive/restore, mobile navigation/search, keyboard login, request protection and CSV import |
| CSV behavior | **34 application cases** cover field/structure errors, limits, duplicate and archive conflicts, ownership, expiry, changed files, replay, rollback and cleanup failures |
| Fresh installation | Dependencies installed from lockfiles into a clone without an environment, database, credentials or installed packages |
| Setup and repeat setup | 40 synthetic customers, 3 accounts, 12 appointments; a repeat preserved database contents and generated access files |
| Code and assets | Strict Composer validation, complete PHP style check and production build passed |
| Dependency advisories | Composer: no reported vulnerabilities or abandoned packages; npm: zero reported vulnerabilities at check time |
| Application history | Gitleaks found no secrets in the 10-commit candidate history; a separate scan found no private filesystem paths or former-project identifiers |
| Local environment | macOS 26.6, PHP 8.4.23, Composer 2.10.1, Node 24.19.0, Google Chrome 155.0.8059.84 |
| Views | Desktop 1440 × 1060 and mobile 390 × 844; no document overflow in checked views; the mobile CSV table scrolls intentionally |

The 18 October fresh-clone run superseded the earlier separate browser runs. Current screenshots were refreshed during the 19 October interface review with synthetic data. The user-facing demo was not used for browser write tests.

The private application has a GitHub Actions configuration, but it was not executed remotely and is not included in this presentation. Public application CI, a downloadable software release and a hosted service are outside this repository's scope.

These checks do not establish a security certification, production load readiness, MySQL support, Safari/Firefox coverage or accessibility certification. Dependency advice is a point-in-time result. Concurrent edit conflicts and appointment collision prevention remain outside the demo. CSV imports add new customers; they do not update existing customers.
