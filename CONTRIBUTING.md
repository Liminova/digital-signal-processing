# The python-project Contributing Guide

## Setting up your Git repository

You should set your Git configuration to automatically rebase on pulls. This is
a saner default and helps with managing unclean branch merges.

```shell
$ git config --global pull.rebase true
```

Afterwards, you will need to clone the repository to your local machine, using:

```shell
$ git clone https://github.com/Liminova/digital-signal-processing
```

Or, if you're using SSH:

```shell
$ git clone git@github.com:Liminova/digital-signal-processing
```

After the repository is cloned, checkout a new branch with:

```shell
$ git checkout -b <branch-name>
```

where `<branch-name>` should follow the format of `<type>/<description>`, e.g.
`feature/print-text`. This will help with managing different feature branches.
The `main` branch should mostly be static and only be merged from these feature
branches, through pull requests.

After you're done, push your code to the remote repository through

```shell
$ git push -u origin <branch-name>
```

Or if you're pushing more code to a branch that already exists on the remote:

```shell
$ git push
```

A pull request should be created from that branch, and after it's reviewed and
fixed of any outlying issues, it will be merged into the `main` branch.

## Development requirements

This repository uses Python 3.10 and `poetry`. If you don't already have
`poetry`, follow the instructions to setting the repository up for usage in the
[README](README.md) file.

This repository uses [commitlint](https://commitlint.js.org) to lint commits,
with the [Conventional Commits](https://www.conventionalcommits.org) format.
For the best experience in committing code, you should have
[Node.js](https://nodejs.org) installed on your local machine. Afterwards:

- Install [pnpm](https://pnpm.io). This repository mainly uses `pnpm` (as shown
  by the `pnpm-lock.yaml` file) but you can use anything. `pnpm` simply gives
  the sanest defaults and the best performance. If you use anything else (`npm`
  or `yarn`), please add their respective lockfiles - `package-lock.json` and
  `yarn.lock` into the `.gitignore` file.

```shell
$ npm i -g pnpm
```

- Install dependencies using `pnpm`:

```shell
$ pnpm i
```

- Every time you want to commit something, use `pnpm cz` after adding files
  with `git add`. This will give you an automated prompt to fill in the
  details of your commit, according to the Conventional Commits format.

- Code should be linted using `pnpm lint` before you commit code. This will
  keep the code style consistent between different files and programmers.
