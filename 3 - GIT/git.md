# Introduction

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. Its purpose is to keep track of changes to computer files including coordinating the work that various people do on shared files in a code repository.


# Most frequent commands.

## Configure tooling

```
# Sets the name you want attached to your commit transactions.
- git config --global user.name "[name]"


# Sets the email you want attached to your commit transactions.
- git config --global user.email "[email address]"
```


## Create repositories

```
# Turn an existing directory into a git repository.
- git init


# Clone (download) a repository that already exists on GitHub, including all of the files, branches and commits.
- git clone [url]
```

## The .gitignore file
Sometimes it may be a good idea to exclude files from being tracket with Git. This is tipically done in a special file named .gitignore. You can find helpful templares for .gitignore files at github.com/github/gitignore .


## Branches
Branches are an important part of working with Git. Any commits you make will be made on the branch you're currently "checked out" to. Use git status to see which branch that is.

```
# Creates a new branch.
- git branch [branch-name]


# Switches to the specified branch and updates the working directory.
- git checkout [branch-name]


#Combines the specified branch's history into the current branch. This is usually done in pull requests, but is an important Git operation.
- git merge [branch]


# Deletes the specified branch.
- git branch -d [branch-name]

```

## Synchronize changes
Synchronize your local repository with the remote repository on GitHub.com

```
# Downloads all history from the remote tracking branches.
- git fetch


# Combines remote tracking branch into current local branch
- git merge


# Uploads all local branch commits to GitHub
- git push


# updates your current local working branch with all new commits from the corresponding remote branch on GitHUb.
git pull is a combination of git fetch and git merge.
- git pull

```

## Make changes
Browse and inspect the evolution of projects files.

```
# Lists version history for the current branch.
- git log


#Lists version history of a file, including renames.
- git log --follow [file]


#Outputs metadata and content changes of the specified commit.
- git show [commit]


# Snapshots the file in preparation for versioning.
- git add [file]


# Records file snapshots permanently in version history.
- git commit -m "[descriptive message]"

```

## Redo commits 
Erase mistakes and craft replacement history.

```
# Undoes all commits after [commit], preserving changes locally.
- git reset [commit]


# Discards all history and changes back to the specified commit.
- git reset --hard [commit]

```

CAUTION! Changing history can have nasty side effects. If you need to change commit that exist on GitHub (the remote), proceed with caution. If you need help, react out at github.community or contact support.

### First steps making a repository:

```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin [URL of the repository]
git push -u origin main

```

Or push an existing repository from the command line:

```
git remote add origin [link of the repository]
git branch -M main
git push -u origin main

```