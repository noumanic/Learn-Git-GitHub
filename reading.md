# Git
-> VCS -> tool -> track changes in the code (history, deletion, addition, commits etc.)

# Git 
-> time machine for project -> it records what changed, who changed and when.

# GitHub 
-> software App/website -> store and manage their code using git.
https://www.github.com

# cloud hosting platform for Git repositories.

# What does Remote Actually means in the Git?
In Git, a remote means a version of the repo that is stored somewhere else - online (GitHub, GitLab, BitBucket etc.

Git = local tool -> local repo -> stays on computer
GitHub = remote service that stores Git repos online -> remote repos lives on the internet




md -> markdown 
change -> do
changes 2 step process
1. change -> add
2. changes final -> commit

# Commit Process
changes -> snapshot -> saved the history


# The Three Areas in Git

Every file in Git goes through three stages:

Stage		    	Description								                            	Command

Working Directory	Your local folder where you edit files	git status shows		    	what’s changed
Staging Area		Where you prepare (select) files to include in your next snapshot	    git add file.txt
Repository (Local)	Where Git permanently saves your snapshot (commit)			        	git commit -m "message"


# Git User Naming + Emails (Account in action)

1. Global name and email

When you make a commit in Git, Git stores who made the changes:
For example:

Author: Muhammad Nouman Hafeez <noumanhafeez.nh11@gmail.com>
Date:   Sat Oct 05 2025 ...


These details come from the "Git Configuration"

# Git Configuration Types:
1. Once -> Globally -> For all projects
2. Per Project

# How to Set Globally:

Open Git Bash -> type following commands

git config --global user.name "Muhammad Nouman Hafeez"
git config --global user.email "noumanhafeez.nh11@gmail.com"

Now, every future commits from my system show my name and email.

# How to verify this setting?
-> Run these commands
git config --global user.name
git config --global user.email


or do it by 1 command:
git config --global --list


What you will see:
user.name=Muhammad Nouman Hafeez
user.email=noumanhafeez.nh11@gmail.com


# How to Set Locally (Per Project)?
Run abvoe commands without "--global"

git config user.name "Nouman Work"
git config user.email "nouman@company.com"

It will apply on that working curent repo only.


# Where These Are Stored?

Git saves your configuration in text files:

Scope	File		Applies To
Global	~/.gitconfig	All repos for your user
Local	.git/config	Only the current repo

You can even open .gitconfig in Notepad to view or edit it manually.

# Git File Tracking Status Lifecycle

Every file in a Git repo can be in one of these 4 states:

State       	    Meaning	                                        Typical Git Symbol

Untracked (U)	    New file, not yet added to Git	                ?? or A (after adding)
Modified (M)	    File changed after last commit	                M
Staged (A / M)	    File added to staging area (ready to commit)	A (Added) or M (Modified and staged)
Unmodified	        No changes since last commit	                — (nothing shown)



Symbol	                            Meaning	                        Example Output	                     Description

??	                                Untracked	                    ?? newfile.txt	                    File not added to Git yet
A	                                Added (staged new file)	        A newfile.txt	                    New file added to staging area
M	                                Modified	                    M script.py	                        File changed since last commit
M (in first column)	                Staged modification           	M script.py	                        File changes staged and ready to commit
M (in second column)	            Unstaged modification	        M script.py	                        File changed but not staged yet
D	                                Deleted	                        D oldfile.txt	                    File deleted from working directory
R	                                Renamed	                        R100 oldname → newname	            File renamed
C	                                Copied                          C100 fileA → fileB	                File copied
U	                                Unmerged / conflict	            U file.txt	                        Merge conflict during merge/pull


# Cheat Sheet

Symbol	        Meaning	        Staging?	         Description

??	            Untracked	    ❌	                New file not tracked yet
A	            Added	        ✅	               File added to Git
M	            Modified	    ⚠️ / ✅	          File content changed
D	            Deleted	        ✅	               File removed
R	            Renamed	        ✅	               File renamed
C	            Copied	        ✅                  File copied
U	            Unmerged	    ❌	               Merge conflict


# Quickly check the file statuses
git status -s

# Example

M  index.html      # modified & staged
 M style.css       # modified but not staged
?? new.txt         # untracked


# Other Useful Global Settings

# Set your default branch name to main (demonstrated below also)
git config --global init.defaultBranch main

# Set your preferred text editor (for commit messages)
git config --global core.editor "code --wait"     # for VS Code
# or "notepad" or "nano" etc.

# Enable colored output for better readability
git config --global color.ui auto

# Make Git remember your GitHub login credentials
git config --global credential.helper store

# Creating a new project
mkdir MyProject
cd MyProject

# Initializing git
git init

# Creating a file
echo "Hello Git" > file.txt

# Check what's happening
git status


# Stage the file
git add . (add all)
git add file.txt (only add the specific file)

# Commit ( save the snapshot)
git commit -m "Initial Commit"

# See the history
git log

# Connecting a local repo to GitHub

1. Creating a Empty repo with the repo name , description, tags, collaborators
then connect it with the git.

2. Link your local repo to the GitHub
git remote add origin https://www.github.com/username/reponame.git

3. Push your local commits to GitHub
git push -u origin main


# How to check the Remote Servers the local git repo is connected to?
-v -> verbose -> shows more details -> the URLs

let's say we connected a local repo to a GitHub using

git remote add origin https://www.github.com/noumanic/MyRepo.git

Now type,
git remote -v

we will see something like,

origin  https://github.com/noumanic/MyRepo.git (fetch)
origin  https://github.com/noumanic/MyRepo.git (push)


# What the output means?
Part	Meaning

origin	This is the name (alias) of your remote repo. Default name is always origin.
fetch	The URL used when you download (pull) changes from GitHub.
push	The URL used when you upload (push) changes to GitHub.
URL	    The actual web address of your GitHub repo.



# Why & When to Use It?

Situation		        	    	Why use it

After cloning a repo		    	To check which remote repo it’s linked to.
After adding a remote		    	To confirm you added the correct GitHub link.
If your push/pull isn’t working		To debug and ensure your remote URL is correct.
When working with multiple remotes	To see all remotes (e.g. origin, upstream).


# Disconnect a remote

git remote remove origin

Update/change the remote URL

git remote set-url origin <new-URL>


# Download Updated from the GitHub

git pull -> Hey Git, go to the remote repo (GitHub), get the latest commits and merge them into my local copy.

Shortcut for 2 commands:

1. git fetch      # download changes from remote
2. git merge      # combine them into your branch


So,

git pull = git fetch + git merge


# When You Use git pull?
1. Already have a local copy of a repo.
2. You want to update your local repo with the latest version from GitHub.

# Case 1: Already have a local copy or Already cloned GitHub Repo
git clone https://www.github.com/noumanic/MyRepo.git
cd MyRepo
---> Now if someone (either me, or anyone else in the contributors or any user make the changes)
I can get the latest version by running:
git pull origin main
origin -> the remote repo (GitHub repo)
main -> branch specified (usually it is main or master) master was old name now it is main

By default when we do
git init -> Git initializes a new empty repo -> it requires/needs to create a default branch to start with -> By default -> master branch

Now Git changes the default branch (master) into the main branch


# Git Configuration:
git config --global init.defaultBranch  -> returns = nothing -> master branch -> returns = main -> main branch


# Setting to main:

git config --global init.defaultBranch main
So now, future git init -> default branch -> maoin branch


# Renaming a branch to main:

git branch -m main


# Case 2: ou made local repo first, then connected GitHub later

mkdir MyRepo
cd MyRepo
git init
# ... add files, commit etc.
git remote add origin https://github.com/noumanic/MyRepo.git

To get updates from GitHub later:
git pull origin main

If it is ypour first pull, you might need to set up tracking:
git pull --set-upstream origin main


# Pulling Other People’s Public Repos

# Option 1: Just clone it (If you want to copy to explore or learn):
git clone https://github.com/someuser/project-name.git
Later if the origin repo updates then
cd project-name
git pull origin main
Note: You can see updates but can’t push unless you have permission.

# Option 2: Fork → Clone → Pull updates (for contributing)
If you want to contribute to someone’s repo:

Fork it on GitHub (your own copy under your account).

Clone your fork:

git clone https://github.com/yourusername/project-name.git
cd project-name


Work locally, commit, and push to your fork.

If the original repo gets new updates, you can link it as upstream:

git remote add upstream https://github.com/originaluser/project-name.git
git fetch upstream
git merge upstream/main


# or simply:

git pull upstream main


# git pull Visual Flow

GitHub (remote repo) → git fetch (downloads new commits) → git merge (combines with your local branch) → Your local folder updated


# In Short:

Working Directory  →  Staging Area  →  Local Repository  →  GitHub (Remote)
(edit files)          (git add)         (git commit)         (git push)