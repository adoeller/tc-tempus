# Tempus — optional Everything (voidtools) integration

Tempus can use **[Everything](https://www.voidtools.com/) (voidtools)** to speed up
folder work and to show folder sizes, by reading Everything's index over IPC.
**No extra DLL is shipped or required** — Tempus talks to a running Everything
directly. Configure it in the `[Everything]` section of `Tempus.ini`.

## Requirements

- **Everything must be running.** Download: [voidtools.com](https://www.voidtools.com/).
- **Everything 1.4.1 or later.**
- For **folder sizes** (the `ESize` field on folders): enable **"Index folder size"**
  in Everything → **Tools → Options → Indexes**. Without it, folder sizes are left
  to Total Commander (files still show their native size).

## Keys (`[Everything]`)

- `UseEverything=1` (default) — folder-date fields get the newest descendant date
  from Everything's index instead of scanning the filesystem. Falls back to
  scanning when Everything is unavailable or the drive isn't indexed.
- `UseEverythingSize=0` (default) — the `ESize` field reads folder sizes from
  Everything. Off by default; needs "Index folder size" enabled (see above).
- `EverythingTimeoutMs=300` — per-query hard timeout so a stuck query can't freeze TC.

## The `ESize` field

Add the column `[=tempus.ESize]`. Files show their native size; folders show the
recursive size from Everything (when `UseEverythingSize=1` and "Index folder size"
is enabled). The field offers the usual size units (bytes / KB / MB / GB).

SDK reference: [Everything SDK](https://www.voidtools.com/support/everything/sdk/).
