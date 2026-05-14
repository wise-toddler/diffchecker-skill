---
name: diffcheck
description: Create shareable Diffchecker URLs for comparing text, files, or code. Use when the user wants to share a diff, compare before/after, or create a diff link.
---

# Diffcheck

Create shareable Diffchecker URLs from the CLI using `diffcheck`.

If `diffcheck` is not found, it lives at `~/code/sandbox/diffchecker-skill/diffcheck`.

## Setup

```bash
# Store your session cookie (one-time, optional — works without auth too)
diffcheck login '<diffsession_cookie_value>'
diffcheck whoami
```

## Commands

```bash
# Compare two files
diffcheck diff file1.txt file2.txt

# Compare with title and expiry
diffcheck diff old.py new.py --title "refactor auth" --expiry 1_week

# Compare inline text
diffcheck diff --left-text "hello world" --right-text "hello earth" dummy

# Pipe left from stdin, right from file
cat old_version.py | diffcheck diff - new_version.py --title "migration changes"

# Full JSON response
diffcheck diff a.txt b.txt --json

# Private diff
diffcheck diff a.txt b.txt --private
```

## Expiry Options

`1_hour`, `1_day` (default), `1_week`, `1_month`, `forever`

## Typical Workflow

When the user asks to share a diff or compare content:

1. Write left/right content to temp files if needed
2. Run `diffcheck diff <left> <right> --title "descriptive title"`
3. Return the URL to the user

Example with git changes:
```bash
git diff HEAD~1 -- path/to/file > /tmp/old.txt
git show HEAD:path/to/file > /tmp/new.txt
diffcheck diff /tmp/old.txt /tmp/new.txt --title "latest commit changes"
```
