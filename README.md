Adding information about user

```sh
git config --global user.name "John Doe"
git config --global user.email john@doe.com
```

Checking the information has been saved

```sh
git config user.name
git config user.email
```

Checking if there are any changes on the repository

```sh
git status
```

Adding a new file to staging

```sh
git add readme.md
```

When we do run "commit", we send a "hunk" (difference with the previous commit), a message, a SHA, a date, a time and an author

Doing commit from staging to the repository

```sh
git commit -m "Creating the file readme.md"
```

Checking the log

```sh
git log
```

Reverting a file locally

```sh
git checkout -- readme.md
```

After deleting a file, we need to remove it from staging

```sh
git rm readme.md
```

Deleting a file from stating (including file removal)

```sh
git reset HEAD readme.md
```

Reverting locally the previous commit

```sh
git reset --hard HEAD~1 
```

Reverting remotelly the previous commit but not locally

```sh
git reset HEAD~1
```

Checking the diffence between the working repository and the local copy

```sh
git diff HEAD
```

Checking all the events in the repository (not only on master backwards)

```sh
git reflog
```

Reverting to a specific commit (locally too)

```sh
git reset --hard 3313388
```

Reverting to a tag

```sh
git reset Beta
```

Creating/Checking branches

```sh
git branch NewFeature
git branch
```

The branch pointer doesn't move when creating a new branch, a checkout is needed

```sh
git checkout NewFeature
```

Alternatively, this will do both

```sh
git checkout -b master
```

Updating the name of a branch

```sh
git Branch -m Windows8 Windows8.1
```

Deleting a branch

```sh
git branch -D NewFeature
```

The command "checkout" moves the pointer HEAD from one place to other one, also discard changes

The command "reset" moves the branch (and the commit). It's commonly used to undo a commit

When deleting a branch by mistake, the way to recover it is doing a checkout to the last commit and then creating the branch with the same name again

Chaining commands

```sh
git branch master && git checkout master
```

Same than previous command

```sh
git checkout -b master
```

To create/check/delete tags to mark events. Tags cannot be moved, only created or deleted.

```sh
git tag NewTag
git tag
git tag -d NewTag
```

Merging branches is possible with two methods: "with fast-forward" and "without fast-forward"

```sh
git merge picard
git merge –no-ff picard
```

Without fast-forward, a new commit is created with two parents (the previous branches). With fast-forward, the pointer is moved to the last commit of the merged branch 

A merge is also possible with a tag or a commit

Generating logs

```sh
git log --graph
git log --decorate
git log --pretty=oneline
```

Customising commands

```sh
git config alias.graph “log --graph --decorate --pretty=oneline”
```

These two commands are different HEAD~1 and HEAD@{1}, however, these two are the same HEAD~ and HEAD~1

If there is a conflict, the file needs to be edited and then commited

To cancel a merge

```sh
git merge --abort
```

Reverting a merge without fast-forward

```sh
git reset –hard HEAD~1
```

Checking the information from commit or branch

```sh
git show NewFeature
```

Generating .gitignore for any project
[Gitignore.io](https://www.gitignore.io/)

Checking the origin from remote repository

```sh
git remote
```

Linking local repository with existing remote repository

```sh
git remote add origin https://github.com/melquiadesvazquez/GitBash.git
```

Uploading the changes to the remote repository

```sh
git push <remote> <branch>
git push origin master
```

Downloading the changes from the remote repository (git fetch + git merge)

```sh
git pull <remote>
git pull origin
```

Setting a remote branch as the default one so in the future the command git push is enough

```sh
git push -u origin master
```

When pulling a repository the branches will be hidden by default unless

```sh
git branch -a
```

Checking out a remote branch

```sh
git checkout origin/NewFeature
```

Discard changes locally

```sh
git checkout – readme.md
git reset –hard HEAD
```

Commiting changes to a temporal place while a branch is changed

```sh
git stash
```

And in the other branch to import the changes from the temporal place

```sh
git stash pop
```

To check the difference with the repository

```sh
gif diff HEAD
```

To create a new branch in the remote repository and the same for a new tag

```sh
git branch NewFeature
git push origin NewFeature
```

Deleting a branchin the remote repository

```sh
git push origin – delete NewFeature
```

Using "rebase" for those situations when there is a merge without fast-forward. The new code is in top of the existing code, but it's cut from the common parent and the commits are cloned

```sh
git rebase NewFeature
```

Deleting a specific file from all the commits

```sh
git filter-branch --tree-filter 'rm filename' HEAD
```

Simple daily git workflow

```sh
git pull
git checkout -b branch-name-here
git add file-name-here
git status and/or git diff
git commit -m “Detailed message”
git checkout master
git merge branch-name-here
git push
```

Git flow organizes the information with two main branches (master and development) and with temporary branches (hotfix, release and feature). It can be used with the command line but it works very well with Git Kraken
