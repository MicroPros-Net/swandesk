# Changelog

Notable changes to the SwanDesk installer. Versions follow a `YYMM.DD.build`
scheme (e.g. `2607.23.2` = 2026-07, day 23, build 2). Each GitHub
[release](../../releases) also carries its own notes and download.

## 2608.31.1 — 2026-08-31

- **Security:** Text submitted by a user could contain template placeholders that
  the page renderer resolved when that content was displayed, which could cause
  confidential configuration values — including the license key — to be shown to
  whoever viewed the page. Ticket descriptions were affected, and those can arrive
  from customers through the portal or by email. Placeholder handling is now
  restricted to a small allow-list of display values.
  **Updating is recommended for all installations.**
- **Fixed:** Several pages showed raw template placeholders instead of their text —
  most visibly the "Forgot Password" dialog. The password reset, two-factor,
  access-denied and error pages now render correctly.
- **New:** **Common Issues** report — surfaces recurring ticket topics over a date
  range, with an ignore list for terms you don't want counted. HTML, CSV or print.
- **New:** **Ticket Register** report — a date-ranged ticket listing with SLA
  status, scoped to what you can already see. HTML, CSV or print.
- **Fixed:** Reply emails keep their line breaks after the "… wrote:" divider, and
  before the reply-online button.
- **Fixed:** Password-expiry reminder emails now display correctly in Outlook, and
  the AD password-expiry list no longer comes up empty *(Enterprise)*.

## 2607.23.4 — 2026-07-27

- **Fixed:** Replies sent from the **Inbox** now reliably email the customer.
  Staff replies were being saved to the ticket without notifying the requester.
- **Fixed:** Outgoing ticket notifications are no longer delayed when the
  mailbox check runs slowly — they now send promptly.

## 2607.23.2 — 2026-07-26

- **Fixed:** LAPS local-admin password *pull from AD* and *rotate* now work
  reliably from the web interface *(Enterprise)*.

## 2607.23.1 — 2026-07-23

- **New:** LAPS — local-admin password rotation with a secure vault *(Enterprise)*.
