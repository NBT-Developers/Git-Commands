Git-Commands for Colleages
==========================

Installing git
```bash
http://git-scm.com/downloads
```
- Download and follow the instructions (recommended).


Create a new Project
--------------------

Initialise the current directory as a git directory
```bash
git init
```

Link it with a remote repository
```bash 
git remote add origin //nbsvr134/gitserver/example
```
- 'origin' is the name you assign to this remote repository (origin is the standard).
- '//nbsvr134/gitserver/example' is the url of the remote git repository


When you've initialised a folder with git init, git will watch (know) what you've changed.

The way in which you should manage your work with git, is that you complete some piece of work (ie. a feature) or fix one.

Then commit that change with a useful comment, so that you and everyone else can see what happened with that commit.

Making a commit
---------------

The way to make a commit is as follows:
```bash
git add .
git commit -m 'Updated this README.md with git command instructions'
```
- At this point, you've committed all the changes since your last commit to your local git repository; you've segmented that piece of work (feature or whatever it is).

Pushing commits to a remote repository
--------------------------------------

```bash
git push origin master
```
- 'origin' is the name you've assigned to the remote
- 'master' is the branch; the master branch is your main branch, and should be the working copy.


Pulling (getting) the lastest version from a remote repository
--------------------------------------------------------------
```bash
git pull origin master
```
- This gets the latest master branch version of this project from the remote repository

Branches
--------

Branches are one of the things that sets git version control systems apart from others, and is extremely powerful

The commands are:
```bash
git branch dev
```
- This creates a new branch locally.
- 'dev' being the new branch name (in this case).

When you've created a new branch you can switch to it by using checkout
```bash
git checkout dev
```
- Checkout (or switch) to the 'dev' branch
- Any changes you make are now made against this branch, leaving your master as it was.
- This means that if you want to work on a new feature, your master still works, and can be deployed - you effectively still have a working version.

Once you've finished working on your branch, it works perfectly, committed all the changes and you want to put this back into your master branch, you do this...

```bash
git checkout master
git merge dev
```
- Checkout 'master' branch again
- Merge the 'dev' branch to 'master'


You can at anytime check which branch you're in by...
```bash 
git branch
> * master
> dev
```

- The two '>' are the returned information
- * next to master, indicates you're on the master branch
- NB. Your git command-line also tells you which branch you're in.

'Git Reset' - Is your friend
----------------------------

Git reset, allows you to reset your current working directory, either to the current working commit (most recent push to the gitserver), or to a particular commit

To completely reset your current working directory to the current gitserver head (last commit)
```bash
git reset --hard HEAD
```

To reset your local commits to a particular commit point, and revert any changes since to 'uncommitted'
```bash
git reset --soft z6c829075ccf6ae98fd4668f229c7d1c7e1a5254
```
- 'z6c829075ccf6ae98fd4668f229c7d1c7e1a5254' is the unique reference for that commit.

So as an example...
- I have a repo, the last commit ref was 12345.
- I make some changes, commit and push to github; with a commit ref of 23456
- But yikes, I did something wrong; and I want to revert; but don't want to completely destroy my changes.
- I would then do...

```bash
git reset --soft 12345
```

My working local commit would now be reset to 12345, but I would still have the changes I'd made.

- This is also useful when you want to bundle small commits - you've done as you've gone along into a single commit.
Example commit history (desc)...

```bash
Started notifications 12345
Added notifications settings 23456
Discovered bug with admin users; and started fixing. 34567
Fixed bug with admin users. 45678
Added additional notification for xyz. 56789
```

This is potentially a lot of commit history, that you may not want in a big project.
So...

```bash
git reset --soft 12345
git add .
git commit -m 'Notifications added'
git push upstream master
```

Now you have a commit history of:
```bash
Notifications added 67890
```