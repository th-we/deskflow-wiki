Rules for reviewing, creating, or modifying a pull request.

See also: [[Hacking Guide]]

### 1. Use 'Draft' mode until your PR is ready to land

Open PRs will be landed if approved. If the PR is not yet ready to land (e.g. blocked by another PR or WIP) then use draft mode to signal to others that the PR is not yet ready to land.

### 2. Use 'Blocked by' at the top to indicate blockers

If another PR needs to be landed first, use the term "Blocked by" at the top of the PR to indicate that another PR blocks the current PR and needs to be landed first.

### 3. Rebase in open requests (do not merge from `master`)

Rebasing keeps the commit history clean and linear, making it easier to track changes and avoiding unnecessary merge commits that clutter the history.

### 4. Never fix PR commits with new commits (use `--amend`)

Using `git commit --amend` allows you to update the original commit with the corrected code, keeping the commit history cleaner and more concise. This avoids having multiple commits like "fix typo" or "fix previous commit."

### 5. Rebase, do not squash or merge

Squashing allows casual commits in a PR, which we do not want.