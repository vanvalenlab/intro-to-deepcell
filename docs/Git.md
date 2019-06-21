# Git and Version Control

## What is version control

Version control is a system of tracking changes to a software codebase. It prevents both catastrophic change and gradual quality erosion via human errors. Additionally, by `branching` and `merging`, it allows different teams to work on the same codebase concurrently, with full traceability.

## What is Git

Developed in 2005 by Linus Torvald, [`Git`](https://git-scm.com/) has become the most widely used version control system in the world. While being a bit hard to learn, it is a standard tool in the software industry. Below we will cover some of the most common commands and workflows.

### git clone

Navigate to a directory where you would like to keep code projects from the lab. Your home directory, `~`, is a perfectly fine choice for now. Then, make a copy of the git repository:  

```bash
git clone https://www.github.com/vanvalenlab/intro-to-deepcell
```

This should download a copy of the codebase inside the current directory.

### git branches

Now that you have the project available, let's switch to a `branch` that is designated for active development. Let's use the `student-bootcamp` branch.

```bash
cd intro-to-deepcell

git branch  # list all local branches
```

Next, let's create a new branch and re-view the list of branches:

```bash
git checkout new-branch-name  # usually a descriptive name

git branch  # list all local branches
```

Now, any changes you make to the code will only affect this new working branch.

As a test exercise, modify the file `resources/name_list.txt` by adding your name to the list. Confirm that your change is recognized by git:

```bash
git status
```

### git commit

Now that you've made a change, let's go through the formality of committing that change to the git repository.

Next, for each file whose changes you want to keep, add that file to git's staging area:

```bash
# To add all files, use `git add .`
git add resources/name_list.txt

git status
```

Now that all the changes you want to keep are in the staging area, let's commit them to your local repository, along with a pleasant note informing your future self of exactly what was running through your head when you made these edits:

```bash
git commit -m 'short explanation of the new changes'

git status
```

At this point, these changes only exist on your local machine. No one else can see them, as they do not exist in the central repository. Let's `push` the commit to the central repository so it can be fully tracked by git:

```bash
git push
```

### Pull Requests

[Pull requests](https://help.github.com/en/articles/about-pull-requests) let you tell others about changes you've pushed to a branch in a repository on GitHub. Once a pull request is opened, you can discuss and review the potential changes with collaborators and add follow-up commits before your changes are merged into the base branch.

Pull Requests keep the git history nice and orderly, and prevent any unexpected changes to the master branch. Once your pull request is submitted on GitHub, the owner of the git repository will do a code review with you, and ultimately will either:

* Approve the PR: The PR is good to go and is ready to be merged into the master branch!

* Request Changes: The PR looks good, but there are a few changes required before it is ready to merge.

* Deny the PR: The PR is redundant or stale, and is no longer needed. Hopefully this will happen rarely.

### Stay updated!

If anyone has made changes to your branch since you created it, you can get access to all of their new changes by performing:

```bash
git checkout master

git pull
```

### Merge Conflicts

What happens if the master branch you pulled from edited the same code that your branch edited?  The dreaded [merge conflict](https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts).

In a merge conflict, Git is not sure which edited lines of code it should keep. It is up to you, the developer, to decide whether to keep `Yours` or `Theirs` (or a combination of both). Most modern code editors will have tools to resolve merge conflicts and git has their own [git-mergetool](https://www.git-scm.com/docs/git-mergetool), but often the following is the easiest way:

```bash
git merge --abort
```

### Additional Resources

There are many other git commands, which have been nicely summarized by Atlassian in [this PDF cheatsheet](https://www.atlassian.com/dam/jcr:8132028b-024f-4b6b-953e-e68fcce0c5fa/atlassian-git-cheatsheet.pdf).
