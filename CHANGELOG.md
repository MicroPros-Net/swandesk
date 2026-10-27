# Changelog

Notable changes to the SwanDesk installer. Versions follow a `YYMM.DD.build`
scheme (e.g. `2607.23.2` = 2026-07, day 23, build 2). Each GitHub
[release](../../releases) also carries its own notes and download.

## 2610.27.1 — 2026-10-27

This release updates the database automatically the first time it starts.

- **Security:** A signed-in customer could send a specially crafted new-ticket
  request that named someone else as the requester, or set the assignee,
  category or SLA. SwanDesk now ignores those fields when a customer opens a
  ticket. **Update is recommended for every installation.**
- **New:** **Role permissions.** A new **Settings > Permissions** tab lets
  administrators choose what Reps and Managers can do: see tickets from every
  department, delete tickets, edit knowledge base articles, manage canned
  responses, edit the Change Log, edit tasks and assets, see software license
  keys, edit vendors, open contracts and the budget, retry failed email, and
  more. Each role starts with exactly the access it had before, and **Reset to
  defaults** puts it back. Buttons a person isn't allowed to use are hidden, and
  a Rep without task editing sees a read-only view of each task. Settings,
  users, security, API keys and other administrator tools stay admin-only.
  Edition limits still apply: a permission never unlocks a feature your edition
  doesn't include.
- **New:** **Maintenance windows and staff notices in the Change Log**
  *(Professional and Enterprise)*. A change can now carry a maintenance window:
  start and end time, a short summary, the expected impact, and the office it
  affects. SwanDesk emails your staff about it, modelled on the maintenance
  notices internet providers send: an **announcement** when you save with
  **Email the announcement now** ticked (off by default, because most
  maintenance doesn't affect anyone); **reminders** a set number of days before
  the start (default 7 and 1) at a set time of day (default 3:00 PM), plus a
  **final reminder** the day before, never more than one a day; a
  **Rescheduled** notice when you move an announced window; and **Completed**
  and **Cancelled** notices from the new buttons on the change, sent only if
  staff were told about it in the first place. For unplanned outages, the
  **Emergency** box sends the notice the moment you save, allows a start in the
  past and an open end ("Until resolved"), and the Completed notice shows when
  service was restored.
- **New:** Maintenance notices go **To** the help desk address with your
  recipients (usually an all-staff distribution group) in **Bcc**, so a
  "Reply All" reaches only the help desk, and a reply becomes an ordinary
  ticket with a note pointing to the change. Times show your server's time zone
  (PST/PDT, EST/EDT, ...). The email never includes the change's description,
  reason or rollback plan, contains no links, and says so. If SwanDesk is not
  running when a reminder is due, that reminder is skipped rather than sent
  late. The Change Log list and timeline now show each change's window and
  status (Scheduled, In progress, Completed, Cancelled). Defaults live in
  **Settings > Change Log**; the wording can be edited as the "Maintenance
  notice" email template *(Enterprise)*.
- **Fixed:** Saving the password-reminder template (or any template whose event
  isn't a ticket event) in the email template editor silently changed its event
  to "Ticket Updated". The editor now keeps every template's event.
- **Note:** If you customised any page under **Settings > Templates** (for
  example the Change Log, knowledge base, asset, software or ticket pages), the
  saved copy predates these features. **Settings > Permissions** lists any such
  page with a **Use built-in page** button.

## 2609.28.1 — 2026-09-28

- **New:** **Import users from Active Directory.** On a server joined to a
  Windows domain, administrators get an **Import from AD** button on the Users
  page. It lists every enabled account in your directory. Tick the people you
  want, or filter and use **Select all shown**, and SwanDesk creates them as
  regular users. Their name, email, phone numbers, job title, office and
  department come from Active Directory. People who are already in SwanDesk are
  marked and skipped, so importing again is safe. When someone later signs in
  with their domain account *(Enterprise, External Authentication)*, they get
  the account that was imported for them.
- **Fixed:** Email sent to a help desk address through a distribution group
  (for example, a shared "Help Desk" group in Exchange) now gets the usual
  acknowledgement. Before, the group's auto-reply settings suppressed it.
- **New:** Replies are now added to the right ticket even when the subject has
  no ticket number, such as a Reply All to the original email. SwanDesk matches
  the email thread itself. This works for tickets that are still open.

## 2609.18.2 — 2026-09-18

All changes in this release are to **AD Password Expiry** *(Enterprise)*.

- **Changed:** The password-reminder email has been redesigned so it no longer
  looks like a phishing message. It has a fixed subject ("Reminder to change your
  password"), gives your security policy as the reason instead of warning about
  lost access, shows details only your IT team would know (the account name and
  when the password was last changed), says plainly that it contains no links and
  never asks for a password, and uses your brand color. Unedited reminder
  templates upgrade automatically; customized ones are left alone.
- **Fixed:** The reminder subject could read "expires in soon day(s)", and accounts
  that had already expired were told their password "expires in -5 day(s)". Expired
  accounts now show their date marked overdue, and accounts that must change their
  password at next sign-in are told exactly that.
- **New:** **Password change interval.** For domains where Active Directory never
  expires passwords, SwanDesk can date each account from its last password change
  (for example, every 90 days). These dates are marked "policy" and show as
  *Due soon* or *Overdue*. A real Active Directory expiry always takes precedence.
- **New:** Any account with an email address can be reminded individually,
  including accounts whose passwords never expire.
- **New:** A **Changed** marker shows when someone changed their password after
  your last reminder, and a **Reminded, not changed yet** filter lists who still
  needs to act.
- **Fixed:** Saving the reminder settings updates the account list immediately, and
  **Remind all expiring** no longer re-sends to people it reminded moments earlier.

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
