# Git Aliases

This repository contains my personal Git aliases for easier searching and history review.

## 🚀 Setup

1. Clone this repo to your home directory:

```bash
git clone git@github.com:<your-username>/dotfiles.git ~/dotfiles
````

2. Include the alias config in your global Git config:

```bash
git config --global include.path ~/dotfiles/.gitconfig.aliases
```

> If you already have an `include.path`, you can add this one in addition.

3. Verify installation:

```bash
git config --get-regexp '^alias\.'
```

You should see the `find` alias listed.

---

## 🔍 Available Aliases

### `git find`

Searches commit history for a given regex **and shows only relevant lines** with pretty output.

**Usage:**

```bash
git find "<regex>" [<file>]
```

* `<regex>` → The pattern to search in diffs (e.g. `Add.*Record`)
* `[<file>]` → Optional file path. If omitted, searches the entire repo.

**Examples:**

```bash
# Search AddRecord changes in ReportView.js
git find "AddRecord" report.js

# Search any "Record" changes across the repo
git find ".*Record"
```

**Output includes:**

* Commit hash, author, and date
* File(s) touched
* Diff lines matching the regex
* Blank lines between commits for readability

---

## ⚡ Notes

* Requires `git` installed and available in `$PATH`.
* On macOS, no GNU tools are required — works with default BSD tools.
* Uses `grep` and `sed` internally.
* Colors are forced with `git -c color.ui=always`.

---

## 🛠 Maintenance

To update your aliases, edit:

```bash
~/dotfiles/.gitconfig.aliases
```

Commit and push changes back to this repo:

```bash
cd ~/dotfiles
git add .gitconfig.aliases
git commit -m "Update git aliases"
git push
```
