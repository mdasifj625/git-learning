
# Git Log Customization

This document explains the `git log` command and provides some improvements and possibilities for customization.

## Basic Command Breakdown

The basic `git log` command:

```bash
git log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(yellow)%h%C(reset) - %C(cyan)%an%C(reset) %C(green)(%ar)%C(reset)%C(auto)%d%C(reset)%n''%C(white)%s%C(reset)' --all
```

### Explanation:
- **`--graph`**: Shows a visual representation of the commit graph.
- **`--abbrev-commit`**: Shortens commit hashes.
- **`--decorate`**: Adds symbolic names (like branches and tags) to commits.
- **`--date=relative`**: Shows the commit date in relative time (e.g., "2 hours ago").
- **`--format=`**: Defines how each commit is displayed, with color coding:
  - `%C(yellow)%h%C(reset)`: Short commit hash in yellow.
  - `%C(cyan)%an%C(reset)`: Author's name in cyan.
  - `%C(green)(%ar)%C(reset)`: Relative commit date in green.
  - `%C(auto)%d%C(reset)`: Shows branches or tags next to commits.
  - `%s`: Commit message in white.
- **`--all`**: Includes all branches in the log.

## Improvements

### 1. Colorize Commit Body:
If you want to view commit messages along with the body, and highlight the body:

```bash
git log --graph --abbrev-commit --decorate --date=relative \
--format=format:'%C(yellow)%h%C(reset) - %C(cyan)%an%C(reset) %C(green)(%ar)%C(reset)%C(auto)%d%C(reset)%n''%C(white)%s%C(reset)%n%C(red bold)%b%C(reset)' --all
```
- **`%b`**: Includes the commit body in red and bold.

### 2. Display Absolute Date:
If you want both the relative and absolute date:

```bash
git log --graph --abbrev-commit --decorate --date=relative \
--format=format:'%C(yellow)%h%C(reset) - %C(cyan)%an%C(reset) %C(green)(%ar | %ad)%C(reset)%C(auto)%d%C(reset)%n''%C(white)%s%C(reset)' --date=iso --all
```
- **`%ad`**: Absolute commit date in ISO format (e.g., `yyyy-MM-dd`).

### 3. Add Commit Statistics:
To include stats (insertions and deletions) for each commit:

```bash
git log --graph --abbrev-commit --decorate --date=relative \
--format=format:'%C(yellow)%h%C(reset) - %C(cyan)%an%C(reset) %C(green)(%ar)%C(reset)%C(auto)%d%C(reset)%n''%C(white)%s%C(reset)%n''%C(magenta)%C(bold)%C(yellow)%d%C(reset)' --shortstat --all
```
This will display how many lines were added or deleted with each commit.

## Additional Possibilities

### Filter by Author:

```bash
git log --graph --author="asif" --all
```

### Filter by Date:

```bash
git log --graph --since="2 weeks ago" --until="yesterday" --all
```

### Search Commit Messages:
You can search for specific terms in commit messages:

```bash
git log --graph --grep="fix" --all
```

### Show Merge Commits Only:

```bash
git log --graph --merges --all
```

These options allow for powerful customizations and filtering of the `git log` output, making it more useful and visually appealing.
