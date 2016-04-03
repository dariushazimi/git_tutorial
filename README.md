# git_tutorial
Info on Git from commandline

git log
git show
git status

#revert changes from staging to working area

git reset HEAD README.md


#revert changes back 
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