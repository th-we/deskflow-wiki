When reviewing or modifying a PR, we should follow these rules.

See also: [[Hacking Guide]]

## Rules

### 1. Rebase in open requests (do not merge from `master`)

Rebasing keeps the commit history clean and linear, making it easier to track changes and avoiding unnecessary merge commits that clutter the history.

### 2. Never fix PR commits with new commits (use `--amend`)

Using `git commit --amend` allows you to update the original commit with the corrected code, keeping the commit history cleaner and more concise. This avoids having multiple commits like "fix typo" or "fix previous commit."
