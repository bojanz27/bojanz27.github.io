
# Git reference

This is a personal reference of basic everyday git commands.


## Contents:
 - [git init](#git-init)
 - [git remote](#git-remote)
 - [git add](#git-add)
 - [git commit](#git-commit)
 - [git status](#git-status)
 - [git push](#git-push)

## git init 

Creates a new git repo in the current folder.
The newly created repo has a single empty branch named `master`.

```bash
git init
```

## git remote

Used to connect local repository to a remote repository

```bash
git remote <nickname> <url>
```

- _url_ is the URL of the remote repo, i.e. https://github.com/bojanz27/bojanz27.github.io.git
- _nickname_ is just the name by which we will refer to the remote. Could be anything. But the standard is to use term `origin`

So the full command is:

```bash
git remote origin https://github.com/bojanz27/bojanz27.github.io.git
```

This merely creates a reference/link from a local to the remote repo. It does not automatically link local branches to the remote branches. The local branches must be linked to the remotes individually. This is done during `git push`(git push)[#git-push]

## git add 

Stages changes for commit. Only staged files are committed during `git commit` 

| Command | Purpose |
| ------- | ------- |
|`git add .` | Stages all files | 
|`git add README.md` | Stages only the one README.md file |

## git commit 

Commits staged changes to local git. Flag `-m` is for the commit message.

```bash
git commit -m "Commit message goes here"
```

## git status 

Shows the current working tree status - any local changes, staged and unstaged, and whether the local branch is behind remote

```bash
git status
```

## git push 

Used to push local commits to the remote repo's branch (called the upstream).

In it's full form, the push command is:

```bash
git push <remote-nickname> <local-branch>:<remote-branch>
```

So, we are pushing commits from a local branch named `local-branch` to the remote branch named `remote-branch` from the remote repo which we nicknamed `remote-nickname`

For example:

```bash
git push origin main:main
```

The entire `...<remote-nickname> <local-branch>:<remote-branch>` part could be omitted if we link local and remote branch by setting the so called upstream reference:

```bash
git push origin main:main --set-upstream
```

or shorter

```bash
git push origin main:main -u
```

>_NOTE_: Flag `-u` is shorter for `--set-upstream`

This is done only once, after which our local git memorizes what is the corresponding remote branch. So we only do:

```bash
git push
```


## Example 

Let's assume we have a remote github repo at https://github.com/bojanz27/bojanz27.github.io.git. 
We want to create local branch with this repo as its remote.

Step 1 - git init 

```bash
git init
``` 

Ste 2 - connect remote named origin

```bash
git remote origin https://github.com/bojanz27/bojanz27.github.io.git
```

Step 3 - add some files 

Let's create a file so that we could be able to commit and push:

```powershell
"This is our readme file" | sc README.md
```

Now lets stage and commit:

```bash
git add .
git commit -m "Initial commit"
```

Ready to push and connect local `master` branch to remote `master` 

```bash
git push --set-upstream master:master
```

That's it. Our local repo is ready for development with `master` referencing remote's `master`