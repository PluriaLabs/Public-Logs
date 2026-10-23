# Pilcrow — public logs

Diagnostic reports from Pilcrow that a customer chose to share publicly, and the issues that go with them.

**Everything in this repository is public.** Never put a report here that came to you privately.

## How reports arrive

In Pilcrow, **Settings ▸ General ▸ Diagnostics ▸ View Log… ▸ Send Report ▸ Report on GitHub…** opens a new issue in this
repository. The issue carries the Pilcrow version, a count of log entries, and which parts were being recorded. It carries
no log text. The customer saves the report from the same menu and drags the file into the issue, after reading it in the
viewer.

An attachment lives on the issue, not in the repository. To keep one for good, save it under `reports/`.

## Layout

- `reports/` — reports worth keeping, named `YYYY-MM-DD-issue-<number>.json`.

## The report file

One JSON file per report (`format` 1). It always has `appVersion`, `generatedAt` and `entries`. It has `device`,
`performance` and `appSettings` only when the customer left those switched on. Each entry has `time`, `level`, `kind`
(`log` or `breadcrumb`), `category`, `message`, `metadata`, `session` and `source`.

Pilcrow is built to keep document text and file names out of the log: a file appears as a label such as
`file-3fa9c2d1.md`, and paths are removed. If you find document text in a report, treat it as a bug in Pilcrow and
remove the file.
