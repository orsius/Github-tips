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
Always prefere doint a recursive merge (with rebase) then a fast forward merge.

```bash
git checkout <feature_branch>
git rebase master
```
:information_source: you can use `git merge --no-ff feature_branch`to tell git not to do a fast-forward merge

## Tags, Branches and Releases
Tracking production releases using Git Tags, release branches, and GitHub Releases

### tags
Tagging suggestions: *Release:* __major.minor.patch__
* prefix your version names with the letter v
`v1.0 or v5.5.0`
* If the tag isn't for production use, add a pre-release version after the version name
`v0.2-alpha or v6.0-beta.3`

```bash
git tag -a v1.3.2 -m "Tag message"
git push --tags
```

### release branches
When do I have to use them?
* Manual __QA__ *(Quality Assurance)*
* Long running releases *(ex: with ubuntu)*
* On demand hot fixes

```bash
git checkout v1.1
git checkout -b rb1.1
<do your hotfix>
git commit -m "Hotfix"
git tag v1.1.1 -m "Hotfix"
git checkout master
git merge rb1.1 -m "Merged hotfix"
git branch -d rb1.1
```

### releases
If you want to share downloadable binaris plus additional notes with each of you targs, use the "releases" feature in Github.

Benefits of releases:
* Host binary downloads without checking into Git
* Provide additional documentation/release note

:information_source: it's based on your tags.





