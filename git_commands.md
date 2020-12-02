# Git and GitHub commands

## Create a new branch off master

```git
git checkout -b <branch_name>
```

## Create new branch from another branch*

```git
git checkout -b <branch_name> <base_branch>
```

## Do first push of a local branch

```git
git push --set-upstream <remote_name> <branch_name>
```

## Delete remote branch

```git
git push -d <remote_name> <branch_name>
```

## Pull a new branch from origin that doesn't exist locally

```git
git pull origin <remote_branch>:<local_branch>
```

## Fetch a PR and create a new local branch in the process

```git
git fetch origin pull/<PR_ID>/head:<branch_name>
```

## Fetch a fork from someone else and make it a local branch*

```git
git remote add <username> https://github.com/<username>/<forkname>
git fetch <username>
git checkout -b <local_branch> <username>/<branch_name>
```

## Delete local branch

```git
git branch -d <branch_name>
```

## To update the local list of remote branches

```git
git remote update origin --prune
```

## Remove file from git repo history

```git
git filter-branch --index-filter "git rm -rf --cached --ignore-unmatch path_to_file" HEAD
```

## Go back to a previous commit

```git
git reset --hard <comit_id>
```

## Check log of everything that was done, can see deleted / unreachable commits

```git
git reflog
```

## Add individual file changes separately

```git
git add -p
```

## Pick commit from other branch and apply it to front of other branch

```git
git cherry-pick <commit_id>
```

## Good morning workflow

```git
git checkout master
git pull
git checkout <branch_name>
git rebase master
```

## Check origin

```git
git remote show origin
```

## Force push to remote while checking 

```git
git push --force-with-lease
```

## Stash current changes - allows changing branch, etc

```git
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
