# mastering github
## Config
## Forking and Cloning
Cloning a repo if you're not a collaborateur; 
Contributing to Projects via Forking consist in:
1. fork on your remote repo
2. clone on your local machine
3. push on your remote repo

### submitting a pull request
:information_source: please refer to the github online docs.

### Updating your fork
```bash
# 1. Add remote for upstream
git remote add upstream ${REPO_PATH}
# 2. Fetch changes
git fetch upstream
# 3. Merge them into master
git merge upstream/master master
# 4. Push them to your remote
git push origin master

```

## Single Repository Workflows
Best practices for collaborating in a single repository
### Single repository workflow

```bash
# How to clone a specific Git branch
git checkout -b <branch-name> <origin/branch_name>
```

#### reviewing a pull request
bash```
# 1. download all branches from github
git fetch
# 2. view all of the branches
git branch -a
# 3. checkout a local copy of a remote branch
git checkout ${BRANCH_NAME}
# 4. test code, make any changes and then commit and push changes
<make edits>
git commit 
git push
```

#### rebase
```bash
git checkout <feature_branch>
git rebase master
```
:information_source: you can use `git merge --no-ff feature_branch`to tell git not to do a fast-forward merge








