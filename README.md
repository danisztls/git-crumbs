# Git Crumbs

How to identify a Git repository without `.git/` and restore data from the remote without changing the existing working tree? How to scale and automate that? This is the predicament that this tool aims to solve.

It does so by leaving a trail of crumbs in the form a `.gitcrumbs` file containing the repository know remotes. It does so by reading that file to restore the Git data while keeping the local working tree.

## Use cases

### Syncing

Git is a descentralized version control system where everything is contained within the `.git/` directory. That is awesome but poses a challenge for continuous syncing. It's argued that one should not use such tools with Git as that would be intermixing version control systems and will end badly and ideally Git has everything you need. Though in the real world there are situations where it may make sense to do so because Git often is used in uncoventional ways. As such it's not uncommon to have a rule that ignores `.git/`.

- Git repositories can be mixed and contained within non-Git repositories. As such it's difficult and undesired to exclude them from conventional syncing.
- Local non-ephemeral BLOBs (e.g. videos) can be set to be ignored from Git versioning but expected on the working tree. Git LFS solves that issue but slows down Git operations and at least double the size of the repo.
- Syncing the working tree might be advantageous to someone that is frequently hoping between machines. As the Git data is left untouched it's trivial to discover and fix syncing issues.

### Metadata

One may want to draw a map of Git repositories in a system without the added Git data found at `.git/`. While having hundreds of repositories in a system it's easy to lose count of things. It's possible to have a monorepo and abuse Git submodules to keep things neatly linked. Though Git submodules are a pain to work and add a lot of maintenance work. Git crumbs preserve the filesystem tree, have a low footprint making it easier to sync and share anywhere and can be used to replicate the repositories in another machine with a single command.

## Features

- Find Git repos and generate a `.gitcrumbs` file containing the repo remotes or update it.
- Warn of repos containing no remotes and leave an empty `.gitcrumbs` file.
- Traverse a directory looking fo `.gitcrumbs` files and restore the Git data while preserving the working tree.

The later is done by cloning the repo with `--no-checkout`.
