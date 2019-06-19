# Git and Code Development tutorial

`git` is a ubiquitous tool in software development. It allows multiple coders to work on the same project simultaneously without having to worry about whether other coders' changes are affecting their own code, or vice versa.

In order to make changes to the code, we'll be using `sshfs` and whatever text editor you've chosen.

When making changes, everyone will be working on their own Git BRANCH. They then modify some files on their branch and ADD those changes. After they have added all the changes they desire, they COMMIT those changes and PUSH their commits back to the central git repository. (In our case, the central repository is located remotely at https://www.github.com/vanvalenlab/intro-to-deepcell, but in principle it could be located anywhere, even on your own machine.)

### Step 0: Logging into a lab server

If you're not logged in already, open up a terminal and login using the following command:  
```bash
ssh -X -p 5078 [your_username]@[machine_ip_address]
```

### Step 1: Cloning a Git repository

Now that you're logged in, navigate to a directory on the server where you would like to keep code projects from our lab. Your home directory, the one that your terminal puts you in by default once you've SSH'd in, is a perfectly fine choice for now.

Then, make a copy of the central repository:  
```bash
git clone https://www.github.com/vanvalenlab/intro-to-deepcell
```

That command should automatically place a copy of the entire repository inside your current directory.

### Step 2: Mounting a remote filesystem with SSHFS

Open up a second terminal and mount the server's copy of the `deepcell-tf` repository onto your local machine using the following command:
```bash
sshfs -p [port] [username]@[server_ip_address]:[location_of_remote_folder] [desired_local_folder]
```

This might seem kind of strange at first, but we're doing this in order to allow ourselves to modify the code on the server using whatever our favorite text editor on our local computer. (When we're working on Deepcell, this is a critical part of the iteration loop: edit sshfs-mounted Deepcell files in text editor, execute that code on the remote server, repeat.)

Take a moment now and use your favorite text editor (Atom or Sublime, perhaps?) to open the Deepcell code you just mounted locally.

### Step 3: Git Branches

Now that you have the Intro to Deepcell git project available on the server and have a copy of that server code available inside your favorite text editor, let's switch to a `branch` that is designated for active development. Let's use the `student_bootcamp` branch.

First, let's look at a list of all the pre-existing branches:  
```bash
cd ./deepcell-tf
```  
```bash
git branch
```

Next, let's move to the `student_bootcamp` branch and then view the list of branches again:  
```bash
git checkout student_bootcamp
```
```bash
git branch
```

Finally, let's start working on the new branch we just created and look at the list on last time:
```bash
git checkout [fanciful_branch_name]
```
```bash
git branch
```

Now, any changes you make to the code will only affect this working branch.

As a test exercise, let's all modify the file `resources/name_list.txt` and add our own names. Each of you should end up with a file that contains only your name and my name.

### Step 4: Adding, Committing, and Pushing

Now that you've made a change, let's go through the formality of committing that change to the git repository.

First, check git's status to view all the files which you've changed:  
```bash
git status
```

Next, for each file whose changes you want to keep, add that file to git's staging area:  
```bash
git add [filename]
```  
```bash
git status
```

Now that all the changes you want to keep are in the staging area, let's commit them to your local repository, along with a pleasant note informing your future self of exactly what was running through your head when you made these edits:  
```bash
git commit -m [calm_informative_message]
```  
```bash
git status
```

At this point, these changes only exist on your computer. No one else can see them, as they do not exist in the central repository. Eventually, though, we do want to inform everyone else on the team of our hard work. Let's do that now:  
```bash
git push
```

### Step 5: Staying updated

If anyone has made changes to your branch since you created it, you can get access to all of their new changes by performing:  
```bash
git checkout master
git pull
```

### Step 6: Dealing with Merge conflicts

By now, all of you (or maybe all but one?) of you should have gotten errors indicating that there is a conflict.

Let's resolve this conflict.

### Step 7: Making a new branch

Dealing with merge conflicts is... unpleasant. Let's do things the right way in order to minimize the likelihood of them cropping up.

First, let's look at a list of all the pre-existing branches:  
```bash
cd ./deepcell-tf
```  
```bash
git branch
```

Next, let's make our own branch and then view the list of branches again:  
```bash
git branch [fanciful_branch_name]
```
```bash
git branch
```

Finally, let's start working on the new branch we just created and look at the list on last time:
```bash
git checkout [fanciful_branch_name]
```
```bash
git branch
```

Now, any changes you make to the code will only exist within your branch. Go wild!

### Step 8: Merging

That's most of the workflow.

Eventually, once you've finished working on whatever it is you created your branch for (adding a feature, fixing a bug, etc.), you'll merge your branch into the master branch, so that it's now part of the main codebase. Then, whenever other people create their own branches in the future, their branch will include the changes you just made. (To be clear, it's not a rule that everyone work in their own branch. In fact, it often happens that multiple people will be working on one branch at the same time.)

We typically handle the merging process via the GitHub web interface by creating a pull request. Go to www.github.com/vanvalenlab/intro-to-deepcell, select your branch, then click "Pull Request".

Once you have a pull request in, Will and probably someone else will have a code review with you. Given how critical and overbearing we all are, this should be a very painful process.

### Additional Resources

There are many other git commands, which have been nicely summarized by Atlassian in [this PDF cheatsheet](https://www.atlassian.com/dam/jcr:8132028b-024f-4b6b-953e-e68fcce0c5fa/atlassian-git-cheatsheet.pdf).
