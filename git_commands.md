# Git and GitHub commands

## Create a new branch off master

```console
git checkout -b <branch_name>
```

## Create new branch from another branch*

```console
git checkout -b <branch_name> <base_branch>
```

## Do first push of a local branch

```console
git push --set-upstream <remote_name> <branch_name>
```

## Delete remote branch

```console
git push -d <remote_name> <branch_name>
```

## Pull a new branch from origin that doesn't exist locally

```console
git pull origin <remote_branch>:<local_branch>
```

## Fetch a PR and create a new local branch in the process

```console
git fetch origin pull/<PR_ID>/head:<branch_name>
```

## Fetch a fork from someone else and make it a local branch*

```console
git remote add <username> https://github.com/<username>/<forkname>
git fetch <username>
git checkout -b <local_branch> <username>/<branch_name>
```

## Delete local branch

```console
git branch -d <branch_name>
```

## To update the local list of remote branches

```console
git remote update origin --prune
```

## Remove file from git repo history

```console
git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch path_to_file" HEAD
```

## Go back to a previous commit

```console
git reset --hard <comit_id>
```

## Check log of everything that was done, can see deleted / unreachable commits

```console
git reflog
```

## Add individual file changes separately

```console
git add -p
```

## Pick commit from other branch and apply it to front of other branch

```console
git cherry-pick <commit_id>
```

## Good morning workflow

```console
git checkout master
git pull
git checkout <branch_name>
git rebase master
```

## Check origin

```console
git remote show origin
```

## Force push to remote while checking 

```console
git push --force-with-lease
```

## Stash current changes - allows changing branch, etc

```console
git stash
git stash pop
```

## Get admins of repo on Github

```console
curl https://api.github.com/repos/equinor/ioc-santos/collaborators \
    -H "Authorization: Token $(cat ~/.github_api)" | \
    jq '[ .[] | select(.permissions.admin == true) | .login ]'
```

## Fork setup and syncing

<https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork>

## Test GitHub ssh key

```console
ssh -T git@github.com
```
