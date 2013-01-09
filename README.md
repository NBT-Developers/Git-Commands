Git-Commands for Colleages
==========================


Create a new Project
===================

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


The way to make a commit is as follows:
```bash
git add .
git commit -m 'Updated this README.md with git command instructions'
```
- At this point, you've committed all the changes since your last commit to your local git repository; you've segmented that piece of work (feature or whatever it is).

Pushing a commit(s) to your remote repository
```bash
git push origin master
```


git pull
git branch New_Branch_Name
git checkout Branch_Name
git branch
 - List of branches with * next to current
git merge dev
