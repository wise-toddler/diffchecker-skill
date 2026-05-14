# diffchecker-skill

Create shareable [Diffchecker](https://www.diffchecker.com) URLs from the command line.

## Install

```bash
# As a CLI tool
uv tool install diffchecker-skill
# or
pip install diffchecker-skill

# As a Claude Code skill
npx skills add wise-toddler/diffchecker-skill -g
```

## Usage

```bash
# Optional: login to link diffs to your account
diffcheck login '<diffsession_cookie_value>'
diffcheck whoami

# Compare two files
diffcheck diff file1.txt file2.txt

# With title and expiry
diffcheck diff old.py new.py --title "refactor" --expiry 1_week

# Pipe from stdin
cat old.py | diffcheck diff - new.py

# Shorthand (no subcommand)
diffcheck file1.txt file2.txt
```

## Expiry Options

`1_hour`, `1_day` (default), `1_week`, `1_month`, `forever`
