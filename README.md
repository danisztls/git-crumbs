# Git Prints 

How to efortless maintain similar development environments in multiples machines?

This tool maps recursively Git repositories under a path creating a blueprint that can be used to replicate the same repositories structure in another machine.

If the target directory is dirty — as in the case of existing file syncing that excludes `**/.git/` — it will clone Git administrative files from the remote while preserving the local working tree.

There are many ways of solving this use case like using Git submodules or a development server though for my needs I found that they all sucked and so far I'm unaware of a better way of doing this.

### Syncing

Git is a descentralized version control system where everything is contained within the `.git/` directory. That is awesome but poses a challenge for continuous syncing. It's argued that one should not use such tools with Git as that would be intermixing version control systems and will end badly and ideally Git has everything you need. Though in the real world there are situations where it may make sense to do so because Git often is used in uncoventional ways. As such it's not uncommon to have a rule that ignores `.git/`.

- Git repositories can be mixed and contained within non-Git repositories. As such it's difficult and undesired to exclude them from conventional syncing.
- Local non-ephemeral BLOBs (e.g. videos) can be set to be ignored from Git versioning but expected on the working tree. Git LFS solves that issue but slows down Git operations and at least double the size of the repo.
- Syncing the working tree might be advantageous to someone that is frequently hoping between machines. As the Git data is left untouched it's trivial to discover and fix syncing issues.

## Similar tools

- [git-clone](https://github.com/rkooyenga/git-clone): mass clone repos from a user or an organization
