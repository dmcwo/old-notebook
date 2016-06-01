# Learning Git

## Intro
Recommend - https://www.codecademy.com/en/courses/learn-git

Learn / Do approach

```git init``` "init" = initialize - this command sets up git in a directory to  track changes

3 parts to a git project:
* working area
* staging area
* repository

```git status``` check the status of current directory

```git add``` -- adds a file. also do this after updating a file.

```git log``` -- shows a log of commits and messages

### Review
* ```git init``` creates a new Git repository
* ```git status``` inspects the contents of the working directory and staging area
* ```git add``` adds files from the working directory to the staging area. You can string together filenames: ```git add filename_1 filename_2```
* ```git diff``` shows the difference between the working directory and the staging area
* ```git commit -m "message"``` permanently stores file changes from the staging area in the repository
* ```git log``` shows a list of all previous commits

## 2 - backtracking

```HEAD``` commit is the commit you are currently working on

```git show HEAD``` displays this.

```git checkout HEAD filename``` gets rid of the changes you have made since the last commit. Why is this command called "checkout"?

```git reset HEAD filename``` unstages ```filename``` from the current commit but keeps the changes.

> Creating a project is like hiking in a dark forest. Sometimes you take a wrong turn, then another wrong turn. Before you know it, you're surrounded by bears. >

### Turn back time

```git log``` to get a list of commits
```git reset first-7-characters-of-one-of-the-past-commits```

### Review

* ```git checkout HEAD filename```: Discards changes in the working directory.
* ```git reset HEAD filename```: Unstages file changes in the staging area.
```git reset SHA```: Can be used to reset to a previous commit in your commit history.

## Branches

```git branch``` lists the branches you have, with a ```*``` next to the active branch

```git branch branch_name``` creates a new branch called ```branch_name```

```git checkout branch_name``` switches you to working in the branch ```branch_name```

```git merge branch_name``` merges changes in another branch into the current branch.

```git branch -d branch_name``` deletes ```branch_name```

#### Review
* ```git branch```: Lists all a Git project's branches.
* ```git branch branch_name```: Creates a new branch.
* ```git checkout branch_name```: Used to switch from one branch to another.
* ```git merge branch_name```: Used to join file changes from one branch to another.
* ```git branch -d branch_name```: Deletes the branch specified.

## Collaboration

```git clone remote_location clone_name``` - clones a repository - but what does this mean? Any relationship maintained to original? — gives the repository you clone the name "origin" when working on that repository.

```git remove -v``` gives you a list of a projects "remotes" (related repositories?)

```git fetch``` - checks for changes to the remote repository. Doesn't merge changes, but creates a "remote branch" with those changes for review. Doesn't give any feedback, just does it! also - doesn't seem to require that a remote be specified - maybe there can only be 1 per repository?

### Typical Workflow

The workflow for Git collaborations typically follows this order:

1. Fetch and merge changes from the remote
2. Create a branch to work on a new project feature
3. Develop the feature on your branch and commit your work
4. Fetch and merge from the remote again (in case new commits were made while you were working)
5. Push your branch up to the remote for review

The command:

```
git push origin your_branch_name
```
will push your branch up to the remote, origin.  The syntax here seems to be ```push``` the changes I have made to the ```origin``` from ```your_branch_name```

—

https://help.github.com/articles/fetching-a-remote/

