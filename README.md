# Git Prints 

How to efortless maintain similar development environments in multiples machines?

This tool maps recursively Git repositories under a path creating a blueprint that can be used to replicate the same repositories structure in another machine.

There are many ways of solving this use case like using Git submodules or a development server though for my needs I found that they all sucked and so far I'm unaware of a better way of doing this.

## Features

- Ignore submodules. For each candidate it will query if it's a submodule of it's parent and ignore it if so.
- Preserve existing working tree. If the target directory is dirty — as in the case of existing file syncing that excludes `**/.git/` — it will clone Git administrative files from the remote while preserving the local working tree.

## Usage

### Plan

```sh
git-prints plan <path>
```

NOTE: Prints will be saved at `path/.gitprints/`

### Build


```sh
git-prints build <path>
```

NOTE: Path should be an empty directory containing only prints at `.gitprints/`.

## Similar tools

- [git-clone](https://github.com/rkooyenga/git-clone): mass clone repos from a user or an organization
