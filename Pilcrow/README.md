# Pilcrow — public logs

Diagnostic reports from Pilcrow that a customer chose to share publicly, as issues.

**Everything in this repository is public, including the files attached to an issue.** Never put a report here that
came to you privately.

## How reports arrive

In Pilcrow, **Settings ▸ General ▸ Diagnostics ▸ View Log… ▸ Send Report ▸ Report on GitHub…** opens a new issue in this
repository, titled `[Pilcrow] Problem report`. The customer chooses how the report gets onto it:

- **Add Log to Description** puts the newest entries on the clipboard, up to 60,000 characters (GitHub allows 65,536 in
  all), and the customer pastes them into the issue. The report is compact JSON in a code block, and its heading says how
  many entries it holds.
- **Save and Attach File** saves the whole report, and the customer drags it into the issue or chooses it with the attach
  link.

The issue text carries the Pilcrow version, a count of log entries, and which parts were being recorded. Nothing is
committed to the repository.

Customers may write in their own language. Translate with your best effort and answer in theirs where you can.

## Retention

Reports are kept for at most 90 days, and you delete them by hand. Once a month, open the repository's issues and search
for the old ones, replacing the date with the day 90 days ago:

```text
is:issue in:title "[Pilcrow]" created:<2026-07-24
```

Open each one and choose **Delete issue** (closing an issue does not delete it). Deleting needs admin rights, and an
organization owner must first allow issue deletion for the organization's repositories. Anyone may have copied a public
issue or its file by then, so this removes it from this repository and nothing more.

## The report file

One JSON file per report (`format` 1). It always has `appVersion`, `generatedAt` and `entries`. It has `device`,
`performance` and `appSettings` only when the customer left those switched on. Each entry has `time`, `level`, `kind`
(`log` or `breadcrumb`), `category`, `message`, `metadata`, `session` and `source`.

Pilcrow is built to keep document text and file names out of the log: a file appears as a label such as
`file-3fa9c2d1.md`, and paths are removed. If you find document text in a report, treat it as a bug in Pilcrow and delete
the issue.
