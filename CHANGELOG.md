# Changelog

Notable changes to the SwanDesk installer. Versions follow a `YYMM.DD.build`
scheme (e.g. `2607.23.2` = 2026-07, day 23, build 2). Each GitHub
[release](../../releases) also carries its own notes and download.

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
