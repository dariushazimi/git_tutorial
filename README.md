# git_tutorial
Info on Git from commandline

	git log
	git show
	git status

#Revert changes from staging to working area

	git reset HEAD README.md


#Revert changes back 
git checkout -- README.md

#Setup your editor
	git config core.editor "mate -w"
	git config --global -e

#Git History and Alias

	git log --oneline --graph --decorate --all

- Just type git log and compare it with the line of above.
- online: allows us to combine the lines
- graph: provides an astrick based graph denoting our branching higharchy
- decorate: tells us with commits are part of which branches and other lables
	within the git repo
- all provides the history for all the commits available in this repo

We can creat an alias for this 

	git config --global alias.hist "log --oneline --graph --decorate --all"

to use it now just type 
	git hist 
	git hist -- filename

Look at your git config file
	git config --global --list
	
	git add -u # to update git after changes such as move a file to a new file name

	git add -A # make all modification possible on to current working directory and add it to git index
	
#Ignore files
Create a .gitignore file
Include *.log and or any other pattern you want to exclude

#Comparing differnt commits
as an example we run the git hist and we see something like this:
* 56e2b25 (HEAD -> master) added gitignore
* 25cabf1 Ignoring files with git
* d9772b1 (origin/master, origin/HEAD) Cleaned up Readme
* 1d2d466 Nothing added, cleaned
* 889cf06 Removed git_command line file
* ed59c80 deleting demo file
* 89dd901 Git command line tips
* 8cdba8e Added new commands for history and alias
* aff70a2 Added basic commands to get started with Git
* b3044b7 Initial commit

to compare one of the commits with the head:
	git diff 8cdba8e HEAD
	
or use the difftool command
	git difftool 8cdba8e HEAD
	
#Branching
Juat a time line of a commit. 
<<<<<<< HEAD
<<<<<<< Local Changes
<<<<<<< Local Changes
=======
>>>>>>> updates
keep in mind HEAD points to the last commit of the branch.

##Which Branch
	git branch

##New Branch
While working on changes if you decide that these changes should be really part of a new 
branch you can do the following by createing a new branch.
Lets create a new branch called updates
	git checkout -b updates
	

To see the changes and differences between updates and master branch run the following:

	git diff updates master

To integrate the changes from updates to master
We need to change to master
	
	git checkout master

	git hist
	
	-merge changes from updates branch to master
	
	git merge updates

To see the changes and differences between updates and master branch run the following: 
	git diff updates master

# Fastforward
##Fastforward
What is git fastforwad? When changes are so simple, git will do a fast forward, meaning we will
pretend that we never moved away from the master.
Once the changes are done we can delete the branch 

	git branch -d updates
	The above command does not remove the history, it just removes the label.
	
##Conflict resolution - 
