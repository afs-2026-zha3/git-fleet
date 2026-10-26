# Git Fleet — zha3

A Git collaboration lab for this class. Everyone shares `main`, with one boat per fixed group (4 groups in total).

## Get started

```sh
git clone https://github.com/afs-2026-zha3/git-fleet.git
cd git-fleet
git branch --show-current
git status
```

Use your GitHub username without the `@` prefix as your unique ID. Write a one-sentence introduction in `introductions/<id>.txt`. Commit only your own introduction file.

## Two rounds of collaboration

At the start of each round, wait for the instructor to pause pushes and announce the common baseline. Confirm that your working tree is clean, then run `git pull --ff-only origin main` and `git rev-parse --short HEAD` to check the baseline. If the update fails, ask a coach to inspect your copy before continuing.

Edit `boarding.txt` in the first round and `reboarding.txt` in the second. Change only your group's list and keep its heading and end marker unchanged. Add your own ID and commit locally, then wait for the instructor to open the push window. When resolving a conflict, keep the published IDs in their existing order and append your own ID. Do not add IDs for other learners.

The first ID in each group's first-round list is the captain. In the second round, the captain returns last: prepare your local commit first, wait for the rest of your group to publish, then merge their changes and publish your own ID.

## Command card

These examples use the first-round file. Substitute your introduction file or `reboarding.txt` for the relevant stage.

```sh
git diff
git add boarding.txt
git diff --cached
git commit -m "docs: add my boarding ID"
# Wait for the instructor to open the push window.
git push origin main
```

If your push is rejected because the remote branch has advanced:

```sh
git fetch origin
git merge --no-ff --no-edit origin/main
```

If Git reports a content conflict, run `git status` and inspect the conflicting file. Preserve the published IDs in their existing order, append your own ID, and remove the conflict markers. Then run:

```sh
git add boarding.txt
git diff --cached
git diff --cached --check
git commit -m "docs: preserve all boarding IDs"
git push origin main
```

An automatic merge does not need an extra conflict-resolution commit. If your push is rejected again, repeat fetch and merge without recreating your original ID commit.

After the instructor stops all writes for final synchronization, everyone runs:

```sh
git pull --ff-only origin main
git rev-parse --short HEAD
git status
```

Check that your commit matches the final commit announced by the instructor and that your working tree is clean. If you encounter a state you cannot explain, preserve it and ask a coach for help. Do not force-push, reset the shared branch, or delete another learner's work.
