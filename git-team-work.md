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


## Issues
Use issues for tracking:
* bugs
* features
*(you can simply use labels do achieve that)*

:information_source: To automaticaly close an issue, you can simply add `fixes #` to your message commit.

```bash
git commit -m "fixes #1"
```

# Markdown 
## readme.md
## wikipage
go to https://github.com/<github_user>/<repo_name>/wiki/_new

# Managing and Securing GitHub
Repo setup, tracking project progress and managing access to your repositories.

## Acces Control in Github
* Owners can do anything
* Collaborators can do anything except manage settings
* Limit ability to commit using fork

:information_source: all dev work on the same code base BUT then have a seperate repo to send pull request to. AND only the team lead or a manager can reject or accept.

* HTTPS favored over SSH
* Use a credential help to avoid typing passwords
* Upgrade to two factor authentication (2FA)
* Creat Access Tokens
	* For login with 2FA
	* For access via build script/API calls, etc.
*(To do so, simply go to 'personal access tokens" and click 'Generate new token' button.)*

### Automated Github Access Options
* SSH agent forwarding => great starting point, no automation available
* OAuth acess tokens => same permissions as the user
* Deploy key => access token limited to a single repo
* Machine user => create a new github account and manage its permissions


# Authomating Github
Integrating existing services, creating custom webhooks, and working with the GitHub API.

## Services
## Webhooks

## Github API
```bash
curl https://api.github.com
curl https://api.github.com/users/orsius
# shows you X-RateLimit values
curl -i https://api.github.com/users/orsius | grep X-RateLimit
# Authentication with token
## get info about your username
curl -i -H'Authorization: token ${TOKEN_HASH}' https://api.github.com/user
## create a repository
curl -i -H'Authorization: token ${TOKEN_HASH}' -d'{"name": "newest_repo"}' https://api.github.com/user/repos

```


